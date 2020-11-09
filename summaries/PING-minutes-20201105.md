# Privacy Interest Group meeting (5 November 2020)

## Attendees 

* Peter Snyder (PING Co-Chair)
* Sam Weiler (W3C/MIT)
* Christine Runnegar (Co-chair) 
* James Rosewell (51Degrees)
* Theresa O'Connor (Apple)
* Sean Harrison (Google)
* Paul Jensen (Google)
* Nick Doty (UC Berkeley)
* Joel Meyer (OpenX)
* Tara Whalen (Cloudflare)
* Wendell Baker (Verizon Media)
* Theodore Olsauskas-Warren (Google)
* Michael Klebar (Google Chrome)
* Eric Mwobobia (ARTICLE19) 
* Alex Cone (IAB Tech Lab)
* Brad Lassey (Google)
* Terri Oda (Intel)

Scribe: Christine

Pete: May be brief meeting due to unexpected issues

## Privacy reviews

### 1. CSS Conditional 3

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

Privacy and security considerations section: https://drafts.csswg.org/css-conditional-3/#priv-sec

Answers to the Self-Review Questionnaire: Security and Privacy: w3c/csswg-drafts#5567

Changes since 2013 CR: https://drafts.csswg.org/css-conditional-3/#changes

The WG has advised that they would prefer responses and discussion to happen on that issue, but they have invited us to open other issues on that GitHub for any substantive issues discovered.

#### Discussion

Pete: Assigned to Jeffrey, not available to discuss right now, so we move to next call.

### 2. Web Authentication Level 2

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

Pete: Assigned to Pranjal. Large spec. Needs more time and more eyes to review. Pranjal would appreciate someone to tag-team with him on this. Volunteers? If not, I can help him.

(no volunteers during call)

## New Review Requests 

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

#### Discussion

Pete: Next person on the review list is Nick. Is anyone familiar with the spec able to take on the review? Nick?

Nick: Depends on the timeline. I don't have a lot of time to do a review now, but I can do early next year.

Pete: We will discuss offline and if time does not work, we will assign someone else from the list.

### 2. CSS Sizing Level 3

#### Background

Specification: https://www.w3.org/TR/css-sizing-3/

The CSS module defines the various sizing properties and concepts used throughout CSS.

New features since CSS2 are summarized in https://www.w3.org/TR/css-sizing-3/#changes-3

The WG advised that the specification is in the “almost CR” stage of development, so they expect it to transition, in more or less its current form, after completing horizontal review.

Privacy and Security Considerations section: https://www.w3.org/TR/css-sizing-3/#priv-sec

Answers to Self-review: Security and Privacy Questionnaire: https://lists.w3.org/Archives/Public/public-privacy/2020OctDec/0021.html

The WG has asked that we raise any issues in the csswg GitHub repo: https://github.com/w3c/csswg-drafts/issues

#### Discussion

Pete: Small spec. Anyone interested in taking on the review, and perhaps also the next one?

(no volunteers)

Pete: We put out call on Slack and if not takers, we will go down the list of reviewers.

### 3. CSS Box Model Module 3

Specification: https://www.w3.org/TR/css-box-3/

The specification describes the margin and padding properties, which create spacing in and around a CSS box, and defines a bunch of terminology used throughout the CSS layout specs.

Changes since CSS2 are summarized in: https://www.w3.org/TR/css-box-3/#changes
and basically consist of

* updating the prose to account for vertical writing modes
* defining a shared list of box-edge keywords for use in other properties

There are no new features.

The WG advises that it is really just a redrafting of a very basic piece of CSS2.

#### Discussion

(See re: 2 above)

### Adding Permissions Note

Christine: Spoke to Nick about publishing the permissions blog post as a Group Note, and work with the TAG.

(npd: I think TAG was looking both for this as a standalone document, and then some additions to their design principles doc, a couple of questions and then a reference. So hopefully we can collaborate with them on both parts of that.)

Christine: yes! (TBD)

### AOB

No AOB

