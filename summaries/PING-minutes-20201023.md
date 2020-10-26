# Special Privacy Interest Group meeting for TPAC (23 October 2020)

### Attendees (sign yourself in)

* Peter Snyder (PING Co-Chair)
* Sam Weiler (W3C/MIT)
* Christine Runnegar (Co-chair) 
* Philippe Le Hegaret (W3C)
* Jeff Jaffe (W3C)
* Sean Harrison (Google)
* Shaun Gilmore
* Kris Shrishak
* Karima Boudaoud (Université Nice Côte d'Azur)
* David Waite (PING Identity)
* Wendy Seltzer (W3C) 
* Mark X
* Tomoaki Mizushima
* James Rosewell (51Degrees)
* Dave Harbage (DuckDuckGo)
* Konrad Dzwinel (DuckDuckGo)
* Joey Salazar

### How to do a privacy review

Scribe: Sam

[Slides](https://github.com/w3c/ping/blob/master/assets/Privacy%20Reviews%20in%20PING.pdf)

#### What are privacy reviews

Pete: Part of W3C horizontal review.  When spec moves between levels, groups review.  Goal to identify issues unintentionally introduced by authors. 3 other horizontal areas (see slides)

Sam: There are also security reviews

Pete: but no more Web Security IG

PLH: There are also TAG reviews

Pete: reviews done when people want to move to Rec, or in special cases. They tend to come very late in the process, after much work has been done.  Bad because it invites conflict, reduces the solution space we can explore.  Much conversation re: how process can be improved.

When WG wants to move spec to Rec, they request review.  We discuss in PING and have a list of people to do reviews.  We have a list of reviewers; unless someone has particular expertise, usually go through list.  Reviewer does review, reports back to PING; chance for IG to improve review.  Results in Github - in WG's repo.  Those are reflected in a mirroring repo.  PING will work with WG to address issues.  If no way to resolve issues, formal objections can be filed.  ultimately up to the Director to adjudicate.

Christine: Pete has been talking re: process of horizontal and privacy reviews.  Pete will say, but good to say multiple times ... Privacy IG was created with goal of improving privacy on the Web.  One of the ways we do that is with reviews.  Try to make sure new, updated, and existing standards have better privacy design.  Looking for things that are privacy vulnerabilities and increased fingerprinting surface.

#### Goals

Pete: In scope: 

* new harms from new functionality.  e.g. allows identification, reidentification, or tracking.

* note existing harms in current spec.  Not just deltas; look at whole spec

* want to make "private by default".  default path needs to be privacy preserving

Christine: relaying Kris: were there FOs in the past?  Resolution?

Pete: HR time.  Director did not share concern.

PLH: No, director decided to keep issue open; decided there was no solution at the time.  Let them move to rec, but with open issue; expect issue to come back.

Pete: Sorry.  Director did not stop the move to rec.

Jeff: FO on Dev and Sensors is about privacy. But did not come from PING.

Pete: I think that one is still live.  Goal is to get the spec fixed without...

Christine: relaying James: are harms defined?

Pete: enumerated, but not exhaustive.  Certainly, things come up that we hadn't seen those before

James: where is that?  in security and privacy doc?

Pete: clarify?

James: where is enumerated list?  In charter?  In S&P doc?

Pete: questionnaire.  

James: that's the list you mean?  Things seems scattered over ethical web principles, etc.  If it's just there, great.

Christine: That’s not the only place.  Also find guidance in reviews done over time; things might not have been incorporated into the questionnaire as yet.  There is also the PING Group Note on Mitigating Browser Fingerprinting.  And IETF RFC6972 Privacy considerations for Internet protocols, and the W3C ethical design principles. Need to assess potential privacy harms in a specification on a case by case basis.

James: no exhaustive; also in other reviews; also IETF docs.

Jeff: slow down (to speaker)

Pete: Not in scope:

* finding alternative privacy-preserving way to fix issue.  May not be domain experts.  Not our responsibility to provide new version of their spec.

Christine: Joey reminds us that privacy threat model doc is in progress.

Pete: 

* we don't prove that harm will be exploited.  not a research body itself.

* don't make functionality v. privacy tradeoffs.  We enumerate concerns and push for them to be addressed, not to make the tradeoff.

* answer "what is privacy"

Jeff: I agree re: PING not making tradeoffs, but if there are things like HR time, where there is a functionality v. privacy tradeoff, I'm sure director would appreciate PING's perspective.

scribe= jeff

Pete: PING will have thoughts on these things, but PING would not close the issue on that point.

Christine: On the philosophical point (value/necessity of privacy) I've found that rather than policy or legal concepts of privacy, it’s more helpful in tech standards work to ask questions that are more about the (mechanics) of the specification such as, "does it create a globally unique ID"

Pete: PING is not responsible to write alternative spec text

Pete: Privacy reviews should relate only to privacy

Sam: A reviewer can comment on anything; but it does not make it a PING issue

Pete: Things that are in the middle - PING wants to engage but not always possible.

Pete: Could work with WG on alternatives, provide research demonstrating the problem, connect WG to privacy folks who can help.

Pete: Privacy review does not fail if these are not done

Pete: We should focus on collaboration - makes life pleasant; have joint goal to improve the web; keep long term impacts in mind.

#### Conducting privacy reviews

Subtopic: Before the review

Pete: PING gets a request over email, find reviewer with expertise, create an issue, communicate a timeline.

Subtopic: The review

Pete: Reviewer understands the goals, functionality - asks around, reads the spec explainers

Pete: Reviewer looks for things.  Possible harms.  New state for user profile (which would become a long-term identifier)?  New implicit state (aka fingerprinting)?  Accidental or unneeded information disclosure?  Geolocation (e.g.).

Pete: Questions to ask: is it necessary?  Can we reduce the privacy harm?  How are "harms" constrained?  Make sure user is centered.  What is the default path when privacy may or may not be an issue?  What fixes are required by correct implementation?

Pete: Guiding questions: Does the default spec behavior harm privacy?  Does it exacerbate existing harms?  Is the user always centered?  (e.g. is it user privacy v developer priority)  

Subtopic: Completing review

Pete: Discuss at PING call; file issues (which are mirrored to PING); notify WG

scribe=Sam

Pete: we schedule review for a call; let others weigh in.  File issues in WG issue; flag issues with privacy-tracker or privacy-needs-resolution. These reviews can be unpleasant, but important to get them right.  We can show a growing list of improvements that have come from these.  That, by itself, should incentivize us.  These can turn combative, which is understandable, WGs have done much work.  Sometimes more unpleasant, name-calling.  Not acceptable.  Doing these reviews requires understanding web platform; necessary but not sufficient.  PING combines some people who have deep Web platform knowledge and deep privacy knowledge.

#### Conclusions

Pete: to make process smoother: with a WG, where you might be alone v. 30-40 people, please pull in someone else from PING.  Co-chairs, others.  Disagreement inevitable.  Abusiveness not acceptable.  That's not a cost of doing business.  Let me or W3C staff know.  ABD - Always be depersonalizing.  Keep the focus on the tech, not the people.  Even if you're saying "here's what I'm worried about", appreciate the work that went into the spec.  Escalate not just abusive behavior.  Focus on the long-term health of the Web.  

Christine: We're not going to tolerable abusive behavior.  Feel free to contact the Ombudsnab or chairs.

Jeff: thank you.  Appreciate PING and PING leadership for all you've done for Web privacy.  I remember pre-PING days, and Privacy was barely on the table.  PING has done a tremendous job of raising privacy; timely.  You've identified challenges of doing this.  You've been great.  I also sense that lots of the debates we've had about privacy over last few years have been about gratuitous violations of privacy, e.g. getting more info than they need.  They didn't realize it was a privacy violation.  They've done a lot of work.  They wish they had known earlier.  Very heated debates, unacceptable abusive behavior.  My perception is that PING will soon move into a more challenging arena, privacy v. function.  I think you saw some of that with HR time.  there are things at stakeholders want to do and they don't know how to do that w/o some impact on privacy.  We'll all have to figure out how to do that better.  TAG has been talking about this.  We have to realize that things will get challenging because external world will be challenging.

James Rosewell: thank you for presentation and keeping to a level I could follow 100%.  re: use of language: very combative language e.g. "guns", "threat".  I wonder if taking that language away might help.  Jeff said "privacy violation" - you have to have a rule.  Laws change by jurisdiction.  We touch on policy when we state "improve the web" - lots of docs re: improving policy are high level and can be interpreted in different ways.  Privacy is now front and center in business policy, features, differentiation and regulation - US congress, other jurisdictions.  Last PING meeting, we talked about need to define that policy.  Not in PING charter at the moment, but would be helpful.  Proposed a session next week: [Privacy baseline](https://www.w3.org/2020/10/TPAC/breakout-schedule.html#privacy-https://twitter.com/OnlyInBOS/status/1320704230789947392) Not in golden hour.  Lot of interest that re: do-not-sell.  I think it's dangerous to create standard around specific laws. However, defining a base line will help avoid confusion and provide clarity in a way that the ethical web principles and other documents don't. 

Konrad: thanks Pete.  What happens after privacy reviews.  Are spec authors forced to address comments?  what are common outcomes?

Pete: people deeper in W3c process will know better.  Nothing with -needs-resolution should transition, right?

PLH: yes.  WGs will send transition req in GH; director looks at where spec received wide review.  Because our knowledge of privacy has evolved in last 3-4 years.  We're asking groups that did not get privacy review in last 2+ years to get one.  If we see -needs-resolution, we will block.  Sometimes it's just not clearing the flag.

Konrad: thank you.

Wendy: thank you Pete and everyone who has been participating.  Privacy review critical part of improving web platform.  Appreciate the work going into making this an effective process.  I hope you'll make slides available.

Jeff: which breakout, James?  

James: privacy baseline + definition session.  Good paper from Tess.  

Kris: I understand we only do review when requested?  We don't bring things in otherwise?

Pete: totally happens.

PLH: we have a lot of CGs, lot of proposals with early implementations.  Nice thing about PING - you're looking at things coming through incubation as well.  Nice that PING is not waiting, sometimes.

Sam: Want to highlight 2 things - we are doing security reviews by different people but with overlapping expertise - we also have different pre-requisite requirements - TAG wants literal answers to the questionnaire - PING expects narrative description of issues in the document (note: TAG usually does reviews earlier in the process)



