# Privacy Interest Group meeting (6 April 2023)

## Attendees (sign yourself in)

* Pete Snyder (Brave, PING)
* Christine Runnegar (PING co-chair)
* Sam Weiler (W3C)
* Nick Doty (CDT, co-chair)
* Tom Van Goethem (Google)
* Jeffrey Yasskin (Google Chrome)
* Don Marti (CafeMedia)
* Stephen McGruer (Google Chrome)
* Wendell Baker (Yahoo)

Regrets: Aram Z-S

Scribe: Pete

Chair: Nick


## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/) 

https://www.w3.org/Consortium/cepc/#expected-behavior includes treating each other with respect

### 2. Privacy review of Secure Payment Confirmation

Reviewer: Sam

See: https://github.com/w3cping/privacy-request/issues/110
 
Sam: SPC is coming for its 3rd look. 2 changes in the doc.  As summary, this lets sites use web auth creds across sites.

…: the idea is to (for ex) allow a bank's credentials to be used on a merchant's site

…: the group made 2 changes, Sam has 1 additional concern.

#### Change one: https://github.com/w3c/secure-payment-confirmation/issues/172

Sam:group made an opt out feature that lets a payment site describe how to stop the merchant from storing information.

…: The browser defines text thats presented to the user if the site wishes to let the user choose to opt out of data collection (?)
…: Sam is worried this could confuse the user, but it doesn't seem like fingerprinting risk

Nick: are there samples?

Stephen: yes https://github.com/w3c/secure-payment-confirmation/issues/172#issuecomment-1147532444

Sam: i'll add the examples in the minutes

Pete: When I'm engaging with the browser, is it an additional button to let me opt out of data flow?

Sam: The button just does it, right?

Stephen: No, we're not comfortable sending users from browser UI to a new page. Instead, we return to the site (closes the dialog), and we return an OptOutError in Javascript, which lets them redirect the page to an opt-out experience for them. IANAL, but in order to power SPC, you need a lookup from ID to credentials. For SPC, there's a Payment Service Provider that uses credit cards. Then they're storing credit card info. They interpret the GDPR as saying they mustt offer the user a way to remove that ctredit card data. And that way to remove it has to be as easy as it is to create it, so it has to be in the same UI flow. We thought this was out there, but it's coming from regulations and seems to be a real need.

Pete: Repeating that: I'm engaging with the dialog. I have one option to share data; another to tell the site to remove data. That's sent to the site via JS, and the site can do whatever it needs.

Stephen: Yes.

Pete: Is that presented to everyone, or just where it has legal bite?

Stephen: The message is optional, and the page decides whether to display it. Sites will usually only present that where it's regulatorily relevant. Chrome's text says you're requesting the data to be removed, and Chrome can't promise it'll happen.

#### Change two: removing user activation requirement https://github.com/w3c/secure-payment-confirmation/issues/216

Sam: Steven, please tell us about removing the user activation

Stephen: presently SPC requires a user activation to trigger the SPC UX (e.g., the click that might occur on a pay button the user would click on)
…: we did this bc it seems common practice in web standards

…: however, SPC partners say this is a problem bc its common to do a redirect payment flow (you click pay on site X, your passed to site Y to do payment/auth. Site Y doesn't have an activation)
…: Site partners said showing a button was no good

…: We (spec authors) think of requiring user activations as a protection against click jacking and spamming.

…: We don't think these are concerns in the case of SPC.

…: Click jacking not a concern bc SPC dialog still needs to be interacted with

…: spam not a concern bc this is a page-modal dialog and limiting it to a single free activation

…: we dont think this has any privacy implications

Nick: Understood that in payments we often redirecting users to other sites.  But isn't the point of SPC that you don't have to redirect users anymore

Stephen: yes, by redirecting users it does seem to loose 50% of the benefit of SPC, but there are still benefits

…: additionally, you can be on a merchant site, who has a payment provider, who uses SPC to talk to a (say) bank

Pete: I thought I heard you say this was page-modal, so it's attached to the page instead of the browser?

Stephen: Yes, that's an implementation-detail; the spec can't say it; but yes, in Chrome it's attached to the tab, and you can always close the tab.

Pete: That's important for the privacy model: if you remove the activation requirement, then a page in the background could fire it. So we should require it to be tied to the thing issuing the request.

Stephen: Do we spec like that? I'd be happy to spec that.

Jeffrey: Permissions doesn't do that, but maybe it should. Some specs check the page's visibility (https://html.spec.whatwg.org/multipage/interaction.html#page-visibility) to avoid ephemeral fingerprinting, and you could do the same. We could also say that the dialog should be no more visible than the page.

[npd: +1 for foreground tab making sense and we should spec that]
Stephen: https://github.com/w3c/secure-payment-confirmation/issues/237

#### Previous issue re: downgrading a credential creation request: https://github.com/w3c/secure-payment-confirmation/issues/154

Sam: also see "SPC for non-payment use cases" https://github.com/w3c/secure-payment-confirmation/issues/186
...: and "Consider separating the SPC powers of Third Party invocation and Payment display" https://github.com/w3c/secure-payment-confirmation/issues/157

Sam: I dont see additional concerns with the changes

…: i do have a concern with how credentials are used

…: i'm worried sites could create these payment credentials as a way of piercing site isolation features

…: can a user downgrade (?) the ability for SPC to create these creds

Stephen: Sam's desc of how credentials are created is correct.  Its an extension in FIDO.

…: we asked webauth if we should have additional language to allow the user to remove the additional bit (?)
…: I _think_ UAs could drop the extension (i.e., creating a 3p credential) on behalf of the user, but it's not clear what'd happen then

…: No update other than FIDO and webauthn folks were not interested

Sam: It also seems like some folks are thinking about these concerns around 3p credential misuse

Stephen: we struggle w/ it bc the people who want to use SPC would consider a non-3p enabled credential useless for their usecases
...: so they would take this created credential and just throw it out, and they would be upset that the user has wasted their time

…: not clear what to do

Sam: should we keep pushing on this
(pete nods)
Nick: can the user reject the credential? 
Sam: but a site could ask for one of a 3p credential w/o the user knowing knowing it

Stephen: at least some mitigation bc the credential request would be obvious

…: Sam so this would need to be part of a payment flow?

Stephen: yes

Sam: this (?) is enforced by the browser or the site?

Stephen: the browser (re client) is allowed to do a lot




### AOB

#### AC Meeting

Nick: this meeting is happening next month. Agenda was just announced; lots of topics about governance, might be other discussions around values and process

…: inc ones relevant to privacy reviews.  Might be good to have AC members attend

#### charter discussion to come later

Nick: Our charter ends at the end of June. We shoudl think about changes we might like (growing, shrinking, etc responsibiities)
…: more discussion to come

#### privacy principles asking for review: https://www.w3.org/blog/2023/03/privacy-principles-for-the-web/

Nick: the privacy principles doc is being work on by membmers of the TAG and other privacy folks.  We'd love more thoughts and input and wide review

…: this might impact PING reviewing and process, so feedback is important. Please share it with others who might be impacted too

…: and esp this month as we try to get wide review

PhL: can we add TPAC 2023 to discuss if we should have a PING face to face

…: TPAC is in Sep, but we need to give input about requests for TPAC events by end of May

…: gets harder to make changes then

