# Privacy IG meeting, 18 April 2019
## Agenda

1. Experimenting with new tools - Zoom, Cryptpad and Slack
2. Update from the recent AC meeting
3. Discussing big PING ideas (see the latest email on the thread [here](https://lists.w3.org/Archives/Public/public-privacy/2019AprJun/0007.html)
4. Discussing the proposed charter for a new Media Working Group (and EME, privacy implications)
5. AOB

## Present (sign yourself in)
- Tara Whalen
- Mike O'N
- Christine R
- Sam Weiler
- Craig Spiezle
- Brent Zundel
- Jason Novak
- Peter Snyder
- Pranjal Jumde
- Wendy Seltzer
- Pranjal Jain
- Terri Oda

Mike O'Neill will start as Scribe


## Experimenting with tools

Christine: I suggesting typing "hand" in the Zoom chat window rather than use the Zoom "raise hand" tool - that keeps the queuing in order.

## Update From AC Meeting

Christine:  report from AC meeting - Tara
AC Meeting: "Advisory Committee Meetings are Members-only meetings that focus on strategic issues facing the Consortium and future directions envisioned by the Membership and Staff."
Smaller than TPAC (about 100 attendees?)
[Members can see meeting details](https://www.w3.org/2019/04/AC/Overview.html)
Privacy Panel: Wendy Seltzer (moderator), David Singer, Sam Weiler, Pete Snyder, Tara Whalen, Katie Haritos-Shea 
included presentation + discussion about PING
Well received, lot of interaction from audience, someone signed up to PING during the panel. 
We want to improve the PING practical work, reviews etc.
What else can we do? (strategy, big ideas)
Pete: Normative rather than non-normative well received, Jeff said help us clean up the mess

## Discussing big PING ideas
(see the latest email on the thread [here:](https://lists.w3.org/Archives/Public/public-privacy/2019AprJun/0007.html)

Big PING ideas?
Pete to lead
How do we deal with legacy functionality?
Can talk over whats in email.

The ideas from Pete's email

1) Determine all rarely used browser functionality (difficult, but I have ideas!), any for any functionality behind a certain threshold, put it behind a permission prompt and / or block it until there is a user gesture in the frame and / or block access to it from 3p code.

2) Use an APIs similar to Trusted Types (e.g. strings that know they’re different from other strings, or kinda-sorta a facsimile of taint tracking) to prevent values from storage syncs from moving across frame boundaries / network sinks.

3) Flip the script on iframes; define a restrictive default feature-policy on all 3p frames.

4) Add idea of feature policy for scripts, define default restrictive feature policy for scripts, make this the default for sites taking advantage of Y new nice feature (HTTP3 / QUIC, etc.)


Christine: (ancient history - things have changed) - remember geolocation, idea was that we should encrypt the data, overwealming response the status quo will be upset, sites will break etc. - challenge is changing specs when already widely deployed 

Sam: we should work out what we want to do, process will work itself out
Pete: lets define some  functionality existing spec to take alook at
Jason: like the local IP address funcionality hat was looked at in WebRTC
Christine: Battery status API
Jason: makes sense to start with a unique thing we can have a win with, is there an API that is being used for abuse case.
Jason: e.g. the cookie spec.
Pete: needs to be something infrequently used for benign purpose.
Jason: if we make our goal look at cookie spec, we may not get a win.

Christine: what would be a good target?
Pete: webgl, webaudio, gating existing functionality behind permission prompts.
Jason: fonts are a tractable problem.  WebFonts has been so widely adopted that browser-supplied fonts are less interesting.  I nominate it for first target.
Jason: font enumeration for fingerprinting.
Sam: bluetooth, USB?
Christine: point us to research that this is a problem
Where is right place to attack in specs
Pete will find research showing that font enumeration is a practical fingerprinting vector, and will take a stab at suggeting where the change could be written into a standard.x
Christine: where do we want to see changes made? Anything else on big ideas?

## Slack Interlude
Christine: Tara interlude on Slack
Tara: we just created a new Slack workspace for PING
Tara: should be an email with Slack invite (sent to all PING members)
Tara: little bit of experimentation, feel free to organize as you feel best. Goal is to foster conversation and community, allow for dynamic interaction. 

Christine: idea is not to replace email list, tool is useful to explore topic when a quick call would be helpful

## Discussing the proposed charter for a new Media Working Group (and EME, privacy implications)
Christine: proposed new charter for a new media WG, folding in DME into this group
are there Privacy ramifications of this?
Jason: Should we finish talking about the big ideas?

## Back to Big Ideas for PING (numbers 2, 3, 4)
Pete: trusted types, look into possibilities for privacy mitigations.
Pete: Feature Policy, can disable functionality, lets look into this from Privacy POV
Pete: Carrot and stick approach for new APIs.
Mike: How do we interact with these groups and organize our response?
Sam: wish we had Mike West was here.
Wendy: we can also post in the [feature-policy repository](https://github.com/w3c/webappsec-feature-policy/)
Sam: [next webappsec meeting May 15th](https://www.w3.org/2011/webappsec/): meeting info at top of page: 

[One of the Mike West things](https://github.com/mikewest/http-state-tokens)

[Another Mike West thing](https://speakerdeck.com/mikewest/cookies-are-bad-at-http-workshop-2019)

[One more](https://mikewest.github.io/http-state-tokens/draft-west-http-state-tokens.html)

It was suggested to review these before the next meeting.

## Back to new Media WG discussion
Sam: new media group will take over EME
Sam: digital rights management, my pet issue tech measures get in the way of things, from privacy you cannot look into modules so you cant see what they are doing


Mike: are there channels for data that we should make more explicit?

Wendy: AC review lasts a month, we are in middle of that. There is a new fingerprinting surface
Wendy: interaction with anticircumvention provision of DMCA makes it hard for privacy and security researchers to find out what is happening,
Christine: Do have Apple, Brave have positions on EME
Jason: will check internally
Brave: ditto

Christine: is there something we hae in our fingerprinting document which is relevant
Christine: transparency is issue, what is impact on privacy/security research,
Wendy: has put up link to draft charter

https://www.w3.org/2019/04/media-charter-draft.html
"add four minor features incubated in the Web Platform Incubator Community Group since then, namely: Persistent Usage Record sessions, HDCP Detection, Encryption scheme capability detection and an API to find existing sessions."

## AOB

### Device Orientation at FPWD

Next call: 16 May 2019 ?
Happy with Zoom?

-- will keep this notes page open for a short while (rest of day) for people to fix up notes, add things etc and then we'll move it to The Real Minutes

Mike: where can I post documents in PING github space?
Sam: in the w3cping organization.  I suggest one repository per document.  Give me the doc names and, with chair consent, I will create those for you:

https://github.com/w3cping/storage-policy
https://github.com/w3cping/server-declaration
