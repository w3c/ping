# Privacy Interest Group meeting - 27 June 2019

## Attendees

* Tom Lowenthal
* Pranjal
* Christine
* Sam
* Pete Snyder
* Nick Doty
* Wendy
* Jason
* Brent
* Mike


## Minutes

### Administrivia

* For today, queuing in Cryptpad.  Add name to the list below.

### Background / recap from last mtg

Pete: 1) green/yellow/red scores for horz. areas.  2) involved earlier instead of last moment. 3) coordinating, e.g. a buddy system

Jason: how do we make PING be more effective and PING's findings actionable.  WoT came to us late in their cycle; we had some fundamental issues with their approach, and the converation felt, to me, pro forma.  This is more about the process than WoT or us.  I want to make sure the work we do here has impact and, if people choose not to follow our suggestions, how do we signify that?  

Nick: how to use time on calls.  What makes a more effective phone call.  Some calls have been useful intro & discussion and some we've gotten bogged down and not gotten to other topics.  

Christine: both Pete and Nick suggesting we shouldn't do reviews on calls.
	[npdoty: actually, I'm fine with doing reviews on calls, but it's not always the most productive, or needs limits.]

### Green/yellow/red

Christine: I think it's a good idea.  For Wendy & Sam: if PING thought this was a good idea, what steps would we need to take in process to make this happen?

Wendy: ranges of "we could do it now" and offer a tracker on the PING side, attached to issues on the groups' docs.  Groups are already, by process, supposed to consider open issues at transition. That would not require a process change.  If we wanted to require that that be shown to a larger body (e.g. to the AC when they're asked to approve a PR-->Rec transition) - some of those might require a formal addition to the process.  To get started, PING could issue red/yellow/green and call it to the WGs' attention, then director's if the note of caution is ignored.

Jason: slight difference in my vision v. what's being discussed.  I'm proposing having a table at top of each spec with a line for each horz group.  "Above the fold" on the spec - easy to see.  Important to have that visibility - makes it abundantly clear to AC if horz review has occured.  Also lets groups say publicly that a spec didn't meet our bar (e.g. has weak mitigations) this is powerful.  

Pete: 1/10 or 5* is a lot of machinery; we're really more about yes/no.  More important to be earlier, not more graularity.

Tom: I like traffic light or four states - very actionable.  Powerful for both standards devs and implementers.  A way of closing the loop between wider community that the horz review groups represent and the spec authors.  Could also enable implementers to draw some hard lines.  This is good for devs.  I like using issue tracking; makes things actionable for implementers.  If initial review is "no", here are three problems, need to solve them before we're happy.  textbook case for issues.  having people come for (late) rubber stamping sets everyone up for failure.  and the context as a telecon as the first point of contact also sets people up for failure.  effective procedure for reviews should be along the lines of the WG opens issue on PING repo requesting review; some people assign themselves; comments in that issue.  @@ 

Nick: i like tom's issues idea.  good work mode. lends itself to earlier reviews.  I like the top-of-doc "this doc has issues" doc.   concern re: traffic light proposal is that i'm not sure how we'll make that decision - that's a new set of group decisions, and I'm not sure how we'd make those. [Sam: +1]  We might have a rules of "this is sever enough for yellow v. red".  that requires a lot from our side.  might be easier to decide on indiv issues than decide on red/yellow/green, and if an individual opens an issue and the resolution seems flatly unacceptable, we could have Formal Objections, as in the current Process.
	[Tom: (not aloud) seems like these are decisions that we _should_ be making. So let's work out how to do it. Feels like consensus is a pretty good method for making those decisions.]
	[npd: I think we could do that, and I agree consensus is a good model, but just it would take a lot of time, a new process with shared criteria, need many people very regularly involved.]
  [Tom: IMO we only need _enough_ involved people not to burn folks out.]

Pete: i dislike the levels for diff stds; more machinery for us, more arguments we need to have.  maybe it's more of "these things are strong 'no' for the web platform.  the further we get from that @@

Sam: WGs would like us using consistent interfaces - need to learn from accessability & i18n group processes, and other horizontal groups
	[npd: we did invite the i18n group to show us their process at one point, it involved Tracker issues that appear both in individual WGs and were followed by the i18n group to be checked on their status]

Jason: [scribe: no, no, put them back!]  I'm fine with "approved", "not approved", and "not yet reviewed".  as long as consensus on what they mean, fewer states is better.
	[npd: issues resolved, issues not resolved, not yet reviewed]
  [Tom: 👆🏻]
  [Brent: +1]
  
Wendy: in terms of process, changes to a doc template would likely need Process update or at least buy-in from the groups or director (e.g. for above the fold).  issue tracking we can do on our own.  this intersects with conversations re how to make other things (e.g. implementation status) more visible - annotations.  might be at a feature level.  if ping is able to provide granular review, that could be helpful

christine: maybe as a group, we trial the three-level approach and we, as a group, make sure we can do that.  figure out among ourselves, what the line is.  if we can do that well and demonstrate and track it, then we have a good way of going to other horz groups and THEN get it added to process/docs.  That's not an overnight process. 

	[npd: +1]

Sam: that addresses the "can we do the labels"; it doesn't address the queuing/how to request.

Pete: if we're not going to be blocking... annotation doesn't make things improve.
	[npd: -1, I think the traditional model of raising issues does help, even if it doesn't give you a veto on the ongoing process.]
  [pes: stop lights / 4-scale good bad / etc doesn't seem related to the above goal / strategy]
  	[npd: maybe I'm not following, could chat more on Slack]
    [wseltzer: a red light could be a blocking issue]
    [pes: I may be the one confused here :) does the current suggestion just scrape down to "add a light indicator to whether the standard has a PING opened issue related"? My reaction is that any feedback along the lines of "PING weakly objects" will have no benefit / outcome, so any statment more granular than proceed / we-will-object is not useful]

Mike: this discussion was triggered by WoT, and things like the mandatory ID need to be dealt with.  what's happening with that?  

Christine: as a group, put fwd "here's what needs to be done".  i looked for a volunteer to pull that together; still need it.  Putting that aside to continue on the meta-discussion.

Tom: ridiculous/controversial suggestion: lots of ideas of what process could look like.  maybe we should try writing it down and then everyone react to that proposal.  

Christine: you're right; writing this down is a good idea.  by trying to keep this in discrete discussions, I have have taken us off-track.  We need to be there earlier in the process.  I like the idea of telling WGs to create an issue for us.  @@  Tom, would you draft it?

Tom: yes.

Christine: more generally, need to make sure what we say is actionable and, when need be, is blocking.  that's partly a bigger conversation.

Sam: We're making some progess on "actionable" feedback.  I filed an issue on the payment request API after the PING call, and that got traction.  And Pete gave High Res Time (WebPerf) some very actionable feedback - they didn't like it - but it's currently blocking them.
	[pes: i'd add Client-Hints (the w3c chunk), and current fonts biz]

Nick: are we using a consistent label?  
  [Tom: let's just pick an issue label 🤷🏻‍♂️]
  [Brent: yes]

Wendy: we mean to have a soln to this; goal of overal horz review process.

Tom: we can solve by, when we file issues in other WG, ALSO file issue in ping issue tracker. 
	[npd: right, that was roughly what i18n had in place]

Pete: too few people opening issues.  better to open more issues, not more machinery to track.  
[wseltzer: +1!]

Christine: challenge is small group.  If we're successful getting WGs to ask for review, wondering if we'll have the people to do it.

Tom: only one way to find out.

Pete: if they're early enough to be useful, I'll do more.

Jason: the call to the AC reps to send people to ping - we're discussing a fundamental change in how PING works.  Need to tell them that and tell them that their participation is necessary, and changes are premised on them following through.  we need to say that we're restructiong to be more impactful.
	[npd: +1 to doing both at the same time. I'm scared of saying, "we will review all specs for privacy" when it's just a handful of us, but if we make it clear that we expect and require other members, that's more plausible.]
	[Brent: Is there a process for recruiting?]
  [pes: honest, there have been zero cases where we haven't been able to review things b/c of lack of membership]
  [npd: I recall many, many cases where we haven't reviewed because of lack of membership. I also recall burning myself out trying to review many specs alone.]
  [pes: that ~might~ *def* predates me.  Which specs went un-reviewed? (not calling out, just saying that those would be terrific examples to present people when asking for more PING members)]
  
  
Christine: +1
Christine: would it be useful to have webinars to educate? 1 on threat models, 

Tom: better to have documents than live chats, because they aren't time-specific. Makes sense to have live Q&A sessions where spec authors can ask about those docs. Not a fan of the term 🙅🏻‍♂️"webinar"🙅🏻‍♀️

Jason: more documents to be written, more like anti-patterns than questionnaire. 'what should i not do to get slowed down later'. could antipatterns be more than a blog post, a continually updated Note? a webinar/presentation could be useful for some people who learn that way, but generally want less ephemerality.

### Next steps

Tom to write up document on process.
Christine to look at GitHub repository/issues.
Jason to help Sam with charter and AC outreach.

pes: start at the level of WICG, when it's still not widely visible. there are chairs that track ongoing work. usually small specs focused on narrow use cases. could be much shorter reviews.

tom: document format work mode? github gist?
	markdown text documents in our github repo
 
Christine: call frequency?

Sam: how should we approach the next review request? should we not schedule for a call?
	[npd: unless they ask for a call to chat?]
  [Tom: 👆🏻]
  [pes: +1, default should be no call, calls if special case, if we think we need it]

tom: let's follow a model for actionable feedback.
	[pes: +1]


  [Tom: agree with npd's suggestion that calls are useful when people need to explain esoteric specs to us.]

Sam: calls were useful in increasing the number of people who looked briefly at something.

Christine: we could chat amongst ourselves about whether we want a call for each, case by case.
Sam: could we do a strictly time-limited overview on a call?
Christine: hearing different opinions, so suggest case-by-case basis for now.

Next call scheduled for **11 July**
	tom: could at least discuss process document at that point
  christine: outstanding: web of things, json-ld, data catalog, font enum.

[jnovak: apologies, have to drop]
[pes: same]

## Queue

Please type to be placed in queue [and remove yourself once you're done].




## other thoughts

npd: I think PR->Rec is mostly too late to make a big difference. (pes agrees)
pes: should i be deleting my comments from the queue?  sam: only if you're done with them or no longer want to raise them. (thanks!)
