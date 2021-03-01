# Privacy Interest Group meeting (4 February 2021)

* Peter Snyder (PING Co-Chair, Brave Software)
* Sam Weiler (W3C/MIT)
* Christine Runnegar (Co-chair) 
* Sean Harrison (Google)
* Kris Chapman (Salesforce)
* Wendy Seltzer (W3C)
* Matthew Finkel (Tor)
* Joe Genereux (Brave Software)
* Nick Doty
* Wendell Baker (Verizon Media)
* Sam Macbeth (DuckDuckGo)
* Jonathan Kingston (DuckDuckGo)
* Konrad Dzwinel (DuckDuckGo)
* Theresa O'Connor (Apple)
* Brendan
* Jason Dorweiler (DuckDuckGo)
* Kelda Anderson
* J Lukas
* Theodore Olsauskas-Warren (Google)
* Alexis Menard (Intel)
* Terri Oda (Intel)
* Jeffrey Yasskin

Scribe: Brendan/Sam

## Privacy reviews

### 1. Custom Highlight API Module Level 1 (continued from 21 January 2021)

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

#### Discussion

Peter: Two things to review. Also, what will be better to do better as end

Peter: Matthew, what you can talk about CCS

Matthew: The spec (Nick and I talked about quickly on mailing list) is basically an extension of previous work (CSS enhancements) Allows highlighting sections, spanning elements, and arbitrary pieces of a page.  

Matthew: The main enhancement is to highlight multiple locations of the page, where the current spec doesn't (single part only)

Matthew: I didn't see any obvious privacy issues related to this draft.  The draft itself discloses that the authors aren't aware of.  

Matthew: It's pretty straightforward, not obvious links.  
[no items]

Peter: Thanks, seems pretty cut and dry.  

Peter: Joe, DIDS spec

### 2. Decentralized Identifier Specification v1.0

Reviewer: Joe Genereux (Brave)
  
#### Background

Decentralized identifiers (DIDs) are a new type of identifier that enables verifiable, decentralized digital identity. A DID identifies any subject (e.g., a person, organization, thing, data model, abstract entity, etc.) that the controller of the DID decides that it identifies. In contrast to typical, federated identifiers, DIDs have been designed so that they may be decoupled from centralized registries, identity providers, and certificate authorities. Specifically, while other parties might be used to help enable the discovery of information related to a DID, the design enables the controller of a DID to prove control over it without requiring permission from any other party. DIDs are URIs that associate a DID subject with a DID document allowing trustable interactions associated with that subject.

Spec: https://w3c.github.io/did-core/

Answers to Self-Review: Security and Privacy Questionnaire: https://docs.google.com/document/d/1c36r86oI7q4qv0YKVsu0zlNiMwWTqCfWWReAkg3gd2A/edit#
  
Issues: https://github.com/w3c/did-core/issues

#### Discussion

Joe: This is the first time I have done privacy review.  I work at Brave, focus on crypto and etc. there. The DIDS specification: decentralized identifiers (reading from the spec).  The controller of the DIDs can delink.  Each DID document can link to...  Lastly, this spec common data model, and a few other aspects.  

Joe: Attempt to break down what all this copy from the spec means.  It is a very long spec.  It is also very ambitious, sometimes too ambitions. Lots of jargon and vague concepts, will do best to break it down. The spec covers 4 sub-specs, wrapped into 1
* DID URL spec (new type of ID and syntax) 
* DID Document spec (what the URL resolves to, valid fields for doc, 3 additional sub-sections about representing (JSON, JSON LB, CBOR))
* DID ... tell the curious reader about how to write a subspec for their own. It is overall a how to write, doesn't
* DID Resolution specification.  What it may look like, how it might work.
  
JOE: DIDs look like a standard URI.  We use these all over the place.  URI specification.  
DIDs are simply URIs.  3 parts SCHEMA/Method/Unique, method specific identifier.  They can be extended, to locate specific resource, like PATH.

Joe: Not SME.  DIDs seem to be 3986 compliant.  No problems there.  but concerns with sub-sections.  DIDs are URI how to locate a resource. 

JOE: Subsection part 2 - "document" - This section (and all subsequent sections) might be better to visualize.  Look at spec.  This resource looks like is described in this subspec.  Verification methods, and how to interact with the 
 
Peter: Check with queue
 
Wendell: Was going to maybe try at a high level, but let's continue with the current description.

Joe: Will try to keep it concise.  DID document contains 17 different optional fields (required "ID Property", must match URI). Broken down into categories.  
* Keys, JSON Webkeys and another type.  DID Document of these types are public key.  
 * Service endpoints.  URLs where you could reach the person that the document is about.  
Three other subtypes described.
* DID Method Specification - this is the most interesting one.  Very vague, talks about keys and resolution thereof.  Doesn't give details beyond that, especially not privacy and securtity implications.  Does reference "DID Method" that doesn't exist (someone would need to write that)
* Resolution Spec, not detailing, the authors don't think it will stay in.  
* One section from the Privacy Questionnaire: "The questionnaire applies to the DID Core Spec, but this is just rules for writing other stuff, each DID method spec might have additional privacy and security implications"
  
Joe: The DID spec authors wave their hands and sidestep privacy/security and leave it up to the subspec authors to deal with it. Does leave a big section to discuss this, but doesn't deal with it exhaustively. We in the working group should scrutinize subspecs, because the current CORE spec leaves a big, open hole.  
  
Joe: I went deeper because it's complicated.  

Peter: Thank you Joe, Wendell in the queue.

Wendell: Very sympathetic with this work.  Verizon has an open-source implementation of these similar ideas.  https://github.com/yahoo/tunitas-scarpet. Mostly vision at the moment. The whole DID theory and ideas is designed to be unassailable in the privacy space. It consists of a couple of components, Core / Peripheral. The peripheral ideas add functionality. The system is for identifying people, devices, software agents without central system, but with public/private keys. Many kinds of crypto that degrade over time.  The software is always the same. There is a private part that is never revealed, there is a public part that is broadcast everywhere. In more advanced forms, the public part is more than just what we see in PKI.  
The public part needs to be registered somewhere.  Using decentralized is a preferred way of doing it, for variety of reasons.  Number of implementations. Hyperledger foundation had many diff proposals for what is best decentralized tech, ultimately they generalized.  Versions on Ether / Bitcoin / Fabric / etc. They used web standards for JSON, SEBOR, etc., for transmit on the wire or point at things in a document. Document is a special word, to capture what it means to look up a thing and find something. The pointer to other things is the important thing. The sidestepping of privacy is intrinsic. On the other side of the DID document, when you contact the things that are being pointed to, there are privacy implications (mail, social). The document needs a few things - Proof that it's your document, that it pertains to the ID that it purports to be about.  
  
Wendell: My POV, I can extend DNS and have a registry for these things, as well.  Since my company is a DNS operator, this is easier. You just need a registry, whether it's DNS, Blockchain, etc.  Other people need to look up. META DID Registry, a registry of registries. In the same way that IANA has a list of known numbers, hand curated. Service discovery problem. In this community, this is an important framework for looking at this problem. The DID document itself: there's no problem of concern there, but there might be concerns about the services or the presentation of the services being pointed at. The notion that there are public/private keys and their use model, but it's not exactly the web, it's straight up crypto.  There are key recovery thoughts, how you might move or delegate keys, in-service of other scenarios.  Broad theory of social governance, but this is probably out of scope.  

Nick: Haven’t read details spec.  How is this similar to Webfinger?  Webfinger is not abstract, so how is this different?  What is the rationale for developing a totally new spec?  Can we take a chat with the people who reviewed Webfinger?  [rfc 7033 does have specific privacy and security considerations, which we might be able to apply.]
  
Joe:  Not familiar with Webfinger. DID spec is first of many.  This is just the language; the umbrella.  Maybe Webfinger could sit under that?  When DID methods start to emerge, PING will have to pay attention to those.
  
Christine: first reviews aren't easy.  This one looks complicated; thank you!
  
Pete: this feels familiar to Web of Things reviews; not obvious which part of system is where the privacy issues land.  
  
Wendell: this issue big enough that we should have meta- discussion.  Idea of Web having an identity layer is historically controversial.  WedID is another proposal trying to establish similar.  VC is from same people.  Would be helpful for PING to have opinions on identity schemes in general.
  
Pete: Joe, Any general thoughts here?  
  
Joe: at an org level, this often comes down to legal teams. Big debates re: whether public keys on a blockchain are PII or not.  Decentralized space is wild west.  No place to punt this to; many orgs punt to legal.  GDPR came out when blockchain wasn't big.  DID spec is abstract because it has to be; if it tried to tackle everything, it would never get through.  We have to look closely at the DID methods and related techs.  
  
Wendy: thanks Joe and Wendell for breaking down the levels.  As people get into the implementation, lots of privacy questions.  Any guidance we can give the people working on the next level of spec?
  
Pete: how to catch larger concerns?  this spec?  something later?
  
Joe: this is not the place; e.g. if you look at URI RFC, it can't address all issues with URIs.  Just not possible.  treat the DID spec in that light.  e.g. when spec for DIDs in the browser emerges, need to consider requirements for not spoofing.  treat this as an umbrella; let it go through.  community has put a lot of time in.  be mindful of the future.
  
Christine: Thank you for the clarification.  I prefer to have some languages in the security and privacy considerations section flagging that, as a reminder. 
  
Joe: they've alluded to that.  I'll file a new issue and talk to spec editors.  Good idea.
    
Sam: I have background in the DNS space, and in that space, there isn't a concern for privacy of the name, but there is once you can enumerate them.  SO the concern isn't the DID; it's what's wrapped around it.  Is that an apt analogy for DIDs?
  
Joe: yes, that's fair.
  
Pete: there are uses here that seem concerning.  Best path is a message in the privacy considerations section.  
  
Matthew Finkel: re: DNS, not only enumerate, but also what name you're looking up.  I wonder if there will be similar concerns when looking up DIDs in registries.  Keep in mind for future. I asked on list re: places where we track issues; Sam pointed me at the tracker.  We should make sure this is included in the tracker, so we can refer to it in the future.

Pete: thanks to Joe; this is an enormous spec.  
  
WebFinger RFC 7033 https://tools.ietf.org/html/rfc7033#section-9.2

### Privacy review questions

Pete: want to reflect on questions from people who have done reviews (for the first time).  What can we do as a group to make that easier?  Docs? Tooling?  What lessons can we learn?
  
Christine: the buddy system has been great.  thanks to Pete and others who have offered to be the second person and provide wisdom.
  
Nick: Thanks to Sam and others at W3C re: issue tracker; review comment tracker has come a long way.  It seems really useful; we always wanted this.  This makes the value a lot clearer.  Maybe needs to be documented better.

https://w3c.github.io/horizontal-issue-tracker/?repo=w3cping/tracking-issues
  
Sam: most of the credit goes to PLH.
  
Pete: this is an ongoing topic; feel free to raises questions on Slack or on calls.
  
Matthew: I wasn't exactly sure what guidelines were for reviews; I scavenged questionnaire and using Tor's internal process and looking at previous examples.  After the fact, I asked about having a table collecting the review outcomes.  One addition that could be helpful is documenting these resources.  Maybe a template re: how to open issues; should we say we're reviewing for PING?  Any experience we can use to make it easier?  Could be a living doc?
  
Pete: I'll draft something before our next call.
  
Joe: maybe it's because I started with a big spec; my common point of reference was the questionnaire.  That's where I postured my stance.  Knowing there's the tracker is great.  I attended the mtg 2 weeks ago, and I was still unclear today how deep I should go.  I needed to understand what the goal was.  The questionnaire was a good starter.  
  
Pete: I'll run this new doc by you, too.
  
### AOB

Christine: Invitation to PING members to provide feedback on ED of The Responsible Use of Spatial Data - https://w3c.github.io/sdw/responsible-use/
  
