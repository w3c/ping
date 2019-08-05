Privacy Interest Group meeting - 1 August 2019

# Attendees

* Christine
* pes
* toml
* npdoty
* Terri
* mikeoneill
* wseltzer
* jnovak
* Tara
* Brad
* C Fennessy
* Shivan

Regrets: Brent, Sam

# Minutes

### 1. Draft PING process document - https://github.com/w3cping/administrivia/pull/20/files (Tom)

tl: last meeting we talked this through, more revisions still to come. goal: legible for someone outside of PING to see what they're supposed to do and why. brief introduction is PING's job on privacy, and horizontal review the most visible step.

tl: privacy review as a process. a github repo called privacy-reviews, and this will become the readme. open an issue in this repo based on the template (still to come, based on self-review questionnaire), tell people who don't know about your spec what they need to know. we (ping) will raise issues in your repository/preferred issue tracker, and keep track of those as a checkbox list in a comment on the issue in the privacy-reviews repo. hopefully we close all those issues satisfactorily and close the privacy-reviews issue.

tl: "oh no!" outcome, which we might call "architectural concerns". rather than raising individual issues, we describe the comprehensive revisions, rather than piecemeal.

tl: ideal privacy review would be no issues raised, because it's been discussed and resolved so early on in the process.

tl: specifications are in 1 of 4 states:

* reviewed and no outstanding issues
* reviewed and there are issues
* reviewed and there are architectural concerns
* not yet been reviewed

tl: should indicate the status at the top of the specification, in the document template for horizontal review status (ping, i18n, a11y, etc.). recommend that implementers avoid working on specifications that are likely to need material changes.

many thanks!

jnovak: agree w3c specs should have horizontal review at the top. 1, is there w3c consensus to change the spec template to include horizontal review status? 2, is there consensus that outstanding issues should prevent proceeding on recommendation track? we can either lead or follow the horizontal review process.

tl: idk. happy for ping to take a vanguard role. dsinger's comments in horizontal review seem to be leaning that way. jnovak: +1, will need to take it further at TPAC.

pes: for context, conversation about HR process https://github.com/w3c/w3process/issues/130
    
pes: at least one other i18n HR-er seems to be thinking in the same direction https://github.com/w3c/w3process/issues/130#issuecomment-509779995

wseltzer: re w3c process, both issues are architectural concerns are things to treat as Formal Objections (if not resolved), the document should not proceed without resolution. tl: yes, both should be considered Formal Objections, but especially architectural concerns wseltzer: maybe not every issue would raise to that level tl: sure, some issues are just constructive comments jnovak: if we default to blocking, that could discourage filing issues. yes, often PING issues should block, but not automatic. tl: [hard to hear] jnovak: it should be part of our process on filing issues to be clear lassey: like specify blocking/not-blocking on each christine: just needs to be clearly communicated

tl: will update this document, and make it part of the privacy-reviews repo.

nd: don't have to include all W3C process stuff - others manage, might change, consensus developed elsewhere - all issues have to be addressed under W3C process - a good time to decide if essential to raise as formal objection is the response to it (from the working group) - we need to figure out how we will communicate with WGs and what we want to do

jnovak: review template mentions in the sec/priv questionnaire that you should include a section, but the section should not be just answers to the questionnaire but rather a good section, as described in rfc 3552 / rfc 6973 (?) [for the record, npdoty did correctly guess the rfc number off the top of his head]

tl: issue template to start with, but would happily take improvements

christine: a good time to remind wg's that they should use that questionnaire

pes: explicitly talking with other horizontal review groups. hear something similar from someone in i18n. christine: as we speak to other groups, we can adapt accordingly. [scribe didn't catch that] tl: will make a batch of changes before further reviews

wseltzer: what would it take to make changes to the Status of the Document section, for other wgs? Process updates through the Process Community Group, which welcomes input. if some groups want to try it out experimentally, can talk to team contacts about adding it just below sotd christine: any wgs that might be amenable to the experiment? wseltzer: will ask in w3c team

a privacy-reviews repo in the w3cping organization? npd: +1, if it isn't working out, we can always change it later wseltzer +1 tjwhalen +1 (agree with npd, can adapt)

concern about groups not following the process when it's not clear, or people working outside the rules.

tl: mitigation is to be extremely clear about what we think the status or process is.

### 2. Updates on pending privacy issues - various draft specifications (Pete)

a central place for tracking issues https://github.com/w3cping/administrivia/blob/master/issues.md pes: a markdown table, but unpleasant to deal with?

tl: pretty easy to add assignees for privacy review requests, and then github project boards can show reviews and their current status tl: my suggestion is to make a comment on the privacy review request issue, with a list of the issues that the reviewer opens pes: but for existing issues..., an interim problem

tl: project board can have cards with issues in other repositories, "Tom the Project Manager!" will demonstrate, and can share the link.

### 3. Media Capture and Streams (GetUserMedia) privacy considerations (Pete) 

https://www.w3.org/TR/mediacapture-streams/

christine: returning to a topic we looked at a long time ago :)

pes: concern is that this is further along, so harder to get involved. years ago issues were raised and concrete changes were accepted, but maybe they haven't been made. concerning.

pes: creating a unique identifier to return to the website. fingerprinting vector prior to permissions request.

[scribe is hearing a lot of static from pes. welcome help scribing. better yeah.]

christine: wseltzer, advice on process? wseltzer: if we see issues that haven't been addressed, can file blocking objections even late in the process. as any procedural step, have to see who would back that from a stakeholder perspective, or if most people would ignore or prefer to ignore. wseltzer: if the group isn't being direct/accurate regarding response to issues raised, that could be raised directly with Director, etc. christine: would browser implementers have thoughts?

jnovak: issue 2 years ago wasn't followed up on, didn't have as many people tracking issues. if we come in now being more blocking, could decrease goodwill/acceptance. new reviews can operate under new regime, old reviews could be kind of grandfathered. can some of this be resolved just getting on a call with the rtc group? there is a fair process point, and a call could be more effective than github issues or emails. we can make sure the right people are there.

christine: +1. jnovak: will reach out.

tl: wg has the responsibility to address issues. there was an issue raised about identifiers early in the specification's life, this issue was simply not resolved. constructive dialog would be practical, but the responsibility is still on the wg/spec for making the fixes given the issues raised.

nd: re open question about whether we can make a change, is it practical - depends a lot on browser implementers - if they said they did mean to and we still can and won't break functionality, often easier to move on - check with implementers, you might have missed this - to see if interest and ability - might be useful to still discuss process, what happened

pes: thanks to npdoty about keeping the notes, otherwise we wouldn't even know about the process topic. can be strategically useful to distinguish between old and new process, but if there is going to be a discontinuity, should say so explicitly that there will be a different standard going forward.

jnovak: not suggesting can continue doing whatever, but if feature X has been out there for several years, pushing for an update out-of-band or out of normal process will be more costly in many ways, compared to taking a stronger line on new feature Y. a la 'PING will going forward track all features with significant concerns and pursue objections as necessary'

tl: not new that users care about privacy or that that's important for the web. but now we have more systematic representation of those concerns. there may be technical debt of existing deployed features with privacy issues, but easier to make changes the more thorough review process is catching now for not-yet-deployed features.

jnovak: +1 for technical debt in describing decisions and how they'll be addressed.

christine: can close conversation for now, with jnovak taking the action to identify best way to continue chat with webrtc group. jnovak: ack. pes: will write up @@@ as well.

### 4. AOB

Introductions of new folks:

* Brad Lassey, from Chrome's anti-tracking team
* Caitlin Fennessy, IAPP and formerly Department of Commerce

jnovak: Lukasz and I are drafting a new blog post on updates to the security/privacy questionnaire, and add the privacy review process as part of that

August 15th next call

Other Thoughts

Part of the review process could be what features need to have a Permission. If GUM insists on a device id then user should have to agree before browser executed it
