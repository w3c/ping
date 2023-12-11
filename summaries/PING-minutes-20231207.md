# Privacy Interest Group (PING) meeting, 7 December 2023

## Attendees 

* Nick (& Forest)
* Pete
* Philippe
* Jeffrey
* Harun
* Wendell (Yahoo)
* Aram

Apologies: Christine, Kyle

Chair: Pete & Nick

Scribe: Pete & Nick

## Agenda

###  1. Introductions, Code of Ethics and Professional Conduct

https://www.w3.org/Consortium/cepc/

Welcome all (a small group today). CEPC.

### 2. Privacy review

Pete to pass on a report from Kyle, re: Securing Verifiable Credentials using JOSE and COSE

https://github.com/w3cping/privacy-request/issues/125

Pete: how to secure/prove authenticity of the claims in the Verifiable Credentials spec.
Jeffrey: also reviewing it. assertions that a person or entity has certain characteristics. main spec requires that it be secured in some way. either an embedded proof with a signature over an RDF canonicalization. or wrap with JWT/CBOR and a signature over the bytes.

Pete relaying concerns from Kyle's review.

1. highly dependent on the other VC specs, should link to them.
2. formatting: split out different security and privacy considerations
3. security/privacy trade-offs depending on which path you take; spec should describe the strengths and weaknesses. should give guidance to implementers.
4. very many options for implementers, and so you could have a complete implementation without knowing the security/privacy properties of that implementation. spec should either be more specific to implementers, or it needs to rule out options for an insecure implementation.
5. known to be insecure/deprecated parts of COSE/JOSE, should rule out those algorithms
6. don't duplicate definitions

Pete: Kyle's concern on point 4 is a blocking/needs resolution, shouldn't go forward in current form.

Jeffrey: group has started to address point 4. I have left review asking for a better job. I also filed a bunch of issues on the JWT format (defined in IETF); need to tighten the algorithms.

JY: privacy concern if there is an issuer field in the VC or JWT, the implementer might fetch those URLs to check for keys, which would then reveal when something is being presented.
JY: without the algorithms defined, we can't tell if the implementer is doing the right thing. I could add a comment in Kyle's review.
Pete: and Kyle can craft into individual issues.

Nick: why are there large security differences in the different options? seems simple in signature over a serialized set of bytes.
Jeffrey: could use encryption "None", or could do signatures badly, like just doing an HMAC with a public key. can sign JSON, and if processing JSON-LD, you could pull in a context that isn't signed. group is resisting this security-related comment.
Nick: thanks!

### 3. Charters for review

There are a couple proposed charters looking for horizontal review re: privacy. In particular, see WebAppSec and Web Identity Credential.

https://github.com/w3c/strategy/issues?q=is%3Aissue+is%3Aopen+-label%3A%22Privacy+review+completed%22+label%3Acharter

phl: there are several new specs under review.  I've asked the groups to better describe the dependencies and relationships between groups. It would be good to have privacy folks look a this, in particular the identity spec.

nick: there are multiple groups doing web identity credential work, but not all of what we've reviewed before would be work items for this group

phl: this group (WIC) would build on top of some existing work; group does not currently 

pete: not clear how login status is related to the scope of the group

jy: needed a way to indicate to the browser that a federated user was logged in, and so wanted to re-use the Login Status API, which didn't have a Working Group yet

### 4. Privacy Working Group proposed charter

The proposed charter for a Privacy Working Group (which will take over the work of PING and add some normative work) should be ready to go!

https://w3cping.github.io/administrivia/2023/charter.html

Take a look. Goal is to confirm at this meeting that this is ready for Advisory Committee review.

Nick: i think all open issues have been addressed from wide review. In particular we've addresed requested fixes around group dependencies and timelines for work items. We think these issues are ready to close, and we have a complete draft here. I think its ready for AC review. Do others agree?

Pete, Wendell, Aram: yes

Nick: okie dokie, lets start the process for AC review

phl: will do

### 5. Credentials considerations

https://github.com/w3cping/credential-considerations

Brief update: Rick Byers has added his risks.md document to this repo and we will work on merging these texts together.

Nick: this relates to proposed APIs that'd enable browsers to handle high sensitivy credentials.  Rick has added text around risks and mitigations in the orig doc. I have also added some privacy concerns. We now have two documents and it'd be good to merge them into one document. Please add any more issues or concerns you have

### 6. AOB

Next meeting before the end of the year? Depends on agenda items, but likely not.