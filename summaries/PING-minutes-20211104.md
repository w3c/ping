# Privacy Interest Group meeting (4 November 2021)

## Attendees 

* Christine Runnegar (PING co-chair)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C/MIT)
* Pete Synder (Brave, PING co-chair)
* Aram Zucker-Scharff (The Washington Post)
* Theodore Olsauskas-Warren (Google)
* Wendell Baker (Yahoo)
* Kris Shrishak (Invited Expert)
* Jeffrey Yasskin (Google Chrome)
* Nick Doty (CDT)
* Joey Salazar
* Eric Mwobobia (Article 19)
* Michael Kleber (Google Chrome)
* Sean Harrison (Google)

Scribe:  Sam

## 1. TPAC 2021

Pete: today we're reviewing TPAC

#### New and related CGs

[Notes & recordings from breakouts](https://www.w3.org/2021/10/TPAC/breakouts.html)

* [Anti Fraud Community Group](https://www.w3.org/community/antifraud/)
* [Private Advertising Technology Community Group](https://www.w3.org/community/patcg/): [minutes of first meeting](https://www.w3.org/2021/10/29-patcg-minutes.html)
* [Federated Identity Community Group](https://www.w3.org/community/fed-id/)

#### Breakout Week (18 October 2021 - 21 October 2021)

* Mon, 18 Oct Anti-Fraud for the Web 4:00 PM-5:00 PM UTC [minutes of breakout](https://github.com/WICG/trust-token-api/blob/main/meetings/tpac2021-antifraud-breakout.md)
* Tues, 19 Oct WebAppSec WG (at its normal time) 6:00 PM-7:00 PM UTC
* Wed, 20 Oct Cross-Device Security (caBLE) 2:00 PM-3:00 PM UTC
* Thurs, 21 Oct Federated ID  2:00 PM-3:00 PM UTC
* Thurs, 21 Oct Upgrade Privacy Boundary Solely Defined by Registerable Domains 2:00 PM-3:00 PM UTC
* Thurs, 21 Oct The state of browser storage partitioning 3:00 PM-4:00 PM UTC
* Thurs, 21 Oct PING (at its normal time) 4:00 PM-5:00 PM UTC

#### Joint Meetings Week (26 October 2021 - 29 October 2021)

* Tues, 26 Oct 1400-1500 UTC Machine Learning / PING joint mtg 
* Tues, 26 Oct 1500 UTC EPUB / PING joint mtg 
* Tues, 26 Oct 1530-1600 UTC Web Payments briefing on Privacy Sandbox
* Wed, 27 Oct, 1500-1600 UTC: Web Payments re: Frictionless flows
* Wed, 27 Oct, 2300-2359 UTC Web Advertising BG (slot 1)
* Thurs, 28 Oct, 1400-1430 UTC: Web Payments PING review of SPC
* Thurs, 28 Oct, 1430-1500 UTC PING and Privacy CG updates for Web Payment
* Thurs 28 Oct 1500-1600 UTC Web Advertising BG (slot 2)
* Fri, 29 Oct, 0500-0700 UTC Devices and Sensors WG privacy discussion 
* Fri, 29 Oct, 1600-1700 Private Advertising Technology CG initial meeting

Sam: I missed the Antifraud break out session that led to the creation of this new CG.  Was created today.  Looking at use cases that privacy sandbox authors may over overlooked or not looked into sufficient depth. [Minutes](https://github.com/WICG/trust-token-api/blob/main/meetings/tpac2021-antifraud-breakout.md) and call video are above.

Aram: Where are the links?

Sam: they are in the minutes doc (i.e. here :)

Aram: PAT CG.  At most monthly mtgs, most likely.  Meetings repo has planning and scope info.  First work items: a WG charter & a common terms doc.  

Aram: Meetings Issue - https://github.com/patcg/meetings/issues/4 

Wendell: there was a discussion during PATCG re: separating BG and CG and how to make CG successful; came up again in PARKEET meeting (alternating Wed sessions) - part of discussion was how to get techs tested.  Meeting notes are good.  [PARAKEET](https://docs.google.com/document/d/1AisedrNyJRDxvehaSactuS6zrLy4htDaRyiZDcyktqE/edit#). I proposed that PATCG be successful by enrolling FLEDGE, PARAKEET, and conversion measurement.  

Sam: some discussion of and pressure for physical mtgs, esp. from EKR.  

Aram: Might make sense to cluster some meetings re; privacy and adv stuff.

Wendell: is that a w/s or f2f?

Sam: we're thinking f2f.

Aram: not overlapping; sequential.

Nick: (re anti-fraud) Is this ad fraud or other?  Captchas? authorization/authentication?

Sam: I heard this in the payments context.

Wendell: I had a different take on the breakout.  We've seen 3rd party sets having difficulty getting consensus and definitional issues.  What I heard: everyone can agree fraud is bad and mitigating it is worthy.  That it showed up re: payments doesn't surprise me; gives underpinning that doesn't excite controversies re: same origin / FPS.  

Sam: FedID: you likely know about it, but calling it out just in case.

Pete: any other meetings people want to talk about?

Christine: though logistically difficult, it was nice to have groups reaching out for joint meetings with PING.  

Pete: Most of the Web Payments was similar to what we had discussed at the PING call on SPC

Sam: Web Payments had lots of long meetings, and much of it was privacy related, Sam attended much of it. pushback was that the user might not have to provide an identifier first (for novel kinds of payment methods) because the dataflow depends on payment provider returning a list of credentials. people in the WG using privacy folks as cover to fix privacy issues that they would have wanted to resolve anyway.

Pete: SPC function but partitioning merchants across relying parties or partitioning relying parties. receptiveness in the group to work on it with concrete proposals.

Aram: Interesting analysis.  What are the forces & proposal interests that needed cover? Types of proposals that have privacy issues?

Pete: not a formal reason, but helped individuals that had concerns to hear that others were raising them.

Sam: what I heard was that we want to build persistent device identifiers, which would be okay if they were limited only to payments. and not clear how it would actually be limited. some people are imagining that they can create that capability and restrict it.

Aram: already a concern that payments will be used more often which will create identifiers .. and then those can be used for tracking

Sam: if users become familiar with approving payment-related credentials, will they just always approve that (even when not making a payment) which might get used just for tracking not for payments.

Wendell: yes, definitely a concern unless/until there's an alternative way for effective media measurement.

Pete: there is some direct conversation about an anti-goal of being able to connect payment identifiers

Christine: Machine Learning joint meeting?

Nick: privacy concerns around fingerprinting and GPU processing; will expose more on device processing which might reveal some details about hardware. Another set of concerns about the models. The group is not currently looking at doing training on the device / federated learning, only a ship-the-model-to-the-device approach.  However, concerns about users being able to inspect the model, so discussions around DRM or other mechanisms to prevent users from learning about the model. Also discussed the kinds of inferences and applications of the models, and what the new APIs might be used for and the ethical implications (e.g., facial recognition). 

…: There is also a WebGPU spec where some of the fingerprinting and executing-on-the-gpu features might be discussed

Christine: EPUB joint meeting?

Nick: I joined the EPUB call and previously sent out an email with the concerns.  Discussion didn't seem to lead to conclusions (yet)?  DRM and obfuscation were discussed (e.g., protecting fonts).  These seem user hostile and so would be good to mitigate.  GitHub issues have been opened; might be a long discussion

Christine: Thank you Nick, it’s a long spec.  Hopefully this leads to changes and other groups are aware of the privacy issues as a result

Aram: I also attended.  I observed two big themes. 1) change in the idea that the publisher and reader-vendor were the same person. and 2) the idea that EPUBs might be easier to read in Web clients / browsers.  This is HTML.  Introduces more privacy concerns.  Group seemed to want to avoid DRM issues, but seems like folks are going to use it

Nick: Several folks joined the device and sensors group (Sam too).  Call was at 1-3am.  Lots of new APIs, some old (e.g, geolocation).  Recognition that the specs have privacy issues and maybe those specs should be revisited.  There are also process issues and formal objections the group needs to address before the group can move forward.

Sam: Group had some questions about how to get reviews and how to work with PING. 

Eric: There is a session about edge computing on the web, they request review and support

https://www.w3.org/2021/10/22-edge-computing-minutes.html

Aram: Does the edge computing group have proposals at the moment? To date, much edge computing work has been about identifying users through HTTP request mechanisms rather than fingerprint.js. I’m interested in seeing seem if / how things are formalized.  Podcasts for example, where targeting is done on the edge

Nick: what was the connection to podcasts?

Aram: Most podcasts assume the client will download the audio file, so edge computing is used to insert the advertisements into the podcast audio through targeting. Then caching is performed at the edge to deliver the bespoke targeted podcast.  Google (I think) and Amazon have these products for video.

Nick: Thanks, that is helpful

## 2. AOB

Aram: Wanted to point folks to recent Google analysis around their conversion API. I thought it was interesting that they saw 16% of conversions lost because of users clearing web data. Was higher than I expected. Might be a mismatch between what users do and what users intend. Might point to users taking an action more frequently than anticipated with a common browser control that mismatches their results from the browser (does not clear long lasting cookies, does not clear 3ps interacting with the 1p they engaged with and cleared data from, etc...). 
* Link: https://developer.chrome.com/docs/privacy-sandbox/attribution-reporting-data-clearing/ 
* My notes: https://twitter.com/Chronotope/status/1455554273052434433 

Pete: is this from user-activated clearing or automatic clearing?

Aram: indication from post was that this was manual action, in Chrome.

Sam: Improving Web Advertising BG switching to a bi-weekly meeting cadence.

Wendy: Improving Web Advertising will try to make folks more aware of groups activities and meetings

Nick: If we have extra cycles, we could review HTML and DOM or other specs.  Let’s work on a privacy considerations and chat with our friends at WHATWG.

