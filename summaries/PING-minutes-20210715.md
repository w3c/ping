# Privacy Interest Group meeting (15 July 2021)

## Attendees 

* Peter Snyder (PING Co-Chair, Brave Software)
* Christine Runnegar (Co-chair, invited expert) (part)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C/MIT)
* Nick Doty
* Sean Harrison (Google)
* Theodore Olsauskas-Warren (Google)
* Kris Shrishak (invited expert)
* Matthew Finkel (Tor)
* Brad Rodriguez (Magnite)
* Wendell Baker (Verizon Media)
* Konrad Dzwinel (DuckDuckGo)
* Peter Lowe
* Eric Mwobobia (ARTICLE19) 
* James Rosewell (51Degrees)

Scribe: Sean Harrison

### 1. Privacy reviews 

## a. Media Stream Image Capture 

Spec: https://w3c.github.io/mediacapture-image/

Reviewer: Peter Snyder

Issues:
* https://github.com/w3c/mediacapture-image/issues/283
* https://github.com/w3c/mediacapture-image/issues/284
* https://github.com/w3c/mediacapture-image/issues/285
* https://github.com/w3c/mediacapture-image/issues/286

[Peter] You have a media stream you requested somewhere else (webcam, etc.) and would like to grab frames out of that stream, of such size and with other information the camera might have. Found 3 non-trivial concerns, 1 kina trivial, 2 trivial. First is mentioned in privacy and security section and I grab an image out of the media stream and has header information that they might not want to share (accept headers, geolocation, etc.) just mentioning it here is insufficient. Should be dealt in the mandatory part of the spec, if the origin doesn’t already have geolocation headers must be stripped. I'm not confident this is the right suggestion, but I think you should need additional permissions to get headers other than camera, it's the first issue I'll create.

[Sam] What layer is this at. Capture an image coming into a zoom feed, or a web application wants to capture itself?

[Peter] Already getting data off the webcam and would like individual frames, want this image from my twitch stream or something

[Sam] Image you are receiving or sending?

[Peter] I don't know. As long as you have a media stream track object you can grab it.

[Sam] I like the idea of sanitizing, this isn't so much stripping but not adding additional info

[Peter] depends on the hardware, but more or less

[Sam] I agree this should be normative

[Nick] Why would any header metadata ever be added

[Peter] I don't know, but since it is in the spec, I assume there is some use case that was adding this information

[Nick] Since the site already has the media stream. There could be a camera doing video that could do a shutter and take a nice high-quality picture? And that picture could have all sorts of photo metadata (exposure, etc.)

[Peter] From a large distance understanding that data is not normally available in codec metadata, as it is in images, but the spec authors may say that is it. I will at least make sure the question is asked.

[Theo] This came through internal review process. This is based on additional capabilities of the camera, such as pan-tilt-zoom. This is in the same bucket of idea, so you could set the aperture exposure etc. of the camera. Our idea was to put this all behind the PTZ permission to give full control of the camera to allow specifics to be added to the photo.

[Peter] If you have insight into this, is it your understanding that chrome users or internet users have an understanding that users understand that camera is included with headers?

[Theo] No users don't have that mental model, Can we bundle this up as a set of capabilities, camera and super camera, but I think geolocation is an interesting thing to pull out of this.

[Peter] Alternatively the spec could say no metadata

[Sam] Or default to no metadata

[Theo] I think this is against the spec, it won't work for photographers, etc.

[Peter] I'm not entirely familiar with this use case so I will raise it with the spec authors.

[Peter] Second issue, allowing the site to request the cameras capabilities, this is a fingerprinting surface. You already have a fair bit of info from the stream data on the camera. Need to check on the permissions and the capabilities. The additional fingerprinting without distinct user gesture seems problematic, red-eye correction etc.

[Theo] On the tracking capabilities, the properties of the camera are quite fingerprintable. It wasn't clear to me if site A could set the aperture value to a known value, could site B read it to get cross site info from it.

[Peter] It doesn't appear to be settable configuration data but default hardware properties of the device.

[Theo] I think we have had different reads of the spec, so we should clarify this

[Matt] The main question I have is whether the primary use case of this spec is on mobile devices (verses desktop/laptop use cases)?

[Theo] No insight into this aspect

[Peter] We will follow up later. 3rd issue: A whole bunch of privacy concerns/meta concern through media control. It is partially solved through web activation, but there is still a lot that appears to be incompatible with the direction the web is going. The WG doesn't feel like they can change the status quo but would like to change things going forward to require more user interaction for getUserMedia. This is locking the web more into the getUserMedia approach, this doesn't seem great to further entrench this known privacy issue. I thought there was previous agreement on this spec going forward, but we appear to be doubling down instead. And how to reconcile this previous review with where we are going. I can very briefly go over these issues if interested, but I don't think there is any controversy there.

[Peter] Last sensitive concern I had around user activation for grabbing frames from the stream. Assuming my understanding that this is meant to grab the frames and not the configuration, if the site grabs enough frames it could learn about the configuration that way, if there aren't any speed bumps (user gesture, etc.). We should at least learn the tradeoffs for not needing user activation to grab frames of the stream. 

[Nick] This API shouldn't provide access to current settings (focus), but after a photo is taken the values of focus should be reset to default to prevent a side channel to pass data.

[Peter] Can you get the current configuration

[Nick] No, but you can set the current configuration

[Peter] This should be explicit in the text that is can influence the state of the device

[Nick] Sometimes this is the physical configuration of the device (zoom) other times it is not

[Sam] How much did you look at their responses to the questionnaire?

[Peter] Not at all just the spec

[Sam] It looks like they didn't do a sufficient privacy analysis.  I wonder if we should look at their responses to the questionnaire also.  https://github.com/w3c/mediacapture-image/blob/main/security-privacy-questionnaire.md

[Peter] I'll go back and look, I didn't read it, as I see it as a way to help the spec writers more than us

[Peter] This redefines bits of the spec, it should just link to things instead of redefining them. "Reading bits of the spec" I am not sure what is intended there or how those separate values will reduce fingerprinting surface. It should be removed if it is confusing or redefining things. Neither of these things are core to the functionality. Once these issues are added, with all the additional comments, I will come back and add them here.

## b. Performance Timeline and User Timing

Specs:
https://w3c.github.io/performance-timeline/
https://w3c.github.io/user-timing/

Reviewer: Konrad Dzwinel

[Konrad] I worked on these together with ??, I want to split credit. First is performance timeline leveled tool, performance timeline provides a list of performance events that can be queried, it is high level, does not give exact details, but defines how to query them, store them, etc. I was reviewing them as a whole thing as the V1 spec is broken, but there was a handy diff doc. Performance observer allows access to these events. This API extends this to webworkers, some changes are inherited from before. V2, which may or may not be important, has been shipped for some time now, it is universally enabled in browsers. Went through the spec and saw no red flags, but there are some changes we would like to discuss here. there is a start time on these events, it is rather precise to allow precise measurement of performance, these timers are a bit of a red flag nowadays, and the spec mentions it as an issue, but requires a different, high level resolution timer spec, to handle it. Is this okay to point to a different spec, or should the concerns be copied over at a high level.

[Peter] Whether or not copied over, it should at least be explicitly referenced for completeness.

[Konrad] Maybe some concerns should at least be listed at a high level

[Peter] The text pointed to by the link could change, so yea they should at least copy over the high level.

[Matt] Is this API accessible by third parties? Or is that a decision left to implementors?

[Konrad] Depends on what you mean by 3P, if there is a 3P script on the page it can access it like 1P. 

[Konrad] The second minor concern is that the script can be accessed by 3P script on the page, which could reveal some info. If the 3P script is loaded by the 1P. Performance API gives some info into all requests being made by the page, some custom points can also be added to the timeline which can reveal some aspect of the internal script (cryptographic, etc.). 3P can see this and 1P might not be aware that they are revealing some of this information to 3P so this should be restricted. It is mentioned in the second spec I'm talking about, but this applies to all performance timeline APIs and should be surfaced at the top level, I can clarify.

[Peter] How do you see this interacting with a previous issue, that it is too easy to give this away? The easier it is to give away the more these concerns bite

[Konrad] Not only is this easier, it enables something not possible before, if a 1P script is running the 3P script can peer into the closure, but now if the 1P script adds performance marks to their scripts the 3P can learn about it. This allow applies to requests, if the 1P is making requests the 3P can learn something about these requests, which is not something that could have been done previously

[Nick] Is this done only if the 1P adds these markers or can 3P learn this info regardless

[Konrad] For requests the 3P will learn this regardless, but the performance markers have to be added in the 1P script for the information to be leaked but this should be explicitly called out.

[Konrad] The last one is that spec avoids the word origin in the entire spec, it lets all the APIs, all the subspecs, solve the cross-origin problem themselves. For example the resource API has this carveout for it to be available at the top level for this API. ?? API has this cross origin problem, measuring how long an i-frame is rendering. They kind of specify it but not really. The top spec should provide guidance on how this should be handled by sub-specs, with the default that no information should be leaked cross-origin. The spec is blurry on these cross origin-issues, they could be more concrete. I don't know if 1 spec should be telling other specs that build on top of its standard behavior.

[Peter] The spec being proposed defines the world how it is and shouldn't make it worse for other specs

[Konrad] In summary we have these 3 minor issues, and we will have a discussion about them, thankfully not show stoppers since it has been shipping for a long time. We covered resource timing in the previous meeting a year ago, now I would like to cover user timing. It allows the user to add custom points to the timeline to measure the differences between 2 points on the timeline. Level 3 makes two changes over level 2, it allows the inclusion of a bit more custom data, including more metadata about the event. They can add points on the timeline with a custom timestamp. Previously it added the timestamp at the current time the API was called. This makes it easier to manipulate the timeline, that's pretty much it. These are simple additions over level 2 and not problematic. This API mentions the risk that 3P scripts will learn something from 1P scripts, we would like to elevate this to the original performance timeline API rather than a subspec.

[Matt] Are there any restrictions on an embedded (third-party) frame obtaining performance measurements of a frame it embeds (three levels, in total)? Something along the line of a third-party having a side-channel to learn information about the first party?

[Konrad] This is not well specified, the performance timeline spec the word origin is not mentioned once, each is left to the individual APIs to figure it out. User timing is restricted to the current frame, resource timing creates a 3P carve out that is problematic, ?? timing is suspicious, we only took a quick look at it. There is some chance for side channel attacks, but not in these 2 specific specs.

[Peter] What happens if I set the timeline, my mental model is analogous into the timeline I see in dev tools, there are tools to set these to persist across frames or navigations. Can this API be used to persist things?

[Konrad] No

[Peter] I mean if the users ask timing info to persist across navigations in dev tools would it persist across navigations?

[Konrad] If the page is reloaded or navigated away it should be wiped

[Peter] If I hit the persist this button in dev tools, would these marks persist across navigations

[Konrad] I haven't thought of this edge case, but it is relying on dev tools in a browser, but this could be a bug

[Peter] Should look at making sure this is cleared across navigations, even with dev tools?

[Konrad] We can mention this to the spec authors

[Peter] If it feels redundant and not necessary we can not bring it up

[Konrad] Asking developers to double check this makes sense to me

[Peter] Please drop any new issues you file into the agenda

## c. HTML Review Draft (requested)

Spec: https://html.spec.whatwg.org/review-drafts/2021-01/

[Peter] We have been asked to review this by WhatWG, it is that time when we review the HTML draft for privacy issues. Is there anyone interested/willing to review this? Please send a message to me if you are willing to pick it up.

[Nick] I am interested, but it might be good to split up with people, since it is a large spec.

[Peter] I can co-review with you

[Peter Lowe] I would be interested in trying to help out with the review

[Peter] The 3 of us can coordinate the review

## AOB

[Sam] The Federated ID community group is starting up, for anyone interested https://www.w3.org/community/fed-id/

[Matt] Did we hear anything from the UK?

[Wendy] Did any regulators get in touch with me, no

[James] I have spoken to them and they will get back to you


