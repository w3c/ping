# Privacy Interest Group meeting (21 January 2021)

* Peter Snyder (PING Co-Chair, Brave Software)
* Sam Weiler (W3C/MIT)
* Christine Runnegar (Co-chair) 
* Kristen Chapman (Salesforce)
* Theodore Olsauskas-Warren (Google)
* Terri Oda (Intel)
* Matthew Finkel (Tor)
* Kris Shrishak
* Jonathan Kingston (DuckDuckGo)
* Sean Harrison (Google)
* Joe Genereux (Brave)
* Jeffrey Yasskin (Google Chrome)
* Shivan Sahib (Salesforce)
* Erik Anderson (Microsoft)
* Melanie Richards (Microsoft)
* Wendell Baker (Verizon Media)
* Wendy Seltzer (W3C)
* Nick Doty (UC Berkeley)
* Theresa O'Connor (Apple)
* Sam Macbeth (DuckDuckGo)
* Eric Mwobobia (ARTICLE19)
* Rob van Eijk (FPF)

Scribe: Sam

## Privacy reviews

### 1. Payment request API (call for wide review)

Reviewer: Theodore Olsauskas-Warren (Google)

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

Theodore: I work on Chrome; web platform privacy.  Payment Req API makes browser more active part of merchants and payment handling.  Next step up from auto-fill.  In general, privacy-positive.  This is the glue layer defining data flow between merchant and payment handler.  There are two draft specs for payment handlers: basic card and "url based".  "basic card" is a drop-in replacement for auto-fill.  "web based" is more interesting; have registered as service workers.  e.g. apple pay.  or cryptocurrency things.  Capabilities in handlers important.

Two compartments to dataflow.  UA->merchant and back; and merchant->UA->payment handler and back.

[Address privacy issue](https://github.com/w3c/payment-request/issues/842)

Issue Sam raised re: address.  Only a Boolean requested - entire address.  Facility allows partial blocking, but site can only request the full address  This regresses the status quo.  e.g. a merchant that needs some info - e.g. state - but not full address.  But this model gives whole address unless UA has redacted part.  We requested a more granular way to request address.  The WG has a proposed fix but it has stalled.  Q to PING: proposal maintains option to request whole and adds option to ask piecemeal.  I chimed in on the issue.  What do we think of allowing a spec to transition to a less privacy preserving state in the hopes that it might later transition to more-privacy-preserving?

Christine: You and I are in agreement.  It's a bad idea to default to w/s gets everything.  Should be the other way around.

Theodore: we should make privacy-preserving the easy path.

Pete: re: a spec moving to Req in less privacy-preserving state.  This is a bad pattern, especially for issues that have been raised well in advance.  That would be a bad pattern that we should discourage WG from.  

Theodore: So, what next?

Pete: I'll follow-up with folks.  In general, note issue as "privacy-requires-resolution".

[Spec is silent on its role in facilitating arbitrary communication between top level contexts](https://github.com/w3c/payment-request/issues/936)

Theodore: The above was data flow UA-> merchant.  Now let's look at UA via payment handler, esp. for URL-based.  Int he current draft, they're registered as Service Workers but also have access to a top-level context.  The set of data transferrable is arbitrary.  Space to send anything back and forth.  This is a vertical slice of @@.

Spec is silent about this.  Is this required for facilitation?  I think so; payments are inherently high trust, high info flow.  

Hard to apply a hard limit of what data can flow.  Places a higher burden on Payment Handler spec.  Pete raised an issue about this.  Maybe it should be treated as a 3rd party iframe?  Spec needs to call out its place in this.  Need mitigations in other specs, e.g., payment handler.

Is that a win?

I think it's good to call this out.

Christine: I understand the need for info flow; worried about abuse.  You propose either restricting it in spec or making it clear that arbitrary transer happens here and make mitigations elsewhere.  Better to engineer protection. How can be we sure that mitigations come to fruition?

Theodore: @2.  Payment Handler spec is the correct place

Pete: Need first party context because high trust?  why?

Theodore: do we need the capability for arbitrary data xfer?  I can see the argument for yes.  @3

Pete: I'll follow up on issues.

Sam: Related to Christine's comment, how well do we understand the mitigations proposed in the payment handlers spec.

Theodore: Chrome's implementation suggests "badly"

Sam: If we don’t know how this will be mitigated in the future, it seems bad to let the issue go

Theodore: The spec seems good, understanding of the spec seems lacking

Sam: Can you be more specific about the mitigations?

Theodore: I mentioned one in my issue.  The UA provides UI to select the handler.  I am worried about drive-by attacks; requiring interaction seems like a good mitigation. My opinion could be changed.  It may be a challenge to convey risks of top-level identifiers.

Nick: I'm concerned re: drive-by.  Wouldn't want a feature nominally for payments to be used for silent, drive-by communication.  Sounds like you've thought about it.  Don't we want some of those limits in this spec?  e.g., what is communicated when payment request is initiated, e.g., user involvement. 

Theodore: we're in agreement that we need mitigations, just not sure where they should be.  We need a normative control here.  

Nick: I'll follow-up on the issue.  Will this apply to any payment handler in future, or is this all about the payment handler spec itself? 

Theodore: I don't think we'll see a new one for a while, after the current two.

Sam: returning to the address issue, the WG has said no one is interested in implementing. is there an implementor that’s willing to request less information. 

Theodore: I’m not sure

Christine: I wonder if media outlets interested in GPC - ones that take subscriptions online - might be interested.  

Theodore: good idea.

Wendy: Thank you for the review.  Re: procedure, part of why this is difficult is that we're doing two things at once: 1) identify issues and 2) help WG toward a resolution, taking into account willingness to implement.  Important to distinguish those two phases, then figure out which are critical to solve when and how.  Happy to help figure out where they go procedurally.  

Theodore: add weight to the issue I opened.

Sam: and to the address issue.

### 2. Web Neural Network API (early review request)

Reviewers: Christine Runnegar (Invited Expert) and Kris Shrishak (Invited Expert)

#### Background

The Web Machine Learning Community Group requested an early privacy review on 10 December 2020.

Spec: https://webmachinelearning.github.io/webnn/

Background from the WG: This request is a heads-up. There's work in progress to form a Web Machine Learning Working Group [1] following the workshop recommendation [2] to start formal standardization work on the basis of the Web Neural Network API [3], an API currently incubated in the Web Machine Learning Community Group [4].

Explainer: https://github.com/webmachinelearning/webnn/blob/master/explainer.md

To facilitate early feedback gathering, the CG has opened an issue in their GitHub repo for the self-review questionnaire responses. They welcome our feedback there [5].

[1] https://lists.w3.org/Archives/Public/public-new-work/2020Oct/0001.html
[2] https://www.w3.org/2020/06/machine-learning-workshop/report.html
[3] https://webmachinelearning.github.io/webnn/
[4] https://webmachinelearning.github.io/
[5] https://github.com/webmachinelearning/webnn/issues/119

#### Discussion

Christine: This is earlier than many reviews; it's still in the CG, though they're about to get a WG.  They had a workshop last year; report focuses on privacy.  

Kris: The soec makes scaling of neutral nets more convenient.  So, WebApps can compile and run neural networks in the browser.  

First concern: no privacy and security considerations section(s).  They'll follow up.

Second concern: performance adaptation.  concern re: device ID if this is passed to JS framework.  Spec does not describe if JS has access to this.  Needs to be more explicit. 

Third: timing attacks.  Because they rely on diff HW and SW; if implementations different, chance for fingerprinting.  Specific issue re: matrix multiplication, implemented differently by ARM.

Use cases, e.g., face recognition, have privacy implications.  switching on microphone/camera.  

Christine: some use cases might be regarded as being privacy-invasive.  But they have one use case, 2.1.2, semantic segmentation, to protect privacy of video conference participant.  Would be nice to have more use cases that are privacy-enhancing.  Good that this is in secure contexts.  

Q for group might be how they handle permissions?  Or, how they deter sites from using these power-intensive capabilities?  

Is this limited to first parties, or would third party frames have access to API?

Unsure if everything running client side - should API mandate client-side only processing?

Tess: what is the scale of the fingerprinting risk?  e.g., Apple's products are fairly homogenous.  Is it more fine-grained than "class of device"?

Kris: e.g., is there a GPU?  ARM implementation gives diff timing info.  
Open issue: https://github.com/webmachinelearning/webnn/issues/85

Nick: are these about pre-trained networks?  or are they looking at learning?  Quite distinct privacy implications.  

Kris: they don't mention training

Sam: this seems like a basic, low level building block (a la cos()), and its difficult to evaluate the privacy implications until the rest of the system is defined.  Does that seem correct

Kris: yes correct

Sam: other than potential for device identification, are there other concerns at this level. Is this API equivalent to computations that could already be done in JS?  Or is there more?

Kris: yes, seems equivalent to just, alternative implementation of computation 


### 3. CSS Color Adjustment Module Level 1

Reviewer: Matthew Finkel (Tor)

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

Matthew: adds 4 types of functionality: color adjustment - to force a certain color scheme, to control styling of page; color scheme - tell UA what sort of scheme you prefer (normal, light, dark); color adjustment - from author to UA re: whether it's okay for UA to adjust - use case is for printing when styling is not useful; force color modes - to indicate to w/s authors preference of UA for e.g., high contrast.

The Security and Privacy considerations section calls out that force colors and color schemes lead to additional fingerprinting because they leak preference of UA to w/s author in JS.  I felt that info revealed, e.g, in force colors - was not only a fingerprinting risk but also revealed to w/s that someone might have need for accessibility.  

This was raised in an [issue](https://github.com/w3c/csswg-drafts/issues/5710) a couple of weeks ago.  Not planning changes.  

I commented on issue.

Correctness of the values returned could be permissioned.  

Sam: why doesn't the website just ask for the color preference?

Matthrew: so that sites can learn easier

Sam: Why not handle through CSS conditionals?

Matthew: that is the current implementation, but that still leaks the preference 

Jeffrey: we [discussed this within Chrome](https://groups.google.com/a/chromium.org/g/blink-dev/c/hkjRPJ1-Ruk/m/zbo12-LbAwAJ).  This is already exposed.  System colors visible to CSS in computed style.  The cat is out of the bag.  We could change getComputedStyle to lie (Nick Doty's idea) but that would have to be across many APIs.  Shipping this doesn't make it harder to fix later.  

[Discussion cut short because of time running out]

[Side discussion: "is there a place being tracked about updating getComputedStyle across multiple specs?"  and "I was curious about that, too. I'm also curious about whether there is a collection of all specs that introduce fingerprinting, so we have a single place where we can evaluate the interaction across them "]

### 4. Custom Highlight API Module Level 1

[skipped this today]

Reviewer: Matthew Finkel (Tor)

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


### 5. Decentralized Identifier Specification v1.0

[skipped this today]

Review: Joe Genereux (Brave)

#### Background

Decentralized identifiers (DIDs) are a new type of identifier that enables verifiable, decentralized digital identity. A DID identifies any subject (e.g., a person, organization, thing, data model, abstract entity, etc.) that the controller of the DID decides that it identifies. In contrast to typical, federated identifiers, DIDs have been designed so that they may be decoupled from centralized registries, identity providers, and certificate authorities. Specifically, while other parties might be used to help enable the discovery of information related to a DID, the design enables the controller of a DID to prove control over it without requiring permission from any other party. DIDs are URIs that associate a DID subject with a DID document allowing trustable interactions associated with that subject.

Spec: https://w3c.github.io/did-core/

Answers to Self-Review: Security and Privacy Questionnaire: https://docs.google.com/document/d/1c36r86oI7q4qv0YKVsu0zlNiMwWTqCfWWReAkg3gd2A/edit#

Issues: https://github.com/w3c/did-core/issues

### Privacy review questions

[skipped this today]

### AOB

Pete: thank you for reviews.

See https://www.w3.org/blog/2021/01/privacy-interest-group-ping-2020-year-in-review-and-thank-yous/

Privacy CG having Storage Access API meeting after this: https://github.com/privacycg/meetings/issues/11#issuecomment-763193259


