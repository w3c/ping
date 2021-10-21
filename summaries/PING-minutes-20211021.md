# Privacy Interest Group meeting (21 October 2021)

## Attendees 

* Christine Runnegar (PING co-chair)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C/MIT)
* Pete Synder (Brave, PING co-chair)
* Stephen McGruer (Google, guest)
* Aram Zucker-Scharff (The Washington Post)
* Anne van Kesteren (Mozilla)
* Ian Jacobs (W3C)
* Nick Doty (CDT)
* Shivan Sahib (Brave)
* Sanketh Menda (invited expert)
* Brad Rodriguez (Magnite)
* Eric Mwobobia (ARTICLE19) 
* Wendell Baker (Yahoo)

Scribe: npdoty 

### 1. Privacy review of Secure Payment Confirmation (reviewers: Pete and Sam)

* URL of spec: https://w3c.github.io/secure-payment-confirmation/
* Link to privacy considerations: https://w3c.github.io/secure-payment-confirmation/#sctn-privacy-considerations
* Response to self-review questionnaire: https://github.com/w3c/secure-payment-confirmation/blob/main/security-privacy-questionnaire.md
* Explainer: https://github.com/w3c/secure-payment-confirmation/blob/main/explainer.md
* Issues list: https://github.com/w3c/secure-payment-confirmation/issues

Stephen: Secure Payment Confirmation (SPC) wants to bring secure authentication to payments on the web, enabling payment specific use cases not currently enabled by webauthn. let merchants initiate a ceremony on behalf of the bank, in order to keep friction of payment low. bind payment information into the authentication, to satisfy regulations (like showing the user how much money they are agreeing to pay)

Ian: browser UI is presenting natively this information

Sam: example shows user identifiers (name and email address), why are those included?

Stephen: user identifiers are part of webauthn. the bank needs to be able to track which credentials are for which person. this is up to the relying party (the bank), can put any arbitrary data in there.

Ian: this example isn't part of the SPC protocol, it's just from webauthn.

Sam: I don't think it's required to identify the user by webauthn. or call out that it's not necessary in all cases.

(Action Stephen and Ian to look at an example that doesn't require this and/or noting why this information is in the example?)

Sam: How does this interact with partitioned storage? 

Stephen: by design, want to be able to access credentials in iframes. but protected because of a user interaction with the browser.

Anne: webauthn history, delegation was possible, but wasn't clear what the origin was
Ian: and this is the reason for SPC

Pete: does this undo the partitioned identity that browsers are otherwise trying to provide?

Stephen: if you use virtual credit card numbers on different websites in order to protect your identity, but you use the same credential, then the merchant site could figure out that it's the same user. one possible mitigation design that involves salting, but that could also relay extra information to the browser.

Pete: relies on bank to successfully handle the salt.
also applies to cryptocurrency or token transactions, for people with particular privacy concerns

See our issue on this: https://github.com/w3c/secure-payment-confirmation/issues/77

Stephen: the merchant is the third party. you're on the merchant origin, but you're doing an authentication scenario with the bank. the bank can already de-identify you, in that they know you already. but we wouldn't want the merchant to link those payment instruments.

Sam: the bank is returning a list of credential IDs to the merchant, which requires giving some identity from the merchant to the bank. how does the user know which identifier to provide?
Stephen: the user has to provide a payment instrument (credit card, crypto wallet, etc.)

Sam: goal is to have more private payment methods, where the merchant doesn't receive those details in the future.

Ian: is there a flow where you don't identify yourself before making a payment? or at least indicate what you will use to pay?

Sam: crypto payments don't generally require identifying the person paying.

Ian:  ... user picks a card to play with, the bank comes back with some credential IDs. or you click on the paypal button. SPC doesn't care how that's determined.

Pete: take this to GH 

Anne: there is user-facing UI. can it be initiated by third parties or is it restricted to first parties?

Stephen: the UI can be initiated by the page that you are on, but not initiated by the bank/relying party. there is a big UX to show the transaction details.

Anne: can it be triggered by a cross-origin iframe?

Stephen: yes, if the permission policy payment bit is set/delegated.

(Aside: Even though we are saying that the bank is the RP, the RP could be lots of other parties such as the Payment Service Provider of the merchant.)

Pete: can include an image about the bank taht will be showed the UI?

Stephen: merchant provides the transaction details to the browser for the UI, and the same details will be presented to the bank/payment provider.

Ian: decoupling -- the bank provides data about the instrument including an icon, but the merchant could corrupt that. the bank gets the assertion back, and the bank gets a signed copy of what UI/data was shown. if the merchant corrupted the data, then the bank can decide not to approve the payment.

(this was helpful)

Anne: sounds fine, following existing patterns of how permissions should work. confusing that the top-level origin prompts on behalf of your bank. I'm not sure users will comprehend, for example the user might be confused that the address bar is different from the bank that they say is being prompted about.

Ian: agenda for next week, Web Payments WG will be discussing privacy-related topics; joint webauthn meeting; frictionless risk assessment related to third-party cookie deprecation. would appreciate privacy advice to avoid bad pathways. open invitation to talk about privacy developments.

https://github.com/w3c/webpayments/wiki/Agenda-TPAC2021 

thanks for review and discussion!


### 2. Privacy review of CSS Cascading and Inheritance Levels 4 and 5 (reviewer: Aram)

* URL of spec: https://www.w3.org/TR/css-cascade-4/
* URL of spec: https://www.w3.org/TR/css-cascade-5/

Note: Cascade 5 is a superset of Cascade 4, so the WG sent the review requests together. See https://www.w3.org/TR/css-cascade-5/#additions-l4. The WG expects to transition to CR by the end of October, ideally.

Previous review request was against Level 3 (now REC). WG has requested that we please file any issues in https://github.com/w3c/csswg-drafts/issues

Aram: (cascading level 5). changes to @import rule, and @layer rule -- a layer of CSS rules that can be applied and the ordering. components can deliver stylesheets with layers, so that authors can override without worrying about breaking further styles.

Aram: privacy and security considerations note that the @import rule doesn't apply CORS protocol. they are attempting to resolve that. general CSS problems for fingerprinting, can expose the cascade process, information about the user agent, information about the device. that is well-covered, not introducing something new here.

Aram: loading of third parties that can operate in the context of a stylesheet loading. intended to encourage developer behavior of importing stylesheets freely, and that the developer's overwriting won't be further overwritten. encourages more freely and frequently importing of stylesheets from third party domains. creates issues: by design, imports can be nested, which can import others, which can be limited based on media queries. opens fingerprinting risk. importing new scripts, which can differentially load scripts which create styles for fingerprinting. you think you are importing styles that will only apply to a particular component, but it could actually import additional stylesheets applied on other things.

Aram: if figcaption is not in the base stylesheet, might import a stylesheet for a video component, which includes another stylesheet that applies a particular style to figcaption (based on some user identity or timing). other scripts on the page could read the figcaption styling. because layers are intended to make it easier/safer to import more stylesheets, this could be a growing issue, more and more stylesheets with potential traffic analysis.

Pete: CSS is active, in being able to probe device capabilities.

Aram: nesting allows network traffic as well.

Pete: some of that is currently capable in CSS

Aram: unlimited numbers of requests changes that. nesting and more requests creates additional tracking and timing of additional requests.

Nick: Not clear whats new here, aren't @import's already used in deployed CSS?  Could this already be happening?  And / or will import + layer make it more common?

Aram: not sure if nested imports are being used already, but might be because there are existing mechanisms that are easier to use that we would like to close or are in the process.

Aram: layers can be composed. layer names could reveal information to others, not currently described in the spec how those names are controlled. unsuspecting authors could reveal information about their users.

Sam: +1 for filing issues now, and let PING know.

Aram: happy to open issues in CSS and work in the open.

Christine: hurrah, good job on a first review.

cheers!

Aram: fun review to do, always enjoy reading specs :)

### 3. AOB

Sam: TPAC related meetings on privacy

* Tues, 26 Oct 1400-1500 UTC Machine Learning / PING joint mtg ** [will be covered by Christine]
* Tues, 26 Oct 1500 UTC EPUB / PING joint mtg ** [will be covered by Nick, Aram]
* Tues, 26 Oct 1530-1600 UTC Web Payments briefing on Privacy Sandbox
* Wed, 27 Oct, 1500-1600 UTC: Web Payments re: Frictionless flows
* Wed, 27 Oct, 2300-2359 UTC Web Advertising BG (slot 1)
* Thurs, 28 Oct, 1400-1430 UTC: Web Payments PING review of SPC **
* Thurs, 28 Oct, 1430-1500 UTC PING and Privacy CG updates for Web Payment WG**
* Thurs 28 Oct 1500-1600 UTC Web Advertising BG (slot 2)
* Fri, 29 Oct, 0500-0700 UTC Devices and Sensors WG privacy discussion ** [unfortunate time of day for many PING participants, maybe Nick]
* Fri, 29 Oct, 1600-1700 Private Advertising Technology CG initial meeting

Some relevant links:
- https://github.com/webmachinelearning/meetings/issues/18
- https://github.com/w3c/webpayments/wiki/Agenda-TPAC2021
- https://github.com/w3c/devicesensors-wg/issues/47

TPAC ongoing updates:

* Developer Council a promising approach
* how to improve WG processes (so you aren't in email and slack and irc and everywhere; and good labeling). https://lists.w3.org/Archives/Public/www-archive/2021Oct/att-0004/How_to_work_with_COGA_Presentation_TPAC2021.pdf

TPAC social hours -- welcome and it's fun to chat about random things.  One in the next hour; one tomorrow 9am EDT.

wseltzer: recordings and consolidated resources from our meetings will be sent around after the end of tpac.
