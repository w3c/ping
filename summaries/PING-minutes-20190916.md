# Privacy Interest Group meeting - 16 September 2019

Location: Room Yoh (3F)

## Attendees

* Christine (invited expert, co-chair)
* Pes (Brave, co-chair)
* Tara Whalen (Google, co-chair)
* Artur Janc (Google)
* Mike West (Google)
* Jeffrey Yasskin (Google)
* Brad Lassey (Google)
* James Fishback (Wikimedia)
* Pranjal Jumde (Brave)
* Steven Englehardt (Mozilla)
* Laszlo Gombos (Samsung)
* Aaron Gustafson (Microsoft, *observer)
* David Singer (Apple, *observer)
* Michael Kleber (Google)
* Rowan Merewood (Google)
* Sam Weiler (MIT/W3C)
* John Wilander (Apple WebKit)
* Tom Lowenthal (Brave)
* Wendy Seltzer (W3C)
* Konrad Dzwinel (DuckDuckGo, *observer)
* Dave Harbage (DuckDuckGo, *observer)
* Kamila Hasanbega (Google)
* Nick Doty (remote-only) (UC Berkeley)
* Carlos Ibarra Lopez (Google, *observer)
* Jeff Jaffe (W3C)
* Jia Qiang (China Mobile)
* Jatinder Mann (Microsoft)
* Melanie Richards (Microsoft)
* Ricky Mondello (Apple)
* Ryo Kajiwara (Lepidum, *observer)
* Victor Costan (Google, *observer)
* Chase Phillips (Google, *observer)
* Tomoaki Mizushima (Internet Research Institute, *observer)
* Dominic Cooney (Facebook, *observer)
* Darwin Huang (Google, *observer)
* Daniel Xie (Google, *observer)
* David Marsh (AusPayNet *observer)
* Alex Russell (Google)
* Chris Wilson (Google)
* Reilly Grant (Google, *observer)
* chaals nevile (ConsenSys)
* J.C. Jones (Mozilla)
* Yuriy Dybskiy (Puma Browser)
* David Schinazi (Google, *observer)
* Victor Vasiliev (Google, *observer)
* Ian Clelland (Google, *observer)

Regrets Jason, Brent

## Minutes:

Introductions

### 9:00-9:30: Plenary day planning

**Sam**: Interest in privacy summary workshop on plenary day or combining sessions?

**Pete**: How much overlap between 1 and 2?

**General view**: Not much overlap

### 9:30-10:00: Overview of existing PING issues

https://github.com/w3cping/tracking-issues/issues

#### #1:

**Pete**: HR Time will be discussing this with us - does anyone have anything to add? - especially those not implementing high resolution time stamps? Har

**Mike West**: If haven't already suggested to Web Perf WG - look at Spectre mitigiations - cross-origin opener / embedder policy etc. - seems reasonable for other things like time resolution to align - will discuss in WebAppsSec WG tomorrow these mitigations - seem like the right approach for this kind of thing ([context for COOP / COEP](https://docs.google.com/document/d/1zDlfvfTJ_9e8Jdc8ehuV4zMEu9ySMCiTGMS9y0GU92k/edit#))

#### #2

**Pete**: persistent IDs in GetUserMedia - ongoing discussion - are people interested in getting involved more?

**Brad**: 

**Pete**: website asks for permissions to hardware like microphone - userid persistent - concern is there a better way to handle access to hardware while not introducing a new tracking vector

**Mike West**: is it disctint from EME identifer?

**Jeffrey Yasskin**: yes, device ids, not machine Ids like EME

**Mike**: what is the use case? (for cross tracking)

**Pete**: text suggests if allow double-keying, should allow double-key storage, but not if does not say, mitigations should be double-key or not have the persistent ID

**Mike**: tie lifetime to storage lifetine not usefuL?

**Pete**: vendors - if say when storage is cleared - no universal storage lifetime

**Mike**: come up with consistant storage for information - seems like a useful approach - [storage spec WHATWG](https://storage.spec.whatwg.org/), could we align on a set of hooks for that spec, call hooks via mechanisms

**Pete**: not familiar with that - but useful to add to discussion

**Mike**: ITP mechanims that clear after 30 days

**Pete**: different mechanism

**Mike**: cookies mechanims are not well-defined - but this work sub-divides - sugges if in storage spec, easy to point people to when writing specs

**Jeffrey**: interesting different between writable and readonly storage - something to think about there

**Mike**: clearing (whatever that means) needs to happen - in response to hooks being fired, could do something

**Pete**: standard likely to go for approval soon - need to make choices now

**Mike**: problems with standards process - not sure worth doing now - these kinds of milestones - 
Hoping we'll work out a good model of evergreen specs. 

**Wendy**: AC meeting will get a presentation on evergreen [sllides](https://www.w3.org/2019/Talks/TPAC/continuous-standards/#) - Goal is to enable continuous development, where if changes should be made, they can be. Some users like versioned specs whereas others need to continue to evolve.

**Pete**: either, or ?

**Mike**: prefernece for underlying infrasture - storage spec is shared infrastructure on which things can be built - if for timing reasons have to do separately, okay - but prefer not one-off solutions

**Pete**: seems appealing

**Jeffrey**: convince Chrome to double-key for this spec - other browsers already do

**Tom**: double-keying only get you part of the way - need both

**Pete**: seems to have general consensus on this - double-keying seems like a convenient way of dealing with it GetUserMedia (every frame has a seed that goes into random number generator to make the id) - if fed seed and the information about double-key frame origins, would have this nice double-key solution

**Pete**: spec would need to say that all need to be double-keyed - could right PR, but if someone from group here?

**Brad**: people are in second screen right now, but I can follow-up as Jeffery suggested.

#### #3:

**Pete**: revisit existing standards where privacy violations are happening, e.g. fingerprinting, can we go back and fix - CSS Font Enumeration 

**Steve Englehardt (Mozilla)**: bundle fonts approach

**Pete**: some pushback re performance - withint PING, a lot of interest, others?

**name**: sense for distribution of OS fonts across different systems?

**Pete**: goal to make no more identifying in the user agent

**Artur Janc**: does it mean not possible to use non-system fonts

**Pete**: website would need to include non-standard fonts as you would other things

**Brad Lassey (Google)**: what is user wants to use a proprietary font in say, Google docs? - need to handle this

**Pete**: discussion about whether to add permissions - for this narrow issue - more than we want to take on - WCIG is working on a spec on enumerating all fonts

**Brad**: need to deal with niche case

**Pete**: don't want Dto hold off because don't know when that will happen in WCIG

**Brad**: if new language in spec, it should be optional

**Tom**: strong disagreement - exposure should be non-default list - privacy risk

**David**: so user should do something to indicate that they want to use special fonts

**Tom**: Yes

**Pete**: need standard privacy sey

**Brad**: concerned about breaking existing use cases on the web

**Pete**: reaearch that this is being done in the wild - bad uses for abuse of privacy

**Tom**: fix actively exploited harm - if use case with advanced functionality provides urgency to develop spec to do that

**Brad**: we roughly agree, but don't break existing use cases until we have that

**Tom**: but, trying to stop privacy violation

**Mike West**: asking for changes in Font enumeration spec? or? Font enumaration spec is on font enumeration API so questions or prompts could be put before the user - seems to solve some of the issues

**Tom**: we disagree on where we change the default 

**Nick**: it sounded like we were going through all specs - re: HTML are looking at changing some of the things we are discussing

**Pete**: Going through existing issues now - 11:30 we could do some other things, unless specific things you would like to call out now

**jyasskin**: 2 suggestions: (1) no solid decision without CSS WG in room, (2) disagreement seems to be about when browsers implement the spec change rather than the content of the change, e.g. it is possible that Chrome might be slower than Brave, Chrome is going through the process of developing the replacement API now - talk about scheduling when browsers ship the change

**Pete**: seems reaonable to me - wanted to have a detailed discussion at PING

**jyasskin**: seems Chrome has a different view than other browsers on scheduling - others seem more witlling to break and then implement a replacement for the use case, whereas Chrome usually reimplements before breaking the previous case - that's a reasonable thing for browsers to differ on.

**Pete**: if agrement, other than implementation order

**Sam**: meeting with CSS WG this week?

(npd: +1, the scheduling of implementation can depend on the implementer)

#### #4:

**Pete**: Privacy and WoT - trying to set up a meeting on Thursday or Friday.

**Sam**: The WoT WG asked for Thursday afternoon, which conflicts with WebAppSec.  We have counter-proposed Friday.

#### #5: https://www.w3.org/TR/reporting/

**Pete**: Reporting API - disagreement re: lifetimes, who the API can talk to, extensions it gets filtered through - whether sites should instruct users to report by default, etc. - relatively early in standardisation process, but good to discuss now

**Jeffrey**: Ian is working on a prooposal to deal with privissues

**Brad**: Considering whether one or two specs - one controversial and one not

**mkwst**: reporting API supposed to be the non-controversial part.  
curious, don't know context - portions core to reporting API - lifetime of pin, does liefetime match what the website said it can do

**Pete**: lifetime of reporting process is not tied to document, different time space 

**Mike West**: also controversial?

**Pete**: yes

**Mike**: Same issues with Beacon? [Fetch](https://fetch.spec.whatwg.org/#dom-requestinit-keepalive)?

**Pete**: yes Beacon, not so familiar with Fetch

**name**: ?

**Pete**: if text is changing past, perhaps not worth getting involved now, but worth knowing where other browsers stand

**Mike**: Ian is looking at mechanisms to address this

**Pete**: network error logging - worthwhile to know if separate or not, proposals

**Mike**: my understanding - `includeSubdomains` mechanism is unnecessary and more cleanly align with reporting mechansim - worth doing irrespective of privacy concerns

**Pete**: networking error logging, privacy concerns - early days - is it worth discussing

**mkwst**: discuss reporting generally - core to security features - but if concerns about reporting we should discuss now - to deploy security mechanisms at Google need reports from the wild - difficult to deploy without an understanding as to how they interact with clients in the wild

**Pete**: concern is not whether reporting is good or bad - but debugging agent without user knowing, consent

**Mike**: what is the difference between debugging and [insert]?

**Tom**: one is for the site and the other is for the user

**Mike**: debugging helps user

**name**: Chrome, it's opt-out to turn off reporting mechanisms

**Nick**: useful to have a separate reporting API spec - otherwise have to repeat with Beacon, Networking Error Reporting, Beacon - could I have the link to the latest version? - issue of transparency and user control - on by default/off by default - lots of questions: GET vs POST, do requests have cookies? also a-ping

**Pete**: there is a spec, right?

**name**: yes, [reporting](https://www.w3.org/TR/reporting/)

**Pete**: link in the issue

**John Wilander**: by the title sounds like a global thing but you envisage that the user turns or or off by site

**Pete**: natural thing for user - by site

**John W**: if anything to report, then ask user 

**Aaron**: As in via [ReportingObserver](https://w3c.github.io/reporting/#observers)?

**name**: one issue of that set up - TLS 1.3 and QUIC deployment can't get initial bits of website, behind midlle box doing bad things would have the time to ask

**Michael Kleber**: re: reporting after something goes wrong - re font enumeration, need enumerator and demoninator - need to know what worked and didn't work

**name**: thinking of benign case - website broken, different if malicious

**Mike**: reporting observer, JS better if register and do something based on that - totally resonable to have different opinions about both sides - is it contraaversial for browser to tell page? or browser then might be instructed to take action?

**Tom**: providing reports more complicated and broadly scoped than regular JS - expect webpage to exist in window box, if close, stops existing and computer takes no more action on its behalf

**name**: if executing, okay taking action on own behalf?

**Tom**: some concern, but certainly not happy if in background - if a page can ask my computer to do things outside that "window" much more distressing - removes natural controls around page executive

**Kleber**: a lot of this work used to be done in unload handlers - had user performance impact - one thing was to stop this having to happen when user closes the window

**Tom**: Big distinction between opt-in app experience and the single visit website experience 

**Pete**: find time to continue discussion later in the week

(**npd**: fixing the performance issue of unload handlers seems like it mostly help sites that collect lots of data and block to send all that data back, which meant there was previously a performance advantage for sites that didn't do that. if it's 'fixed', then background reports use bandwidth and slow down all other pages, and the site doing the reporting doesn't pay any of those costs.)

#### #10 [Move enumerateDevices behind a permission](https://github.com/w3cping/tracking-issues/issues/10)

**Pete**: FP vector.  Proposal is: instead of value per media device, there would be one per category.  e.g. one audio device, one video device.  Once site asks for audio, it gets labels, and not before.  Seems less controversial than other getUserMedia issue.

**Brad**: since there are several issues with this, maybe meet jointly?  

**Pete**: they meet Friday.  Sounds like rough consensus that this is good.

### 10:00-10:30: Highlights of recent Mozilla + Microsoft privacy summit

**Jatinder**: Moz and MS hosted a web privacy w/s.  when we talk to customers, hearing uneasiness re: data on the web. Creepiness re: targetted ads.  Helplessness.  Some customers okay with relevant ads.  See this as a global socieital issue; aiming for cross-industry coordination.  Also want consistency in privacy practices, for web compat.  Highlights: 9 vendors in room.  2-day workshop.  Deep dives from Apple and Brave. Google re: proposals, MS re: auditing proposal, non-technical.  Talked re: how we're doing slightly different tracking prevention things.  Long-term future of cookies.  Restrict first party sstorage?  Incognito detection.  Network privacy.  Discussion of APIs to remove or restrict.  Consensus: new APIs should have FP mitigations built in.  Discussion of cross-industry principles.  Felt like there was a lot of value in contining that discussion - might be that group here today.  Might also be a standardizing group.  

**John**: Intesting discussion re: whether to have replacement techs first or tracking prevention first.  Q was where have replacement tech live.  Even if people who aren't members of W3C have feedback on these.  Move into IG/CG discussion now?

**Sam**: lets talk about the techs first, then the "where to do it".  

**Pete**: lots of talk re: interop; lots on web compat. 

**John**: in search for replacement techs for web sites to have ways of funding their business: we are not only concerned with server-side tracker, also concerned with consenquences of profiling people and targetting them.  things people might not know about themselves, or want others to know, and the ability to target them is problematic, no matter where and how that profiling happens.  that was a new discussion at that w/s.  this is not just about third part tracking.  the problem is profiling.

**Pete**: how could this group tackle that?

**John**: part of google's privacy sandbox: finding new capabilities of profiling people (e.g. FLOC) without having server create those - we said that's problematic even when profile is created on the client.  

**Steve**: is that defining privacy?  Is that simply linking cross-site?  Or is it revealing info re: user?  

**Pete**: would be interesting. Brave does some profiling (client-side).  Concern re: any kind of profiling?  how does apple's ad attribution scheme fit in?

**John**: existing server-side profiling has negative consequences.  the fact that people ahve been profiled ... microtargetting is problematic.

**Nick**: impressed by breadth of topics and depth of consensus.  I was surprised re: consensus on FP mitigation.  Is there any sense of what was the trigger to make this happen now?

**Jatinder**: MS wanted to bring vendors together.  We want to see discussion continue with other parties.  Started with smaller group, to kick discussion off.  Where is next venue.

**Pete**: plans for a follow-up?  

**Jatinder**: I hope to decide this week what group, then decide.

**Nick**: not objecting to starting with small group.  Just wondering what prompted that now v. a year ago.

**Jatinder**: MS is building tracking prevention.  differences in behavior in browsers; hearing about compat.  It feels like technical enforceability is just a part of this.  Lots of folks thinking similarly.

**Tom**: Apple ad attribtuion protocol is distinctive because it's not about enumeration multiple evetns re: an individual but by counting groups of people.  Not associated with indiv.  To the extent that we need measurement, this is the sort of world I think we should be in.  Count overall flux w/o tracking indivs.  Not profiling; no dossiers.  Still understand audience.  

**Mike**: dossiers/microtargetting: Q re: what level of aggregation mitigates what level of privacy impact.  What is that level?

**Tom**: if you can pull a person out of data set, too personal.  If not, good.

**Christine**: concern re: server-side profiling.  Europeans concerned in general, even client-side.  Be ready to address that legal/policy concern technically.  There were attempts to extend definition of personal data to include cases where you could single out an indiv.

**Sam**: worried about deanonymization of data (like medical data) even data that seems to be anonymized. maybe we could give a model that attempts anonymization and ask researchers to see if they could break it.

**Sam**: The w/s reached common consensus on private mode: it violates a user norm if sites behaves differently in private mode. Proposed that it would help to rename to ephemeral/amnesia mode.  I saw some dissent re: fp, for example always having mitigation, or reducing fp surface when adding it somewhere else.  There was a warning that industry is already moving to cookie-less tracking (via fp).

**Sam**: Also a w/s conclusion: mitigations that work for smaller browsers might not work for others, because half the industry moving could trigger a technical arms race.

**John**: part of google's presentation of priv sandbox - google wanted to get auction revenue up.  3 kinds of ads - if we get rid of retargeted ads, okay, but need to keep interest-based ads.  Doesn't have to be a collection of data on you.  Could be user expressing interest; doesn't have to be automated.  eg. credit card companies can see two years in advance if you're going to get a divorce. people might not see that themselves.  definitely won't put it in a profile.  ML approach could deduce that.

**Tom**: re: deanonimization: not talking about classic anonimization - I'm talking about production of records that are non-individual to begin with.  e.g. a person that is obliquely linked - number of people passing by a site - inherently non-indiv.  can't line them up unless info already in other record.  that's the sort of analysis I'm asking for.

### 10:30-11:00: Morning break

### 11:00-11:30: parallel sessions

 - Publishing WG joint session, Koh (3F) (re: https://www.w3.org/TR/audiobooks/)
 - Horizontal review at W3C and how to improve, Yoh (3F)

**scribe: Mike West**

#### Horizontal review at W3C.

**pete**: Concerns from PING about horizontal review. Large number of specs that go by that we're not aware of/become aware of too late. Want to be collaborative. Perhaps there's a formal role in W3C procedure rather than an ad hoc mechanism.

**...**: WICG is a large concern here. Lots of work. In some sense in the open, in another opaque about where work stands, how they want input from groups like ours. How can we work with WICG earlier? What's a process that can foster a collaborative workflow?

**Alex Russell**: I'm involved. Chris Wilson is a co-chair. TAG has been aiming to create a more collaborative body that improves the quality of design. That includes features incubated at the WICG. Along with Mike West and other folks, I'm one of the folks who approve/disapprove features landing in Blink. My day-job team is furiously throwing features into WICG. Our job is to push ahrd and fast to make the web competitive. The way our work is structured (Google, Chrome, Blink specific): we invoke review through the Blink launch process via requests for TAG review early on in design.

**...**: The TAG has bee weren able to stop designs from going forward that we could know ahead of time would cause pain in the platform. We've adopted that as a core part of the Blinkprocess.

**...**: Asking for TAG review early. Smell test before implementation is complete. Important to get design review at that stage. That's a good model to learn from.

**...**: Think about how you could use the TAG's review backlog (heavily structured these days).raft off of that work, already a lot of momentum behind that.

**Tom**: Curious about how proposals within WICG relate to standards track methodology.

**...**: My understanding is that someone says "I have an idea." Then they write a spec. Not a process that depends upon the input of other potential implementers. Doesn't seem like it results in proposals that have the feedback of specialists in various area: a11y, l18n, etc.

**...**: WICG feels like one vendor writes down things it wants to implement, and says "This should be a standard."

**Alex**: Putting my Google hat on: We go to WICG to do our design in public, with the community to the extent that we get their time and attention.

**...**: Can get to an agreement with other vendors about how a feature should work. But no test that you're solving an important problem well. You can prove that you've solved _a_ problem, but need developer input to know the problem is important.

**...**: Pitching features, getting them into WICG. We want to talk to other browser vendors. WICG is open process. Goal is to get to feedback from _developers_. Historically overindexed on subject matter experts. Get features that fit into the platform, but don't solve an important problem.

**...**: Origin Trials are an important part of this process to get developer feedback about the way we're addressing a problem.

**...**: Want to talk to developers as much as possible.

**Tom**: This sounds like a Google thing. Not a W3C thing. You talk about soliciting feedback. I see threads where Google asks for feedback, and by the end of the day, 30 other Google responses come in before anyone else takes a look.

**Chris**: I co-chair the WICG. 4 co-chairs. 2 from Google: myself and Yoav. Marcos from Mozilla, Travis from Microsoft. Created the WICG to participate in conversations with everyone. Service Workers: had many conversations, not intended to be private. Creating a WG for those conversations puts you on a standards path that isn't helpful for design. Also imposes legal obligations, need to go through legal for each new WG/CG.

**...**: We don't just dump things into WICG. We should describe interesting problem spaces. Ask folks not to fall in love with their initial proposals, but to agree on a set of problems and work together on a solution.

**Tom**: What's the bar for getting out of the WICG?

**Chris**: Done the design work to know that this is an important problem to solve. Done enough design work to have the skeleton of a solution. 

**Sam**: Alex, you said you want to "Make the web competitive". Vs what?

**Alex**: Every other platform. Folks have a limited amount of time. The web is competitive on desktop. Losing on mobile.

**Tom**: You say you have discussions in WICG. Outcome should be basis of work for a WG to develop a specification.

**Alex**: Yes. We try to insist on short charter time periods. Pop up for air, look around at what's happening, and adjust charter accordingly to pull in relevant work.

**Pete**: You talk about TAG as one horizontal review body. There are others. How do others get involved?

**Chris**: There's a scale problem. The TAG has scaled a lot recently. Right now, the WICG does not have processes in place that say "Thou shalt ask for HR from this group at this time"

**Alex**: To be clear, the TAG review today is part of Blink's process, not part of WICG's process. It's a coincidence today that the TAG review queue gives you an indication of the kinds of thing that are flowing into WICG right now.

**Pete**: Google has a lot of WICG members.

**Alex**: Not going to apologize for investment.

**Pete**: Not asking for apology, just noting that the two are very similar sets.

**Alex**: If you want your group to be in Blink's process, talk to Blink's API owners (for example, Alex and Mike).

**Chris**: Note: Intent to Implement is just about implementation. That triggers a review in Blink's process, but it's not the point at which we ship things.

**...**: Also, note that WICG is not required. It's fine to fail quickly in any other group, we just don't see it happening in working groups, and WICG is a good venue for it.

**Nick**: When is a good, useful time to get privacy reviews for WICG prototypes/explainers/etc? Separate from when it's _required_?

**Chris**: Speaking out of turn for the WICG co-chairs, since no one else is here: My personal opinions is that there's a point at which you have a minimum-viable design. You've thought deeply, you've captured feedback, you think you have something that works. Usually this is about when you have a prototype implementation behind a flag and can say "Hey community, please play with this and tell us what you think." That's a good time to get security and privacy feedback. At that point, you need to be thinking about HR.

**Alex**: Note that we start writing code early. That doesn't mean that things are set in stone.

**Nick**: Is there a place where "minimum-viable design" is flagged?

**Chris**: No. I'm thinking about how we can do that in a way that's clear to the community.

**Wendy**: With a few hats (W3C strategy lead, participant in PING): one of the things I hear PING asking for is "How can we watch for the right flags to help in reviews?" Signals would be helpful.

**Chris**: I sit at the middle of this as WICG co-chair and at Google. We at Google should get our ducks in a row. We sould be thinking about privacy and security implications early. We shouldn't come to this group or any other until we have some idea what we're doing. At the same time, I want to keep the bar low for starting an incubation. Otherwise costs to proposing an idea are too high to bring everyone in.

**Tom**: I think I understood you to say that the only time WICG proposals actively seek out HR is when the Blink process suggests it, and then only from the TAG. IS that right?

**Chris**: The Blink process forces Blink engineers to ask TAG for review very early because we want to make sure we're being open about that to the platform.

**Alex**: That's not the full set of responsibilities, of course. They need to find a community, etc. They need to convince Blink's API owners that they've done the work to ensure that we're adding reasonable things to the web platform.

**Tom**: To Chrome, not the webplatform.

**Alex**: We recognize some responsibility here as a widely used browser engine. Need to find the right folks to weigh in on features to inform those decisions.

**Tom**: Maybe I'm asking the wrong questions. I want to know at what point a google engineer thinks they have a good idea and have to ask the W3C for review to find out "oh wait you might have missed something"

**Chris**: Two things: there are simultanious processes. There's "becomes a REC" and "ships in any browser". These aren't tied together. Getting a REC is not a prerequisite to shipping. The expected process in Blink is that you have an idea, incubate it, and then migrate it to a working group. Process requires you to outline HR-like concerns at that point.

**Tom**: I'm hearing that either in the WG stage, or just before it, HR happens.

**Alex**: That's when it's explicitly invoked. Nothing stopping groups from being involved earlier. TAG built up reputation over time by doing exactly this.

**Tom**: Feels like you're suggesting that in order for PING to provide feedback, we should be proactively providing feedback by keeping track over WICG generally.

**Chris**: No. As a WICG co-chair, there are two things we'd like to see. The etter we are about . 
We have this in our process "Intent to Migrate" Nobody should get past this point wihtout horizontal review. We are certainly open to revising that process. We don' tthink that sending every new incubation to PING, because that will be a lot of noise to signal.

**Pete**: It's not clear to me whether WICG/Blink would _like_ more review? IF you'd like more review, the earlier in the process we can be the higher our bandwidth. Working back and forth to police the review and make sure it takes effect is what takes time. Giving design feedback is not as high a bar.

**Sam**: Sufficy of TAG reivew.  The TAG changes makup fairly often. A TAG might be constituted that doesn't have privacy expertise on it.

**Alex**: The TAG is not going to solve every problem. As someone who was on the TAG, our hope was to turn the things we discover in reviews into things like the security/privacy questionnaire. When someone comes in, they shouldn't be asking basic questions like "Should I use Promises or callbacks?" We created a corups of design guidance that we hope folks work through in a self-service fashion.

**Pete**: We have such a questionnaire.

**Alex**: We rather persistently asked PING for a way to understand the model.

Sam: How close is the current document?

**Ales**: It is not fit for that process.

Jeffrey: How would the PING help Blink's API owners add PING to the process.

**Alex**: Help save us from our selves. We're going to make mistakes. My team is going to make mistakes. Everyone has the motivation to not end up on the front page of hacker news for bad reasons. Collaborating and getting constructive dialog will convince people. Not convincing people that you're right, but that we can be more right together.

**Pete**: How can we arrange that trial run.

**Alex**: You need to figure this out. In the TAG, we were proactive about it. "Would you like design help? We have some expertise."

**Chris**: One piece of feedback in the PING charter review is a request for an understanding of the underlying model that informs your reviews. As an example: in WebXR review, we got feedback that a certain thing was a bad design pattern. We asked them to document that design preference so that we have up-front guidance about the kinds of things we're going to get feedback about.

(npd: that is the intent for PING as well, to add issues on priv/sec questionnaire, or otherwise collecting feedback on what would have been useful for a review.)

**Jeffrey**: PING is outgoing at the moment about doing exactly that. Filing issues on specs, giving feedback. Some issues aren't working well, conversations going on and on.

**Alex**: we had a lot of people tell us to buzz off originally. Its not like we had credibility to begin with.

**Jeffrey**: What characteristic of reviews helped build credibility?

**Alex**: The tag got into our process because the TAG saved us from our selves several times. That trail of evidence of being helpful.

**Tom**: I feel like I'm getting mixed messages. We keep asking what it is you want, and every time someone repeats it back, you say "No, no no." The specific thing you're pointing to with the TAG seems like a red herring. The set of concerns most likely to be articulated from the TAG preconform with the views of folks at your orgnization. The privacy feedback from PING is important and vital precisely because it represents views from people that don't share your perspective. Feels like a catch 22.

**Alex**: I'm also distressed by some of the content of framing that you just use. There was an assumptiopn that some of the people that work at google don't want the same things. 

**Tom**: Not assuming, Describing set of interactions I've had.

**Alex**: That's fair enough. I can think of a number of working groups that I'll decline to name that had to experience a bad time to learn their lesson.

Tom: That's a relevant perspective if the goal is to change the minds of Google and Googlers about what ships in Blink. Hugely Google-centric view of what it means to build a web platform.

**Alex**: the blink launch process doesn't require concensus from anyone else

**Tom**: I'm aware. I'm not telling you how to run your thing. I'm talking about things you'd like to become concensus recommendations of the W3C. If you like feature X and I don't, you're going to ship it, it's your thing. If you want X to be standardized, you need to get the feedback from others and to take others' feedback into account. Can you understand how that is perceived?

**Alex**: I can understand how I may have communicated poorly about the intent or the process we're using. It strikes me that things that ship without that concensus. There's a set of thigns that we havent' shipped and everyone has and the compat risk is that we haven't shipped. There's a set of things that we want to work on but others aren't seeing the need. In those cases you might see a very seat of the pants i2i and if you see those sort things I hope you'll talk to Mike or talk to me.

**Tom**: Flip-flopping between Blink and W3C as substitutable.

**Nick**: Talking a lot about the Blink process. It might be more useful to figure out when/how we can get better, actionable insight about when to do things at WICG/W3C groups. Don't need agreement about how Google does things with Blink intents. Need to know when the most useful points are for us to step in.

**Jeffrey**: One idea is to watch the w3ctag/design-review repository. Should at least be in a state where uninvolved folks could understand the proposal.

**Nick**: Is that simular to the minumal viable thing that Chris mentioned?

**Chris**: No. It may well be much earlier. TAG reviews are requested by the Blink process very early. It's the point at which folks go out and begin writing code.

**Nick**: Could WICG make process changes? just a signal/tag somewhere when it reaches another stage

**Chris**: I think the WICG is quite open to expanding our process or adding horizontal review. This is quite different than the process today, our Intent to Migrate template does ask if you have asked for security review and other reviews.

**Jeffrey**: Origin trials might be a better slot.

**Chris**: That's not crazy, but it's not a great match. Not everything goes through origin trial.

**Alex**: Signals interestingness and maliability.

**Nick**: Are we getting privacy reviews at "intent to migrate" stage?

**Chris**: So, intent to migrate says "have you done a security and privacy review, enter you securituy and privacy review here". But, its also hte hand off to another WG, so there may be other process in place in those other WGs. Our goal is to create an exit path which should probably be taking security and privacy into account.

**Nick**: Is there a list somewhere of the things that are migrating? I don't think we see that group of things now. Would like to proactively review those.

**Chris**: We have a list of all incubations. WE'd like to make the process better, better tooling.

**Pete**: Maybe break for lunch at 12:00? Reconvene at 1:15?
...: To close this out, the more, earlier conversation we can have, the better.

**Sam**: I find it helpful when spec authors tell us that "Now is a good time for review". Folks are generally good at that.

**Chris**: Meh.

**Sam**: They can be taught!

**Brad**: The TAG early review is a good signal. It's a low bar. A "PING early-review" might be helpful.

**Chris**: Identifying the right time to ask for review is hard.

**Tom**: Flip-flopping back and forth from Blink process to WICG is making this really difficult.


### 12:00-13:15: Lunch Break


### 13:15-13:45: Positive standards brainstorm (inc. improvements to existing standards)

- scribe (first 30 min): Rowan Merewood

**Pes**: Are there standards that would make sense for PING to take a more proactive role or to go back and investigate existing standards:
- Hardware leaks from WebAudio / WebGL - fingerprinting risk

**Pes**: For example, Brave does not allow access to those APIs unless the user allows it. Don't know what other vendors are doing, is there a way we can standardise that?

**Nick**: Highlight what I was mentioning earlier - HTML5 includes fingerprinting text very early on. Interest from vendors in moving that to a separate location. Would be good to revisit this for what's necessary, what can be updated. Should look at recent research for what has the most entropy - I know Canvas and fonts are on that entry. 

From a 2018 paper:

> We show that by changing some features of the fingerprint, such as Content language or Timezone, it is very probable that the fingerprint will become unique. We also show that User-agent and HTML5 canvas fingerprinting play an essential role in identifying browsers on mobile devices, meanwhile the List of plugins is the most distinctive elements on personal computers, followed by the HTML5 canvas element. Furthermore, in the absence of the Flash plugin to provide the list of fonts, we used an alternative for collecting fonts through JavaScript. Even if the list of tested fonts is much smaller compared to what could be captured through Flash, collecting fonts through JavaScript still presents some good results to distinguish two devices from each other.


**John**: What does Brave mean by a "positive signal"

**Pes**: Turn off shields essentially (an interaction in the location bar). The context being that there's more third party fingerprinting on a page than users are aware of. We haven't dug too much into the difference between 1P / 3P there.

**Jatinder** : IC vs CG - what's the difference? What's for incubation, etc?

**Wendy**: WGs and CGs have mechanisms for patent commitment, so new spec work should start in one of those. Spec work happens in WGs because that's where you get the IP commitment. Typically, IGs do horizontal reviews, which is contributing to spec work, but they do so by making comments on specs hosted in WGs. (scribe note: there was a comment about CGs that I didn't get)

**Artur**: There have been ideas for privacy-positive work we could consider. Legacy behaviors on the web that rely on shared global state in the browser. For example: `:visited` CSS selector, cache, number of openable sockets. All can either reveal something about the user, or fingerprinting vectors in different way than we usually think about. All could be changed in the platform to be more privacy-friendly. Interest in further discussion?

**Pete**: Yes.

**Artur**: Mike. Talk about things.

**Mike**: Some people think visited links are useful so we don't think we can remove them. There has been come assertion that we can limit the history or double key it as mitigation. (Previously it was possible to get direct access to the style, but even with that blocked, it's possible to use timing attacks where the style will require the browser to do some work, and time to see whether it took that time.)


**John**: On Wednesday we are having a session on measuring ads. We will cover WebKit PCM and Chrome's conversion Measurement.

**Mike**: Browsers are starting to limit existing standards in ways that do have an impact of existing sites. We could make use of the Permissions API to expose this. For example, the site could ask if it has access to Canvas and then show the relevant messaging to the user. We should create a more standardised mechanism that sites need to ask for a piece of functionality allowing browsers to intervene in more meaningful ways. That means browsers also expect that the functionality may not be available. Interventions that block the behaviour often put users in a position where they cannot recover.

**Pes**: I think Tor has done something similar shimming in a Permissions model for Canvas.

**Jatinder**: At the workshop we did talk about a bit on what things should be investigated and applied to existing standards? Restricting, adding permission, the privacy budget, etc. Could we come up with a suggestion for mitigations?

(**npdoty**: to follow up later with Jatinder, it's worth noting that we have published an Interest Group Note "Mitigating Browser Fingerprinting in Web Specifications" which has a list of mitigations and how to apply them. http://w3c.github.io/fingerprinting-guidance/ if it needs updates, that's useful too!)

**Pes**: Hold for the next session.

**PJ**: Discussion during summit - can we move Storage Access API to a privacy group?

**John**: If we get a privacy WG I would prefer to move the Storage Access API there, but I will use what we have available?

**Sam**: Are we ready fr that?

**John**: I'm not sure.

**Mike**: I'm curious what you would get out of a new working group that you don't get from the existing one?

**John**: It's currently just one huge thread on the HTML SPec, not even I know what's been said there and it's kind of my job! I want somewhere we can file multiple issues, hash it out, and then lump it into one PR/

**Mike**: I think this applies to other issues - COOP, etc. that will fold into HTML later. I'm not sure we need a separate forum but just have something in the same process.

**John**: In WhatWG?

**Mike**: Whereever - personal repos, separate, etc. I htink something like Storage Access API is larege enough that it needs separate discussion. Chrome has used presonal repos for the initial discussion before it's mature enough to graduate into WhatWG, etc.

**John**: The Privacy community discussions are not just for the Storage Access API.

**Jatinder**: I don't see a disagreement there, there are separate repos. If there was a Privacy group it could be done there.

**Mike**: It took a long time to get Microsoft to get involved in WhatWG due to the various legal agreements. I don't want to create another group that requires that whole process again. If we re-use existing groups there's an existing IP agreement that everyone is happy with. Allows us to get the right people in the room with the right legal framework.

**John**: I feel like there is scope for a community group that has separate chairs, etc. It's been hard to propose these things.

**Mike**: Speaking as a chair of a group, I don't think chairs do that much. I think it's about having the right people in the room, I think the best a chair can do is faciliate that.

**John**: I think having people who have been passionate about this could chair.

**Nick**: I understand the motivation in not getting more laywers involved. I think an IG/CG doesn't require the same committment though that an entirely new forum like WHATWG did. I think the other thing is people can use the group as a bat - the charter says we won't focus on your thing and so we can downplay its importance.

**Pes**: I think there's some degree of marketing that goes into creating a WG that can bring new people with new motivations. A new WG is a way of doing that.

**Sam**: What would be wrong with doing that work here in this IG?

**John**: I know too little about what an IG can do? Can I do spec work here and then move it to a WG?

**Jatinder**: I thought we could only do non-normative work

**Wendy**: If we're doing work that requires patent commitment then we need a WG or CG. We could pair an CG / IG and the IG can oversee the use cases and requirements faciliated through the CG where the CLAs etc. were signed. That would likely require legal review of joining the CG.

**John**: WebAppSec feels like home so I take things there. Let's say we have an IG and WG for privacy would could discuss then take to the WhatWG. Privat click measurement is in the existing WG. The explainers in the Privacy Sandbox need to find a home.

**Brad**: For a lot of the stuff in there we're planning on going to the WICG.#

**John**: You would rather do that than go to an existing group?

**Brad**: Yeah.

**Mike**: I don't think that's as important as finding the right people who can give the feedback. I think I would be sad if Storage Access API was a totally separate document to the HTML spec. However as an explanation mechanism I think it's totally reasonable to have a separate doc that explains that as a standalone thing. However it points to the specific bits in fetch, in HTML, where the spec needs to change.

**John**: Another thing that was brought up at the workshop was if we had our own group we could guard the use of the word privacy and private so it can not be put on things that don't meet that.

**Sam**: The term privacy washing comes to mind.

**Mike**: Had a conversation about the incredibleburger™ and how it can only be used in certain places. However, I have some concerns about blocking where the words can be used.

**Jatinder**: By hosting the workshop we did see a lot of new ideas being discussed. It was a good venue for getting the community group together to discuss these ideas.

**Mike**: If we spin it up and it works, wonderful. I don't think we should see that as blocking progress.

**Jatinder**: I don't want to block, I want to see if we can speed things up.

**Pes**: There were different faces in that group, I'd be much more interested in a group that's more privacy focused than WebAppSec. Just from my time, it's hard to spread my time across all the topics.

**Mike**: Definitely don't care on process as long as we can get the work done!
tch
**Pes**: Mixed interest in creating a group, definitely interest in addressing fingerprinting - whether it's gating behind permissions or restricting access.

**Sam**: Where to do the work is one of our later topics, I would like to resolve that.

**Pes**: If people were interested in a group, what would be the next step?

**Sam**: A CG needs five people and then just press the buttons.

**Tom**: A CG can't make recommendations.

**Wendy**: Correct, but they can push to other WGs. That could lead to the creation of a new WG too.

**Tom**: Feels like we do have proposals that are close to the recommendation track stage, we coul just push to WebAppSec but it sounds like there's a tigher group that's interested in that.

**Jatinder**: I do worry that a WG comes with  a higher "tax" to create. A CG seems easier to incubate and discuss and then graduate to the WG when they're closer.

**Tom**: Storage Access feels ready.

**Mike**: I feel like Storage Access is done and ready to go to HTML. You already have the WhatWG as the place to do it.

**Tom**: So we create a CG and then create the WG once we're ready with the first draft.

**Wendy**: Sounds like you're saying that's not a solution.

**Tom**: Sounds like people aren't happy with a WG, but do we all consent to a CG?

**John**: It sounds like we will eventually need a WG. Do you have intended WGs for the Privacy Sandbox explainers? Not yet for Private Click Measurement. A Privacy WG would be the natural place for this.

**Brad**: WhatWG would probably be the home for Conversion Measurement and FLOC and Privacy Budget would go to WebAppSec.

**Mike**: Let's not spend the time arguing about venue for things that are done: write the Storage Access API PR, and submit it to WhatWG.

**John**: Let's get the CG created then.

**Tom**: Do we have the 5 people (5+ put up their hands)

**Wendy**: Does the PING want to sponsor the CG so that's the place where drafts from PING can go? Not a formal mechanism, but a useful flow to put in place, e.g. answering the question of I've got this draft but I don't know where it does? If so, the CG doesn't need distinct meetings and high overhead.

**Christine**: Yes, good idea. We'll have the hallway conversations and get that sorted!

**Nick**: Thinking about proactive things we can do, it would be good to have a list of problems e.g. the fingerprinting vectors and a list of solutions or things we would like to do. I was hoping the group would be the place for those kind of open ended discussions. I'm not sure where the right place for that would be.

**Christine**: My feeling based on what people were saying is that the running list of problems and potentially solutions would be in the IG and once there's sufficient interest it would shift to the CG.

**Pes**: This looks like the next agenda item!

### (todo: update time) 13:45-14:00: IG vs CG vs WG: where to write new privacy standards
[rolled into above discussion]

### 14:00-15:00: Development of W3C privacy principles (and browser privacy statements)

scribe: 

**Sam**: At the workshop we asked about what princples guided people, but we didn't put those down in a matrix and start categorising them. Is that something we want to do in this room? Build the list of W3C privacy principles?

**Jatinder**: We (Microsoft) though wouldn't it be great if we had a hippocratic oath we could subscribe to? Transparency, choice, control, etc. At the workshop we ended up with about 2 dozen suggestions. My suggestion was that we do have some alignment. Can we focus on that list of guidance we want to provide. I think we might make more progress on the technical side here rather than interpretation of words.

**Sam**: Technical is probably more productive...

**Nick**: Curious as to what those words are. It would be useful to have a document that was a privacy model for the web that explained those technical explanations. Hard to have those conversations with other parties when we raise these issues. Having those principles written down would really help, specific properties and expectations of the Web model, like not having permanent cross-origin identifiers, or state should be clearable by users, etc. Hippocratic oauth seems very different  - more ethical and individual - but the technical version would be easier and more immediately applicable.

**Christine**: It would be most useful if we can explain what we expect from a privacy point of view from a technical point of view. e.g. if we say "Privacy by default" versus "Privacy by design" can we technically define that.

**Tom**: I think we disagreed on how to follow fundamental principles. The principle is is "People shouldn't be trackable online.", but that doesn't seem to be helpful to us as a guiding light because we all balance it differently against other constituencies and tradeoffs. If we want to enumerate technical boundaries I think we will end up in the same place. I don't think it's non-productive, but "It should not be possible to identify a user agent on a subsequent visit" we may agree on that but I think we will run into issues with the details based on where we place different weights on the values and trade offs.

**Wendy**: Ties into the "Privacy Threat Model" session planned for later, use threat modeling to consider whom we're protecting, against what - we may come out with multiple threat models.

**Jatinder**: We should have the discussion, I think it would be useful to define a minimum bar. We need the flexibility to address things like user fatigue with permissions.

**John**: I worry a minimum bar will have people claiming they are privacy compliant without meeting the principles.

**Jatinder**: It will be a trade off, Brave for example raises the privacy bar while sacrificing compat.

**Tom**: Brave doesn't hit the minimum bar for privacy, that "you don't get tracked on the web". Privacy debt.

**Pes**: Mike, can you talk to us about agreement

**Mikew**: We can agree on things that have impact on user privacy. We may disagree on the value of changes and side effects. Threat model would be a list of things we see impacting user privacy. Possible disagreement: whether impacts of the feature justify changing the feature, mitigating, or accepting the impacts. We can have good productive arguments about the value of those impacts.

**TomL**: Let's talk about threats

**Jeffrey**: I started a rough document: https://github.com/jyasskin/privacy-threat-model rendered at https://jyasskin.github.io/privacy-threat-model/
click the checks to see how an attacker can currently accomplish. This piece of the threat model is all about transferring user IDs. There should be other sections covering other privacy topics. 

**TomL**: Tracking is the threat. Multiple dimensions. 

**Jeffrey**: I was experimenting with visualization.

**TomL**: maybe we want bullet points. Listing threats. e.g. a site can recognize me on a second visit. Whether because of cookie or fingerprinting.

**Christine**: Hearing from Tom that you'd like to spend some time brainstorming privacy threats.

**Jeffrey**: Also: learning which devices are around you.

**Mike**: Cross site, single-site. Many of the browser-mediated-hardware-access create ID opportunities. Also learning something about the individual that may not be identifying, such as having a game controller connected, also have privacy implications, indicative of preferences. Similarly, machine settings, such as prefers reduced motion, dark mode. Accessibility model. 

**Tom**: Recognition, configuration, preferences. 

**Mike**: One set of threats is recognition/identification: you're the same user who was here yesterday. In the context of one website vs distinct websites. Same threat, but talking about them separately is worthwhile. 2) Preferences of the entity using a session.

**Nick**: "Information disclosure" from security engineering.

**Mike**: Recognizer over time. 2) Above and beyond that identifier. Characteristics of device, context of device. Sensors. Timezone->location. They're exposed to the web and aren't identifiers on their own, but give you context of how 

**Jatinder**: +1 to break up first-party vs third-party recognition.

**Mike**: Initial opinion is to list threats. Weighting of those threats will be more contextual ... but maybe this document should say "if you make tradeoffs, do it this way."

**Tom**: Recognition same-site, Recognition cross-site, extra information.

**Wendy**: [RFC 6973, IETF privacy considerations.](https://tools.ietf.org/html/rfc6973) Can usefully discuss how these apply in the web context instead of protocol context.


**John**: Our threats weren't just as low-level as what we're talking about now. End goals. Targeting user with malware/ads. Manipulating user. Profiling user to learn about trends.

**Nick**: +1 that RFC6973 is useful. Think we can add things that are higher level. 6973 might take a narrower view than we want. "Manipulation" might be "Intrusion" from 6973. There are also actions site can take on user's behalf. "Cost user money". Some threats cross privacy+security.

**Steve**: If we just focus on identifiers, we miss why we care about removing those identifiers. e.g., protect against manipulation, abusive ads. Consider the higher-level.

**Christine**: In Europe, had a push that users must consent to cookeis, so websites add banner. Beyond fatigue, become a vector to get malware onto devices.

**Jeffrey**: Useful to have high-level goals and fundamental steps needed to use it. Fundamental steps are what build to high-leve. 

**Wendy**: Another angle/set of threats is the "surveillance capitalism". Desire not to become part of someone's dataset.

**Pete**: These points align with my personal politics. If our goal is to help people writing specs, I question how useful that is. People who've been frustrated with PING, are the things here useful:

**Jeffrey**: To design something that actually protects privacy, we need to know which attacker capabilities we're defending against, and which are hopeless. 

**John**: One of the reasons to mention the higher level goals, if we try to design all bad things, we'll miss things. Spec author will check boxes.

**PES**: Frame the list as necessary but not sufficient. 
  chaals+1
  
**Jeffrey**: Iterative document, like TAG's principles. 

**Jatinder**: Assume that spec writers have good intent. Authors aren't *trying* to subvert privacy. 

**John**: At the workshop, we had the conversation that the browser should track you instead of servers, and that's not good enough for us. We don't like the profile in the first place.

**Steve**: A privacy model needs to capture these goals.

**Mike**: Isnt' that captured with recognition cross-site?

**Steve**: It's about what the recognition allows you to do.

**Mike**: Put together a list of things the web shouldn't be capable of. I'd thought listing the technical abilities was enough, but maybe we need to start a level above that.

**Tom**: Am not saying they *always* need to be prevented.

**Mike**: Heard John saying "there are things you cannot do."

**Tom**: Think those things are bad, but as long as you can log into a website and tell it things, the web platform supports telling it things.

**Mike**: Things today that fall into what you're talking about. Brave does ads in the browser, but is the browser learning something about you and doing something on your behalf. Other ad models clusters users into groups. That's in the category of things that build a profile. Need to be very careful about things we say are "bad, period". The nuance is important. Black and white statements will be difficult for us to agree on. But information flow might be easier to agree on.

**Pete**: Another dimension is how to understand additional risk that parallels existing risk. Spec authors argue that "we're not making it any worse." I disagree. How do we reconcile that with the enumeration of threats. 

**Brad**: Like Jeffrey's description as a "target" threat model.

**Mike**: If there's no plan to remove the thing that does a bad thing, it's really hard to argue that we shouldn't add a place that does the same thing.

**Tom**: I want to get rid of the things. All of the threats below are things the web platform will be capable of. Thigns should be available whent he user is in control.

**Mike**: I think I agree with that? It's easy to make the argument that you shouldn't do X because we're in the process of removing X from the other place. Hard to make the argument that we have no idea of how to remove X, but you still shouldn't do X in the other place.

**Tom**: We should remove X.

**Mike**: There are places things exist on the platform that we can't and shouldn't remove, because the value of those things exceeds their detriments. Cookies: Quite valuable to have a session on a website. Can make changes, but the fundamental capability is valuable.

**Tom**: We have a list of capabilities. Our job is to make sure they're available at the right times but not at the wrong times. And the web platform is our backlog. 

**Jatinder**: We have consensus on enumerating the threats and trying to remove the bad ones. Mike's saying there will be some difficult ones. Nobody's saying that just because something's available today, we should extend it.

**Brad**: It's not identification that you can already do. So you can detect what OS I'm on by 30 different mechanisms, and there's pessimism about removing that. So we shouldn't argue against an API that exposes the platform.

**Tom**: That's conditional on us deciding something's definitely not removable. We should treat bad things as removable by default.

**Charles**: If we think something's fixable, then just because it's possible today, that's not an argument to do it somewhere else. It's hard to argue that "just because your friends are jumping off the bridge, doesn't mean you can", but we need to argue it.

**Nick**: Coming around to the threat model concept instead of what I called a privacy model. If we just come up with a list of threats, that's not consensus that we're trying to get to a particular state. Where we can, we should have explicit goals that we think we can get to and are going to try to get to. Also useful to identify things where there's a privacy threat but we are pretty sure we can't fix it. If we can find agreement there, it'll help a lot of privacy review discussion.

**Tom**: Do we have consensus that we should work backwards throught he web platform, and 

**Sam**: Privacy budget if it's going to work, assumes we're going to go through the whole platform and measure/mitigate entropy leaks. Might be some places we can't mitigate, but we'll have to mitigate most.

(npdoty: depends if they're cumulative or identical to some existing functionality or threat surface)

**Mike**: Agree that we need ot go back and look at old APIs. The fact that something exists doesn't mean it should continue to exist. Some things in the platform will be harder to remove than others. Worth spending time on the quick wins, while we also figure out how to deal with harder problems. Philosophically, we shoudl go back and fix everything. Practically, if that's the only goal, we'll have a hard time.

**Tom**: New stuff should be good, and old stuff should be made good.

**Jatinder**: Sounds like consensus.

**Artur**: [Jumps queue apologetically] Helps to think of less controversial APIs than cookies, where we don't have any idea of how to remove them from the platform. Web lets you time load of cross-origin resources. Lots of side-channels. Can say we won't expose any new timing APIs, but unless we have an idea of how to prevent exposing timing information via onload, etc., then telling devs they can't get the same information via a better way is a hard sell at the least. Onus is on people who want to prevent APIs with equivalent information, to describe a way to remove the information from teh platform.

**Tom**: I don't think we need to have already gone back and worked out the convoluted fixes for every information leak before we stop adding problems.

**Artur**: "Problems" implies that every API is bad. (?)

**Christine**: Trying to sum up where we are and next steps. I hear consensus that we want a document (Jeffrey's or another) laying out the privacy threat model, would be a good thing. A *target* privacy threat model would be useful. Describes how we want to go mitigate the things attackers want but users don't.

**Jeffrey**: I hope to extend this document in PING, if people want to work on it. 
(npd: +1)

**Wendy**: Underlying tension around Pete's notion of privacy debt. Shoudl we block new ways of getting things people can already get and we don't know how to get rid of. May not achieve consensus, but still useful to enumerate places the platform allows privacy risks. Might find consensus or find that different implementations go different ways, but still useful to identify those choices.

**Jatinder**: We seem to agree that a threat model is a good idea. Jeffrey's started the document. Good to work on that together. Can then talk about mitigations on present, future APIs.

**Pete**: Any other consensus?

**Tom**: Consensus that we should go back and isolate and remediate/isolate threats in web platform wherever possible. 

**Pete**: "Wherever possible" does a lot of work in that sentence.

**Mike**: That's reasonable. Add that a way to get less resistance is to address the underlying use case, if it's a use case that you find acceptable. e.g. Client Hints help remove information from the platform by default but can gain a subset in ways we find more palatable. General idea of giving people a well-lit path is effective way of reducing the capability. 

**Tom**: There's a lot of heavy lifting around whether we agree that a thing people want is a thing people should have. Is value high enough to provide things everywhere instead of somewhere.

**Mike**: Yep, vendors make that decision a lot. If there are low-capability ways of giving a thing, it's better than the high-capability ways.

**Tom**: And if there are 1000 different small things, it may be ok to get any one of them, but 10 gives you a different thing instead.

**Mike**: Look at direct attacks, look at side effects of combining unobjectionable things.

**Tom**: Unify the unobjectionable things into a brightly lit path.

**Pete**: Is it appropriate to object to a standard if there's a more privacy-preserving way of achieving the same functionality?

**Nick**: There's disagreement on whether it's exactly the same functionality. Agree with the question, but in practice you still wind up arguing.

**chaals**: in practice, you get hung up on performance and user interaction.

**Pete**: For exmaple, in unique device ids, there may be another way of describing devices without identifiers, given that proposal, it should be a reason to oppose unique identifiers.

**Brad**: In that in particular, had they identified a use case that wouldn't be satisfied?

**Pete**: In that case, implementer difficulty?

**Pete**: Test for concensus: Duplicating a risk that can plausably be removed is inappropriate for a new standard?

**chaals**: Is "plausible" important? Duplicating a risk is inherently a reason to object (because it adds a mole to whack when we want to mitigate the problem)

**Mike**: That's important. Can remove the web to get rid of the risk, but that's not plausible.

**Kleber**: Intersection observer: Don't know if detecting whether a rectangle is on-screen is a privacy problem. 5 years ago, that was about 1/4 of the browser CPU spent knowing if the rectangle is on the screen. Because of ads. No good way to do that, but there were lots of hacky ways to do it, which cost lots of CPU. Intersection Observer took the clearly defined use case, added an API, ad industry migrated, and we improved battery life of mobile devices by about 1/3. Even if it might be plausible to remove the core ability to know where you're scrolled, it was still useful to give the cheaper path.

**Tom**: When I'm just reading a site, it shouldn't know what I'm looking at. The fact that JS allows you to do anything badly is unfortunate, but don't think that's a justification for adding ways to do bad things well. Blame the sites for using mobile battery.

**Kleber**: Don't exactly agree with proposal, depending on timeline, because improving situation until the underlying capability is removed, is still useful.


- pes: alt possible consensus points:
  * if there is a more privacy preserving option with the same capabilities, we should always preserve <- success!
  * duplicating a risk that can plausably be removed is inappropriate for a new standard <- mixed / no consensus
  * we should aggressivly remove risk from existing standards <- not discussed [pes annotations]


Sam: Please join PING. If you're not a W3C member, you can join as an invited expert. We use Slack: ask the chairs for an invitation.

#### Threat/risk list
1. Unexpected Recognition (being confident that this is the same person/device you saw before), cross-site
2. Recognition, same-site
3. Benign information disclosure (connected hardware [game controller or assistive device], system preferences [like dark mode]…)
4. Sensitive information disclosure (user location, user camera, file information, financial data, contacts, calendar…)
5. Intrusion (displaying messages/notifications, playing sounds, full screen…)
6. Obtaining capabilities (sending SMS, finance/billing…)


### 15:15-16:00: Afternoon break

### 16:00-17:00: Horizontal review topics, joint with i18n (in PING room!):

https://github.com/w3c/i18n-activity/wiki/i18n-Horizontal-Review-ideas [confirmed]
w3c/i18n-activity#759


### 17:00: Any other business





