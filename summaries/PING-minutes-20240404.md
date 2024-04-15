# Privacy Interest Group (PING) meeting, 4 April 2024

## Attendees 
- Pete Snyder (Brave)
- Nick Doty (CDT)
- Anil John (DHS)
- Jeffrey Yasskin (Google Chrome)
- Philippe Le Hegaret (W3C)
- Simone Onofri (W3C)
- Joshua Ssengonzi(Article 19/DefendDefenders)
- Walter Rudametkin (Inria/University of Rennes)
- David Waite (Ping Identity)

Apologies: 
 * Joey Stanford - meeting conflict
   * Will review the Ethical Web Principals items and provide async feedback

Chair: Nick

Scribe: Nick, Pete


## Agenda

###  1. Introductions, Code of Conduct

https://www.w3.org/policies/code-of-conduct/

> Ensure that everyone who participates is treated equitably and with respect.

Anil, DHS, with an interest in privacy and identity

Walter, INRIA, professor working on privacy, fingerprinting, ads and tracking

Simone, new W3C staff on security, building a security group as a sibling to PING

### 2. Privacy reviews: ARIA, MathML

#### ARIA 
https://github.com/w3cping/privacy-request/issues/131
https://www.w3.org/TR/2024/WD-wai-aria-1.3-20240123/

Reviewer: Nick

Nick: rereview from a previous PING review from an earlier version.
…: in the past concerns have been around trying to prevent pages from learning if people are using assistive techinologies
…: this is difficult. https://github.com/w3c/aria/issues/1371
…: This doesn't change much, but how events are handled have changed.
…: There is a new event for when parts of the page change, so that screen readers and similar can be notified about changed page content.

Pete: whats the diff between this a mutation observer

Nick: spec doesn't say how notifications / events are sent when pages change, just that there must be a way

PHL: DOMAttribute observer and related are similar to mutation observers

Nick: We should confirm then, PHL will

Jeffery: https://www.w3.org/TR/core-aam-1.2/#mapping_events is also new


#### MathML

https://github.com/w3cping/privacy-request/issues/130
https://www.w3.org/TR/2023/WD-mathml-core-20231127/

Reviewer: Pete

Pete: minor update. presenting LaTeX-style equations, things that are hard to lay out in text. spec often recommends doing what LaTeX does :)
... no particular privacy concerns. sometimes specs like this introduce privacy issues around fonts. but this just refers to CSS, and often use the default math font (or the default fantasy font)
... as a result, browser just uses default font, or downloads through the normal means.

### 3. Privacy review requests: Ethical Web Principles, group charters

https://github.com/w3cping/privacy-request/issues/132
https://www.w3.org/TR/2024/DNOTE-ethical-web-principles-20240319/

Nick: new requests for privacy review. The Ethical Web Principals doc comes from TAG, that defines principals and guidance for work done across all of the W3C.
…: TAG is interested in putting this document through wide review, on statement track
…: There is some privacy relevant principals, but its not all privacy.

Pete: already started review and filed issues

Nick: Joey will review


https://github.com/w3cping/privacy-request/issues/133
https://drafts.csswg.org/css-view-transitions-2/
https://github.com/WICG/view-transitions/blob/main/cross-doc-explainer.md

Nick: We also need a review for CSS View Transitions v2

Pete: I think i reviewed v1
previous review: https://github.com/w3cping/privacy-request/issues/107

PHL: There are significant changes so another review would be good, including a same origin requirement for controling transiton display

Nick: Chairs will reach out

https://w3c.github.io/sustyweb/wg/charter.html
https://w3c.github.io/smartcities-workshop/draft-charter/index.html
https://w3c.github.io/charter-drafts/2024/svg-wg.html

Nick: New charters also need review

PHL: 3 charters are under review currently (see above).  2 might not be important
…: Sustainable Web group is giving guidelines for the web, and is a new direction for the W3C.
…: Second, there is a new interest group for "small cities", but they're not doing standard work so maybe not as much of a concert.  Reviews still welcome
…: Third, the SVG charter, which I think probably also doesn't need a review (the specs are mostly in maintaince)

Jeffery: re sustainable web, no concerns with the charter, but draft spec is very broad, and touches on privacy concerns.
…: The charter seems to rule out a lot of whats in the draft spec too.
…: Would be good to review.
…: For the smart cities charter, there are a lot of risks, so interst group should be aware of them, even if not doing spec work

Nick: I also have concerns with sustainability. Group is not just thinking about enviornmental sustainability, but other things like corp governance, etc.
…: Seems very broad

PHL: We ask groups to have sec + priv sections in their own documents, so we encourage others to consider privacy.
…: but point taken, that privacy guidance should come from privacy groups, not the sustainable web group

Lubna: I work on AI and sustainability, and privacy is an important part of sustainability.
…: this gets more complicated with smart cities. Its important to have privacy considered across all work

Nick: Jeffery, can you help Nick look at the charter, and figure out what the right role for the sustainability group is in privacy discussions.

Jeffery: Google will already be giving comment on the charter, so can share that

Nick: re Smart Cities, is there any action needed other than urging them to consider privacy?

Jeffery: Maybe no further action needed

PHL: Group says they will consdier privacy

Nick: maybe no action needed for PING, AC reps will already be looking at it


### 4. Digital credentials

#### Potential Working Group charter change

https://github.com/w3c/strategy/issues/450
Threat modeling, for privacy and security?

Nick: there is a [proposal](https://github.com/w3c/strategy/issues/450) to add a new work item to the federated identity WG, to add a new API to handle additional kinds of credentials
…: this will be discussed at the AC meeting. I want to mention here bc it would be good for the WG to have a plan for handling privacy issues before adding this new work item
…: Charter will also need other changes to make the new work item fit.

Pete: These don't seem like federated credentials. this is just for mdocs?

Jeffrey: a more general API for providing access to mdocs, verifiable credentials or any other format. some of it is driven urgently by centralized actors, like state-issued credentials. but it could be anyone with a website, which is the connection to federated identity.

Pete: but if the main use case is government-issued, which is more centralized, maybe it's not a strong fit.

David: "federated" terminology is primarily to distinguish from a centralized single vendor to provide identity on the web. w3c wouldn't in any case take on centralized identity of a single identity for the entire web.

Pete: point taken, but if all identity on the web is "federated" then we should drop the term federated.

(comments reordred by scribe)

Anil: API would allow a browser to mediate a site accessing credentials in a wallet. Other identitiy types are being considered. Is this understanding correct

Nick: Yes this seems correct. There could be multiple wallets

Anil: There are privacy concerns. One question is how do sites present information about what informaiton is in each wallet, and the privacy implications of the API. This is a general identity mediation API

PLH: The group is only chartered to work on federated credential management. Charter would need to change signifigantly to incorporate new API. There will be conversation at AC meeting and the IIW

Nick: I want more feedback to make it possible for the browser to protect users againt abusive credential requests

(moving discussion again)



Origin/verifier lists, trust marks or other verifications
* https://github.com/WICG/digital-identities/wiki/2024-02-21-Meeting-Notes#follow-up-discussion-limit-access-to-the-api-based-on-known-allow-listed-origins-59
* https://github.com/WICG/digital-identities/issues/59

Nick: Next topic is allow lists for who can request what kinds of identification
…: for example, maybe only certain origins should be able to access drivers licenses.
…: That proposal was not popular, but new direction of discussion is what signals can sites or browsers provide users about what sites or parties can request certain credentiials.
…: Group would like our thoughts on what mechanisms could work here.

(re-insert)

Walter: What is the trust model being used in the EU

Nick: I think, memberstates in the EU must give their citizens credentials, and also regulate the credential verifiers, and confirming that only necessary and legit

Simone: Differs by country. In Estonia, tech is managed by the govt w/ a smart card. Spain also does not have a third-parties involved

Walter: Issuer of the credential decides who can verify?

Anil: I dont have an opinion on the EU context, but in the US, dept of homeland security, the US is consdiering verifable crendetials for manaing crdentials.
…: US does not have a qualified verifier list. There is no US list for who the issuer trusts to verify credentials.
…: private sector use cases for US govt issued credentials are very broad. Having a US govt curated allow/deny list isn't going to work
…: US govt wants to be able to issue credentials into a wide range of wallets, not just US controlled digitial wallets

Nick: API might need to handle different requirements. Is there additional protections we can design other than a pre-approved allow list, to prevent abusive credential requests
…: for example, maybe a trusted third party could evaluate credential requests. Maybe this kind of information could be relayed to the user agent

PLH: Nothing prevents current sites from asking for any credential they want currently, or just a web form that people enter information into. New API will make it easy to share information

Simone: Goal is to prevent insecure ways of presenting credentials (like webcameras).
…: We might also need to consider protection the wallet from the browser.

Nick: Summarizing: Threat modeling seems useful. Hope you can help with that Simone. Privacy considerations can be part of that
…: Second, we wont get to it, but group wants thoughts on what, if anything, shoudl be learnable by the site pre-permission (see below)

### 5. Announcements, and any other business

W3C AC Meeting next week, with human rights, privacy and security to be discussed

Automotive Information Privacy Architecture
https://lists.w3.org/Archives/Public/public-autoprivacy/2024Mar/0001.html

