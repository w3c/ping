# Privacy Interest Group meeting - 03 October 2019


## Attendees (sign yourself in)

* Aaron Gustafson
* Caitlin Fennessy (cfennessy)
* Erik Anderson
* James Fishback
* Jatinder Mann
* Jeffrey Y
* Michael Kleber (kleber)
* Mike O'Neill
* Pete Snyder (pes)
* Pranjal
* Sam Weiler
* Scott Low (MSFT)
* Shivan
* Tanvi Vyas
* Tara Whalen
* Terri Oda
* Theresa O'Connor (hober)
* Tom Lowenthal (toml)
* Wendy Seltzer (wseltzer)
* npdoty


## Minutes:

### PCG discussion
- Tara: TPAC was fruitful, generated the below agenda.  Lets talk Privacy CG (PCG)
- Sam: There have been two volunteers for PCG chair, looking for third chair.  Apple suggested getting decision making process doc
- Tanvi: Do we need to revise the PCG proposal, do we need to act right away
- Sam: we can wait another week.  Things are moving, we're waiting for text on PCG doc
- Jatinder: no concern waiting another week


### Font fingerprinting etc.

- Tara: talked re: reducing FP surface
- Pete: background is going back to revisit past specs that enable passive FP.  [Font enum](https://github.com/w3c/csswg-drafts/issues/4055) was identified to be one of the worst.  Proposal to revise spec to include mandatory mitigations.  Thread has gotten to a point where it seems unproductive.  Moz, Apple, and Brave proposing mitigations.  Some people seem OK with mitigations generally but have specific concerns re: these specific proposals.  Blink folks say it's inappropriate to make progress now.  Frustrated.  How can we get progress?
- Nick: CSS discussion seems similar to discussions happening at TPAC - some interest in having a numeric model before we decrease surface.  I'm concerned about having a specific number (e.g. 20 bits) - I don't think a single number is feasible.  Most of this entropy is not independent.  One common agreement was to collect research and list FP surfaces by priority and size.  Pete or Tom got that started.  Might be useful to have that list.  Based on current reseach, font enum will be high on that list.  I wonder if that will help unblock us.  Multiple browsers might be interested in dynamic approach.  With large surface areas, if we have something that works, it will make dynamic approaches work better in other areas.
- Pete: proxying for Pranjal: any interest in Privacy Budget by other vendors? 
- Tess: interesting idea.  Might be worth pursuing in addition to active effort to reduce FP surface.  Still need to reduce FP surface.
- Jatinder: we're interested in understand Privacy Budget research.  Wondering how feasible it is.  If not, we need other mitigations.
- Jeffrey: keeping in mind that I'm not authoritative for Blink on this question.  The sense I get is that we don't want to take half-measures - don't want remove things that just move trackers to other forms of FP.  We want a plan  that says it's possible before we start breaking unctionality.  PB is such a plan, but details aren't out yet.  Hard to say wait for that.  I understnd frustration but there will be resistance until we have a plan.
- Kleber:  unfortunately, Brad isn't here - he owns this.  I agree that there's no reason that the forthcoming work on PB should prevent us from eliminating surfaces right now if we think they're being abused.  Jeffrey is right - the reason we're interested in measurement is that it's easy to push people to things you can't see.  At the same time, no harm in cutting down on existing surfaces so long as not hugely breaking.  PB should be about helping us make good tradeoffs.  But no need to stop us now.
- Pete: let's not dig into PB on this call.  If Blink isn't fundamentally opposed to working on mitigations now, it would help to have those voices in that issue.  How do we approach situation when marjority want to make an improvement and we have an outlier?
- Nick: goal state of removing FP completely... that's not a reaonable goal.  That's not how we describe goals in this space of security and privacy.  There are feasible mitigations.  Removing FP completely is not viable. Is there another statement of the goal that we could work towards?  
- Sam: couple of options:
  * it would be good for folks to weigh in on the issue if they think the font-fp reduction goal is worthwhile
  * if there is an exception, then we proceed, one party should not stop progress - "rough consensus"
- jyasskin: there are other folks that aren't blink and aren't vendors that are concerned about the proposal, and (AI) blink folks will discuss internally to get to a position
- wseltzer: distinction between specific product and the platform in general.  Different products in the platform will always make their own decisions, while standards are often modular. Think about the big picture but don't be paralyzed by lack of complete understanding.
- npdoty: action items?
  * jyasskin will lead discussion within blink 
  * PING keep working on priority list of fingerprinting surface areas
- pes: would be good to get process folks involved too.  Would also be good to choose the next candidate for tackling

### Next FP target

- sam: is there a doc thats shareable
- pes: you bet: https://docs.google.com/spreadsheets/d/1fymZUeVa5Ha6RzBtdZT-ZS0ax7sKFvSXuNkSSDs-gro/edit#gid=0 ([jyasskin] and the older https://docs.google.com/spreadsheets/d/1ZB1zINfGFcrcFzNg4eytRnBQN3nBoKHua2jhV_X6W80/edit#gid=0)
- npd: canvas and UA would be good candiates, UA already has a Client-Hints spec proposal
- pes: lets discuss over slack and make a decision on the next call
- sam: is canvas the best next option?
- npd: yea, canvas seems like a good next step
- sam: do we need a proposal around UA
- npd: Mike West's propsoal exists, it seems good and useful (would freeze UA, move it to client-hints)
- pes: i can reach out to vendors to discuss UA + Client-hints
- Tanvi and Tess: we'll check internally whats going on with CH + UA implementation plans
- scottlow: (from MS) we're also interested in following up
- kleber: UA-freeze + CH is distinct from fonts as a vector.  Privacy budget wants to measure and cap FP surface; impossible to measure use of UA as FP surface since its sent out universally.  Goal is not to remove informaiton, its to make it active instead of passive
- npd + kleber: (general agreement on the UA-CH idea)
- npdoty: allows for measurement, allows for browsers to take dynamic measures (a la Privacy Budget), allows for researchers to see what sites are using it -- it's a mitigation that works in lots of ways

### WoT
- pes: back and forth on horizontal review of Web of Things document. specifies privacy sensitive information, the group has responded that future documents may address that. concern that maybe PING should oppose until those future mechanisms are described. call tomorrow for more discussion. think the doc is not baked enough to move forward.
  * specs: https://www.w3.org/TR/wot-architecture/, https://www.w3.org/TR/wot-thing-description/

- kleber: re constructive engagement, what I heard pes say is that the current state is privacy harmful and not well-enough detailed to review. what would our goals be to next steps / ideal roadmap?
- weiler: one concrete example: a Thing Descriptor that includes a static, presumptively long-lived identifier, but there will be privacy protections coming in something in the future. if doing something potentially harmful now, need to ship the mitigation at the same time. also not sure a unique identifier is needed. telemetry as a use case, but anonymous telemetry options should be possible. should we hold off on recommending until the mitigation is ready?
- toml: re TPAC conversation, responses were that identifiers aren't as bad because of some factor, but those mitigating factors are not in the text of the specification.
- kleber: okay that turns into questions about next steps.  Should open issues on spec.
- weiler: WoT response has been "we're too far along".  PING did a blog post saying that privacy mitigations need to ship as part of the base spec; seems particularlly applicable here.  Is this still the position of the group.
- kleber: question is can PING bring others along.
- toml: yes, in their hearts they know its true
- Terri: only for other folks specs?
- toml: yes, exactly, if folks think it for everyone elses' specs but theirs, thats demonstrated belief that the principle is correct
- kleber: is WoT concerns _only_ a matter of timing?  Why not ship the protections later?
- toml: the spec document should be cohesive and understandavble to all; non-privacy folks may implement w/o concern for privacy if the mitigations are not included in spec.  The spec is incomplete on the privacy grounds, but not only the privact groups
- kleber: if the group plans on dealing with them in the future, its surprising that they're hesistant to address now
- jyasskin: if they're blocking issues, they should be raised individually too.  re publish recs before mitigations: groups should know what the mitigations are at least, but if the rec is ready before the mitigation, prob okay to ship (or mitigations are in a separate document)
- npdoty: maybe no need to focus on process question now; plenty of other concerns with the spec. we can raise the issues, and how to handle documents with lots of open issues is part of the W3C Process.
- weiler: another of the WoT WG's objections is this is just about pushing data, like HTML.  The doc format should be evaluated independent of the contents of contents.  But this seems to be insufficient to evaluate the standard, need full stack eval to completely understand the correctness / merits / privacy-implications of the standard
- kleber: big diff between "spec with harmful stuff currently, but feasible / understood mitigations" and "there are privacy incompatible goals in the spec"
- pes: next steps are to meet w/ group and let them know the above convo
- Sam: put links to the issues in these minutes, so people can +1 them:
  * https://github.com/w3cping/tracking-issues/issues/11

### AOB

#### Charter

- Nick: do we have a charter?
- Sam: yes
- Wendy: yes.  no objections to changes to charter.

#### Recap

- Sam: action items: weigh in on Font/CSS issue, +1 WoT issue, talk with teams re: Client Hints.  CG charter still in progress.

- pes: if Client Hints is in progress, we can find another new area for focus.

## Agenda:

1) Privacy Community Group: status, next steps

2) Reducing fingerprinting surface area of existing web platform
  
  * font fingerprinting & CSS GitHub issue: https://github.com/w3c/csswg-drafts/issues/4055
  
  * next target(s)?
  https://docs.google.com/spreadsheets/d/1fymZUeVa5Ha6RzBtdZT-ZS0ax7sKFvSXuNkSSDs-gro/edit#gid=0

3) Web of Things: possible PING formal response (as a group) to recommendation publication?

4) Any other business?

## Queue:



## other comments

npd: you can file issues even to larger topics like, "this is missing everything about X", especially if that's the gruop work mode.