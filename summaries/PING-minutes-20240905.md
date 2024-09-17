# Privacy Interest Group (PING) meeting, 5 September 2024

## Attendees 
- Pete Snyder (Brave)
- Nick Doty (CDT)
- Tara Whalen (W3C)
- Jeffrey Yasskin (Google)
- plh (W3C)
- Joey Stanford (Invited Expert)


Apologies: 
Christine
Aram
  
Chair: Nick

Scribe: 

## Agenda

### 1. Introductions, Code of Conduct

https://www.w3.org/policies/code-of-conduct/ 

Tara: privacy lead at W3C! getting hand off of the current work. conversations to figure out what is happening and needs to be done. will be getting more involved in advertising stuff, digital identity, anti-fraud, and connections to security.

[yay!]

Jeffrey: newly a member of the TAG

[congrats!]

### Privacy reviews
        a. Incremental Font Transfer - https://github.com/w3cping/privacy-request/issues/140 (Pete)
        
Pete: new version of an earlier proposal. a way for a site to indicate downloading only a portion of a much larger font file. previous concern was that streaming from the host what content you are reading on the page. group has instead developed patch sizes for very large fonts, so it doesn't communicate the exact glyphs but rather the large relevant sections. seems like a privacy improvement and a good balance with utility. but not clear where the patch sizes are defined. open to feedback, or will open an issue to understand.

Joey: let me know, happy to work together on a review. +1 that it sounds like how segments are defined was left unsaid.
        
        b. Controllers Document - https://github.com/w3cping/privacy-request/issues/137 (Nick)
        
https://github.com/w3c/controller-document/issues/93
        
        c. Pointer events API - https://github.com/w3cping/privacy-request/issues/134 (Jeffrey)
        
Jeffrey: generally innocuous, but identified two potential issues. too much granularity on a sensor can precisely identify a device from its calibration. define a minimum granularity / rounding to solve that. getPredictedEvents -- computer guessing which direction you are drawing/dragging. prediction may rely on learning something about the user's style. predictions should only be based on your interaction with that site or session, treat it like a storage mechanism.

Joey: coalesced events?

Jeffrey: frame rate reduction not likely important since you've already dragged/drawn through each point.
        
       d. WebXR Device API - https://github.com/w3cping/privacy-request/issues/142 (TBD)
           https://github.com/w3cping/tracking-issues/labels/wg%3Aimmersive-web
       
Looking for a reviewer.

Pete looked at an earlier version, will check on previous issues.
Joey: interested. spatial, and also eye movement for pointer events.

### Update regarding Privacy WG (Philippe)

There is a Draft Report
 https://www.w3.org/2024/07/team-report-privacy-wg-fo.html
Waiting on W3C Counsel to finalize it.

### TPAC agenda (Nick and Pete)

https://github.com/w3cping/administrivia/issues/49

should include either a working session or an informational update on Global Privacy Control

Privacy Principles? Jeffrey: even after Statement publication, will need maintainance as bugs come in.
Nick: regular changes to an editors' draft and then occasional Statement publications?
PLH: could publish updated Notes.

https://www.w3.org/groups/ig/privacy/publications/

Security & Privacy Questionnaire: Note was last published in 2021. Should that be published again based on changes to the editors' draft?

Joey: good to regularly re-publish just to show that we have looked at it

Jeffrey: have learned some things about identifiability and what we can do about active and passive. advertising groups might have some good guidance.

Pete: can provide updates on recent batch of changes on Sec/Priv Questionnaire.

### Digital credentials - privacy reviews for a registry (Nick)

https://github.com/WICG/digital-credentials/pull/157

Registry model to do privacy reviews for protocols before they are approved or entered.

Pete: not clear where/how we will implement privacy protections when the details are in a protocol parameter.

Nick: some browsers suggest introspection of the protocol parameter to determine the risk or explain how to do so. some other browsers would just be a dumb pipe, and the wallet application would be where the user consent and protection is.

Pete: what privacy protections can we define in the browser API?

Nick: could define what risk/protections should be in place by browsers, such that sites know what kind of requests will trigger what kind of protections. not sure CG consensus there is likely, but a possible protection.

Nick will share that feedback and share a link to the relevant issue in #ping.

https://github.com/openid/OpenID4VP
Open ID Foundation looking to publish a final 1.0 version of OpenID4VP with any signficant changes to be made immediately, so that publication can happen by the end of the year. Unlikely to complete large privacy review or make substantitve privacy changes in the next week.

### Privacy reviews of charters (Pete)
        https://github.com/w3c/strategy/issues/466
        https://github.com/w3c/strategy/issues/477
        https://github.com/w3c/strategy/issues/478
        
Pete: no areas of concern, mostly boilerplate changes.
PLH: will clarify that no privacy issues needed.

Good to see security analysis (thanks Simone!) for CSS.

What about specs that haven't gone through CR / wide review in a long time? Media Queries, for example.

Some groups maintain vNext or backlog issues that will apply to future versions of their specs. But what about issues that are to be addressed outside of any particular spec?

Jeffrey: W3C TAG keeps this gaps repo as an experiment to track platform-wide gaps: https://github.com/w3ctag/gaps/issues
PING could also track long-term large issues that we'd like to keep track of. Not clear if this will work, but an idea to try.

https://github.com/w3c/transitions/issues?q=is%3Aissue+label%3Awg%3Acss+is%3Aclosed+media
https://github.com/w3c/transitions/issues?q=is%3Aissue+label%3Awg%3Acss+is%3Aclosed+fonts

https://github.com/w3cping/tracking-issues/labels/wg%3Acss
https://github.com/w3c/csswg-drafts/issues/5421
