# Privacy Interest Group meeting - 16 April 2020

## Attendees 

* Peter Snyder (co-chair, Brave)
* Tara Whalen (co-chair, Google)
* Christine Runnegar (co-chair)
* Sean Bedford (Facebook)
* Ben Savage (Facebook)
* Wendell Baker (Verizon Media)
* Sam Weiler (W3C/MIT)
* Kristen Chapman (Salesforce)
* Shaun Gilmore (Apple)
* Erik Anderson (Microsoft)
* Brad Lassey (Google)
* Paul Jensen (Google)
* Melanie Richards (Microsoft)
* Nick Doty (UC Berkeley)
* Jeffrey Yasskin (Google)
* Theresa O'Connor (Apple)
* Hannah Quay-de la Vallee (CDT)
* Joey Salazar (ARTICLE 19)
* Anthony Nadalin
* Terri Oda (Intel)

apologies: Brad will need to drop for the second half

apologies: Melanie will also need to drop

scribing: Sam

## Agenda and Minutes:

### 1. Privacy reviews 

##### RTC Accessibility User Requirements

Link: https://github.com/w3cping/privacy-reviews/issues/3

Pete: completed review; being turned into issues.  No large concerns.

##### Privacy and Accessability document (early draft)

Link: https://www.w3.org/WAI/APA/wiki/Privacy_and_accessibility
Link: https://github.com/w3cping/privacy-reviews/issues/5

Pete: review is complete (above).  No big concerns.  Some tradeoffs.

##### Update re TTML

Link: https://github.com/w3cping/privacy-reviews/issues/2

Nick: Pete and I talked to TTML; I did IMSC review; Jeffrey looked at TTML.  WG wsa somewhat resistance to putting requirements on implementers.  Pull request opened on TTML to note concern.  Debating talking just re: font detection or also conditional loading of resources.  Not sure how WG is working on this.

Pete: spec defines ways to request resources but doesn't go through existing API.  Suggestion was to go through defined API.  Some resistance, so discussion is ongoing.

##### Personalization Semantics Explainer and Module 1 - Adaptable Content

Links:

- Explainer - https://www.w3.org/TR/personalization-semantics-1.0/
- Module 1 - https://www.w3.org/TR/personalization-semantics-content-1.0/
- Privacy and security self-review - w3c/personalization-semantics#131
- Wiki - https://github.com/w3c/personalization-semantics/wiki/
- Getting started page - https://github.com/w3c/personalization-semantics/wiki/Getting-started-with-personalization-semantics
- Github repo - https://github.com/w3c/personalization-semantics/issues

Pete: Pranjal did this review, maybe a month ago.  This is mostly a data spec/ schema.  Dialog going well.

##### HTML Call for horizontal review

Tess: MOU between WhatWG and W3C.  Sent req for horizontal review.  Req contains a list of pull requests that we think might be of interest; there's a list of things we've flagged as likely having privacy implications.  Ideally, each w3c horitzonal review groups will poactively review changes being worked on in HTML and DOM specs.  This request is retrospective.  In the future, we would love tobe able to send you a list of things already merged and hear "yeah, yeah, we already looked at those".  Please take a look.

Pete: timeline?

Tess: no specific timeline.  We're not asking to jump the queue.

Pete: feedback in two weeks useful?

Tess: that would be amazing.

Nick: Tess, you're suggested we just review changes from last review draft?

Tess: yes.  Request has a date range.  

Nick: I'm not sure we've done a review of the full HTML spec.

Tess: that seems like a large effort.

Nick: maybe we should have that on our todo list.

Tess: we're making a point of not asking groups to look at the whole thing.  We hope the deltas are more tractable.  But a more holistic review would be a great idea. and TAG is also doing a review of the delta now and starting a longer process for reviewing the document as a whole.

Brad: where is list?

Tess: [in email requessting horizontal review](https://www.w3.org/mid/034307057eaf9785fc9eedbf6a2e7e8b@w3.org).
There's only ONE entry under privacy!!

Pete: I'll take that as an action item.  Second set of eyes would be good.

Nick: security? (are there any groups doing security reviews right now?)

Tess: I think that request went to public-web-security or webappsec.  I'm not sure which.

### 2. Update regarding font fingerprinting

Pete: CSS WG discussing two proposals out of PING; others from elsewhere.  Call earlier this week.  Seems like there is a way forward.  WG will have another call on issue, possibly w/ PING people.  Resolutions from call: there should be some reduction in number of fonts exposed.  

### 3. Check-in on privacy threat model

Link: https://w3cping.github.io/privacy-threat-model/

Jeffrey: no news from 2 weeks ago.  3 open PRs needing review; not very substantive.  I've been blocked on font stuff instead of this.  

Pete: what do you need?

Jeffrey: review the PRs.  Keep an eye out for things to add to doc; file issues.

Nick: larger work items are re: filing issues.  We have some high-level issues that need to be fleshed out.  PRs might be a much smaller piece.

### 4. New Web developments and privacy considerations 

Jeffrey: Google joined the Privacy CG

[cheers]

### 5. Triage of privacy tracking issues

Link: https://github.com/w3cping/tracking-issues/issues

Pete: new machinery in place.  New way to differentiate between "advisory" and "very important".  We should look though existing issues to see which fall into the second bucket and assign a tracking person.

Discussing issue 89 - https://github.com/w3cping/tracking-issues/issues/89

This was split out from a general review - this issue hadn't been addressed.  All three of these sub-issues need follow-up.

Christine: screen share?

Christine: ones marked as "pending" were pulled in by automated system; I think those need triage.

(scibe switches from Sam to Pete)

Nick: is the goal to assign it to someone?
(maybe the issues that are opened automatically could be opened by a bot username rather than plehegar, otherwise philippe is going to get a lot of questions he doesn't know anything about.)

Sam: Goal is to figure out which issues PING wants to make sure are addressed - that the WG's response should be reviewed by us.  

Pete will review newly opened tracking issues, and contact the PING openers, or otherwise find which person is likely most informed and should review, or have them reviewed on the next PING call.

Sam: we're in agreement that the person most swapped in may set that "resolution-needed" flag?

Pete: definitely they can determine "no resolution needed".  Go ahead and set "resolution needed" for now.

### 6. AOB

#### Notice of WebAppSec mtg next week
#### Notice of Privacy CG f2f

Tess: It'll be the second week of May. I'll be sending out an announcement email soon.






