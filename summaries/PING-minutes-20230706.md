# Privacy Interest Group meeting (6 July 2023)

## Attendees

* Pete Snyder (Brave, PING co-chair)
* Christine Runnegar (PING co-chair)
* Nick Doty (CDT, PING co-chair)
* Philippe Le Hegaret (W3C, Team Contact)
* Sebastian Zimeck (Wesleyan University, Global Privacy Control (GPC) group)
* Max Gendler (News Corp, AC Rep)
* Matthew Finkel (Apple)
* David Waite (Ping Identity)
* Kyle Duren (Yahoo)
* Corentin Wallez (Google Chrome, WebGPU co-chair)
* Jeffrey Yasskin (Google Chrome)
* Ken Russell (Google)
* Francois Daoust
* Shivan Sahib  (Brave)
* Myles (WebKit)
* David Neto (Google)
* Francois Daoust
* Tess
* Kelsey Gilbert (Mozilla, WebGPU co-chair)
* Rafael Cintron

Scribe: Jeffrey Yasskin

Chair: Nick Doty

## Agenda

### 0 Introductions and CEPC

Nick welcomes the group. The meeting is conducted under the [CEPC](https://www.w3.org/Consortium/cepc/). Reads the statement of intent.

### 1. WebGPU

primarily fingerprinting surface issue: https://github.com/gpuweb/gpuweb/issues/3101

Nick: WebGPU asked for a privacy review. Pete Snyder, a co-chair, took it. Talked with PING about the notes, then filed issues and has had a long conversation with the WG. There have been some challenging issues around the fingerprinting surface. Looking for ways forward to resolution, or at least document the issues.

Pete: High level, there's a range of values that a web page can learn about the GPU hardware. I think some is planned to be removed, like the description, and another property. I'm still concerned about access to architecture, vendor, supported features, and supported limits (used to optimize programs). 2-3 other things: 1 mitigation is to restrict the range of values that can be returned. Limited to 5 bits of entropy. Implementers can reduce that; it's an upper limit. There are practical problems, and 5 bits is a lot of entropy. Some of this information is already available through WebGL-Debug extension in canvas. We don't love that aspect of the platform. A greater amount can be inferred through canvas fingerprinting. e.g. drawing operations and probing limits. I think we should aim to reduce fingerprintability and give a path toward removing fingerprinting surface. Even if it's about 5 bits, that's an enormous amount for a single spec to contribute.

Corentin: Thanks for the summary; that does descirbe the fingerprinting in the spec. We planned to remove architecture and device description; that'll happen. The idea is that to be able to optimize and access more than the base WebGPU features ... it's meant to work everywherre, so it provides a low guarantee on the features. Needs to be very portable. But developers want to be able to create bigger textures when they're supported. So we expose that information. Vendor and architecture are exposed for a similar reason: developers need to reason about what they're working with. But it's all under the UA's control. A UA can just expose the base features, and no information about the device. I read "what about incognito mode?" The group's probably open to saying that incognito mode should only support the base mode. Finterprinting is highly correlated to not only canvas fingerprinting, but also a bunch of other things. e.g. With iphones, there's a small number of variations: if you know you're on Apple hardware, then the screen size gives you lots of information, and it's highly correlated with WebGPU. On other platforms, it's also correlated with other information. We want to reduce the amount of fingerprinting throught feature levels, but that takes a lot of developer feedback to know what features and limits are important. Chrome folks don't think we have enough information to do that right now.

Kelsey: There's bits we've found in our spec audit that we believe are intractably revealed because of the nature of the thing we're doing. We expose how things are hardware rendered, and when you draw triangles, there's minor differences in how the math works out. You can't expose a hardware rasterizing API like this without revealing the vendor. We include that in the 5 bits. We haven't broken them up into what we think is intractible, and things we might be able to do better about. 2.5 bits are just the vendor. Perhaps what mega-generation the GPU is. Further than that, we get into optional bits. e.g. things your hardware supports that other people's hardware might not support. We want to let developers use those. The privacy thing is a subset of the larger privacy goals of the web platform and our browsers. We struggled in trying to spec anything stricter because it's hard to get all implementations to mitigate in the same way. We had trouble agreeing. What's our highest-level goal? To constrain the amount of fingerprinting. It was hard to be more specific. The 5-bit solution is what we came up with. It's an upper bound. All the implementers came together. It's possible to fall short of that in practice, but we could fall short of any specified mitigation. We're all trying to keep this private; it's a UA goal.

Nick: Want to hear more about the different mitigations. It's been useful to talk about types of mitigations. The only concern isn't the amount of entropy, although that's important. Ways to make it so this isn't available in all the same ways, or isn't immediately accessible. We've seen that specs that provide complex functionality, which reveals entropy, sometimes it's primarily used for fingerprinting instead of its goal. Designers didn't actually want that. So some potential mitigations, like it could require user interaction, or permission, or top-level only, or 1 frame at a time. To make it so the primary use isn't fingerprinting. Have y'all considered these mitigations?

Kelsey: One useful things we got from horizontal review was "have you tried all these things". That list is in [the issue in our org](https://github.com/gpuweb/gpuweb/issues/3101). A lot of them are challenging. e.g. requiring user interaction tends to get in the way of the breadth of apps, and how they need to work. Some are compute-based. Some want to do things immediately on load. Limiting to visible contexts is tricky. There's a fundamental friction between a novel set of building blocks, which is best used if it's available everywhere. We also run into these with canvas and WebGL fingerprinting. We're out of ideas for things we can implement and that successfully extend the web platform. e.g. feature sets / tier levels. Maybe we have 4 types. But we couldn't agree on the definitions of the levels.

Corentin: +1 to Kelsey. We're interested in looking at other kinds of mitigations. e.g. what about iframes with a sandbox attribute? We decided not to; don't remember that whole conversation. We don't know what would satisfy both the need to expose these things and explain things adequately to users, and everyone's goal to reduce fingerprinting. e.g. users don't understand the implications of "can we access information about your GPU?"

Pete: I don't mean that any of those mitigations would be complete solutions. A permission would be a strong mitigation; user gesture would be weaker. Point taken about correlations; there's a small amount of graphics hardware. That's the concern: if you run a small browser, and you see uncommon hardware, that person sticks out. The correlation can make the problem more difficult.


Jeffrey: how do we get to resolution despite disagreement? Nick suggested other mitigations, give people access to baseline and then require permission to do more. Corentin's right that it would be hard to explain to users. Could still put a permission request in the API, and different UAs can present that differently -- some could present it by default and others could provide a user prompt. or privacy-focused browsers could provide just the baseline, although privacy-focused browsers might not like that because that would limit the functionality to their users.

Jeffrey: re correlations, the spec says don't provide too much entropy by bucketing users. if very few users have mismatched hardware, the UA can take that into account, spec currently enables that. getting new features can sometimes be worth increasing the fingerprintability of the web. this doesn't increase it, but may preclude decreasing it. ability to use powerful hardware might justify keeping this constrained amount avaialbe 

Myles: What if you require user interaction, or different policies for iframes? One of the common use cases for WebGL is 3p maps in iframes. The spec shouldn't say it requires user interaction for WebGPU because maps should work in 3p iframes. When you're writing a spec, it's challenging to differentiate between 3p maps providers and trackers or ads. It's hard to differnetiate in a spec. It's possible to differentiate themm, but it's complicated and subtle enough that we don't think we could make it normative. We're going to try to be sophisticated about where we allow WebGPU, but it's hard to make it normative.

Shivan: WebGPU is already shipping. Which APIs are used in the wild, and which aren't actually useful? There are some things in the spec that aren't filled in by Chromium. If we don't intend to use things, we should remove them from the spec. We talked about the feature level approach. Bucketing things. UA only reveals "how powerful" the device is. How much have we explored that? Is the hesitation about having already done the work to expose the labels, or are there fundamental issues?

Kelsey: We've talked about feature levels. If we had 3-4 feature levels, and 6+ device vendors, and each vendor supports 3 features levels, you get close to 5 bits. Intractible bits around vendor; more tractible bits around feature levels. We can try to formalize this into feature levels, but the 5 bits are a better actual guarantee. Some of the fields are being implemented by Chromium over time. If the fields are empty, and we remove them from the spec, then everything's good. If someone was using those fields to exceed the 5-bit limit, they might not remove them even if we remove them from the spec.

Nick: Seems like we have had some concrete suggestions in this conversation. E.g. a permission in the spec that different browsers would handle differently. Finish removing fields from the spec that aren't used. What's the progress?

Myles: We (WebKit) proposed feature levels originally: they're good for privacy but also good for developers. If we could expose a similar API, that'd map better onto the bigger engines. Simpler for developers because they have a smaller matrix of things to support. It's hard to get there, but 

Jeffrey: tension in the discussion thread .. if the webgpu wg doesn't come to agreement with reviewer, what does it mean for formal objection if we don't get to consensus? Is it the PING objecting, or an individual?

Nick: My general understanding is that PING parcels out reviews, and then issues are filed by individuals. Individual people could formally object; the PING doesn't formally object. We're a venue to try to resolve objections.

Kelsey: The list of ideas aren't new, and we've discussed them all, and we haven't made progress on them. Personally, from Mozilla, there's not a good path forward that addresses the core issues about device identification, and specifically the cross product of the intractable vendor bits (via rendering/math differences) and the bits from feature levels. Don't think anything else we do is actually mitigating it.

Christine: Generally, the PING tries to reach consensus as PING. We delegate the reviews to individuals, but we discuss them, and if there's concerns about those reviews we raise them in these calls. Might not be formally "the PING view" in all cases, it's our goal to have consensus among PING. I appreciate that this (GPU and privacy) is really tough. I hope from this discussion that there might be some mitigations that would help. There's an opportunity for UAs to improve the privacy experience, but I worry that we're placing too much burden on the user agent. In an ideal world, we'd put it in the spec layer.

### 2. Charter for proposed PrivacyWG

https://w3cping.github.io/administrivia/2023/charter.html

Nick: We've been discussing narrowing the charter of PING or combining it into a WG. Now's a good time to get out the issues and discuss the way forward. Proposed charter is for a privacy working group. Like in soem other Horizontal Review groups, we'd do horizontal review. We wouldn't incubate new work. We coudl do normative deliverables. We have a draft charter. 

Jeffrey: Support. Thanks Nick for drafting. Other groups have some language for dealing with incubations that might not progess enough to adopt.

Tess: I'm skeptical about doing a WG for general-purpose privacy. Can't say whether a WG doing horizontal review is an improvement from the PING status-quo. Virtually every web spec involves privacy issues. Need a dispersed set of privacy experts, in all the working groups. When we look at incubation in the Privacy CG and privacy-related specs inn the WICG, there's an already-existing group that should pick things up. Would be strange to charter a privacy WG that wouldn't take up the majority of privacy work. Only GPC doesn't have an obvious place to land, and it'd be good to charter a smaller group for that. Easier to get companies to join smaller groups. You attract only engaged people. Even if in the future it makes sense to charter a general WG, it doesn't make sense now. Want to see a larger set of plausible deliverables.

Pete: Support. Want to get more expertise in ping and have more people aware of the horizontal review process. My hope is that there will be lots of small additions, of which GPC is one. Google team has work around bounce tracking. Things like that don't have obvious homes, and they're privacy-related.

Matthew: This seems aspirational rather than concrete. There aren't concrete proposals that we know we want to take on. 

Nick: In the current text, we have one committed deliverable: GPC. We have proposed deliverables that the group can choose to adopt if/when they're ready.

Nick: We have some differences. We shoudl discuss on Slack and Github. It seemed like more work to do lots of 1-off WGs, but I'm not completely committed to a Privacy WG.

### 3. Privacy review requests

https://github.com/w3cping/privacy-request/issues

Pete: Verifiable Claims group asked us to review things, and someone from Brave wrote them up. We'll mail to this group. Reviewer is in a bad timezone for this call, but I'll proxy.

### 4. Charters that need privacy review

https://github.com/w3c/strategy/issues?q=is%3Aissue+is%3Aopen+-label%3A%22Privacy+review+completed%22++label%3A%22Horizontal+review+requested%22+

Nick: Philippe, how should we review charters?

Philippe: The draft charters are in the public record and in the strategy repository. Some have been sent for review to the AC. Others are in early stage, and might not even be a commitment to create the group. e.g. Privacy WG. Some are just maintenance like Pointer Events; others are new ideas like Solid. Privacy experts should suggest broad privacy concerns about new areas. Don't want to start work on something and then realize problems a few years later. We wait several weeks for comments, and then move forward to AC review. e.g. Web of Things charter is pretty ready for AC review. 

Nick: Trying to identify classes of issues in charters.

### 5. Self-Review Questionnaire #101 auto publishing

https://github.com/w3ctag/security-questionnaire/issues/101

Nick: There are updates to this spec, and we want to auto-publish on approved pull requests. That seems like our general process as PING, that approved pull requests can then be published as a new version. If people have concerns, we could talk about another process for approving publications.

---

Thanks to attendees, and thanks to Jeffrey for scribing.