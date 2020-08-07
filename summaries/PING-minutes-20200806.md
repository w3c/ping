# Privacy Interest Group meeting (6 August 2020)

Scribe: Sam & Pranjal

## Attendees 

* Chris Wilson (Google)
* Christine Runnegar (co-chair)
* Dave Harbage (DuckDuckGo)
* Eric Mwobobia (ARTICLE 19)
* Erik Anderson (Microsoft)
* James Rosewell (51Degrees)
* Jeff Wieland (Magnite)
* Jeffrey Yasskin (Chrome)
* Kris Chapman (Salesforce)
* Lisa LeVasseur (Me2B Alliance)
* Lubna Dajani
* Mallory Knodel (CDT)
* Michael Kleber (Chrome)
* Nick Doty (UC Berkeley)
* Paul Jensen (Chrome)
* Pete Snyder (co-chair, Brave)
* Pranjal Jumde (Brave)
* Sam Weiler (W3C/MIT) 
* Scott Low (Microsoft)
* Sean Harrison
* Shaun Gilmore (Apple)
* Theresa O'Connor (Apple)
* Wendy Seltzer (W3C)
* Theodore Olsauskas-Warren (Google)
* Joe Lukas (Magnite)
* Tanvi Vyas (Mozilla)
* Brad Rodriguez (Magnite)

## 1. PING mission

Pete: James, you had some questions?

James: new in past ~4 mos.  My goal is to understand how docs that talk to privacy are constructed.  My questions are very broad.  I've filed comments re: balancing multiple concerns/issues e.g. anti-trust policy.  IF we have a standard being advanced that impacts for competition and privacy e.g. definition of 1st and 3rd parties.  How do we balance those issues?  I get a feeling that W3C isn't yet ready to embrace.  Not sure if that's a question.  Interested in listening and understanding.

Pete: The best place for this discussion is in GitHub, where there can be asynchronous discussion, and to get more participation.  If you have other ideas for where, feel free to email me or suggest them here.

James: I have four questions outstanding. I'll continue to pursue them there.

Christine: As several people have joined PING recently, it may be helpful to review why we are here.  We are chartered to reduce privacy risks and fingerprinting surfaces.  James, the issues you're raising may be better dealt with elsewhere in W3C.

Wendy: James, in framing questions, mention of anti-trust is likely to signal that it's not a question for W3C at all and instead drive people to seek legal counsel rather than engage.  There are issues behind that - of opportunity for interoperability and choice; framing that way would invite more discussion.

Nick: Process CG might be a relevant place for these discussions.  We often hear "there might be competing interests".  Perhaps a point of broad horizontal review is to have multiple groups looking at different issues; e.g. privacy group might not well understand i18n issues, and vice-versa.

Pete: The email list is also a good place for these conversations, if GitHub doesn't seem to fit.

Jeffrey: discussion of competition and ecosystem effects reminds me of some discussion in IETF.  They also have a human rights group that looks at other issues in addition to privacy.  I agree that this might apply in Process; we might be missing some horizontal groups.

Pete: agree.

(npdoty: +1! here's the HRPC at IETF: https://hrpc.io/ and they have early experience regarding human rights reviews generally)

Note: HRPC is in the IRTF not the IETF

## 2. Privacy review request from the WebRTC WG of its MediaStreamTrack Content Hint spec

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

Pete: Kris and I will work on this.

## 3. NEW (came in last night) Privacy review request from the Devices and Sensors API WG for Screen Wake Lock API

Current ED: https://w3c.github.io/screen-wake-lock/

This document specifies an API that allows web applications to request a screen wake lock. Under the right conditions, and if allowed, the screen wake lock prevents the system from turning off a device's screen.

Substantive changes since the last CR are documented here: https://w3c.github.io/screen-wake-lock/#changes-20171214

Link to the Security and privacy considerations section:
https://w3c.github.io/screen-wake-lock/#security-and-privacy-considerations

Request for issues to be filed at https://github.com/w3c/screen-wake-lock

Pete: This just came in.  Anyone with particular interest?  Otherwise we'll go through list.

Pranjal: ME!!

Pete: YAY!  Two weeks?

Pranjal: Ok.

Eric: What kind of expertise do you need?

Pete: in general, when we get requests from WG; we ask people who might know how that feature works to do a review, if they're available, otherwise to people who have done privacy reviews generally.

## 4. Brief updates from previous privacy reviews

Pete: WebAudio is wrapping up. WG and PING reviewers seem happy; good work between groups. Geolocation API conversation ongoing.

Encourage people to engage in those.  

- https://github.com/w3cping/tracking-issues/issues/114
- https://github.com/w3cping/tracking-issues/issues/112
- https://github.com/w3cping/tracking-issues/issues/111

## 5. Privacy threat model (working meeting)

Agenda
- Progress updates
- Document structure approach and discussion
- Next steps, PRs and Unblocking

Link to draft: https://w3cping.github.io/privacy-threat-model/

Pete: This doc is intended to provide guidance to spec authors; what sort of things are in scope.  and as guidance to our own thinking, to help review consistency, and so results are understandable to the outside.

Jeffrey: Few changes since last meeting about the threat model.  I would like a second set of eyes on some PRs.  But if they're blocking people, I can merge them anyway.  High level threats section needs to be expanded, and that's not in my expertise; I need help.  Low level threats section needs expansion. I've been working on WPACK.

Pete: Any interest in participating?  e.g. I could turn high level threat issue into text.  Anyone else want to take a piece?

Eric: Question: how to understand evaluation high, medium low risks?

Jeffrey: Threat model document doesn't currently try to assess risk level. We could add that to the document (such as issues not about cross site tracking might be better for a non-binary label here). PRs welcome.

(npdoty: +1 on severity descriptions, even if we can't make it completely detailed. )

Eric: I will give it a try, thanks!

Shaun: Is there consensus on the overall structure of the document?

Jeffrey: The overall structure of the document may not be useful for arriving at consensus for the final shape of the document, but there are competing goals: don’t break the web vs privacy. The current document might not be currently in the right shape to get to consensus on this. Particularly on "don’t break the web."

Kris: The document talks about types of threats (same site vs cross site recognition), I think there should be more about "user want /consent"; document seems to assume it’s never wanted.

James: What is the definition of right privacy. Browser fingerprinting can be seen as a good or bad thing e.g: elimination of fraud. Beneficial for stakeholders on the web. Better understand the answer to right privacy?

Sam: Want to be cautious. Fingerprinting helps to prevent fraud. Bad slope, it helps law enforcement if we don't encrypt things. Having explicit mechanisms that hidden fingerprinting might have been used for. Covert mechanisms should not be enabled if overt ones are available.

Kris: Where we draw the line in the threat-model is important.

Pete: Here is a privacy principle should be upheld. 

Christine: If memory serves, the Web Payment Security IG, recognizing that the Web is changing and getting more privacy features, they are actively looking at not relying on fingerprinting – looking for ways to do what they need in a more privacy-respecting way. Their work might be interesting to look at.

Jeffrey: WebID should be allowed by the threat model. Needs to describe how users can opt-in to cross-site recognition.

Lisa: Preference and privacy right depends on context. Eg: you're logged in, you are allowing certain things to be remembered. Threat/Attack language is violent, consider human-rights focused language like risk/harm instead.

Nick: No specific definition of privacy. Better not to have a simplified definition. Highlight privacy threats. In some cases, we can have capabilities that don't have privacy harms, because of user controls or transparency or opt-in etc. 

James: +1 to Lisa

Jeffrey: Threat/attack are more violent than I intend.  Missing a term.  Harms/risks, yes.  Then there's the mechanism by which someone causes harm.  I've been calling that an attack; I welcome another word.  

(npdoty: I think we are using "attack" and "threat model" from experience in the security world. jyasskin: Indeed, but that doesn't mean they're the best terms. erik: maybe "circumvention" in some contexts?)

James: I've been creating a doc elsewhere; I like "harm" and "risk".  Widely used elsewhere.

Pete: I want to suggest concrete ways forward.  Some people have made specific text suggestions.  I'd like to assemble them in Slack (and others are welcome).  I'd like to try to get concrete PRs before our next meeting in 2 weeks.  Others like this approach?

Kris: +1

Lisa: +1

Jeffrey: Are people blocked by outstanding PRs and should I just merge them?

Pete: Let's work that out on Slack in next 24-48 hrs.
