#  Privacy Interest Group (PING) meeting, 16 May 2024

## Attendees 
- Pete Snyder (Brave)
- Nick Doty (CDT)
- Christine Runnegar (co-chair, invited expert)
- Walter Rudametkin (Inria/URennes)
- Joey Stanford (Invited Expert)
- lubna dajani (Invited Expert)
- Bartosz Niemczura (Meta)
- Jeffrey Yasskin (Google Chrome)
- Philippe Le Hegaret (W3C)
  

Chair: Nick


Scribe: Pete

## Agenda

###  1. Introductions, Code of Conduct
 

https://www.w3.org/policies/code-of-conduct/


Ensure that everyone who participates is treated equitably and with respect.


Nick: Intros, reminders of code of conduct (above)

Bartosz: from Meta, software engineer, representing privacy team at Meta


### 2. Re: privacy review of CSS View Transitions 2


https://github.com/w3cping/privacy-request/issues/133


Pete: update to a spec previously reviewed a year or so ago. proposal allows styling how transitions from one document to another, like fading between one page and another. change is that it's restricted to same-origin transitions. if anything, that limits any potential privacy risks. raised a couple editorial issues, but no substantive privacy issues.


### 3. Status update and discussion - re: proposed Privacy WG


Nick: as context, last year this group proposed a new group, PrivacyWG, that would do both rec track work, and perform privacy HR reviews: we're still waiting on the status of resolving a formal objection

PLH: we're still waiting on a report from a Council that was formed in March. No ETA on when that report will be ready

Nick: added this to the agenda for an update, but also to see what PING could do to help to resolve the FO / push the report forward

Christine: We should emphasize the importance of establishing the WG ASAP. Its an important signal that the W3C is doing privacy work, but also prioritizing privacy-focused standards work. Other privacy work is also behind held up

Nick: Private Advertising WG is also waiting to be chartered behind the same FO. Is there anything the group would like to do?

PLH: I am pushing this forward each week, would welcome a messages coming from the Chairs

Joey - Chairs

Pete - Chairs

Jeffrey: Process says the console should be convened no more than 45 days after the objection, so we're behind the SHOULD in the process. It's not the console, it's the team that needs to move faster

Nick: Is the suggestion to have folks mention to their AC reps?

Jeffery: yes i will talk to Google's AC rep (CHris Wilson), others should too

Christine: Same, members should talk to their AC reps

Joey: I think the AC rep route is also a good idea, for those that have AC reps

Nick: next steps are i. Pete will propose some text for a possible PING statement, and ii. folks should contact their AC reps. I'm seeing some thumbs up in the call.


### 4. Update and discussion - credentials and privacy


https://github.com/w3c/strategy/issues/458

https://github.com/w3c/strategy/issues/450



Jeffery: there seems to be agreement that there needs to be work between the PrivacyWG, and other credential-related groups. However, that hasn't been discussed here yet so wanted to raise it here. Other discussed options are TAG taskforce

Nick: yes there is a strategy item on github, and something similar is being discussed in WICG each week (see https://w3ccommunity.slack.com/archives/C05UG0EJUDB/p1715738471025739) where folks have concerns about these APIs. Concerns being discussed here are more than just privacy issues


Pete: where to locate the discussion, maybe not a part of the Privacy Working Group since we aren't specifically chartered for it. some people in the privacy group will want to work on that regularly, but not always the same. +1 for a task force or some separate discussion venue.

Jeffrey: we could do it in the working group, and have HR notice the problems, but that will limit our effectiveness. We'd be more effective to be invovled earlier in the process. I haven't confirmed that this is part of the WG charter, but this might be covered by the "other" section in the charter.

Nick: i think that this would be in scope, but its possible that it might be the wrong fit for PrivacyWG. That might suggest a seperate group, or having dedicated Privacy WG meetings. We coudl also work on it async or with the groups

Pete: I take Jeffrey's point. It would be difficult for us to be intimately involved with every spec and I think we should focus our time on activities within our charted scope

PLH: two things, i. Simone is working on the (revised Federated Identity Working Group) charter, but we wont be ready to send it to the AC this week (too many comments).  ii. pLus mozilla expressed a negative opinion, so more work on will be needed. Some interest in adding additional success conditions to the charter about privacy concerns. 

Nick: Is that something we could review?

PLH: Yes, will ask

Nick: best place to follow is the slack thread or github strategy issue


### 5. Re: ARIA 1.3 privacy review


Nick: i did a short review of this. We discussed it on one of the last two PING calls. There were not substantial privacy concerns except possibly around events being sent, and this has been confirmed to not be a privacy concern with the group. There is a broader privacy question about whether a website can learn if an acccessiblity tool is being used. TAG has something related in design principals, and maybe in the TAG security + Privacy questionaire. Just a reminder that we should note


Pete: agreed with Tess to add to security/privacy questionnaire, Pete will draft text.


Pete: during the ARIA 1.2 review, agreed it would be useful to just notate that when a feature might expose accessibility tool usage. that task hasn't been taken up, but at least having it in the questionnaire.


Christine: Is there a way to get the "watermark for accessibility device discovery" on someone's TODO list? PLH, is that something team could do?

PLH: you can open a strategy issue, to track it, and if we can't find someone / somewhere to do it, I'll let you know

Jeffrey (on chat): its a tooling issue, to make sure W3C tooling has this capability in it

Nick: maybe good to open an issue here?

Jeffrey: might need three issues actually, since requires three groups. All three groups are in communication. Needs infra definition (like https://infra.spec.whatwg.org/#tracking-vector), and needs to be added to bikeshed (https://github.com/speced/bikeshed/issues/964) and respec (https://github.com/w3c/respec/issues/4303). Easiest to do in infra first, and then add it to tooling changes. Anyone can send a PR to infra to get things going. Infra is written in bikeshed though (https://github.com/whatwg/infra/blob/283e1b61/infra.bs#L177-L178), so you might need to start there first.

Nick: is there a volunteer to open the first issue?

Christine: I will open the issue in strategy, but may need help if it gets to the bikeshed level of things

Nick: if Christine opens in strategy, I will move relevant bits to infra


### 6. Announcements, and any other business

#### TPAC 2024

Are we (or Privacy WG) meeting there? Yes

Conflicts to avoid: Privacy CG, PAT CG/WG, WebAppSec, Credentials (FedId, VC, CCG), TAG

Number of participants: (check Vancouver attendance)

Joint meetings: ?

TPAC 2024: We would like 4 hours in total, preferably on Monday or Tuesday (late morning).

Mask wearing policy? Yes, please.
 

PLH: we need to decide if we'll go to TPAC. Im assumign we want to meet, regardless of whether we're PING or PrivacyWG. Assume we want to avoid: PrivacyCG, WebAppSec, credentials groups (all of them?), TAG. We said we expected 50 last year, but thats more than I remember being there; maybe 30 would be closer?

Nick: Attendance changes a lot each year

PLH: okie, lets call it 40. No joint meeting targeted. For meeting, 2 hours last year.  Same this year?

Christine: typically i'd think 2 hrs was fine, however, if we have the PrivacyWG charter approved by then, we might want to use TPAC time for technical work. Can we pick two 2hr slots?

PLH: request what you want, team will do its best

Christine: Lets request 4 hrs, and if we don't use it, people can use the time for personal time

PLH: during the week, I'll say mon + tues.  Morning vs Afternoon?

Christine: diff times are better for Europe vs Asia

PLH: Lets do one of each. No, late morning. Do we care about masking policy?

Christine: I am infavor of continued masking

Jeffery+Nick: I favor masks

Lubna: People should be able to choose

PLH: but do we want a requirement?

Christine: how good is the air quality in the meeting space? Risk is lower if good air quality.  In Brisbine IETF had good air quality

Pete: one vote for encouraged but not required

Nick: this is just input for the team and AB right?

PLH: Yes. I dont know about the HVAC system

Lubna: i think it should be optional, but to request better air quality controls, maybe provide air filters in the rooms

PLH: I will check on air filters.  We will def have masks and tests


Nick: AOB? Seeing none, lets wrap up early.

