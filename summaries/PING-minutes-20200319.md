
# Privacy Interest Group meeting - 19 March 2020

## Attendees 

* Peter Snyder (co-chair, Brave)
* Tara Whalen (co-chair, Google)
* Christine Runnegar (co-chair)
* Pranjal Jumde (Brave)
* Chris Wilson (Google)
* Paul Jensen (Google)
* Theresa O'Connor (Apple)
* Martin Meyer (Akamai)
* Kristen Chapman (Salesforce)
* Erik Anderson (Microsoft)
* Konrad Dzwinel (DuckDuckGo)
* Hannah Quay-de la Vallee (CDT)
* Wendell Baker (Verizon Media) ([wcbaker on github](https://github.com/wcbaker))
* Dave Harbage (DuckDuckGo)
* Michael Kleber (Google)
* Melanie Richards (Microsoft)
* Nick Doty (UC Berkeley)
* Wendy Seltzer (W3C)
* Anthony Nadalin (microsoft)
* Sam Weiler (W3C)
* Tom Lowenthal (Brave)
* Scott Low (Microsoft)
* Jeffrey Yasskin (Google)
* Joey Salazar (ARTICLE19)
* David Senecal (Akamai)
* Joshue O'Connor (W3C)
* Brent Zundel (Evernym)

apologies: Shivan

## Minutes:

### 1. Privacy reviews 

a. Personalization Semantics Explainer and  Module 1 - Adaptable Content (Pranjal)

Pranjal: I work at brave. Reviewd explainer. Standards 
Reviewed explainer and content. No major findings, have a few qs out to authors. Once get responses will updat.
Questions arounfd interaction w 3rd party scripts. No responses back yet, but only out for a week. Will file issues if no responses.
pes: Thanks. Anything worth discussing in group?
Pranjal: Nothing major.
pes: Any qs? Nope

(from the Personalization Taskforce of The Accessible Platform Architectures (APA) Working Group)

Links: 
* Explainer - https://www.w3.org/TR/personalization-semantics-1.0/
* Module 1 - https://www.w3.org/TR/personalization-semantics-content-1.0/
* Privacy and security self-review - https://github.com/w3c/personalization-semantics/issues/131
* Wiki - https://github.com/w3c/personalization-semantics/wiki/
* Getting started page - https://github.com/w3c/personalization-semantics/wiki/Getting-started-with-personalization-semantics
* Github repo - https://github.com/w3c/personalization-semantics/issues

b. TTML Profiles for Internet Media Subtitles and Captions 1.2 (Nick)

Nick: Jeffry did review of CTML 2nd ed. Also published 2nd profils of internet media profiles and captions. Comments wilapply to TTML. Had talked about prev. versions. Jeffrey did review of recent. Only changes to subtitles and captions were ability to change fonts for captions. Requires loading external font resources, has potential priv. and sec. issues, and potential fingerprinting issues. Tricky to provide reviews because TTML a doc model, not necessarily widely implemented by web browsers. Lack of common understanding about common implementers makes it harder to give really good feedback. Have opened a couple issues about fingerprinting issues, but will need broader discussion w/ TTML group about how much they are part of different implementation approaches.

pes: Has working w/ the group been receptive or would group-to-group comms be useful.

Nick: Communication has been fine. They have said they would appreciate github issues, but communication about how to interact with the rest of the web patform might be helpful. Relationship has been collegial, but explainers might be useful.

pes: Would a call be helpful?

Nick: Could be a good long email discussion, might need a call.

pes: good action item. I will take on. Next step will be determining what type of interation.

Nick still planning to transition because had already submitted a request. Most issues are ongoing issues about TTML generally. Issues will still be ongoing.

pes: Not a concern to go forward with issues open?

Nick: Yes, no need to block now.

pes: No other issues, will take as an action iten to work on intergroup communication.

c. WebXR (Pete)

pes: Review of spec for other reasons, and other issues came up. Spec def'ns two ungated unpermissions ways to ask for [pes edit]information about whether the device has certain categories of WebXR hardware installed ~hardware installs~[end]. Very identifiable info
Other [pes edit]issues where the spec is ambigious ~issue 2-3 places of ambiguity~[end]. Can access sensor pads w/o permission. Can get to sensitive data, which was delt with in unrelated parts of the spec. Broader issues: Spec had definied its own ahoc permissions system for what requires explicit vs implicit permissions. Suggest getting rid of that and calling into existing permission spec. For this group, during reviews look for places to call into existing specs. 

...: WebXR specs deal with a lot of senseor data, have worked with the sensor group to define specs. Would ask not to write your own but call into that existing spec.
Will keep people abrest of that convo.

Nick: Good practice about keeping convo in one place. Relatedly, gettin onfo about attached hardware capable of something, is a similar conversation we've had about webRTC and get media. Might be good to use a similar model for security and privacy about attached devices. Gamepads might be another. Would be nice to have the same advice about trying to figure out if a user has a capable device before using it.

pes: Another convo about ways to learn about hardware. A spectrum from explicit request to just list of everything user has.

Tess: here's the [existing TAG guidance](https://w3ctag.github.io/design-principles/#device-ids) and our [open issue](https://github.com/w3ctag/design-principles/issues/152)

Josh: Do you have URIs to discussions on where those fingerprint pointers might be? Could have particular fingerprinting for people w/ disabilities, specific devices.

pes: Specific guidence relates to not giving away specific hardware, but rather generally about devices with video/audio capabilities, so not quite so identifiable, but could be identifiable.
Issues is not just preventing access, but also once a site has access, how to restrict access to just what is needed. Sounds very useful for your users.

Josh: Yes, especially because sometimes it is useful for a handshake for access to other services, so don't want to be too restrictive.

Chris: WebXR API has a stated design goal of not exposing identifiers, with a specific note about the challenges. Have already hit VR challenges. If you do identify specific hardware, can be hard to insert specific tools if you are not that hardware. API is moving towards capabilities rather than specific hardwares.

pes: enumerated device API risks comes from legacy stuff, so hattip to folks for doing the work to update.
will keep folks informed about updates.
For discussion, given that some folks who face different risks, depend on devices in different ways, is there value to discussion between PING and accessibility groups

Josh: Yes that would be useful. Platform accessibility group is looking at privacy concerns now. Would be benefits to continued conversations about pros and harms of different approaches.

pes: Will take as an action item to set up that call.

### 2. Audio/canvas/webgl fingerprinting (Pete)
pes: Follow up to open up fingerprinting surface from Audio/canvas/webgl APIS. Not too much to add other than issues exist in github, links in Slack. If this is of interest, please get involved, given how entranched and long lived the issues are, will be a particular challenge.

nick: To clarify, are audio and webGL separate issuses from canvas?

pes: audio is a separate issue, not a new issue, link to an old. No special webGL issues, though they do open up different fingerprinting issues, so if someone wants to take that on specifically, feel free. Can reshare the issues in slack if useful.
 * [audio api fingerprinting issue](https://github.com/WebAudio/web-audio-api/issues/2061)
 * [canvas fingerprinting issue](https://github.com/whatwg/html/issues/5373)

### 3. PING administrivia / Privacy review process (Pete)

pes: had convo on last call about how to understand the result of a privacy review. 
Take away:  Make clear a PING review is not necessarily speaking for all of PING, but the members who did the review, and part of a conversation within the group. Should be taken as the review of some members within PING, but not necessarily unanimous feelings within the group (which rarely happens)

pes: will write that up withing the next 24hrs, but won't share in a more public way until everyone in PING has had to read it, before nxt call.

(npd: +1, I like that. thanks) 
 
### 4. Threat model (updates over the last 2 weeks) (Jeffrey/Nick)

Jeffrey: Nick has been reviewing patches, landing some of them. Biggest thing is the threat models or description of what sensitive info means. Needs fleshing out, but framework is there. Could use input about what it means for info to be sensitive. Restriced info. Growing more open issues other people can look at. would like more reviewers.

[sensitive info PR#12](https://github.com/w3cping/privacy-threat-model/pull/12)

Nick: Other change integrating a PR to talk about a wider range of high level threats. Got work started with concrete work on tracking between sites, but want do more than that, so now includes things from RFC 6973 https://tools.ietf.org/html/rfc6973. Good time to consider high level threats, have started to do that in the doc, could use more feedback from this group about what threats are missing.

pes: Best way to get involved?

Jeffrey: Read the [doc](https://w3cping.github.io/privacy-threat-model/), [issues](https://github.com/w3cping/privacy-threat-model/issues/). [Complain](https://github.com/w3cping/privacy-threat-model/issues/new) about things that are wrong.

### 5. Updates on font fingerprinting

pes: Updates on font fingerprinting conversations: 

Jeffrey: Initial [anti fingerprint repo](https://github.com/w3cping/font-anti-fingerprinting/) was reslut of convo internal to Google get rid of confusion between TAB and sandboxing anti fingerprinting. Wrote down options for how to move forward. More approaches than are written down, would like to add more. Doc can then write down pros and cons, more research needed, which direction we should then go. Whether all browsers need to all do the same thing, or can take different but compatible approaches. Still working on text, then will be some time to research and discuss before moving forward.

pes: Should convo continue in [CSS WG issues](https://github.com/w3c/csswg-drafts/issues/4497), or should convo move here. Is there a way to hook into CSS WG convo, or how do we no talk past eachother.

Jeffrey: Not following the CSS issues as closely I should be to feed back into doc. Would hope that as convos lead to concrete approaches, will hope those get back into the font fingerprinting repo, memorialized in an actual doc.

pes: Should make sure that is communicated to CSS group so we are all pursuing the same solution.

Jeffrey: CSS approach should be added to the doc if they are doing something different.

pes: should PING have a work-in-progress tag so we can make that clear?

Jeffrey: There is metadata that bikeshed uses, but seems like nobody reads it, so have to continue sharing that out.

pes: May also need bold text at the top or something, because bikeshed metadata means something different.

Jeffrey: is a different thing, but people don't seem to see it on the threat model. Will add it to the threat model.

Jeffrey: Names of folks with confusion would be helpful.

pes: will send.


### 6. New Web developments and privacy considerations 

pes: Nothing to say about new specs. Anyone else have someting they's like to discuss

Christine: Mention that Firefox 74 provides suppord for [MDNS Ice](https://tools.ietf.org/html/draft-ietf-rtcweb-mdns-ice-candidates-04) so cloaks IP address in some scenarios. Public interest technology group did some work at an IETF hackathon a while ago examining different browser implementations of WebRTC with different implications for privacy (i.e. exposure or not of local IP addresses) ... now good to see FF 74 ... Would like Shivan to discuss journey, but he's not here today.

pes: Is any of that being pushed into upstream spec or just FF mitigation?

Christine: Not sure, maybe someone else knows?

Joey Salazar: What we got is pretty much what C said. Firefox now provides better privacy by cloaking IP. Doesn't solve all preblems, but good example of improvement in response to complaints.

pes: ask for an update from Shivan on next call.

pes: all vendor fingerprinting mitigations into one doc to see what is movable into the spec. Should we revisit? Does it seem valuable? If so, anyone willing to own? Maybe will bring up on next call as a more formal discussion. Doc may be useful since there are mitigations that aren't documented anwhere that may be useful. Will take as action item to add to next call

Erik Anderson: Google shipped mdns mitigation in the fall as well. See https://groups.google.com/a/chromium.org/d/msg/blink-dev/z5hSy6Rf_aE/u3MPuMYZGAAJ

Joey: Elaboration on MDNS Ice: [Post from Shivan](https://www.article19.org/resources/privacy-and-consent-in-the-age-of-browsers-the-question-of-webrtc/).
Hackathon demo https://github.com/ntblk/webrtc-privacy

### 6. AOB

pes: anything to add? Nope.





