# Privacy Interest Group meeting - 6 February 2020


## Attendees 

* Peter Snyder (co-chair, Brave)
* Tara Whalen (co-chair, Google)
* Nick Doty (UC Berkeley)
* Chris Wilson (Google)
* Pranjal Jumde (Brave)
* Joshue O Connor (W3C) 
* Kris Chapman (Salesforce)
* Erik Anderson (Microsoft)
* Paul Jensen (Google)
* Zach Edwards
* Shivan Sahib 
* Michael Kleber (Google)
* Jason Dorweiler (DuckDuckGo)
* Konrad Dzwinel (DuckDuckGo)
* Dave Harbage (DuckDuckGo)
* Melanie Richards (Microsoft)
* David Benjamin (Google)
* Theresa O'Connor (Apple)
* Irene Knapp (unaffiliated)
* Terri Oda (Intel)
* Jeffrey Yasskin (Google)
* David Senecal (Akamai)

apologies: Christine Runnegar

## Agenda and Minutes:

Scribe: Erik Anderson

### 1. Past privacy reviews 

Pete Snyder: past privacy reviews to discuss.

Nick Doty: recent updates: ongoing discussion about calibration of device sensors. Will talk about later.

Trace context privacy reviews back in Nov 2018. Trace context a standard set of headers for various software, both client side and server side to track problems across a multi-server system. They took into account our feedback and are trying to publish a recommendation. Following up to see how they handled our feedback; will send out to the list this week. Some things that could maybe be written better (though they were responding to the concerns we raised). Procedurally we should figure out how to do this faster and earlier and figure out how we follow up after a review.

Pete: going over the history of it, was it a matter of us expecting them to open issues and didn't, or issues got closed prematurely or unsatisfactorily?

Nick: they opened issues and tried to provide mitigations. It got written up in their privacy consideration section and it wasn't as consistent and the presentation could have been more helpful.

Pete: in the future, it sounds like part of the privacy review assignment should go beyond opening issues to also ensuring they are closed satisfactorily.

Nick: yeah, that's not the fun part of working on a new spec, but it would make the reviews make more of a difference in the end.

Pete: call for comments on Trace Context or other reviews, none raised in meeting

### 2. Privacy review process 

Pete: figuring out who does what review when and how we can get a diversity of opinions and do work sharing. Straw suggestion was to do a round-robin and with enough participants that would be enough, but we've found it's not been useful.

New suggestion is to have a sign-up sheet and have people opt-in. Seven people have signed up, here's a link to the sign-up sheet:
https://cryptpad.w3ctag.org/pad/#/2/pad/edit/XFYXN76vmE+W3BTD3M2pFE0s/

My suggestion is, for new privacy reviews, ask if anyone has particular expertise for a specific spec and wants to volunteer, otherwise we'll go round-robin via the membership in the list.

Questions or thoughts?

Tess: yes, that sounds great.

Pete: Seven is great, would be great to have more orgs in general represented. Please don't consider the list closed. You or someone in your org that can contribute expertise and time to reviews would be appreciated. 7 is a good number does seem sufficient to go forward, though.

Questions or opinions?

Josh O'Connor: glad to participate from an accessibilty perspective.

Pete: great, please add yourself to the list! Anyone who isn't confident to take one on entirely the first time out, I and others would be happy to tag-team for the first one or two times until you're more comfortable with the process. This is more a request to express willingness to participate than an expression of current capability.

Pete: other folks in your org who might want to do reviews but not on call, please circulate to other folks in your organizations. Will also go into the email so other folks can see it.

Kris Chapman: if you're willing to tag along to learn the process (I'm in that camp), do you want us to note that in the list?

Pete: yes, that would be great, please add yourself to the list and note what level of assistance you'd like.

Nick Doty: is there a mini mailing list or some way to mail all of these folks at once?

Pete: not currently, but everyone on this list I believe is on our Slack. I'll make sure we always discuss this on calls, and so I hope that's sufficient. If a mailing list would be useful/necessary at some point I would help spin that up; prefer to avoid new machinery right now. Is there anyone on the current list that is _not_ on the PING slack?

Josh: I'm not on Slack right now... would like a list.

Pete: sufficient for me to notify you 1:1 since others are on Slack?

Josh: yep!

Pete: reiterating, can adjust if Slack isn't working but let's start with that.

### 3. New privacy reviews

Identifiers for WebRTC’s Statistics API - https://www.w3.org/TR/2020/CR-webrtc-stats-20200114/

Pete: WebRTC stats folks would like a review by Feb. 24th (?). There's time enough before our next call to do a review.

There's an enormous amount of machinery in WebRTC API and there's additional specs that layer on top of it. This one allows folks using WebRTC to get info about connectivity, throughput, and other perf data like that. A lot of sensitive, finger-printy stuff in the specc. Unless someone else feels drawn to this, I'm familiar with the spec already and am willing to pick up the review. If others want to tag-team let Pete know.

Shivan: happy to look at it with you.

Pete: yes, let's coordinate and we'll try to have a review by the next call.

Pete: any other groups that anyone knows about that wants a review that didn't make it to normal channels?

Nick: first working draft of Media Capabilities. I don't know what that is. I don't think we've done a review. We don't always do a review on first working draft, but it's a good time to do reviews. Allows sites to pick the optimal encoding for the user. Exposes info about device decoding capabilities.

  https://www.w3.org/TR/2020/WD-media-capabilities-20200130/

Pete: yes, better to steer early on. Jeffrey: you're on the list next, can you pick this up?

Jeffrey Yasskin: sure, can do.

Nick: they published 4 at the same time, this one had particular privacy relevance. Not sure how all of the specs connect (e.g. PIP and others). We should check with them on which likely need privacy feedback.

### 4. Process for adding privacy considerations in WICG work
Pete: This got pushed off of our last call. Let's pick it up now.

Pete: Background: there's a large amount of working coming out of WICG. Since it's a CG, not a process for a horizontal review, no requirement for a review of any kind. For Blink authors, there's a Blink-side commitment to seeking TAG reviews for specs coming out of WICG. The question here is: should PING be involved here, doing reviews of only-in-WICG specs? I see some TAG members on the call. What is the best way forward to keep these privacy-preserving as well? Any thoughts in the room?

Pete: in particular, thoughts from folks in WICG would be particularly appreciated ass well as folks involved in TAG reviews.

Tess: I can speak to the TAG review side of things. There are different groups at W3C responsible for horizontal reviews. TAG is for architectural review. It's the case that Blink process requires TAG review for web-facing APIs. We get lots of requests for reviews from Blink engineers, many times for WICG things. It's typically not the WICG itself asking us to do the review. It's a bit of a fire hose. PING should talk to Blink, they are the folks that have requirements that require TAG review, so they would be a good place to involve you. PING could also look at the issues list the TAG has, and PING could separately file a PING review. And, of course, TAG invites participation in the design reviews repo from everyone; comments are always welcome from experts in different areas. If PING wants to be getting the same level of requests for reviews, then the fastest way is probably to ask Blink to include you directly as part of their process.

Pete: just for background, for folks who don't know the process... what is the usual window between request and review?

Tess: highly variable. Some reviews take a very long time, some happen relatively quickly. On the TAG side of things we're aware of it and are trying to improve our process as we go so that we can be more responsive. The TAG only has 10 people, which is a fixed number, unlike PING with an open-ended number of participants. There's a limited amount of review we can do in a given week. PING may be in a better position to give reviews in a timely manner.

Pete: I've been trying to follow the TAG issue as much as I can and tag issues and then bring it back to PING. I wonder if that's too slow, it can be 2-3 weeks-- too slow for the TAG side?

Tess: I doubt we'd consider it too slow, but I'm only one of the ten people, so I'm only speaking for myself.

Pete: Blink or WICG side folks thoughts? Appetite for PING members to get engaged on an extra category of reviews?

Chris Wilson: first and foremost, as far as Blink members being here, I manage technical program management of Blink process. We're the right people to talk to. Everything that Pete and Tess said about WICG process vs. the Blink process is true. TAG reviews get kicked off by Blink process. Not blocking until Intent to Ship. API owners look really cautiously at anything that hasn't done a full TAG review. But we also ask as part of Intent to Prototype which is an early stage behind a flag, API may not be complete; that's about attacking the problem but not having a full solution yet. Talking to TAG about how we can maybe have multiple stages; we don't need a full review when it's just a first idea. Looking at open issues on WICG incubations, some things are basically, "this is a bad idea"-level of thing and some of them are relatively detailed, "if you expose this in this way, it introduces some concerns". Maybe the right model for PING issues as well (multi-stage). Changing the process and notification, we already have a built-in announcement to TAG, we can add a PING notification to that, but need to have a process for follow up on issues. Getting notifications that "this is an idea someone is looking at" or "this is something Blink is going to ship" or "this is something more mature in WICG" is something that can be done...

Nick: I wonder if, as a starting point, we follow the TAG design reviews issue list I see 10 opened in the last month. That's a lot but not so big we can't look over them. Some triage process, like cookie store APIs, freezing UA string, etc., clearly will have privacy relevance and more worthwhile to spend time on. How HTML handles focus may have some privacy issues but probably less urgent for us. I wonder if we can look over the list and triage each week or month on which to focus on.

Pete: unless there's disagreement from anyone, flipping the switch immediately to build machinery would be great. Understanding how PING comments will be understood on the WICG and/or Blink side and how they will be taken would be good. Setting expectations would be valuable.

Nick: does it need to be different from other reviews? Have same questions for how other groups respond.

Pete: difference as I understand it is for specs in a WG all issues have to be closed to transition. WICG/early process and how early issues will be dealt with would be good.

Chris Wilson: treat as two different things. WICG process, the best you can do is say, "look at any PING issues when we transition to a WG" when we transition to a standards body. Anything in WICG is an incubation, subject to change any time. Explicitly not a consensus-driven spec, can have competing specs, competing CGs...

Chris Wilson: on the Blink side, today API owners make those decisions. API owners have to look at a long list of inputs. blink-dev discussions on Intent to Ships are an interactive conversation. PING should decide what they are looking for at that stage. I can't sign up for hard-blocking ship requirements, but I can say "this is how we will address these issues and come up with a response to them."

Nick Doty: min-bar would be good. I understand Chris's point; there's a transition from WICG to a more-established standards-body. Useful thing would be to make sure things don't get lost. If we open privacy issues in incubation with no formal process for what needds to be addressed, would be great if the privacy issues didn't disappear. Common understanding about how they'll be addressed, or notification to PING when things get moved so they don't get lost... incubation is definitely incubation, but let's not lose past discussions.

Chris Wilson: makes sense. We haven't transitioned anything without moving the entire repo across including issues.

Nick: great, just want to make sure that happens.

Pete: would be valuable to understand if an issue gets opened on a WICG spec, are Blink folks planning on responding through issue queue, or on blink-dev? Where does conversation typically happen? Want to interact accordingly.

Chris: should engage in the relevant WICG repo. Actual development happens there. Blink-dev is there for chatter about intents (transition points). Intent to Ship is the most active conversation for a feature. Mostly about going through checking boxes. If a box isn't clearly checked, there's a discussion. Shouldn't need to raise new issues then, they should already be in the repo.

Nick: discourse.wicg.io? Useful place for us to spend time? Anything happening there or it's open-ended and it will always go to github?

Chris: yeah, it's like a mailing list for WICG. Entry point for checking if there's enough backing to move to an incubation. As a WICG chair I won't bring it in unless it has some level of support from multiple orgs. If no one else is interested in it, there's not a lot of value to moving it into WICG. Conversation in Discourse typically ends when it moves to a repo.

Pete: we have item 8, ongoing privacy things. Re: WICG issues... should we let WICG authors know we will be creating issues on their spec and they can join us here? Would that be valuable?

Chris: point of WICG is to get broader eyes. Probably don't need explicit notification (not opposed either, though). Getting into WICG should hopefully mean people are looking at all of the horizontals. e.g. accessibility folks should raise concerns. As far as people joining a PING call, probably best to do one-offs instead of getting people from every incubation to join all of the calls all the time. Synchronous discussion can be valuable.

Pete: my takeaways are WICG will turn on the firehose toward PING as well. PING will grab whatever seems to need comments and issues raised. We'll try that for a while. Accurate?

Chris: yes. You and I have a discussion about how to make the conversations productive; let's continue to chat offline on that.

### 5. Privacy threat model
Jeffrey Yaskin: I'm currently blocked on Tom reviewing. He said he wants to rewrite the intro. I'm inclined to start checking in what I have, but would like to have someone else review first to make sure I'm not off the deep end. Someone looking at the PR in the repo would be great.

Nick Doty: I haven't checked in with Tom, but will be happy to help with that. Threat model document is great and I would be happy to be a second set of eyes. Have some support from Brave to do more privacy reviews work. Jeffrey-- I will follow-up offline with you on reviews that are blocking and will stay in the loop with you and Tom.

Jeffrey: great, thanks!

Pete: I know Tom still wants to be in the loop, please make sure you continue to involve him as a three-way process.

Nick: yep, exactly.

### 6. Font fingerprinting
Pete: long, ongoing issue on how to solve privacy harm on CSS fonts spec to do fingerprinting based on non-standard fonts installed on the system. A F2F meeting with me representing PING and CSS Fonts group-- rep from Google indicated no change will be made there until there's an internal Google proposal. Given this was an action item that PING wanted to solve, would like to talk about how to proceed-- does that seem satisfactory to the group or do we want to plan some other way forward?

Tess: I think I have a rosier memory of that conversation. I think the CSS WG made a lot of progress on this issue. (I'm in the CSSWG which is why I was in the conversation.) Broad agreement that there should be some ship requirement here and a need to do research on what minority community fonts should be listed as part of a ship requirement. Will take a bit of time. While we didn't get issue resolved/closed completely, where we ended up is a lot better than where we were before. A bunch of work to do to figure out what fonts belong on the list. Things take time and that's okay.

Pete: I'm open to the idea that my interpretation isn't shared. Comment was not confidence in PING and CSSWG and needing Blink to figure it out.

Tess: hopefully the minutes captured things, I'd recommend reviewing those.

Paul Jensen: I've been talking to font folks at Google. We've been putting metrics in to measure font usage. We're in investigation phase of this. If we can come to agreement on a list of system-installed fonts we want to expose, that would be great. Not sure if that's possible necessarily. If it's this hard for us to figure out the list, how do web developers know what they can use? Want to help web devs understand what fonts are good to use. We are continuing to work on it, but don't have a proposal yet.

Nick Doty: I wanted to make sure someone had an action item to do the research. Paul, you'll get back to the group at some point with more info?

Paul: ... I think so, it's ongoing research so I will report back when I figure something out. We're also talking to some OS people about what fonts come with different versions and also if we can have APIs to tell us this info so that we don't have to keep track of the list ourselves. And also so web devs can know what fonts they can assume might be there.

Pete: it's great you're doing that list and I'm thankful for it. I find it a little unsatisfactory that this is an IG-raised issue, but research is being done in private without a timeline. Can we set some sort of timeframe for it given it's a priority for the group to get sorted out.

Paul: I'm not sure at this point what collaboration would be helpful, I'll need to think about it a bit more.

Pete: that's a difficult endpoint for a collaborative and open process but also understand business concerns.

Michael Kleber: I'm a little confused by that last comment. What sort of PING involvement into research on fonts would you envision? What would be a more collaborative mode of work?

Pete: timeframe for research to set expectations. Another possibility would be to have PING have some capability. Another would be to have other companies/vendors do that work.

Michael: any offers from any other vendors to do any of that?

Pete: I've offered to build some of that machinery but haven't moved forward based on comment that Blink will block on their own research.

Michael: other sources of info would be valued as well.

Pete: there's still the procedural blockage.

Jeffrey: the Blink position is that, until there is research we are blocked, but not necessarily only from Blink. Blink is the only one we're aware of doing sufficient research, but if other research appears that gives an answer that could speed it up.

Pete: would be great to understand what sort of data would be complementary or supplementary, understand what Blink is doing and what other info would be helpful.

Paul: trying to differentiate between system-installed and user-installed fonts is difficult. "Included" OS fonts vs user fonts are hard to differentiate. Participation from OS vendors would be helpful there.

Pete: that's a great point.

Josh: there may be folks with disabilities that have fonts that are more of a distinguishing identifier. As an FYI, it's something to be aware of. System vs. user-installed fonts may be an important thing to mitigate fingerprinting of folks wiht disabilities.

Kris Chapman: I know there's ongoing research about some of this already publicly available.

Pete: if you have a pointer, please add to the minutes or send to me offline.

Kris: I will try to dig it up and add it to the minutes.

(npdoty: if someone understands the research action item, we could see if someone else wants to do it in parallel, and then compare notes.)
[pes: seconded]

### 7. Device orientation API
Nick: quick question-- Paul, you published a proposal in line with what I suggested which seems like a great plan. Accelerometer data-- researchers don't have detailed info, should we open issues on those specs in addition to device orientation?

Paul: I have been looking at accelerometer stuff a little bit and was going to propose something. Hard to find specs for accelerometers. Haven't finished developing the proposal.

Nick: great, I'll follow up with you.

### 8. New Web developments and privacy considerations
Moved to next call.
