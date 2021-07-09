# Privacy Interest Group meeting (1 July 2021)

## Attendees 

* Peter Snyder (PING Co-Chair, Brave Software)
* Christine Runnegar (Co-chair, invited expert)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C/MIT)
* Matthew Finkel (Tor)
* Kris Shrishak (invited expert)
* Konrad Dzwinel (DuckDuckGo)
* Newton K (Magnite)
* Theodore Olsauskas-Warren (Google)
* Sean Harrison (Google)
* Paul Jensen (Google)
* Nick Doty (invited expert)
* James Rosewell (51Degrees)
* Kelda Anderson (Microsoft)
* Garrett McGrath
* Wendell Baker (Verizon Media)
* Joey Salazar (invited expert)
* Theodore Olsauskas-Warren (Google)
* Eric Mwobobia (ARTICLE19) 


Please add your name above

Scribe: Sean Harrison

### 1. Privacy reviews 

## a. Media Stream Image Capture (requested)

Spec: https://w3c.github.io/mediacapture-image/

[Peter] anyone willing to take this? If not will go through the volunteer list.

## b. Performance Timeline, User Timing and Resource Timing

Specs:
https://w3c.github.io/performance-timeline/
https://w3c.github.io/user-timing/
https://w3c.github.io/resource-timing/

Reviewer: Konrad Dzwinel

[Konrad] Only had time to rereview the resource timing API, may want to follow up on the others. The issues from a year ago have not been addressed and the situation has not changed. Will go over the 3 issues originally reported. First, VPN can be detected using the next hop protocol/property, not tested but people agree this is plausible. This has come up in other specs, even only server side this can be done. This techniques existing already make this less of a concern overall. The other one is about leaking various information about user state, extracting DNS cache information and HSTS information using redirect start and end, looking at secure connection start being 0. The most concerning is what body size can tell you about the headers, cookies, etc. 3P cookies are going away, we will eventually have double key caching, and this will address all of these issues. We learned a few days ago that 3P cookies are around for 2 more years than previously thought. Should we rely on the 3P cookie deprecation and double keying or come up with [temporary stopgaps](https://github.com/w3c/resource-timing/issues/222#issuecomment-624479601, good ideas in the comments. Pausing reported values of header size. One more important thing is that ?? size will not be included.

[Nick] It looks like you opened these issues a year ago, why are we rereviewing this when the issues haven't been addressed, what prompted this.

[Peter] The group is trying to move back to recommendation status, triggering another horizontal review. Should we wait to do another review until existing issues addressed or just start now.

[Sam] They are going to CR again

[Peter] wanted to go to CR, didn't get there partially due to these issues, want to go to CR again.

[Nick] Shouldn't they have to address the issues before requesting again?

[Peter] Not necessarily how the process works.

[Sam] Each of these 3 issues threads have no discussion since last year. I think it would be worth saying in the issue that these are not resolved.

[Konrad] the issue is not closed so I don't consider them resolved

[Sam] Do you find your current comments sufficient

[Konrad] Yes, but it would be good to update issues with some of what is in the comments, but they have not been addressed.

[Sam] This was done before we are doing tracking labels as we are now, do we think all 3 issues need Needs resolution flags

[Konrad] Yes, the arguments in the ?? discussion. I don't think we should create another way to detect VPN/proxies, but if there are other equivalent methods then we might not be able to fix this. Maybe the resolution is to mention the risk in the priv/sec section, but I don't know if there is much else we can do.

[Peter] Same concerns on the other 2 issues?

[Konrad] No we either need to rely on double keying, or some mitigation

[Sam] I'm going to add needs resolution flags on all of them. VPN one just needs documentation

[Konrad] works for me

[Peter] I understand there wasn't enough time to re-review all of them, but could you go back and do that for a later meeting?

[Konrad] Happy to follow up on the others

[Sam] Will add to next agenda, and add comments to the issues

[Konrad] Maybe there is something that has changed that I missed but will follow up.

[Peter] Main issues are how does an origin indicate it would like to participate.

[Christine] These 3 requests came in through the new github privacy request method. Add a comment to look at the minuets of this meeting and that the other 2 will be followed up in the next

[Nick] The other 2 seem to be about high resolution timing. In each case priv/sec refer to other documents about high resolution timestamps. I just wonder since this is a re-review, if the security team has looked at this, spectre, etc. There are some mitigations in the high resolution time spec. But I don't know what the latest is there in regards to high resolution timers and spectre.

https://www.w3.org/TR/hr-time-2/ 

[Peter] What is the current status of the security reviews here

[Sam] I don't know if we have had someone new look at these security issues. There are some people at Google looking into high resolution timers.

https://github.com/w3c/resource-timing/issues/221
https://github.com/w3c/resource-timing/issues/222
https://github.com/w3c/resource-timing/issues/223

### 2. Candidate Recommendation snapshot requests

[Peter] Moving to publishing snapshots regularly, instead of the old model. New snapshot every 6-24 months, could greatly increase review volume. Does anyone here have concerns over the new approach, and doing reviews of each snapshot/candidate recommendation document. Another approach would be to have a different triage team, to determine if the changes in the snapshot are large enough to have a formal additional PING review. I'm curious how people would like to handle this. A pre-triage step by the chairs, or a lot more reviews in a lot of possibly non-substantive changes.

[Nick] Do we know what sort of detail we will get from the last snapshot, this will tell us if this is doable.

[Peter] Have to say what's changed, but is self reported. They are supposed to summarize changes for each snapshot.

[Nick] If this actually happens, we can see how useful these are. And evaluate by email if there is enough change, poke last reviewer, if enough has changed to warrant re-review

[Peter] Someone in the chairs can do a spot check if we need to look at it again before a full review happens

[Matthew] That sounds that would work. In theory it would be good to have the original reviewer look at it again, but with the 6-24 month timeline no guarantee the originally reviewer might not still be here.

[Peter] 2 years may be on the low side for the first set of snapshots

[Wendy] Groups should be encouraged to write informative snapshot changes. PING should keep pressing on requests for reviews that are lacking in context, or are missing significant updates, please flag it to be brought back to the group. Let's be helping them to help us better..

[Wendell] Reinforcing what was said before, continuous development is good. PING review doesn't need to be as much a gatekeeper so much as what of our previous feedback have you addressed.

[Peter] One other thing, my understanding is there isn't yet an expected timeline for snapshot announcement and going to the director. Some feedback would leave enough time for this, say a week or 2.

[Nick] I haven't followed the exact process steps for snapshots, seems similar to WhatWG process. But I think we should be thinking about how we want to be giving feedback to them in that way, even if there isn't a formal time.

[Peter] There is a formal review twice a year for certain specs, during those reviews there is a formal opportunity for PING and others to review. are you suggesting increasing that frequency or a more continuous channel.

[Nick] I don't know if this process is set up for all, 

[Peter] This is set up for Docs? and ??

[Wendy] We just concluded an update with WhatWG to cover more areas. Our thought is that the formal review happens mostly as a an emergency brake and much more effective review of their specs would be in their process which is an even more continuous process. Picking some time and going though their specs and filing comments there. At the time the spec comes over to W3C it would trigger the formal notice of there are some unresolved privacy issues. We very much hope it doesn't wait until that formal time, but earlier. Hopefully WhatWG is taking these into account into their discussions earlier. Does PING want to take its remit as looking at WhatWG development in more detail and what would that look like.

[Nick] that would be a longer conversation. But this could speed things up for HTML and DOM. A good starting point would be applying the privacy threat model and priv/sec questionnaires to current WhatWG specs. We haven't looked at HTML in awhile and should have someone do that, and particularly the DOM.

[Peter] An action item would be looking at WhatWG process and determining how we could collaborate earlier and more often. I can bring this up at the next meeting in 2 weeks. Where to go from here: The PING chairs and W3C staff will spot check group self reported changes during candidate snapshot and present those to PING and see if it warrants full re-review. It would be good to have some informal understanding of how long PING has to determine if a re-review is needed for the snapshot and object to it going forward.

[Matthew] QQ on snapshots, when will we start seeing snapshots

[Peter] Now

### 3. AOB

* Closeout/assignment of [older tracking issues](https://github.com/w3cping/tracking-issues/issues?q=is%3Aissue+is%3Aopen)

[Sam] As you all know we have a repo with some tooling to track issues in other repos that tracks things for privacy resolution. This tool also notices when the issue has been closed. We have not yet been assigning people to those issues. But would invite people to look at the [repo]. And assign yourself (don't have permission ask the chairs), if they have a closed question mark flagged, see if the resolution is sufficient, if not re-open the issue.

[Peter] The label of privacy means an issue to be discussed. Privacy needs resolution means the reviewer thinks that the issue can't go forward without resolution.

* Updates of the [Security and Privacy Questionnaire](https://w3ctag.github.io/security-questionnaire/) - James

[James] Relating to the security and privacy questionnaire. Which is partly the responsibility of the TAG, part of the premise of this group. I am very involved in the UK with regulators around privacy. There have been a lot of announcements in June. At a [CEPR Conference 17 june](https://www.digitalevents.uk/cepr_privacy_and_antitrust_17june/) - Simeon Thornton - Director, UK Competition and Markets Authority, said the distinction between 1P and 3P was harmful (also see note). This is starting to come out into the public domain and is calling into question our questionnaire. The ICO is looking into [anonymous identifiers](https://ico.org.uk/about-the-ico/news-and-events/news-and-blogs/2021/03/building-on-the-data-sharing-code-our-plans-for-updating-our-anonymisation-guidance/), which are in the questionnaire. I would like to see the document updated based on this input. The position of this document is not available to me, how these questions were decided on. Perhaps Sam/Wendy would reach out to governments and get their input on our questionnaire? If we don't solve this I think we will be wasting a lot of time. In the last year a bunch of sites are pushing more sign in, etc. In practice people’s privacy, in spite of our efforts here, is being eroded. People being asked to provide more identifiers as identifiers are removed. I think we need to be ahead of the game here.

Note: [Online platforms and digital advertising market study](https://www.gov.uk/cma-cases/online-platforms-and-digital-advertising-market-study) | [Appendix Z: assessment of potential data-related 
interventions in digital advertising markets](https://assets.publishing.service.gov.uk/media/5efc3f7ae90e075c5aeb9947/Appendix_Z_-_Data_related_interventions_in_digital_advertising_markets.pdf)

[Wendy] Thanks James, to the point of hearing from others, the UK gov is a W3C member, I've reached out to them, with an invitation if anyone from there would like to chat with us.

[James] Was that DCMS?

[Wendy] Listed as Her Majesty's Government

[Nick] Input from governments, I know we have gotten input from non-government W3C members, but it is welcome. Issues and emails would be great, but if they are only willing to talk on the phone that would be fine too. More input is great. I don't think one particular jurisdiction saying something should change fundamentally what the Web should do, but more input is good.

[Christine] It is my recollection that in the past we had data protection experts from the government participating in PING. Websites should not be asking for personal information when it is not needed, issue within concern of data protection authorities. 

[James] They are doing so to compensate for the lack of identifiers they were previously relying on and maybe would stop doing so if various pseudonymous identifiers were available.

[Sam] Invite James to provide link to the June 17th statement re: the distinction between 1p and 3p being harmful

[James] Not recorded but I can link to the event and get you in contact with this individual. But the statement was later published June 20? and I can link that.

* Participating in PING - Christine

[Christine] Want to remind everyone we have a PING member group, and to make sure that you individually and your company are a member of PING, please check the participant list to double check [here](https://www.w3.org/groups/ig/privacy/participants).

[Peter] Summarize action items from call. I will talk to WhatWG about collaborating more closely and how we will handle recommendation snapshots, and some smaller action items about talking to Her Majesty's Government.
