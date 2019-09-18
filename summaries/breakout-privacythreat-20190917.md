# Target Privacy Threat Model, TPAC 2019

## Metadata

* **Location**: We're in [Navis-A, Floor 1](https://www.w3.org/2019/09/TPAC/schedule.html#map), starting at 11:00.
* **Remote participation**: https://meet.google.com/aoe-vzqz-stt; dial in https://meet.google.com/tel/aoe-vzqz-stt
* **IRC**: [#privthreatmodel irc.w3.org minutes](https://www.w3.org/2019/09/18-privthreatmodel-minutes.html)
* Attendees:
   * Jeffrey Yasskin (Google)
   * Christine Runnegar (PING co-chair)
   * Tom Lowenthal (Brave)
   * on irc: npdoty, (remote), dezell, taraw, Anssi_Kostiainen, Ian, blassey, yoav, jmann, dbaron, manu, Ralph, iclelland, Mek, wseltzer, toml, kleber, rowan_m, scheib, jfishback, christine, mitja
   * [your name here] and we'll also capture the present+ from irc, #privthreatmodel  

## Agenda

1. Recruit:
   * Scribe: Yoav Weiss
   * Queue manager: Manu Sporny
2. Modify agenda
3. Prior work:
   * [Security and Privacy Questionnaire](https://www.w3.org/TR/security-privacy-questionnaire/#threats)
   * [RFC 6973: Privacy Considerations for Internet Protocols](https://tools.ietf.org/html/rfc6973)
   * [RFC 3552](https://tools.ietf.org/html/rfc3552)
   * ...?
3. Present https://jyasskin.github.io/privacy-threat-model/; describe PING discussion from Monday; Is this a good structure/baseline?
4. Brainstorm threats to model.
5. Where should this work live?

## Action Items/Things to think about

* Describe things like when cross-site identification is allowed. What UX is needed?
* Talk about problems at more levels. Enough detail so a spec author without context can figure out how to block the threats.
* Explicitly describe target audience, including spec authors.
* Include the possibility that there's consensus that tradeoffs are acceptable for particular attacker goals.
* Use the term "reasonable expectations", but don't be too pessimistic
* Include the fingerprinting entropy problem in this document.
* Define all terms clearly.
* Talk about second-order 

## Minutes

**jyasskin**: prior work on overall goal in [Security and Privacy Questionnaire](https://www.w3.org/TR/security-privacy-questionnaire/#threats) and [RFC 6973: Privacy Considerations for Internet Protocols](https://tools.ietf.org/html/rfc6973), but quite high-level, not detailed enough for folks writing specs.
... https://jyasskin.github.io/privacy-threat-model/ describes achievable target state
describes essential bits of the web that can be used for attacks, so we can discuss them,
Wants to get thoughts on this model, what venue it should be discussed at, etc

**Tom Lowenthal**: talked about the document at PING. enumerated list of misuable threat capabilities.
  
> * Unexpected Recognition (being confident that this is the same person/device you saw before), cross-site. This threat is discussed in § 4.1 Anti-tracking.
> * Recognition, same-site
> * Benign information disclosure (connected hardware [game controller or assistive device], system preferences [like dark mode]…)
> * Sensitive information disclosure (user location, user camera, file information, financial data, contacts, calendar…)
> * Intrusion (displaying messages/notifications, playing sounds, full screen…)
> * Obtaining capabilities (sending SMS, finance/billing…)
  
**Nick Doty**: threat model can mean we don't all have to agree on an end state. So valuable to develop even if there's no overall agreement. https://tools.ietf.org/html/rfc3552 is a useful piece of prior art. Big fan of this.
...  in particular, here's the section titled "The Internet Threat Model": https://tools.ietf.org/html/rfc3552#section-3
  

**Manu Sporny**: How would other WGs apply this? Would WGs review this and pick and choose what Security&Privacy sections would include?

**jyasskin**: would help WGs design the features in the first place. and when PING is doing horizontal review, would have less to do.

**TomL**: A lot of inconsistencies in S&P sections. Some copy-pasta. Some state threats and do nothing about it. We need a model that creates a standard that specifications need to reach. PING would like it to be something that sets out normative options and spell out the spectrum. Security & Privacy sections that say UAs can avoid implementing privacy sensitive features, that's not helpful for developers. Specs should write down the user expectations and spell out deviations above and below that.

**jyasskin**: anyone thinks this is an awful idea?

**manu**: all here because we care. this document can be used as a hammer to prevent work from progressing, but no one is suggesting that. But there are use cases that require tracking and that is not going to change soon. (e.g. passport check when crossing borders) Would be good for the document to outline when this is allowed. In the decentralized ID we're looking at idea that enable users to identify themselves. So don't want this to be used as a hammer. Agree with Nick, but there will be conflict, and a lot hinges on how the doc is written.
also, weird to get a press inquiry(it might be that Manu is responding to Tom, rather than Nick.)

**TomL**: I'd like for it to be used to stop specs from violating privacy. A web platform that allows every website I visit to ID me is a bug and is harmful. And that is kinda possible today. That doesn't mean we can't have a standard for cookies that enable you to log in. But when you're not logged in, you're not recognized. These capabilities should be available exclusively when the capabilities are used. All capabilities stated above are something we'd need to support, but they should be limited. They should not be side effects, but features.

**dbaron**: missing in the structure is talking about problems at different levels. High levels principles are good, but needs more detail around fingerprinting, 3rd parties interactions, etc. So that people can easily recognize those privacy traps in specs even if they are a few steps away from the high level goals.

**jyasskin**: are you asking for spec advice?

**dbaron**: presentation with enough detail so that spec author knows their spec touches that even if they are not privacy experts. Not tutorial, but just enough description that would enable folks to recognize their own issues.

**Jon Krafcik**: Like the general approach. How do we think about regulatory changes? privacy sentiments of individual and populations like interest groups or regions? Need to tradeoff that with user goals and developer goals. The tradeoffs between those can be tricky. How can the document address that.

**jyasskin**: There can be places with hard rules and places which enable tradeoffs.

**Michael Kleber**: a large number of threat so would be good to talk about prioritization and levels of harm. Seems hard to use the document unless you have a notion of the threats and benefits.

**Wendy**: the standards process has few hammers, we're looking to build consensus. A document that helps understand the tradeoffs can later be complemented by PING or individuals filing reviews or objections. So can help us think about making the web best for all.

**mnot**: pushing back about language Manu used. for some people, it's a use-case to track what I do. Also systematic oppression. We need to talk about our values and reasonable user expectations. Handing passport gives users the expectation that the information will be used. Great work. The [Internet Architecture Board](https://www.iab.org/) is thinking about revising the internet's threat model; this is aligned, and there's a chance for liasion.

**TomL**: Expectation that one is not tracked doesn't mean people can't logged in, it's just not the ambient default. Need to wield the powerful capabilities of the platform without the tracking use-case, which is a bug, not a feature.

**Ian Jacobs**: Setting a vision for the web as a privacy preserving web would make the threat model resonate. Building consensus around what that threat model would be.

**TomL**: Asking for context rather than technical clarifications?

**Ian**: An ideal world model upfront would help.

**Manu**: responding to mnot. Support user expectations as a way to frame things. We should say that tracking by default is an anti-pattern. Any objections to that position? We should also speak strongly against permanent identifiers as email addresses. Should that document say something on that practice?

**jyasskin**: I think there's lower hanging fruit than getting rid of email as login ID. But if there's consensus for that, it should be here. I expect this to be a Living Document. If holes in it are found, it should be fixed. You mentioned that this document should say that tracking is never possible (?is an anti-pattern?). If servers compare logs, servers can track people on the server side, and this is something we can never fix. So prefer to talk about capabilities and goals.

**Alex Russell**: Asked for a model that helped the TAG in design reviews. Would be valuable for a document along these lines that can help guide us towards a better destination. Not having such a model will just end in endless debate, which would undermine the security of the platform.

**dbaron**: what's important is "what happens" vs. "what users expect to happen", which can differ between cultures, envs and can be influenced by user agents. A big piece of privacy is when things are exposed when users don't expect it. Another is, should we try to shift people's expectations?

**Joe Andrieu**: wanted to invite a shift in talking about expectations. User expectations may already be in a bad place. So we can shift user expectations towards an ideal world.

**TomL**: I don't want to set honest expectations, as that'd require a lot from the user agent and impact user experience. Also, using email addresses as IDs beyond the scope of this discussion. We can make that stop with WebAuthn. Sites will still ask for email to spam you.

**Michael Kleber**: What does "tracking" mean? We need to define that. One of the threats is "recognize the same user over cross origin sites". Firefox and Safari have tracking prevention policies which differ. Regarding emails, we totally need to think about the ecosystem implications. A world where all content is behind an email-wall should not be the end state we end up in.

**John Krafcik**: Agree with Michael. A lot of attack vectors but the order in which we close them can impact user goals. Should think about closing capabilities/holes that would push users and developers to other platforms. The goal is to make user's lives more private.

**jyasskin**: What's the venue? PING, CG, elsewhere?

**TomL**: No meaningful distinction. PING would be good

**Manu**: PING, not in CG

**Jatinder**: PING will be discussing IG/CG/WG tomorrow

PING chairs: +1

jyasskin: I'll move the doc to PING's GH. File issues and PRs

[applause]

Note that PING github is w3cping
## Queue

_the queue for speaking is [in IRC](http://irc.w3.org/?channels=%23privthreatmodel)_




