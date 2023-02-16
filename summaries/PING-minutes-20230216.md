
# Privacy Interest Group meeting (16 February 2023)

## Attendees 

* Christine Runnegar (co-chair)
* Peter Snyder (Brave Software, co-chair)
* Chris Lemmons (Comcast)
* Don Marti (CafeMedia)
* Philippe Le Hegaret (W3C)
* Boris Hazanov (Shopify, Engineering program manager)
* Tom Van Goethem (Google)
* Wendell Baker (Yahoo))
* Aram Zucker-Scharff (The Washington Post, 10m late)
* Jeffrey Yasskin (Google)
* Eric Mwobobia (last 15 mins)

Scribe: Pete, Don

## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/) 
 
### 2. Privacy review of CSS View Transitions
  - Reviewer: Pete

Pete: CSS view transistions proposal allows a document to describe what it looks like when you navigate to anotehr document (example, cross fade)

Apply CSS to state of transition between 2 documents

Images, not live DOM content, can move, fade, other transformations. Previously needed 2 version of everything on the page, like a SPA. This allows SPA like features when navigating

2 privacy concerns, one difficulty

naming is confusing, each element being acted on has 4 elements: the first is the "group" 2nd is reference to 2 images, last 2 are images (group as a term is confusing because it applies to both the group and the 1st member)

2 concerns may or may not be part of this proposal, need to read explainer text to unddrstand 4 corners of proposal -- not clear if parts of this spec, need to talk to group to understand

if doing a cross origin navigation it seems like the previus page is given the ability to cancel navigation, gets element being navigated to as an event (?) If going through bouncing or mitigations applied to the URL by browser the from page does not have access

If a link gives you different destinations if authenticated or not then the source page may receive info that it would not have otherwise. May or may not be part of this current proposal, if so it could be a privacy harm. If not possibly edit this proposal

2nd concern: not sure if JS has access to pixel data. If the page does get access to pixel data then these methods might be usable for attacks similar to canvas fingerprinting (if introspect of pixel data than could be many risks) need to understand this access and if part of this spec

Philippe: naming comment may not be an issue, could be a bikeshed issue, not a privacy issue Focus on privacy in this review, 

Pete: 2 labels can be provided: privacy and needs resolution -- can be applied separately to indicate if a concern is not a privacy concern

Christine: sometimes we notice a non privacy issue in a spec when doing a privacy review, not privacy issues just identified at the same time, if they need to be raised they can be raised as a non-privacy issue

Philippe: If the group cares then they can be put in, could be weird but if it helps, fine

Pete: Will file issue separately

Philippe: if issues do need to be filed, do so. We will pay careful attention to those tagged with "needs resolution"

Tom: question, as far as I know view transitions is only cross document on the same site

Pete: in the explainer it talks about cross origin navigation -- not clear if this is part of the spec, or has it been moved, will check with group

Tom: in security and privacy considerations it is disclosed that script can not read pixel content

Pete: If script can't read pixels this goes away

Jeffrey: important to disclose what parts of spec are for review and which are just disclosing possible future directions -- authors of explainers need to make that clear

### 3. Privacy review of Autoplay Policy Detection
  - Reviewer: Pete
  
Pete: this is a small api that allows page to detect if autoplay is allowed

Call on document or on media elements in document, get back a small set of possible results

privacy considerations seem incomplete, lists things that spec does not do. Not helpful but not a blocking concern

different browsers do different things to decide on auto playing media. In some cases may be relevant to other things going on at the same time, like is another page playing media. May reveal other activity on the system

Might be new information that could disclose a system preference or cross page info leagkage. If the user has a preference to not allow auto play media then that could be a fingerprint big THis issue might go away, needs mention in the privacy considerations section

Browsers do this because they don't see page as acting in users best interest. Might not be in the user's best interest to disclose.

Disclosing to the page that a video is playing muted might cause the page to do something that could be hostile to the user. Hard to split the user harming from non user harming cases. Maybe in non normative text, not discussed, seems like a tradeoff

Jeffrey: these items need to be disclosed in the privacy considerations stection, let browsers know to be careful when disclosing info. Disclose that we are awayre of the fingerprinting risk. Do not make it depend on what other tabs are doing to avoid the leakage risk. Implementations need to be careful

Pete: will file issues

Jeffrey: privacy considerations is normative
  
### 4. Privacy review of PNG 3rd edition
  - Reviewer: Aram
  
#### Notes (written by Aram not minuted)

- https://github.com/w3cping/privacy-request/issues/105
- Changes: [Portable Network Graphics (PNG) Specification (Third Edition)](https://www.w3.org/TR/png/#changes-since-the-w3c-recommendation-of-10-november-2003-png-second-edition) 
- User data encoded on the fly at Edge in response to a user request? 
	- [Security considerations: malicious data after `IEND` · Issue #170 · w3c/PNG-spec · GitHub](https://github.com/w3c/PNG-spec/issues/170) 
	- [PNG and Hidden Pixels - The Hacker Factor Blog](https://www.hackerfactor.com/blog/index.php?/archives/894-PNG-and-Hidden-Pixels.html) 
	- Can encode user data and rely on local cache of images to reidentify the user? User returns to site, local cache image loads, JS operates on it? Is this possible? 
	- [RATs Wrapped and Hidden in PNG | Trustwave](https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/rats-wrapped-and-hidden-in-png/)
- Data encoded in EXIF and [tEXt](https://www.w3.org/TR/2022/WD-png-3-20221025/#11tEXt), [iTXt](https://www.w3.org/TR/2022/WD-png-3-20221025/#11iTXt), and [zTXt](https://www.w3.org/TR/2022/WD-png-3-20221025/#11zTXt) chunks
	- [Extensions to the PNG Third Edition Specification, Version 1.6.0](https://w3c.github.io/PNG-spec/extensions/Overview.html#K.Keywords)
- BOOKMARK: [Portable Network Graphics (PNG) Specification (Third Edition)](https://www.w3.org/TR/2022/WD-png-3-20221025/#11tEXt)
- In theory, a lot of things can be encoded in the PNG chunks or in the leftover encoding space. 
- > When a fatal condition occurs, the decoder should fail immediately, signal an error to the user if appropriate, and optionally continue displaying any [image data](https://www.w3.org/TR/2022/WD-png-3-20221025/#dfn-image-data) already visible to the user (i.e. "fail gracefully"). The application as a whole need not terminate.
	- Intentionally partially rendered images could be used as part of a fingerprinting process that also looks at page height or height of elements on the page. 
	- Early termination can clearly be an issue of transmitting some sort of fingerprinting vector. 
- > A PNG datastream is composed of a collection of explicitly typed chunks. Chunks whose contents are defined by the specification could actually contain anything, including malicious code. But there is no known risk that such malicious code could be executed on the recipient's computer as a result of decoding the PNG image.
- There is a history of trackers using image serving as a vector. 
- Privacy considerations open in three major areas 
  - Height can be interfered with to change the DOM, either through the chunks included or through interfearing with the bitstream 
  - Arbitrary chunks can be cause interference with the rendering process. 
  - Chunks can encode private data 
  - Text chunks, especially the elevation of Exif to the main spec, can encode private data on edge responses and be used to communicate between parties for whom communication is intentionally not intended to exist. 
  
#### Discussion

Aram: These changes are mostly around metadata bits, and incorporating animated PNGs (APNG).  There is no privacy considerations section (maybe bc it wasn't needed when the prev version of this was written).

Aram: The group did not identify many privacy concerns, and I (Aram) agree, there don't seem to be PNG-specific concerns, more about things that can be encoded into images broadly

Aram: The spec includes text about how to handle early termination; this could create a communication channel possibly for a fingerprinting flow

Aram: There are rendering ambiguities in how browsers should render partial images, this could form a cross-site flow (?)

Aram: There was an issue in Apple's PNG decoder which could cause images to look different on Apple (ed: sites? devices?) vs other sites (or devices?)

Aram: This spec also standardizes EXIF data in PNG images. This opens possibitilies for unexpected / covert information flow. It would be good for the group to mention in their privacy section

Aram: The new spec includes "private" chunks, which are non-standized metadata. For example, Apple's PNG encoder included metadata that allowed Apple's PNG decoder to operate more effectively than other decoders. This could also form the basis of a covert channel.

Aram: Other ways that data could be encoded in PNG (and so create a covert channel) is in specified metadata (pallet, information about hidden pixels, etc)

Aram: In summary, i. chunks could encode data in PNG's so could be used to create covert channels, and ii. the same can be done through text chunks, and iii. whether or how the image is decoded can also be used to create a covert channel (and how the image renders could reveal info about the decoder being used, so possibly a fingerprinting risk)

Pete: I think these are covert ... I heard "cross-site", but these are covert channels, not new communication channels. Things that communicate already can now communicate in new ways. Right? 

Aram: With the exception of the EXIF chunk. Which wasn't in the spec and is being added. Can have all sorts of data.

Pete: But anything in the EXIF chunk could have been encoded into other places. Not a new communication channel.

Aram: Yes and no. When it wasn't on spec, it was still widely recognized. In theory, a PNG decoder discards unrecognized chunks that aren't vital for recognizing image. So many decoders probably were discarding the chunk. But now that it's in the spec, maybe some decoders will stop discarding them. Anything that intends to recognize EXIF chunks probably already does so. But it's still notable for moving up the standardization level.

Pete: Want to separate new ability to send information from new ways to send information that could already be sent.

Aram: Maybe we just want them to explore this feature in their privacy considerations.
 
Christine: Maybe thats an answer to Aram's Q then, with what to do about these issues.  Privacy considerations section then

Pete: How to do a privacy review -> https://github.com/w3c/ping/blob/main/howto-conduct-a-privacy-review.md
 
Jeffrey: These seem like new ways that sites that can already communicate, to continue communicating, not new ways new parties can communicate

Aram: Maybe not.  In browsers third-parties are (sometimes) partitioned, this would allow a partitioend 3p to communicate to the 1p

Jeffrey: Agree, but seems like as long as partitioning works, this creates a new 1p <-> 3p communication w/in a partition, not a way of communicating cross-partition 

Aram: 3p could have data it doesn't want to share with the 1p site though, and so thinking about data 3p partitioned data as being distinct from the 1p is important

Jeffrey: sounds like this is a new channel that sites can do things they already can do
 
### 5. Report out from PATCG F2F 
  - Report: Aram
  
Aram: PATCG met in person in NY, first day focused on org issues. For example, the charter has received objections, and so the chairs split those into issues and PRs. Several PRs were merged to try and address raised objections. Consensus was reached for a lot of issues/PRs. There are a few still-open PRs on the charter though that need additional conversation. Hopefully we'll have a new charter submission by the end of next meeting.

Aram: Critio and Google gave "industry reports", Google presented results from Topics API experimentation. It _did not_ come up that Google is restructing where Topics API information is coming from 

Pete: Where is topics going?

Aram: I'll share a link 

PlH: you should check out the Google response to the TAG's position (https://github.com/w3ctag/design-reviews/issues/726#issuecomment-1424728951)

Aram: main change is moving from domain level to page level

Aram: Also took a poll of particpants, on whether private measurement was of interest, in scope, and particular propsoals.  Here is a link to histograms  https://docs.google.com/document/d/1bydwuN0_K2anOZV41xNJn1Kt0vt9WPOkf56ESnmQ5_A/edit?usp=sharing 

Aram: Day 2 we considered possible future proposals and participant experiences around proposed work items.  Everyone in the group/room (inc Apple) agreed off device computation could be part of a private measurement proposal.  Possibly multiparty compute (?). 

Aram: We want to lock in meeting times going forward. 

Pete: please provide links to MPC propsoals for private measurement
 
### 6. AOB

Christine: We need reviews for the below issues

PlH: Nick is going to work on EPUB, Secure Payment needs eyes

Pete: We might have someone coming at the start of next month for Payments

Aram: I can do Compute Pressure API

Christine: Boris, can you look at the WCAG one?

Boris: I could but will need help

Chris: I can help



