# Privacy Interest Group meeting (19 November 2020)

## Attendees 

* Peter Snyder (PING Co-Chair, Brave Software)
* Sam Weiler (W3C/MIT)
* Christine Runnegar (Co-chair) 
* Pranjal Jumde (Brave)
* Célestin Matte
* Theodore Olsauskas-Warren (Google)
* Sean Harrison (Google)
* Paul Jensen (Google)
* Theresa O'Connor (Apple)
* Roy (Mu Lei) 
* James Rosewell (51Degrees)
* Anthony Molinaro
* Eric Mwobobia (ARTICLE19) 
* Marcal Serrate
* Kris Shrishak
* Pranjal Jumde
* Jeff Wieland
* Lisa LeVasseur (Me2B Alliance)
* Wendy Seltzer (W3C)
* Jeffrey Yaskin
* Shaun Gilmore (Apple)
* Terri Oda (Intel)
* Wendell Baker (Verizon Media)

Scribe: Kris Shrishak

## Privacy reviews

### 1. CSS Sizing Level 3

Reviewer: Lei Mu (Roy)

#### Background

Specification: https://www.w3.org/TR/css-sizing-3/

The CSS module defines the various sizing properties and concepts used throughout CSS.

New features since CSS2 are summarized in https://www.w3.org/TR/css-sizing-3/#changes-3

The WG advised that the specification is in the “almost CR” stage of development, so they expect it to transition, in more or less its current form, after completing horizontal review.

Privacy and Security Considerations section: https://www.w3.org/TR/css-sizing-3/#priv-sec

Answers to Self-review: Security and Privacy Questionnaire: https://lists.w3.org/Archives/Public/public-privacy/2020OctDec/0021.html

The WG has asked that we raise any issues in the csswg GitHub repo: https://github.com/w3c/csswg-drafts/issues

#### Discussion

See below

### 2. CSS Box Model Module 3

Reviewer: Lei Mu (Roy)

Specification: https://www.w3.org/TR/css-box-3/

The specification describes the margin and padding properties, which create spacing in and around a CSS box, and defines a bunch of terminology used throughout the CSS layout specs.

Changes since CSS2 are summarized in: https://www.w3.org/TR/css-box-3/#changes
and basically consist of

* updating the prose to account for vertical writing modes
* defining a shared list of box-edge keywords for use in other properties

There are no new features.

The WG advises that it is really just a redrafting of a very basic piece of CSS2.

#### Discussuion

Roy: No apparent privacy concerns in CSS Sizing and Box module.

Pete: Can you go over the content of the spec?

Roy: Box UI. (1) From privacy perspective, this information is public to the visitors. Easy to access this info with access to css files. (2) This info can be changed and not unique to use as a fingerprint. Both the specs are related.

### 3. CSS Conditional 3

Reviewer: Jeffrey Yasskin

#### Background

Spec: https://drafts.csswg.org/css-conditional-3/

This module contains the features of CSS for conditional processing of parts of style sheets, conditioned on capabilities of the processor or the document to which the style sheet is being applied.

The main extensions compared to CSS level 2 are allowing nesting of certain at-rules inside@media (https://drafts.csswg.org/css-conditional-3/#at-ruledef-media), and the addition of the@supports (https://drafts.csswg.org/css-conditional-3/#at-ruledef-supports) rule for conditional processing.

The specification has been at CR since 2013:

* https://www.w3.org/TR/css3-conditional/
* https://lists.w3.org/Archives/Member/chairs/2013JanMar/0130.html

but due to the long interval since that time, CSS WG is restarting wide review before publishing a Candidate Recommendation Snapshot.

The WG advises that the specification is widely implemented. 

They expect to meet the CR exit requirements in the next few months.

Links and other review information:

Privacy and security considerations section: https://drafts.csswg.org/css-conditional-3/#priv-sec

Answers to the Self-Review Questionnaire: Security and Privacy: w3c/csswg-drafts#5567

Changes since 2013 CR: https://drafts.csswg.org/css-conditional-3/#changes

The WG has advised that they would prefer responses and discussion to happen on that issue, but invited us to open other issues on that GitHub for any substantive issues discovered.

#### Discussion

Jeffrey: This spec is an extension to media query block syntax. Does not define the mediua queries that the browser should support

Privacy worries:

* Support could expose config settings of the browser. Fingerprinting and privacy risk.

* The spec defines a flag as experimental feature. The potentially sensitive settings may not be exposed due to this spec.

* Privacy and security considerations of the spec cover these concerns. 

No further concerns about the spec.

Pete: Where are the things that are to be queried for specified?

Jeffrey: In the media query spec

Pete: Thanks and much appreciated

### 4. Web Authentication Level 2

Reviewer: Pranjal Jumde

#### Background

Spec: https://w3c.github.io/webauthn/

This is an incremental update to WebAuthn Level 1 - https://www.w3.org/TR/2019/REC-webauthn-1-20190304/

WG reported substantive changes since Rec:

* Added new method to allow Discoverable/Resident Credentials Preferred
* New methods added for Attestation Objects
* Added Enterprise Attestation, Apple Attestation
* Added Large Blob storage and credential properties
* Modified cross-origin iFrame usage (only 'get' command)
* Removed unused extensions (they remain in Level 1); also simple tx auth, generic tx auth, UVI, biometrics.
* Clarified some inputs and outputs in extensions
* Fixed some serialization issues with JSON parser

Privacy Considerations: https://www.w3.org/TR/webauthn-2/#sctn-privacy-considerations

The WG welcomes comments on github - https://github.com/w3c/webauthn/issues

#### Discussion

Pranjal: This is an extension to WebAuth level 1. This establishes public key credentials.
   Focussed on a specific part instead of the whole specification.
   
   Positive: Authors have thought about privacy. Included mitigations. This spec has a detailed privacy considerations
   
   4 Issues: (1) Large blob can be used to track users cross-domain. Work in progres to figure out if this is an issue
   (2) Location extension that is included in the spec is unused and there is a work in progress to remove the xtension
   (3) Enterprise auth: Lot more user identification ifo
   (4) Related to large blob. Auth with cross origin.
   [issues filed](https://github.com/w3c/webauthn/issues?q=is%3Aissue+author%3Ajumde)
   
Wendy (as team contact): Thanks for the review. WG discussed the issues yesterday. They thought that large blob was subsumed by other identification opportunities and did not introduce new id opportunities. Re enterprise attestation, Implementers do not want to give UI in the spec. Each implementation had different means of giving users sufficient info.

Pranjal: Having DM with John to resolve the issue. Need to clarify with John before updating on Github.

Pete: What about cross-session tracking? 

Pranjal: Not sure about it. The vector only exists if you are logged in; In the case of completing authentication session.

Sam: The working group has closed all the issues. Usually the chair or someone flags them. They said they will take up the location auth but it is still there. Isn't it?

Pranjal: I can check again

Wendy: I think it is gone. I don't see it in [Level 2](https://www.w3.org/TR/webauthn-2/)

Sam: Large blob?

Pranjal: There is still some confusion between how I see it and how the tea sess it.

Sam: Enterprise tracking?

Pranjal:

Sam: Going to reopen the issues.

Pete: Spec had some functionality to send the strength to the website. 

Pranjal: this falls into attestation terms. There is no indirect where the amount of info sent. 

Pete: Geo ID is per session?

Pranjal: Not sent with every request.

## How the issue tracker works

Sam: Issues in our tracking repo and WG repos are linked with a link preceeded by a 'section marker' (in our tracking repo)

Example: https://github.com/w3cping/tracking-issues/issues/48

Sam: If they don't have the section mark, they are not linked.  If you manually create tracking issues, use the weird special syntax, or ask Team for help.  Sam will fix the tracking issues Pranjal opened (no fault to Pranjal - we haven't explained this magic). 

## Upcoming Reviews

### 1. Accessible Rich Internet Applications (WAI-ARIA) 1.2

#### Background 

Specification: https://raw.githack.com/w3c/aria/2020-09_CR/index.html

The specification provides a framework to improve the accessibility and interoperability of web content and applications.

Changes since ARIA 1.1 : https://raw.githack.com/w3c/aria/2020-09_CR/index.html#substantive-changes-since-the-last-public-working-draft

The WG reports that changes mostly consist of the addition of roles to get closer to parity with HTML to allow the creation of accessible Web components.

This specification is in the “almost CR” stage of development, so the WG expects it to transition, in more or less its current form, after completing horizontal review.

The WG reports that they "do not have a privacy and security section as there was no content to add".

Answers to the Self-review: Security and Privacy Questionnaire: https://lists.w3.org/Archives/Public/public-privacy/2020OctDec/0024.html

They have asked that we raise any issues in the ARIA GitHub repo: https://github.com/w3c/aria/issues

### 2. (new) DOM Standard

#### Background

Horizontal review of the commits of the DOM Standard between 19 June 2019 (b5eac4d) and 15 June 2020 (ad06a4c) requested by the HTML WG 

Link to commits: https://github.com/whatwg/dom/commits/master?before=ad06a4c686a62a2a0f175125932200930364c170+35

The WHATWG published a new Review Draft of the DOM Standard on 15 June 2020. The HTML WG plans to take this Review Draft to W3C Recommendation in 2021.

The WG has requested that Issues identified during wide and horizontal review be filed directly on the WHATWG HTML repository. They have also asked that we send a pointer to the place where we track issues by email to public-html@w3.org.

They also advise that they expect issues to be opened, discussed, and resolved in WHATWG space, but the HTML WG can provide an escalation point if one is needed. The WHATWG FAQ explains how to raise issues here: https://whatwg.org/faq#adding-new-features.

The WG plans to open the CFC to adopt the HTML Standard Review Draft as W3C CR in January, so they request that the review be completed by 29 December 2020.

#### Discussion

Pete will have a look at this. If anyone else can have a look, inform Pete.

### Administrivia: call coordinates & Privacy CG

Sam: Every Thursday people who want to go for Privacy CG come to this meeting. Inform Sam if the confusion can be eliminated. (Note from Tanvi: Same thing happens on the other end - people who want to go to PING, end up in Privacy CG zoom)







