# Privacy Interest Group meeting - 19 September 2019

Location: Navis C (Level 1)

## Attendees

* Christine (invited expert, co-chair)
* Pes (Brave, co-chair)
* Tara Whalen (Google, co-chair)
* Sam Weiler (W3C/MIT)
* Jeffrey Yasskin (Google)
* Tim Dresser (Google)
* Wendy Seltzer (W3C)
* Jatinder Mann (Microsoft)
* Eric Lawrence (Microsoft)
* Chaals Nevile (ConsenSys)
* Dave Singer (Apple)
* Brent Zundel (Evernym)
* Michael Kleber (Google)
* Tom Lowenthal (Brave)
* Terri Oda (Intel, remote)
* Pranjal Jumde (Brave)
* Konrad Dzwinel (DuckDuckGo *observer)
* David Harbage (DuckDuckGo *observer)
* James Fishback (Wikimedia)
* Diogo Cortiz (W3C Brazil Office *observer)
* John Wilander (Apple WebKit)
* [insert your name here]

Regrets: Jason

## Minutes:

### 9:00-9:30: Privacy CG/IG/WG discussion: practical next steps

Pete: Split business between IG and as-yet-unnamed CG. Division of responsibilities. Potential co-chairs, meeting times, etc.

...: A suggestion is to have horizontal review, guidance (meeting with groups who want advice, threat model document, etc) owned by the IG. CG could own any spec work, and take responsibility for going backwards and revisiting old specs, pushing mitigations into old documents. Is that a reasonable division?

Jatinder: Microsoft and Mozilla hosted the privacy workshop a week and a half ago, primarily because we didn't feel like we had the right venue to bring the right folks together to have a discussion about how to standardize privacy-relevant work. Would like to see the IG continue for HR, creating documents like the threat model, gathering requirements. Will need to listen to publishers and ad networks and etc. This is a good venue to continue that listening. Would like the CG so we can focus on creating new standards, moving forward technical discussions. Doing that in the same IG will cause distraction, slow down progress. Can take things to WGs (WHATWG, elsewhere) in order to push normative changes.

...: Would like multiple chairs for the group. Microsoft is happy to sponsor one, Aaron Anderson(?) might be a good candidate.

Chaals: What was wrong with the IG? 3 groups is a lot to deal with.

Tara: Rally just 2.

Chaals: Still.

Jatinder: We wanted to find an existing venue. Talked to a lot of vendors, 9 at this workshop. Heard feedback from some attendees that PING was sometimes distracting. Other customers that might slow down progress. Very focused on technical discussions, made a lot of progress in two days. Valuable to have a CG focused on incubating the privacy standards.

kleber: On the subject of customers: the web advertising business group is another good venue. On the browser side, it had Google and Apple (though Jason Novak just left, hope for a replacement from Apple), sounds like MS might get involved as well. Others from other parts of the ads ecosystem, very educational.

toml: I want to distinguish the activities more clearly:

...: HR and being available to all the other teams, WGs, etc. as a place to go with privacy questions is a thing that PING is showing it's proficient at. Would like for it to focus on that one activity. CG is a good place to incubate materially separate work of specifications, technical changes.

...: There are folks who want to work on those technical changes without doing review work with other WGs, and others who want to do the review work, and don't want to sit through half of a call talking about a new privacy spec.

...: Having focus in a group seems advantageous.

pes: Internal process changes for HR should stay in the IG. Different skillset than folks working on spec work. Increasigly large part of the conversation here in PING.

...: Wendy, can you walk us through why we would do this? Subsetting the CG as a part of the IG?

wseltzer: The CG has a contributor license agreement that members agree to. Contribution-level patent commitments. IG isn't producing specs, doesn't have the CLA. That's one reason that the CG is a good place to do spec work. Open to anyone, W3C member or not. Can be coordinated loosely or tightly with IGs. Pattern we see is the pairing of a CG and WG. WebXR & WASM are recent example. CG for incubation, WG for REC-track development. IG can work with the CG on talking about the ideas that are being incubated, and helping the CG (or not!) to figure out where the specs would go after being incubated. Would things go to an existing WG for REC development? Should we spin up a privacy working group? 

...: Up to the PING chairs to see how much of a dispatch function you want PING to serve. Need to point folks to the right answer to "Where should I do this privacy thing?" How much discussion you want in PING vs elsewhere.

Chaals: Whether you have multiple groups or a single groups is a working style preference. You talked about not wanting to slow down work. That's exactly what folks say when they are trying to move forward with their development, and don't want to get derailed by people saying e.g. "we don't want to get sloewed down". It's a red flag when folks go off on their own "to make sure the work doesn't slow down" - the desire for effectiveness makes sense, but we should be clear to remember the point and make sure we don't fall into the trap.

Jatinder: I think it's exactly that point. We worry that we've gotten feedback in other groups that because it's not focused on privacy, that conversation is slowed down. By having a set of like-minded folks focusing on privacy, we won't be slowed down.

dsinger: I worry about fragmentation. We're a small community, worried we won't be cohesive as a community.

...: Horizontal review: there's a deeper purpose to HR, to expose ourselves to privacy problems as they arise, learn about all the aspects of privacy, better understanding of how privacy appears in specs, important part of HR. Point of TAG doing HR is not the review itself but that TAG has an overview, emerging problems, etc. Seeing things happen as they happen is an important learning exercise.

Christine: My take-away is there's a case for having slightly different places to do the work, not least because of the requirements needed for doing spec work. Need to be careful in the mechanics that the PING and CG are coupled to combat the fragmentation concerns.

pes: I hear concerns, not sure they boil down to "No we shouldn't do this thing." Is anyone actually against this thing?

chaals: I'm not going to stand in the road, but wonder what people prefer?

pes: We can't do spec work in this group.

chaals: That's wrong. You can incubate a spec in an IG.

brad: No IP protection. We have a CG for incubation already.

pes: WICG is a very different community with a different set of interests.

brad: IT's a community interested in incubating web specs and sending them to a WG.

toml: You have a rosier view of that group than I do.

jatinder: We need to change something; no CLA in IG. Could take things through the WICG, that's possible. Or we could create a similar group focused on privacy. Very similar to WICG group, but more focused. MS is interested, don't want to keep hosting private focused events, want a broader group.

wilander: I talked with some Googlers last night. WICG is, so far as I know, championed by Google, a lot of what Google is doing is incubated there. Others feel that they want something new, take the platform in this new direction. Happy and inspired with a new place to set the tone and do their things. That seems to be the reason why some would like a new CG. They're not saying WICG is bad, it's doing great stuff, but it's not a breath of fresh air for privacy on the web.

wseltzer: A reason that PING hasn't been doing discussions of spec work is that they haven't been coming to the group. It's great to see that happening now. CGs are a shell we can fill with whatever we want. CG can be a repository for PING to use, or can run as an independent or related group. The option I want to put on the table, how much extra infrastructure vs using a task force within PING that hosts its own calls.

dsinger: WICG is the worst option. Large, amorphous group, no sense of identity, no development of esprit de corps.

chaals: I disagree. In the arena where many specs we want to see developed. Collection of communities. Could happily develop in that context.

pes: Based on the conversation we had with WICG on Monday, they were not eager for early engagement from PING. They were not asking us to join WICG and give feedback.

jeffrey: I've heard some worries about the governance of the CG might be. Hard to talk about it without a concrete proposal. Standard W3C governance model seems reasonable.

pes: Could you explain?

jeffrey: Second hand: Heard of a WHATWG-like process based on browser engine implementers.

jatinder: Not sure where that came from, interesting. MS is super-supportive of WICG. No problem with WICG. Practically, though, this group needs to organize separate calls and meetings to talk about the things we're incubating. Might as well call it a CG.

brad: Putting the work in the WICG gives you IP protection.

jatinder: Proposal is not to do work in PING, but in a new privacy group. Still means that group needs to get together and talk. It's a CG without a name, might as well give it a name.

pes: Does anyone writing privacy specs want to go to WICG?

pes: Why?

brad: Well-known process for moving specs forward, wide community.

pes: Are you interested in examining existing specs, or authoring new documents?

brad: All the documents we're talking about in privacy sandbox, we're interested in moving forward in WICG.

pes: Will continue this in the final hour as we're running out of time.

toml: Sounds like there are some folks who want to write specs in WICG, others who thing WICG won't achieve their goals. Seems reasonable for folks to put specs in different places.

sam: I heard brad saying he wants feedback from WICG, but would be happy in a new CG?

brad: If specs are privacy-focused, I'd expect PING to talk about it.

sam: Or the privacy CG?

brad: Sure. We can join another meeting.

toml: IG should focus on wide review. Not incubation. Question of where folks want to spend time. There is a critical mass to form a privacy CG. We should just go ahead. Those who want to join should do so, those who don't shouldn't.

dsinger: We want people in the broader community to notice the work. A separate CG is not a way to hide from anyone.

pes: Let's finish in the last hour.

### 9:30-10:00: Ralph Swick re: issues raised in HR Time discussion 

Pes: There are a number of PING initiated concerns around the High Resolution Time specs. Issues were raised to Directors, decisions are close to being made, this is a post-mortem to understand how can we be more effective in the future.

Ralph: Want to be clear that privacy is important, privacy reviews that happen on W3C specs are critical, and the purpose of the convo this morning is how to improve what we're doing and better use of everyone's resource to the effort. Those capable of doing horizontal reviews of specs typically don't hear early enough in the development of a new standard to have the influence that you want to have. This is an issue that we've struggled with for a while, we don't have a perfect fix, but I'm hoping we can better. One discussion, what signals do the groups needs to contact WGs for the right privacy group. The HR2 spec was frozen before the privacy converastion could happen. 

Pes: Would like to move the converstaion to two directions: how can PING get involved earlier and what feedback can we give to influence the direction.

Chaals: For privacy, it's useful to have a look at the general decision thinking very early. You'll get feedback that we're not ready for review, but PING will want that review.

Sams: A second example, web of things. The feedback we got from them is 'we really hope you dont have any changes for us, please'. We don't want to review things when they are finalized, we want to review when they are ready to change. I worry about WICG process that even when they come to WG, they are not ready to change.

Jon: Not a part of PING reviews, but Apple has been reviewing specs from privacy perspective and file issues. These issues are typically flushed out and acknowledged, but nothing happens. It takes time to do privacy reviews, enumerate threats, talk about mitigations. Unless, you know you get better privacy out of the review comments, people won't do it.

Ralph: Another example?

Jon: Web Packaging. Gave feedback, people acknowledged it's a problem, but not action.

David: There's a case where a spec is designed in a way that it needs to be fully re-archited. Don't want to give feedback late, when many specs are built on top of the initial spec. I want to see AC and Director to see privacy review in clear form to Directors and others before specs are published. E.g., we want to say this spec is good from privacy so can be published, this is red can't be published. Payments is the other example where they want to fix in V2.

Ralph: Director pushed back, wants fixes in V1.

Pranjal: Question on the word frozen. PING has discussed going back to existing standards and try to figure out issues. What's the right way to go about doing this?

Ralph: We always want to maintain specs and produce version n+1. If we can't fix the issue in the next published version, continue to work on them to fix them. Ultimate recourse we have is to recinde a spec. We've never had to do that, but it's an option. It's important for us to realize that there's various pressures that cause technologies to be shipped before they are ready. I insisted that HR time hasn't resolved the privacy issues and they need to re-open the issue, even if we don't find a resolution that satisifies the privacy and web perf communities. Make sure we identify that it's not a resolved issue in the current editor's draft that points to the open issue in GitHub. Not completely satisfying resolution for you, but at least we shouldn't state that things are closed.

Pes: We had a valuable conversation in the hallway that PING should review specs right when incubation ideas are ready for TAG review. This is an implementer policy, not W3C. 

Mike: We spoke about Blink process on Monday. We noted that TAG review is a mandatory part of the Blink process, we want to make sure we do not miss anything. For many specs, we are asking too early practically. We talked Monday about giving feedback when things are further along when you can see the actual design. But that's a hard magic spot to find. So we want to get people involved early, and we want the feedback to be useful. Internally, we find TAG review very useful. We think we can find ways to involve PING earlier. Feedback from Alex and Chris on Monday was around PING building up the credibility within the Blink community that the reviews are going to be valuable. Part of the conversation is to build a threat model. We're making good progess, Jeffrey's doc is very good. Once we get good feedback around the threat models. It's perfectly reasonable for folks in Blink to ask for feedback directly from PING. Right now we have a single spec for Blink developers and there's a clear process for doing so. If we can find a reasonable way to integrate things into that process, that feels reasonable to me personally.

Ralph: The signal that a group wants TAG feedback, that seems like the right time for other hortizontal review groups to at least glance at the spec and give feedback earlyJeffrey to discuss Web Packaging and how PING can convince implementer security+privacy teams in the design process. Either we see a problem or feedback on potential designs. Finding the sweat spot for when the design is mature enough is going to be an ongoing judgement call, but setting the GitHub flags to see when comments can happen early enough.

Mike: Tom made a comment about not wanting to be sea-lioning someone's design. Don't want people to feel that no one asked for their feedback. 

Jeffrey: I want to apologize to Jon why we're not responding fast enough. Part of the reason we wrote the threat model was going to our privacy teams and asking Brad, who's leading our privacy efforts, to understand what should be blocked. Blink ships things before standards are done, to experiment, the way to slow that down is to convince the Chrome privacy team to block the change. The threat models was designed to get feedback from internal teams, so that if the internal teams are bought on, they will block new features if they don't meet the bar.

John: Thank you for pointing that out. I was not super sad at the delay in response, I expect it would take time to respond. I was disappointed when the news was published that this new thing was published in browsers.

Jeffrey: It was inapprop for that blog to say that modern browsers support that tech when it was still in reviewed.

Christine: One positive feedback we're hearing from other groups that they're realizing the horizontal feedback has been useful in development of new specs, and that it is important to not look at the spec in isolation for privacy considerations.

Tom: I don't want to pick on you since we heard the same thing from other people this week. We've heard that to have an impact on the standards process you need to convince internal teams to do something. I don't care about your internal process, I care about the public standards process. It's not my job to change your internal process. It's your job to adjust your internal process. If I don't hear about internal blink process, it'll not be too soon.

Tess: What I would like to see active engagement from PING to work directly with engineers directly, so you don't have to worry about internal processes.

Brad: The claim was you saw a blog post that's internal, standards is not internal process.

Mike: Just want to give an update on Blink process. There's a public process to ship Blink APIs. You need to get three LGTMs from Blink API owners. Most of the time it's not controversial, but there are times when we get public feedback that an API is bad. A lot of time we get very good feedback from Mozilla. We like that this feedback is given publicly from you and others.

Pes: Ralph, what can we do to have a greater impact on the Director's decision in the future.

Ralph: Our goal is that specs follow the direction that we want technologies to go. Don't be discouraged by short term failures. One suggestion from Tim, was could there be non-normative text to set that direction. The feedback that the WG get early and often feedback, we'll work with you to make sure that the groups are aware that they need to get that feedback and often. I'm wondering if there's an too early conversation. I was optimistic last year on new toolings so Director can have a better sense of the direction of new standards, but the tools haven't materialized. The discussions that we're having with payments, HR, that we need groups to talk to PING.

Jeffrey: I wasn't involved in the HR time discussion. Apologies if this is wrong. My impression was that the review wasn't very convincing. It rates reviews that browser security teams had already looked at and the PING review wasn't convincing enough to convince the browser security teams that change was really needed.

Pranjal: We've seen concerns that non-normative text leads to confusion. We would like to not see privacy and security as non-normative.

Ralph: In this case, it's not advice for implementers of the spec, but to developers using the APIs. To help them identify how bad actors could use the interface in an inapproperiate way. It's not a direction W3C specs typically engage in. I'd refer to TAGs recently paper on ethical web standards.

Sam: A couple of weeks ago we offered to get meetings space for Friday, confirm no one wants it? Great!

### 10:00-10:20: items of interest learned from other meetings this week

Peter: Other issues that need to be on PING's agenda?

Tara: Or what have we missed?

* Sam: Yesterday the telecom auth session proposed an authentication scheme, where the mobile operator attests to the number in use. These are all linkable identifiers: a phone number. And they just trust the mobile operator as proof of possession. They're not using WebAuthn. :( Folks from somewhere in Europe said they're using SMS as a second factor, and this is better, so let's standardize it. Be aware this is out there. 200M users, 100M auths per day. And China doesn't have number portability.

Tom: Good cue to revisit the question of the earliest possible point to engage. If we need to change foundational things.

* Christine: At the Publishing WG, was excited that they're very interested, and they send documents they want PING to look at. And used self-review questionaire about audiobooks.

Link to documents to consider:
https://www.w3.org/TR/audiobooks/#security-privacy
https://www.w3.org/TR/pub-manifest/#security-privacy
https://github.com/w3c/pub-manifest/issues/61

Christine: Decentralized Identifiers (DIDs) WG: They're self-proclaimed privacy advocates, and PING folks are attending. They're keen to ensure design is very privacy-respecting.

David: What Sam mentioned: we're seeing groups that replace proof of authorization with proof of identity. Seeing this more and more. May need to make clear that that's not great for privacy.

Chaals: What Dave said. Should be careful about saying "that's just stupid" and chasing people out of the room & organization. They'll build the same system elsewhere. In this specific example, see things that are concerning, but see strong parallels with how I authenticate work systems, which is by showing I have a Google Account. Functional difference between that and having a telephone isn't huge. Big question is who has control of the information. Even if we think there are serious concerns and this should stop, we need to say that in a more effective way.

Tom: I disagree with your first point. Just because someone's going to build a bad thing anyway doesn't mean that a standards org should sign off on it. 

Chaals: Didn't mean to say we should agree to a bad idea. We should still be clear what's good and bad, and shouldn't sign off on it just because someone can threaten to do it anyway. It's about how we approach things initially.

Michael: Agree with Chaals. Constructive engagement. "What goals are you trying to achieve? How can we achieve that goal in a way that has better properties?"

* Wendy: Pleased to see whole privacy track on the breakout day, and look forward to seeing those ideas coming into the CG for discussion. Let's revitalize the sense that the web is doing positive things for privacy. Will mention that work in the Advisory Committee.

### 10:20-11:00: break

### 11:00-12:00: Planning of deliverables

pes: goal is to assign people to take charge of moving forward the things we want to get done.

pes: what can be useful, who will take the lead on these things.

**Privacy threat model**

pes: Jeffrey and tom leading this?

tom: we can put together a draft and see where we go from there.

pes: What would be the best way to support you for the rest of us?

jeffrey: Please feel free to write up PRs suggesting capabilities, threats, etc. Tom will write up the initial piece but I would rather we didn't do all the writing.

tom: THink we will start from the conversation yesterday taking the high-level threats and apabilities, and what should oly occur on purpose not by accident, then branch into the detailed descriptions of where we think there are current risks in the platform. We might do some restructuring / reorganisation so you may want to rebase. You are also welcome to file issues with an explanation rather than having to do the work of folding it in yourself.

jeffrey: Repository is moving, please wait until it is in the right repo.

Jatinder: When it is there we will put the MS Edge Privacy team onto it...

Tom: cool.

pes: so give a shout when it's ready please.

Michael: curious what the feeling is on wehether the doument should look intothe question of trade-offs, enumeration of risks might persuade people to go with relative seveiry - how do we make tradeoffs?

tom: Don't think we have a good consensus there so it might be premature to put it in. Speaking for myself, I'd be happiest enumerating the risks, and start to accumulate tradeoff balances as we do reviews - collect the particulars of cases before we try to lay out the general rules.

jeffrey: Would like to call out in the document where there is not consensus

chaals: +1 to Jeffrey

Michael: when we talked about horizontal review, DSinger talked of a traffic light model. Does that belong in the threat model doc, or something about ping policy for reviews?

pes: The proposal is across all horizontal reviews it is to help have a clear view across the set of different horizontal reviews.

tom: Think that as we start a review, we get a treaffic light. don't want to get ahead of ourselves and document tools that don't exist yet. We can update the thing with particular reviews to collect the history so we can map out the comfort space

michael: makes sense. think it is part of how you get horizontal review happening. A key is the abililty to see some sort of guidane that sets expectations helps people get comfortable with horizontal review. So what makes things red/yellow/green might help getting people to come forward.

tom: agree. But not sur we have the answers yet and not sure I want to write that on behalf of everyone without a history to call on. Think it would help have conversations on where we think those liines are as PING discussions. They are effective when we are working from practical examples - privay reviews will feed that.

chaals: I think the traffic light thing is about tooling. I think this task was for W3C to provide those lights as a tool for all HR groups. And I'm with Tom as to going to reviews and finding what we called as being different lights and recording those or going back to change them when we think that we've made mistakes.

Christine: stating the obvious, red/green/yellow shuld be separate from the threat model. Don't want to mix it in to thed detriment of the work.

jeffrey: possibility of yellow lights informs the threat model. Some things are *sometimes* but not always bad.

pes: let's not mix "who is leading this" with doing the design work for them. Sounds like tom and jeffrey are on the hook for threat models - thank you. We should move on now, and that work will continue.

**Tooling**

pes: Who is going to take the tooling discussions to the process group?

DSinger: had a discussion on horizontal review. i18n have some tooling to tag issues, and we are looking at generalising that as a way of helping us manage review by seeing things. This won't always be right, and if we rely on it being perfect we will miss stuff and have to come back late in the process. I hope that leads to quesions coming to PING when there is still scope to make changes. There is also interest in the traffic lights.

pes: We agree, who is the champion for it within PING?

Tess: Dave.

Dave: Yes, I will take this on in the context of PING. So talk to me, i18n, ... We (expanding the blame pool to include chaals) will try to keep you posted as we are developing this.

**Retrospective review/mitigating risk in new + existing specs**

pes: the fingerprinting is the one I can think of and that is me. Anyone else want to volunteer to take on a specific task?

Tess: are you looking at font table access and ..? Would make sense to review them together

pes: Want to distinguish reviewing new stuff compared to existing stuff. We hve discussed WebGL, Web Audio, ...

Nick: I like the idea of talking about listing the highest priorities an going down the list. On that 2018 paper: font enumeration, user agent strings, canvas. Not sure we want to do something on canvas, hope we make progress on fonts. User Agent strings has some entropy and it seems to be getting worse. Can we freeze them? Use client-hints to make user agent details opt-in? Would be good to have the list and start picking off pieces.
'
pes: we can also look at whether something is close to shipping.

brad: We are starting to work on implementation in CHrome. On meta-level does it make sense to separate new and existing specs? For WWGs doing privcy-sensitive work do we want to assign liaison to go to their calls?

Nick: shipping client hints in general, or for the user agent?

MW: We are shipping client hints generally behind a flag. UA client-hint is implemented. We are waiting on a dependency and then we can ship, so it's a question of timing, an then how do we remove entropy?

Nick: Where is that discussed?

MW: Repo in WICG. File issues there. No intent to ship yet, but working on a plan for that. I suspect we would ship UA client hint, get people using it, then remove entropy over time, but feedback on that idea is welcome. There is an outline in the explainer and it isn't very detailed yet...

> https://github.com/WICG/ua-client-hints

tom: changing tracks, in terms of going back through existing specs, there is a huge pile. We should create an agenda looking for low-hanging fruit vs gnarly problems, and every time we are not buried in new stuff, we should go back in remediation. That probably needs a champion, maybe the chairs but I am hoping Nick the sky-light-god can do this curation task. Nick?

Nick: Interesting idea, cannot commit to the work unfunded at the moment.

pes: let me know how it goes.

chaals: sometimes review of a new spec is a good trigger for fixing a problem that also exists ion old things

pes: OK, hopefully nick and I an work out how we are going to lead this

Privacy reviews/assistance requested

**Deciding who will champion FP mitigation methods in existing standards**

**CG creation**

pes: I talked to Wendy about how to formalise this, there are at least people interested, so I am happy to take that on as an action item assuming potential hairs can become atual ommitted chairs.

Jatinder: Would be great to see broader coverage from browser vendors providing chairs. Would be nice to see more

Tess: I am working on trying to pony up somebody. takes time...

pes: Will get the group set up, will wait on Moz/Apple/MS, and anyone else, who wants to take on the work.

Nick-the-sky-god: CG sounds cool, I like the idea of working with the IG. What is the status on chartering the IG?

Sam: There was a formal objection to the charter, have not been able to resolve, so may take the charter for the director's approval overruling the objection. Don't **expect** us to fall out of charter. Ther was a question about trimming the charter, I think we can go with what we have, and let the CG make some parts of it redundant in practice to be fixed next time when the world has actually changed.

**Open issues**

pes: some of our issues will be discussed tomorrow with WoT, WebRTC. Think those have leaders but if anyone wants to step upo on issues, GH has a very handy "assign yourself" button...

**other business**

Christine: we might have a couple of meetings with groups tomorrow: WebRTC 9.15am to talk about specific privacy issues. Web Payment Security at 12-12.30 mostly get to know you, intial conversation. Web of THings 1-2. Please if any is avialble go to those meetings.

Sam: Anything we can usefullly follow up from breakouts in the next 20 minutes?

Tara: THere is webappse in this room this afternoon.

Mike: Suggestion we talk about hte scope of webappsec, wondering if it should be doing more privacy work. Don't know of concrete plans but it is a worthwhile conversation to have, please look at the agenda, expet it late in the day.

**[adjourn]**

pes: Thanks everyone, we got through the agenda, looking forward to more good waork happening and the web becoming perfect. So we get an early break.

thanks to chairs, scribes, sky-gods, participants, ...




