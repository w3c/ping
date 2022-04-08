# Privacy Interest Group meeting (7 April 2022)

## Attendees (sign yourself in)

* Pete Synder (PING co-chair, Brave)
* Christine Runnegar (PING co-chair, invited expert)
* Nick Doty (PING co-chair, CDT)
* Aram Zucker-Scharff (The Washington Post)
* Don Marti (CafeMedia)
* Sean Harrison (Google)
* Sam Weiler (W3C/MIT)
* Matt Liu (The Washington Post)
* Jeffrey Yasskin (Google Chrome)
* Wendy Seltzer (W3C)
* Wendell Baker (Yahoo)

Scribe: Wendell

## Introductions, and CEPC

https://www.w3.org/Consortium/cepc/

> Be sensitive to language differences. English is the default language of the W3C. However, only some of us are native English speakers. Many participants speak English as a second (or third) language. People who communicate in non-native language often struggle to understand fast and/or quiet speech and may speak louder than they usually would when communicating in their native tongue. If someone struggles to express their thoughts, help ensure their ideas are adequately expressed, heard, and granted thorough consideration. 

### 1. Impressions and takeaways from the Privacy Advertising Technology Community Group (PATCG) meetings this week

A summary of PATCG is solicited.  Aram was MC in the meeting.
Two days of meetings spread across two days.  Reach & Frequency and buyer requiements were covered on the first day.    Ad buyers turn user attention into product.  There was an overview of the World Fedeatin of Advertisers (WFA) work to standardize these methods.  There are experiments nad papers and code.  Trusted Execution Environments (TEE)s and MPC (Multi Party Computation) were overviewed.  This wasw an education session with the capabilities nad limitations of these systems.  There was interactive work on the WG charter and the CG charter.  This discussion should be concluding soon for return to W3C.  Completion ETA is roughly "the next month"

And on the second day an overview of governance was presented.  Some operational experience with MPC using the ENPA system as an example.  Robin Berjon covered the Privacy Principles document of the W3C and the general principles 

Wendell: lots of discussion about what privacy means and what can be accomplished at the tech level vs somewhere else. Robin trying to convey that it's an interactive process, requires community to come together and debate and make decisions. Example of nudity where people know where it is and is not appropriate to be naked, even though it's complex and contextual.

Nick.  There will likely e a charter to review in PING. This will allow us to understand and debate the concepts of privacy in such a group.

### 2. WebXR Device API (https://www.w3.org/TR/webxr/) CR snapshot (changes since our last review)

There is a CR snapshot to be considered.  This will be an update to the previous work.  Pete Snyder will review.

Pete: The first review was a year ago and there were comments returned.  For example the passive fingerprinting capability in the hardware specification was present and whether there was manifest consient embedded in the flow.  The consieration here was whether the consent was exaplicit or implicit.  The resolution on consent is that they will use the same consent model as is used elsewhere, which would be towards manifest and explicit consent ceremonies for high-value activities.

But there is new passive fingerprinting surface added in the new specification.  For example the passive leakage of the possible frame rates supported by the device is now available.  That is not behind the permission api.  So the suggestion is to do a full end-to-end review of the specification.  Pete volunteers to do the re-review by himself or with any others; the invitation is extended.

Sam: this would be a good opportunity for a new reviewer to work with Pete. Don Marti volunteers.  

Pete & Don will pair-review.z

Nick asks whether there is any timely response needed to return to the XR group.   

There is discussion about whether a CR draft has different considerations.  The consensus is that there is more ceremony for a re-review of a CR draft.  A discussion of W3C process considerations follows.  

Wendy relates the history that this request originated in a call for the wide review from the XR WG.  

Pete and Sam disucss whether a wide review needs to happen and under which auspices.  The Director approved the prior need for no wide revew.  But Pete proposes that a wide review is needed because of the substantive changes.  Sam will pass back to the XR WG that a wide review is needed.

Pete and Don will have the review ready for the next PING call.

### 3. Web Machine Learning WG work on ethics for Web Machine Learning

Christine relates information about the WebML WB.  A group note entitled The Ethical Machine Learning note will be produced.  This contains principles of ethics as they pertain to the appliation of machine learning, as sated in the titie.   Further contributions are solicited.  Further contributions in the areas of privacy risks and privacy principles are warranted.  A link pointer to the working document is forthcoming.

Nick: the TAG has The Ethical Web Principles.  
Christine: Yes, this draws on that and also the UNESCO principles documents.

### 4. Charters

* Immersive Web WG
* Timed Text WG
* HTML WG
* Web of Things WG

Sam reviews the ongoing charters as they develop before they go the Advisory committee, rather than having PING review each. Help is solicited in one.  The rest are for informational purposes to the group here.

The Timed Text WG has nothing interesting.

The HTML WG charter may soon be coming for AC review despite my complaints that the WG is not doing the work it is chartered to do.

Wendy relates that the relationship with WHATWG is an inter-organization relationship which poses additional challenges, and the possibilities for change by review are circumscribed. We're still working to develop the work-mode to influence its privacy considerations.

Pete: yes, this is the only WG where Privacy Sections are not required.  Is that the only issue, or is it just the DOM references only?

Sam: that is still on the table, but I've not been pushing it because I thought that PING generally didn't want to.  If that's wrong and you want to continue pushing on it, go for it.

Nick: there are considerations throughout that specification but not a dedicated section.  So the WHATWG may need some help in writing a section that is appropriate for the PING considerations.  The belief is that WHAT WG is open to working together in this way.

Sam: Help around the Web of Things charter is solicited.
https://github.com/w3c/strategy/issues/298

Sam on Web of Things WG Charter observes that this is a difficult and unstructured area.  The area is not as mature as the other areas so the WG charter does not help to resolve the difficulties in privacy rewview and response.  

Pete asks whether the WoT WG group has presented directly to PING or any interaction at all?  By way of background, there are a large number of specifiations, so it may be that direct interaction is warranted here.

Sam: does not remember or see any records of direct contact with WoT WG.

Aram: is interested in engaging with WoT WG. The evolution here seems to be that (regular) Web privacy is evolving in a good direction but the WoT (devices) space may not be evolving in such a good direction.  So participation here is helpful.

Sam: Are there aspects of the WoT WG work that the PING group would like stopped or modified?

Pete: I can look at it for an overview.   This was considered two years ago, so it's hard to see how to proceed without a detailed review.  Many of the responses from the WoT group were pointing towards the incompleteness of certain other sub-specifications so review and modification suggestions where not yet appropriate.

Sam: In 2019 many of the responses were around the impossibility of treating certain suggestions as being impossible in the conceptual architecture of WoT.  But this may be too far back.

Nick: perhaps a general suggestion for an overview of the general architecture should be given, perhaps from the W3C TAG.  That the charter of the WoT WG should be set to include a work product of a general architecture document.  

Sam: Thing Description has had a requested TAG review, not acted on yet. and responded by the WoT WG.

https://github.com/w3ctag/design-reviews/issues?q=is%3Aissue+wot+

Nick: so PING has given some feeback here for Sam to work with WoT WG. 

Nick: a charter strategy issue exists in the PING notes above.


### 5. AOB

Christine on Web Payments
WebPayments has extended a save-the-date to PING towards May to present their work to PING
11AM-local 15:00 UTC 2022-05-04
There will be an agenda prior to the meeting.

Next meeting is 2022-04-21 with a tenative agenda of WebXR.