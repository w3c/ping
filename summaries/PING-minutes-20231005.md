
# Privacy Interest Group meeting (5 October 2023)

## Attendees 

* Pete Snyder (Brave, PING Co-Chair)
* Nick Doty (CDT)
* Forest Doty (unaffiliated)
* Philippe Le Hegaret (W3C)
* Aram Zucker-Scharff (The Washington Post)
* Sam Weiler (W3C)
* Shubhie Panicker (Google Chrome)
* Jeffrey Yasskin (Google Chrome)
* Daniel Kahn Gillmor (ACLU)
* Eric Mwobobia
* Tess O'Connor (Apple)

Apologies: Christine Runnegar (PING co-chair)

Chair: Pete

Scribe: Aram

## Agenda

###  1. Introductions, Code of Ethics and Professional Conduct

https://www.w3.org/Consortium/cepc/

Pete: Anyone new?

dkg (Daniel Kahn GIllmor): New, from ACLU, haven't been super active, saying hello
Shubhie: Hi, I work on Google Chrome, new to this forum, I have an agenda item from a W3C workshop

### 2. Privacy review - Dubbing and Audio description Profiles of TTML2

https://github.com/w3cping/privacy-request/issues/122

Looking for a volunteer to review

Pete: Review request for this new spec. This is an additional functionality for text annotations for videos. 
- It would be great to have someone to take on that review. If someone is interested and new, I can co-review. 
- If not, I am also able to review. 

Aram: Hi, I'm open to doing a review. I'm hoping to use privacy review to help with training my internal team of privacy engineers. So this would be a good way to say "here's how to review these things". I've had trouble with privacy reviews in the past, and I want help watching for feedback on the review. Lots of different places feedback can happen. Often happens in the spec, and that feedback seems to be hard to surface in my tools. Would be good if there were organized checking that the larger group could help with. 

PLH: You're welcome to cc the chairs and myself on the github issue. Then it'll cross my radar.

Pete: We've been trying to list the issues in the review request issue, but have the discussion take place in the actual spec so it's as close to the document as possible.

Aram: that sounds like a good way to get help on this. 

"github notifications: I have a lot of them" -- everyone

### 3. Next steps on proposed WG charter

https://w3cping.github.io/administrivia/2023/charter.html

https://github.com/w3cping/administrivia/issues?q=label%3Acharter

Pete: Next steps on the charter. Nick? 

Nick: THe charter for this group is expiring and because we have some standardization work we are working on a working group charter that allows us to better take on standardization work. 
Here is the current draft - I've made responses to feedback. 
Potential deliverables make things clearer, they need incubation work before they come to us, but we are noting picking up GPC. PLH as our team contact. Scope is limited only to the stated deliverables and horizontal reviews for this. We'd need to re-charter for entirely new work. 
I think we're getting close here. Are there any remaining issues? 
One area where we need help - what groups should we coordinate with? 
If you have thoughts add them to the issue and then we'll incorperate. GFive feedback. 

Jeffrey: 
Have you talked to Tess about the GPC deliverables entry yet? 

Nick: scheduling issues, but we're meeting tomorrow. Update soon. 

Pete: Anyone else? 

### 4. Next steps regarding credentials, identity and age verification and privacy

Pete: Next steps regarding credentials etc...
Breakout sessions from TPAC. 
Open floor

Nick: Update here. The WICG has a [sub group working on identity credentials](https://github.com/WICG/identity-credential). Browser-side handling of a website asking for a credential of a certain property and getting it from a wallet. They met for the first time last night and described a pretty broad scope though not a lot of participation from all the browser vendors. 
TPAC discussion shows there is a susbstantial list of privacy and policy concerns that would be needed to be addressed for it to be acceptable. 
It cuts across a lot of wokring groups. FedCM. Also outside of this - IETF, etc.. 
Here we could work on baseline privacy concerns for any works in this space, author principles for review ascross all proposals 
Then it could be reviewed by all groups working on crednetials etc.. 
I have an outline draft - 

https://github.com/npdoty/identity-age-considerations/blob/main/credentials-age-considerations.md

An organized list of questions for the most part. Privacy questions that would come up but also beyond that free expression, accountability, accreditation.
I think there is enough interest for this to be a workitem either here or in a ad hoc team. 
I would suggest this doc as a starting point, tho perhaps not the only one. 
Do we want to discuss here in main calls or have a seperate call for this? 


Aram: I vote we work on it on these calls instead of creating another group.
[+1 in chat]

Pete: sounds great 

Nick: good for me

Pete: Would some or all of this make sense to upstream to other docs like Ethical Web Principles? 

Nick: That's a good idea. group also wants TAG review

Tess: We review everything sent to us 

Nick: Yeah, that makes sense to coordinate. 

Pete: sounds good. No one else currently on queue. 

Jeffrey: dkg most likely to have noticed this type of discussion happening elsewhere 

dkg: a bunch of places where this is happening as a discussion. Gov't and state and federal in the US. TSA has a major question that is open for public comment on this type of mechanism. (https://www.federalregister.gov/documents/2023/08/30/2023-18582/minimum-standards-for-drivers-licenses-and-identification-cards-acceptable-by-federal-agencies-for)  Piggybacking on ISO standards *something* but I don't think we can rule out ISO getting pulled into web standardization. Not just traditional standards orgs where this is being discussed. If the w3c can articulate principles around this it would be very useful. I have no objections to it happening here. 

Jeffrey: Identity credentials plan to accept mDLs in addition to other credentials. 

dkg: Reminds me about GSSAPI... layers of abstraction all the way down. We need to think in nick's outline of the rubric - what are the legal and polictical mechanisms and are their protocols that can support them. If the protocols in use don't have use for this or ways to check against unreasonable requests that seems troubling to me. I'd like to read in more ddetail but I've not beern confident that there is a place for that hook - what are the bigger social and opolitical structures these standards slot into and how do they deal with social or political abuse? 

Nick: Some other regulations in the US seem to have specific specifications or requirements in mind that we would have to consider, especially acceptable and unacceptable uses and we will need to input that into the technical design. 


### 5. Proposal for a workshop on evolving fingerprinting protections

https://github.com/w3c/strategy/issues/430#issuecomment-1735517517

Pete: Proposal let's pick it up. 

Nick: Note in the W3C strategy repo - considering a workshop on fingerprinting. Shubhie had set up a session at TPAC . Hoping to cover at higher bandwqidth. 

Shubhie: Looking for folks in this group who want to engage. We're early in this so big opportunities to shape this. Browsers have been shipping this for a while and there is high level alignment for users having particular protections. But we want to think about how to take it to the next level for protecting users. We want to have a conversation about what is success here and how do we shape and change the industry. How do we talk about where we want to take the industry and we don't have  aclear stance yet, even on what is tracking. 
The key things have been we want to have a more informed stance on tracking and we want a spectrum of use cases with payments analytics, etc... 
Open source collaboration on detection of fingerprinting and tracking signals. 
Do we want declerations from the developer ecoystem? 
How do we engage a regulatory lens on this?
My call to action is please let us know by reaching out to me or Nick or Sam who is here to work with you all here. 

Pete: Location in mind? 

Sam: US East COast seems to be the center of gravity for this crowd?
2019 was bay area but we're hearing east coast this time. 

Pete: Where's the best place to register interest? 

PLH: Give a thumbs up to the issue to start with. 

Shubhie: that makes sense. Ping me Sam or Nick. We want to know what level of interest. Do people want to get involved in organizing? Are there particular topics you want to propose? Ping me in Slack

PLH: Thumbs up the issue for notifications. 


### 6. Sharing privacy-related conversations and insights at TPAC

Pete: just a catch all for anything that grabbed folks attention during TPAC. Discuss. 

Nick: WebAppSec and permissions - this working group had some privacy relevant discussions. Especially on permissions. Proposals for a permissions element with a user visible UI on the webpage. Some other proposals about adding context or something in the request itself. 
I think these are going to be work items because they are taking up the permissions API. Give people a better sense of the privacy implications. 
Right now requests are out of the blue and mostly get rejected b/c people don't understand what is going on'

Pete: Also - have a session with the page with out recording it in the browser is a proposal that is up and may be of interest. 

[current, IETF formatted version of the Request-OTR proposal, though it'll be rewritten to match W3C spec-format now that its been adotped by WebAppSec https://datatracker.ietf.org/doc/draft-sahib-httpbis-off-the-record/]

dkg: Reviews considering privacy are coming out of the blue and getting rejected? I've seen that pattern happen in the IETF where I'm trying to get more involved. Human rights or privacy concerns are coming from privacy people and 15 years ago that would be security concerns in the IETF. Having a dedicated privacy / security / human rights group has been counter productive in some of these meetings. 
I don't know how useful that is for organization process? 
Privacy reviews mixing with non-privacy reviews helps make documents a little better because you are helping them. 

Nick: very useful thought that wasn't the specific case we were talking about earlier. We try to do broader reviews and not just privacy ones so we can have that situation. I think it is good guidence. 
I was talking about earlier the notifications from browser to the user like requesting the camera access. They are overasked and people don't understand them and reject them. 

dkg: got it, understand the level now. 

Nick: Yes but that was very useful feedback. 

Aram: re notifficaitons, it would be good to engage earlier with experts (in PING). OTherwise we could get a situation where the platform continues to move to the current model, which I think is a UI failure. Users don't like them and they get rejected and so legit uses are discouraged.  WOuld be good to get involved earlier and prevent repeating mistakes

Nick: WebAppSec would love to hear about it. There's quite a bit of frustrations. Browser vendors would be interested as well. 

dkg: that's a great observation - when people have the opportunity to reject the feature and do that is a reflection that isn't what they actually want. I am reminded about the AppTrackingTransparency feature in iOS - but iOS users don't want to be tracked so this was a clear indication made clear by users being given the option. When you say legitimate uses aren't even attempted what do you think it is and how users can distiguish? Information overload hapepning all teh time. 

Tess: one way to improve - have request be more specific . Storage access API - this is a catch all it is for things not imagined in other uses on the platform. People often hit deny. Solution - purpose built APIs that people can get specific comprehensible notifciations about. 

Aram: 

Jeffrey:I don't think no one has clicked allow on a notification prompt. Edge has started hiding the prompt and making it show up in the URL bar and used heuristifs to say ' this often gets clicked yes on this webste' and that is how it decides to show 
I don't know if there are enforcement options it is about helping users or preducting if users will want the prompt. 
Then helping websites to give the prompt the context it needs to be successful. 
Websites that prompt it on load are going to get problems 
News websites that make it more likely to get notifications are ones that have a particular thing for the user to click and then get a notification request in response. 
We just did the easiest thing for the browser and that let the ecosystem run out of control and that was the problem. 
Connecting back to the permissions element, I'm not sure it will help for this. The website can give more context but that's not really the problem here. Websites asking too often and in improper ways. 

Aram: I think this is broadly correct, but I don't know if it really is a full solution. It would be great if someone published about the URL bar version. 

Jeffrey: I'll ask around. 

Sam: reminds me about Shubhie's point at TPAC - detection of behavior and how that can influence when a prompt shows up vs is hidden. Reminds me of ad blocking as a problem. How do we know an API is being misused? This is not clear exactly. 

Jeffrey: user revokes permission. You need UI in the notification itself saying I didn't want this notification to appear. If you give enough surface area you can see at the browser level if it gets more denials than average and than demotes the visibility of the API from the site. Crowd Deny is what Chrome is calling it. There's a lot of stuff we can do and just need to decide on how to do it. 

### 7. AOB

* charter reviews

https://github.com/w3c/strategy/issues/414
https://github.com/w3c/strategy/issues/429

Nick: Asked to do horizontal reviews of charters and there have been less recently. Chairs have informally done this in the past. I've filed comments on this. This might be another thing we want to have people in the loop for the group. If you want to be in the charter review process let us know. Check the comments and see if we've raised the right things. 

PLH: that's good. New one Web and Networks IG https://github.com/w3c/strategy/issues/433 . If there is no interest to review than I'll say no comments from PING on a charter. 

Pete: we haven't been requiring everyone to review them like we review specs, but we just ask if anyone sees anything concerning. 

* Revisit GPC in the Privacy WG charter now that Tess is here?

Nick: updates on the charter were previviously discussed to ask about feedback 

Tess: Changes?

Nick: yes more limited scope. Made easier for IPR review by lawyers for feedback. 
GPC is the committed deliverable and potential ones based on incubation. 

Tess: Assumption is that GPC to rec is also horizontal privacy reviews? 

Nick: Yes

Tess: Does that make sense? 

PLH: Different individuals doing the work?

Tess: I understand if the need is to get more people into the group and not split them in different groups by giving them deliverables to work on. The security interest group got closed for lack of participation and webappsec hasn't taken up security reviews. Sam has previously maked them happen.

chatter: now they don't happen anymore? 

Tess: examples of this working? Internationalization? Accessability? 

PLH: Lists working groups that do this working well. Some are. Having conversations with the ATN(?) working group. Constant dedicated working individuals. 

Sam: I don't see it as dragging more people into security reviews. I don't think GPC headcount will be high. I see it as not spreading resources too thin. Rather than a new group, reasonable to put them all into one. 

Tess: I'm worried about namming something general for a group with specific work 

Sam: I like one spec groups but we need more people to chair such groups. 

Pete: closing meeting. 

