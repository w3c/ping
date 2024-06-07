# Privacy Interest Group (PING) meeting, 6 June 2024

## Attendees 
- Pete Snyder (Brave)
- Nick Doty (CDT)
- Christine Runnegar (co-chair, invited expert)
- Philippe Le Hegaret (W3C)
- Bartosz Niemczura (Meta)
- Simone Onofri (W3C)
- Jeffrey Yasskin (Google)
- Joey Stanford (Invited Expert)
- Kyle Den Hartog (Brave)

Apologies: 
  
Chair: Nick

Scribe: plh

## Agenda

###  1. Introductions, Code of Conduct
 
https://www.w3.org/policies/code-of-conduct/

Seek diverse perspectives. Help new perspectives be heard and listen actively. 

Nick: we talk a lot but we should make sure newcomers get opportunities to pitch in. so we commit to active listening.

### 2. Federated Identity WG Charter review

See:

- https://github.com/w3c/charter-drafts/issues/531#issuecomment-2144910458
- https://github.com/w3c/strategy/issues/450
- https://w3c.github.io/charter-drafts/2024/wg-fedid.html

Nick: Simone has been working on updates for that. We got a privacy review from Roy but he is on Tokyo time. Simone, any update?

Simone: new charter changes the scope and got new updates. It mentiones the digital credentials API, ie the presentation of credentials from websites to the wallet. To be opened to complete the loop on the issue of credentials, getting the full experience to the user. From privacy perspective, there was proposal from Nick to add a document on potential harms. It's now listed in the charter. Lots of focus in Europe and US on government issued credentials. The threat model would focus on privacy and security. 

https://github.com/WICG/digital-credentials/issues/115

Simone: I'm preparing the checklist for harms. Lots of standards, formats in the ecosystem. (STRIDE, LINDDUN threat models discussed) Depending on what you use, it will be totally different. As an example, depending on the identifier used, it might do an HTTP get.

Nick: My understanding that it includes the set of additional work that would need to be done, in coordination with other groups. We could be doing threat modelling: STRIDE (https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats), LINDDUN (https://linddun.org/threats/). Might be good to list them. Roy has done this privacy noted that the charter defines privacy (<quote>) and stated some concerns. By picking up the user environment, we might be confusing people on what other privacy issues we'd like to address.

Simone: yes. I started with on threat model. we also have data minimization, tracking and unlinkability. in the success criteria, I added wording to address the privacy. It's difficult to write something more precise while the work is in progress. Maybe we could follow up on Github and do a new PR?

Nick: sounds like a great plan, given the timezone challenges. folks, please add comments directly into the issue.

Jeffrey: one the minimally sentence: goals is to talk about privacy preserving interactions. It might be clearer to just say that, rather than adding a sentence with a short definition of privacy.

Simone: yes, it was just an example. [...]

Nick: I encourage this group to look at the draft and add comments, so that W3C can have horizontal review before sending new charter for AC review.

Simone: the definition is also because the scope of the group, having the browser mediate the interactions.

Nick: may of us are concerned with the many implications, not just the browser api.

Simone: it's a complex list indeed. I caught up with the eIDAS folks on their threat model document, which is only focusing on the digital wallet.

Jeffrey: 2 other comments, that might not need actions. Roy was asking out of scope and division of responsabilities between the various groups. Last bit about coordination section: current section is pretty standard and don't think the charter needs to say it's best practice to do self review prior to soliciting horizontal review.

Simone: for browsers, they've done a lot of internal privacy/security reviews before shipping. our work on threat model will help, taking of these things asap.

Jeffrey: the charter does say to work with the other groups in its development.

Nick: ok, we have a bit of home work to continue here.

### 3. Privacy review of HTML Ruby Markup Extensions

https://github.com/w3cping/privacy-request/issues/135
reviewer: Pete

Pete: in order to balance our load and spend our time wheere it is most useful. For Ruby, it seems pretty easy so did it myself. The label attribute allows you to connect different parts of page markup. No state being described here, so it seems harmless related to privacy.

Joey: also looked at it and reached the same conclusion.

Nick: that's great, thank you!

### 4. New privacy review requests

#### a. Pointer Events Level 3

https://github.com/w3cping/privacy-request/issues/134

Nick: events or actions from a mmouse or finger accross the screen. I think we had some issues in the past. If you're interested in fingerprinting, this might be a useful one.

Jeffrey to look at Pointer Events.

#### b. Device Posture API

https://github.com/w3cping/privacy-request/issues/136

Nick: this is about different types of devices that can be folded. Might be a little CSS related but also exposed to JS.

Pete will follow up with Walter.

#### c. Controllers Documents

https://github.com/w3cping/privacy-request/issues/137


Nick: Another one from the VC folks. Closely related to DiD and VC Data Integrity. New spec but expect to be quite similar to previous ones.

Nick to help with this one.

#### d. WebTransport Rechartering

https://github.com/w3c/strategy/issues/445

Nick: that's a group charter about webTransport.

Pete: it's an API similar to Raw Sockets.


Nick: ok, any takers on those reviews?

Pete: I'm always happy to co-review things. 

Nick: I can with someone the VC one. Jeffrey can take one of them.

Pete: I might nudge Walter related to the Device Posture one.

Jeffrey: I'll look at Pointer Events.

### 5. AOB

* Harm modeling

Simone: I was looking at this model. Next week, on Tuesday, I'll be at the CCG call to understand how to proceed. 

https://www.w3.org/events/meetings/8e8242af-7a68-40e4-9a7f-71e2f06b6b12/20240611T120000/
Harms on IDs https://www.accessnow.org/campaign/whyid/
List of threats https://docs.google.com/spreadsheets/d/1WE-xT8fYXfr6yy8de6dav3Ve2G9pB18Eadh6_VqmCuU/edit?ouid=100636309240434757393&usp=sheets_home&ths=true (ask access)


Christine: is there a draft or not yet?

Simone: there are links from charter and issues but it's still work in progress (https://github.com/WICG/digital-credentials/issues/115). It's a threat meta-model. Complex due to the decentralized approach.

Nick: we could combine with other drafts, like the one from Google? (https://github.com/w3cping/credential-considerations/pull/9)

Simone: (shows the "Threat Modeling: Designing for Securit" book).

https://www.google.es/books/edition/Threat_Modeling/YiHcAgAAQBAJ?hl=en&gbpv=1&dq=threat+modeling&printsec=frontcover

* WG Charter

Christine: we still have no update where the privacy wg charter is. I'll be sending a Note from the Chairs asking W3C to make this a priority.

(thumbs ups and thanks to Christine for that)
