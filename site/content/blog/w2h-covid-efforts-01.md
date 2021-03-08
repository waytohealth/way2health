---
title: Responding to COVID-19. Part 1 - COVID Watch
date: '2021-03-09'
summary: >-
  The COVID pandemic has impacted us all in various ways. This is part 1 of a series on Way to Health's involvement in helping address the pandemic. To date, Way to Health has enabled over 10 COVID related projects which were all set up within days to ensure patient quality of care while optimizing resource investments. This post focuses on the design and launch of the COVID Watch project. 
image: /images/uploads/covid.blog.01.jpg
authorname: Mohan Balachandran
authorimage: /images/team/mohan.jpg
label: COVID-19
---

## Genesis
In early March of 2020, when the U.S. began to take the threat of this pandemic seriously, a small team began to brainstorm ideas of how this challenge could be addressed. At this point, the biggest concern was hospitals becoming overwhelmed with patients as we tracked how New York hospitals were struggling. We also realized that for each patient requiring hospitalization, there might be 25 or more patients who would not be sick enough to require hospitalization, but who could worsen quickly or be worried they might. So we focused on addressing the latter problem i.e. we focused on developing a strategy to watch over patients with confirmed or presumed COVID-19 at home. As the [paper](https://catalyst.nejm.org/doi/full/10.1056/CAT.20.0342) published later details, we tried to solve for three goals simultaneously:

1. Support a heterogeneous population of patients infected with Covid-19 who were remaining at home.

2. Identify and expedite the care of infected patients whose conditions were worsening.

3. Reduce health care personnel burden at a time when clinicians were being diverted to other tasks.


## Operational implications
The team met on a daily basis at 7:00 AM, 7 days a week for the first 8 weeks of the program. A few decisions were made quickly. These were:

- We chose SMS as the preferred channel of communication.
- We knew clinicians had to enroll patients into the program otherwise the patients would be confused by a sudden SMS showing up claiming to be from Penn Medicine.
- To simplify the clinician's workflow, we knew we had to enable enrollment from within the electronic health record (EHR), EPIC in our case.
- We focused on dyspnea (difficulty breathing) as the primary symptom to track. While there were other symptoms of COVID, none of the others was felt to be **as clinically critical**. We also had the advantage of having worked on a COPD program which influenced some of these decisions and logic trees. 
- We iterated on the protocol quickly (summarized below) with a lot of focus on language so that patients could easily understand what needed to be done.
- We realized that the technology had to be backed up by personnel to call the patients who escalated to identify if they needed to be brought into the ED or could safely continue to monitor at home.
- We quickly spun up the infrastructure to do that leveraging Penn Medicine on Demand (PMOD) nurses.
- We simultaneously set a target of calling the patient back within 1 hour at the most. 
- We knew we had to track enrollments and escalations so a dashboard was built for that and reviewed daily.
- We knew we had to track quality of the enrollments so false positive and false negative dashboards were also built and reviewed on a daily basis. 

![alt COVID Watch Program Logic](/images/uploads/cat.20.0342-f1.jpg "COVID Watch Program Logic")


## Ramping up and numbers

The program went live on March 23rd with all the operational backends in place and had 3 patients enrolled into the program. By April 1 (10 days), we had 421 patients in the program. By May 1, that number had increased to 3627 and the pace of enrollment kept accelerating. We are currently (at the time of this blog post) at a cumulative count of 15,071 patients. 

![alt COVID Watch Count](/images/uploads/covid.watch.counts.jpg "COVID Watch Count")

At one point, it was thought that perhaps we were being too restrictive in terms of symptoms i.e. asking only about dyspnea. To test this out, we added additional symptom questions that would cause escalations to the nurses manning the lines. We found an 10x increase in escalations but no difference in ED referrals. We quickly reverted this change and the escalation rate dropped back to expected numbers. 

- **Engagement** - Patients continued to engage with the twice daily check-ins at an approximate rate of 80%

- **Escalations** - Depending on the time period, this ranged from 20-40 per day on average. This volume paralled the ebb and flow of the disease in the community.

- **NPS** - Net Promoter score continues to be in the 70+ range with over 5000 respondents. Note that NPS only counts 9s and 10s as promoters. 

- **Spanish version** - To ensure broad coverage, a version of Watch in Spanish was also stood up. This variant has served 346 as of this post's publication.


## Variants

With the ongoing success of the program, there was immediate interest from other departments within Penn Medicine. We were able to very quickly set up variants of the program:

- **Pregnancy Watch**: This was targeted at (obviously) pregnant women. We created a few sub-variants to address site specific phone numbers, times etc.
- **Cancer COVID Watch**: Targeted at oncology patients and managed fully by the Oncology team at Penn. 
- **Main Line Health**: Our CEO, Kevin Mahoney, offered this program at no charge to the other hospitals in the Philadelphia community. We deployed a version of Watch specifically for Main Line Health. 
- **Lancaster General**: We deployed an integrated version of Watch for LGH within 2 weeks. This program was later discontinued as LGH received a grant from the state that required the use of specific software. 

## More to come

Given the success of the program and the sister program (COVID Pulse that gave patients Pulse Oximeters to have a more objective measure of dyspnea - more on this in a subsequent post), the team applied for and [won a $2.5 million grant from PCORI](https://www.pennmedicine.org/news/news-releases/2020/august/2-million-grant-supports-penn-medicine-study-of-covid-watchs-impact-on-health-disparities) to run a full randomized control trial comparing the relative advantages and the program's ability to eliminate racial disparities in care. Enrollment in this program was completed in 4 months and we are currently in the data analysis phase. We'll post more about the results when they can be shared. The program has a [dedicated website](https://covidwatch.waytohealth.org) where more details on the team involved, press, publications, patients quotes and more are documented.

There is an additional manuscript being written about the effectiveness of the Watch program. More on that soon. 

<br/> <hr/>
Hope you found this post useful. Please feel free to drop us a line via the Contact link below and we'll be happy to discuss this more with you. Look for part 3 of this series next week.