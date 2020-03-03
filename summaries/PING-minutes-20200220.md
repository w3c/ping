# Privacy Interest Group meeting - 20 February 2020


## Attendees

* Peter Snyder (co-chair, Brave)
* Tara Whalen (co-chair, Google)
* Kris Chapman (Salesforce)
* Terri Oda (Intel)
* Tom Lowenthal (Brave)
* Wendell Baker (Verizon Media)
* Nick Doty (UC Berkeley)
* Shivan Sahib
* Michael Kleber (Google)
* Theresa O'Connor (Apple)
* Dave Harbage (DuckDuckGo)
* Brent Zundel (Evernym)
* Pranjal Jumde (Brave)
* Melanie Richards (Microsoft)
* Jeffrey Yasskin (Google)
* Zach Edwards
* Martin Meyer (Akamai)

apologies: Christine Runnegar, Wendy Seltzer

## Agenda and Minutes:

Scribe: kleber

### 1. Privacy reviews 

##### Current: Identifiers for WebRTC’s Statistics API 

https://www.w3.org/TR/2020/CR-webrtc-stats-20200114/

**pes:** Extension to WebRTC API for collecting statistics about connection (network bandwidth, codecs used, packet through-rate, etc.).  Two concerns about spec:

 1: fingerprinting surfaces exposed -- do these just correspond to OS, or is there per-user information being revealed?

 2: cypertext lets you extract underlying plaintext from shape & size of packets, which is relevant because sometimes site doesn't have access to underlying communication, so this might leak new stuff.  May be addressable by limiting codecs, or may need to limit what stats can be collected, or may need additional user opt-in if it's not otherwise possible to remediate the risk

**npdoty:** API for debugging is a worthwhile use case to discuss -- may want to distinguish ongoing statistics collection from debugging use cases when something is already going wrong.  These modes both come up with some regularity; "extra information to fix a problem" maybe should be treated differently in our privacy reviews.  Other examples: error reporting, ...

**pes:** Crash logs, OOM errors also of this nature.  Don't know of any way to signal that in the platform now.

**TomL:** Good to think about whether these serve the needs of the person using the browser.  Platform wasn't designed to distinguish these use cases, and so sites tend to assume they don't need any extra UI prompting, since no additional friction to using the API.  Maybe these debugging use cases could be automatic in some UA's but require explicit consent in other UA's; would be nice if specs clearly cleaved off the parts that maybe should require hightened permissions to access. Thank you Nick for identifying this category — it's a useful mental model.

**pes:** The line between these two modes may not be entirely clear; developer aids are ambiguous.  Keeping these code paths out of common availability may help security as well.

**Jeffrey:** Are these APIs promise-based?  Policy is that they _should_ be, and if so then we can inject permission dialogues without breaking stuff.

**pes:** Not sure, will take AI to ensure stuff is async for future flexibility, if it's not already.  We (PING) should ask our friends in PrivacyCG to distinguish this mode.

_npdoty in text:_ I think the RTC Stats is promise-based -npd
https://www.w3.org/TR/2020/CR-webrtc-stats-20200114/#example-of-a-stats-application

**Tess:** SGTM

**WBaker:** SGTM

##### Previous: Trace Context

https://www.w3.org/TR/2019/PR-trace-context-1-20191121/

**pes:** Trace Context moved forward without all PING issues being addressed.  Nick agreed to re-review spec to look at open things, and post-mortem on what went wrong in process.

**npdoty:** Interactive discussion in 2018; issues were opened on github, changes were made in response and issues were then closed, but PING didn't re-review afterwards to see if they felt the changes addressed all the issues.

https://lists.w3.org/Archives/Public/public-privacy/2020JanMar/0026.html

Mitications section could have benefitted from re-review, which didn't happen before publication as a W3C REC.  We should re-review, and also give guidance on how to write a privacy mitigations section, not discouraging use of mitigations.

**pes:** Thank you Nick.  We should have some PING-owned linkage between something in our own repo and the spec owner's repo, to help keep track of possibly-still-open items in our opinion.  Going forward, PING's increase horizonal-review role should help here too.

### 3. Font Fingerprinting

**pes:** Jeffrey produced [proposal](https://github.com/w3cping/font-anti-fingerprinting) that PING and PrivacyCG are iterating on, CSSWG will participate also.

More successful approach to legacy fingerprinting surfaces: PING identifying issue, raising with working groups, then PrivacyCG incubating proposed ways forward, PING bringing it back to relevant working group.

**Kris:** response from Media Lab: [Browser Fingerprinting: A survey, Laperdrix 2019](https://arxiv.org/pdf/1905.01051.pdf) for something recent; Media Lab data is out of date, ~10 years old.  Will bring this to the Privacy CG.

**Jeffrey:** Counter-proposal from Pete, not yet integrated into explainer.  Document moved to the PING rather than the Privacy CG. Yet? Awkward until Google joins.

**Tess:** Great example of work that the Privacy CG ought to take up.

**pes:** What is the way for PING and PrivacyCG to collaborate on this?  PING identifying problems / PrivacyCG making proposals to improve?  Something else?

**Tess:** Obvious difference is that PING is responsible for horizontal review, so they are in a position to work with WG's on their specs.  PrivacyCG is the right place for new privacy-preserving approaches to things.  Similar to TAG arrangement on security.  PING's horizontal-review opportunity is the time to find new privacy points of view that haven't been taken up yet.

**pes:** How about existing specs, not at the horizontal review time?

**Tess:** That's perfectly good; PING review of CSS fonts spec is an example.  Bringing them to PrivacyCG is the right way to get appropriate expertise from a wide range of communities in the room to hammer out ideas for fixes -- low barrier to entry.

**Jeffrey:** Note that in PING, our W3C staffers are very welcoming to invited experts.

**npdoty:** What work happens where?  PrivacyCG is clearly right for whole new privacy specs, but is it good for improvements to other specs as well?

**Tess:** Yes, we want to do new work there and also for stuff that would be challenging to do elsewhere.  Current example: Storage partitioning, which is likely to turn into many PR's across many existing specs.  This is paying down technical debt, where Safari did this a while ago and other browsers are very different right now.  Having a central place to talk about it and to track cross-cutting issues is a good role for PrivacyCG.

**Jeffrey:** Agree with Tess that it's awful to modify WHATWG specs as a single PR against the spec; very good to have another place to work on it.

**pes:** PING will keep owning minor changes, will refer to PrivacyCG for whole-new-cloth ideas or for larger work items on other WGs' stuff.

### 4. New Web developments and privacy considerations 

**pes:** No new WICG issues.  Anything else new to review?

**npdoty:** Personalization semantic content module specification, from Web Accessibility Initiative:
https://www.w3.org/mid/50989c64-c4b3-1d86-f2aa-b601880d6111@w3.org
https://www.w3.org/TR/2020/WD-personalization-semantics-content-1.0-20200127/

Resize observer and scroll anchoring don't seem particularly privacy-focused.

**Jeffrey:** Going to check in on some media stuff, still outstanding.

### 5. AOB

**Kris:** European Commission announced new strategy for Data & AI in the EU and what it might change for regulations.  Will share link.  It's early stage now, "what we're going to be doing." https://ec.europa.eu/info/sites/info/files/communication-european-strategy-data-19feb2020_en.pdf

## Questions
Is there a (semi-)public URL for these minutes once the cryptpad is complete? Yes, it's https://github.com/w3c/ping/tree/master/summaries

Post meeting note: minutes can be found here https://www.w3.org/Privacy/IG/meetings.html
