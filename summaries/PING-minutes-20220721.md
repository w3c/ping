# Privacy Interest Group meeting (21 July 2022)

## Attendees 

* Pete Snyder (Brave, co-chair)
* Sam Weiler (W3C)
* Wendy Seltzer (W3C)
* Nick Doty (CDT, PING co-chair)
* Christine Runnegar (invited expert, PING co-chair)
* Wendell Baker (Yahoo)
* Andrew Aikens (TripleLift)
* Aram Zucker-Scharff (The Washington Post)
* Providence Baraka (Article 19)

Regrets: Don Marti

Chair: Sam

Scribe:  Wendell

## Agenda

### 1. Welcome, introductions, code of conduct

If you make a mistake in the CoC behaviors, stop, briefly acknowledge, apologize and move on.  Don't explain; don't minimize.
https://www.w3.org/Consortium/cepc/#mistake

### 2. Privacy review of DCAT 3 (https://github.com/w3cping/privacy-request/issues/90)  (Nick)

https://www.w3.org/TR/2022/WD-vocab-dcat-3-20220510/

[Nick] There is a terminology issue with the 'catalog' word in this request.  This is about metadata.  The use case is about search for data sets across a wide range.  This is different than what we usually treat with privacy reviews. The team did the review using the Privacy Questionnaire, but did not find the questions that useful for their use case.

A vocabulary for metadata should have a vocabulary set that pertains to the domain at hand.  For example, if there are privacy-relevant aspects about (personal) data then the vocabulary should reflect that stance.  This sense seems to be missing from the standard.

There are vocabularies for distribution requirements, availability, and copyright, but not copyright.

The data set is often a service rather than a set which can be copied.  When data sets are not copyable, but rather are only available from a service-oriented API there are opportunities for privacy-centric features such as Differential Privacy, privacy budgets  and so forth.  The vocabularies do not directly enable this sort of characterization.

The sense of provenance is not adequately characterized in the vocabulary, especially the sense of authenticity.  While there is a checksum to characterize the bit-level consistency, there is nothing higher-level in the scheme.  This is more of a security concern rather than a privacy concern.  It is however not specifically addressed in the standard.

[Sam] these concerns should be documented.

[Nick] I have not opened issues.  I worked with Lubna.

Issues
1. Privacy-relevant Vocabulary
2. Authenticity
3. Service-Oriented Sense


Andrew Aikens introduces himself.  Andrew is with TripleLift.  He is with Privacy & Identity solutions at Triplelift.

[Sam] is chairing this meeting because Pete, Nick & Christine, the usual co-chairs are reporting 

### 3. Privacy review of Baggage (https://github.com/w3cping/privacy-request/issues/94) (Pete)
Spec: https://www.w3.org/TR/2022/WD-baggage-20220617/

[Pete] This is the same as the Trace Contacts Spec.  It has some headers that describe metadata about distributed events.  The specification does not define the sorts of values that can be captured in the headers.  The receivers have a great degree of flexibility in treating the data, interpreting it and passing it on.   The Trace Context proposal which was reviewed in PING around a year ago is very similar.  

The sense is that privacy protections of Baggage are fewer than those in Trace Contexts.  It would be helpful to understand the differences between the two specifications.

The second concern is that there are other ways of encoding name-value pairs such as HTTP Structured Headers.  It would be helpful to understand why a new standard is required.

The standard should be more clear about what privacy guarantees are afforded in the web context (in a browser).  While it is understood that these headers will be used in other contexts (AMPQ and MQTT are cited in the spec), it should be clear what happens in the Web context.

[Sam, Aram] is this an HTTP header discussion?

[Sam] the standard is not clear how this should be used.

[Pete] the context that I used was that of Trace Contacts from before.  But if it is otherwise unclear how the specification should be used then that should be fixed.

[Nick] Would like a clearer explanation of the differences between Trace Context and Baggage.

[Pete] There is not a perfect containment relationship between the two use cases.  For example, where Baggage has a single header for certain purposes, Trace Context has multiple headers.

[Nick] But, it's the same use case?

[Pete] Yes.

[Nick] How should the web case work for the browser origin boundaries?

[Pete] I was considering this to be the same as the Storage same-site boundary

Pete will file three issues.

### 4. Privacy review of CSS Color 5 (https://github.com/w3cping/privacy-request/issues/92) 

Deferred until next time.

### 5. Privacy review of Web Neural Network API (https://github.com/w3cping/privacy-request/issues/96) (Christine)

Spec: https://www.w3.org/TR/2022/WD-webnn-20220630/

The Web Neural Network API defines a web-friendly hardware-agnostic abstraction layer that makes use of Machine Learning capabilities of operating systems and underlying hardware platforms without being tied to platform-specific capabilities.

[Christine] this is a very nice privacy request.  It would be great if others were as well done as this.  They highlight the privacy concerns and affordances.  The specification describes use of data on-device and the minimization of information.  The specification is unclear with clarity that the fingerprintability of the implementation is not completely characterized.  Some examples will be forthcoming here.

For future consideration are the future fingerprintability conditions that might arise with new devices. The advice is that implementors are expected to apply privacy considerations to their implementations.

With respect to the power preference hint, there is a fingerprintability consideration, perhaps. This needs to be clarified given that this is only a hint.

Ethical considerations are also included.

[Nick] there is a smaller scope of a privacy analysis of a specific standard or specification or a larger consideration of privacy implications of larger uses of technologies (for example, emotion detection, sentiment detection, facial recognition and so on).  The work process here deals well with the smaller considerations and mitigations. It does not do so well with the larger considerations or the ethical considerations of the application itself.

[Christine] yes, acknowledged.  However, the team also considers some of the features as privacy-affording which the review team often uses as wedge issues to show the privacy dangers of the technologies.  So, we must look to the ethical statements and the vision statements for the use cases.  At least there should be warnings in the specification which acknowledge the difficulties with perhaps how to mitigate the problem.  For example, to try to put processing at the edge or on the device rather than in a central server.  Suggestions are welcome.

[Nick] Agreed.  Perhaps a deeper analysis of the actual damage that can occur and the transparency & control that is afforded by alternative approaches. A clearer, more prescriptive recommendation set is warranted here.

[Christine] Let's follow up.

Wendell: Yes, prescriptive advice is more helpful than platitudes. facial recognition on-device vs off-device, reducing a face to a print on device could actually create false positives by trying to reduce the amount of data.

[Pete] The issue is not the specifics of where the work is done, on-device or on-server, but whether the API allows a specific activity and whether there are policy or user controls around that affordance in the API. explicit API vs just doing low-level GPU calculations, and explicit API makes it easier to turn on/off.

[Aram] There are two considerations in this sort of analysis.  The consideration that technology can be used for bad activity is out of scope because such can always occur.  The second consideration is whether there are controls, transparency or consent.  Consent is not usually the preferred route to mitigate.  Another approach is to have a clear allow/disallow list to be applied. Whether this is sufficient in general warrants discussion. The question of a dialog should be more clear about what sorts of activities are being undertaken by "the learning" for the purpose of user-to-machine dialog.  For example, to ask whether machine learning for X or  Y is to be allowed rather than merely asking whether the user consents to "the use of machine learning"  There may be places in the Permissions Policy or in the Navigation API can host this sort of affordance.

[Christine] thank you for the feedback.  The follow-ups will be around acquiring more detail towards making the recommendations more concrete.

[Pete] I don't understand the fingerprinting concerns. Especially the consideration of the hint not being a fingerprintable feature.

[Christine] the issue is to ask questions about its capability and on to [Nick]

[Nick] the classification as a "hint" does not mitigate the utility as a fingerprinting feature. The treatment can be towards the state of mind of the developer (of the software) rather than the user.  The user does not choose the power mode of high-or-low or such.  Of course, if the user was able to control this feature directly then this could be a fingerprintability feature.   Either this is a developer-controllable feature, a browser-settable feature or a user-settable feature; each has different treatments as a fingerprintability feature.  The default value versus the non-default value (exceptionally set) would be revealing.

[Pete] the issue is more about whether the API can answer differently and the range of answers that it can give at all is the fingerprinting feature space.  

[Nick] how one might be able to learn about the hardware through this API is the issue here.

[Aram] The developer has the ability to make a choice, and there is a default operating mode.  If the API can answer back with a refusal to move to a different mode then this may not be a fingerprintable feature.  Also, if the power mode is optional then it isn't clear that fingerprintability concern is at the same level.

[Nick] Yes, this is an optional feature, so it is weaker.

[Aram] this is different than the pixel depth use case which is clearly fingerprintable but has a use in serving different files from a script or server. I'm unclear what the developer use is.

[Nick] There doesn't seem to be direct feedback from the API that the power mode request was accepted.  It is just a hint.

[Nick] This concern needs more clarity in the feedback because it isn't clear here whether the hint is fingerprintable or not.


