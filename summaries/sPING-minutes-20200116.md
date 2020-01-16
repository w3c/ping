# Privacy Interest Group meeting - 16 January 2020


## Attendees 

* Tara Whalen (co-chair)
* Peter Snyder (co-chair, Brave)
* Christine Runnegar (co-chair)
* Pranjal Jumde (Brave)
* Wendy Seltzer, W3C
* Hannah Quay-de la Vallee (CDT)
* Dave Harbage (DuckDuckGo)
* Scott Low (Microsoft)
* Melanie Richards (Microsoft)
* Jason Dorweiler (DuckDuckGo)
* Wendell Baker (Verizon Media)
* Anthony Nadalin (Microsoft)
* Jeffrey Yasskin (Google)
* Michael Kleber (Google)
* Brad Lassey (Google)
* Paul Jensen (Google)
* David Benjamin (Google)
* Konrad Dzwinel (DuckDuckGo)
* Terri Oda (Intel)
* Martin Meyer (Akamai)
* James Fishback (Wikimedia)
* Theresa O'Connor (Apple)
* Steve Morris

scribe: Melanie (big thank you!!!!)

## Agenda and Minutes:

### 1. Privacy threat model (update - Jeffrey/Tom)

https://github.com/w3cping/privacy-threat-model
  
**Tom:** little bit of a slowdown over the new year, apologies. Good bit of back and forth about PRs and issues in the doc, thank you especially to those have looked and commented on the PRs / opened issues. I'd like to encourage everyone doing privacy review, any time you see a potential privacy issue, risk, threat, and there isn't a section of the threat model you can readily cite, that sounds like an issue with the threat model. Would like to encourage you to open an issue on that repo. Right now we have mostly a lot of detail in a cross-reference of actor capabilities and the things they should(n't) be able to do. We're working on some more expansive reference material that should help give more of a general understanding more than point by point of what the expectations are.

**Pete:** was hoping for discussion of higher level stuff rather than specific issues. Can you talk about the roadmap?

**Tom:** that's the task we assigned me on. Some may recall vibrant convo at TPAC where we outlined in broadest terms capabilities that should and shouldn't be available to sites, reasons that people should/shouldn't expect it. That's what we'll add. The core of it is a 6 point list, my hope is to put some text around that to express the less mechanical, the more intuitive notions that form that list. Express the underlying intuition.

**Pete:** thanks again to Tom and Jeffrey.

**Wendell:** on these sorts of things, these vision concept documents, where is the sense of where these go? One can imagine they get written, and a certain class of folks are like "yeah yeah that's fine, but for those of who live in the real world..." and they get ignored. How should we support the process and not ignore these as theoretical? (Are they a checkbox etc)

**Jeffrey:** to answer that, I think that people writing specs will need to go through the threat model and check their spec against it. Privacy/sec questionnaire can be an entrypoint into it. The threat model will be helpful in grounding privacy reviews that this group does, convincing to those writing the specs, privacy group can say "you violated this, here's the attack". People writing specs can understand rather than theoretical.

**Wendell:** yeah, that's a helpful framework.

**Jeffrey:** reason to go from high level to concrete attacks is so that people can join it at level they're comfortable with.

**Tom:** want to echo, I envision that double role. A precheck for spec authors to not be surprised by privacy review. Between this and questionnaire, no reason to be surprised by outcome of review. And creating consistency in what we're looking for in reviews. Limit confusion and back and forth...we can fundamentally this issue is something addressed in x section, and why that's a big deal is paragraph 3 in intro.

**Jeffrey:** I think we can describe low-level attacks in parallel to high-level. Any time something comes up in review that's not in the model, we should try and fit into the model.

### 2. Discussion of specific privacy reviews:

#### Screen Capture - https://www.w3.org/TR/2019/WD-screen-capture-20191119/ (led by Wendall)
  
**Pete:** two specific questions I had. Things related to the structure and lifetime of device IDs. Wendell, we chatted, have you heard back on that? Right now current API returns UUID-like persistent identifiers for hardware on your machine, that seems like a big risk, probably more private ways to accomplish. WG said it would be hard to remove from existing, could move to something more private. 

**Wendell:** as I read, did not see a proposal for a new scheme. I'd have to conclude that they'll come with up new naming and numbering scheme, which would be different from careful scheme of OS developers. Not able to dream up one my self. Unsatisfying. I worry that this req is perhaps too tall an order, and that's reason for the response. Can't fix current because OSes have settled on this unique naming and numbering. So no confusion across OSes. No I didn't see anything, and 2) it's a tall order. Process question: what do we do about such things? When we're expecting something spec writers are not within their control to address?

**Tom:** I like that framing, particularly comparison to OS approaches. I think OSes have a diff set of reqs and goals than standard authors should. Being uniquely identified by GUID of CD rom drive when the thing IDing you is the driver. But uniquely ID'd by a site IS a big deal. Makes sense there's differing reqs. The fundamental obligation of spec author is to ensure that their spec doesn't harm web plat, privacy, sec. So if they don't have a safe way of doing things, they should not be doing those things. So in some cases, they have the difficult task of creating API that doesn't allow for unexpected persistent unique ID. To extent that is an open research question, their ability to complete spec is dependent on satisfactory answer to research challenge.

**Jeffrey:** already have hard req of not sharing ID across origins. Growing req of not sharing with subframe origins (not original use case). So they're already doing some re-mapping. UUIDs to UIDs. I haven't followed Pete's detailed argument about small integers, if it's a hard req, want it in the threat model, otherwise if it's a guideline, then spec might be alright in its current state. *scribe missed some details, feel free to fill in*

**Pete:** the current API globally IDs every device on internet, which is much more than is needed. ID a single device on a single origin is what's needed.

**Wendell:** ok, agree and understand with all of it. Tom's point deserves discussion: if I can paraphase, if what you're doing is dangerous as defined by this group, you may not do it. We give a no vote. I've worked with folks in action mindset, they don't take well to that input. They'll launch anyway and clean up in post. Is there some other stance we can take that gives avenue other than a hard no? I don't have great suggestions, but giving someone no option but to break the law is going to end up w/ law breaking.

**Tom:** I stand by sentiment. First, do no harm. Can't achieve, not part of the web plat. This is not a no, this is "these are the properties you need to achieve, you must provide property of not being uniquely ID'd". They need to work out how to work w/ these reqs. Want PING review as part of spec process.

**Jeffrey:** don't think gating on PING will prevent harmful specs from getting out. We've seen groups blocking Chromium proposals in W3C/WHATWG standards, but they still get shipped in Chromium. My and Michael Kleber's job is to ensure Chromium review process is aligned to what PING wants. Will require negotiation between Chr process and PING reqs. If there's a disagreement about what's a harm, we should talk about that. If it can't get shipped, it doesn't get exposed on the web, no matter what people propose. In this case, re-mapping IDs will helpful getting them to ship, and we can specify that. Other are harder...direct access to TCP sockets. Discussed so many times, always a no, can't figure out how to do it safely. In many cases though we can find ways to do it safely.

**Pete:** I will take this action item on, also lifetime of permission, will file as an issue.
  
#### Resource Timing Level 2 - https://www.w3.org/TR/resource-timing-2/ (led by DuckDuckGo team)

**David:** We're reviewing Resource Timing Lvl 2, which extends the existing Resource Timing Lvl 1 standard to provide more detailed network performance data on requests. Resource Timing Lvl 2 is already fully implemented in Chromium and partially implemented in several other browsers, so we were able to do some testing and research on how it's being used in the wild today. 

Detailed performance information for third party resources is by default unavailable to the site loading them, but those resources can opt-in into making that information available via a timing-allow-origin response header. For that to work, the header must be present on requested resources with a value of either: the domain or domains where it should be enabled, or a wildcard. The majority of the issues we discovered are related to the use of a wildcard in this header, which allows any website to access detailed resource timing data for a third-party request.

**Jason:** since this is already in use, we want to get an idea of how used in the wild. Crawled top 50k sites, looking for 3p requests using timing allow header. Roughly 1.1 million requests already using header, 95.4% of those are using wildcard value. Konrad has details on possible threats.

**Konrad:** starting from most impactful, some issues related to level 1. First, linking info about proxy usage. Level 2 gives info about next protocol for a given resource. Will reveal if using proxy info or not. If we know resource delivered with HTTP/2 + QUIC, but we see something different, might be proxy. Given potential to expose proxy usage, should be clear what benefits of including this data are and benefits outweighing the negative? Second is leaking state by accident. Header size, response size, it's easier to accidentally leak info about users being logged in. Also note that level 1 was there for some time, by level 2 we are automatically opting in all the resources into sharing more information with first parties. Suddenly harmful info, there's more of it, and it can leak side effects like log in state. Vast majority use wildcard, which open up ways of leaking browser history, and can be used for fingerprinting. One is extracting info from DNS cache. This is level 1. HSTS info, this is again level 1. Extracting secure reused connections, hinting that it was opened recently in another tab, again from level 1. We can also extract info about if cookies were sent with a given resource by looking at response size. If cookies are transferred, have to set the header, can look at the size of the header to figure out if cookies were sent.

**David:** most of these issues stem from issues of wildcard and timing-allow-origin header. Wildcard is default, most cases using it. Our suggestion would be to drop the ability to set wildcard. Servers can basically spoof that, more explicit and requires more work for developer. Another option is unsafe all for wildcard instead of asterisk. We think wildcard should not be default.

**Jeffrey:** wondering how double-keying caches effects privacy issues you're worried about.

**Konrad:** we haven't looked in detail, Pete suggested it and we plan on it. We know CDN cache info is not double-keyed, so it can still be extracted.

**Wendy:** thanks for doing the research as part of the review and how it's used in the wild, very helpful.

**Michael Kleber:** on question of star, unsafe all...going to remain a problem. The people who send timing-allow-origin headers and are happy to let other domains figure out how long it took to load, reason why this happens is something like, I'm an ad company who wants to load ads and want to know which one of those are slow. Question: am I willing to let other people look at my timing info is about, is my privacy as someone who serves stuff, are my biz interests harmed by letting people see latency? And that's diff motivation from browser, where various threats are not the concern of individual site that happens to serve something and keep biz data private, instead it's user info that browser has motivation to keep private. Even if we rename to unsafe-all, the person who it's unsafe for is the user, and the person doing the deciding may have diff motivations on what they want to keep safe. The stuff that Jeffrey mentioned, splitting caches and doing other things that could help isolate, could be a better approach.

**Pete:** when those things butt heads, interests, W3C unambiguous that user takes precedence. In terms of caching, don't know how this would work for DNS caching in first party origin, very different from caching that browser is concerned with. DDG team, when you file these as issues, please let me know.

**Konrad:** will do, we'll take a look at double-keying caches.

**Brad Lassey:** Chrome is double-keying DNS cache. Completed work, will point to document for design. 

https://docs.google.com/document/d/1UvieZrwoSMHg5-UB2tzxUFPhLur8NZT7gZajLFk5EDc/edit#heading=h.qn6dz38mj8h0

Bug https://bugs.chromium.org/p/chromium/issues/detail?id=997049

### 3. Privacy review process (discussion)

**Pete:** some competing proposals for review process for discussion. Slight issue of contention is, should there be anything mandatory or heavily expected (most people against), and if not, should we just have a sign-up sheet? If so, will take an action to create it...seeing no comments, taking it that we should have gentle suggestions and a sign-up sheet. Will see how that goes.

### 4. Font fingerprinting (update - Pete)

**Pete:** had discussion with CSS WG, across the board agreement this a problem to be addressed. Propose algo: do measurements on the web, see what's used, segment on OS of browser, have that be all that's used, everything else is a web font. May be special cases for certain languages and perf considerations. Plans to address that but remove largest distribution of font fingerprinting capabilities.

### 5. Device orientation API (update - Brad/Pete)

For background, please see: https://github.com/w3c/deviceorientation/issues/85
  
**Pete:** research that you can uniquely ID device w/ highly-sensitive accelerometer...Nick and Brad and team took action items to suggest ways to remove this fingerprinting surface.

**Brad L:** proposal to round to nearest 10th of a degree. Order of magnitude needed to fingerprint, but will not introduce some extra work.

**Pete:** thanks to the team for helping to move these mitigations forward, it's been a really positive thing all around (WG, original academic findings, etc).

**Brad L:** we think it's good enough, should put out to field trials, if it breaks anything might have to reconsider aggressive clamping.

**Pete:** particular timeline?

**Brad L:** would have to check but no

### 6. New Web developments and privacy considerations (new standing item)

**Pete:** new communication spec proposed, discussion at TPAC. UDP-style/no-guarantee style comm client-server. Web transport. Not clear how it would work w/r/t content blockers. Some folks saying no spec for content blocking. In past, describing interaction with Fetch API, talk about blocking abilities in non-normative text. Comments?...okay, I'll continue conversation on this.

### 7. Privacy Community Group

**Wendy:** on its way, but for one last internal approval. We should expect the group and repos to launch soon.

### 8. Process for adding privacy considerations in WICG work

(Moving to next call)

### 9. AOB

**Christine:** WebRTC WG published up CR for WebRTC's statistics API. Request feedback by Feb 21 in Github.

Identifiers for WebRTC's Statistics API - https://www.w3.org/TR/2020/CR-webrtc-stats-20200114/

Link for feedback:   https://github.com/w3c/webrtc-stats/issues









