# Privacy Interest Group meeting (17 August 2023)

## Attendees 

* Nick Doty (CDT)
* Kyle Den Hartog (Brave)
* Pete Snyder (Brave, co-chair)
* Manu Sporny (Digital Bazaar)
* Jeffrey Yasskin (Google Chrome)
* Christine Runnegar (co-chair)
* Matthew Finkel (Apple)
* Przemek Praszczalek (Mastercard)
* Dave Longley (Digital Bazaar)
* Greg Bernstein
* David Waite (Ping Identity)
* plh
* Don Marti (Raptive)
* Sam Goto
* Dimitri Zagidulin
* Bruno Vavala
* Matthew Finkel

Apologies: Wendell Baker

Chair: Christine Runnegar

Scribe: Pete Snyder

### 0 Introductions and CEPC

intros from Kyle, Manu, Przemek, Greg, Dave

### 1. Verifiable credentials

Reviewer: Kyle

#### Verifiable Credentials Data Model: https://github.com/w3cping/privacy-request/issues/121
Kyle: this is the base layer data model.  There isnt a clean alignment with Web's typical 1p/3p distinction
…: i map this spec to the Web w/ issuers as 1p, and wallets/holders are user agents, verifiers are 3ps
…: I looked at prev review issues, and focused on the new parts

…: First, bc of the design of the core datamodel, theres a lot of optionality in the proposal, called "profiles" (e.g., creential status lists for certain formats, etc)
…: combining profiles can reveal metadata about where things were issued (Bc only certain regions issue / use certain profiles)
…: for example, the E.U. uses one profile, US a diff one.  Allows people to infer information about the holder
…: kinda a sidechannel from the metadata / format
…: spec/propsoal should mention this in the privacy considerations section

Manu: good feedback, we should add this to the privacy considerations sec
…: should provide guidance that type of credentiasl leaks info about holders, and so implementors / participants should strive to hold
…: and minimize granularity of profiles
…: should favor issuers who don't allow this kind of correlation

Jeffrey: Apple's private access token system seperate the attester (e.g., DMV) from the issuer (e.g., intermediary)
…: could have issuers generalize over more specific issuers 

Manu: GOod point.  Group has discussed idea of a "witness", trusted 3p which could attest to PII while blinding it from
…: an end party. Has downside that the new 3p poses its own privacy risk.
…: some approaches like this have been deployed

Kyle: there are tradeoffs in crypto schemes.  ring (?) signautres (used in monero) blind who the signer is.
…: possibly an issuer blidning system in BLS (?)
…: has the trade off of more profile meta data, and which crypto scheme itself might leak info

…: Second, similar to above, and kinda already discussed; issuer based corrleation.
…: can be mitigated by using common issuers

…: Third: holder based tracking. Some text exists on how things are stored, but not processed (?)
…: Similar to a browser being able to look at a users browsing history, a credential holder has the ability to view and learn about all the user's credentials
…: proposal should mention the tracking risk here, and map the holder to the same kinds of risks posed by UAs in browsers

Manu: +1. +1 in general to Kyles general points. We (the group) think he's done great work.
…: Please assume this feed back for future Kyle points

Nick: I like the idea of making it explicit that the holder software is similar to the UA, and so we should make the same risks and expectations explicit

Kyle: is there a seperation between the user agent and the user.

Jeffrey: IMO, not really, in terms of a trust / privacy model

Kyle: that might make things tricky, but holder -> might map cleanly in most cases, and maybe we should explicitly rule out the cases that dont

Manu: That sounds tricky bc of cases like guardians who hold credentials for others. Spec assuems other people's PII will be exposed by the holder
…: this happens all the time in the browser (scribe ?)
…: there are edge cases that we should be careful about

Jeffrey: different users have different interests on the web, and they each have their own UA to enforce their own interests
…: like Don pointed out in the chat, the draft W3C Privacy Principles cover user agents and [guardianship](https://w3ctag.github.io/privacy-principles/#guardians)... https://w3ctag.github.io/privacy-principles/#user-agents has some points on how these situations can be navigated

Kyle: this will take a while 
…: Point 4 of [#121](https://github.com/w3cping/privacy-request/issues/121), where the creds are stored makes a diff.
…: There are some that require, for example, adult sites to store credentials related to age
…: in some cases this will be privacy harming, since it centralizes risk
…: we should highlight the risk here, and favor credentials being re-requested from the holder, instead of folks storing credentials

Jeffrey: Is the issuer the attester, or the verifier? (?)

Kyle: the verifier is the relying party (scribe, not sure i have this right)

Nick: I also had this wrong, thank you for clarifying.  Sam, did you discuss a diff way of doing this?

Kyle: Sam and I have been discussing the Identity credentials spec, and exposing these through the browser UI, and the privacy impact
…: the concenr is what legislators will require

Nick: thank you for clarifying. There are more verifying parties than issuers.  Good to give guidance, but its difficult to get folks to follow guidance

Manu: Agree with Kyle, the info sent to a verifier could be cached over time and create centralized risk.
…: suggestiont to relying parties are unlikely to work
…: we need to encourage implementations to minizmie privacy risk in data before sending it to the verifier 
…: re NIck's comment, there are tech measures we can work on, we can also work with regulators and law makers to favor privacy preserving laws/flows.
…: We shouldn't only rely on technical mechanisms to reduce centralization risk
…: US govts are following VC and want guidance

Kyle: I agree with Manu. Horizontal reviews should be careful about how to address privacy risks at data model layer, vs protocol layer
…: for example, digital credentials to social media accounts. Might have case where this could harm folks expressing dissent

#### Verifiable Credential Data Integrity: https://github.com/w3cping/privacy-request/issues/120

Kyle: will continue with the mapped to the web model discussd above
…: this should include many of the privacy concerns discussed in the above presented review

…: First, there are proof chains and proof sets; are you signing the same claims (set), or also other people's attributes (chain) (scribe: ?)
…: bc chain signs over prev signers, you're learning something about other partities. In some cases this is necessary,
…: but privacy considerations section should highlight this risk and encourage folks to use claim sets when possible

Christine: are there ways to mitigate abuse?

Kyle: Through profile selections and required passing to the holder. Maybe no good mitigations at this layer, but might be possible at protocol layer

Manu: +1, we'll add text to the privacy considerations section.  I also agree we should point to privacy consderations from the data layer doc
…: layering the specs makes it tricky; we'll make sure deeper layers point to higher layers re privac conisderations

Kyle: rest are more security related. Should I discuss them here?

Christine: usually we discuss privacy issues, but lets also cover security issues

Kyle: Third, key reuse is a concern, an we should advocate not re-using keys (for example, with DiDs).
…: Key reuse is difficult to prevent. RIsks aren't proven, but suspected. Spec should discourage key reuse

Kyle: Four, crypto sweets should be required to define a well known context.  I expect this is known but just missing.
…: if you dont require it, these contexts / identifiers used to address RDF tuples can be abused to reveal IP (?) tracking by putting an ID in a verifying URL
…: I think its mentioned in the data model, but should be enforced here

Manu: +1, we were waiting for "you should cache contexts" to land in the data model. I expect it'll also show up here

Kyle: Five, should point to the RDF conocilzation spec bc this spec is dependent on those for security and privacy

Kyle: Six, should non-deterministic sigs should be disallowed. They can reveal info about the issuers priv key

Greg: I wanted to push for disaloowing non-deterministic sigs.  

Manu: We do have this in the ECDSA Cryptosuite today (but no normative statement) -- https://w3c.github.io/vc-di-ecdsa/#implementation-considerations-for-ecdsa-algorithms

Dave: we also had a concern for folks using the WebCrypto API, to use non-determinisitic sig. So folks implementing in the browser currently need to do non-deterministic sigs

Kyle: Okie, i think should is fine

Matt: FOllowing up on Greg's point, seems like this could overlap w/ PRivacy Pass, which also requries unlinkable credentials

#### Verifiable Credentials JSON Schema Specification: https://github.com/w3cping/privacy-request/issues/119

Kyle: summary, in the VC data model, you can restrict the cred scheme by using a JSON Schema
…: First, spec says the ID prop should be a de-ref-able Id.  THis creates privacy risk
…: Second, certian proof sweets might allow a verifier to learn information based on the credential scheme. Should be discussed in privacy sec
…: Third, to prevent IP based resolution tracking, when resolving URLs in the data model, would be useful to use OHTTP or something similar to hide IP->content based tracking

Matt: that'd be a recommendation to issuers, so their systems can be compatable with OHTTP (or similar)

Kyle: yes

CHristine: thank you very much for your help in doing reviews

### 2. Privacy concerns related to credential type mechanisms and age assurance/verification

Nick: re privacy conerns about credential management in general, which might come up in specifications, but also
…: system/ecosystem wide concerns aobut how these could get used, what happens to data afterwards, etc
…: Seems like a particular concern bc of regulatory requirements around age verification, and chilling effect of
…: normalizing credential requirements.
…: Might be good for a longer convo at TPAC.  Touches on VC, WICG crdential management API
…: what should PING's role be in guidance here?

Christine: we might invitie relevant groups

Jeffrey: you're limiting discussion to age verification, but this tech can prove other kinds of things too. Focusing on the existing concrete legislation could help, but we might also want to discuss other techniques and uses.

Nick: Good point

Manu: +1 to Jeffrey/having the broader disucssion.  Digital Bazaar is deploying a digital age verification system w/ an agressive privacy stance.
…: Would be glad to discuss what our system's design looks like and how we do privacy things (prevent retalors from tracking, etc)
…: we're also working with DMVs bc of recent legislation / regulations
…: having something from PING would be helpful with talking with govs

Kyle: https://github.com/WICG/mobile-document-request-api/issues/6
…: ive been raising similar points in WICG.
…: this should be a statement with some offical capacity in W3C, bc of orgs like state dept / white house being interested
…: some groups are worried about abuse potential when there is malicious regluation in place
…: w3c endorced statement would be helpful

Christine: might be good to involve TAG too

### 3. Charter reviews
(reviewed by Pete, skipped bc of time)

### 4. Privacy WG charter

Nick: lets discuss at TPAC, but we have a draft WG charter.  Please file issues at the PING repo

### 5. Preparing for TPAC

Christine: if you have ideas for what to discuss at TPAC, please disucss on Slack or public email list

You can also add suggested items to this github issue: https://github.com/w3cping/administrivia/issues/36

### 6. AOB

PHL: please open issues on the charters Pete

Christine: Please share them on the privacy reviews channel too



