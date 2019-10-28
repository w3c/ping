# Privacy Interest Group meeting - 24 October 2019


## Attendees (sign yourself in)

* Christine Runnegar (co-chair)
* Tara Whalen (co-chair)
* Ian Jacobs (WPSIG Co-Chair and Team Contact)
* Wendy Seltzer 
* Pete Snyder (co-chair)
* Nick Doty
* Brent Zundel
* Melanie Richards
* Erik Anderson
* Eric Lawrence
* Michael Kleber 
* Chris Wilson
* Michael Horne (for payments)
* Christina Hulka (WPSIG Co-Chair)
* Bastien Latge (WPSIG Co-Chair)
* Sameer Tare (for payments)
* Jeffrey Yasskin
* Brad Lassey
* Mateus Teixeira (Publishing CG Co-Chair)
* Tanvi Vyas
* Pranjal Jumde

## Minutes:

scribe: npdoty

anyone new, introductions
Christina Hulka, Web Payments Security Interest Group;
Tony Nadalin, MSFT;
Melanie Richards, MSFT;
Tanvi Vyas, Mozilla;
Eric Lawrence, MSFT


### CSS Font fingerprinting

pes: part of a larger effort to remove fingerprinting surface from existing standards. the attack is to query the fonts that are installed in a browser/device, and uncommon fonts can be very identifying.
ko
... areas of disagreement: 
* can we have a static, default policy or need a dynamic, runtime solution?
* can we address this in the standard, or will it just be implementation by implementation?

pes: option a: set of local fonts could be empty by default, or default set of system fonts that a browser chooses a subset from. (current Safari implementation) or b: a user preference/checkbox for a user to opt in to using local fonts. or c: the user could choose which non-default fonts could be added in to be used by websites, but not every shipped font.
pes: getting closer to some common ground, through Slack discussions. want to check if that's the current status.

kleber: privacy budget as part of google's privacy sandbox proposals. not intended to be black magic, but a very practical solution. the philosophy would be to say that querying a small number of fonts exist/use is reasonable and not particularly identifying, but we do see font fingerprinting scripts going through 60 or 200 checking the presence of each: that's not being used for functionality, just for tracking. let's set a limit that reasonable uses are under the limit, the browser intervenes only after that limit and cuts down to system default. would need to gather data from the field to decide how many fonts are typically used: anticipate that it's bimodal (between common functional uses and a spike at the fingerprinting).
kleber: larger philosophy: even if we place limits on font use in particular, the combination of entropy sources might still be uniquely identifying. want to identify reasonable limits for each, but if you use some features, you'll be able to use less of other features.

[pes: https://github.com/w3c/csswg-drafts/issues/4055#issuecomment-538581310 <- large number of practical reasons privacy-buget doesn't seem to work]

pes: some issues opened on privacy budget where I haven't seen answers. what is the lifetime of the budget, how does it get used by third parties. seems like the practical questions aren't completely filled in. if it's not fully formed yet, how can we move forward in the meantime?

kleber: privacy budget is in its infancy and we shouldn't have to block other things in the meantime. we can come up with a proposal that works for a specific thing like fonts. like, the browser can pick a limit per origin: if the number is 0 you do Safari's current implementation, or 10 could work for most sites today. we do need to answer those practical questions, and maybe we can come up with those answers from the font fingerprinting example.

pes: if we are still setting the budget, need to scope (3rd parties, etc.) and set a lifetime.

kleber: generally agree that we need to answer those questions, and great for PING to come up with answers here (or in some other venue). brad lassey not here today, but generally available.

[pes: the answer is "budgets" are not the solution, what about the other two approaches: users opt fonts into websites?  Or just opt into local fonts at all?]

npdoty: even if browsers use a dynamic budget approach, there still needs to be a static "the budget has been exhausted" policy, and a limit to the surface will be useful in reducing the number of sites that hit the budget. So whether there is a budget approach, other options (e.g. opt fonts in) still would be useful.

pes: given that we've been discussing this issue for months, when would we have answers to the other privacy budget questions, and what do we think of the other options in the meantime?

jy: I like the user choice of fonts to be exposed to the Web. how much of that needs to be in the specification? I recognize PING generally prefers specifying more, but it seems like the original options could be a reasonable area where browsers choose to vary.

pes: don't want the standard to be dangerous that the browsers then fix. want users to have confidence in browsers in general.

tess: skeptical about users being able to choose specific fonts to expose to the web. hard to phrase that question to users in an understandable way. hard to rely on permissioning here.

kleber: asking for concrete answers to open privacy budget questions -- that's fine, and should happen now, in discussion with the CSS folks. wanted to see whether a solution like that would work for PING before diving into it.

jy: +1 to tess that user choice/permission sounds hard. the thing that the browser does when we hit the limit, is to say that the font is not available. developers have to expect that no font is guaranteed to be available, which is consistent. could give a list of options to browsers to choose from.

pes: opt-in proposal wouldn't be users individually selecting fonts, but rather that some groups are installing fonts for particular languages to make the web work for them. the conversation is happening in CSS WG, could have a separate call.

runnegar: best next step would be a call with CSS WG. will schedule later. can continue discussion in email/slack.

### Web Payments

-> https://www.w3.org/2019/Talks/ij_ping_20191024/#Cover Ian's slides

Ian: co-chairs of the interest group, and 3-d secure auth protocol authors also present

Ian: joint discussion at TPAC, clear that payments side wants to know the impact of addressing fingerprinting on methods of authenticating cardholders. presentations on emerging technologies in this area on "trust tokens". satisfying risk mitigation requirements with emerging privacy trends in browsers.

Ian: goal is to develop a plan for payments folks to do the right thing

[slide 3]

Ian: education sessions on web payments call (many attendees) would be useful for presentations.
Ian: 3-D Secure could be something reviewed by PING, integration of FIDO.

[slide 4]

* fraud prevention
* shared privacy principles from W3C, FIDO, EMVCo
  [npd: +1]
* trust tokens
* entity attestation tokens
* token binding

Ian: what other topics should web payments security hear about?

pes: generalization of modal dialogs -- first party contexts within another first party context. concerning that it may be confusing about first vs. third party access. are there other alternatives or explanation of that background?

Ian: Web Payments Working Group developing concrete protocols, Web Payments Security Interest Group discussing higher level topics of interop and security. don't have answers on modal dialog yet, but the payments ecosystem has specific use cases where this top-level-origin interactions happens, and just exploring whether other use cases should have that. if there are more use cases, it might be worth browser implementation, which would simplify Payment Handler specs.

3-D Secure protocol: https://www.emvco.com/emv-technologies/3d-secure/
... some particular areas of concern about how iframes are used

-> http://www.w3.org/2019/Talks/emvco_ping_20191024.pdf EMVCo Deck

[Presented by Mike Horne]

Mike: 3DS browser-based flows, highlight where information is gathered from the browser in a hidden iframe
... a 3DS server integrated with a merchant, a directory server operated by payments systems, ACS Access Control Server does cardholder authentication
... the Access Control Server optionally gathers device information through a script on the merchant website (in a hidden iframe or otherwise in the background). collect information to use for risk-decisioning purposes. assigned an ID that would link information gathered to the subsequent authentication request.
... optional but critical for ACS to have this information in order to have a frictionless flow. authentication without the need for a cardholder challenge/step-up. if comfortable, can just proceed with the transaction. if uncomfortable, uses a "cardholder step-up".
... if 3DS isn't used, or is too slow, then the rate of step-ups will increase. to create a good, frictionless cardholder experience, this is widely used today.
... we have heard of plans to restrict access to information that's typically gathered in this background auth step.

pes: with this level of detail, can we take time offline to review and reply later.

Mike: focused on continued promotion of frictionless authentication, maintaining the ability to collect necessary information, in collaboration with FIDO Alliance.
Mike: what alternatives are available if access to information from browser is restricted? need to better understand trust tokens and token binding.

runnegar: thanks for the presentation, and we will need to look at these flows in more detail. as a takeaway, find a time to address in more detail.

Ian: have a list of 3DS design goals, and comparison between SDK and the Web-based approach. if we don't have all that data, what can we do instead? trust tokens/bindings is appealing to some people from TPAC.

See also Ian's slides for more background -> https://www.w3.org/2019/Talks/ij_risk_20190808/index.html

[Ian drops off thanks!]

### Privacy reviews

#### Publication Manifest & Audio Books

https://www.w3.org/TR/audiobooks/#security-privacy

https://www.w3.org/TR/pub-manifest/#security-privacy

https://github.com/w3c/pub-manifest/issues/61

pes: a schema/manifest for audiobooks to be described from websites. doesn't add web api functionality, so shouldn't be problematic. would anyone else like to review those proposals?
runnegar: +1.

#### WebDriver Extensions for Sensor APIs

pes: WebDriver is a standard for browser automation. those modifications wouldn't touch typical functionality. but there are scary items about sensor access and inferred permissions.
pes: suggest that inferred permissions question be separated/handled in permissions not in the sensor api.
pes: no normative mitigations.
pes: [paper released on accelerometer access fingerprinting](https://www.repository.cam.ac.uk/bitstream/handle/1810/294227/405.pdf) -- need to address this problem.

runnegar: we did years ago look at sensor APIs under development. there has been a change in our understanding of risks and potential mitigations; I think it would be worth looking at them again.

#### WebRTC

#### TTML2

### Privacy threat model

jyasskin: busy through part of November, then will draft in more detail with toml.

Link: https://github.com/w3cping/privacy-threat-model

### Community Group

runnegar: if all goes smoothly, should have a CG in November.
wseltzer: we have prospective co-chairs here.

### AOB

pes: can schedule another call, to go through other reviews and issues to open.

## Agenda:

1. CSS Font Fingerprinting
2. Web Payment (a joint discussion with the Web Payment Security Interest Group)
3. Privacy reviews - update and discussion
4. Privacy threat model - update 
5. Starting a Privacy Community Group - update
6. AOB


## Queue:


## other comments

