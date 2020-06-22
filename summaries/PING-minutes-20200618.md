
# Privacy Interest Group meeting (18 June 2020)

## Attendees

* Christine Runnegar (co-chair)
* Kris Chapman (Salesforce)
* Lubna Dajani (Allternet)
* Brad Lassey (Google)
* Paul Jensen (Google)
* Erik Anderson (Microsoft)
* Michael Kleber (Google)
* Shivan Sahib (Salesforce)
* Jeff Wieland (Rubicon)
* Tom Kershaw (Rubicon-Telaria)
* Garrett McGrath (Rubicon-Telaria)
* David Benjamin (Google)
* Theresa O'Connor (Apple)
* Martin Meyer (Akamai)
* Konrad Dzwinel (DuckDuckGo)
* Mingzhe Li (Akamai)
* Shaun Gilmore (Apple)
* Nick Doty (UC Berkeley)
* Wendy Seltzer (W3C)
* Joey Salazar (ARTICLE19)
* Wendell Baker (Verizon Media)
* Scott Low (Microsoft)
* Terri Oda (Intel)

apologies: Peter Snyder (co-chair, Brave), Sam Weiler (W3C)

## Agenda

#### 1. Privacy review request from the Web RTC WG - WebRTC Scalable Video Coding (SVC) specification

Spec: https://w3c.github.io/webrtc-svc/

This document defines a set of ECMAScript APIs in WebIDL to extend the WebRTC 1.0 API to enable user agents to support scalable video coding (SVC).

Explainer: https://github.com/w3c/webrtc-svc/blob/master/explainer.md

Privacy considerations: https://w3c.github.io/webrtc-svc/#privacy-security

Repo: https://github.com/w3c/webrtc-svc/

Christine: We've been asked to provide review on this new spec. Details above. Before this meeting I reached out to Shivan (as next on the list and with knowledge of WebRTC) to ask him to take point on the review. He's quite busy, but has stepped up. Thank you.

Shivan: I haven't had a chance to look at this as yet, but will do so.

Christine: Has anyone else had an oppertunity to look at the spec or is familiar with the spec? Seeing no one, we don't have a deadline but we'd like to get it done so I'll put it on the agenda for our next call. Everyone else please have a look as well. Anything else on this agenda item? No.

#### 2. New WebTransport Working Group charter

Link:  https://www.w3.org/2020/06/proposed-webtransport-charter.html

Christine: There was a call for review on the webtransport charter. Has anyone been involved?

Brad: involved in the begining but stepped away now.

Wendy: WG proposed to coordinate web api with IETF work with QUIC.  Gives low level access to network communications so privacy review will be important.  Helpful that we're involved to make sure privacy considerations are a part of the structure of API.  Timeframe for spec is 2023 Q1, though first public working draft January 2021.

Nick: Is this a JS API for network communcations? like AJAX?

Brad: Similar to WebSockets.  Esp important considerations for CORS and port scanning.

Christine: PING will want to get considerations in early.  Would anyone like to volunteer to monitor work and keep PING up to date?

Brad: Could do review.

Christine: Review is important, thank you Brad. Is anyone willing to help monitor for the group?

Joey: Can help monitor.

#### 3. Self review: Security and Privacy Questionnaire

* [Latest published version](https://www.w3.org/TR/security-privacy-questionnaire/)
* [Editors' Draft](https://w3ctag.github.io/security-questionnaire/)
* [GitHub repository](https://github.com/w3ctag/security-questionnaire)

Christine: Pete and Tess have been doing a review of the document and updates.

Tess: This is a document TAG and PING work on together.  TAG requests that people proposing reviews look at this document.  Originally started by Mike West. Tess is editing from TAG side, Pete editiing from PING side.  Started a pass to reword/rework to clarify in last few weeks.  Document presumes a fair bit of knowledge, so trying to make it more approachable.  Don't want to lose nuance.  Addressing issues one at a time.  Inviting TAG and PING folks to review pull requests.  Links in notes.  PING folks encouraged to review and file issues, in particular what should the doc ask that it isn't.

Christine: Encourage new members especially to review the doc.  Feel free to reach out to Pete, Tess, Christine with more questions.  Thanks to Tess and Pete for leading this work.  This doc helps other WGs think about what they need to consider when developing specs.  Encourage other members to review.

#### 4. Privacy threat model

Christine: Pete is not here to lead (last minute absence). Jeffery is not here either.

Shaun: Next step was to get high level principles from Pete and Jeffery.  In call to discuss, the high level princincles were the missing part.

Christine: We could discuss high level principles now as we have time, but if people prefer, we can also do this offline.

Nick: Curious to hear what high level principles means.  Prior work was on threats.  Are high level princinples what the browser or doc provide?

Christine: Ad hoc meeting indicated these were privacy design principles, e.g. what are we trying to achieve.

Nick: Examples?

Christine: My understanding that Pete was hoping to make a start on the principles, but it appears he has not had the time as yet.  We will add this item to our next agenda, and we can continue the discussion in the interim on Slack in the #privacy-threat-model channel.

Kris: Understands 1p vs 3p thread model.  Concern 3p can be divided into 3p that invovled with just 1p concerns (e.g. help desk).  Concerned doc doesn't divide up 3ps and could make 3ps move into a 1p context.

(npdoty: I think if there are recommendations on how to provide protections/limitations for third-parties to guarantee that they’re only providing a service to the first party, that could be helpful)

Christine: Important that we discuss this issue.  Encourage getting in touch with Pete and Jeffrey

Wendell: In ad hoc meeting, discussion ranged from this was a measurable entropy type thing to the web be safe and free from manipulation.  Pushed away from "web be safe".  Privacy Thread model doc should characterize threats but not necessarily prevent/mitigate.  Example was there exists powerful entities that can do larger things (e.g. walled gardens).  This was a browser focused; browser should have a viewpoint if these were problems, and maybe just identify them as bad but need future attention/tech to solve.  There was a call at the end to rework the table to lay this out.  Jeffery was going to take a shot.  Layering from math to layer 9/10.

Christine: Current draft mainly focuses on what could be fixed now.  My recollection from the discussion is that there are three situations we want the doc to cover: what can fix now, going forward and can't fix now (but maybe in the future).  Wide ranging discussion.  Needs work in lots of places; great chance to get the doc into good shape.

Brad: WRT Kris question, doc is laying out capability set for each.  In terms of it treating them differently, e.g. encouraging 3p to run in 1p context, then this is a bug.  Providing services 1p is important, composability, but shouldn't be for leaking 1p data out.  Identifying what powers of 3p and 1p is important and should be outlined.

Kris: Missed meeting, will try and read notes.

#### 5. New Web developments and privacy considerations

##### CTA CMCD Task Force draft specification

Spec: https://docs.google.com/document/d/1S_Dj_aHVnbWnjeJYMfLU1D6tZoqYdgHT1stfznBvxig/

Security and Privacy Questionnaire: https://github.com/cta-wave/common-media-client-data/issues/60

Github issues and feedback: https://github.com/cta-wave/common-media-client-data/issues

Christine: Consumer tech association invited us to do privacy review of their spec. It is not a W3C spec requiring review, but we still chartered to improve privacy on Web so the CTA is here as our guest.

Mike Bergman (CTA): Thank you for inviting us.  CTA you might know from the CES computer/tech gadget conference.  CTA is ANSI accreddited standards body.  WAVE for streaming video.  CTA notes W3C help for streaming and HTML apis.  Device API and encoding specs.  Common Media data group, when click on video, download JS media player, fetches media chunks, plays them, generates performance metrics.  Metrics can indicate local issues (e.g. geo-local performance).  Challeng is what data can be exposed from media player within browser, to help debug issues with streaming.  Exposing data from client can be problematic.  Privacy was kept in mind when considering what data to expose, e.g. device ID was never an option.  Anonymized QOS info was the goal.  Privacy risk considered.  Group did a good job, but in retrospect, privacy recommendations, the threats were not documented, currently being re-reviewed currently.  Talking to PING.  Proposing API to doc these exposed performance metrics, including privacy considerations, need to doc thos considerations.  Inviting comments and review.

Nick: Thank you for background.  As background for reviewers, talking about who would implement is helpful.  Initial review indicates this would be used by publishers of JS players on sites.  This JS can use existing functionality to send back data; this standard describes what can be sent back?

Mike: Yes, intended users are JS player writers (e.g. NetFlix, JW).  CDN is who uses data.  Doc contains info about how they use the data.  Doc describes prefetch of media chunks.  Exposing this prefetch info exposes what content is being played.  Better to not expose what's being played.  When insecure content requested, can be viewed, this problem is not addressed by this doc.

Nick:  PING has reviewed things like this before that are standardizing communication using existing functionality.  Limit to how much we can provide utility because not new functionality.  A known surface to some degree.  Lots of data that can be communicated.

Mike: Different for data to be exposed by many different implementations.  When standardizing, the centralizing of format makes it somewhat easier to be found.

Christine:  It sounds like CTA found the existing version of the Self Review: Security and Privacy Questionnare useful and that you view data minimization as important. We are looking for feedback from questionnare and I am curious to know what kind of mitigations you've put in place to minimize data expose.

Mike: Will kick off thread in own discussions for questionnare feedback.  Looked at privacy and security, amplification of API for DDoS attacks.  Some discussion of reducing fingerprinting surface and amplification attacks.  PII like IP address are intentionally not carried by spec.  Section 5 rewrite under review.  Considerations of threats: eavestropper, on client, on server (CDN).  Section 5 includes things thought to be important at the time, more coming.

Wendell: Advertising space doing a lot of video work.  One of the challenges is knowing about devices (what/how many).  This talks about watching movies, less so commercials.  Some media moving to more like this spec.  Commercial challenges happen when ads show, to comply with trade records etc.  Your spec removes a lot of tracking vectors from protocol.  There will be other ways of recovering that info (if played, how many times, progress).  Thoughts on interfacing with that?

Mike: Would like followup discussions.  Audience measurements of ads.  QOS being developed for player oriented details, goes to content source not CDN.  This is standardization of existing things.  Answers if ad played etc.  This doc being discussed is more privacy oriented.  Streamig video alliance?

Wendell: Short form video only begining to interact with that world.  In the press everyday for text web tracking removal for transparency consent.  To get it reformated with hard privacy guarantees.  Verizon looking at other areas that have solved these problems.  Video content creators consider their content very important.  Privacy not necessarily as concerned.  Audience selling does a lot of the tracking.  Looking to meet up to discus these problems both technical and streaming (making sure content doesn't escape, and audience measurement).

Mike: Happy to discuss

Christine: Thank you Mike, esp for your considertion of privacy.  Helpful to hear about it and to hear that the questionnaire is valuable. Even though not a W3C spec, if we can help, encourage you to take a look at the CTA proposal to help them with privacy considerations.  

Mike: will send along next version.  Thanks everyone.

#### 6. AOB

Nick: TC39, the folks that standardize JS versions, asking about privacy of i18n for new versions of JS.

https://github.com/tc39/ecma402/issues/443

Nick: Imporant to consider.  Will see about inviting them to talk about it.




