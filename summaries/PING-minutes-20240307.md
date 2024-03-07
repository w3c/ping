# Privacy Interest Group (PING) meeting, 7 March 2024

## Attendees 

* Joey Stanford (invited expert)
* Nick Doty (CDT)
* Philippe Le Hegaret (W3C)
* Pete Snyder (Brave, PING Co-Chair)
* Ray Holton (NBC Universal)
* Lubna Dajani
* Jeffrey Yasskin (Google Chrome)
* Christine Runnegar (invited expert, PING co-chair)
* Walter Rudametkin (Inria/IRISA)

Apologies: 

Chair: Nick

Scribe: Pete, Jeffrey

## Agenda

### 1. Introductions, Code of Ethics and Professional Conduct 

(see https://www.w3.org/Consortium/cepc/)
https://www.w3.org/policies/code-of-conduct/

Joey: from platform.sh, invited expert, based in CO, USA, I work on sec+privacy

Ray: also new, I plan on attending regularlly. Work at NBC on advertising


### 2. Privacy review of DeviceOrientation Event Specification 

(see https://github.com/w3cping/privacy-request/issues/128)

academic work on identification via calibration of sensors: https://ieeexplore.ieee.org/document/8835276

Pete: Had a call with Walter. Functionality is different ways the page can be alerted to the device's orientiation. Vertical, on countertop, etc. Similar review 4-5 years ago, and the group wants to move forward now. Our main concern was that there was a [paper](https://ieeexplore.ieee.org/document/8835276) saying you could use the orientation to fingerprint the device. The device has hardware to measure orientation; not every device is exactly the same physically. Those offsets are unique, and if you can learn the calibration settings, that identifies the device. The spec caps the granularity of the information, to nearest 1/10. That's useful and removes the concern. Neither of us had serious concerns with the spec.

Walter: Permissions: there's some entropy in the 1/10 degree granularity, and the paper's web page is no longer up. That granularity is still useful to games, but we don't know how much entropy is still leaked. But there's still a permission, which mitigates that.

https://github.com/w3c/deviceorientation/pull/86
https://github.com/JensenPaul/sensor-fingerprint-mitigation

Walter: My understanding is that the attack worked for factory-calibrated phones, but not necessarily all phones.

Nick: And the mitigation works in any of those cases, right?

Walter: Right. We should get real data. When does the PING consider entropy a problem? Is a permission enough?

Nick: We have worked on a Mitigating Browser Fingerprinting document, which doesn't give a precise answer. There are varying levels of severity. Permission or user action limits the risk, since it prevents drive-by use. Decreasing the surface is also useful. ... The entropy of factory calibration seems like it's eliminated by this granularity reduction. Is there some left or just user behavior?

Walter: There is user behavior that's exposed. I don't see a mechanism to prevent that. But I still don't know how much entropy is left from the factory calibration after rounding. Original vector is ~67 bits, and 1/10 degree reduces it strongly.

Pete will close the review and let the group know.

Philippe: We have 2 issues (https://github.com/w3cping/tracking-issues/issues/19, https://github.com/w3cping/tracking-issues/issues/105) that were closed by the Devices & Sensors group. Can we close them on our side? 

Pete: Can definitely close #19. I haven't checked the references in #105, and I'll check and close it after the call.

Nick: There are some notes in the privacy section, that it only fires the events while you're using a page, so it doesn't correlate across tabs. Also a SecureContext.


Philippe: https://github.com/w3c/deviceorientation/issues/87 is still being worked on by the WG. Comment by Marcos about sampling frequency. Anssi asked about WebKit behavior. We should keep it on our radar.

Pete: Sounds good.

Nick: Timeline? Is it going to CR, or will the issue be addressed first?

Philippe: We should put needs-resolution if we want it to be handled before CR.

Pete: I hadn't looked at this. I'll look and give my opinion.

### 3. Pending privacy reviews - ARIA and MathML 

(see https://github.com/w3cping/privacy-request/issues/131 and https://github.com/w3cping/privacy-request/issues/130)

Nick: we need reviewers for the above two specs. ARIA would like to move on this (opened just after our last meeting)

Pete: can co-review MathML, with Walter

PHL: Shivan (Brave) reviewed ARIA before

Nick: I can review ARIA


### 4. Off-The-Record Response Header Field, proposal from AC review of Web Applications Security WG charter to move to Privacy WG

Nick: PrivacyWG would be a new working group to do standards track work for privacy items. Someone in WebAppSec would like to move one work item (Request-OTR) to PrivacyWG instead it staying in WebAppSec. Request-OTR is a mechanism where the site can suggest to the browser/user that the data stored from visiting a site might be ephemeral.

PHL: Shivan is an author on Request but is on vacation so we don't know what his opinion on where this should live

Pete: similar to some other work in WebAppSec, re CSP headers (or Clear-Site-Data?). might be that the WebAppSec WG had specifically requested it.

Christine: I'm fine with PrivacyWG taking it if WebAppSec doesn't want it

Nick: What does this group think? (notes that this group seems positive on it)

Jeffrey: This group taking Request-OTR seems good. However, this makes chartering PrivacyWG tricky, and if we need rechartering we can do that

PHL: Lets not delay chartering PrivacyWG, we can recharter later

Nick: (summarizing) this group seems to be positive on adding Request-OTR to PriacyWG with a future possible rechartering

PHL: Will ask the same questions to the WebAppSec group


### 5. TAG review of BBS Cryptosuite, asking for PING guidance regarding unlinkable credentials & privacy guidance for credentials

Nick: Last call we discussed BBS cryptosuite and unlinkable credentials, and the TAG has also done a [review](https://github.com/w3ctag/design-reviews/issues/922#issuecomment-1963814265) since our last call
…: TAG is asking for PING feedback on whether credentials _must_ be unlinkable, and then TAG will follow up
…: I (nick) have an issue and a PR (below)

https://github.com/w3cping/credential-considerations/issues/6
https://github.com/w3cping/credential-considerations/pull/7

Nick: (summarzing the above issue) you might present two claims to a site (e.g., "im over 18", "i have a drivers license"), and a site might link those two claims to the same person using a shared credential.
…: This seems bad. It could cause unanticipated privacy harm / reidentification. In some cases reidentification by colluding sites might be unavodiable, but the standard should prevent linkability in cases that things aren't "inherently" unlinkable
…: In other cases, where linkability is unavoidable, we (PING, TAG, etc) should provide some guidance on how to explain to users the linkability risk

Jeffrey: this seems similar to ZKPs. Should we use the same language, or is that "formal" language confusing, and so should be avoided?
…: If we say "always act like ZKPs", that seems to forbid the [bitstring status list](https://w3c.github.io/vc-bitstring-status-list/) ... which may be an argument to explicitly allow additional linking information on already-linkable claims. So maybe the text you already have is right.

Nick: the revocation list should only be used for inherently linkable claims (as a suggested conclusion)

Jeffrey: Might be good to include that text as an example

*** Nick to add examples

Joey: If something is unlinkable, it'd be good to explain why its unlinkable

Jeffrey: do you mean k-anon, or what threshold is being used?

Joey: no opinion at the moment. But im thinking about it from the end user pov, not the implementation.

Nick: we should inform the user why we think its linkable, or not linkable?

Joey: both.  Ill think about it more and come back

Nick: I'll include more examples (Jeffrey request), i'll also talk to the VC spec authors to get their thoughts


### 6. AOB

* Privacy Principles for wide review

Nick: [Privacy principles](https://w3ctag.github.io/privacy-principles/) is now in wide review. Jeffrey is a co-editor. Please take a look, feedback would be very helpful
…: next steps will be looking for community wide consensus on making this a W3C statement (which is new aspect of W3C process)

Joey: I've read it, changes are great

Nick: positive feedback is uncommon and great to hear
…: there will be discussion at the W3C breakouts day (12 March, 14:00–15:00UTC, https://www.w3.org/events/meetings/9330e02e-2f20-4cb0-9fe3-22fd9dcdb629/), and at the AC meeting


