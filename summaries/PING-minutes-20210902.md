# Privacy Interest Group meeting (2 September 2021)

## Attendees 

* Peter Snyder (PING Co-Chair, Brave Software)
* Christine Runnegar (PING co-chair)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C/MIT)
* Nick Doty
* Lionel Basdevant (Criteo)
* Sean Harrison (Google)
* Jonathan Kingston (DuckDuckGo)
* Don Marti (CafeMedia)
* Matthew Finkel (Tor)
* Theodore Olsauskas-Waren (Google)
* Theresa O'Connor (Apple, TAG)
* Aram Zucker-Scharff (The Washington Post)
* Jeffrey Yasskin (Google Chrome)
* Eric Mwobobia (ARTICLE19)
* James Rosewell (51Degrees)
* Newton Koumantzelis (Magnite)
* Brad Rodriguez (Magnite)

Scribe: Jonathan, PeteS

## 1. Privacy review of DOM Review Draft - Published 21 June 2021

### Background

* Lead: Matthew, Sam, possibly Eric

* URL of spec: https://dom.spec.whatwg.org/review-drafts/2021-06/

* What and when is your next expected transition? 2021-08-31, CR

* What has changed since any previous review? Please look at the list of [important changes](https://github.com/w3c/htmlwg/issues/19).

* Where and how to file issues arising? Please file an issue via https://github.com/whatwg/dom/issues.

This is issue [#49](https://github.com/w3cping/privacy-request/issues/49) in PING privacy-request repo.

### Discussion

Matthew: DOM spec is quite large, authors highlighted two areas. Abort functionality nothing impacting from a privacy perspective. Ads multi processing. There is not a priv/sec section, brought up 2 years ago. Conclusion was doesn't lend itself to this as a section. In retrospect, I think it is helpful to have this as a section. Even if there aren't concerns it's helpful to state that.
There have been prior reviews but no documentation of this and so it's clear what the prior understanding is.

Sam: Broadly agree

Tess: I have multiple hats, co-chair HTML spec in charge WHATWG collab. A long history of horizontal review. Challenge here is to help these documents get to a point where we are happy with them from a blind horizontal review process but aren't disruptive to WHATWG current processes. I'm supportive of this section for XHR attacks and others. Submit a PR for this section. Presenting historical facts.

Nick: There are lots of privacy questions around lots of features (mouse move events). Should we be pursuing it in DOM etc.?

Tess: yes I think mouse move is a known concern and interesting source of fingerprinting data (in whatever spec defines that).

Nick: UIEvents is at W3C Web Apps WG, does have a security considerations section, doesn't mention privacy issues: https://w3c.github.io/uievents/#security-considerations

Pete: This group might have different conventions. I don't think PR should be a requirement.

Tess: Yeah, file PRs or issues. (PRs are better, but opening an issue and letting the authors know about issues is always good too).

Sam: I can imagine other WGs preferring that we write this section for them also, and I would not want us to get into the habit of saying "yes".  Why should we treat this differently?

Tess: WHATWG does the work on the spec itself rather than the HTML WG.

Matthew: What is the nature of their resistance? Are there other reasons?

Wendy: Both trying to work on this. Still early in the W3C-WHATWG cooperation under [Memorandum of Understanding](https://www.w3.org/2019/04/WHATWG-W3C-MOU.html).  Aiming to be effective within WHATWG work mode and W3C's. I hope we can smooth the bumps as we go.

Nick: Are there privacy issues about how events are propagated or what scripts/entities can subscribe to them. Is it something that should be documented? Or is it all abstract and just focus on HTML, UI Events, etc.?

Matthew: There isn't much to say about priv/sec within the spec.

Sam: We didn't call out that HTML spec didn't have the privacy section.  Should we?
(npdoty: I thought that was about only just starting a longer privacy review of HTML, and that review was just on the recent changes.)

Pete: Yes, we should.

Christine: It sounds like there is consensus that it would be helpful to add this section, we should do for all specs DOM and HTML. I agree with Tess adding help here would be worthwhile in what this section should look like.

Tess: One great example of W3C horizontal review going well with WHATWG is i18n. I'd recommend looking at how they do it. Accessibility experts also proactively engage there, though I'm not sure offhand how that relates to horizontal review.

Jeffrey: It sounds like someone will make issues. There should be cross linking to specific privacy issues that should be considered. We can work incrementally.

## 2. Privacy review of CSS Scrollbars Level 1 

### Background

* Lead: Jonathan

* URL of spec: https://www.w3.org/TR/css-scrollbars-1/

This is issue [#53](https://github.com/w3cping/privacy-request/issues/53) in the PING privacy-request repo.

### Discussion

Jonathan: Briefly looked. This spec doesn't define much. Allows page author to color the browser's scroll bars. I did not find significant issues (re cross frames, etc); it seems to only be styling. Doesn't provide access to state (theming etc.) and doesn't allow access across origins/etc.

Christine: Thank you to Jonathan for the quick review, and Matthew and Eric for the DOM ones too. Please help, we need volunteers!

Sam: How should we notify the group we're done?

Jonathan: I added a comment to their issue

Christine: I will close the issue in our privacy-request tracker after the call too

## 3. Privacy review (requests received)

### a. CSS Masking Module Level 1

URL of spec: https://www.w3.org/TR/2021/CRD-css-masking-1-20210805/

This is issue [#50](https://github.com/w3cping/privacy-request/issues/50) in PING privacy-request repo.

Review assigned to Mu Lei. To be discussed on 16 September 2021.

### b. EPUB 3.3

URLs of specs: https://w3c.github.io/epub-specs/epub33/core/ and https://w3c.github.io/epub-specs/epub33/rs/

This is issue [#52](https://github.com/w3cping/privacy-request/issues/52) in the PING privacy-request repo.

Review assigned to Nick Doty. To be discussed on 16 September 2021.

#### Discussion

Nick: How do we review this, since it's not exposed to arbitrary web users, or not always browsable in the same way?

Tess: EPUB includes arbitrary web content, so there's lots of potential privacy and security issues with loading untrusted web content in an ebook reader. So lots to say, although lots is downstream of them, so don't tell them about pure HTML issues.

Pete: Font fingerprinting issues in maybe-EPUB. At least in the same category. 

(npdoty: captions had some similar implications)

Aram: Does this bring up the concept of dynamically-inserted ads, where you might request the EPUB file, and file is built with ads injected? That can create privacy risk.

Jeffrey: TTML was similar.

Pete: Might have issues where Web users would expect privacy issues, but ebook users wouldn't expect them.

## 4. Privacy tracking issues triage

Sam: We have two trackers; one is for review requests coming in.  The one we're discussing today though is for issues that have been previously filed against specs. The goal here is to both show how the tracking repo works, and to triage some recent ones. Usually these issues are not manually created. Usually they're automatically created by Github tooling, by `privacy-tracker` or `privacy-needs-resolution` labels on the issue _in the authoring group's repo_.

We should assign these to PING members, so we know who will deal with follow up on the issues. Being assigned owner of a tracking issue does not have technical / procedural significance beyond a note who is expected to monitor the issue.

Christine: PING members who are monitoring an issue should also feel welcome to bring updates back to PING and/or ask for help in handling interactions on the issue.

Sam: Each tracking issue links back to the original issue in the authoring group's repo.ometimes PING adds the relevant `privacy-*` issues, sometimes the group does.
… For example: Is anyone interested in #242 (ambient light) spec?

Jonathan: I am!

Sam: Okay I will assign you.

Christine: you can add me too

Sam: other tracking-repo side labels: `closed?` means the WG has closed the issue. Dark green labels tell you what spec things came from. Sometimes it might make the most sense for an issue to be assigned to a PING member who has been involved, even if they didn't file the issue.
Sometimes we also get tagged on things from the TAG. PING would welcome anyone to take ownership of these issues.

Christine: For that last category of issues, groups might not have done S&P questionnaire.  It may often make sense to request the group do so first and to formally request a privacy review when they are ready.

Matt: Question about the labels; do labels require special powers?  I don’t seem to have those powers?

Sam + Christine: we'll get that sorted.

Sam: If you have the rights in the authoring group's repo, you can also add labels there instead. Assigning all the mediacapture-image issues to Pete. WebXR raw camera access, anyone interested?  It’s also TAG Review level (Theo volunteers, thanks!)

Christine: thank you Sam for the demo; reminder that pending means its shown up but not triaged.  And thank you again to everyone who's volunteered to own a tracking issue

Sam: Jonathan were you going to take Baggage?

Jonathan: Nope, ambient light

Christine: Folks, please join the repo.  Please request if needed, we'll send invites too

Note: The Github assignments are being recorded in the tracking-issues repo

* #244 - https://github.com/w3cping/tracking-issues/issues/244 (assigned to Mathew and Sam)

* #243 - https://github.com/w3cping/tracking-issues/issues/243 (assigned to Sam)

* #242 - https://github.com/w3cping/tracking-issues/issues/242 (assigned to Jonathan and Christine)

* #241 - https://github.com/w3cping/tracking-issues/issues/241 (assigned to Sam)

* #240 - https://github.com/w3cping/tracking-issues/issues/240 (assigned to Pete)

* #239 - https://github.com/w3cping/tracking-issues/issues/239 (not assigned)

* #238 - https://github.com/w3cping/tracking-issues/issues/238 (assigned to Pete)

* #237 - https://github.com/w3cping/tracking-issues/issues/237 (assigned to Pete)

* #236 - https://github.com/w3cping/tracking-issues/issues/236 (assigned to Pete)

* #235 - https://github.com/w3cping/tracking-issues/issues/235 (assigned to Pete)

* #234 - https://github.com/w3cping/tracking-issues/issues/234 (assigned to Pete)

* #233 - https://github.com/w3cping/tracking-issues/issues/233 (assigned to Theo)

* #232 - https://github.com/w3cping/tracking-issues/issues/232 (assigned to Nick and Sam)

## 5. AOB

Update to PING members concerning the progress, stakeholder input, and expected deliverables of the "Web Privacy Principles Task Force" - https://github.com/w3ctag/privacy-principles

Sam: James, you were asking about the privacy principles doc.  The TAG has a task force here.  Most answers can be found on the repo.  Reminder that the current text does not represent group consensus yet

James: I asked the question because I have been following the work.  I've been following it.  Many of us have worked on interop and related specs.  What input is being solicited, and on what timeline, and with what process.

[Kitten Cluster ('Kitten' for shorthand) - Privacy Defintion](https://github.com/carbondmp/Kitten_Cluster#210-privacy-defintion)

[W3C Improving Web Advertising Business Group - Success Criteria in reference to Individual, Social and Business Concerns](https://github.com/w3c/web-advertising/blob/main/success-criteria.md)

[Self-Review Questionnaire: Interoperability, Choice, Accessibility and Accountability ](https://github.com/w3c/web-advertising/blob/main/interoperability-choice-accessibility-accountability-questionairre.md)

Sam: The group hasn't solicited input, but we'll let folks know when we do?

James: Will PING mention it on the agenda?

Sam: Not sure what PING's role will be; task for is organized by the TAG

James: I thought it was joint between PING and TAG?

Sam: I think its TAG convened and they're the drivers.

James: okay, i think it’s important for the doc to incorporate everyone’s input

Nick: How to divide the work up? How does this interact with the threat model document?

Jeffrey: Some of the principles have made their way into the principles document.  How the principles document proceeds can guide what stays in the threat model

(npdoty: happy to help wherever I can, as I think I had some open items on the threat model draft regarding principles)


Sean: Question to co-chairs, could you set the zoom call to auto-mute participants on join? [Sam: done.]

Eric: this was my first time reviewing, PING chairs were helpful

Lionel: Thanks to the task force for the definition work on privacy. Privacy is a key concept for much of the work done these past months. We'll be happy to help for reaching a broad consensus.


