# Privacy Interest Group meeting - 19 December 2019


## Attendees

* Tara Whalen (co-chair)
* Peter Snyder (co-chair)
* Christine Runnegar (co-chari)
* Brad Lassey 
* Wendy Seltzer
* Nick Doty
* Michael Kleber
* Wendell Baker
* Brent Zundel
* Konrad Dzwinel
* Dave Harbage
* Melanie Richards
* Jason Dorweiler
* Theresa O'Connor
* Jeffrey Yasskin
* Scott Low
* Anthony Nadalin

## Agenda:

Agenda:

1. Web of Things Architecture request to move to PR

https://github.com/w3c/transitions/issues/202

2.  Privacy threat model (status check)

https://github.com/w3cping/privacy-threat-model

3.  Privacy reviews - process

4. Privacy reviews

- Time Resolution 

https://www.w3.org/TR/resource-timing-2/

- Screen Capture 

https://www.w3.org/TR/2019/WD-screen-capture-20191119/

5. Update on open issues

6. Update regarding Privacy Community Group

7.  AOB

## Minutes:

scribe: lassey (for the first half), npdoty (second half)

### Web of Things
**pes**: Wants to move forward, larger architectrure doc isn't specific enough to evaluate for privacy. That decision was overruled, so it is moving forward to standards track. Does anyone want champion a formal objection?

**Nick**: No strong feelings. Not sure it matters much, won't affect other parts of the web. Can we at least get responses in there noting the open privacy issues? If we can get that ack, we don't need to hold it up.

**pes**: There have been 4 or 5 calls between PING and WOT where they have said that there will be more details in 18 other docs. Does that addresss the concern?

**nick**: can we note which docs?

**pes**: no, they say they can't specify it in this doc because its a descriptive doc not a prescriptive doc.

**nick**: Would still apreciate some note saying that there's more privacy text coming.

**Christine**: Your proposed approach is a sensible one. At least noting that mo

**Brad**: How is this a standards track document but not a normative document?

**pes**: This is a bizarre mismatch, but director overruled my complaint about that

**wseltzer**: Note that in the [proposed WOT re-charter](https://cdn.statically.io/gh/w3c/wot/master/charters/wot-wg-charter-draft-2019.html?env=dev) the WOT group has committed to putting privacy considerations in identifier management, which seems like a good place for us to engage. Perhaps we could put that in a comment. I'm trying to figure out what you mean by this is normative but not normative.

**pes**: WOT describes this as a document that surveys what exists today, and yet its on the standards track as a normative doc.

**nick**: There is some open question about whether the doc is drescriptive or if it is propsing something for interop

**pes**: Yes, but if it is describing something new it should be able to describe the privacy properties of the new thing.

**wbaker**: Why hasn't someone from WOT championed this

**pes**: we've done that, PING objected due to open issues and the director overruled. I'll take AI to draft a prefunctory response.

### Privacy threat model

https://github.com/w3cping/privacy-threat-model

**jyasskin**: I've started to send PRs to add bits of text. My prefered operating model is to send PRs and have someone else approve them. Does that work for the group or should I be more agressive.

**Christine**: I think you should be more agressive and just push things at this early stage

**pes**: being agressive for initial text is fine, but if you and Tom can be co-agressive that would be useful.

**Jyasskin**: OK, I'll work with Tom. I've got intitial stuff done. Working towards low level stuff. Probably mid-January we'll have something worth reviewing. Would welcome comments about what needs to be in there or what needs to change.

**Nick**: What specifically you want from us? should we be looking at the existing document? or listing privacy concerns that arent' touched on yet

**jyasskin**: stuff that isn't covered yet is most useful

**Nick**: should we talk about this on the mailing lsit

**jyasskin**: I tend to use github issues, but mailing list discussion is fine.

### Privacy reviews process

**pes**: jyasskin suggested some rotating group to be assigned to reviews. or every org contributes at least one person?

**wbaker**: I would recommend the manditory round robin. Want to avoid the council of elders, shoudl require everyone to do at least one to get the feeling of community

**jyasskin**: we should at least have a group of designated experts to ask questions of

**tess**: from TAG we have a triage and people volunteer. If we don't get at least two volunteers, the chairs assign people. No set process for assignment, could be round robin, but also takes work load into account.

**pes**: happy to hand hold and mentor people who are doing their first review

**Nick**: I like the round robin, but asking for volunteers so experts can step up for things they know.

**jyasskin**: the threat model document should also be a good resource. If there's anything that's not covered, please let me know.

**Christine**: don't forget we have the self review questionaire and we should be encouraging WGs 

**pes**: Recommendation: for every group that has a member on PING should make one person available for privacy reviews. We can take volunteers as a first cut, but if there are none we can pull from the queue. I'll take an AI to write that up.

### Time Resolution (Resource Timing)

**pes**: duck duck go will be joining us for privacy reviews

**kdzwinel**: We are fine picking this up, is it OK if that won't happen until Janurary?

**pes**: Most W3C machinery will be shutting down anyway, our next call will be on the 16th, so having a review by then will be fine.

### Screen Capture Review

**lassey needs to hand off now**
scribe:npdoty, thanks brad!

wbaker: an offshoot of Media Capture and Streams, proposes a method to point at a window and have that shared. also possible to share monitors/screens. the web browser could get in a situation where it shared a screen inadvertently. 

wbaker: for phone, TV or desktop use cases. in an office environment, it's clear that you're logging into an application, and punch a button to share, with a ceremony to choose what to share. sometimes people walk out of a meeting and are still sharing without realizing it. would be even more problematic in non-office situations. 

wbaker: can the user be legally culpable in the sense of two-party consent states?

wbaker: section-by-section noted things that worked well, and omissions. and answered the security and privacy questionnaire briefly. per npdoty, if you're sharing your screen, it's likely that you're sharing personal information.

wbaker: next step, share with the mailing list and get further comments.

pes: thanks! for PING mailing list or the webrtc list? -- public-privacy@ mailing list for now.

pes: question about the handles that the website gets back when the user agrees to share a screen or window. is there a unique identifier in the handle that's returned?

wbaker: the proposal is to re-name/re-number all devices. sounds like complex/a lot of work, but the spec doesn't need to explain the exact implementation.

jyasskin: privacy indicator requirements about notifying the user about what is being broadcast. how much does that mitigate the concern about accidental/inadvertent broadcasting?

wbaker: a little bug at the top of my phone status bar that I'm in a call -- but is that going to be enough? red light for recording. zoom has something similar. given the invasiveness, if you just click a menu item. not sure the spec requires a substantial enough ceremony. for some use cases (like a TV), the developer might not want any complexity.

jyasskin: I believe Chrome's current implementation shows an overlay on the screen all the time while you're sharing, but discussions about what is sufficient. not sure what needs to be in the spec vs providing good examples and expecting the implementations to do it right.

wbaker: goal is to highlight the issues and to "get to yes". it could be done well, but it leaves a lot open to the first few implementers (which might not be very many).

pes: in the past, sometimes WGs have asked what's the solution to a problem that's raised. not an obligation for a reviewer to always find the solution.

pes: thanks wendell

### Ongoing reviews/issues

pes: I've just been following [TAG reviews](https://github.com/w3ctag/design-reviews/issues/) or other suggestions, and I've just been doing some of those individually and then bring them to PING. roughly 1-2 per week, but I'm not doing those in PING's name. if that's a problem, let me know.

hober: we (TAG) really appreciate it when experts help with design reviews, so keep doing it

wbaker: it might be helpful to share / show others how to do it so that more people are comfortable. helps to provide permission, structure and tone to others. in terms of getting wider participation, maybe find a way to use them for teaching.

pes: could point people to issues after they're filed, or do a little explainer of what I'm looking for.

wbaker: any format is useful.

christine: 1) a Working Group asks for a privacy review, or asking W3C generally to do a Wide Review. or 2) observing a spec that's changing status or something is happening, and then proactively looking out for privacy issues.

pes: right, many are just early stage specs, not that we're being approached yet

jyasskin: i'll sometimes get comments inside Chrome, like, what does pete mean about this and what do I need to do? always advise trying to understand. it's good to distinguish when you're speaking for yourself and when PING as a whole has a view. makes sense that sometimes if an issue doesn't make sense, could talk with PING as a whole.

pes: for w3c process, no formal difference between individual objection or an objection from a group.

jy: I think you're right, but Director or others more likely to uphold objections when they represent a larger group. but hopefully we're not getting to that point very often.

wseltzer: yes, any objection from anyone is considered in reviewing transition requests. it's useful to know who is putting forward an objection, for example in assessing when Wide Review has been done (has PING actually reviewed a spec) and can be useful in addressing objections know who and what sort of concern is being raised. an individual's concern can be as important, but if an entire group stands behind it, that might signal something about the significance or breadth of community that could be affected.
{wseltzer notes later that knowing where the issue comes from can also help the team/WG know how to respond, e.g., should we ask PING for help to review the issue?}

pes: so I'll continue to file issues, noting when I'm filing them as individual, and keep PING in the loop

pes: font enumeration and fingerprinting, good call with CSS about taking it on as an action item for the next level/publication of the spec. yay! looks like the group is converging on offline enumeration of fonts installed per browser/operating system and commonly side-loaded for linguistic needs. users should also be able to opt in additional fonts. and then other fonts can be loaded as web fonts. sounds like an enormous improvement/mitigation of the fingerprinting risk. a lothttps://github.com/w3cping/tracking-issues/issues of measurement has identified font enumeration as the most distinguishing characteristic.

pes: payment handler api. not clear what kind of storage privilege that embedded party should have. agreement sounds like installing a payment handler will cause a user prompt about whether they should be accessible from other sites. outcome sounds very positive.
https://github.com/w3cping/tracking-issues/issues

npd: should we use the [privacy tracker repository](https://github.com/w3cping/tracking-issues/issues) to collect issues we raise? I know there are past issues I've not included there. will try to catch up on those.

kleber: I thought I heard a different result from the payment handler discussion.

pes: how payment handler handles storage apis, and, separate, how a payment handler is going to try to collect information to detect fraud. separate conversations.

npdoty: Web Share is a tech for sharing a url/page with another application, or with an installed Web App
... Web share API - https://www.w3.org/TR/2019/WD-web-share-20191217/

### Next call

January 16 for next call? (i.e. skip the 2 January call?)

(regrets from npdoty for January 16, but can send updates on email)

happy new year!

### Privacy community group (update)

wseltzer: had hoped to have an update to share by now, but still in legal review. hope to have feedback early in the new year.

