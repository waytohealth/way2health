---
title: 'Release Notes: July 2020'
date: '2021-07-09'
summary: Product updates from July 2020. Focus on performance
image: /images/uploads/w2h.inn.logo.jpg
authorname: w2h team
authorimage: /images/uploads/apple-icon-180x180.png
label: release notes
---
"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum."

Section 1.10.32 of "de Finibus Bonorum et Malorum", written by Cicero in 45 BC

"Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam, eaque ipsa quae ab illo inventore veritatis et quasi architecto beatae vitae dicta sunt explicabo. Nemo enim ipsam voluptatem quia voluptas sit aspernatur aut odit aut fugit, sed quia consequuntur magni dolores eos qui ratione voluptatem sequi nesciunt. Neque porro quisquam est, qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit, sed quia non numquam eius modi tempora incidunt ut labore et dolore magnam aliquam quaerat voluptatem. Ut enim ad minima veniam, quis nostrum exercitationem ullam corporis suscipit laboriosam, nisi ut aliquid ex ea commodi consequatur? Quis autem vel eum iure reprehenderit qui in ea voluptate velit esse quam nihil molestiae consequatur, vel illum qui dolorem eum fugiat quo voluptas nulla pariatur?"

**Enhancements**

* Performance
  * Introduce [Scout APM ](https://scoutapm.com/) to help us troubleshoot slow pages and backend operations across the platform
  * Scale start-events task to be able to process multiple events in parallel
  * Web performance: fewer queries for navigation
  * Web performance: device stats
  * Web performance: inbound twilio webhook
  * Web performance: payment feed
  * Web performance: Add index to MRN
  * Improve Manage Data Performance
* New integrations
  * Add subscription/notification support for Omron
  * TrueMotion integration - Enrollment Flow
  * TrueMotion (Way to Drive) Unenrollment Flow
  * Enroll patients discharged from ED with specific diagnoses into FDA site
* Analytics
  * BE ACTIVE sleep analytics tables and dashboard
* Misc
  * Relax password strictness on ppt portal
  * Message metadata in inbox should show timestamp with seconds

**Bug fixes**

* Event calendar broken on ppt view and when date variable block on arm view
* Ratings questions not serializing correctly
* Event logic not evaluated because "access group no longer exists"
* Slow query causing ppt events page not to load when lots of events
* "To:" field in conditional message logic is broken
* Allow anonymous access when redirecting back to qualtrics survey after submission
* Can't batch finish participant because system thinks they have open events
* List variable error because 'invalid value'
* Omron Integration form display doesn't update though database does
* Password changes broke the profile page
* Embed re-enroll button re-enrolls people into their same/closed arms
* Send message in SMS inbox doesn't work for 'finished' participants
* Enrollment survey opens and immediately closes in PennChart embed
* Epic Status filter not working on Manage Data
* Split out Fitbit processing into more than 2 queues
* HSM Penn Medicine discharge data not appearing in Pennchart discharge X 
* Changing survey question text resulted in misconfigured logic sets 
* 'Stop immediately' function on reschedule not stopping windowed event
* Do not create multiple Message Failure incidents for the same text message
* Calendar download fails if there's a StudyUserSchedule with no FeedbackEvents
* Add setting to bypass approval process for filing flowsheet values
* Trigger event block off of messaging keyword
* Schedule participant events by day of the week
