# Privacy Interest Group meeting (20 August 2020)

## Attendees 

* Andy Sharkey (CafeMedia)
* Brent Zundel (Evernym)
* Chris Wilson (Google)
* Christine Runnegar (co-chair)
* Dave Harbage (DuckDuckGo)
* Eric Mwobobia (ARTICLE19)
* Erik Anderson (Microsoft)
* James Rosewell (51Degrees)
* Jeffrey Yasskin (Google Chrome)
* Joey Salazar
* Konrad Dzwinel (DuckDuckGo)
* Kristen Chapman (salesforce)
* Lisa LeVasseur (Me2B Alliance)
* Mallory Knodel (CDT)
* Martin Meyer (Akamai)
* Melanie Richards (Microsoft)
* Michael Kleber (Google Chrome)
* Mingzhe Li (Akamai)
* Nick Doty (UC Berkeley)
* Paul Jensen (Google)
* Pete Snyder (co-chair, Brave)
* Pranjal Jumde (Brave)
* Sam Weiler (W3C/MIT) 
* Sean Harrison (Google)
* Shaun Gilmore (Apple)
* Theodore Olsauskas-Warren (Google)
* Wendy Seltzer (W3C)
* gmcgrath
* Brad Rodriguez (Magnite)

Scribe: Jeffrey Yasskin

## 1. Privacy reviews

#### a. Request from the WebRTC WG of its MediaStreamTrack Content Hint spec (Kris)

Explainer:
https://github.com/w3c/mst-content-hint/blob/gh-pages/explainer.md

Specification URL:
https://www.w3.org/TR/2020/WD-mst-content-hint-20200728/

Security and Privacy Considerations:
https://w3c.github.io/mst-content-hint/#security-and-privacy-considerations

Security and Privacy self-review:
https://github.com/w3c/mst-content-hint/blob/gh-pages/security-privacy-questionnaire.md

GitHub repo (for any feedback) 
https://github.com/w3c/mst-content-hint/

Kris: This is about: when you have a media stream object, there are different tracks for different parts of the content, like video or audio. This proposal says, based on the type of the content, the best settings are different. So, there should be a client hint to explain what the content is like. e.g. Someone talking, or listening to music. Overall there isn't a lot of concern from a privacy perspective. First thought was, is this going to be adding more fingerprinting information? Not really, because it adds another data point, but it's not expanding beyond what the media stream incorporates anyway. Pete and I talked, and I'm a little concerned that this uses Client Hints, which as far as I know, isn't standardized yet. Maybe chicken-and-egg. Also generally concerned that the Questionnaire isn't very robust. Doesn't go into detail. Dismisses the privacy risk because there's no PII, but I want the questionnaire to be more fleshed out. Also have more security-oriented considerations: When we're worried about fake content, this makes it easier to create fake video. What's the process if it brings up concerns that are beyond our area?

Pete: Second the main point: also didn't see anything directly privacy-related. Calling non-standard-track functionality. when we find things that aren't privacy-related when doing a privacy review it's still helpful to raise the issues. Thanks for doing the review. That was super in depth.

(npd: please do raise other issues you find! and sometimes you might be help other identifying privacy or security problems that we should be considering generally and the group will appreciate the earlier feedback and issue spotting.)

Christine: Re analysis the group did in responding to the self-review questionnaire: as part of our feedback, we could give guidance that it's not sufficient to just say "this doesn't deal with PII, so there's no privacy implication". Need to do a fuller analysis anyway.

James: Re Client Hints: that's an IETF specification that's experimental and expires in Oct/Nov [expires October 2020 https://tools.ietf.org/html/draft-ietf-httpbis-client-hints-13]. When lots of proposals rely on each other, when dependent ones, it can have an impact on other specs.

Pete: Kris and I discussed that this spec depends on non-rec-track specs, so those are expected to change as they move to recommendations in the respective standards bodies.

Sam: I thought this doesn't actually use HTTP Client Hints. Thought this is just JavaScript. Did I read it wrong?

Kris: I think it is part of the JavaScript object, but I think that when it goes back to the server, it's sent via HTTP.

Sam: Surprising that it doesn't cite Client Hints as a reference. Thanks for digging into this.

Sam: I'm not so worried about the questionnaire; more worried about the Security and Privacy Considerations section. Agree that "no PII" isn't sufficient.

Lisa: Making a suggestion: Advocate for systemic and rigorous exploration of more than use cases, but also abuse and misuse cases. Flex creative muscles, and think about how a seemingly-innocent optimization parameter might result in identification of people (for example). How can this tech downstream create unintended consequences?

Kris: This is definitely part of the feedback I'll give. I've started feeling paranoid about giving out biometric data about privacy. When you identify something as a voice or an image of their face ... making it more easy to tap into faces or voices is concerning. I don't think it's a huge risk today, but want to think in the future.

Jeffrey: How do we make the search for abuse cases systematic, and become confident that we're being exhaustive?

Lisa: Don't know yet, just start by practicing.

Pete: What kind of background data would be useful?

Lisa: For me, it's about deliberately thinking about abuse and misuse cases. And harms. In the Me2B alliance we've developed a (not great yet) [digital harms dictionary](https://me2ba.sharepoint.com/:x:/s/LivingDocuments/EcqGrfGY8qJEiioT-RpuNb4BxSIPpzWzWFl7nfTN1cbl8w?e=S1rfS4). Identifies big categories and examples of digital harms, even if they haven't made it into the legal purview of harms.

Jeffrey: How to find _all_ the issues instead of just the ones I managed to think of.

Pete: How to think about web security issues in a formal/fundamental way.

James R: Online harms is a topic of the UK government. See https://www.gov.uk/government/consultations/online-harms-white-paper.

#### b. Request from the Devices and Sensors API WG for Screen Wake Lock API (Pranjal)

Current ED: https://w3c.github.io/screen-wake-lock/

This document specifies an API that allows web applications to request a screen wake lock. Under the right conditions, and if allowed, the screen wake lock prevents the system from turning off a device's screen.

Substantive changes since the last CR is documented here: https://w3c.github.io/screen-wake-lock/#changes-20171214

Link to the Security and privacy considerations section:
https://w3c.github.io/screen-wake-lock/#security-and-privacy-considerations

Request for issues to be filed at https://github.com/w3c/screen-wake-lock

Pranjal: Did a review of the Wake Lock API. This lets JavaScript obtain a "wake lock" that prevents the screen from turning off. Was scared about the capability. bad if third-party iframes can do this. But spec takes a lot of things into considerations. Highlighting to users if screen lock is active or not. Still a lot of edge cases, and have filed GitHub issues. Active discussion.

Pete: Can you share the links to issues? How many did you open?

Pranjal: Opened 3 issues. 2 are primary. How a third-party can request a wake lock? Spec discusses that the user should have an indicator if the lock is active in the UI, but doesn't say how to distinguish whether the first or third-party requested the lock. There have been lots of blog posts about this concern by web developers.

* https://github.com/w3c/screen-wake-lock/issues
* https://github.com/w3c/screen-wake-lock/issues/278
* https://github.com/w3c/screen-wake-lock/issues/277

Sam: These issues don't have tracker labels set.

https://w3c.github.io/horizontal-issue-tracker/?repo=w3cping/tracking-issues (<3 Sam)

This tracks issues across lots of groups. This lists the Wake Lock API, but only has one issue. But Pranjal's issues don't have labels yet. There's a pair of labels for each horizontal area. By default, set the -needs-resolution issue, and if we decide it's just advisory, use -tracker.

Jeffrey: Note that it's hard to set labels in other people's repositories. W3C folks probably have admin privileges, but random folks would need "triage" permission.
[wseltzer notes that the team and chairs may have permissions, but indeed, IG members may not]

Sam: At the top of the tracking issue page, there's a link to the PING repository, where you can file an issue to set the label.

https://github.com/w3cping/tracking-issues/issues

Pete: What would be most helpful as instructions for how to file issues? Model repo? Document?

Sam: Ask in 2 weeks after the improved docs come out.

Jeffrey: Existing implementation in Chrome doesn't have an indicator of the active wake lock. Lots of other mitigations, but no indicator. I think I filed a bug for developer ergonomics, but didn't realize the spec said to do this. [Edit later: I did not in fact file that bug.]

Pranjal: Will file or comment on bug.

Nick: Permission model? Will the browser just grant this unless there are special cases? And then if it doesn't grant for low battery, maybe that's an information leak. Or will some implementations prompt users?

Pranjal: There's feature-policy for saying whether the third party can have access. When the API is invoked, there's a permission prompt that's visible to user, at least in the spec. Haven't checked implementations. Can share exact text.

#### c. Request from the Immersive Web WG for WebXR Device API (Pete)

Current ED: https://immersive-web.github.io/webxr/

This specification describes support for accessing virtual reality (VR) and augmented reality (AR) devices, including sensors and head-mounted displays, on the Web.

Security and Privacy considerations: https://immersive-web.github.io/webxr/#security

Explainer: https://github.com/immersive-web/webxr/blob/master/privacy-security-explainer.md

Pete: Re-review. Not much has changed with respect to privacy issues. Was some ambiguity about how the API would flow for an "inline" WebXR session, where it's XR-y but not using VR hardware. That was sorted out satisfactorily. There are also passive methods to ask whether the browser has VR-compatible hardware. "Does it have audio?" "Does it have video?" Those are fingerprinting bits. Those haven't been fixed. There's non-normative text about allowing UAs to lie about it. That's better but not sufficient.

Nick: Understand the concern about fingerprinting or even just disclosure. Do we have a recommendation for "here's a better way"? How can websites provide a VR solution that lets users know the site supports a VR experience?

Pete: I had a couple suggestions. At the very least, reduce to 1 bit. There are a couple things about a UA having some unusual capability. So maybe we could collapse 18 bits into just 1 that says "the UA has some unusual capability". Maybe half-baked.

James R: We've talked about fingerprinting several times. Possibly 2 specs where fingerprinting is a factor. How do we balance the needs for the use case to be supported efficiently, vs the privacy risk of fingerprinting? If it's a Boolean answer, "nothing can make fingerprinting worse", that would speak to policy which is bigger than today. If not, what's the threshold?

Pete: PING is chartered to register privacy concerns and advocate for privacy concerns to be addressed. When we reach a situation where we can't resolve them, then the Director makes a decision. Doesn't seem to be in PING's charter to do that balancing while we're doing reviews.

Michael Kleber: This issue of advertising the "is hardware capability available" bit seems like an example of something that has recurred in other contexts. Information is useful to affect what's shown on the screen, but it's not necessary to send that bit up to a server. We really only want it to affect how things look on the client. 2 things that are potentially reusable and generalized ways to approach that situation:
1. Possibility that the browser could display something where there's no network access possible. Make it available inside the browser for display but forbid it from being sent to a server. The Chrome ["Fenced Frame" proposal](https://github.com/shivanigithub/fenced-frame/) from earlier this week is trying to provide that capability.
2. If we don't have the magic way to display things, is the browser UX taking on that job: imagine in this case, the page would advertise that it can use VR capabilities if they're available, either in static HTML or calling an API. The browser then has the option of saying to the user "I happen to know that you have VR hardware; this page wants to use VR hardware; should I let the page know that you have some hardware?" This could be shown intrusively as a popup, or unobtrusively as a chip in the URL bar. Would be outside the content space.

Something like Fenced Frame and something like browser UI, will probably come up repeatedly.

Fenced Frames link: https://github.com/shivanigithub/fenced-frame/

Also useful for showing ads, where the surrounding page can't learn what ad is shown. Brave does something related to this, by showing the ad in system notifications. Fenced Frames attempt to incorporate that into HTML rendering.

Pete: For background, where is this being pursued?

Michael: Just an early draft explainer for now, not in a group or incubation yet. Related to things talked about in WebAdvBG. Related to other proposals. Will progress somewhere in the future.

Kris: Responding to James: When I was doing the privacy review, I'm approaching this with the worst-case scenarios. Important that we flag things, doesn't mean we want to block the spec. Then it's a conversation. There's an impression with these reviews that, if it hits a privacy problem that it stops the process, but in my view, that's not what's going on. How do you balance gains from the proposal against possible abuses? If we can't, there's the escalation path.

Nick: Agree with Kris's take. Most of the time with fingerprinting, we think about identification risk and mitigating it. Identify severity. Always have to find mitigations on a case-by-case basis. Appreciated Michael's additional suggestions there. I like declarative ideas. It lets the browser tell the user which pages can take advantage of their hardware.

Link to guidance: https://www.w3.org/TR/fingerprinting-guidance/

Lisa: Lots of language about notice-and-consent, but a number of us in the privacy community are trying to change "consent" into user-proffered permission. Consent is a non-human non-agency-supporting mechanism, and we shouldn't be satisfied with it. IEEE is looking for machine-readable privacy terms. 7012 working group https://standards.ieee.org/project/7012.html. Trying to define a machine-readable way for users to grant permission to use information for particular scopes and durations.

Pete: Links! 

(Lisa) https://ieeexplore.ieee.org/document/9031549 and the Me2B Alliance is working on a new paper eta early September.

James: Useful for W3C to look outside its own walls. Thanks to Kris for explaining how you do it in practice. Makes sense, but the precise interpretation comes down to what TimBL thinks is right or wrong. Can we provide more clarity? We quote text, and it's up to interpretation. Starts with users, and then we interpret what we want in different ways. 

(npd: old school! sounds like the earlier work on P3P, where users could negotiate machine readable terms.)

(kleber: Yep, ouch — lots of past pain and failure that we can hope to avoid repeating!)

Jeffrey: The Privacy Threat Model should be a good place to have the negotiation about what tradeoffs we make.

Pete: Lots of opinions on how the Threat Model should evolve.

Sam: Thanks Lisa for calling out permission over notice-and-consent. As that progresses, and you find things we could use here, please bring them up.

Lisa: Not quite done yet. :) Coming up with a taxonomy and schema. Creating a machine-readable legal contract.

## 2. AOB

Pete: Bottom of queue and bottom of agenda. Anything else?

Sam: Minor thing: Jeffrey: There's an issue in the wake lock repo that looks like it was moved there; do you recall where it was originally?
https://github.com/w3c/screen-wake-lock/issues/137

Jeffrey: No memory of this place, and can't go look right now b/c scribing. :)

James: I've made a pull request on the Security and Privacy Questionnaire, and we'll continue with asynchronous comments. A couple issues that I'd like to talk about more. Consent and supply chains being trustworthy [https://github.com/w3ctag/security-questionnaire/issues/83]. IEEE (IETF?) document allows a broader set of considerations. Definitions of first- and third-parties, and how the UA plays a role in that [https://github.com/w3ctag/security-questionnaire/issues/84]. 

Pete: Please link to PR.

(James) PR for Security and Privacy proposed changes - https://github.com/w3ctag/security-questionnaire/pull/94


