# Privacy Interest Group meeting (2 July 2020)


## Attendees 

* Christine Runnegar (co-chair)
* Pete Snyder (co-chair, Brave)
* Kristen Chapman (Salesforce)
* Sam Weiler (W3C/MIT)
* Shivan Sahib (Salesforce)
* Peter Snyder (co-chair, Brave)
* Hannah Quay-de la Vallee (CDT)
* Brad Rodriguez (Magnite)
* Eric Mwobobia (W3C fellow: ARTICLE 19) 
* Joey Salazar (ARTICLE 19)
* Wendy Seltzer (W3C)
* Erik Anderson (Microsoft)
* Shaun Gilmore (Apple)
* Lubna Dajani (Allternet)
* Scott Low (Microsoft)
* Wendell Baker (Verizon Media)
* Theodore Olsauskas-Warren (Google)
* Sean Harrison (Google)
* Dave Harbage (DuckDuckGo)
* Konrad Dzwinel (DuckDuckGo)
* Chris Wilson (Google)
* Zibi Braniecki (Mozilla)
* Pranjal Jumde (Brave)
* Nick Doty (UC Berkeley)
* Theresa O'Connor (Apple)

scribing: Sam

## Agenda

#### 1. Privacy review request from the Web RTC WG - WebRTC Scalable Video Coding (SVC) specification

Spec: https://w3c.github.io/webrtc-svc/

This document defines a set of ECMAScript APIs in WebIDL to extend the WebRTC 1.0 API to enable user agents to support scalable video coding (SVC).

Explainer: https://github.com/w3c/webrtc-svc/blob/master/explainer.md

Privacy considerations: https://w3c.github.io/webrtc-svc/#privacy-security
[TOC]

Repo: https://github.com/w3c/webrtc-svc/

See issue filed at https://github.com/w3c/webrtc-pc/issues/2460

Shivan reviewed

Shivan: The specification lets browsers indicate their capabilities. Adds getCapabilities items that can be used for fingerprinting.  This spec adds new fingerprinting data.  Discussion re: what new data is added.  Now no HW support for these codecs, but there could be in the future.  WG wanted to move it to -PR spec.  If we don't do anything at -PR, need to add something re: HW support.  

Pete: When you were explaining this to the AG, any difference in response to different proposals?

Shivan: Have not heard from them as yet. From issue history, not much support for adding prompt; thought to be confusing for users.  No HW support now. Needs discussion

Christine: thank you for doing the review.  

Shivan: I wasn't sure if I should file an issue

Pete: (re response) We get that a lot - if it's not useful now, that doesn't mean it's not useful in future.  At some point, it will become a fingerprinting vector.  I support you re-opening issue.

Sam: I think this should be re-opened and flagged as needs-resolution.

Pete: Since I opened it originally, I'll also follow it.

Christine: Anyone else willing to look at this one?

Pete: Often these reviews end up being exhausting with one person from PING engaging with 20 from the group in question.  Good to have more PING people involved, even if they're not owning the issue.

Lubna: I'm new, but if I can help, I will.

Pete: Let's talk on Slack.



#### 2. Privacy review request from the Devices and Sensors WG - Geolocation API

Link: https://w3c.github.io/geolocation-api/

This specification defines an API that provides scripted access to geographical location information associated with the hosting device. It is now maintained by the Devices and Sensors WG, and contains the following substantive changes since the last REC:

  - Now Controlled by feature policy
  - Fixed confusion around call-back interfaces not being an EventHandler
  - Only expose the API in SecureContexts
  - Renamed the interfaces and dictionaries + removal of [NoInterfaceObject] + [SameObject] annotation on geolocation attribute

(Note: the DAS WG is also working on a new API based on the Generic Sensor API: https://w3c.github.io/geolocation-sensor/ )

Link to the Security and privacy considerations section: https://w3c.github.io/geolocation-api/#security

WG has asked that we please file issues at
https://github.com/w3c/geolocation-api/issues

See issued filed:  
* https://github.com/w3cping/tracking-issues/issues/112 
* https://github.com/w3cping/tracking-issues/issues/111
* https://github.com/w3cping/tracking-issues/issues/114

Pete: It is not clear now who will own this in the long term. I looked at it over the weekend; Irene Knapp also offered to review.  No way to give time-limited permission. That seems interesting, since this API allows for background updates over time.  WG seems unenthused and wanted to move this to WebAppSec.  Another issue I raised is that it would be useful to have affirmative gesture.  In Blink implementation, frame has to be visible, but that's not in the specification, and no user interaction requirement.  The goal is to raise the bar.  The WG seems open to idea.  Then, re: issue 114 – the specification says implementers must provide a way to control granularity, and right now that's a binary switch.  Some procedural conversation there re: moving this to Geo Sensor APi specification

Sam: Encouraged by the user gesture conversation, glad to have dialog around granularity. Pete may be confused by who owns the doc. Looking forward to Irene's report.

Christine: We would like as many eyes as possible reviewing this before our next meeting on 16 July 2020.  The Geo API is an old specification. The changes WG are making now are in the nature of maintenance, but it’s also important that privacy is included. The Devices and Sensors WG (DAS) is working on the Geolocation Sensor API (https://www.w3.org/TR/geolocation-sensor/)

Sam: Same WG - DAS - owns both (now).

Pete: If you have input, please file it in GitHub issues.

Lubna: Let's add this to our list. Lifetime is important.

Sam: We should be specific about what’s helpful.  Follow our tracking link https://github.com/w3cping/tracking-issues/issues/111, follow to the group's issue, and +1, add a comment, express support.

Hannah: Why do they want to push this to WebAppSec?  Is this about making it available elsewhere?  If WebAppSec will be slower, I see benefit to doing it here (also) first.

Pete: @@  This spec is going forward now and is dealing with uniquely important data.  No guarantee on timeline in WebAppSec

Hannah: I see value to doing this more quickly in geolocation API

Sam: Frequently when people push things to other groups, it’s worth asking if the group being approached wants to gate their document on the "remote" group. But this has already been published so it’s a bit different. 

#### 3. Updates on open privacy reviews

##### Web audio API

* https://github.com/w3cping/tracking-issues/issues/89
* https://github.com/w3cping/tracking-issues/issues/53
* https://github.com/w3cping/tracking-issues/issues/50

Sam: There are 3 open issues with the WebAudio API specification.  The most interesting one is about exposing different sample rates as fingerprinting vectors. The group has agreed to only expose one of two possible values, and that less common rates will be gated somehow. 
…: Second issue is about inaudible sounds.  Doesn’t look like substantive change, but there will be non-normative guidance
…: Third issue regards floating point fingerprinting.  Group wants to push for a platform wide solution.  Conversation is ongoing to figure out if its truly only floating-point implementation being fingerprinted, or if there are other platform or bits going into this fingerprinting surface.
…: Progress on the first, solution on the 2nd, and 3rd is ongoing

##### Media Capture and Streams

* https://github.com/w3c/mediacapture-main/issues/697
* https://github.com/w3c/mediacapture-main/issues/682
*https://github.com/w3c/mediacapture-main/issues/646

PING tracking equivalents:

* https://github.com/w3cping/tracking-issues/issues/82
* https://github.com/w3cping/tracking-issues/issues/60
* https://github.com/w3cping/tracking-issues/issues/96

Pete: There are several open issues on distinct but overlapping things, mostly re: what device info is available before permission, or after permission given to one device. The WG is leaning toward "what category" available early, but not number of each type. Once the user gives access to one of a type, it exposes the rest of that type.  The WG constrained by existing deployment.  Looks like there will be steps to reduce pre-permission access.  Allow but not require implementers to restrict labels after permission.  And, moving to in-chrome device selection to move away from this.  This all seems positive.  Not ideal, but a good compromise.  But, WG has done a good job working with us.  

Pete: One other issue ongoing: how identifying are device IDs after permission.  Looks like GUID.  Group moving to dual-keying.  positive step fwd; still seems like more than needed.  conversation still ongoing.  Text may be agnostic about shape of those IDs.  

Sam: What’s the difference between deviceIds and labels?

Pete: Labels/identifiers are different.

Pete: Not 100% clear.  There is another issue open to move all of this out of label (specifically device category).  Issues point at each other; not clear what they'll do.  Lots of forward progress.  Receptive

Sam: As folks work from home, we're all likely more familiar with the risks 

Joey: How best can we support you?  GitHub?

Pete: I'll add issues to the minutes and Slack

Sam: Specific issues you need more voices on?

Pete: I'll indicate.

Pete: Reshuffle agenda to tackle TC39 now?

Christine: Zibi is not here at yet, asked to arrive by 45 mins

#### 4. Privacy threat model (principles)

https://w3cping.github.io/privacy-threat-model/

Pete: Some uncertainty re: framing of doc: principles or enumeration of risks.  Structure of document still not hammered out.  My proposal in GitHub at: https://github.com/w3cping/privacy-threat-model/issues/37

Wendell: The threat model is an important document.  We should find a way to give it more attention - otherwise, it has the potential to be just the output of a smaller group.  Potential to be very important.  I proposed: from extreme view, we want doc to describe things we can't stop.  ratcheting down: potential for Web folk - media crew - to sign onto as a set of tenets.  Society going through introspective time; there is an opportunity to have a set of principles, practices, and dangers that people could adhere to.  Some credentials (?) in professional engineering may be too strong. But, it could record known good and aspirational good uses of technology.  those not hewing to that - trying to achieve that good society - we should try to have other things to do.

Christine: A reminder that already have some threats and mitigations identified in the Self Review: Security & Privacy Questionnaire and Mitigating Fingerprinting Group Note

Nick: Can you rephrase/explain? 

Wendell: This comment comes from conversations in Web Advertising Business group.  There is a perfect size here we should aim for in developing the document.

#### 5. W3C Horizontal Review process (update)

See: https://www.w3.org/wiki/index.php?title=Wide_and_Horizontal_Review&oldid=111521

[skipped due to time constraints]

#### 6. New Web developments and privacy considerations

##### TC39, the folks that standardize JS versions, asking about privacy of i18n for new versions of JS.

https://github.com/tc39/ecma402/issues/443

Zibi: I work at Mozilla, and want to talk about ECMA 402 and ask for help.  We work on standardization of a subset of JavaScript, focusing on multilingual issues.  It was started in 2012 and is growing.  It’s of interest to vendors because it’s part of the runtime (e.g. patterns of date formatting, other similar formattings).  Also interacts with DOM and HTML.
…: the group’s goal is the provide building blocks for userland libraries, and to reduce the cost of building multilingual web apps.  E.g. localizing language, names, logos, etc.  
…: if the JS engine has this data, it makes it easier for everyone.
…: Also intended to reward best practices.  Group has 20-40 experts helping design user-friendly APIs.  Since most Web developers are not i18n experts, we want to lower the bar and encourage API choices that scale to other languages.
…: Founded 2012, "restarted" 2016.  2016-2020 had a lot of active development, new APIs and broader scope.  3-(6-7-8) APIs covered.
…: Chair and leaders of the group thinks the API is now about finished with the scope, now focusing on detailing and tweaks.
…: B/c the spec's API carries data, and everyone can't carry all data, the APIs are meant to be best effort and opaque to the developer.  Developer calls the API and trusts the JS engine to do a good job localizing, but diff versions / vendors / users might have different preferences and customizations.  Some platforms might not have the data at all.
…: Recommendation is that developers should use these APIs as the last step, and not rely on specific outputs.
…: So far, we have not strongly worried about privacy, but privacy folks seem concerned and are trying to retrofit the APIs to be privacy friendly (re Tor, Mozilla, etc)
…: Group now thinks retrofitting isn't sustainable, and group needs to specifically consider privacy (e.g., privacy by design, or otherwise discourage attacks)
…: There are three areas group is concerned about. i) current API scope has not been reviewed for privacy (e.g., diff engines have diff locales, and diff platforms).  There is a "resolveOptions" API that allows for introspection, such that an attacker could figure out user preferences based on API output.
…: ii) There are new APIs, some of which seem to have high privacy risk (e.g., enumeration, date time widgets, etc).  These APIs could leak what locales are supported, what formats are preferred.  Maybe it would be better to move this to HTML / DOM, and not JS APIs?  If so, what to do w/ node and other non-browser JS environments.
…: iii) this requires a large amount of data in the runtime, so possibly lazy-load locale information.  This would again leak user preferences / language / locale information.
…: We'd like to have feedback on whether this should be done.
…: Finally, we're trying to get better about respecting user preferences. (number separators, date / time format, etc).  Some folks want JS engine to follow system preferences; if we do so, how to reduce/ prevent FP vector.
…: Also, some users want to control which websites get access to which locale selections, for privacy / safety reasons?
…: The above issue is a request for input and help.

Pete: where to give feedback?

Zibi: GitHub issue is best. If needed we could schedule more PING time. There is a monthly call, but let’s start asynchronous.

Nick: Thank you for this.  Are there other TC39 groups / areas that also might have privacy impact?  Is the ask to only focus on ecma402?

Zibi: I'm not aware of other privacy concerns; there are security issues (re SharedArrayBuffer, Spector), but this is the main privacy concern I’m aware of.




