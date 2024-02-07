# Privacy Interest Group (PING) meeting, 1 February 2024

## Attendees 

* Nick Doty (CDT)
* Pete Snyder (Brave, PING co-chair)
* Philippe Le Hegaret (W3C)
* Christine Runnegar (PING co-chair, invited expert)
* Jeffrey Yasskin (Google Chrome)
* Walter Rudametkin (Inria)
* Lubna Dajani (Allternet)
* Kyle Den Hartog (Brave)
* Aram Zucker-Scharff (The Washington Post)
* Ray Holton (NBC Universal)

Apologies: 

Chair: Nick

Scribe: Pete

## Agenda

###  1. Introductions, Code of Ethics and Professional Conduct

https://www.w3.org/Consortium/cepc/

- Walter Rudametkin: first meeting, work at Inria on privacy work and fingerprinting (AmIUnique.org website).
- Lubna Dajani: also first meeting, interested in ethical AI, human generated data, across multiple technologies and standards, and how privacy and ethics interact

### 2. Privacy reviews

https://github.com/w3cping/privacy-request/issues

#### BBS Cryptosuite
https://github.com/w3cping/privacy-request/issues/126
https://www.w3.org/TR/vc-di-bbs/
https://datatracker.ietf.org/group/secdir/about/ # Can be used for secure
Reviewer: Kyle

Kyle: Spec defines a cryptographic suite (or "proof mechanism") to allow for the selective disclosure of attributes. JSON attributes can be individually signed, and so can be indivually revealled.

...: Also allows zero-knowledge-proofs over each attribute, to prove some party knows the value without disclosing ing.

...: Main concerns are editoral issues, the draft was confusing to read, which was concerning since Kyle has background understanding of the work and area already. For example

...: 1. lack of normative language; things that seem like they should be normative, aren't. For example, BBS signautres section has normative language, but then also includes options for different has algos.

...:    and its not clear w/in the spec how to indicate which algo is being used

...: 2. there may be a security issue. Kyle is discussing the authors. THe "challenge property" is defined by the verifier, and submitted to the holder, during the proof generation period, making it online

...:    BBS is a deterministic signature scheme exept for the randomness in the nonces. Some attributes might be able to be revealed if the private key is revealed (?). Not certain this is an issue, still

...:    discussing with the authors.

Jeffrey: in theory the w3c does security wide review, but we don't currently have the group/folks for that. We need dedicated security people

PLH: We have a new security lead starting this coming Monday, so this is getting fixed and improved. Goal is to add back security horizontal review

Nick: sec reviews often come up in privacy reviews, but its a different set of skills

Kyle: When we (verifiable crdentials WG?) were signing the charter, we agreed to get security review from the IETF sec team. CFRG(?) is also doing a review of the underly crypto too

Nick: who should we follow up with?

PLH: I dont have a IETF team contact anymore, but we should make sure this issue (BBS sec issue) is flagged before the spec moves forward.  Might ask Kyle for contacts

Kyle: I will figure out the contact and follow up

PLH: Martian thompson is another contact for this

Christine: we should use our laison to the IETF too

Lubna: I have some background in IETF sec work if it'd be helpful too

Nick: My undersdtanding is that the advange here is that this crypto system breaks linkability, but that can be undone if you're signing something that undoes that linkability (e.g., identical attributes in two different places).

...: however, timestamps of the signatures themselves might also be linkable. Can someting be done to prevent inadvertant linkability

Kyle: This is a common problem with all VC.  The credentialSubject.id of the VC might be linkabile across different presentations. There is the option to have manditory attributes, forcing the issuer to reveal the attribute, which would cause

...: linkability. BBS is faster though (bc its offline?), but that comes with the risk of the correlation/linkable risk

...: I dont see a way to avoid linkability w/o differential privacy or some other machinery. We could add privcay considerations (some text is already there, even if its not perfectly clear)

...: so, its a problem, even if not easily fixable

Nick: why are mandatory attribures valuble? Why should issuers be able to require any attributes?

Kyle: I dont remember the thinking here, not sure

Jeffery: I filed an issue about helping holders detect and prevent privacy problems. The spec has text saying that issuers could take certain steps to prevent

...: leakage, but the holders are the folks with the privacy concerns, so spec authors should focus on thinking about what the holders can do to have

...: more control over the privacy risk.

...: Also, from slack, BBS is sold a way to prevent linkability, but the VC spec includes a lot of linkability in and of itself.

...: This might create a false sense of security. What can be done to prevent folks from having a false sense of privacy?

Kyle: I agree, and why i focused on normative language. Is there something that could be done at the BBS layer to prevent

...: linkage at the VC later?

...: there should be a user angent boundary when revealing attributes (?). Possibly we could require that users

...: be notified (of linkability risk?) in UI.

...: That risks creating a leaky abstraction, since you're defining UI experiences within cryptographic suite defs

Jeffery: We dont usually say much about the UI in specs. Web Permissions spec is the closest/most in this regard.

...: I didn't notice that the spec was ambigious between "user agent" and "person"

...: but we should make sure were talking about software in specs

Nick: We might normatively require notifications about linkablity risk. We might require obviously linkable values / attributes to have warnings that

...: other attributes don't have

Christine: If we can't address all the risks Jeffery raised, could we note in the privacy conisderations section

...: to make sure the spec / technology doesn't mislead users about how linkable the overall system is

[+1s]

Kyle: that sounds good to me +1. Shoudl be a bigger emphasis on the requirements/protections of holder software

...: the specs sometimes collapse the different interests of the different parties in these systems

...: I assume most wallets will do a risk assessment of different values being shared, but seems like

...: an implementation specific detail

Jeffrey: The conformance section of the spec only mentions one conformance category, but it'd

...: be better to break that into differnet holders, issuers, verrifiers

...: We could also add SHOULD language suggesting warnings to users

Nick: Are there issues tracking this?

Kyle: I'll add it to the list of issues im opening. Can someone else help take a look? Jeffery?

Jeffery: happy to help proofread if Kyle writes/drafts

PLH: will Kyle also file the security issue / risk?

Kyle: Im not sure about the right context, but i will file a review asking the WG to get a security review

PLH: Please add the `security-needs-resolution` tag

Christine: Let us know if you need help with labels or similar



#### Bitstring Status List, from Kyle and Nick.
https://w3c.github.io/vc-bitstring-status-list/
issue: https://github.com/w3cping/privacy-request/issues/127
Reviewer: Nick, Kyle

Nick: use case here is that the holder has received a credential, and is going to present it to verifiers

...: however, verifiers might want to check of those credentials have been revoked (e.g., expired license, credetnial issued in error)

...: This is like a similar problem in PKI

...: Proposal here is a "revocation vector", and just create a list of yes/no boolean values. No metadata. This also compresseses well

...: Privacy goal here is to avoid broadcasting publically which credentials have been revoked

...: I think there are other privacy concerns here though

...: 1. you could have linkable cross-origin identifiers. Credentials might include an identifier to use when checking for revocation

...:    However, the "revocation check" id might end up being persistant, and so could end up being an identifier (across parties, or across time)

...:    this is not covered

...: 2. When you present a credential, each attribute could have its own unique verifier list, which would reveal something to the
….    issuer when the credential is being used. Things like privacy pass could be helpful here
…. 3. Checking for revocation itself reveals information. So, it could reveal sensitive infromation after the data that its useful to the holder
….    Would be useful to limit the time period during which validity could be checked

...: 4. Hashing by verifiers, or CDNs by issuers, could prevent the issuer from learning that a verifier just received a credential (the one they're checking).
….    However, CDNs are not "privacy shields". They keep logs, etc that could be checked

Jeffery: +1 to all. There needs to be more thought given to how holders can chek if issuers are malicious.

...: Theres a trade off between online systems (like OCSP stapling) and "offline" systems (like CRLists)

...: Given the requirements of this spec, it mgiht be better to go with the OCSP-like approach, but this spec could be tighter to guarantee some better properties than OCSP stapling. (e.g. require verifier caching)

Kyle: There are known better techniques for these problems (cryptographic accumulators for example, published on chain).

...: The goal is to hide infromation about the indexes of certain credentials. But, these were ruled ou infavor of a bit list

...: to avoid complexity. I think this tradeoff is okay, but if we're going to go to production, bitlists actually mgiht not

...: be sufficient once these things go live.

Christine: re Jeffery's comment about the OCSP approach, my understanding is that the trend for PKIs is towards CRLists. WHy favor OCSP here?

Jeffery: OCSP was originally designed for browsers to check that certs weren't revoked. This doesn't work. OCSP stapling allowed servers to do the same check and bundle the result with their certificate. This does work, but is equivalent to just having a short-lived certificate, and the CAB Forum has recently (https://cabforum.org/2023/07/14/ballot-sc-063-v4make-ocsp-optional-require-crls-and-incentivize-automation/) adopted short-lived certificates instead.

...: This is a different dimensoin for short lived credentials, which is a supported approach

...: Both of these have different privacy properties from CRLists

Nick: I have a list of issues, if others could check them, that'd be great.

...: but if we want to puruse other designs, that'll be a large amount of new work

#### DeviceOrientation has a new review request.

https://github.com/w3cping/privacy-request/issues/128

Nick: Needs a new review. Pete will review, but other reviewers would be welcome, definitely fingerprinting relevant

* MathML has a new review request

https://github.com/w3cping/privacy-request/issues/130

Nick: This is markup language, first time this has come up. Needs a reviewer

### 3. Announcements / updates

* Privacy Working Group charter updates

Two formal objections regarding work items appear to be resolved. One
formal objection has been made public. The Team is working on it.

We can continue with the PING charter in the meantime, and normative
items can continue in PrivacyCG, or other CGs.

* Credentials considerations

https://github.com/w3cping/credential-considerations

There is sustained interest from WICG in coming up with a more
thorough and consolidated list of privacy and security requirements
for presentation of credentials. So, a reminder about this repo and a
call for issues and co-editors.

* Automotive privacy

The Automotive Privacy Principles Community Group may generally be of
interest to you all, and is responsive to our recommendations in doing
privacy reviews of related automotive specs:
https://www.w3.org/community/autoprivacy/

