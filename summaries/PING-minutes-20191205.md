# Privacy Interest Group meeting - 5 December 2019

## Attendees 

* Tara Whalen (co-chair)
* Peter Snyder (co-chair)
* Erik Anderson
* Brad Lassey
* David Benjamin
* Nick Doty
* Wendy Seltzer
* Scott Low
* Wendell Baker
* Tom Lowenthal
* Brent Zundel
* Melanie Richards
* Jeffrey Yasskin
* Michael Kleber
* Terri Oda 

## Agenda:

1. Updates on outstanding privacy reviews (Tony: DIDs, Brent Zundel: Intersection Observer)
2. Updates on Privacy Community Group 
3. Updates on outstanding issues (CSS Fonts, Sensors API, GetUserMedia)
4. Privacy reviews (general, DeviceOrientation)
5. Device Orientation API - call for experts
6. Updates on some WICG items (Modal Window, Payment Handler, Installed Apps APIs)
7. Call with Web Payments Security Interest Group on 12 December 2019
8. WoT 
9. WebRTC Screen Capture call for wide review
10. Willful IP Blindness - https://github.com/bslassey/ip-blindness/ 
11. AOB
12. if time, wseltzer can share update on [MiniApp CG](https://www.w3.org/community/miniapps/)

## Minutes:

scribe: npdoty

a full agenda, diving in.

1. outstanding reviews

* [Intersection Observer](https://www.w3.org/TR/intersection-observer/)

Brent: not a lot privacy related in this spec. didn't have a privacy considerations section ... I like seeing the spec authors point of view about that, rather than just the outside reviewer

Brent: using a high-resolution timestamp, and there have been fingerprinting concerns. not clear what that timestamp is being used for or where it ends up.

pes: might be surprise for the intuitive understanding of how web pages work

toml: that things are possible in javascript, doesn't mean that it should be possible or easy or isn't surprising. for site-like-experiences, we can have lower trust, like just reading an article, or app-like-experiences, where we need higher trust because the app needs greater capabilities. intersection observer might be an unreasonable level of tracking in a reading-like experience, might be invasive that a site knows what I can see on the screen, how fast I'm reading. this is technically possible, but doesn't mean it should be made easy, currently it's computationally intensive and has performance impacts for sites that do it. fine with tracking functionality having greater/poorer performance impact.

pes: could that be an issue on that spec?

toml: yes, will write up as an issue.

kleber: re high-resolution timestamp, what was the attack? my understanding is that millisecond would be sufficient for intersection observer.

pes: +1, Date.now() should work for most cases

* [DIDs](https://w3c.github.io/did-core/)

tony: fpwd of DID spec and privacy impacts. noted issues and actions. this is a data model, not specific prescribed usages. privacy issues with personal information being made permanent on a blockchain, or otherwise disclosed / out of control.

tony: warnings about zero-knowledge proofs, as there are many kinds that have different properties.

tony: potential issues with accounts, sybil attacks can be used against fake accounts. decentralization could lead to more invalid or fake accounts, which could have downstream issues.

tony: warnings about metadata, fragments, query strings which could contain personal information

tony: can open as github issues

npdoty: where is the writeup? (thanks, it's helpful to see your thinking and analysis)
pes: will send on the Slack

2. privacy community group

wseltzer: potential chairs reviewing charter, should be able to launch the group before the end of the year. would like some time on the next PING call to describe that work.

jy: who are the proposed chairs?
ws: folks from apple, microsoft and mozilla

kleber: is there a draft charter public?
ws: haven't seen a public charter, would welcome updates.
erik anderson: I'm one of the planned chairs. no public charter yet, but as soon as we get all the chairs set, we'll send something publicly.

3. outstanding issues

pes: fonts issue has some momentum after calls with CSS folks. now a separate, positive proposal that incorporates feedback from this group and css wg participants.

pes: sensors api is trying to generalize functionality into a single sensor api spec that all of the individual sensor specs can inherit from. suggestions about including baseline mandatory permissions or other restrictions. not clear where that text will live (in the sensor api or in reference in the permissions specs)

jyasskin: happy to talk about the Permissions spec if anyone wants to talk about it. haven't made updates in a year or so.

pes: not clear on the current state of the document, which makes me worried about what is being relied on. will discuss with you more offline.

pes: GetUserMedia issues about reducing data leakage; enumerateDevices method has been moved behind a permission (yay!), and now trying to limit to more granular permissions (which pieces of hardware the site needs to know about). making positive progress with the group.

5. Device Orientation API - call for experts

lassey: have asked the Blink devices team to review the mitigations described in the paper, but delay (vacations, etc.)

npdoty: had started to look into Device Orientation spec -- lassey confirms this is what he was referring to. Will follow up offline.

pes: for a certain category of device, you can fingerprint it through sensor resolution; want to find alternatives to resolution capping if we can do that to preserve functionality

npdoty: there are mitigations mentioned regarding scope/access of the api, separate from the noise/calibration details

6. Updates on some WICG items (Modal Window, Payment Handler, Installed Apps APIs)

pes: Modal Window and Payment Handler allows a 1st party to open a peer 1st party in a modal-ish window, to do some communication. If all storage is partitioned, this loses the double-keyed privacy protections.

pes: Installed Apps lets a website query for non-browser apps. Can't query broadly because it's restricted to a set of apps that opt into each other, probably by the same company. But it could still be a lot of apps, which could be a many-bit fingerprint.

npdoty: on modal window - payment handler and other things - you would pop up othert context, such as for user login -- I raised [issue](https://github.com/adrianhopebailie/modal-window/issues/5) for phishing capability here. If users starts to trust that they can type sensitive info into field, it won't be sniffed, they could be misled into entering sensitive info. Would like great security review, how do we get experts to review this? (will follow up with jy and with public-web-security mailing list)

jyasskin: recommends getting in touch with Chrome security UX folks (And has now pinged them)

An opinion [the Line of Death](https://textslashplain.com/2017/01/14/the-line-of-death/), 2017-01-14.

wseltzer: suggest tagging issue "security" or raising on public-web-security mailinglist

7. Call with Web Payments Security Interest Group on 12 December 2019

pes: call to go over additional feedback on new hardware capabilities and the web payments spec. they're eager to have more eyes on the issue, so feel free to join. details on the mailing list.

8. WoT

pes: clarifying what is a spec of new features vs. description of technology in use today, and what features are normative.

pes: manifest description and broader WoT architecture-style document. PING suggested removing mandatory permanent identifiers from manifest, which seemed to work for the group. suggested that the architecture description not continue on Recommendation track; Director decided on continuing on Recommendation track though not yet approved.

9. WebRTC Screen Capture call for wide review

new spec looking for privacy review

[mediacapture screen capture editor's draft](https://w3c.github.io/mediacapture-screen-share/)

pes: call for volunteers to read it over. encourage new folks to try it out.

jyasskin: could we have a rotational list? so that we automatically hand them out to the next person, and make it generally pretty fair.

pes: could have a large pool of volunteers, including buddies. I will start to get that organized.

wbaker: is there a template or suggested things to look at?

pes: privacy and security questionnaire is generally a scaffold to build off of. don't need to stay limited to that.
https://www.w3.org/TR/security-privacy-questionnaire/

wbaker: can help with this one, but may be out during the holiday.
pes: check in on the next call, not sure when that is
jyasskin: Slack a good place to check in for help/comments

10. Willful IP Blindness - https://github.com/bslassey/ip-blindness/ (lassey)

lassey: opt-in for servers to be blinded from IP address, advertise that to browsers. please have a look, add comments or file issues.

pes: had some comments on Slack, will discuss there more.

lassey: can discuss on public-privacy, also being described to the Web Advertising Business Group

12. Mini-Apps

wseltzer: a community group around mini-apps, the array of apps that interact within WeChat or other apps. trying to determine what can be described or standardized for mini-apps and super-apps. asked them to get early engagement on privacy and security considerations. pointed them to privacy/security self-review questionnaire. told them PING would be happy to receive review requests and answer questions.

community group is open, and conducts business in English, as well as Chinese.

npdoty: I would like to learn more about mini-apps -- is there a tutorial?

wseltzer: See this [whitepaper](https://www.w3.org/TR/mini-app-white-paper/) will post docs to fill in more details (e.g., presentations at TPAC)
[TPAC breakout](https://www.w3.org/2019/09/18-miniapp-minutes.html)
[Widget presentation](https://www.w3.org/2019/09/Chinese_IG/miniapp_widget.pdf)

lassey: previously some work on client-side web apps, is this related or building on that work. for example, MacOS and Yahoo widgets

wseltzer: they are aware of that, but Chinese ecosystem has developed very differently, looking at what has been developed/deployed already and how it can approach existing work

13. scheduling

pes: not sure people are likely to be available on December 26, January 2. not sure about December 19

tara: joint call is next week an hour earlier, with web payments security

wseltzer: privacy cg also interested in talking on Dec 19

plan on next call Dec 19, and joint call with web payments security next week (separate details)

(adjourned.)
