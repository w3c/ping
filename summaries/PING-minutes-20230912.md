# Privacy Interest Group meeting, TPAC 2023 (12 September 2023)

## Attendees 

* Pete Snyder (Brave, PING Co-Chair)
* Charlie Harrison (Google Chrome)
* Nick Doty (CDT)
* Manu Sporny (Digital Bazaar)
* Filipa Senra (Google Chrome)
* Ben Wiser (Google Android)
* Michael Kleber (Google Chrome)
* Tom Van Goethem (Google Chrome) 
* Yi Gu (Google Chrome)
* Antonio Sartori (Google Chrome)
* Phillipp Schoppmann (Google)
* Mihai Cirlanaru (Google Android)
* Bill Chen (Google)
* Sota Akiyama (Yahoo Japan)
* Jonathan Kingston (DuckDuckGo)
* Tim Huang (Mozilla)
* Tim Cappalli (Microsoft Identity)
* Christian Dullweber (Google Chrome)
* Shubhie Panicker (Google Chrome)
* Johann Hofmann (Google Chrome)
* Raphael Kubo da Costa (Intel)
* Anssi Kostiainen (Intel)
* Kenneth Christiansen (Intel)
* Matthew Finkel (Apple)
* Sean Turner (sn3rd)
* Joey Knightbrook (Snap)
* Rick Byers (Google Chrome)
* Chris Fredrickson (Google Chrome)
* Joshua Ssengonzi(Article19/DefendDefenders)
* Nicola Tommasi (Google Chrome)
* Marek Blachut (HM Government)
* Sam Weiler (W3C)
* Kristina Yasuda (Microsoft Identity)
* Jeffrey Yasskin (Google Chrome)
* Aram Zucker-Scharff (The Washington Post)
* Tara Whalen (Cloudflare)
* Philippe Le Hegaret (W3C)
* Artur Janc (Google Security)
* Wendell Baker (Yahoo)

Apologies: 

Chairs: Pete, Nick
Scribe: Jeffrey


https://www.w3.org/events/meetings/40eb7cef-869b-433a-b749-ad84f95549d0/

12 September 2023, 17:00–18:30 Central European Summer Time 
Nervion-Arenal II, Level -1


## Agenda

### 1. Introductions, Code of Ethics and Professional Conduct

https://www.w3.org/Consortium/cepc/


### 2. Privacy Principles: a quick update

Pete: work ongoing with the TAG and PING participants, for privacy in specifications, guidance for W3C but may also be relevant outside W3C. Still gathering feedback, but the text of the document is getting closer to complete. Breakout session (14:30-15:30) to talk about remaining issues there. Please take a look through the document, including how to treat legacy aspects, designing new features, trade-offs regarding sensitive groups or how to handle data that may be sensitive.

Pete: useful for horizontal review that PING does, and platform review that the TAG does. JYasskin provided an update in the AC meeting.

Nick: Any questions?

Pete: I'll add links to the draft document and breakout.

Privacy Principles editors draft: https://w3ctag.github.io/privacy-principles/
Privacy Principles breakout session: https://www.w3.org/2023/09/TPAC/breakouts.html#b-09ac96f4-d42e-4550-94d0-112287693ab7


    
### 3. Credentials, identity and age verification (30 min)
    Invitees: Verifiable Credentials WG, IdentityCredential collaborators
    
Nick: Verifiable Credentials rep and Rick, please give overviews.

  Rick Byers: [Slides](https://docs.google.com/presentation/d/1Z7blMTME1tAQAdO-Wr42oVNN3CRIbklASjbJdB1JYOc/edit?resourcekey=0-ockU2NbemVbLEeF94-peNA#slide=id.p)
Rick: Overview of the space. I'm not actually an expert in the space, so this is what I've learned over the last couple months. Couple technologies. mdoc, defined by ISO. Extension being developed to present these driver licences over the web, without any browser support. It lets you log in using your driver's license. Apple Wallet has support to native apps, but other apps are integrated into the web.

Rick: W3C Verifiable Credentials is another approach to high-trust credential types. Like federation, but it's an improvement because there's a holder. Sign-in with FedID talks to the IDP, but a wallet can give more privacy. Showing your license to buy alcohol shouldn't tell the government every time you buy alcohol. mdocs could have that property too. VCs are seeing deployment. e.g. U.S. immigration.

Rick: Microsoft has an authenticator app to present VC to a website. There's eIDAS 2.0 regulation in Europe in 2025, designed to be an identity system that Europe is happy with, which compels some companies to accept this form of ID. 

Rick: The ecosystem has been building real-world identity for years without any help from browsers or OSes. We're late to the party. Is this good or bad? Do we want to have a say? For a long time I didn't want to touch this, but I've come to the conclusion that this isn't a good reaction if we want some involvement in where this goes.

Rick: There are opportunities and risks. Can't make a throwaway or anonymous one. Chilling effects. Free expression? Large tech companies might use this to centralize. Discriminate against minority hardware. I wrote up some personal thoughts. What do we want to do about this? I think we should probably add a browser API, which will let us monitor and perhaps warn users. It might already be too late, since things are deployed and in laws.
https://github.com/RByers/identity-credential/blob/risks/risks.md

Nick: Thanks; going to the q.

Matt: What does the world look like if we don't do this? If there aren't native browser APIs.

Rick: If we don't provide any API, the mdoc approach is already fairly seemless with a custom URL scheme. It's hard to predict. I think there's a lot of momentum, and especially in Europe they'll be used to sign in. Will they be used by adtech? We can see the use of the mdoc: scheme, but we're a mitm, so we can't see anything about what kind of request it is. There's a debate about friction, but seems like non-browser route is low-friction.

Kristina: People are thinking about endpoints with an encrypted datastore. 

Tim: The current wallet invocation is highly unreliable and interceptable. on-device and cross-device phishing is a problem. We've worked hard with WebAuthn to prevent that.

Manu: +1 to Kristina. There are multiple deployment architectures today. Is it too late? I think no, there's benefit for privacy if browsers get involved. Be aware that a lot of thinking has gone into this over the years around what the right boundary is between the browser and the wallet. How do you show the right screens to prevent phishing? Work needs good privacy review and needs browser vendors to be more involved.

Aram: If people pick this up, is it about establishing browser APIs generally, or how browsers can contain native wallets, maybe neutral to a bunch of different IDs.

Rick: Both. Started work in the WICG about a specific API that Apple and Google expressed an interest, and Microsoft supported having work in the WICG, but we don't know the scope. I'm interested in the wider scope. Guard rails. Principles to mitigate potential abuse. 

Kristina: I co-chair the Verifiable Credentials Working Group. Right now, there's a user component in the middle. IDP presents data to user, and user presents it. The data model is just between the issuer and wallet, and wallet and verifier. Not talking about algorithms or how to send it. mdocs in ISO have a different stance, and their own full stack. W3C only talks about the data format. The user presents directly to the verifier because the user controls the private key. The browser API is the transport layer. 2 problems that we observe: how the response gets into the wallet when the wallet is a native app. Each mobile OS gives a different experience. Another part is cross-device security. If the attacker generates a QR code and scans on another device, nothing binds the devices. On privacy, we have to be aware which combination of components you're talking about. New fancy cryptography, where RPs can't collude. Or traditional cryptography that doesn't give those properties by default but you can get it in other ways. Can't just assume the 3-party model is it; you have to be precise what you're talking about.

Rick: Pile on with Tim about reducing risks. The ISO protocol users mdoc:, but any app can register those. If we build this into the browser, we can protect the user better. As Kristina said, this all comes down to details.

Nick: Thanks for the overviews. Rick did a good job talking about the legal requirements. We're also seeing age verification requirements. Websites are looking for how to do that, and it might involve a government credential. People in the human rights space are concerned for a long list of reasons. Worried about what might get collected. Free expression bias and discrimination issues. Age verification or credentials might only be available to some people, or the need to present a credential could discourage people. Presented as about pornography, but it can also block health info or LGBTQ information. If we provide an easy capability, it will be abused. If there's agreement among implementers that the work is going to happen, then we can look at thorough guardrails. If a regulator says we need this, we can prevent the potential abuses. I also have a document with concerns, which I'll share or collaborate on it with others. That's from the Center for Democracy and Technology.

Manu: One thing we want to look at is real deployed systems. [shares screen] There's a National Association of Convenience Stores. 150k stores, and they sell alcohol and do age verification in-store. They've been building TruAge. Want to move to a more privacy digital ID check. They ask for the license, and the clerk scans the whole license. 35 pieces of information. Not good for privacy. Association said VCs looked interesting. That system was deployed in Jan 2023. State of California integrated that system and deployed a pilot of 1.5M people. If things go well, they'll deploy to 24M Californians. System was design with what we think is the most aggressive privacy stance for the individual. Tokens are single-use. Can't be used to track people even if retailers collude. Onboarding reads a driver's license, but it's immediately tokenized so the data is unavailable. You ahve a QR code, which is a VC. Deployed in CA through the driver's license app. Can be taken at the point of sale to prove age. Don't have to hand over your license anymore. So these systems are already deployed. Let's focus on these deployments. They want to do the right thing, and would benefit from the PING's input.

Nick: Good reminder to those of us who are less familiar that these are already deployed.

Aram: I think conceptually I dislike these things, but the reality is that they're deploying onto the web, and we need to establish a standard to provide more safety than we have now. There's a lot of low-trust actors who have competed to enter this space. There's a space ahead of us where presenting digital driver's licenses will be required on the web, and if there's no way my browser can protect that, it's bad. We should help support a group picking this up. Also, Nick, I would love to see your documents with resources.

Christine: I'm curious if there's been exploration of having the credential provider (CA DMV) directly issuing people with a VC token that they can use, that merely asserts they're of a certain age, rather than going through intermediaries.

Kristina: I participate in the ISO standard. That might have sailed. TSA is saying a digital document that they'll accept is only a driving license compliant to that standard. It has OpenID Connect. There was a campaign for privacy, and the OpenID Connect is a phone-home, which is bad. So the 3-party model is what happened.

Kristina: Caveat: Driving licenses aren't the only use case for the 3-party model. Educational credentials. OpenBadges have 7M badges issued. Enterprise identity. I also want to see the list, and I share the concerns. But a lot of these things don't depend on technology. Depends how you deploy it. Once the issuer issues to the wallet, then the issuer has no control of how the user uses it. In driving licenses, there's an Intent To Retain, where the issuer asks the wallet to say somethign about the data, and then something said it plans to delete the data. Nothing enforces that legally.
ACLU report very important on this topic.
[i think the reference is https://www.aclu.org/sites/default/files/field_document/20210517-digitallicense.pdf ]

Manu: Re Christine: The TruAge token is a VC with one property that just says you're over a particular age like 15, 18, or 21. By regulation, compels certain actors to do identity proofing. The approach is to get the identity proofing as early as possible, and translate that to a privacy-preserving credential of some kind. Input a DL once while you're onboarding into the app, and then the tokens are just "over 21" tokens that can be used at the point of sale. Need to pay attention to the regulatory burdens for people accepting these documents. Can we reduce the burden so people collect less data?

Nick: Need to move on. My sense of the room is that there's interest in working on privacy guidance to list risks and mitigations. Focus on the fact that these are already deployed. Looking for volunteers to work on a deliverable for this. Contact me on Slack or offline.

Tim: Breakout tomorrow at 2:30.
 

### 4. Privacy reviews follow-ups (30 min)
    Invitees: Devices and Sensors WG

Background material:
- Proposed cross-site covert channels attack and discussion: https://github.com/w3c/compute-pressure/issues/197
- Compute Pressure API specification: https://www.w3.org/TR/compute-pressure/


Anssi: We have APIs for compute pressure. Had a great discussion with PING and came up with mitigations. 

Kenneth: Compute pressure is global state, which can be abused for side-channel attacks. We tried to implement it to see if it's reasonable. It's pretty difficult if there are background tasks, but on a quiet machine it's possible. Use 3 workload levels to send bits. Could send data on my system. Worked on mitigations, which are in flags in Chromium. 2 mitigations: obscure rate and calibration. These block this attack. We'll keep on testing to find values to mandate in the spec.

Anssi: Can point at the github issue where we collaborated on this.

Nick: Great to hear it was a success.

Pete: Thank you to the group for being receptive and working to figure out a mitigation here. Thank you for sharing your experience. It's useful to hear about these reviews being collaborative and productive.

Nick: I hear something about common themes. Are there similar threats that'll show up in other APIs. e.g. calibration. If you provide something with calibration to the web, you need to do X.

Anssi: We could generalize these patterns and tell spec authors to look at them. You wrote a [fingerprinting document](https://www.w3.org/TR/fingerprinting-guidance/), which I gave to our spec authors. High-level abstract principles are hard to deploy to coders. 

Anssi: Web specs are often very algorithmic and hard to read and understand. It's good to have an informative human-readable description too. Pete, you want the spec to recommend certain thresholds. We let implementations pick a value, but we can probably find some reasonable limits.

[+1 for human readable version, which makes it a lot easier for a non-domain-subject-expert person to review]

Anssi: Do you have other groups come to your meetings to report back on similar cases? Would be good to learn from how other groups are doing reviews.

Pete: We don't usually do this. Sometimes groups come when they're having trouble, but it was good to have a positive postmortem of a success story.

Nick: Anyone else who's been in another WG with an experience of how the review process went or what we should be learning?

Manu: Recent review of the Verifiable Credentials spec (See below) was really helpful. Kyle highlighted a number of issues, which we agreed with. One challenge was that our spec is so broadly applicable. Examples from passport to class credit. Becomes really difficult for PING to do a review of how this is used. Don't know how I would review such a general technology. Could be useful to look at case studies and break them apart. Getting very specific with developers is helpful. Postmortem reviews of production systems could provide that for the specification.

Christine: Thank you Nick and to all the working groups that have sought us out, and particularly groups that come early on. We've had great conversations about how to mitigate privacy risks at that point. For new people, there's guidance in the self-review security & privacy questionnaire. Also in the Mitigating fingerprinting guidance. And in the Privacy Principles. We need more people to volunteer for reviews, and thank you to the people who have volunteered.

Pete: Manu's question on what makes reviews easier or more difficult. I really appreciated the VC group moving the specs forward at the same time. oftentimes a group will be working on 14 specs at once, but advance them 1 at a time even though they're interdependent. We'll identify an issue, but it would be better handled in a doc that's not up for review.

Manu: It's a challenge to move multiple specs at the same time. Every WG struggles with that. ... VCs could use unlinkable signatures. You'd have no tracking information. We've had a challenge convincing people that we should invest in this technology. BBS signatures. National governments don't recognize it. We don't see countervailing pressure to say "you need to spend time to develop these technologies." What we end up with if that doesn't happen is an environment with less privacy. We support NIST-based cryptography and selective disclosure, but the signatures are still trackable. Privacy review looks at what's there, and what do you need to think about. It's missing to look at the horizon so governments see that message. Takes 7-10 years to get NIST to approve new technology. There are governments that want to deploy this, but they don't want to look like they're advancing unstable cryptography. PING should say "We need better privacy-preserving technology."



Jeffrey: on that in particular, most often IETF CFRG that standardizes cryptography, and governments are more likely to trust that particular group. PING should be making some sort of statement about solution of a use case.
Manu: +1, just generally identifying and promoting privacy preserving technology wherever it's happening.




Verifiable credentials PING reviews 
 - https://github.com/w3cping/privacy-request/issues/119
 - https://github.com/w3cping/privacy-request/issues/120
 - https://github.com/w3cping/privacy-request/issues/121



### 5. Charter, for Working Group and/or Interest Group

https://w3cping.github.io/administrivia/2023/charter.html
https://github.com/w3cping/administrivia/issues?q=label%3Acharter

Nick: Charters! We need to figure out this group's next charter. We extended this group's charter. We have a [draft WG charter](https://w3cping.github.io/administrivia/2023/charter.html). Sam gave us a good intro to this in the AC meeting. The proposal is that we have a WG that does horizontal review and some specifications. That's more in line with some other horizontal review groups at the W3C. And would give a home for some other work. In response to some advice, we've tried to narrow the scope. We don't think there's a ton of work that we can't anticipate. The updated draft specfies that the scope is only the listed deliverables. GPC and depending on incubation progress, bounce tracking and privacy attestations/labels. We have willing chairs. We'd have to coordinate some, but would also separate agenda items.

Nick: Or! We could narrow the IG's charter to remove incubation wording, and start a separate charter for standards. Seems like more work, but could also give this group a charter.

Anssi: I'm reading the draft, and out of scope talks about incubation, and the Privacy CG will incubate things. How do you expect the graduation to happen? Will you recharter when you take a deliverable? Or more streamlined way?

Nick: An earlier draft said the WG would choose anything that's topical. That avoids the problem of rechartering, but makes it hard to review the scope and join the group. Feedback was the rechartering shouldn't be too hard.

Jeffrey: Ask Tess? And Privacy Sandbox is doing some attestation stuff, although it's not in an incubation venue.

Nick: I haven't talked to Tess. Matt?

Matt: I haven't talked to Tess either. There's important work that needs to happen somewhere, and some situations that other existing WGs don't fit.

Nick: Will talk to Tess. On attestation/labels, need to add text about incubation needing to happen. Privacy Sandbox work is relevant, and Permissions Workshops have talked about labels.

Christine: Like you, we want to resolve this quickly. It's been under discussion for some time.

Jeffrey: Maybe the Team is being too cautious, and we should just push this to the AC and make them formally object.

Nick does a straw poll. Do you think the horizontal review and specs should be combined?
[Zoom has some hands, but the room has 2-3]
Do you think HR and specs should be separate?
[1-2 hands total]

Aram: Do we think one of these options is more likely to pass through review faster? I'm concerned that HR and spec work might not usually be combined.

Nick: Not so much precedent, but there's some WGs that do horizontal review. Accessibility and Internationalization.

Aram: Ok, since there's precedent, I like the combined option.

Sam: Fingerprinting breakout will collide with the chartering breakout.

Nick: I'll go back to Tess, and will update the draft charter to reflect incubation needs. 

Jeffrey: I'll raise that at the chartering meeting.

Matt: I don't think we'd want to split time across 2 separate groups just to have 2 groups.

Anssi: Will you get new participants to do the new work, or is it more work for the existing participants. 

Nick: I think some Privacy CG and WICG folks will come help do the work here.

Nick: I'm somewhat optimistic that the combined group will improve horizontal review participation.
Christine: +1 for improving review


[adjourned]

Thanks all, and thanks Jeffrey for scribing (yet again). Stay safe and be well.

