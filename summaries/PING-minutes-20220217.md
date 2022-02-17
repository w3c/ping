# Privacy Interest Group meeting (17 February 2022)

## Attendees

* Christine Runnegar (PING co-chair)
* Pete Synder (Brave, PING co-chair)
* Nick Doty (CDT, co-chair)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C)
* Sean Harrison (Google)
* Theodore Olsauskas-Warren (Google)
* Kris Chapman (Salesforce)
* Wendell Baker (Yahoo)
* Matt Liu (The Washington Post)
* Kris Shrishak (Invited Expert)
* Aram Zucker-Scharff (The Washington Post)
* Jeffrey Yasskin (Google Chrome)
* Joshua Ssengonzi (Invited Expert)
* Matthew Liu (The Washington Post)
* Eric Mwobobia (Article 19)

Scribe: Sean Harrison

Code of Ethics and Professional Conduct: https://www.w3.org/Consortium/cepc/

## 0. Introductions

Nick - take a look at the CEPC doc, for how to report violations with others, can also reach out to the chairs. [Link] to contact non-chairs (ombudspeople) as well.
https://www.w3.org/Consortium/cepc/#Reporting

## 1. Privacy review of CSS Custom Properties for Cascading Variables Module Level 1 

See: https://github.com/w3cping/privacy-request/issues/79
https://www.w3.org/TR/css-variables-1/

Pete - This is a new proposal from CSS working group to add into the standard something proposed by preprocessors, margins, colors, etc. Need to import all over the place atm. In response there are systems that allow you to plug in throughout the docuemnt. Now want to pull these CSS variables into the CSS spec. Some new syntax for defining variables, no new state introduced or privacy concerns, just about leveraging new CSS capabilites in spec.

Nick - Variables seem like a great feature, curious if you thought the variables were scoped

Pete - CSS seletors define scope, available anywhere is root, or you can set scopes to paragraphs or any CSS selector. Doesn't leak state in any new way for CSS docs.

Nick - Write variable in one doc and access in another, but this doesn't introduce any new capabilites, already doing with JS.

Pete - didn't check specifically, but should be creating new leaks.

Aram - There is potential added level of state, already exists in CSS, an element with shadow-dom can establish its own root, and establish variables there that can overlap page root. Not necessarily an addtional risk. Bring to attention as potential interaction point, but likely not a privacy risk.

Nick - Vaguley aware of shadow-dom, but this is still same author of the page?

Aram - Same author, not :root, called :host for shadow-dom. These are already interacting with other CSS features, so likely non-issue.

Nick - Next steps?

Pete - Pause for a day or 2, but on monday will assume no privacy issues and follow up with group.

## 2. Ambient Light Sensor API privacy risk mitigations

See: https://github.com/w3c/ambient-light/pull/77

Nick - Group is implementing mitigation and wanted our feedback

Christine - Problems were identified with the API some time ago. Last year, the WG decided to make some privacy mitigations normative in the spec. They are proposed in the above thread. Lukasz has done reaserch into the privacy issues all the way back to 2016, info is in thread. Instead of reading out raw values from light sensor they will round to 50 lux. Wanted to make sure everyone else is okay with the mitigations?

Theo - How did they come to 50 lux as a number? They have a dense spreadsheet, what threshold were they using? Why not 100 or 200 lux?

Nick - The idea was really small values could identify the same device or communicate across devices by changing brightness on different screens.

Christine - Theo please ask your question in the thread, I looked in the spreadsheet and am not a domain expert in ambient light, which is why I asked Lukasz to looked at it.

Pete - I have no idea what a typical range for this value is in standard use.

Nick - Is there a numeric value for needed level of detail.

Pete - We generally try to avoid fingerprintable values without permission prompts, and it seems unlikely that this is 1 bit of data.

Nick - Quick pass of spreadsheet numbers in range of ~7000, even rounding to 50 is still a fair bit of information.

Sam - 2 directions. Ask them why 50? This feels like a temporal fingerprinting risk, as the value is changing over time. Even if 1 million at a lux value right now, when it changes for each of them will vary. I don't think they  this risk out in the spec. Privacy consideration section is high up in the spec. They call out this temporal risk in the spec.

Aram - Cross origin leaks seem particularly high bandwidth depending on device.

Sam - They say you can limit max samplbing frequency, ask them about it on thread.

Nick - I think freq was considered but not there yet.

Pete - Link to ephemeral fingerpriting, covers how cookie syncing can be done even with low granularity values. No interest from other implementers atm. Is there a plan to move this to req? If it is moving to req we can give it a more formal review, but still a good time to pay close attention.

Nick - Does someone else know likely implmentation.

Aram - There could be additional mitigations for querying the user to access this API, unclear if this is the case, would need camera permission? An additional mitigation against 3rd party cross origin leaks, limit via CSP.

Pete - Does have a feature policy atm.

Nick - Policy controlled feature with default allowlist of self, so would need to explicitly allow an iframe to use it?

Aram - SG

Nick - not clear on permission name, this is the problem with doing a review and coming back to it 2 years later.

Pete - Since we are not pressed for time, I can work with Christine to go back to the group.

Christine - We were not asked to do a full privacy review, just asked to review reduced granularity in normative way in spec. Even if there are only going to be 1 or 2 implementors I think it is worth the time to get this right because the spec might be used as a guide for other things. Good we have identified further privacy issues that we should check. We should remember what they asked when providing feedback to the team. I would appreciate all here to frame their questions to get the right feedback.

Theo - There is a permission assocaited with it, using the sensor API permission. But this permission is default on in Chrome.

Nick - We still think it may be an ephemeral fingerprinting risk.

Aram - We should give them feedback on what they asked for, but our questions do cover explicitly if their mitigation is effective, so we should still chat about it.

Nick - We have questions about the reasoning behind the granularity, and how effective. And ongoing concerns about fingerprintability (ephemeral) in the short term. Christine do you want to take the lead going and talking to the team.

Christine - Sure, and I invite others to work out on the slack these other issues for response.

## 3. Privacy reviews and process

See: https://github.com/w3cping/privacy-request/blob/main/howto-conduct-a-privacy-review.md

Nick - Talk about how one actually does a privacy review, Pete has taken a first pass at writing down how we do privacy reviews and how you can do one too.

Pete - This is a medium length walk through about how to go through privacy reviews. This is likely not the final home of the doc. Doesn't discuss substance reviews, just the process. Who to talk to, where to put info, where to file, how to follow up on issues. If people also want a doc on what sort of things to look for it will be up to other documents in the future. Feedback issues are welcome, but it will likely move.

Nick - Thanks for laying out how to do this, are there any questions or ideas for next steps?

Christine - Tangentially related to doc, one of the other things I would like to encourage others to do is to set aside time to do privacy reviews so that we get a broad range of people looking at specs.

Nick - Maybe the best way to try out the doc is to do a privacy review following these steps. Anyone on the call who has not yet done a review but would be interested in trying out the doc. Sean if you want to try it out, we can have you take the next review or contact offline.

Aram - This is super useful, the links and resources sections, so people doing the review can see it. and the label cheat sheet seems like a really helpful resources. As someone who has done 1 review I find this useful.

Nick - That is truly the purpose of the document to let people find things they didn't even know where out there.

## 4. WHATWG specs

Nick - Christine and I talked with some WHATWG folks about doing privacy reviews for things showing up only there instead of also W3C. Big takeaway was that WHATWG folks were pretty receptive to this. They have a slightly seperate process, but we can still likely use the same issue labels and have it work with our automation. They had a list of specs https://spec.whatwg.org/ for us to look at. Don't know how much people follow WHATWG, its own group, primary work on dom and HTML. They also work on a lot more such as fetch and notifications and storage (state partitioning also occuring in privacy CG). Making sure that local storage has reasonable privacy and not allowing detailed tracking. Just wanted us to be aware of this list of specs. They will likely not have a state of ready for review as they are living standards, but there are some that will likely be high impact. Welcome peoples thoughts on that list of specs and what we should priortize or if you have worked with WHATWG in the past.

Christine - One thing we could consider as a group, is in the weeks where we don't have priavcy reviews, we could look at one of their shorter specs. Or a high impact one, send out a note before the meeting to read it and be familiar.

Nick - That makes sense, as we don't always get evenly distributed work.

Sam - Just to confirm the scope did not cover the oustanding reporting API issue on the HTML spec

Nick - No, we did discuss the dom review here, we opened an issue for it. There is now follow up we can review.

Aram - If we are trying to figure out which one to take on first, maybe the URL one would make sense. We know browsers are already doing mitigations around URL paramaters and structures in their browser above the standard. Since it already exists as a privacy concern. (See: https://url.spec.whatwg.org/)

Nick - Sure, 1 vote for URL

Jeffrey - We have the navigational tracking work in Privacy CG, not clear the URL spec will be privacy relevant, of course we could review it and determine that. Storage, for instance, is more privacy sensitive. There may be more obviously relevant specs. (See: https://storage.spec.whatwg.org/)

Aram - Open to it, URL just stuck out to me given ongoing work from Apple and others. Maybe we review it and say there isn't anything there.

Nick - Hearing URL and Notification and Storage. I'll take as AI for future call or on list, any strong feelings feel free to follow up.

## 5. AOB

n/a

## 6. Next meeting

Nick - First week of march, March 3rd. May have other reviews if requests come in, or we can look at one of these whatwg specs, or use it as a triage meeting.