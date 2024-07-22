# Privacy Interest Group (PING) meeting, 18 July 2024

## Attendees 
- Pete Snyder (Brave)
- Nick Doty (CDT)
- Christine Runnegar (co-chair, invited expert)
- Philippe Le Hegaret (W3C)
- Alexis Menard (Intel)
- Bartosz Niemczura (Meta)
- Joey Stanford (invited expert) - Tardy

Apologies: 
  
Chair: Chair

Scribe: Christine

## Agenda

### 1. Introductions, Code of Conduct
https://www.w3.org/policies/code-of-conduct/ 

Nick: Reminder to read code and read advice on what to do if you made a mistake

### 2. Privacy reviews

#### a. Vibration API - https://github.com/w3cping/privacy-request/issues/138 (Pete)

Pete: no privacy concerns, because not reliable way to get info out of API - serious problems with spec, should have more revisions - will probably create an issue (but not privacy), some text seems contradictory (re: instruction to vibrate) - boolean issues, could produce both true and false - significant technical concerns with spec - review complete

(Discussion of Mozilla objection to spec and whether issues raised by Pete are the same, Philippe is not sure if they are)

Nick: risks about cross-device communication - if make sound, can signal to another device, low fidelty communication, but significant and annoying to users

Pete: share that concern re: annoyance, but re: data exfiltration is worth noting, still un-permissioned, is another channel for this

Philippe: spec already means that, do you want more detail in spec?

Nick: more .. what should we do about it, not just note privacy risk

Pete: spec says user agent can ignore, seems abidaction rather than taking responsibility, another reason there are problems with the spec, agree with you Nick, don't think is restricted to top level

Philippe: what about a lack of integrations with permissions

Pete: should be, two other technical concerns, asycn behaviour with sycn api, difficult to put a permission on that

Philippe: if we assume work moves forward, what do we say from a privacy perspective, especially the lack of integration with permissions ?

Pete: not concerned re: privacy, still unpermissioned way to play audio already, but permission is not attached to privacy concern for me, maybe permission for audio makes sense, but does not seem to be on the table at this point

Nick: permission could enable some of the mitigations, does a user want or not want, to mitigate concerns

Philippe: wouldn't we expect features like this to be behind permissions?

Pete: would deep re-working to add permission

Philippe: we could still stay we expect, up to the WG to fix api to integrate with permissions

Pete: I don't think that is necessary, audio is unpermissioned

Philippe: surprised with that approach, from a privacy perspective

Christine: we also get the response from WGs that it's already done differently and we push back on that.

Pete: in my privacy review, seems an odd new line to draw, but don't feel strongly

Nick: we did that in ambient light

Pete: that was read, if could read that would be very concerning, in common case you can't do that here

Bartosz: it's more about generating the signal than reading the signal, gyroscope does have a permission, microphone does have a permission

Pete: also legacy

Philippe: we should tell them to make sure permission is doing the right thing

Pete: permission is good for capacity to annoy people, trying to distinguish from privacy concerns

Philippe: annoying by too many questions to users, but I thought we dealt with in permission framework, it would be bad if not doing

Nick: might situation again re: audio, web pages started playing audio and many browsers provide a way to mute, parallel permission system, likely that a browser is going to do, maybe suggest an async api and use permissions - that is the advice we have given, don't ask for permission if you don't have to

Philippe: push to permissions framework

Nick: I was getting to the same point

Philippe: api needs to be able to handle the situation where the user mutes

Pete: we are largely agreeing, could just note that it could be useful for permission integration, even if we disagree about whether it's strictly for privacy reasons. or for both privacy and non-privacy reasons.

Christine: in the privacy principles framework, the sort of annoying behavior is considered an imposition on user privacy. so I think we can say for privacy reasons.

Pete: fine with saying both

Nick: enough agreement, let's continue

#### b. Device Posture API - https://github.com/w3cping/privacy-request/issues/136 (Pete)

Pete: broad overview, effectively is the device folded or not api - preamble is a little confusing, but doesn't not deal with orientation - not concerning in general, but a couple of notes, in privacy considerations there is a fingerprint aspect, but wrong to use pointer api as analogy, closer to ephemeral fingerprinting (where the signal is fired simultaneously in multiple documents), will make a suggestion - 

Pete: some disagreement re: frames in WG, should restrict to only top level context unless they come up with a reasonanable justification

Pete: should get rid of null option, everything except folded device should say continuous

Alexis: the name of spec is because two postures, continuous and folded, but now we know there will be more postures in the future, used to have a third posture but removed because no use cases, like folded over (tent mode), devices expected with more than one mode, keyboards docking or not is important for figuring out whether folded or not, really about how the device is used, some modes are not yet exposed to the Web

Alexis: re: continous posture and null is an oversight and happy to clean up the spec accordingly, thank you

Alexis: re: iframe - I am the implementer - posture in JavaS and can use through media query iframe - no way to restrict in second mode, no permission policies, never came across a spec that restricts in iframe, question for you, unchartered territory, no implementation I could find to restrict media query iframe

Pete: I can't think of any media queries restricted to particular frames but we could do it

Alexis: level of fingerpinting is low, so what is the benefit, does not add a lot entropy, lots of foldable devices now (millions of devices), you can fingerprint a foldable device via screen resolution changing, you can fingerprint a foldable without the api today, don't see value doing something not done before

Pete: for concrete example, two frames blocking from learning from each other, but you could learn that 

Alexis: could already do that another way, if you tell me we have to do that, a lot of work

Pete: take your point, if you can already do this, why are we adding an api

Alexis: can do (motivated actors), but convenience to developers

Pete: is it useful for frames to have this info, maybe and another is we might as well give it to them anayway, so we should give it to them

Alexis: game emulator is an example of use, and so don't play ads in the fold (use cases), if we block it we are going to be told it is needed

Pete: if useful, makes sense to provide it, but not clear in spec that it was useful

Alexis: I started the conversation as I was implementing and received feedback of need from others, including buttons in the fold

Pete: then take your point, sounds like useful so makes sense to leave in, but fix that in spec

Alexis: in CSS, discussing exposure of ? to iframe; re: pointer events, I read that section, what do you mean?

Pete: two categories of fingerprinting concern - (a) semi-identifable identifer over time and contexts (b) not very identifying or stable but viewable across a bunch of contexts - this seems to be the second category

Alexis: yes, second

Pete: different from pointer api example

Alexis: remove section?

Pete: clarify section about re: rate limiting, not clear what privacy benefit comes from

Alexis: from when spec was exposing fold angle, in theory the way you open the device, rate of change could be used to figure out what type of device - so high level, requires user's action to change angle of device, so risk low, so maybe remove

Pete: I think fine to remove

Alexis: I think good idea to remove because we are not doing fold angle and requires user interaction, I will remove

Philippe: two minor points, thanks for attending, re: pointer API, pointer in CSS or pointer events API - which one do you mean

Alexis: I will fix that

Philippe: nul is never returned, only web vibrate and want to delete using web driver - may want to clean that up - nul value is not exposed to the api

Alexis: I forgot about that integration of web driver .. need to address

Nick: re: frames issue - fenced frame example might be relevant, technology in progress, can we have a frame that does not know about the external page (e.g. advertising), we might note we don't want folded status to be revealed to those embedded contexts, we should be thinking ahead about how to do protection even if not implementing today

Alexis: only through permission policy, right? (e.g. geolcation), so we would have to get new permissions - can't restrict CSS aspect of it, they would have to do a lot of work to figure out

Nick: start thinking now, fenced frame would not use permissions framework

Alexis: if want to integrate with permissions framework, not big changes needed, would add a new section in the spec for the api in the future, we can take this offline

Nick: does someone want to CSS? I can do that

Philippe: you mentioned permissions framework

Alexis: currently not, should we? now it is pointless, even if restrict in JavaScript can do in CSS, would make implementation complicated without benefit for users, huge work, is it sufficient risk to block spec to wait for CSS, or we say wait and update with permissions framework - in my opinion, the risk is low and can add later

Philippe: fix with CSS first

Alexis: when CSS is sorted out, happy to go back and make updates. The discussion is really about risk.
	
#### c. WCAG Guidance - https://github.com/w3cping/privacy-request/issues/139 (Christine)

Christine: Applies web accessibility guidelines to non-web tech. The group is also working on a v3, but it'll be a while. No privacy concerns, but I suggest the following text to the group.  Feedback is welcome
	
> This Working Group Note does not introduce any new privacy considerations." the following text: "However, when implementing the WCAG 2.2 guidelines and success criteria in the context of non Web information and communication technologies, information about users' accessibility needs or preferences may be exposed and should be protected from disclosure and misuse in the non Web context. Further, when implementing the guidelines and success criteria, choose implementations that reduce the potential for fingerprinting or other identification and tracking of users, and only collect the data necessary to enable the accessibility features."

Support to send that response

#### d. Pointer events API - https://github.com/w3cping/privacy-request/issues/134 (TBD)

Nick: reviewer?

Pete: Jeffrey, but hasn't been able to undertake the review as yet

### 3. Verifiable credentials / Controller Documents (Nick)

Nick: controller documents spec, has some concepts from DID and other VC specs, no new text, very abstract, it has potential to be more specific, but not enough examples to properly understand how it is intended to be used, some guidance in privacy considerations which hints that you could add extra data, but that doesn't seem to be the case - will be providing some feedback - others have looked at or experience with it?

Nick will reply with feedback on uncertainty, welcome additional viewpoints.

### 4. Security Interest Group

Nick: Has that been announced?

Philippe: still in horizontal review, comments?

https://w3c.github.io/charter-drafts/2024/ig-security.html

### 5. Update regarding Privacy WG (Philippe)

Philippe: I have a draft report, received comments that requires legal review, hope to send to Council this week, but it may take longer

### 6. AOB

adjourned.