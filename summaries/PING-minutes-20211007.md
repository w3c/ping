# Privacy Interest Group meeting (7 October 2021)

## Attendees 

* Christine Runnegar (PING co-chair)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C/MIT)
* Stephen McGruer (Google) (guest)
* Kris Chapman (Salesforce)
* Nick Doty (CDT)
* Aram Zucker-Scharff (The Washington Post)
* Eric Mwobobia (ARTICLE19) 
* Theodore Olsauskas-Warren (Google)
* Rouslan Solomakhin (Google) (guest)
* Wendell Baker (Yahoo)
* James Rosewell (51Degrees)
* Wendy Seltzer (W3C)
* Tim Cappalli (Microsoft)
* Akshay Kumar (Microsoft) (guest)

Apologies: Pete Snyder (Brave, PING co-chair)

Scribe: Sam, Aram

Christine: First up on agenda, SPC privacy review, 3 reviewers. 

Christine: Pranjal, Pete and Sam volunteered to review but are not available today. Sam is here and we have guests from the working group on this proposal.

### 1. Privacy review Secure Payment Confirmation (Pranjal, Pete and Sam, reviewers)

* URL of spec: https://w3c.github.io/secure-payment-confirmation/
* Link to privacy considerations: https://w3c.github.io/secure-payment-confirmation/#sctn-privacy-considerations
* Response to self-review questionnaire: https://github.com/w3c/secure-payment-confirmation/blob/main/security-privacy-questionnaire.md
* Explainer: https://github.com/w3c/secure-payment-confirmation/blob/main/explainer.md

Christine: Would it be helpful to get an overview from the WG?

Sam: I'm actually tempted to do the review myself and there are people here to correct me. 
Part of what I'm doing here is asking other people here to take a look at it and give feedback. 
Secure payment is mostly modifications to ModN(?). It allows both registration and authentication to a third party. On a merchant site you can authenticate to a payment provider without an iframe (provider like a bank). That was the authentication piece, registration is the same. Even if you are on the merchant side you can enroll a web authentication even though the bank is on the other side

Stephen/Rouslan: You can only author a web authentication potential for the domain you are on. On the first time you would still have to open an iframe for the first time. The contract is still with the first party but you are allowed to do it in the iframe. For authentication, you are correct it is deliberately cross origin. 

Sam: A possible attack is that the attacker might be able to probe for what credentials you have available when you haven't intended to allow that. Exposing more information than you intend to do. The document proposes a particular bad implementation choice. A malicious site could choose a unique icon just for you and expose information about you that you did not intend to reveal. The two issues that I had - it didn't look like you were standardizing to a particular loading order - https://w3c.github.io/secure-payment-confirmation/#sctn-privacy-probing-credential-ids

(Steven nods)

Sam: For the issue I was looking at you thought of one way [privacy could be breached] that an implementation will have to remedy but I'd rather you thought of all of them. 

Stephen: We could certainly think of a longer list of them. But we are careful to not specify information about how the user agent must implement. 

Sam: However, if the issues are there we must call them out quite clearly and unless there is a reasonable chance of resolving them in other ways we should specify something like don't load these URLs. 

Stephen: The other main way this can come up is that similar to Web authentication if the user has never registered before the question is what do you do and that opens up a trivial privacy attack - you request info about the user and it returns right away that the user is not known. We need something else besides just the credential did not match. 

Sam: To be clear this is an early draft, thanks for coming in early with this. 

Nick Doty: Is there a Web authentication document explanation about why this type of 3rd party iframe is typically prohibited so we can understand what the potential consequences are?
There was a time when we tried to tell users to only put information into the website when they could see that the website was what they knew in the bar. 

I think we have a similar issue with this where we train users to put in the key any old time and then it is an attack via an embedded iframe that the users are putting in keys all the time [because we instructed them incorrectly]

Rouslan: It appears that in Web authentication we did not use of any useful use case for an iframe to be registering a credential they only knew of the top level needing the credential and that is why they cut off the ability for the cross-origin iframe to register that credential.

We are seeing that merchants often delegate their sign-in experience to a 3rd party like Stripe or PayPal, etc. And those payment providers can embed something like a bank if they'd like to. The payment source provider as a single vendor can then fan out to individual banks and processors. We are saying as a result that this is a typical infrastructure functionality and that is the desired result for a cross-auth iframe. 

We also have to consider other uses for a cross origin iframe. 

For example, a pluggable USB key that may/may not have a UI requirement 
For example, a user might accidentally bump that key and provide data unintentionally. 

Types of authenticators that show a user interface are t/f required for user verification ability. Ex: Touch ID on mac which always shows a prompt and Window hello that always shows a prompt. Those always show an origin and identifier to the user. So that you don't always see it in the window you always see it in the prompt "You are registering credential with Bank of America.com".

Stephen: Web authentication prior art info and discussion links: 

https://github.com/w3c/webauthn/issues/1336
https://github.com/w3c/webauthn/issues/1656

There was an attack in 3rd party creation and that was an issue but the real reason they immediately disabled it was there was no use case, but someone mentioned an attack 

Nick: Is there a reason we shouldn't send the users to origin?

Stephen: The answer is friction and the conversion loss that comes from it. In most payment flows the iframe shows up or an invisible fingerprinting iframe shows up rather than redirect you.

The value add of X is that they consider themselves less friction than the iframe. Merchants really hate friction. 

Nick:I just am not sure not sending them to origin is a good outcome. We're training users to enter their passwords into any old iframe you see and that is enabling other attacks. 

Are we making phishing easier when we're talking Web authentication keys? 

Either b/c we are showing the origin through the prompt or other reasons. 

Maybe there isn't a security risk to entering the key? 

Stephen: To be clear there are privacy concerns you could consider it a way to create a tracking vector. 

Obviously, I cannot speak to what the world would look like if we demanded this. 

Our partners in payment sphere don't like redirect, they would never redirect to bank, they would ignore this technology as a result. 

Nick: Thanks

Sam: Thinking about cultural differences, the Dutch payment system iDEAL - it does go through the bank, it invites a push. Tiny country with a very insular banking system seems to get along quite well. We've seen an example that's not doing this in the form of iDEAL.

Stephen: Does it redirect or use a mobile app? 

Sam: I think it is re-direct to bank but I'm not sure. 

Stephen: This is a good cultural question. We are posited on EU payment flows and credit cards. The EU mobile banking system is different it presumes you will open an app and control it. 

Sam: We do not consider this review complete yet and may throw some more things at you in the next fer weeks 

Christine: Thanks for bringing this early it is good to get in the early stage. 

[We're reviewing to make sure attendees are PING members, or guests] 

Please do join PING if you are interested. 

### 2. Privacy review of CSS Display 3 (Kris Chapman, reviewer)

* URL of spec: https://www.w3.org/TR/2021/CRD-css-display-3-20210903/

* What has changed since any previous review?

	* Copied over order property definition from Flexbox. (No change since last a11y review of Flexbox except some editiorial improvements.)
  
	* Copied over visibility property definition from CSS2 and expanded it to explain interactivity and a11y implications.
  
	* See full Changes list at https://www.w3.org/TR/css-display-3/#changes
  
	* See Disposition of Comments at https://drafts.csswg.org/css-display-3/issues-cr-2020
  
* Response to self-review questionnaire: https://lists.w3.org/Archives/Public/www-archive/2021Sep/0002.html


Kris: Pretty easy review.  The spec talks about the box tree.  Currently single value system.  Two display types: outer - how that box is displayed in relationship at top level, either inline or block. and the other type is how all descendants of that box are treated.  Single value system not well specified. The change is move to a two-value system, clarifying inner/outer display.  Since this is about display, no info user... I don't see any privacy considerations.  I'm a little iffy on visibility - where you can create a not-visible box.  I can see that being abused, but I also see value. And this is not a new consideration.  Only change from 3 to 2 is give an alert, in the spec, re: it's confusing for accessibility when top level says hidden and children say visible.  So nothing new.

Sam: should anything be included in the analysis in the doc?

Privacy and considerations section is empty. Is there anything they should be saying there?

Kris: Not really. They don't. The impact of just this is how the stuff is displayed on the screen here doesn't seem to be a concern to me. The privacy concern is more about the content that is displayed on the site. A note or consideration is useful but users not developers should be concerned. Debatable for sure. 

Aram: I don't think there's anything additional introduced.  Depending on rate of adoption, that could be fingerprinting surface.   Nothing new here; just carried forward from last version.

Christine: Could a malicious site make content invisible as a way to create extra fingerprinting surface?

Kris: content itself might be, but not the display.  If you create a format that has users interact w/ it... user access patterns could be unique.  Would need many unique boxes.


### 3. Upcoming review of CSS Cascading and Inheritance Levels 4 and 5 (needs reviewer)

* URL of spec: https://www.w3.org/TR/css-cascade-4/
* URL of spec: https://www.w3.org/TR/css-cascade-5/

Note: Cascade 5 is a superset of Cascade 4, so the WG sent the review requests together. See https://www.w3.org/TR/css-cascade-5/#additions-l4

They expect to transition to CR by the end of October, ideally.

Previous review request was against Level 3 (now REC)

Please file any issues in https://github.com/w3c/csswg-drafts/issues

Christine: we need a reviewer.  These are together because they're related.  These tend to be smaller and easier.

Aram: Schedule?

Christine: The WG hopes to transition at end of October; we would plan to discuss in two weeks.

Aram: I'm interested; want guidance.

Sam: Pete or I will support you.

### 4. AOB

Sam: We'll get a TPAC joint mtg schedule out.  Please register early.


