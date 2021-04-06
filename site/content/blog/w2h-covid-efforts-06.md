---
title: Responding to COVID-19. Part 6 - COVID SAFE
date: '2021-04-06'
summary: >-
  This is part 6 of the series on Way to Health's involvement in helping address the pandemic. This post focuses on the design and launch of the COVID SAFE project. As the Penn health system and the University were looking at re-opening, the one concern was ongoing testing (this was before there was a vaccine in the picture). It was also felt that surveillance testing is critical in getting visibility into and managing the spread of the disease. This post outlines the COVID SAFE project which did this at scale using Saliva based testing methods and Way to Health. 
image: /images/uploads/covid.blog.04.jpg
authorname: Mohan Balachandran
authorimage: /images/team/mohan.jpg
label: COVID-19
---

## Genesis

In the earlier days of the COVID-19 pandemic, as the health system and the university explored ways in which they could re-open, leadership from both institutions at Penn recognized the need to implement a surveillance testing program for its faculty, staff, and students. The program goals were to help to identify asymptomatic, presymptomatic, or mildly symptomatic cases that would otherwise go undetected, and could monitor for spread of possible vaccine-resistant viral variants. Covid SAFE (Screening Assessment for Exposure) was designed to leverage separate but existing tools and resources at the health system to accomplish this goal.

Even with the anticipated (at that time) arrival of effective vaccines, their impact will depend on the speed of manufacturing and distribution, and a willingness by the public to get vaccinated. The thought therefore, was that for a while, widespread testing will be necessary to safely reopen schools and businesses across the country. Because of the large prevalence of asymptomatic cases and associated transmission, surveillance testing was deemed necessary for a while. The secondary thought was to use an alternative test mechanism - namely saliva based testing as opposed to nasal given the discomfort associated with the latter. 

While the initial discussions started on May 21, the program went live on July 31. A lot of that interim time went into setting up the logistics. This last mile problem is often something that gets glossed over but is a critical and core part of the success of the program. Thank god the Nudge Unit and W2H teams have been working together for years now and knew how to make all this happen. Shout outs to Allison Oakes, Chalanda Evans and Cat Reale from the Nudge Unit and Christianne Sevinc and Michael Kopinsky from the W2H team. 


## A full fledged Randomized Control Trial (RCT)

The LAMP BEAC test developed at Penn has a sensitivity of 100% and a specificity of 99% with a limit of 100 copies per microliter. However, this project was designated as an RCT because the saliva test used was not FDA approved at the time. This meant IRBs, remote enrollment requirements and more. Thankfully, this was what Way to Health was built for. 

Further, opt-in vs opt-out language framing was used to try to get more participants enrolled into the program and to also test ways to improve program effectiveness and scalability. 


## Operational implications

<blockquote>
<h3>Everything should be made as simple as possible, but not simpler.</h3> 

-- Albert Einstein
</blockquote>

The diagram below outlines the flow followed by the program at a high level. There are a lot of nuances involved in text messaging such as what if a participant replies with the incorrect response, wants more information, mistypes things and much more while at the same time also considering their user experience. 

![alt COVID SAFE Program Logic](/images/uploads/covid.safe.png "COVID SAFE Program Logic")


From an operational and technical perspective, the following questions / issues had to be addressed. 

- **Remote enrollment**: Since participants were either employees (faculty or staff) or students, we had the advantage of having their email addresses. We used that channel to reach out and try to enroll them into the program. Consent and other such challenges were managed over text with associated links. 
- **Managing testing kits and associated communication**: The details of this are listed in the paper recently published so I won't go into into in too much detail. The key lessons were to move away from prescribed times and kits to a model that allowed for participants to self-select convenient times and text in the kit ID they used.
- **Lab system and other integrations**: Notify lab of scheduled visits and transfer results. If symptoms reported through the PennOpen Pass program, pause text messaging. Collect data from EPIC/ PennChart on confirmatory results. I would love to say this process was seamless but it took a lot of work behind the scenes to make it all work. 
- **Automated results communication**: Once results were available, the communication of results was important in ensuring that participants felt that they got the results as soon as they were available in a proactive manner. 
- **Reporting and analytics**: We built out the dashboard to report out on the success of the program and as a way to indicate how participants were leveraging the program. We also decided to make the dashboard publicly accessible so we wouldn't have to ask the the leads to have to log in every time. Mitesh chose to broadcast this to all participants with the intent to help with self scheduling.
- **Self scheduling**: Just like when you search for a business on Google, this dashboard also showed the most common / busy times at the testing sites. Participants used this data to self-schedule their appointments which is why you see an almost even spread across the times the sites were open. This was an amazing benefit of the transparency provided by the dashboard. The dashboard was the easiest part of this entire effort (as W2H's head of engineering, Michael Kopinsky keeps pointing out) but it is amazing to see the impact of it on the success of the project. 

## Outcomes and numbers

The program was rapidly scaled through multiple phases as described earlier. There is a public facing real-time dashboard that any one can access [here](https://w2h.us/covidsafe-dashboard). Some of the numbers are summarized from the charts from that dashboard as of the publication of this post. 

- **4585 participants**
- **48,310 results**: Results communicated to participants over the same period.
- **0.04%**: Positivity rate was low which allowed leadership to be more informed about re-opening decisions. 

## Press & Publications

More details of this project are now available. A recent publication in NEJM Catalyst titled "[Covid SAFE: Rapid Implementation of a Saliva-Based SARS-CoV-2 Surveillance Testing Program with Automated Scheduling and Reporting](https://catalyst.nejm.org/doi/full/10.1056/CAT.21.0014)" details out all the specifics and numbers described above. 

<br/> <hr/>
Hope you found this post useful. Please feel free to drop us a line via the Contact link below and we'll be happy to discuss this more with you. Look for part 7 of this series next week. 