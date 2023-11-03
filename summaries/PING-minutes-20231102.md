
# Privacy Interest Group meeting (2 November 2023)

## Attendees 

* Pete Snyder (Brave, PING Co-Chair)
* Nick Doty (CDT), Forest Doty (unaffiliated)
* Philippe Le Hegaret (W3C)
* Don Marti (Raptive)
* Jeffrey Yasskin (Google Chrome)
* Harun Oz
* Aram Zucker-Scharff (The Washington Post)
* David Waite (Ping Identity)
* Michael Markevich (independent privacy advisor)
* Wendell Baker (Yahoo)

Apologies: Christine Runnegar (PING co-chair)

Chair: Pete

Scribe: Nick


## Agenda

###  1. Introductions, Code of Ethics and Professional Conduct

https://www.w3.org/Consortium/cepc/

Overview of our meeting practices, as always.

Harun: phd candidate, security and privacy of emerging applications

Michael M: formerly security officer for Opera browser, security advisor for DHIS2 and consultant on privacy topics, including GDPR and differential privacy


### 2. Privacy review - Dubbing and Audio description Profiles of TTML2


https://github.com/w3cping/privacy-request/issues/122

Aram: spec presents a variant of TTML2, a language for captioning of multimedia, subset provides XML elements to describe audio that you're listening to, like dubbing, pre-created captions, captions that might not match in real time
... instructions to screen readers about how to pronounce captions, modify recitations to make it more similar to what's in the content
... TTML documents allow time-synced text that can match up to audio and video, can be rendered with HTML and CSS onto screen
... DAPT provides additional support for captions that describe audio events (not just speech) door closing, crash/bang

Aram: dapt allows for embedding of audio files, potential fingerprinting surface (identified with an icon via respec :) ). can specify a set of different source audio files, the browser can choose a different one based on its format or size. could leak information about the user's preferences or network support. similar to <audio> element.

Aram: network requests themselves can leak information about the user, unexpected as part of dubbing. one possible mitigation is that network requests should be made in a particular way to avoid leaking information about the user. might be a fingerprinting vector of concern.
... feature detection vulnerabilities, how the styling is rendered in HTML and CSS, etc.

Aram: dubbing and presentation of other languages. user specifying the language might reveal their preferred language. downloading and using these files isn't part of this spec. should at least highlight it, not sure there's a clear solution to it. captions can be sent to particular devices, like a braille display or screen reader. 

Pete: concern is that a document could provide multiple encodings of an audio file, and the browser could choose to download based on some configuration. do UAs actually provide that configurability?
Aram: currently browsers would decide based on network conditions (?), not a user configuration option probably.

Nick: curious about risk of revealing accessabiltiy tools.  Seems sensitive and distinctive (beyond common fingerprinting bits). Is there any possible mitigation, or dsicussion in the spec, to try and hide from the page if users are using accesdsiability devices.

Aram: No its not discussed. These kinds of concerns might be more closely related to the underlyign TTML spec though, and not this immediate spec. I dont think the TTML spec currently mentions these risks either though. Additional risk from this spec though might be that certain accessibility tools might be specific to the additions in this spec though.

Nick: Maybe worth checking the TTML doc thoroughly to see if this risk is mentioned. The obvious mitigations seem unlikely to be inplemented by browsers (downloading extra files, etc)

Aram: sounds good, i'll add that

Aram: My last Q is, what about language selection. Spec isn't specific about which files would be downloaded by the user agent; this might mean downloading diff files per dub revelaing the user's lang preferences.  Might be worth calling out 

Nick: whats the state of revealing language preferencs

Pete: all browsers provide access to main pref, most browsers reveal secondary and further prferences in navigator.languages

(Pete note: Tor browser always sends English in most private conifgurations)

Aram: Might be different set of lang prefs here but not certian (Pete is willing to work with Aram to check this)

Aram: Last, this spec describes certain formatting / objects for descibing people in the dub/text. Having an explicit way of identifying people in a document might make it easier to learn about people

Nick: this seems like an additional piece of metadata that could provide richer information, and so worth identifying. would probably just want to address it like any other piece of metadata when determining whether to redact.

Aram: i'll summarize in slack 


### Privacy review - Securing Verifiable Credentials using JOSE and COSE

https://github.com/w3cping/privacy-request/issues/125

(postponed, reviewer not here today)

### 3. Updates

#### a. credentials, identity and age verification and privacy

https://github.com/w3cping/credential-considerations

Nick: we've disucssed on previous calls about ongoing calls about sharing credentials, in particular govt credentials.  Most discussion is happening in a WICG group, but I'm working on a recomendations document w/in PING. Would welcome questions, concerns or more details. Also would welcome potential mitigations to know and discussed risk. APIs are in flux right now, so ideal to discuss migitations now.
…: Pull requests and issues welcome.  Document is now in the PING repo.

jyasskin: Looks like the ping repo is a fork of the personal one.  MIght be easier to interact if it was owned by ping repo.

Nick: thanks!

#### b. charter

https://w3cping.github.io/administrivia/2023/charter.html

Nick: The proposed PrivacyWG charter has been updated.  The scope text in the proposal has been changed, to specify that there is privacy work that'll happen in other groups as well, and that PrivacyWG would mainly just be a home for privacy work that doesn't have another, more natual venue.
…: Next step is horizontal review for the proposed PrivacyWG charter. THere are still small clean ups and text needed in the document too.  THoughts and help welcome

https://github.com/w3cping/administrivia/labels/charter

### 4. AOB

adjourned.
