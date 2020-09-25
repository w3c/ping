# Privacy Interest Group meeting (24 September 2020)

* Christine Runnegar (PING co-chair)
* Pete Snyder (PING co-chair)
* Erik Anderson (Microsoft)
* Melanie Richards (Microsoft)
* Scott Low (Microsoft)
* Sam Weiler (W3C/MIT) 
* Sean Harrison (Google)
* Nick Doty (UC Berkeley)
* Wendell Baker (Verizon Media)
* Michael Kleber (Google Chrome)
* James Rosewell (51Degrees)
* Kris Shrishak
* Wendy Seltzer (W3C)
* Lisa LeVasseur (Me2B Alliance)
* Terri Oda (Intel)
* Eric Mwobobia (ARTICLE19)
* Jeddy
* John Sabella
* Jeffrey Yasskin (Google Chrome)
* Kristen Chapman
* Garrett McGrath
* Mallory Knodel (CDT)
* Yaroslav Boychuk (Magnite)
* Joey Salazar (ARTICLE19)

Scribe: npdoty

#### 1. Privacy review of the Web Share API

* Spec: https://www.w3.org/TR/web-share/
* Security and privacy considerations: https://www.w3.org/TR/web-share/#security-and-privacy-considerations

melanie: Web Share lets users share text, links and files to a target destination, but the share targets are left unspecified. web sites call a share() method on the navigator interface, which will trigger share UI on the OS/browser level. API can only be used in secure contexts, share() can only be invoked on user interaction, can only share http:/https: urls (to avoid attacks sharing file urls). thorough security and privacy considerations section in the spec.

melanie: usual concerns about URL sharing, users may struggle to understand all the implications of a URL being shared, link decoration could include tracking mechanisms. Web Share can include an arbitrary URL, not a URL that's necessarily the user's expectations (which could be a URL to a malicious site). one option would be limiting to the top-level URL, but would that limit functionality too much? not clear on all the developer use cases. could suggest that the value should be limited to the same origin

melanie: past issue considered origin and some sites might have their own url shortener. intermediate UI could show the contents of the share functionality in some cases. a challenge that it relies on UI that is outside of the standardization process.

melanie: non-normative security and privacy considerations section, we could suggest that they be moved to normative text or provide suggestions. requirement to prevent the app from seeing what apps are installed, limiting what's revealed in error messages. attack with a scheme that redirects to other URLs; share targets could pre-fetch target URLs, but should that be the user agent's responsibility rather than

nick: re normative language, some specs have differed whether privacy section is normative, or whether normative text is elsewhere and pointed to from the privacy + sec section

melanie: it seems like there was more detail elsewhere (not in p + s), so either would be good

nick: thanks! we can clarify re level of detail

runnegar: +1 for pushing for normative text (wherever in doc).

weiler: not sure why the spec is needed

npdoty: API is needed just so that you can click a share button within web content and the UA can translate the content and pass it along. it's fire and forget, and simpler than the Web Intents that were previously specced out here.

pes: there are other widgets on the Web for sharing that often had privacy harming characteristics, so it's a way to improve privacy for the Web.

next steps?

melanie: I can raise issues, and if people have recommendations on mitigations, please feel free.

pes: please link to filed issues in Slack.

#### 2. Privacy review of CSS Color Module 4

* Spec: https://drafts.csswg.org/css-color-4/
* Security and privacy considerations: https://drafts.csswg.org/css-color-4/#priv-sec

Background: The CSS WG identified a potential risk - System Colors. They note that feature previously existed, and was deprecated, for example in CSS Color Module Level 3 which is a W3C Recommendation. The WG notes that they now find that they are unable to fully deprecate the feature, partly due to Web-compatibility and partly due to an interaction with an accessibility feature, forced colors mode which is defined in a different specification. However, they also note that have continued to deprecate some little-used colors and made the interpretation of the remaining ones more generic.

mallory: prior concerns about the use of system colors (which may have already been mitigated in Level 3), but there's another spec that uses system colors and user preferences at the UA level for accessibility purposes, so they couldn't be completely deprecated, so added appendix text on that topic. because this was addressed before, attempted to balance those competing features really well. only presenting this color information to the user agent, not to Web content.

pes: different UAs could implement 'high contrast' colors differently.

mallory: fingerprinting risk that you could distinguish something about the system. but also a security concern of spoofing pop-ups to look like native UI

mallory: css color adjust -- https://www.w3.org/TR/css-color-adjust-1/ -- might be worth reviewing that as well. seems like it will only affect user agents. authors must not use it.

pes: dark mode/night mode might be a similar situation, where sites want to look like the surrounding environment.

mallory: forced colors for higher contrast: mapping will be done by the user agent, and so doesn't expose back to web site authors. 

nick: could be it be queried after the fact by the site content?

mallory: would need to check, seems possible

yasskin in chat: https://drafts.csswg.org/mediaqueries-5/#descdef-media-forced-colors says the fact of forced-color mode is available. https://drafts.csswg.org/css-color-adjust-1/#privsec has "Applying user color preferences via color schemes or forced colors mode expose the user’s color preferences to the page, which can increase fingerprinting surface."

mallory: should review color adjust module when that's ready for review. 

yasskin: could file an issue early on the color adjust module to give them a heads-up, rather than waiting for wide review.

mallory: now that some of the system colors are not fully deprecated that sites may be able to query those forced colors.

yasskin: expressing the concern early might help them with the spec.

mallory: learned so much about colors!

#### 3. Privacy review of CSS Cascading and Inheritance Level 3

* Spec: https://www.w3.org/TR/css-cascade-3/
* Security and privacy considerations: https://www.w3.org/TR/css-cascade-3/#priv-sec

scottlow: all of the rules handle how styles are interpreted and applied to elements. @import rule and how imported styles should be applied. shorthand properties to specify multiple rules in shorthand notation. value processing parsed out of stylesheets. cascade order about how rules should be applied based on where they're defined, e.g. '!important', and user agent stylesheet, user applied stylesheet, author stylesheet. default values and inheritance.

scottlow: issue called out in privacy/security section, cascade could allow detection of user stylesheet or assistive technologies by the page. not an easy way to mitigate, given the user priority.

nick: there have been concerns in the past about history leak through state dependent pseudo selectors (e.g. :visited). Is there something that could be done when applying a user stylesheet similar to those mitigations?

kleber: extremely difficult to prevent side channel leaks of what is drawn on the screen: timing attacks on repainting, etc. difficult to implement render-differently-but-don't-reveal approach. there's a push on history visited status to make it something that isn't revealing rather than limiting querying of rendered style.

erikanderson: visited mitigation is possible by making it especially constrained (to color), but nearly impossible for things that affect layout.

pes: if the user stylesheets are primarily about accessibility, could there be guidance to people who create/use that functionality about privacy implications and how to address?

weiler: does it need a separate security review?

scottlow: privacy/security unchanged since last CR, and no obvious concerns about changes since last CR

thanks to reviewers!

#### 4. AOB

##### a. Physical address privacy in the Payment Request API

* https://github.com/w3c/payment-request/issues/842
* https://github.com/w3c/payment-request/pull/873

weiler: looking for folks who are willing to engage with this WG and take the lead on this issue. payment merchants are collecting billing and shipping addresses in payments. some are collecting address information for calculating sales tax, but often leading to collecting of excess information. billing address may be needed for fraud prevention (like a zip code/postal code).

weiler: asked about the potential of a richer negotiation. WG had an incremental approach: asking for state, then city, then street address, with each step only as needed. but WG is not pursuing that. concern that we are setting defaults in a non-data-minimization way.

pes: point person on payment request handler api (?)
     [pete comments: i opened an issue a while back about the context (1p v 3p) of a payment request handler, if that issue is still open, I’ll already be working with the group, so happy to add this too to my plate]

eric mwobobia: happy to champion for it, but need more context/clarity

wseltzer: not much implementer interest in changes to the API in the year that it's been open. WG concerned that code/implementation was unlikely to happen.

nick: higher level question, what if you're purchasing a digital good, so no shipping address needed. Is there an alternative route sites could use to get less information, and not ask for shipping address if not needed, for smaller payments

weiler: micropayments?

nick: is there any ongoing work to try to provide that, micropayments that aren't full credit card transactions. sounds like not active interest in the WG?

kleber: not providing full details to the merchant on the Web has been done through a smaller set of payment providers (like Paypal), that could be the advantageous outcome, right?

[pete: sounds like there may be two issues here: 1. way to request only minimum amount of physical address info when its needed, 2) some way to do payment requests w/o any shipping address.]

weiler: Paypal-style could be an incremental improvement, but it seems like more information is still shared with the merchant. would prefer an outcome that doesn't depend on a single payment processor that does it right.

lisa: volunteer to be an advocate on this topic

jeffrey: can make connections to the Chrome folks on payment request (Danyao)

lisa and eric volunteering to help with consumer interest. pes looking at status of other previously raised issues.

##### b. (just in) Privacy review request - WebRTC Priority Control API

* Spec: https://www.w3.org/TR/2020/WD-webrtc-priority-20200922/
* Explainer: https://github.com/w3c/webrtc-priority/blob/master/explainer.md
* Privacy considerations: https://github.com/w3c/webrtc-priority/blob/master/security-privacy-questionnaire.md
* Repo: https://github.com/w3c/webrtcpriority-

runnegar: just came in, needs a privacy reviewer.

yasskin: works for me. (pes will follow up.)

##### c. TPAC

runnegar: TPAC is happening virtually this year. breakout session phase, and last year there were many privacy-related topics. if you have some creative idea to discuss, please put those forward. we don't have formal meetings with other WGs, but have been invited to a couple sessions to talk about privacy issues or learn about their current work. (will send to mailing list) but there won't be a separate PING or PrivacyCG meeting at TPAC.

joeys: joint session with WebRTC? 

runnegar: have been invited to talk with WebRTC, Web Payments Security Interest Group, Web of Things. will share details

reminder that folks need to register for TPAC

wiki for breakout session ideas




