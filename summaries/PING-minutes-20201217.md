# Privacy Interest Group meeting (17 December 20200)

## Attendees (sign yourself in)

* Peter Snyder (PING Co-Chair, Brave Software)
* Sam Weiler (W3C/MIT)
* Christine Runnegar (Co-chair) 
* Kris Shrishak
* Matthew Finkel (Tor)
* Kristen Chapman (Salesforce)
* Wendy Seltzer (W3C)
* Joey Salazar
* Shivan Sahib (Salesforce)
* Wendell Baker (Verizon Media)
* Jeffrey Yasskin
* Harneet Sidhana
* Anthony Molinaro
* Shaun Gilmore
* Terri Oda (Intel)
* James Rosewell (51Degrees)

Scribe: Kris Shrishak

## Privacy reviews

### 1. DOM standard (horizontal review)

#### Background

Horizontal review of the commits of the DOM Standard between 19 June 2019 (b5eac4d) and 15 June 2020 (ad06a4c) requested by the HTML WG 

Link to commits: https://github.com/whatwg/dom/commits/master?before=ad06a4c686a62a2a0f175125932200930364c170+35

The WHATWG published a new Review Draft of the DOM Standard on 15 June 2020. The HTML WG plans to take this Review Draft to W3C Recommendation in 2021.

The WG has requested that Issues identified during wide and horizontal review be filed directly on the WHATWG HTML repository. They have also asked that we send a pointer to the place where we track issues by email to public-html@w3.org.

They also advise that they expect issues to be opened, discussed, and resolved in WHATWG space, but the HTML WG can provide an escalation point if one is needed. The WHATWG FAQ explains how to raise issues here: https://whatwg.org/faq#adding-new-features.

The WG plans to open the CFC to adopt the HTML Standard Review Draft as W3C CR in January, so they request that the review be completed by 29 December 2020.

#### Discussion

Pete: Only small changes; no significant privacy concerns that need to be flagged.

No comments

### 2. Audio output devices API (call for wide review)

#### Background

The WebRTC WG issued a call for wide review.

Spec: Spec: https://www.w3.org/TR/2020/CRD-audio-output-20201127/

#### Discussion

Pete: Purpose of the API: allowing access to audio devices from Javascript API; taking device IDs and plugging it into a new property on the page. No serious privacy issues. Some things are ambiguous and implicit. Needs to be made explicit. The WG has decided to move towards browser-based device picking. It is worth figuring out how this will be figured out. Maybe they will consider this in the next version

Pete: Second issue: If the approach is to taint device ID, then it should be mentioned in the spec. If it is about the audio output, then that should be mentioned. Currently, it is not discussed. Kris, you also had a look, did you have any comments?

Kris: Broad concerns; nothing specific that the spec authors can address.

### 3. Accessible Rich Internet Applications (WAI-ARIA) 1.2

#### Background 

Specification: https://raw.githack.com/w3c/aria/2020-09_CR/index.html

The specification provides a framework to improve the accessibility and interoperability of web content and applications.

Changes since ARIA 1.1: https://raw.githack.com/w3c/aria/2020-09_CR/index.html#substantive-changes-since-the-last-public-working-draft

The WG reports that changes mostly consist of the addition of roles to get closer to parity with HTML to allow the creation of accessible Web components.

This specification is in the “almost CR” stage of development, so the WG expects it to transition, in more or less its current form, after completing horizontal review.

The WG reports that they "do not have a privacy and security section as there was no content to add".

Answers to the Self-review: Security and Privacy Questionnaire: https://lists.w3.org/Archives/Public/public-privacy/2020OctDec/0024.html

They have asked that we raise any issues in the ARIA GitHub repo: https://github.com/w3c/aria/issues

#### Discussion

Shivan: This spec defines how users of assisted technologies can better browse the Web. No big privacy issues. Just static HTML that is served. No state that can be stored on the client. But, there are a couple of known attacks that allows the detection of the screen readers (identifies whether or not the user is using a screen reader). Effort can be made to make the attack passive. Knowing that there is a weird button, it can help the user know. This is not an attack on the spec, but it should not be hidden. A privacy consideration section should be added and the attacks should be stated. Not much enthusiasm from the spec authors. 

Pete: There was an email that said that the next spec version will consider the issues. Is this critical enough to be addressed in this draft?

Shivan: This is a legacy issue, but the spec updates roles. Nevertheless, what the diff is, is unclear. Not super critical.

Pete: Needs-resolution issue or please consider this issue?

Shivan: Please consider this.

Jeffrey: It's cheap to add words to a privacy considerations section, so we should offer some text and ask them to add it. Making screen readers indistinguishable from non-screen-readers is much harder and shouldn't hold up ARIA-1.2.

Sam: Shivan, have you opened an issue yet?

Shivan: Yes, https://github.com/w3c/aria/issues/1371

Sam: Give me a link or number to find it...found it.

Sam: We are going to have tooling changes so that anyone can add tracking labels.

## Upcoming reviews

### 1. Payment request API (call for wide review)

#### Background

The Web Payments Working Group made a call for wide review on 2 December 2020.

Spec: https://www.w3.org/TR/2020/CR-payment-request-20201203/

The document was published as a Candidate Recommendation Snapshot.

Reported changes since the last publication:
Changes since last publication

Substantive changes to the Payment Request API since the 9 July 2018 version are as follows. The complete list of changes, including all editorial changes, is viewable in the commit history. Key set of changes are viewable in the Changelog.

* Added support for notification when the user selects a payment handler, but before confirming payment. This allows merchant to update totals, validate acceptance, etc.
* Added support to notify site of billing address selection. This allows a merchant to update a total (e.g., for VAT in Europe). To enhance privacy, only some billing address data is returned to the merchant as long as the user has not confirmed payment.
* Added support for retry() and fine-grain error reporting to the user.
* Clearer definition of canMakePayment() and worked to align implementations. canMakePayment() does not reveal whether payment handler is primed to pay.
* Removed languageCode and regionCode from PaymentAddress.
* Removed currencySystem.
* "Payment request is showing" boolean now attached to top-level browsing context. Previously, only a single payment UI was allowed to be shown at a time across the whole browser. This now allows multiple browser tabs to show a payment UI at the same time (for those payment handlers able to support it).
* Integrated with Permissions Policy.
* Defined handling of multiple applicable modifiers.
* Removed support for merchant validation because of lack of multi-implementer support.
* Deprecated allowpaymentrequest attribute.
* Calling show() now consumes the user activation.

#### Discussion

Pete: There have been comments that there is a difference between API structure and the substance that has been communicated. Beyond that, we have not reviewed this spec. Anyone who has particular interest in reviewing?

Sam: Follow up with Lisa and Erik M. - they had taken ownership of the address privacy issue I filed before.  https://github.com/w3c/payment-request/issues/842#issuecomment-473907871

Pete: I will talk to them.

### 2. Web Neural Network API (early review request)

#### Background

The Web Machine Learning Community Group requested an early privacy review on 10 December 2020.

Spec: https://webmachinelearning.github.io/webnn/

Background from the WG: This request is a heads-up. There's work in progress to form a Web Machine Learning Working Group [1] following the workshop recommendation [2] to start formal standardization work on the basis of the Web Neural Network API [3], an API currently incubated in the Web Machine Learning Community Group [4].

Explainer: https://github.com/webmachinelearning/webnn/blob/master/explainer.md

To facilitate early feedback gathering, the CG has opened an issue in their GitHub repo for the self-review questionnaire responses. They welcome our feedback there.

[1] https://lists.w3.org/Archives/Public/public-new-work/2020Oct/0001.html
[2] https://www.w3.org/2020/06/machine-learning-workshop/report.html
[3] https://webmachinelearning.github.io/webnn/
[4] https://webmachinelearning.github.io/

#### Discussion

Pete: Christine, I think you said you would be happy to review?

Christine: Yes

Pete: Happy to provide support

Joey: What was this one about?

Pete: Allowing ML operations through Javascript

Christine: Which one did Kris want to look at? (referring to chat in Zoom)

Kris: ML

### 3. CSS Color Adjustment Module Level 1

#### Background

The CSS WG requested a privacy review on 7 December 2020.

Spec: https://www.w3.org/TR/css-color-adjust-1/

Privacy and security considerations: https://www.w3.org/TR/css-color-adjust-1/#priv-sec

Background from the WG: This module introduces a model and controls over automatic color adjustment by the user agent to handle user preferences, such as "Dark Mode", contrast adjustment, or specific desired color schemes.

These features work together with related features in Media Queries 5 https://www.w3.org/TR/mediaqueries-5/ and the system colors in CSS Color 4 https://www.w3.org/TR/css-color-4/#css-system-colors:

* media queries allow the author to query the UA
* color-adjust properties allow the author to give hints to the UA
* system colors allow the author to use colors from the forced palette

Overview and explainer for forced colors mode (corresponds to Microsoft’s “Windows High Contrast Mode”):
https://lists.w3.org/Archives/Public/www-style/2019Apr/0004.html

The spec is in the "Refining" stage of development, per http://fantasai.inkedblade.net/weblog/2011/inside-csswg/process
and is being actively implemented by browsers.

The WG has asked that we raise any issues in the csswg GitHub repo: https://github.com/w3c/csswg-drafts/issues

#### Discussion


Jeffrey: I can talk about this in this call or the next

Pete: Next call so that others can have a look at the spec as well

Jeffrey: One note about color adjustment; Chromium is planning to ship "Forced-color mode" very soon. Fantasai already filed an [issue](https://github.com/w3c/csswg-drafts/issues/5710) about the possible fingerprinting vector in that the forced colors are configurable by the user and are reflected in `getComputedStyle()`. It will be good for this group to have a look so that it can be considered before it is shipped.

Pete: When?

Jeffrey: [M89](https://groups.google.com/a/chromium.org/g/blink-dev/c/hkjRPJ1-Ruk/m/ksYRXedLAgAJ), branch probably in mid-Jan.

Pete: It is unlikely that we'll have a PING meeting before then, but individuals can have a look and provide views.

Jeffrey: Look at <https://groups.google.com/a/chromium.org/g/blink-dev/c/hkjRPJ1-Ruk/m/zbo12-LbAwAJ> and <https://github.com/w3c/csswg-drafts/issues/5710>, and comment there if you have concerns.

### 4. Custom Highlight API Module Level 1

#### Background

The CSS WG requested an initial horizontal review on 8 December 2020.

The CSS WG's Custom Highlight API Module Level 1 was recently published as a FPWD.

Spec: https://www.w3.org/TR/css-highlight-api-1/

Privacy and security considerations: https://drafts.csswg.org/css-highlight-api-1/#priv-sec

Background from the CSS WG: The Custom Highlight API extends the concept of highlight pseudo-elements (see CSS Pseudo-Elements 4 §3 Highlight Pseudo-elements) by providing a way for web developers to style the text of arbitrary Range objects, rather than being limited to the user agent defined ::selection, ::inactive-selection, ::spelling-error, and ::grammar-error. This is useful in a variety of scenarios, including editing frameworks that wish to implement their own selection, find-on-page over virtualized documents, multiple selection to represent online collaboration, or spellchecking frameworks.

The Custom Highlight API provides a programmatic way of adding and removing highlights that do not affect the underlying DOM structure, but instead applies styles to text based on range objects, accessed via the ::highlight() pseudo element.

The CSS WG did not identify any privacy concerns.

Results of application of security and privacy questionnaire: https://lists.w3.org/Archives/Public/www-style/2020Dec/0007.html

The CSS WG has requested that any issues be raised in the csswg GitHub repo, using a separate issue for each concern: https://github.com/w3c/csswg-drafts/issues

#### Discussion

As above.

### 5. (new) Decentralized Identifier Specification v1.0

#### Background

Decentralized identifiers (DIDs) are a new type of identifier that enables verifiable, decentralized digital identity. A DID identifies any subject (e.g., a person, organization, thing, data model, abstract entity, etc.) that the controller of the DID decides that it identifies. In contrast to typical, federated identifiers, DIDs have been designed so that they may be decoupled from centralized registries, identity providers, and certificate authorities. Specifically, while other parties might be used to help enable the discovery of information related to a DID, the design enables the controller of a DID to prove control over it without requiring permission from any other party. DIDs are URIs that associate a DID subject with a DID document allowing trustable interactions associated with that subject.

Draft:
https://w3c.github.io/did-core/

Answers to Self-Review: Security and Privacy Questionnaire: https://docs.google.com/document/d/1c36r86oI7q4qv0YKVsu0zlNiMwWTqCfWWReAkg3gd2A/edit#

Issues:
https://github.com/w3c/did-core/issues

#### Discussion

Pete: Dense spec that is not well integrated in the DOM API. Does someone have a domain expertise on this? I can look at who did the review earlier?

Wendell: This is interesting work. Have a look at who did it last. It is separate from the Web but it is about identity on the Web. We should find the previous advice and use it as a base case. Whether ID should be embedded or not in the Web is still an important issue.

Pete: Agree that this spec should be privacy assisted. Would you be interested in doing the review?

Wendell: Verizon has products in this area. I may have to decline. I will look around if someone can review this spec. This spec should not get off easily as it is a big new direction. We have in the past stated that the Web does not do identity. That is changing.

Pete: I will look up who did the review before and follow up. 

### AOB

Sam: Join PING if you have not.
See buttons at the bottom of:
https://www.w3.org/groups/ig/privacy

Kristen: Does anybody know about the Google research on privacy budget of API?

Jeffrey: I don’t know the current state

Kristen: They say they are just measuring at this stage. Looking our of curiousity, and for any details that might be available.

Terri: As we have time, could we go back to Chrome and look at the color issue?

Matthew: In terms of reviews, do we jump in or is there a process.

Pete: (1) We figure out which people will be best suited for the particular spec (2) There is a list of volunteers and we go down the list. The review is shared in the next PING call. Declare them as privacy relevant or critical and report it to the WG. If you are interested, you can take one up or you can co-review with some assistance.

Sam: Mat, are you expressing interest on being on that list?

Mat: I guess, yes.

Pete: Add yourself at this link - https://cryptpad.w3ctag.org/pad/#/2/pad/edit/XFYXN76vmE+W3BTD3M2pFE0s/

Pete: Going back to Terri. Can you restate the question?

Terri: Somebody wanted to say more about the color issue

Jeffrey: There is a privacy issue with forced-color mode. Users can force web pages to be B/W or use particular colors if they have problems with having too many colors. The page can tell that you are in forced color mode and the colors that you have customised. This can be unique to you and can be sensitive. The [CSS issue](https://github.com/w3c/csswg-drafts/issues/5710) mentions why it's also useful. The question is: how do we trade-off usability and privacy?

Wendell: Reflecting on a discussion from sometime back...about involving new folks. It feels scary to sign up to review. We have the opportunity to involve more people into reviewing in this group... I am involved in the ID thing.. First review is scary and nerve-wracking. We have had several sessions to discuss how we can make it easier for new folks.

Christine: Adding something to what Jeffrey said. The customizable info also tells something about the user and their needs to anyone who observes that information, and perhaps even why they need the customisation. This could be a very personal information.

Pete: From recollection, there is somewhere in the TAG saying that spec should not be able to know whether users use assistive technologies

Jeffrey: It is mentioned in the privacy threat model: https://w3cping.github.io/privacy-threat-model/#hl-sensitive-information

Joey: Yes, in the privacy threat model

Pete: Point taken that this is sensitive information.

Wendy: Thanks to everyone who is reviewing specs and making them privacy preserving. Thank you for getting involved.

Christine: Have a look at the minutes and check if your points have been presented accurately.

Pete: Next PING call...

Christine: 7 January 2021

For more info re: privacy reviews, see:

"special breakout for TPAC on conducting a privacy review" minutes link: https://www.w3.org/Privacy/IG/summaries/PING-minutes-20201023

Here is where we are tracking privacy reviews - https://github.com/w3cping/privacy-reviews


