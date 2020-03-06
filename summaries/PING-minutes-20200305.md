# Privacy Interest Group meeting - 5 March 2020

## Attendees (sign yourself in)

* Peter Snyder (co-chair, Brave)
* Tara Whalen (co-chair, Google)
* Christine Runnegar (co-chair)
* Pranjal Jumde (Brave)
* Kristen Chapman (Salesforce)
* Zach Edwards
* Martin Meyer (Akamai)
* Tom Lowenthal (Brave)
* Hannah Quay-de la Vallee (CDT)
* Scott Low (Microsoft)
* Michael Kleber (Google)
* Chris Wilson (Google)
* Paul Jensen (Google)
* Wendell Baker (Verizon Media)
* Jason Dorweiler (DuckDuckGo)
* Nick Doty (UC Berkeley)
* Caitlin Fennessy (IAPP)
* Wendy Seltzer (W3C)

apologies: Jeffrey Yasskin

## Agenda and Minutes:

### 1. Privacy reviews 

##### Current:

=> Requested - Personalization Semantics Explainer and  Module 1 - Adaptable Content 

(from the Personalization Taskforce of The Accessible Platform Architectures (APA) Working Group)

Links: 
* Explainer - https://www.w3.org/TR/personalization-semantics-1.0/
* Module 1 - https://www.w3.org/TR/personalization-semantics-content-1.0/
* Privacy and security self-review - https://github.com/w3c/personalization-semantics/issues/131
* Wiki - https://github.com/w3c/personalization-semantics/wiki/
* Getting started page - https://github.com/w3c/personalization-semantics/wiki/Getting-started-with-personalization-semantics
* Github repo - https://github.com/w3c/personalization-semantics/issues

=> Consider - TTML Profiles for Internet Media Subtitles and Captions 1.2 

(The Timed Text Working Group has sought a security review - https://lists.w3.org/Archives/Public/public-web-security/2020Feb/0002.html - for discussion, whether privacy review needed)

**pes**: Pranjal is able to take the personalization semantics explainer. Nick will take #2.

(npdoty: yes, I can look at this TTML IMSC review, although based on their security-related email, it may be brief.)

##### Previous: 

=> Identifiers for WebRTC’s Statistics API 

Link: https://www.w3.org/TR/2020/CR-webrtc-stats-20200114/

(Discussed on 20 February 2020 PING call)

**pes**: pes: Privacy review for WebRTC stats is ongoing. There's still not a decision here, but it's on the groups queue. There is some thinking that this could be wrapped into the telemetry/debugging mode that's being proposed in the Privacy CG, but that is still in early days. Overall, progress is going well and we are working with the group.

### 2. Font Fingerprinting

Follow-up from discussion on 20 February 2020

**pes**: This has bifurcated. One in the CSS WG on one approach and another cached-based approach on Slack. Given that progress has been fits and starts on this, I'm eager to encourage anyone working on this to continue doing so. I wanted to ask if there's anyone who is interested in participating here and to ask whether anyone has thoughts on how to unify these two approaches (and if that makes sense)

**pes**: It seems like we're at a place where UI would make sense to mock and share. Brave will mock something up next week. If anyone else has UX to share, it would be great to share this in either venue.

### 3. Audio / canvas / webgl Fingerprinting

**pes**: I think it makes sense to start conversations with other WGs similar to what we did with font fingerprinting. We could either continue conversations there or incubate solutions in Privacy CG, PING, or somewhere else. Wanted to ask
- If folks think this is a good idea 
- If folks are interested in participating here

**Christine**: We've had some experience with font enumeration and I think starting other conversations now is a good idea

**Nick**: We had an idea to come up with an ordered list sorted in terms of how much each web API contributes to fingerprinting. I know UA string was high, so we've made some progress there. I think it makes sense to put together a list and to start working on this.

**pes**: I recall Google had a list previously. Does this need to be updated?

**Nick**: Yes. We should make sure it's up to date

**Michael**: I was wondering how fingerprinting you're talking about relates to the Privacy Threat Model. I don't think we've locked on a Threat Model yet, so I want to understand how these two are related

**pes**: Adding to agenda for later.

**Wendell**: I think my question/comment is aligned with Michael's. As we go through this fingerprinting exercise, where are the limits that this group will take to stop investigating fingerprinting. What I'm thinking about now is DNS fingerprinting. This is technically outside of the web. And there are some theoretical discussions that DNS will be removed from the web. It'd be great for us to align on a limit.

**Nick**: One of the challenges we have is the fact that fingerprinting goes across the stack. Some might be HTTP-related which would go to IETF. I'm not familiar with the DNS work, but it'd be great if you could share some of this on the mailing list or Slack. Since fingerprinting is a cumulative privacy threat where data from multiple sources can be consilidated from multiple sources to enable tracking, the best thing to do would be to coordinate. We may realize that what we need to do to combat some of this is to take issues that were raised in the W3C to the relevant group (such as IETF)

**pes**: I want to echo what Nick said. 

**pes**: To summarize, it sounds like we ought to document the progress we're taking on fingerprinting. This might be the list Nick was surprising. Because the "big four" are categorically different based on how identifying they are, we should start these conversations with other relevant working groups.

**Wendell**: I'm good with that.

**pes**: Call for volunteers. Seeing no one on the queue, I'll open those issues. If anyone changes their mind, please feel free to let me know. 

**Michael**: One last question. My understanding from the font side of things is that the Privacy CG would be involved in these interactions for incubating solutions. Is that still the plan? 

**pes**: The way this was discussed in the last CG call was for PING to open the issues and to see if the relevant WG is interested in incubating solutions themselves. If the WG feels they need more support, then the Privacy CG could help incubate solutions.

**Nick**: Privacy CG would be where we talk about new functionality. It could be that new fingerprinting work requires incubation.

dnscookie.com
and 
https://svs.informatik.uni-hamburg.de/publications/2019/2019-08-13-Sy-preprint-Enhanced_Performance_and_Privacy_via_Resolver-Less_DNS.pdf

### 4. PING administrivia / Privacy review process

**pes**: Two items:

1. Should we do more formal tracking of privacy review machinery? (i.e. should GitHub be the ground truth for PING?)

**Christine**: I tend to agree with that with one addition. Not just having this information in the PING chair's heads and the minutes, but I think this is a good idea even though folks may need to learn GitHub.

**Nick**: I'll +1 on this. I think for a while we were using a wiki page. If we have a GitHub for tracking issues already, then it makes sense to have a place for tracking privacy reviews as well.

**sclow**: +1 (scribing)
**pranjal**: +1 (chat)

**Wendy**: W3C is creating more tooling around linking PING issues to WGs. GitHub is being used as the base for this, so having more of our work in GitHub will help ensure we're working better together.

2. How to understand the result of a privacy review

**pes**: I'd like to see if there are suggestions for changes to understand if what we're doing today isn't sufficient and whether there are opportunties to add more documentation
  
**Christine**: I don't want us to create more overhead. Now that we're setting up a space on GitHub, I think it would be useful to record there what PING consensus was. 
  
**Kris**: I was also going to vote for more process documentation. It'd be great to link to minutes to bring more clarity back to GitHub.
  
**pes**: The process we've been doing so far has been we discuss with the group and they open up issues. Unless there's some talk from folks that these issues have gone sideways, then those issues become the PING issues and are linked to PING. If there is disagreement between PING folks around the issues, how do we record this?
  
**pes**: I take as the default that we can document what I just said (that PING issues would be majority wins rather than agreement)
  
**Wendell**: I think it could be interesting for dissenting opinions to be captured similar to court cases. Then for legitmate differences, we've captured this and interested parties could see the history. 
  
**pes**: Where would these dissenting opinions live?
  
**Wendell**: I don't. I'm a little puzzled that the web is devolving to GitHub, but in a GitHub issue is fine. Something with a link that people can point to is fine.
  
**Nick**: I think it's fine to document those different points of view. If our job is to do horizontal review, I think it's useful to raise any opinions that folks have. Someone who thinks that something is a huge deal could still raise that issue as part of their review. Then other folks could chime in and state their agreement/disagreement. I don't think we need a uniformed opinion on everything
  
**Michael**: Another place we need to think about disagreeement is when we start engaging with the outside CG/WG. We raise an issue; people who are not inside PING say they believe that a mitigation should resemble a certain technique. But then there's disagreement around whether that mitigation is sufficient. 
  
**pes**: One way of interpreting this is that the authority rests with the folks who are running the reivew. Another way is to build consensus within PING. Second way feels more in the spirit of horizontal review. 
  
**Christine**: I think that's an interesting point. We should make sure that all of us collectively as PING pay attention to the discussions post-"Here's what PING thinks" to make sure it's consistent and to contribute other pieces as that discussion evolves. 
  
**Kris**: I was going to add that it would be helpful to note child issues that spin off of child issues. It's sometimes hard to navigate through the issues when we treat them all as being in the same plane.
  
**pes**: I share this cocern and think that it would be better to tie together the issue graph. For anyone opening issues, make sure you use links as much as appropriate
  
**pes**: To summarize (we can continue conversation on Slack or future calls), we should document publicly that the outputs of PING are privacy reviews. We should say these are not consensus driven, but rather majority opinion. Working Groups should then address these in a way that addresses the concerns or furthers better understanding and leads to better outcomes. Does this capture the room? If so, I'm happy to write this up.
  
**Christine**: I'd prefer that this is PING consensus rather than majority. Consensus is different in different contexts. When I think of PING context, I don't necessarily mean that every single person who is part of PING will have an opinion, but I think what consensus should mean is that the general view of PING is X and there are no objections. We might also have a situation where the general view of PING is X, but there are a few individuals who think Y. I think this is an important call out.
  
**Nick**: I'd agree with Christine on avoiding majority. I also had the opinion that we wouldn't have the interest group review every review. It might be interesting to say that this is an issue opened as part of a PING review, rather than saying that everyone in PING has had a chance to review.
  
**pes**: We can get more input on Slack. We need something more than "This is Brave's concern". We should say something related to PING rather than just one entity's opinion. 
  
**Michael**: I kind of thought the Threat Model was supposed to make something not someone's opinion, but rather something grounded in truth. Why isn't the Threat Model the key answer to your question?
  
**pes**: Even if something is written down in the Threat Model, there could still be differing opinions. 
  
**Chris**: The TAG has a similar thing where they list their guidance. They come across things they didn't think of that are new. I was the subject of a review where the TAG went back and edited their guidance. So input of that nature should change the threat model over time. 
  
**pes**: Point taken. None of this is to say we should not pursue a Threat Model. But what I'm trying to track is how we capture dissent.
  
**Christine**: I wanted to remind everyone that we put a lot of work into two documents. One is to update the self-review security and privacy questionaire. Another was the limiting browser fingerprinting. There will be cases where we just didn't think of something. It would be good to add to those documents and the Privacy Threat Model.
  
**Nick**: Michael is right that having that documentation is going to make it easier when we're raising issues or when we're discussing mitigations. As we keep those documents up to date, it will make this a more systematic process. 

### 5. Threat model (new approach?)

**pes**: I wanted to share my understanding which is the parties who are largely responsible is that Nick is going to help out more moving forwards. Jeffrey got us started and unfortunately couldn't be here today so I'm going to help with that. 

**Nick**: Michael, do you have anything you wanted to discuss about the contents of the threat model today?

**Michael**: No. I more meant that that I thought the threat model would be useful in helping distinguish one person's opinion from a general PING consensus position. If we can point to the threat model doc and say that it indicates that X should happen, we then have something more grounding about what should happen next.

### 6. New Web developments and privacy considerations 

**pes**: Call for topics.

**Wendell**: isLoggedIn concept. It seems fairly radical given the consensus of web stewards in the past is that the web does not have an identity layer. Question for this group is whether this is something we deal with here or if there is another venue to discuss that.

[Wendell] Love to understand more thoughts about isLoggedin from https://github.com/WebKit/explainers/tree/master/IsLoggedIn

**Christine**: My first question is whether someone could summarize this. I don't see anyone from WebKit on the call. Having some time to read it would be helpful.

**pes**: I'm fairly familiar. Since it's not in any WG and isn't formally proposed in Privacy CG, the proposal itself is probably premature for PING as a group to discuss. The proposers are eager for feedback, so I'd recommend you giving guidance (or putting together a subset of PING to help provide this guidance informally)

**Nick**: It looks like the suggestion was to send this to the Privacy CG as a proposal.

**Kris**: It's not really a privacy review, but I was curious to know if anyone has looked at what [Inrupt](https://inrupt.com/) is doing with SOLID out of MIT. It's interesting what they're trying to do. I'll link to the notes. 

https://solid.inrupt.com/

**pes**: Is the group looking for feedback? 

**Kris**: I talked to them and I know that we should come in to review and discuss. They're probably in process of joining the group. Just generally, what they're trying to do is very relevant. When you think about things like Identity on the web, this is a very interesting concept. For those who don't know what they're doing, it's just the idea of transferring data from company's databases to personal PODs (data repositories) where users have control over their own data.

**pes**: Privacy CG would be an interesting venue to discuss this further.

### 7. AOB

See 6. above


