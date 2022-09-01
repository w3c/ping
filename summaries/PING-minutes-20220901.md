# Privacy Interest Group meeting (1 September 2022)

## Attendees (sign yourself in)

* Pete Snyder (Brave, co-chair)
* Nick Doty ( CDT, co-chair)
* Wendy Seltzer (W3C)
* Sam Weiler (WC3)
* Igor Chechelnitsky (Medtronic; trying to join as an IE)
* Don Marti (CafeMedia)
* Alex Kone
* Eric Mwobobia
* Kris Chapman
* Theodore Olsauskas-Warren (Google - First half only)
* Sean Harrison (Google)
* Joshua Ssengonzi

Regrets: Christine

Chair: npdoty

Scribe:  Pete Snyder

## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/)
Igor: I'm new, intro, i work at a company that builds pacemakers and similar products.  Happy to join
Nick: Welcome. 

Nick: We also review and follow the W3C Code of conduct.  In particular, important to keep in mind emphatyh and respect when discussing sensitive and difficult topics

### 2. Privacy review of Core-AAM 1.2
https://w3c.github.io/core-aam/
Reviewer: Joshua

Joshua: I work for a human rights organization in Uguanda. This is my first review. This spec is for helping folks interacting with the Web using assistive technologies.
…: All APIs do not work identically.
…: Since these APIs expose information about page content, they can put users at risk.
…: since these APIs allow for automated tools to interact with the page, user agents should ensure that interactions are authenticated

Nick: thank you for the review, many of us are unfamiliar with the area so this is a good learning experinece for all of us.  
…: When you mention that data is being exposed though through these APIs, who is that data being exposed to.

Joshua: The information might be exposed to malware or other malicious actors.

Nick: the concern is that malware might be running in the operating system? Or in the assistive technology?

Joshua: My concern is that malware might be running thorugh the OS

Nick: Malware is a general concern in network systems. Is there a specific concern here?

Wendy: quotes from the spec "Accessibility APIs make it possible to communicate accessibility information about user interfaces to assistive technologies"

Nick: This spec is about mapping HTML markup to the assistive technologies / APIs provided by OSs?

Joshua: Yes, its about assistive technologies, and about an internal mapping to the end user (how the informaiton is provided to the end user?)

Nick: I see that you have issues filed in this document. Could you share them with the mailing list? Generally we provide these issues back to the groups but I think it would be good to refine these and more carefully identify which risks are unique to the spec?

Joshua: What are next steps? Should i edit and/or comment on github issues, or open new ones?

Nick: Yes, creating new issues is the end goal, though I think it would be good to refine these first w/in PING by sharing the concerns / identified issues w/in PING first


### 3. Privacy review of Web Content Accessibility Guidelines 2.2
https://w3c.github.io/wcag/guidelines/22/
Reviewer: Wendy

Wendy: WCAG is the spcification that W3C provides as guidance to Web content authors (and so not primarily targeting browser implementors).
…: this is a large spec, containing background information, technical recomendations, and accompanied by suggestions for understanding and implementation
…: its also used to guide legal guidelines and requirements in some jurisdictions
…: The group is preparing an update from 2.1 to 2.2; I reviewed the newly updated guidance sections
…: I raised an issue with the groups guidance around avoiding users needing to re-enter redundant information. The spec's suggestions for how to avoid needing users to (Re)enter information could be met in ways that introduce privacy risks
https://github.com/w3c/wcag/issues/2615
…: The group responded with a PR https://github.com/w3c/wcag/pull/2659 that satisfies my concerns

Nick: Thank you! Its great (and uncommon) to have a review of guidance to site authors. Once the group has merged the above PR, we can close the tracking issue


### 4. Privacy review of MiniApp Packaging 
https://www.w3.org/TR/2022/WD-miniapp-packaging-20220729/

Pete: non-blocking privacy issues but came up during the review anyway. spec defines on-disk how an application should run, within a larger runtime/environment, like widgets or tabs within other apps.

Pete: loading app fully into cache initially, but also has functionality for different languages or functions to be loaded at different times.
Pete: entry point in app.js and basic styles in app.css, which is required even if empty.
Pete: lots of requirements about valid filenames, but seems redundant to other specs, could maybe just reference.
Pete: contradictions in requirements about the file extensions
Pete: signing apps to authenticate, method will be shared with others
Pete: not well defined on accessibility

Pete: privacy section -- state may be maintained after a miniapp is deleted. give privacy-protecting runtimes the ability to limit data. 
... goal for user agents to prevent tracking, but not very well specified. aspirational but without guidance.

https://www.w3.org/TR/international-specs/#file_naming

npdoty: signing issues, not using TLS or the certificate authority system. would be good to consolidate, or will need detailed review to address downgrade attacks, authenticity, etc.

sam: questions about delegating lots of issues to the UA
pete: this spec is mostly about the folder structure and encoding, but it's the intersection of specs where privacy or security issues come up. just saying "do this in a private way" is not useful advice.

pete will open issues, but waiting on security help reviewer at Brave prior to the signing question.

### 5. Update on privacy review of Web Neural Network API
CR: Review complete - see https://github.com/webmachinelearning/webnn/issues/280
Reviewer:Christine

Nick: Web Neural Network is an ongoing reivew that Christine has been working on (who is not able to attend today).
…: Christine has filed issues though and is working on the spec authors on providing gudiance, w/in the spec, for site authors that mgiht use the new APIs in the future

### 6. Secure Payment Confirmation (SPC) re-review
https://github.com/w3cping/tracking-issues/issues/260
https://github.com/w3c/security-review/issues/120
Reviewer: Sam

Sam: there are two open issues that the group would like the push out.  Summary of the issues:
…: first was a request to provide UX to the user to prevent the downgrading of credentials. The group does not have a way of doing this yet, and so the groups wants to push the issue out to a future version
…: second issue was around "roaming authenticators" (e.g., yubikeys, things not built into the device). Folks w/in the roaming authenticator business think the issue needs to be pushed out, so I'm (Sam) is okay with it

Nick: where should we track these issues (even if they're postponed)

Sam: we'll leave the needs-resolution issues open

Nick: thank you for the reivew, i know this took a lot of time

Sam: The other issues we originally filed have been dealt with well and many were closed successfully

### 7. Agenda for TPAC 

Nick: TPAC will be hybrid, some of us will be there in person. There will be a PING meeting on Monday. We are working on building out the agenda
…: please share suggestions and requests with the chairs
…: First, we should use the time to decide who will go to which other meetings during the rest of the week at TPAC
…: Second, updates and changes to the privacy review process (including documentation)
…: Third, discussing lessons learned and guidance from doing privacy reviews, to increase consistancy and qualities of reviews going forward
…: Fourth, recruiting more reviewers
…: Fifth, discussing how to track and keep on top of how to follow up on TODO's from TPAC

Don: There is a private advertising group in W3C (WG proposal currently under review) and will generate many new proposals.  We shoudl think through how these new proposals will work together, since if we look at them in isolation we might miss privacy issues
…: second, how much should we (PING) focus on the privacy properties of what folks do on the Web today, vs the direction and incentivies a propsoal would create on the web if a propsoal were adopted

Nick: that sounds important but difficult!

Don: I don't expect it to be a big concern / issue going forward, unless folks are cyncial and maliciouslly strategic in how they construct proposals (to make privacy harming systems out of less privacy harming parts)

Nick: We should also work on guidance on abuse potential / prevention (so, how to make proposals non-harmful to start with)

Wendy: Its important for us to think about ecosystem effects when considering improving privacy.  Where do we have leverage as reviewers, and where should we reach out to and work with other groups.
…: TAG does arch considerations during design reviews.  It would be good  and interesting for us to do similar

Nick: Can we start writing "ecosystem issues" text and guidance (even if just starter text / bullets)

Don: I'd be happy to help write up text like that (example of a proposal that can have positive follow-on effects for users, a proposal that will have predictable negative follow-on effects for users)

Nick: Chairs will send out agenda information and planning materials in advance of TPAC
