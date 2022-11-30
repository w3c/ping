# Privacy Interest Group meeting (3 November 2022)

## Attendees 

* Christine Runnegar (co-chair)
* Sam Weiler, W3C/MIT
* Nick Doty (Center for Democracy & Technology, co-chair)
* Peter Snyder (Brave Software, co-chair)
* Jeffrey Yasskin (Google)
* Aram Zucker-Scharff (Washington Post)

Scribe: Nick

## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/)

Small group today!

### 2. Privacy review of CSS Values and Units Level 4

See: https://github.com/w3cping/privacy-request/issues/104

Pete: surprising number of units you can use, and functions/calculations you can do. Nothing about storing state. Makes subresources more active in that you can do more powerful calculations. Worth noting. But no privacy concerns to note.

Separating CSS into many specs does make it so that more have fewer privacy issues.

### 3. Privacy review of Trace Context

See: https://github.com/w3cping/privacy-request/issues/103

Pete: just did Baggage spec review recently from the same group. These two headers are defined, helps tie together multiple HTTP requests/responses together, passes a value on that gets included in response headers. Small item: span id and parent id are synonyms: confusing? Substantive: not clear the boundary of where you cascade these IDs, if done on navigations that would provide for navigational cross-site tracking. Application has to keep around the state id for some period of time. Explainer notes that it's not a privacy concern because applications can already do this. Spec should describe the boundary, explicitly about top-frame navigations.

Explainer: https://github.com/w3c/distributed-tracing-wg/blob/main/EXPLAINER.md#can-a-response-header-returned-to-the-browser-be-used-to-identify-users

Nick: primary use case context is tracing of enterprise applications which are likely single-site, but could be used for easier tracking across sites.

Jeffrey: is this something for browsers to know about explicitly? doesn't anticipate browser implementation.

Pete: could see privacy-harmful implementations that are compatible.

Jeffrey: don't read this as saying that you need to save the context across multiple sites, maybe more for loading an image from a different origin.

Nick: don't anticipate browsers to implement it or to go out of there way to block it

Aram: could expect that browsers might block headers that are being used to track users. more and more services are using fetch() to send tracking information

Nick: Maybe that's good feedback: that the group should make sure this isn't useful for tracking so that there's no incentive for browsers to block it.


### 4. Privacy review of VISS 2 Core and Transport

See: https://github.com/w3cping/privacy-request/issues/102

Sam: We'll postpone this. As a reminder, this is a way of extracting information from vehicles, and they're punting the privacy stuff saying they're not describing the data, just the system for retrieving it. I want to look in more detail.

Aram: Their TPAC presentation was full of potential privacy pitfalls.

Nick: Security issues? Escalate privilege via this API?

Sam: Don't know yet. Thanks for the question.

### 5. Update from privacy reviews of Core AAM and WCAG 2.2

See: https://github.com/w3cping/privacy-request/issues/95

Nick: Joshua started the review here before, and I have a task to try to turn that into GitHub issues. Potential security issues of automation and accessibility. do we have security guidance / feedback from a11y?

Aram: privacy risk would just be fingerprinting?

Nick: concern about automation or exfiltration by malware. will look through spec again to see if that is more of a risk than malware generally.

Sam: could connect to a specific security reviewer.

See: https://github.com/w3cping/privacy-request/issues/98

Pete: will follow up there.

### 6. AOB

PNG (image format) has revisions and looking for a review

https://github.com/w3cping/privacy-request/issues/105

Aram to review later this month

Nick: potential concern about EXIF metadata included in images.

Next meeting would be 17 November (not Thanksgiving week), if necessary.











