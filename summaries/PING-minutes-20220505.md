# Privacy Interest Group meeting (5 May) 2022

## Attendees 

* Christine Runnegar (PING co-chair, invited expert)
* Nick Doty (PING co-chair, CDT)
* Sam Weiler (W3C)
* Wendy Seltzer (W3C)
* Sean Harrison (Google)
* Erc Mwobobia (ARTICLE19)
* Aram Zucker-Scharff (The Washington Post)
* Theodore Olsauskas-Warren (Google)
* Jeffrey Yasskin (Google Chrome)
* Don Marti
* Tess Hober (Apple)
* Wendell Baker (Yahoo)

Scribe: Sam

## Introductions, and CEPC

https://www.w3.org/Consortium/cepc/

### 1. Update regarding privacy review of EPUB 3.3 (Nick)

Nick: I did the first review some time ago.  EPUB is an eBook standard; mostly used not-over-the-web.  They had no privacy considerations before; got them started on threat modeling.  WG came up with long privacy considerations sections in 2x specs, defining a threat model and mostly not mitigations.  They closed issues and are moving to CR.

They addressed some things re: obfuscation, not DRM, but making it hard for people to reuse fonts.  DRM is the biggest harm today: can't view source on the book.  Their charter prohibits them from doing anything different with DRM; no progress; don't expect that to be resolved.

Security things that might be fixed, e.g. re: loading resources over secure transport.  

There is a reading system string about which system is reading the book - compare to UserAgent string.  Some implementations may have both.  I'm concerned about repeating that mistake; not limiting entropy.

The long text about what could be done is non-normative.  e.g. "don't track what users do".  Not sure what to do when we're punting enforcement to another layer.  Past spec had a normative section, but no one followed it.

Sam: could some of these things be fixed technically, in this layer?  I'm less a fan of policy solutions.

Nick: could have normative reqs in spec.  Not market appetite to make technical changes.

Don: could constrain the DRM sandbox, but can't look inside.

Nick: DRM is special case.  We're not even trying at this point.  Should w still have this aspirational guidance?

Christine: important to have content, even if non-normative, because if entities are ignoring it, it gives something to point to as best practice / community expectations.  Would like to see some of it normative; e.g. constraints on DRM.

Sam: non-normative text and analysis still helpful. what's capable is more of a question for charter-time, and depends on who is willing to participate. 

Nick: lots of responses from group re: the charter requiring backward compatibility.  I'm going to open or reopen a few things.  They're planning a CR transition.  Not sure which should be blocking.

Sam: I prefer fixing pre-CR.

Sam: there was a 3rd spec - on a11y - that they hadn't asked us to look at before.  Anything new on that?

Nick: it doesn't add features; I wasn't worried.

### 2. Privacy review requests from the Web of Things WG (Sean)

- Web of Things (WoT) Thing Description 1.1 2022-04-27 > 2022-05-15

See: https://github.com/w3cping/privacy-request/issues/84

- Web of Things (WoT) Discovery 2022-04-27 > 2022-08-30

See: https://github.com/w3cping/privacy-request/issues/83

Issues raised:
- https://github.com/w3c/wot-thing-description/issues/1490
- https://github.com/w3c/wot-discovery/issues/303

Sean Harrison: this was my first PING review.  I was confused about the spec coming through W3C; not really Web.  3 reviews requested; last one was just this Tuesday.  Thing Description (TD) is about endpoints.  They call out that these should not have keys/passwords.  These all have IDs; there is no need for global uniqueness; but there is a caveat that they have immuntable unique IDs by law.  I propose they require anything with these not emit these to all.  There wasn't much beyond the "have a security policy for these trackable IDs".

The other spec was "how to get files from these devices".  Uses existing discovery mechanisms to get URI for device.  Example is a TD Directory (TDD) of charge points in an area.  Introduction is bluetooth, QR codes, etc. to get URIs.  Things got more interesting re: what data needs to be and not be in these directories, e.g. for not-public devices.  Directory should have a TTL so you don't learn a person's coming-and-goings.  The IDs that SHOULD NOT be unique, but they're listed in the directory.  They have a system for devices that don't have IDs so they can register anonymously.  I suggest they default to that.  

They handwave - and don't cover - many pieces.  So there's much I didn't review.

Nick: similar before, where they pointed at other documents.

Sam: proposed anonymous registration as a default?

Sean: default behavior for a device that is reasonably on someone's person, or a permanent id. no response from the WG yet.

Sam: is there a threat from just watching changes to the directory? 

Sean: TTL should make it hard to evaluate when a device is added or dropped.

Sam: ID rotation might be frustrated by watching changes in a directory

Sean: or other characteristics of the Thing (not just ID) can be stable

Sam: still worried about other document/draft in progress. any general advice we should give, or should be in a group charter?

Sean: not directly Web technologies so not sure. needs more effort on identifiers, like an exception for legally-required permanent unique identifiers. makes searching a particular risk.

Christine: big thank you to Sean, especially under time pressure.  You haven't looked at the architecture spec - and they're looking at CR in June.  Should we ask for the architecture doc done at the same time?

(nodding)

Christine: the group itself flagged an issue for needs-resolution.

Theo: I read the spec also.  The idea of the user entirely missing in both specs.  On the web, we think about empowering the user via the UA.  It seems bad, in these specs, for the manufacturer to have a permanent backdoor.  This feels incomplete.  How can we get them to place more emphasis on the user?

Nick: also important.  Seeing this in other areas, also - the person who's privacy is implicated might not be a 1-to-1 mapping to the device.  IoT things might, even if owned by different people, have impacts on others.  We're starting to see that in Web stuff, too.  More so with devices with limited UI.

Jeffrey: the description of non-permanent IDs in doc is that they must be able to be reset - but that's probably only when device is sold.  But that's not rotating frequently.  Might be useful for WG to consider treating IDs like modern operating systems treat MAC addresses, where they rotate fast enough that they're not useful for tracking.  Maybe provide access to the more stable things only when asked, e.g. the medical device.  Maybe require user activation for that.

Wendy: long tradition of web-of-data and data interop work at w3c that this builds on.  These reviews pointing to places they can improve could help bring them value.  would be good for them to have a better concept of the people using their devices.

Sean: re: "where is the user", much of this is meant to be machine-to-machine interaction.  

Nick: the directory scares me.  I can see advantages, e.g. looking up all cameras around me. but having lists of devices makes it easy to do the wrong things.  Example: GeoLocation APIs often done with WiFi SSIDs.  Many people thought no privacy risk - e.g. from broadcasting SSIDs.  I think I understand that argument, but people move house.  Now the database, which we thought was static, has a link between the locales.  A thing moving could have implications.  Could be hard to distinguish between them.  

Sean: they mitigate this in how they segment directories.  e.g. for your local network.  Dirctoties can have own auth systems and own scopes.

Jeffrey: they seem to have a use case that users can remember devices; bluetooth has addressed that - long term device ID encrypted into part of the addr - if you've paired, which gives you the long-term ID, you can recognize it, but someone watching it can't match them. (Bluetooth cryptography isn't ideal, but idea is sound.)

Christine: does the directory mitigation still work for things that need outside connectivity/control?

Sean: in theory, yes, but @@.  there are @context aspects of the TD that can reveal things about the device; weird jargon included in the clear.  They recommend long caching times.  I wasn't clear why this was readable in transmission.

Sam: re rotating identifiers, can JY open an issue and share? Sean: relevant both to TD and Discovery.
Sean to file an issue on jargen transmitted in the clear.

**Post meeting clarification**: no issue to file, the jargon itself isn't transmitted in the clear, the @context componenets in the TDs have links out to public documentation for interacting with the Thing that could reveal things about the device via DNS leakage, which is why the spec recommends very long TTL for caching of @context information.

Nick: seems like a recently-developing class of things that are re: location tracking, e.g. to find lost things.  Might be a rotating identifier.  Would that be relevant to this WG?  Should it be standardized?

Sean: by my understanding, those qualify.

Nick: sounds like, in addition to the issues we're opening, we have bigger concerns re: taking users into account. 

Sean: given how they focus on machine-to-machine, I don't think they'll be receptive.  We'll see how the architecture review goes.

Nick: mabe just ask for that complete review?

Christine: is there a concept of a gateway or hub acting as UA?

Sean: closest concept is directories

Sam: should we ask them to not publish TD/TDD until architecture doc is ALSO ready.

Jeffrey: IETF has notion of cluster of specifications.  

Sam: I can take on talking to group and Director re: clustering.

https://rawgit.com/w3c/wot-security/master/index.html

Sean: they have a sec/priv doc, separate from these docs.  They have not asked us to review it yet.  

### 3. AOB

Report out from meeting with the Web Payments WG regarding Secure Payment Confirmation

Sam: Web Payments discussion specific to Secure Payments Confirmation, using WebAuthn authenticators specifically for payments, including relaxing some Webauthn constraints that bind credentials to a specific origin. in order to make payment flows less friction. Webauthn group is not particularly worried. architectural concern that users must give payment card numbers (a long lived identifier) to the merchant, can't easily use a tokenized, one-time payment identifier. WG is responding to the current situation which mostly relies on those identifiers, although new payment systems (like Apple Pay) are using tokens.

Sam: some improvements on addressing fingerprinting surface for leakage before the user chooses to use Web Payments. UA algorithm is better specified, normative mitigation.

