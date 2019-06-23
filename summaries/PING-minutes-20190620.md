# Privacy Interest Group meeting - 20 June 2019

## Attendees

* Tara Whalen
* Peter Snyder
* Matthias Kovatsch
* Tom Lowenthal
* Sam Weiler
* Jason Novak
* Pranjal
* Mike O'Neill
* Kaz Ashimura
* Nick Doty
* Taki Kamiya
* Brent Zundel
* Terri Oda



## Minutes

Kaz: presenting the WoT / IoT description and arch.  The documents describe both a data model and a scripting API for having IoT devices communicate.

-> https://w3c.github.io/wot-architecture/ WoT Architecture
-> https://w3c.github.io/wot-thing-description/ WoT Thing Description

Taki, Matthias: also joined from the WoT / IoT group 

Sam: the documents are long, can you provide a brief summary of whats being targeted, what issues are covered in each doc's S&P sections.

Matthias: the document attempt to summarize how IoT systems communicate, and some use cases.

to be Web of Things, rather than just IoT, devices follow some basic Web requirements: use URIs, IANA-defined media types, affordances following a REST model, discovery of devices, etc.

pes: seems like there is more identification of privacy risks, but not as much on the privacy mitigations. can we get more of that?

Matthias: there are mitigations discussed in the privacy sections, and in other documents

tom: the mitigations are not specific, but the privacy harms are well defined.  this means that implementing the spec doesn't guarantee a privacy preserving implementation

Matthias: its implementation specific.  This is about interoperability.  But is it practical?

tom: privacy concerns do relate to interop, since implementors will need to implement the hightly detailed spec, and not know how to do privacy-preserving interop

Matthias: example: spec describes a URI, but it could include sensitive data or not

tom: yes, exactly, the privacy preserving behavior is not as well defined as the general behavior

Kaz: this is intended to be covered by the follow up document

Scripting API (a topic where some thought there should be more specific privacy requirements) is being moved to Note rather than Rec-track status, because of a relative lack of implementation interest and differences about API design.

pete, tom, Kaz: much concern whether these documents should be privacy preserving, or whether thats better to come in a future document.  

Jason: tries to cut the knot.  The schema document as is currently describes identifiers that can be privacy harming.  The point is well taken that future documents may describe that the values stored in the id should be privacy-preserving, but that it'd be better to define the vaule to not allow harmful values in the first place
... it's possible that a stronger statement would be that it isn't good to recommend the presence of an identifier in the schema without a mechanism for limiting its persistence

tom: yes, it'd be better to either consider this along side the use of the identifiers, or to define the schema to not allow the storing of harmful values

Taki: mitigations are described in the privacy considerations section.  The privacy considerations section was the result of much consideration of different risks.  It'd be good to include links to the privacy risks section from the description of the schema

tom: i think thats a misunderstanding, or different from the recomendation.  The request is not to raise the concern in more locations, but to strictly descrive how the risk will be addressed

Kaz: this spec is a data model, but the use cases it describe are not privacy-harming b/c they're not about humans

tom: information from devices related to a person are also privacy signifigant, since they describe a person

Kaz: this is a group note, we thought about privacy concerns

sam: seconding tom's concern; just b/c the devices aren't recording info specifically about humans doesn't lessen the privacy risk

tom: ex, does the spec address capailities for tracking?

Matthias: difficult to standardize since there are many possible use cases.  It seems like you're asking too much, you'd have killed HTML since it didn't include OAUTH

tom: no, more apt comparison is HTTP since it involves privacy harms (e.g. cookies).  The time to figure out what identifers can be safe is before the standard gets passed

Brent: charter prohibits the group from modifying protocols that'd use the data

tom: if the charter prohibits them from addressing, then it should be rechartered

nick: the abstractness of the document makes it difficult to review, provide recs.  Identifiers are a good example though; the spec says unique, but how unique?

Taki: we're using this on JSON-LD, which includes references to URIs.  We discuss the uniqueness of the ids there, for example

Matthias: the data model can be parsed with JSON-LD documents, so the id maps to an identifier in a knowledge graph.  In a linked data framework, its an IRI identifier.

Tara: we're running short on time, but we're greatful for Taki, Kaz and Matthias's time.  Whats the best way to follow up?

Matthias: github and issues

Tara: deadlines?

Kaz: we'd like to have this approvied today.  But we're going to publish this as is. have already started second version, where we could review more detailed comments.

Tara: thanks for joining, we'll pass comments on to GH


## Private browsing modes docs

Sam: what did folks think about the TAG private browsing doc

Pete: I thought it was not much, the PING generated doc is process focused

https://github.com/w3cping/privacy-mode/blob/master/private-browsing.md

Jason: TAG doc seems to have conflicting goals / be internally inconsistant, AC meeting seemed to suggest lets get more private in default case

Sam: what should we do w/ the current TAG document?

Nick: i think the TAG document is useful b/c it states private browsing modes should be indistinguishable from standard modes. and if we agree on that as a goal, that's useful (because it helps us in providing recommendations on specs)

## Meta-discussion

Jason: it'd be good too have alternate venues for feedback and review, metaprocess, and PING meta / internal discussion.  I don't want to take one of the normal monthly review calls for it, because docs still need to be reviewed.

Tom: seconded

tom, Jason, tara, sam, others: lets talk next week if possible about process.  We'll run it by the list.  Failing that, we'll fall back to July 11th.


## Non-transcript'ed notes

npd: I could talk June 27 or July 11


Mike: Why is the Thing's unique identifier mandatory?
	npd: I wonder if maybe the identifier could be described as unique within a local network (because it's needed to distinguish between devices and contact them), but not globally unique
	... if identifiers could also be left out (apparently an open question?) and then used as blank nodes, that seems like a pretty dramatic difference in terms of providing persistent unique identifiers
