# Privacy Interest Group meeting, TPAC 2024

## 23 September 2024

### Attendees

- Pete Snyder (Brave, PING co-chair)
- Nick Doty (CDT)
- Shivan Sahib (Brave)
- Matthew Finkel (Apple)
- Christine Runnegar (PING co-chair)
- John Wilander (Apple WebKit)
- Aram Zucker-Scharff (The Washington Post)
- Ty Everett (BSV Association)
- Brayden Langley (BSV Association)
- Brett Banfe (BSV Association)
- Jake Jones (BSV Association)

Apologies: 

Chair: Nick, in room
Scribe: (Shared)

### Agenda

#### 1. Introductions, Code of Conduct

- Introductions of people in the room and online
- Interest Group - publish documents guidance, horizontal review, charter to create WG (and recharter when adding new items)
- Cover charter first on the agenda, due to timezones

#### 2. Charter updates

AC review of charter, received formal objection to form WG, took a long time to form Council to deal with objection, announced last week, will try to reach a conclusion ASAP (within 2 weeks), in parallel team is preparing draft W3C decision

Current charter has one committed deliverable (GPC privacy controls)
New proposal for an additional deliverable:

- Request-OTR Header (Request off-the-record)
  
  - GH repo for Request OTR spec: https://github.com/brave-experiments/off-the-record-ietf-spec
  - IETF draft: https://datatracker.ietf.org/doc/html/draft-sahib-httpbis-off-the-record
  - Shipping in Brave Nightly
  - Threat model:
    - Local "UI-Bound" adversary
    - Motivating use case: Intimate-Partner Violence, "hand-over-your-phone" (law enforcement)
  - When the header is received, the user agent should treat all information received as sensative
  - Brave shows an interstitial before accessing site
  - Comparisons:
    - Private browsing over-hides and effects all sites loaded in that session/window, not just the one site that should be protected, and easy to forget to use PB
    - Underhiding Clear-Site-Data, etc.
  - Does not cover initiators (search engine result)
  - Does not protect against compromised devices (e.g., malware)

- How many sites are interested in this?
  
  - ~5 sites, with occasional sites show interest

- "Sensitive" may be context specific, so a user may consider a site as sensitive within their locale while the user-agent or site may not

- Does Brave have per-tab cookie jars?
  
  - Chrome's cookie jar is shared across all Incognito windows
  - Could a site use this to extract identifiers about the user if they can force the user into this mode?

- Can this be abused by fraud sites?
  
  - Yes, requires users trusting the site

- Has there been any interest from news publishers that offer e.g., SecureDrop, tip reporting site
  
  - Yes, some discussions at IETF

- Next steps:
  
  - Add some links/references
  - Lots of interest, but need to decide if we should adopt and re-charter

#### Guidance documents

- Three relevant guidance documents:
  
  - Sec & Privacy questionaire
  
  - Mitigating Browser Fingerprinting
  
  - Privacy Principles
    
    - Sec & Privacy questionaire:
      
      - Provide some questions that give authors can answer for pre-review and identify issues at the early stages of development
      - Please let us know if there are any issues/improvements that can improve it
    
    - Mitigating Browser Fingerprinting
      
      - Non-normative guidance, still relevant but not recently updated
      - User agents seem to be currently interested in this, now may be a good time to update
      - Ephemeral fingerprinting
      - Calibration of devices
      - Suggests against noise injection
      - User-agent reduction
      - IP address "hiding"
      - Is there something else to cover?
      - WebKit published a blog post this past summer about new protections that were introduced in WebKit and talks about additional types of fingerprinting - https://webkit.org/blog/15697/private-browsing-2-0/
      - Question of fuzzing/randomness has come up mitigation discussions
        - Understanding/detail why/where it works
      - Taking a step back:
        - are there concerns about removing signals and how those signals can be replaced
      - [ missed some notes ]
    
    - Privacy Principles
      
      - "What the W3C 'thinks' about Privacy"
      - Received two formal objections
        - Ongoing discussion with one objection
      - One objection: W3C should not be talking about privacy and putting constraints on how companies should compete
      - Other: Improvements to various aspects of the document
      - How is this used?
        - In reviews of other documents
        - If a spec clearly violates some aspect of this document, then grounds for rejecting proposal

#### Conducting a privacy review

- Horizontal review groups at W3C
- Pete has been a prolific spec reviews (thoughts on doing reviews)
  - Group files request for review
  - Ping Chairs do Initial Review
  - Chairs find reviewer(s) within group and/or external to perform review
  - Reviewers perform review and share their findings on PING call
  - After discussing on PING call, reviewers open issues in spec repo (may add "privacy-needs-resolution" if issue is a blocker)
  - Request for review is then closed in PING repo
  - What to look for:
    - Specs add new way to access existing data
    - Extending lifetime of data
    - New Fingerprinting surface
    - New interaction with permissions
    - Side-channel from resource contention
    - Ability to read existing writable channel
    - Increasing granularity to an existing capability
  - Out of scope:
    - Implementation errors
    - Issue stemming from a compromised machine
  - On the border:
    - Risk of user error (e.g., introducing footgun)
    - Inherent implementation risk (e.g., too difficult/complicated to "get it right")
  - Areas of disagreement
    - Duplicating an existing privacy risk (e.g., WebGPU)
    - Standard should "require" vs "allow" privacy, depending on implementation details
    - Practical thresholds (theoretical vs possible vs practical vs trivial)
    - When "privacy-needs-resolution" is appropriate (no clear-cut guidance)
      - Simply means that this issue needs a resolution, not necessarily address/fix
  - In the area of privacy-preserving measurement, do not want to expose whether a feature is enabled/disabled (vs. feature supported) and how sites may gate access on allowing access. Does this fit?
    - Is this a privacy-concern? May be covered by Privacy Principles
  - State/storage that are readable, writable, and detectable?
    - Reviews haven't explicitly called out these characteristics, but previous reviews have highlighted concerns around features that fit into these areas

#### AOB

#### Relevant meetings this week

- LoginStatus API at FedIDCG
- Breakouts (too many good ones):
  - Some Permissions sessions
  - Fenced Frames
  - Future of Popups
  - PePC
  - FedCM in process
  - Cookie Layering
  - Harmonizing
  - Partitioning visited links
  - requestAccessFor

## 24 September 2024

### Attendees:

* Nick Doty, CDT  
* Pete Snyder, Brave Software, PING co-chair  
* Max Gendler, News Corp  
* Mark Nottingham, Cloudflare  
* Aram Zucker-Scharff, The Washington Post  
* Ben Kelly, Google Chrome  
* Brandon Maslen, Microsoft Edge  
* Aykut Bulut (Google \- Privacy Sandbox)  
* Chris Fredrickson (Google Chrome)  
* Zainab Rizvi (Google Chrome)  
* Kyra Seevers, Google Chrome  
* Erica Kovac (Google Chrome)  
* Aaron Selya (Google Chrome)  
* Alexandra Reimers (Google Chrome)  
* Lionel Basdevant (Criteo)  
* Aloïs Bissuel (Criteo)  
* Don Marti (Raptive)  
* Eric Kinnear (Apple)  
* Christine Runnegar (PING co-chair)  
* Chris Needham (BBC)  
* Rigo Wenning (W3C)  
* Thomas Prieur (Criteo)  
* Maxime Vono (Criteo)  
* Justin Brookman (Consumer Reports, Global Privacy Control editor)  
* Greg Bernstein (Invited expert, verifiable credentials, privacy enhancing cryptography at IETF)  
* Matthew Finkel (Apple)  
* Zachary Cancio (Google Chrome)  
* Junseok Lee (Samsung)  
* Fatma Moalla (Criteo)  
* Michael Kleber (Google Chrome — Privacy Sandbox)  
* Dan Appelquist (Invited Expert, TAG)  
* Nidhi Jaju (Google Chrome)  
* Sandor Major (Google – Privacy Sandbox)  
* Ben VanderSloot (Mozilla, observer)  
* Emily Lauber (Microsoft)  
* Sarah Jennings (HM Government, Observer)  
* Ashkan Soltani (Observer \- CPPA)  
* Daniel Huigens (Proton)  
* John Wilander (Apple WebKit)  
* Mirja Kühlewind (Observer \- Ericsson)  
* Elias Selman (Criteo)    

Chair: Nick Doty

Scribe: Rigo Wenning

### Agenda: [https://github.com/w3cping/administrivia/issues/49\#issuecomment-2359279913](https://github.com/w3cping/administrivia/issues/49#issuecomment-2359279913)

Minutes: [https://docs.google.com/document/d/1qKADVLZd8wxep0NWxHVmMXoJipdKn4ACxcJbNBBLF7g/edit](https://docs.google.com/document/d/1qKADVLZd8wxep0NWxHVmMXoJipdKn4ACxcJbNBBLF7g/edit)  

#### Code of Conduct and Welcome

[https://www.w3.org/policies/code-of-conduct/](https://www.w3.org/policies/code-of-conduct/)

Nick introduced PING and its goals, explains the limitations of an IG. If work is needed, this can be suggested to the Privacy CG. 

#### Global Privacy Control: an update

[https://globalprivacycontrol.org/](https://globalprivacycontrol.org/)   
[https://privacycg.github.io/gpc-spec/](https://privacycg.github.io/gpc-spec/)

I am Aram from Washington Post and will give a quick update on GPC. Added additional explainers for people who want to use GPC. A few issues still open with GPC. Technical issues are not ready so editors would want to introduce. So the document is ready to go to the Working Group as soon as it is ready. There was criticism, but so far no changes intended, because it is also used and mentioned in legal acts. 

Justin Brookman gave some explanations around the legal & social dimensions. Previous initiative of DNT was mentioned. Goal is to make it easier to opt out of data sharing. DNT failed because stakeholders could not get to consensus. What has changed is that there are new laws, especially in California. So first published in 2020\. Demonstrated that there is an easy way to opt-out. 2021 GA CA said that GPC has legal standing, means GPC interactions are valid legal assertions and since then, GPC tokens have been recognized. Many other states followed, 10-11 states have now legal acts that honor the GPC exchanges and tokens. In Colorado also had an implementation act few month ago. The GPC signal is now legally binding. No other signal recognized at the moment. Because of this legal recognition, it will be hard to have major changes in the specification. Colorado law talks about standardisation as important to avoid a California signal and a Colorado signals and other signals. This is one of the reasons why GPC is proposed to W3C. Started off in the Privacy CG.

Aram: Support GPC in 12 states. Most of the CMPs we are talking to, have some way to opt-out. We talked about simplicity, that is very important. Prompt has a cost in advertisement dollars. CMP are content management providers. 

Kleber: Have been paying attention to GPC for a while. Some things about the GPC make me nervous. Lead to issue No 52 [https://github.com/privacycg/gpc-spec/issues/52](https://github.com/privacycg/gpc-spec/issues/52), establish user intent by browser and how the browser control should look like so that users know. If it carries intent, this has to be represented correctly. Originally in the CA context we could act as if it was easy for us to know what the signal means by reference to law. Colorado law had a different meaning and we are worried about the the diverging meaning. The meaning discussion is covered in issue \#52 and we want to discuss that here. Fear that browsers will be made responsible for the opinion of the users.

Justin: Most things are not that different or at all different and CA is mainly sell data, but then also notes sharing across context. Colorado also framed it as cross site context use of data. So most laws are quite similar. Initially GPC was initially called SPARC and is there for the contextual integrity of interactions. We tried to shorten the discussion and move to a separate legal explainer document and wanted to offer more certainty of what is intended. Signal means what the legal signal is saying. We can try to provide documentation, but at the end of the day, states will determine what is meant. 

Aram from Wapo: Do not sell and consensus concept that colorado and Virginia have. Those are key concept. If you opted of the one you mainly also opted out of the other.   
MNot: Have you considered not non-US laws.? 

Justin: is designed in response to US opt-out regime, but also talked to EU regulators, but this is not clear what they'll accept. Most other countries have accepted a GDPR like approach. 

GPC could trigger a GPC opt-out mode.   
Kleber: Remain skeptical about do not sell mode and opt-out mode. Colorado seems explicit and others aren't. Another thing came up, is in regards on stickiness. Some state privacy law, once you receive the signal you'll have to honor until you get an opt-in signal again. There is no explicit signal for that opt-in in GPC. 

Justin: Law is not opt-out in general but about cross-site. Law does not allow for universal opt-out, so perhaps not relevant for GPC. Only CA and CO are explicit. The law is 10 lines and does not go into the details mentioned by Kleber. 

Justin does not think that it is materially really different. States could decide that GPC means something wildly different, so far have not seen it. 

Aram: So far no opt-in for the spec, because CMP or site is already obliged to provide some interface for that (explains options). Site will log the user in or store their preference locally and retain the choice. GPC signal not needed for that. Flipside, have 10s of thousands of people have opted out and 10s have opted back in, so also there does not seem to be a significant use case for that opt-in option. In regards to the difference between DNS/S and Colorado/Virginia style consents. Things that are personalized are ads and things affected are ads. Looking like others who have adopted Colorado law, it is mainly the same, so GPC is not in a minority on how they implemented it. 

Don Marti: Wanted to agree with Aram. Have rolled out 5k sites in multiple US states and it was straightforward, a small code addition on top of already done CCPA compliance tasks. With respect to meaning, there is a good document for the IAB for the GPP system ([https://iabtechlab.com/gpp/](https://iabtechlab.com/gpp/)) . Compliance mechanism is already in place. If people have questions about the meaning, we should look at sites and third parties such as IAB member companies that are already implementing it. 

Matt Finkel: Similar to Mark's comment. Puts into the web some specific language that is opt-out of advertisement. Can you talk about the global landscape?

Justin: It is intended for opt-out systems. Privacy protecting user agent would also be opt-out, to make the legal systems easily implementable. Could have an effect elsewhere, but this needs further considerations. Most privacy advocates have moved away from opt-in and to reduce choices to reduce annoyance. GPC is a better user experience than the cookie banners for opt-in. Opt-out allows choice

John: Currently is not standardised what is tracked. So if we have a GPC, we establish that the default on the web is that the user is tracked. \[Nick: ??\] This is a big change. This is an obligation on W3C. 

Mark Nottingham: Concern that because it's done in US context, it's responsive to that environment. Privacy in US is extreme, atypical globally. By designing the mechanism for that, it tilts the playing field. Would be much more comfortable if it had more international engagement, e.g., UK ICO, EU, Australia.

Max: Found several points not very relevant. If a user sends GPC, but the browser has not to implement the consequences. It is not on the browser to interpret for the website. Secondly, if a browser wants to support a world where ‘everyone is opted-out and can opt-in’, that is possible with GPC, and some of the browsers that have implemented the standard do this.

Aram: 2 things, what is the default state. The answer is already made, years of technical decisions have put us in that place that tracking is the default. Gain better privacy on the web and what that means for law. This is now a technical issue that advances us similar to many other places where we have advanced privacy in the W3C. 2nd thing is that this is one flavor of standard in the same way the web current supports multiple media codecs we can imagine that the web can support multiple legal standards to the advantage of a massive number of people on the web. If a different specification needs to be added to the web platform to support some new legal privileges under some new law than we can go forward to add that in a separate specification. 

Don: Agree with John on the basic point that the browser default should be not to have cross-context tracking/personalization. GPC is going beyond the web client/server space that the browser can affect, because it also addresses out of band communication (like “conversions APIs”) that the browser doesn’t even see. GPC reaches out beyond what the browser can address. GPC is a complementary tool to browser privacy features.

Ashkan Soltani. 1/ lot of discussion is reproducing discussion from a decade ago about application in different jurisdictions, those are out of scope for W3C. We are working with a consortium of state regulators, many of those have opt-out requirements and look for interoperability. And work with 148 other data protection authorities internationally to talk about the interoperability of those signals, and potentially applicability in GDPR or similar regimes. 

Some confusion about the signal works. Opt-out signal works, but a user can opt back in with an out of band consent. Looking how a technical specification could work internationally. 

John: In DNT there was an attempt and IE was setting it as a default and signal was ignored, whether or not the signal was set by the user. But still not clear about the web default. 

Nick summarizing the discussion.   
Questions and issues: 

* Meaning of opt-out and user interface for it  
* relevance for both opt-outs and Opt-in mechanisms  
* international 

Rigo: reference to [RFC 7258](https://www.rfc-editor.org/rfc/rfc7258) on pervasive monitoring and IETF making that decision and whether W3C has or should make a decision. It is a good question to address but the fact of monitoring is a fact already decided by the IETF and W3C should maybe face that discussion too. 

#### Credentials: user/privacy considerations

Nick introduces the topic and explains the document he did with Rick Byers: [https://github.com/w3cping/credential-considerations/blob/main/credentials-considerations.md](https://github.com/w3cping/credential-considerations/blob/main/credentials-considerations.md) 

Credentials, especially governmental IDs can be permanent and used for privacy invasive things. 

Restrictions of free expressions. Risk is to exclude people from access, if the governmental credential is required. 

Consolidating. Is there a reliance on centralized providers? Central wallet? 

Security threats: Impersonation, access, but also beyond. Can affect offline context as well. 

Mitigations, need help from this group:   
Process mitigation: How do we do standards and implement them? Technical Specification design, p.ex. Only part of the driving license is presented. Linkability is particularly important because of tracking. 

IN context explanation is also a topic. Because people do not know what they are being asked. There are legal requirements that we have seen. Especially out of context questions. 

Frictions and frequency of the presentation of credentials. 

No-phoning home is a way to provide protection against the issuer. 

Revocation was discussed with the VC WG. eIDAS has expectation that inappropriate use and that DPAs could ask about the use of the credentials with the website. Is there a way to report abuse. 

Open questions also in the document, looking of insights from others. 

Matt: How the current standards are reacting to it?   
Nick: eIDAS regulation has to be deployed soon, not clear how to be addressed for the person using the credentials. In context explanations there is no current work

Mirja: not understanding the consolidation point. In essence a general privacy problem, if attracted by a system that extracts data. Nick: whether there is a reliance on a small number of providers. More of a trust question to providers of those issuers. Design principle: use the most open standards possible. Reminds about general privacy by design rules.

Aaron: Concept of 2FA and notification that the credential was used. Fake information on untrusted sites.   
Nick: there is some way to find out whether data was used. Fake information and pseudonymity provided in some jurisdictions. fake information \- directed identifiers

Mark: Disclose mechanism implies user to make a choice. There is a risk of abuse. Is it exposing entire credential or only parts of it. Are there technical requirements around this instead of leaving it to the market. 

Christine: thank you for your contribution. 

Greg: working on VC, unlinkability is very similar to fingerprinting problem. Was using that argument this is also going into impersonation, but use pseudonymity and prevents linkability across website. See privacy write up in the VC BBS cryptosuite: [https://www.w3.org/TR/vc-di-bbs/\#privacy-considerations](https://www.w3.org/TR/vc-di-bbs/#privacy-considerations) (Greg).

Rigo: advantage of verifiable credentials is augmenting metadata with a data protection vocabulary. should also consider good actors to have the information to make the correct decision. possibility of legal liability as a consideration, exchange not just of personal data but credential data.

Aram: Does that implies that we also have something already expressed in the system, whether data use is signaled and other expectations. There was some issues with barcode scanners. We should be able to say we don’t intend our identity to be joined across multiple bars.

#### AOB

Request-OTR Header (Request off-the-record)

- GH repo for Request OTR spec: https://github.com/brave-experiments/off-the-record-ietf-spec
- IETF draft: https://datatracker.ietf.org/doc/html/draft-sahib-httpbis-off-the-record
- Shipping in Brave Nightly
- Threat model:
  - Local "UI-Bound" adversary
  - Motivating use case: Intimate-Partner Violence, "hand-over-your-phone" (law enforcement)
- When the header is received, the user agent should treat all information received as sensative
- Brave shows an interstitial before accessing site
- Comparisons:
  - Private browsing over-hides and effects all sites loaded in that session/window, not just the one site that should be protected, and easy to forget to use PB
  - Underhiding Clear-Site-Data, etc.
- Does not cover initiators (search engine result)
- Does not protect against compromised devices (e.g., malware)
