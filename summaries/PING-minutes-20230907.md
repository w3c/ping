# Privacy Interest Group meeting (7 September 2023)

## Attendees 

* Nick Doty (CDT, co-chair)
* Pete Snyder (Brave, co-chair)
* Christine Runnegar (co-chair)
* plh (w3C)
* Don Marti (Raptive)
* Tom Van Goethem (Google Chrome)
* Isaac Agudo (NICS Lab - University of Malaga)
* Ted Guild
* Eric Mwobobia 
* Carine Bournez (W3C)
* Jeffrey Yasskin (Google Chrome)
* Sam Weiler (W3C)
* Ulf Bjorkengren (Geotab)
* Aram Zucker-Scharff

Apologies: 

Chair: Christine Runnegar
Scribe: Pete Snyder

## Agenda

### 0. Introductions and CEPC

https://www.w3.org/Consortium/cepc/

### 1. Consent handling in the context of the W3C Auto WG VISS spec (with guests from the W3C Auto WG)

See: 
https://www.w3.org/TR/viss2-core/
https://lists.w3.org/Archives/Public/public-automotive/2023Jun/0000.html 

Christine: introductions

Ted: privacy concerns came up during horizontal review, we thought some of the issues were out of scope / our area, but we ack many of the concerns too. THers an article from the Mozilla foundation highlighting the problem.  Cars are similar to a smartphone: you can track folks, there is a lot of data, etc.  We're not trying to come up with a consent management framework (though would be great to align wiht other standadrds bodies if possible) but we want to figure out how to hook into consent systems for metadata

Article shared by Ted: https://arstechnica.com/cars/2023/09/connected-cars-are-a-privacy-nightmare-mozilla-foundation-says/

Consent support proposal: https://rawcdn.githack.com/UlfBj/automotive/ab8ba69b31b101f65f8880665eb432dadc16ca8b/spec/VISSv2_Core.html#consent-support

PR: https://github.com/w3c/automotive/pull/483

Ulf: There is a PR we're considering merging, that would be implemented on a server, exposed to clients (both built into cars, or phones, etc).  Server would have an access control policy to control which clients can access what data.  These access controls/gatekeeper could hook into consent management systems.
…: When server gets a request that requires consent, request would be forwarded to an ECF (external consent framework) that could be in the car or in the cloud.  The framework determines whether consent was given. Consent might have levels (e.g., "yes", "no", "yes but shouldn't leave the car").
…: We think this could be integrated into the spec; it might not fully solve the problem but might go as far as we think we can.

Ted: again, we'd like to align with existing consent management frameworks in standards bodies where possible. (w/in and w/o the W3C).
…: Some cases (like rentals) are tricky cases too.  Already data being collected (for example, with electric vehicles).
…: also want to make sure users are informed about what data is collected, and how policies can be enforced

Christine: Seems like consent systems are binary (w/ the exception of in vehicle).  Have you considered i. more granular controls, and ii. revocation

Ted: Yes, we're hoping theres an existing system to hook into. When sharing informaiton around the car, data would carry with it information about how much consent has been given

Christine: re on device, you might consider the work the machine learning group has done (since they're considering how to handle processing data on device vs on cloud)

Nick: Consent is a large topic, hard to give a concise answer.  I understand you to be proposing a system where devices would advertise their privacy policy, and the client would consult those policies and make decisions
…: however, this model has critics, since that model doesn't answer quetions like "who is setting the policies?".
…: a different model is the Web's permission model. Users are generally asked real time (though users can pre-configure policies as well)
…: W3C/PING also have guidance around how and when and what to be cautious about when designing permission
…: However, these protections generally go away if the client is disloyal, so documentation is important too, as well as audits, etc
…: might be useful to document which software/systems are acting on behalf of the user (i.e., the user agent), even if others in the industry might not follow that model

Policy Decision Point / Policy Enforcement Point is a common design pattern
NIST SP 800.95 is one resource to look at: https://nvlpubs.nist.gov/nistpubs/Legacy/SP/nistspecialpublication800-95.pdf

Adding permissions on the Web:
https://github.com/w3cping/adding-permissions

Permissions API:
https://www.w3.org/TR/permissions/

Ulf: thank you, we'll consider

Ted: If you can send referneces, we'd apprecate it

Christine: there are other groups in the W3C who are working on guidance and general approaches.  I will also share some guidance and principals developed by the mobility group, who have tried to get folks from industry to sign on

https://www.mobilitydataprivacyprinciples.org/


### 2. Privacy WG charter

https://w3cping.github.io/administrivia/2023/charter.html
https://github.com/w3cping/administrivia/issues?q=label%3Acharter

Nick: continuing from previous conversations, the PING charter is expiring soon, and we need a new charter. We're proposing a Privacy working group charter that would both handle horizontal review, but also, in some limited cases, would would to public specificatons too.
…: one issue that came up last time was concerns around haivng to open-ended a scope.  I've listed stated deliverables, which right now would be GPC, bounce tracking mitigations, and attestations
…: this means that if a PrivacyWG wanted to take on other items in the future, we'd need to recharter
…: Do folks think this is the right set of deliverables?  If not, it'd be good to record those concerns and deliveables in GH
…: alternatively, if we don't wanna go in PrivacyWG direction, after TPAC we should figure out an alternative with a horizontal review specific group, and other homes from the discussed deliverables

Don: Im interested in the idea of PING as a subject-matter horizontal review group.  In the private advertising group we've have some similar discussions, also ones around market design concerns/proposals. 
…: maybe it'd be useful to have a market design interest group to handle some issues and to take those issues out of the privacy group
…: by market design i mean putting rules for how markets could work into W3C standards.  For example, how different parties might trade information about users browsing history, or a proposal for advertising auctions w/in browsers
…: so far these kinds of questions have been lumped into privacy work, but this seems like an awkward fit, and more than just privacy
…: simple examples of market design outside the web context: comodities exchanges, spectrum auctions
…: if W3C is going to work on market design, it shouldn't be the same folks doing privacy work

Christine: these don't sound like privacy specs to me, though these have privacy implications.  However, whehter we should have a market design group is beyond my remit

Nick: Other issues than privacy issues come up during privacy reviews (business impact, free expression, etc).  We dont have specific horizontal review processes for these concerns, and should still come up in wide review.
…: we just might not need a formal group for each cateogry of concern (and shouldn't be privacy group)

scope update:
 https://github.com/w3cping/administrivia/commit/6eed4dd53ed253c181a6d1fbadfef79f321e3c33
 
PLH: regarding privacy attestation deliverable, is this only about consent? Nothing is linked to from the charter
…: if this is only consent, seems like we need incubation first

Nick: I listed privacy attestion as a possible deliverable bc it comes up often.  Incubation first, but if / when it got to standardization, we'd need a working group for it

PLH: we should specify we expect incubation first then in the charter 

Nick: good point, thanks

Aram: I support the PrivacyWG proposal


### 3. TPAC 

12 September 2023, 17:00–18:30 Central European Summer Time
 https://www.w3.org/events/meetings/40eb7cef-869b-433a-b749-ad84f95549d0/

https://github.com/w3cping/administrivia/issues/36

Nick: there are issues above for what we plan on discussing during TPAC. The PING Chairs will turn this into an agenda (and send it out probably tomorrow).
…: agenda will include udpates on privacy princiapls, privacyWG work, age verification and credentials work (who have been invited to discuss), would be good to have follow up on privacy reviews too (devices and sensors group)

PLH: re identity work, W3C staff have a proposed charter for identity work, so keep in mind there will be a releated charter coming (FedCM)
…: please look at the breakout chats too, since much of it will be relevant to privacy
…: can still add more proposals and ideas too

Jeffrey: Should we try and organize who goes to what, to maximize coverage?

PLH: see link below for a list of which groups the origanizers think are related to privacy. Though they may overlap

https://github.com/w3c/tpac2023-breakouts/issues?q=is%3Aissue+is%3Aopen+label%3A%22track%3A+privacy%22

TPAC breakouts: https://github.com/w3c/tpac2023-breakouts/issues

### 4. Privacy in charters

See:
https://github.com/w3c/charter-drafts/issues/416

Christine: theres been discussion about what wording should appear in charters, and some though that the existing template isn't clear about whether specs should detail privacy concerns, or mitigate them
…: there is a proposal in the issue about wording

PLH: There are two issues:
…: 1. how to handle updating or changing the charter template
…: 2. specifically what language should appear in the charter template
…: keep in mind that groups can change the template. There was an initial change made, but it needed to be reverted
…: Pete proposed some wording 

Pete: change is that the expectation should be mitigation, not just detailing privacy concerns. would just document what already happens during horizontal privacy reviews.

Christine: Is this a substantive change, or a wording change?

PLH: I think a wording issue. Pete as a propsoal, Sam did too, Nick left a comment. 

Christine: can someone take a look at the issue and suggest a change

PLH: note that the last comment on the issue is off topic


### 5. AOB

PLH: what are your plans for finalizing the agenda? 

Nick: We'll do it tomorrow. Its a short meeting, so hopefully not too many conflicts / requirements for people to show up a particular hour.
