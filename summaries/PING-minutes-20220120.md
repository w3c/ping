# Privacy Interest Group meeting (20 January 2022)

## Attendees (sign yourself in)

* Christine Runnegar (PING co-chair)
* Pete Synder (Brave, PING co-chair)
* Nick Doty (CDT, co-chair)
* Wendy Seltzer (W3C)
* Theodore Olsauskas-Warren (Google)
* Matt Liu (The Washington Post)
* Kris Chapman (Salesforce)
* Aram Zucker-Scharff (The Washington Post)
* Jeffrey Yasskin (Google Chrome)
* Sean Harrison (Google)
* Wendell Baker (Yahoo)

Scribe: Pete Snyder, Jeffrey Yasskin

Code of Ethics and Professional Conduct: https://www.w3.org/Consortium/cepc/

## 0. thanks and introductions

Nick: Thanks to everyone who did reviews in 2021. There were 24 reviews.
… there was a blog post: https://www.w3.org/blog/2022/01/privacy-interest-group-ping-2021-year-in-review-and-thank-yous/ 
… thanks much and 2022 looks good

## 1. Privacy review of CSS Conditional Rules Module 4 

URL of spec: https://www.w3.org/TR/css-conditional-4/; review: https://github.com/w3cping/privacy-request/issues/70#issuecomment-1015880022

Jeffrey: Module 4 adds one feature to @supports.  It allows sites to detect UA and what features are supported.
… this spec lets pages detect which kinds of selectors are supported.
… same implications as prior ability to check for properties
… doesn't seem worrying, since pages could already detect
… theres a privacy considerations section saying the same.

Nick: were there any issues opened?

Jeffrey: No issues to open, but added a comment to the PING request issue.

Nick: perfect, thats the best case!

Aram: I had a look, and agree, doesn't seem to be adding new vulnerabilities
… makes me think about the ability to detect browser capabilities
… but pages can already do that

Nick: Is it the case that @supports rules will be general for UA, not user specific

Jeffrey: thats almost alwawys true.  Users could opt into experimental features, but rare

Aram: UA is a fingerprinting vector.  Some sites might block information in the UA, and sites could re-learn UA
… information using this, but changes in capability across UA are hard (impossible to block)

Jeffrey: I believe all browsers expose major versions, and Chrome doesn't change selector support with minor version bumps

Nick: Its good the spec authors mentioned similar concerns in the privacy considerations section

Aram: Are you (Nick) saying that the group should write such text?

Nick: The section in the spec already has that text (that this capability allows detection of UA major version)

## 2. AOB

* review comments on different types of implementations (imsc)

Nick: This is about how different implementers for a spec would have different implications for how we do a privacy review. Our general case is for web browsers, but the Web is more than that, and it's sometimes not obvious how to do a review.

Pete: Last call, did a review of formatting text on top of videos. Group has responded saying that pieces won't be implemented in browsers. Most of this call's attendees are focused on browsers and websites. How do we respond? "Enumerate the places this might be implemented"; "Forego horizontal review in these sections"; other approaches? What do others think?

Christine: This is a tricky question. Sounds like the group is saying you should review what's in front of you, but not how it's going to be implemented. But we can't separate implementation from the spec. We still need to do privacy reviews. Specification authors need to be mindful about how the spec might be implemented, although they don't need to anticipate every possible scenario. We need to understand the implications. The WG might need to go to outside experts. Not appropriate to ask the PING to not think about implementations.

Nick: Similar sense, that it's tricky. An interesting thing about specs is that they might get implemented in unanticipated ways. Should try to give some idea. If it's completely abstract, it's hard for any horizontal reviewer to give feedback. We want specs to give context about likely scope of implementations. Especially if it's not web browsers.

Jeffrey: Seems like a question to add to the S&P questionare; where is this thing going to be implemented.
… would also be good to think about what the issues are context dependent, and which touch the
… contexts intended by the proposal

Nick: Open an issue on the questionnaire?

Pete: I'll take that directly to the group. As background, the incremental font transfer spec, by considering it in the context of browsers, we found positive changes that make it work better in all places. It's not just pedantic to ask them to add this information; it has practical impliciations.

Nick: In the questionnaire, say "even if browsers aren't the only context, think about how a browser would implement this, and what implications there are."

Pete: Don't think the imsc group will be completely satisfied with this, but it's a good next step.

* triage `pending`: https://github.com/w3cping/tracking-issues/issues?q=is%3Aissue+is%3Aopen+label%3Apending

Nick: we should review pending issues, which happens when issues are opened on other specs (often not by PING members, by the group itself)
… Audio Render Interface and Related ??? PR.  Looks like Sam added the "privacy-issue" label spec-side, so this is a slightly different case.
… lets asign to Sam and leave the "pending" label once we hear from Sam on what he'd like to do

* docs for new reviewers

Nick: Would be good to have more documentation for new reviewers; we have a request.

Aram: I would appreciate a guide: here's the process, here's the expectations at each step, here's the information a review should have. Was thinking about this today, where you said it'd be nice if people pick up the tickets before discussion. We have the questionnaire, but what's a clear place of potential privacy risks that we look for. We assume people have some experience and that's fine.

Nick: There was a longer version of the questionnaire in a wiki that we're not currently using.

Pete: The chairs have drafted something like this, but we've never published it. I'll kick that along. Also want to be sure that we don't unnecessarily delay reviews.

Christine: I like the idea of a ticketing system, and we do have a way to track these in the privacy-requests github repo. Once someone volunteers, it's assigned to them. Typically we send out a note asking people to volunteer. Want to be careful not to make the process daunting. We have enough difficulty finding people with time & expertise to do the reviews. One thing that's worked really well (thanks Pete & Sam) is to partner with someone new. Yes, we can tell people to read documents, but a lot of the ability to spot privacy risks comes from experience, so partnering works really well. Pete has run a couple tutorials on privacy reviews. Thank you to everyone for all the privacy reviews. Sometimes WG interactions can be difficult, but it's really important.

Pete: Aram mentioned it'd be nice to have a ticketing system, and we do that, but we need to document it better. See https://github.com/w3cping/privacy-request. I'll get the documentation published.

Nick: Find below links to resources for doing reviews

Wendell: My positive experience: I signed up way back in the day to get socialized in this group, and it worked really well. Treated it like an academic paper review, since that's what I'm familiar with. Pete was really helpful. Jitters about speaking in front of other people, saying things outside of their culture, went away. *"See one, do one, teach one."* Seen people who've been nervous, and that's just a matter of being new. You get used to it. More docs are great, but should just jump in too.

Aram: I was aware of privacy-request repo, but the process around it is less clear. Not clear how to jump in.

Nick: Action items? Where do we want to put this documentation? README of the privacy-request repo? 

Pete: As a first go, I'll put it on github somewhere, and we can publish it somewhere more formal.

Aram: My inclination is the README of privacy-request repo.

how to get horizontal review: https://www.w3.org/Guide/documentreview/#how_to_get_horizontal_review
self-review questionnaire: https://w3ctag.github.io/security-questionnaire/
privacy-request repo: https://github.com/w3cping/privacy-request

* Other

Wendell: Thanks Sam for that blog post. Reminder to W3C sponsors about what they're getting for their money. These reviews are eventually read. 

Nick: It's useful to see it all put together.

Pete: Thanks to Christine who did a lot of work on that.

Wendy: Echoing thanks; will convey appreciation to Sam.

## next meeting

Nick: Next meeting is Feb 3. Will send an agenda ahead of time.
