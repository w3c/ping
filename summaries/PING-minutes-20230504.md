<<<<<<< HEAD
# Privacy Interest Group meeting (4 May 2023)
=======
# Privacy Interest Group meeting (3 May 2023)
>>>>>>> a935cc0362e8a62da37cf8c20716c5651bc28586

## Attendees (sign yourself in)

* Pete Snyder (Brave, PING co-chair)
* Christine Runnegar (PING co-chair)
* Philippe Le Hegaret (W3C, Team Contact)
* Michael McCool (Intel, Web of Things Working Group)
* Aram Zucker-Scharff (The Washington Post)
* Sam Weiler (W3C)
* Wendell Baker (Yahoo)
* Jeffrey Yasskin (Google Chrome)
* Kristine Moore (DigiCert)

Regrets: Nick Doty

Scribe: Pete, Aram

## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/) 

https://www.w3.org/Consortium/cepc/#expected-behavior includes treating each other with respect

Michal McCool: did you invite me for the WoT Profiles review or a general discussion?
[much discussion and uncertainty about whether WoT was going to be discussed on this call. There was a scheduling issue, WoT is not scheduled for discussion on this call]
[The [WoT profiles review](https://github.com/w3cping/privacy-request/issues/115) was discussed on [16 March](https://www.w3.org/Privacy/IG/summaries/PING-minutes-20230316).]

Christine: (introudctions and reminder of W3C Code of Conduct)

### 2. PING at TPAC

W3C TPAC 2023
  11–15 September, Seville, Spain & online
  https://www.w3.org/2023/09/TPAC/

 Do we plan to meet at TPAC 2023? Any joint meetings? Any overlap to avoid? Any preferences within the week?
 
Christine: We need to decide what PING wants to do at TPAC, and also possible intereactions with other grousp (e.g., PatCG)
Aram: Groups are interested in having meetings with PatCH at TPAC, inc PrivacyCG. PatCG just finsihed working through proposed PatCG charter
…: inc privacy issues on the charter.  Are people interested in commenting
Pete: (nods)
Aram: We're about ready to submit it, so it may go up for review anyway
PLH: you prob dont want to wait for TPAC
Aram: we'll send it out sooner, since we anticipate objections and additional work / revisions
…: If PING as a group is interested in interacting with PatCH, a slot in one or the others group would be good
Christine: Lets put the queue aside, since attendance is light
PLH: Community is interested in web identity, which i expect will come up at TPAC. THis seems probably of interest to PING.
Aram: Is this beyond FedCM?
PLH: This is part of FedCM. We hear a charater is coming, but haven't seen it yet
Pete: i will read PatWG charter proposal by Monday
Christine: would be good to have a PING meeting itself, for people who can travel in person.  Maybe a short meeting?
PLH: Sounds good. Internationalization does not have a meeting planned 
Pete: we should coordinate with folks writing privacy guidelines (TAG, PatCG, PING)


### 3. Charter discussion

 https://github.com/npdoty/privacywg-charter/blob/main/privacywg-charter.md
Christine: Nick shared the above, but he isnt able to be on the call.
…: PING's charter will expire in June, so we need to reflect on what makes sense in a new charter, both for this group but as a broader W3C mission
…: PING chairs have been discussing evolving PING into a PrivacyWG, that would also be responsible for spec work
…: Nick has a work in progress, but its not public yet
Wendel: center piece of PING is a reviews, maybe this isn't the best use of our time.
PLH: Someone needs to do horizontal review. Otherwise privacy will get lost in spec work. Reviews are beneficial
…: A WG would be useful for recommendartions, and we need specific suggestions proposals (Pete says yes)
…: A WG would tigger pattent policy, people would have to make patent comitmnets.  If that soudns like a problem, lets keep the IG
Pete: There are concrete proposals like GPC. There are a limited pool of people interested in doing privacy work and spreading them across too many groups can create overhead. The substintive change last time I looked at it was to jetisin the Threat Model as a formal deliverable and instead make it a as a guidence useful as an intermediate step for formal responsabilities like review and spec work. 
Aram: (question about clarifying minutes)
Christine: if we had a WG, we'd focus on proposals that'd be ready to go through the rec track. We'd also try and pull in some privacy-spec authors to help with reviews.
…: its challenging to have lots of privacy people in the W3C, who mostly focus on authoring and not reviewing. We would like to have more people take turns doing reviews
Jeffrey: Talked to Nick recently, would be useful to have groups doing reviews to give input to guidance documents
Pete, Christine: both +1
Christine: we'll talk about this on going too
Jeffrey: re should incubations go into the charter, some groups have an open offer to be the WG for specific incubations, without promising that the incubation will actually finish.
Aram: PrivacyWG conversations have also been happening in PrivacyCG, Nick may be coordinating (Pete thinks so too)
Christine: Yes discussing with PrivacyCG chairs

### 4. Privacy review of Scalable Video Coding (SVC) Extension for WebRTC

  https://github.com/w3cping/privacy-request/issues/117
  
Pete: So this is a pretty minor addition to the existing webrtc spec gives the ability to show they support a different type of streaming. Addition in the single media capabilities object. Mostly the privacy concerns are fingerprinting issues. Web software can use this to learn about hardware capabilities so if you have unusual hardware it may leak significant data. 
Privacy issues opened are pretty minor: wording and alignment with existing privacy principles. 
Related conversations through deal with fingerprinting int he webrtc and media capability specs. These come from two issues: 

	- https://github.com/w3c/webrtc-stats/pull/732#issuecomment-1426475788
	- https://github.com/w3c/webrtc-stats/issues/730
  
These come from previous ping reviews and the idea is that these go through the same hardware checks so the user has to give access to at least one device to the page to prevent widespread fingerprinting. 

Christine: questions? ... I don't see any hands. I know we are a small group but the burdon of privacy reviews has been pretty heavily on pete's sholders, please other people set aside some time to do privacy reviews. You don't have to do it on your own, Others are very expert on this. 

----

Christine: Hello Kristine, welcome! 
Kristine: Hi, I'm from Digicert . 

----

### 5. Horizontal reviews of Charters

Charters in need of horizontal reviews:
  https://github.com/w3c/strategy/issues?q=is%3Aissue+is%3Aopen+label%3A%22Horizontal+review+requested%22+-label%3A%22Privacy+review+completed%22+
  
PLH: There are two events that trigger HR. When a WG is creating a specificatio (which PING currnetly handles), but HR is also triggered when a new group
…: wants to charter. So far this has been mostly done by W3C team (Sam + Wendy). This is done to limit the risk of groups created that have privacy-harming missions
…: The above link tracks charters that need HR. Other HR groups currently review these. THere are a bunch of charters that need review and are waiting for review
…: Should we keep charters waiting, or "time out" on waiting for privacy review
…: If ping is interested, what would the workflow look like
Pete: We should review, if on chairs calls if not on full calls
Aram: PING should review, some of these look like things we want to review (e.g., WebPayments, Decentralized Identifiers, etc)
…: I'd be happy to help review these, they're more accessible than reviewing specs
Sam: Heres an example of things that come up in reviews. For example, the media group wants to continue doing maintiance on EME
PLH: are there any charters people want to take a look at currently? WebPayment is a minor update, so would be surprising if it triggers a concern
…: Goal is not to say you need to solve prioblems before chartering, but to make concerns clear to team when group tries to move work along in the process.
…: This happened with Secure Payment, for example (charter said they need review from WebAppSec)
Pete: PLH, we'll get back to you by Monday
Aram: DID group looks like it'd be good for review too
Christine: seems to be consenssus that we need to review, even if Sam points out it could be painful
…: 1. PLH: could you let us know what chateres are for review, so we dont miss any
…: 2. lets have a standing item on PING calls for reviewing
PLH: List is available (see above)
Christine: Chairs can take a look on chairs call and suggest what in particular needs review


### AOB

Christine: please encourage folks to participate in PING and do privacy reviews! 🙏
