---
title: Grafana and Prometheus
date: '2021-07-01'
summary: >-
  We recently introduced a new component - or rather set of components - to our
  infrastructure to improve our ability to monitor the operations of Way to
  Health. Prometheus and Grafana give us clear visual metrics for how things are
  working under the hood.
image: /images/uploads/queues2.png
authorname: Michael Y. Kopinsky
authorimage: /images/uploads/kopinsky.jpg
label: technical
---
# Background

Prior to introducing these tools, 

We'll write another post soon about our current monitoring strategy with [health.json](https://inadarei.github.io/rfc-healthcheck/). In short, our application exposes a `/health.json` endpoint which contains information about each of the underlying components of our system - backend microservices, scheduled tasks, daemons, queues, and so on. We run a monitoring tool (sensu) which checks that endpoint every 5 minutes and sends a message to slack if it returns a status of "fail".

![](/images/uploads/health.json-alert.png)

This alerts us quickly to errors, but has a few problems:

1. We have no ability to silence individual errors within health.json. If one component is returning an error (which we're working on or have addressed but ), it's not easy to see if another XXXX. Alert fatigue
1. Have to make up thresholds - no visibility into patterns
1. 

We chose prometheus because it focuses on quantitative timeseries data rather than forcing us too quickly into fail/warn/pass categorization.

# What are each of these new tools?

* Grafana is a dashboard tool that can connect to various data sources. Most commonly it’s used together with Prometheus, but it can also connect to SQL databases, log aggregators, or other things.
* Prometheus is a tool for monitoring and alerting, especially focused on time series data. It is the backend that collects and stores the data, and has a minimal frontend where you can run one-off queries, see graphs, etc. You can’t save graphs or create dashboards - that’s where Grafana comes in.
  * Prometheus polls various “targets” to get metrics at specified frequencies. The targets are configured in prometheus.yml which is baked into our prometheus docker image.
* beanstalkd_exporter XXXX

Both Grafana and Prometheus can do alerting. It seems like in general, the recommendation is to set up alerts within Grafana rather than Prometheus. To date (June 2021), we’re not using these for alerts yet, just for visualizing metrics.

## Feeding data to Prometheus

Prometheus expects to get its metrics in a specific format. By convention, it’s usually at `http://some-hostname/metrics`, and the format needs to be something like the below. For apps that don’t speak this language by default, typically you use an "exporter" to pull data from the application and return it in this format.

This below is a shortened version of what’s returned by beanstalkd_exporter. In this, you see a mix of:

* server-wide metrics
* tube-specific metrics
* Incrementing counters (e.g. total number of times the “delete” command has been used) - you’d only really want to graph the rate of change, not the actual number
* Current stats (e.g. current_jobs_ready)


```
# HELP binlog_records_written is the cumulative number of records written to the binlog.
# TYPE binlog_records_written gauge
binlog_records_written{instance="beanstalkd:11300"} 1.804818e+06

# HELP cmd_delete is the cumulative number of delete commands.
# TYPE cmd_delete gauge
cmd_delete{instance="beanstalkd:11300"} 888629

# HELP cmd_ignore is the cumulative number of ignore commands.
# TYPE cmd_ignore gauge
cmd_ignore{instance="beanstalkd:11300"} 1.5960109e+07

# HELP current_connections is the number of currently open connections.
# TYPE current_connections gauge
current_connections{instance="beanstalkd:11300"} 46

# HELP current_jobs_ready is the number of jobs in the ready queue.
# TYPE current_jobs_ready gauge
current_jobs_ready{instance="beanstalkd:11300"} 836

# HELP current_producers is the number of open connections that have each issued at least one put command.
# TYPE current_producers gauge
current_producers{instance="beanstalkd:11300"} 12

# HELP current_tubes is the number of currently-existing tubes.
# TYPE current_tubes gauge
current_tubes{instance="beanstalkd:11300"} 34

# HELP current_workers is the number of open connections that have each issued at least one reserve command.
# TYPE current_workers gauge
current_workers{instance="beanstalkd:11300"} 43

# HELP total_connections is the cumulative count of connections.
# TYPE total_connections gauge
total_connections{instance="beanstalkd:11300"} 219810

# HELP total_jobs is the cumulative count of jobs created.
# TYPE total_jobs gauge
total_jobs{instance="beanstalkd:11300"} 885380

# HELP tube_cmd_delete is the cumulative number of delete commands for this tub.
# TYPE tube_cmd_delete gauge
tube_cmd_delete{instance="beanstalkd:11300",tube="default"} 0
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_backfill"} 0
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_default"} 32390
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_events0"} 63914
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_events_progressive0"} 0
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_exports"} 0
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_high"} 13
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_low"} 16
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_sync"} 14938
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_sync_fitbit"} 51560
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_sync_fitbit2"} 52609
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_sync_fitbit3"} 51171
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_sync_fitbit4"} 49166
tube_cmd_delete{instance="beanstalkd:11300",tube="demo_sync_fitbit5"} 51103

# HELP tube_current_jobs_ready is the number of jobs in the ready queue in this tube.
# TYPE tube_current_jobs_ready gauge
tube_current_jobs_ready{instance="beanstalkd:11300",tube="default"} 0
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_backfill"} 0
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_default"} 11
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_events0"} 744
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_events_progressive0"} 0
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_exports"} 0
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_high"} 0
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_low"} 0
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_sync"} 0
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_sync_fitbit"} 11
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_sync_fitbit2"} 28
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_sync_fitbit3"} 8
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_sync_fitbit4"} 34
tube_current_jobs_ready{instance="beanstalkd:11300",tube="demo_sync_fitbit5"} 0


# HELP uptime is the number of seconds since this server process started running.
# TYPE uptime gauge
uptime{instance="beanstalkd:11300"} 996309

# HELP version is the version string of the server.
# TYPE version gauge
version{instance="beanstalkd:11300"} 1.1
```

# What do we see or what can we already learn?
* Jobs going through the queue - airport/first class analogy

# Future directions

* Alerting
  * To start, we've set up these tools only to monitor with no alerts set up at all.
  * Dynamic thresholds for queues: Currently health.json has hardcoded thresholds. Which means we need to set them, guess at what a problematic value is, and deal with false positives when it briefly goes above that. Prometheus and Grafana should let us set thresholds like: “Alert if the queue stays above 1000 for more than 5 minutes” or “Alert if this queue length gets longer than 120% of its 2 week high water mark”.
  * A general problem with our health.json approach is that we get a single message in slack for the entire platform, listing all of the problems. A dedicated alerting tool will let us build more granular alerts, silence them, adjust them, etc.
* Data sources: Currently the only data we’re pulling into prometheus is beanstalkd data. I see us finding future value from:
  * pm2 data: Restarts per minute are impossible to capture with our current health.json approach. Health.json/Sensu also throw errors into slack when daemons are down during a deploy. Really what we want is to be alerted if daemons are down for more than 3 minutes, not if they’re down at all
  * Mirth: Raw message volume isn’t interesting/useful/actionable right now, but there are some things that could be. Many of these can be fetched trivially from the API (the same API endpoints 
  * Error rate - if a channel normally errors once or twice per day and now it’s erroring 60 times a day, that means something is up.
  * Performance - is a channel slowing down over time?
  * Volume trends - if a channel is suddenly enrolling twice as many or half as many participants as yesterday/last week, that might indicate something.
