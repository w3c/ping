# Privacy Interest Group meeting (2 June 2022)

## Attendees 

* Christine Runnegar (PING co-chair, invited expert)
* Pete Snyder (Brave co-chair)
* Sam Weiler (W3C)
* Wendy Seltzer (W3C)
* Nick Doty (CDT, PING co-chair)
* Theodore Olsauskas-Warren (Google)
* Irene Knapp (invited expert)
* Wendell Baker (Yahoo)
* Sean Harrison (Google)
* Kris Chapman (Salesforce)
* Lubna Dajani
* Providence Baraka (Article 19)
* Joshua Ssengonzi
* Eric Mwobobia (Article 19)
* Don Marti (CafeMedia)

Scribe: Nick, Pete

## Introductions, and CEPC

https://www.w3.org/Consortium/cepc/

welcome, and welcome back

## Privacy review of WebXR Gamepads Module Level 1 

https://github.com/w3cping/privacy-request/issues/89

URL of spec: https://www.w3.org/TR/2022/WD-webxr-gamepads-module-1-20220426/
Reviewer: Irene

Irene: simple review because most of the behavior is included in other specifications. WebXR Gamepads, integrating specific gamepad devices. Would be most concerned about motion tracking, but that's covered elsewhere. Gamepad is also not a new concept.

Irene: device fingerprinting through model or device identifiers, or fingerprinting through characteristics of the gamepad. identifiers not a particular concern for this. fingerprinting through characteristics is a potential threat. mitigation is that gamepads cannot be enumerated until an XR session has been created, which would involve a user authorization.

Nick: Thank you for the review.  Curious about fingerprinting.  Gating access to the identifiers behind permission is a useful mitigation since its not driveby (passive).  Maybe there are other techniques worth consdering though, especially if WebXR devices become more popular / common.  Are there things we could do to mitigate even post permission?

Irene: One way to do that would be through higher level functionality (for example, generalizing mouse clicks through `onclick`).  However, the group might object that the higher level semantics aren't available / practical yet given the newness of the technology.

Nick: There was a similar discussion in GamePads; there are lots of gamepads on the market, websites want to use the device's capabilities, and there was progress towards defining a general / standard "gamepad interface" that didn't expose sepecific capabilites to the page.

  standard gamepad layout: https://www.w3.org/TR/gamepad/#dfn-standard-gamepad
  XR standard layout: https://www.w3.org/TR/2022/WD-webxr-gamepads-module-1-20220426/#xr-standard-heading

Irene: I believe its because of the tight coupling in the WebXR capabilities of these particular gamepads.  This spec includes a similar "general gamepad" concept for WebXR devices, but I dont know if its enough fucntionality that user angents could present only that interface.

Christine: i) Since the WG is working on a general gamepad definition, could we create an issue for it, ii) how did you feel about the spec's privacy considerations?

Irene: The privacy considerations section does discuss this concern and this mitigation.  The security section also seems accurate and comprehensive.

Christine: Sounds like no further issues to raise then, unless Nick identifies further issues (and possibly an issue about the standard / canonical layout)

Nick: maybe worth raising an issue to note the privacy improvements of a general interface

Christine: Fin! Thank you Irene (and for reviewing the associated specs).

Irene will file issue, and PING can help with creating labels as necessary.

## WebXR Device

(re)Reviewers: Don and Pete

Pete: early review 18 months ago, clarifying when a user is in a session, and passive fingerprinting surface about which devices are available (drive-by, without a permission prompt). defined a particular permission for those capabilities, though many user agents will grant that permission by default, but at least UAs that want to could make that an asynchronous permission request.

Pete: reviewing new changes to make sure there aren't substantial privacy impacts. some new capabilities, but doesn't seem like there were concerns about needing a whole new review.

Don: there is functionality that may be fingerprinting surface, but that hasn't changed in the most recent updates.

Christine: thanks! useful to do these re-reviews to make sure no new issues are introduced.

## AOB

Sam: many new review requests recently, including AR module in the WebXR. just letting people know there are many requests coming and so likely not to be skipping meetings.

https://github.com/w3cping/privacy-request/issues

CSS Color, Data Catalog Vocabulary, WebGPU, XR/AR -- a wide range of technologies

Theo: have done some internal work on WebXR, so can take the AR module spec.

Pete: volunteer to take one that isn't covered. could co-review with Lubna (getting back up to speed).

Joshua: should we let you know if we are interested in taking a review?
Christine: helpful to let us know if you're interested in taking on a review; email, Slack (#privacy-reviews). we keep track in a github repo, so we can assign a review issue to a user in github.
Pete: if it's your first time doing a review, let us know and we would be happy to help with co-review.

Next meeting in 2 weeks, lots of reviews to do.
