# Privacy Interest Group meeting (16 July 2020)

## Attendees 

* Christine Runnegar (co-chair)
* Pete Snyder (co-chair, Brave)
* Sam Weiler (W3C/MIT)
* Sean Harrison (Google)
* Paul Jensen (Google)
* Irene Knapp
* Wendy Seltzer (W3C)
* Dave Harbage (DuckDuckGo)
* Eric Mwobobia (ARTICLE19) 
* Nick Doty (Berkeley)
* Wendell Baker (Verizon Media)
* Scott Low (Microsoft)
* Michael Kleber (Google)
* Chris Wilson (Google)
* Shaun Gilmore (Apple)
* Terri Oda (Intel)
* Mingzhe Li (Akamai)
* Melanie Richards (Microsoft)
* Lisa LeVasseur (Me2B Alliance)
* Joey Salazar (ARTICLE 19)
* Erik Anderson (Microsoft)
* Konrad Dzwinel (DuckDuckGo)
* Tanvi Vyas (Mozilla)

Scribe: Wendy Seltzer and Sam Weiler

Note: Today we had some issues with Cryptpad - a few people noted forked Cryptpad page

## 1. Privacy review request from the Devices and Sensors WG - Geolocation API

Link to spec: https://w3c.github.io/geolocation-api/

This specification defines an API that provides scripted access to geographical location information associated with the hosting device. It is now maintained by the Devices and Sensors WG, and contains the following substantive changes since the last REC:

 - Now Controlled by feature policy
 - Fixed confusion around callback interfaces not being an EventHandler
 - Only expose the API in SecureContexts
 - Renamed the interfaces and dictionaries + removal of [NoInterfaceObject] + [SameObject] annotation on geolocation attribute

(Note: the DAS WG is also working on a new API based on the Generic Sensor API: https://w3c.github.io/geolocation-sensor/ )

Link to the Security and privacy considerations section: https://w3c.github.io/geolocation-api/#security

WG has asked that we please file issues at https://github.com/w3c/geolocation-api/issueshr's very passionate

--

Irene: I did a read-through, did not identify issues beyond the two GH issues already filed. Those two are important and should prompt changes. Issues 47 and 48 in GH repo.

[47](https://github.com/w3c/geolocation-api/issues/47) Lifetime should be limited because location info is sensitive, users may not expect persistence. Discussion whether this should be specific to this or generic. I can see that geo info might be more prone to abuse than others; also viewpoint that generic permissions mechanism is valuable, and geo info is particiularly sensitive in that regard. 

[48](https://github.com/w3c/geolocation-api/issues/48)  concern re user activation as gating requirement, so tracker embedded in page could activate geoloc, ideally.  Restrict to frames visible to user, i.e. if it's a map, that user can see the map. 

Pete: I filed another issue, not privacy-specific. Spec says sites should be able to control level of resolution. It's not currently well specified. [49](https://github.com/w3c/geolocation-api/issues/49) 

Irene: yes, that's a weird mechanism. Agree it's not privacy-specific. 

Nick: This is a revision of a previous API. There was a time or spec that provided meaningful civic address info. I think the implementers dropped it because complicated, not widely used. It has potential advantages for meaningful interactions with sites, e.g., show me stores in my city, without learning where I am in my house. Has potential to be useful, don't know whether it's being discussed again. This other flag re high accuracy was mostly about power usage. Semantic resolution was dropped.

Pete: Seems like something spec authors should be aware of. And spec should be made internally consistent, not call out to something that no longer exists. 

Nick: anyone from the group here who could speak to the requirement section re specifying required accuracy? 

Pete: don't see anyone from the group here, but can invite them to next call if no objection. No objection. 

Pete: Re user-activation (48), usually requesting permission is gated on user gesture. Automatic update. Resolving the request is gated on visibility. Concern that it's easy to be "visible" in browser sense, without being seen necessarily by user. Hence requirement for user gesture. Not clear why I'd want a frame to get info on me without any interaction. 

Nick: Other APIs where browsers have used paradigm of interaction with frame?

Pete: I think WebAudio API does. and Permissions API. Storage Access API

Nick: useful to point toward other cases. If there's a giant iframe with map, do I need to tap the map?

Pete: and permissions can last beyond the lifetime of user activation

Irene: Seems it should require an activation each time; so, can't be in the background without user noticing. Other issue of lifetime goes hand-in-hand

Chris: Web Audio permissions. Accounted for in the spec for autoplay, but not specified there.  In practice, has the user interacted with the site often enough that they'd want autoplay. Otherwise suspended.

Pete: Web Audio API?

Chris: If you create Audio in non-autoplay context, starts suspended. 

Nick: User activation. You know you went to a particular page, whereas your location is being requested by an element in the page, could be another origin. One key concern is knowing who is asking you for location. You must include host component of URL. Not clear what should happen if there's an embedded iframe. Should we be asking questions or providing guidance there?

Irene: Excellent question. We should have a concrete recommendation. Providers can easily design their content to run with third-party or first-party cooperation. We should document the decision. 

Pete: say I go to e.g. GrubHub, a Yahoo map is there. I want to see my food delivery in progress. but shouldn't necessarily have location permission next time I open GrubHub or Yahoo. 

Irene: You can't technically prevent Yahoo from getting info while you're on the GrubHub website. But you could link it, so Y doesn't get location when you visit DoorDash if they also contract there. 

Nick: it might be meaningful, lots of iframes without script tag. You don't want the map embedded on a completely different website to have permission in new context.  Consider origin-pair concept. The paired origin is the permission, not the provider anywhere. 

Kleber: Agree with Irene. A 3rd party script that creates an iframe is far more common than HTML embedding iframe. Best way of future-proofing. If getting permission in 1st party context is necessary, 3d parties will be able to do so. 

Irene: In practice not possible to make a 1st/3d pty distinction stick. I think the context-pair concept is a good one here. 

( npdoty: we'd be giving up quite a lot if we completely give up on the distinction of scripts running in a first party context and all embedded objects. )

Pete: lots of places we have distinctions between 1st and 3rd parties on the Web. significant loss if we start collapsing those. appreciate the input. 

Konrad: we want to limit 3rd party access to the context in which it was granted, right? 

Kleber: still useful to distinguish 1st/3rd parties and their permissions; just suggesting that contractual and business operations also matters. There are many 3rd parties who show up only in iframes without any relation to 1st party, and useful to keep distinctions. 

## 2. Discussing privacy review process

Pete: ways to make it easier/inviting to get involved in privacy reviews and discussion of privacy issues. what makes it welcoming or unwelcoming? have heard several comments from people who weren't sure about how to get involved.

Wendell: there is a high bar to understand what's allowed or expected. for people who don't spend a lot of time involved in W3C-related work (applies to many w3c public groups). it is work to conduct a new privacy review, to read a spec and learn about a new area and understand how a WG is working, and write up explanations.

Pete: both the amount of work/technical barriers and tone/tenor of conversation on individual issues

Sean Harrison: barrier of amount of knowledge/background needed. listening for now and hope to contribute later

npdoty: I have a good amount of background knowledge, but even w/ my understanding, sometimes privacy issues and reviews can become contentious, which drains my energy and involvement. Sometime privacy issues are not received well from groups.

Christine: some privacy experts may not have expertise about W3C standards. encourage not to be disillusioned by in-depth technical discussions. you have a lot of experience about potential privacy vulnerabilities and implications. helpful when we have discussions not just to discuss the technical details but also what functionality the spec is trying to achieve and a higher-level overview of the spec design and the potential privacy risks. 

Wendell: +1 to npdoty, privacy work can sometimes be interpreted as negative, have to work on explaining the positive implications.

Pete: +1, can be emotionally draining. move horizontal reviews earlier in the process, when it's easier to have a more collaborative tone, lower stakes about making changes

( npdoty: +1, good idea )

Pete: happy to be a sounding board, or use Slack channel for intro/beginner questions, checks in a Slack conversation rather than immediately entering into a GitHub issue. chairs or others with more experience can be volunteer messengers to pass on issues if others don't want to get involved in controversial discussion.

Christine: could set aside time on calls for new groups to come and meet and discuss what their group is working on, establish a relationship. could get discussion going earlier.

Wendell: panel session at USENIX’s Enigma 2020 with representatives from browser privacy teams to discuss visions. venues for expressing vision and more wide-open ideas could be helpful/encouraging.

Pete: will provide side channel on Slack. welcome any private messages too.

## 3. W3C Horizontal Review process (update)

Pete: ongoing discussion about horizontal review in W3C Process. PING is one of several hr groups. should it be more formalized? process or just self-help resources?

Weiler: discussion about how much requirements from horizontal review to put into the formal process. we do want to require groups to ask for horizontal review before going to Candidate Recommendation. not sure if FPWD would be a trigger, or which horizontal review groups, or if groups need to have completed self-review or include privacy/security considerations section. the end goal: groups will be required to show that they asked for horizontal review. I've suggested less specifics in the Process because these reviews have been changing over time.

welcome input at the Process CG: 
https://github.com/w3c/w3process/issues/130

Pete: process can be dry, but really gets to the role that reviews play in the process of developing a recommendation

## 4. Privacy threat model (update)

Pete: several issues and PRs being discussed on the privacy threat model (threats, goal of the document, how to structure). still a need for more involvement, and doesn't require lots of technical detail. input needed on the level of trust on the Web and guarantees to provide for users, not just details of Web architecture.

Wendell: need smaller group discussion for privacy threat model. discussion of aspirational values, but also not clear how everything would be measurable or achievable. back and forth needed in those smaller conversations, 1x/month e.g.

Pete: will follow up about a time to hold another one of those.

## 5. New Web developments and privacy considerations

other topics we're watching on web privacy?

(Note: no items discussed today)

## 6. Web Audio

Report on issues filed v. Web Audio: of the three, one has been resolved, and we have paths forward on the other two.

Weiler: resolved one issue and have a path for the others. thank you chris! on one, working on documentation rather than a technical fix. very pleased. re how to work positively, we had a lot of pushback, and we managed to understand each other.

cwilso: good example of how we need to get understanding both of the technical details of the particular WG and the details of the privacy issues.


