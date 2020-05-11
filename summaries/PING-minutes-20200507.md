# Privacy Interest Group meeting - 7 May 2020


## Attendees (sign yourself in)

* Peter Snyder (co-chair, Brave)
* Christine Runnegar (co-chair)
* Sean Bedford (Facebook)
* Wendell Baker (Verizon Media)
* Erik Anderson (Microsoft)
* Sam Weiler (W3C/MIT)
* Shaun Gilmore (Apple)
* Wendy Seltzer (W3C)
* Hannah Quay-de la Vallee (CDT)
* Martin Meyer (Akamai)
* Chris Wilson (Google)
* Joey Salazar (A19)
* Scott Low (Microsoft)
* Melanie Richards (Microsoft)
* Theresa O'Connor (Apple)
* Brad Lassey (Google)
* Michael Kleber (Google)
* Paul Jensen (Google)

scribing: Erik Anderson

## Agenda and Minutes:

### 0. Chair announcement

Tara has stepped down as chair. We appreciate her service.

### 1. Deciding next steps for PING tracking issues for Web Audio and Media Capture

Christine: expected to transition in the near future. Outstanding tracking issues; let's review them today and decide what we want to do with them.

### Web Audio

Web audio API: https://webaudio.github.io/web-audio-api/

Sam: Let's make sure we agree that these are issues that need to be followed-up on. In some cases the working group closed them and I have asked to re-open them.

#### Sample Rate fingerprinting
*   https://github.com/w3cping/tracking-issues/issues/50

Sam: This issue talks about whether the sample rate a device uses gives you extra bits of fingerprinting surface. We seem to have concluded that while most devices uses one of two frequencies tied to the platform sample rate. When a user has specialized hardware that can do higher sample rates, it's a smaller population that has the hardware and exposing those by default exposes extra fingerprinting surface.

Sam: The working group has said that downsampling is not viable because it takes CPU. My pushback was that users with high sample rates presumably have higher processing capability; can we hide those higher frequencies?

Sam: I would like someone else to own the follow-up if possible, please speak up if you can. *+1/-1 prompt about if this is something we needd to do more on*

Pete: +1 for me. Other hardware, e.g. getUserMedia, and WebGL expose some state, this is the only one for audio hardware.

Chris Wilson: for context, I'm a former editor of the Web Audio spec. Want to underscore that we should get data on how frequent this is; hiding things under a permission might be tenable. Not something you can avoid just with downsampling. Downsampling brings a quality loss for that hardware. Good to understand how narrow in practice that is.

Sam: do you know of anyone doing that measurement?

Chris: Chrome collects info like that. either 44.1 or 48khz. Most people can't hear better than that. When you increase the sample rate it requires a lot more resources to run that. Most software is going to ask for a lower sample rate anyway. Today, Web Audio doesn't say anything specific about what the default is. A UA could say "I offer this rate. Period." Nothing to prevent that in Web Audio at all.

Sam: we've gotten pushback in the issue saying, we don't want to do that computation to downsample. Glad to hear you say that's okay.

Chris: I said it's fine for a UA to do that. For someone with high-end hardware they're going to be pretty disappointed if you start downsampling.

Sam: but could be hidden behind a permission or consent structure?

Chris: yes, but not sure how easy that would be to set that up.

Sam: the vast majority are using 44.1 or 48, I'm worried about the ones that don't use those.

Chris: not sure what your bar is for identifying bits.

Sam: extra bits add extra entropy for that browser.

Chris: concept/term makes sense, not clear on the bar for caring about that. 2 sample rates super common, 4 or 5 more that are somewhat common, and then that's it.

Sam: what we proposed in the issue is gatekeeping anything but the platform default. 44, great. 48, great. Anything else, hide it.

Chris: I think you need to come up with a design for how to unhide it. Web Audio been shipping in major engines for 6-7 years; getting them to add a gatekeeping for devices... I'm not sure how to hide it in a way that doesn't mess up people already out there.

--no one else on the queue--

Christine: issue is not yet resolved, it needs resolution. Not clear on what the next steps are.

Sam: given WG has shut down discussion on the issue, it's up to them on if they want to have that discussion.

Wendell Baker: I thought the conversation highlighted that this group was not able to recite a bright line in which privacy concerns are relevant. What I heard was: those who have exotic fancy hardware, good luck to you. Others with consumer-grade equipment, concerns about experience.

Christine: I think we should keep the "needs resolution" tag on the issue. Hopefully we can figure out a way to resolve it with the group. In the interests of time, let's move on.

#### Generated Wave form / floating point implementing fingerprint 
*   https://github.com/w3cping/tracking-issues/issues/53

Sam: this one observes that floating point math is done; platforms have different floating point characteristics that can lead to fingerprinting surface. Brave introduced a mitigation for this that involves fuzzing. Because we have a working example of a way to mitigate it; I propose  we mandate it without specifying the mechanism. Pushback has been about not wanting to specify a specific mechanism but I think it's reasonable to demand one.

Pete: process point, let's discuss the issue details less and focus on process. On the substance of this one, this one is a very important issue, this is being exploited in the wild.

Chris: process point, how would you like folks to give a +1/-1; something in the issue, in the cryptpad, or something else?

Sam: wasn't specifying, you can type into the cryptpad as we go.

#### Inaudible Sounds
*   https://github.com/w3cping/tracking-issues/issues/89
    (https://github.com/WebAudio/web-audio-api/issues/2191) 

Sam: this one observes about linking devices in the same place, or even cross-browser/cross-frame by emitting sounds that the user can't detect (outside of human capabilities). Light sensor had a similar concern. This is a "could we do something" to cut off parts of the spectrum. Someone indicated that there are things that could be emitted in the spectrum that humans can hear, but still not be detectable by a human.

Sam: I think there's still discussion to be had here. The WG has closed the issue, I would like the discussion to continue.

Wendell: there's a paper by Mary Baker about this which shows that colocation by patterns of silence, low computation. Some of this is going to be very very difficult to deal with. I'd call for the higher-level understanding of what we're trying to do here. We can call out and bully pulpit "hey this might be happening" or may even see it happening but WG may still close it and move on. That may be our duty because we have knowledge it might or is happening. Some, for the last few percentage of computational activity required, may not think it's warranted. What do we expect this group to be doing, high moral ground or every last fingerprinting surface is locked down?
At least:
Wai-Tian Tan, Mary Baker, Ramin Samadani, and Bowon Lee, "The Sound of Silence." SenSys'13, Rome, Italy, November 2013.
The colocation stanza in
https://www.hpl.hp.com/people/mary_baker/publications.html

Chris: Wendell said a bunch of what I wanted to say. What are you really looking for? I know enough about how audio ranges work, people have different audible ranges. Once you give people access to a microphone, they can figure out ways to do interesting things. The paper Wendell mentioned is a good example. You can also do fun things with pitch to determine colocation. Once you give people access you're going to start up a war back and forth about how you could determine things from the audio feed. Anything that gives you microphone access should be concerning to a user, which is why we lit that up (user indicator). The response from the Web Audio group is that they don't really know what you're looking for and these are well-known attacks (others consider them super useful, e.g. ultrasonic audio was a big deal a few years ago to walk around a museum to detect whate exhibit you're next to and folks viewed that as neat).

Pete: in terms of what would be most productive on this immediate conversation, we should think of 3 buckets: (1) we need a fix, PING feels strongly and those should be "needs resolution", (2) important and we want to take high ground route but without label, (3) if we are satisfied what has been done we can just close the issue. Another paper that might be interesting is ultrasonic techniques for cross-tab tracking by emitting audio signals to understand browsing activity. For this one, I put it in the second category, important but requires mic permission.

Sam: I agree with Pete. I want to seed the discussion. Paper links are helpful. They understand it better than I do.

Christine: perhaps we leave it open but don't add a "needs resolution" label. And share the papers. Sound good?

Sam: sure.

Chris: maybe one possible resolution is that you want some of these risks highlighted in the spec. Maybe not mitigated, but calling it out specifically to make sure readers understand what is going on.

Sam: I worry that the person who doesn't understand the risk of turning that on is the user.

Chris: certainly true.

Wendell: I like the framework Pete came up with. There are grades, or buckets, of things and if we formalize and campaign that as a "logo program", this group could come out and say, we looked at this issue and it's "level 1" and we put that sticker on it and ask, or maybe require, and ask that the upstream issue carries the label. When someone who is not apprised of all of the issues and asks where the standard/recommendation fits on the privacy spectrum. DHS used funny colors for threat level. That could be our teaching moment. I like Pete's framework and it might help get to where you want to be, Sam-- traction on a broad range of issues.

Sam: David Singer from Apple has proposed banners on specs with such warnings, right at the top like WICG does with compat and availability info.

Joey: building on what Chris said, I totally agree with what Sam said. Users won't understand the risk even if they see them highlighted in the spec. I wonder if there is a scenario where asking for uyser consent on those sort of things would be possible?

Christine: thanks for the comments about the framework/banners. I'm going to take that out of the conversation for today so we can get through the discussion of the issues. Joey-- thanks for your thoughts, would recommend discussing on the issue.

Christine: want to make sure we know where we are with generated wave form. It has a needs-resolution tag, is that right?

Sam: yes, I believe it does.

#### Older closed issues
*   https://github.com/w3cping/tracking-issues/issues/13

Sam: This is just a placeholder.  Nothing we need to do today.

### Media Capture

Media Capture and Streams (aka GetUserMedia): https://w3c.github.io/mediacapture-main/

Pete: getUserMedia a page for requesting info about media devices that are plugged in: webcams, mics, speakers, things like that. A lot of interconnectedness between these issues, will walk through it high level first.

Pete: as it exists today, the draft spec says I can request info about the plugged in devices through enumerateDevices. Will tell me both about what devices are plugged in and also the category of the device. That is currently unpermissioned as described in the spec. Trying to walk through in a web-compat-friendly way how we can roll that back to reduce fingerprinting. Lots of existing content that we'd like to keep working.

Pete: the initial versions of the spec were probably too permissive, future trajectory of the spec is focused around browser interface mediates. No disagreement between PING and WG there. Future state would be much more moderated about what is allowed/blocked.

#### Changes in # of Devices Per Category
*   https://github.com/w3cping/tracking-issues/issues/96

Pete: relates to devicechange event whenever something is plugged in or removed. Leaks info about device capabilities. WG proposal is only fire it when the available categories change. 0->1 mics, fire event. 1->2 or 2->3, don't fire until the page has received permission. Focused on before the page requests permission. My view is this is a net positive change. Trying to disentangle the discussion about what categories should fire by default (work going on elsewhere). I vote for this to be in Wendell's category 2, they're aware of it but not a fire alarm fire type of thing. Seems to be general agreement: we should stay involved, but not category 1.

#### Don't reveal available hardware w/o permission
*   https://github.com/w3cping/tracking-issues/issues/83
*   https://github.com/w3cping/tracking-issues/issues/61
    (only reveal device info for devices in same category as permissioned devices)
*   https://github.com/w3cping/tracking-issues/issues/60
*   https://github.com/w3cping/tracking-issues/issues/10
    (don't reveal any device info before permission)    
*   https://github.com/w3cping/tracking-issues/issues/59
    (don't reveal any device info before permission, move device selection to browser UX)
*   https://github.com/w3cping/tracking-issues/issues/23
    (only reveal device info for specific permissioned devices)

Pete: This category is about what the page should be able to see when no permission has been given, or I give permission for mic but not video camera. What should I be able to learn about video camera if I only gave permission for mic? I don't know how useful it is to go through them, they're all different points on a spectrum. One extreme is the page sees everything without permission being given, the other is nothing at all is seen. And then once I can see info, how much can I see (e.g. device manufacturer info).

Pete: I would put this bucket into category 1, this is worst-case fingerprinting data, very identifying and unpermissioned. Any other opinions?

Christine: queue is empty. Taking silence as agreement.

Pete: want to make sure we take back the right message to the group. Is that "everyone agrees"? ... taking silence as agreement, if that's not the case please chat in our tracking issues.

Sam: +1

Wendell: I think, Pete, what you may be experiencing is we need more deliberation. This being a high ceremony group, we need to tee these issues up, have folks think about them, have people respond, and take a roll call. I think what you want to do is take these back with a banner of authority from the group. I would like to see a bit more deliberation from the others here, e.g. speak one sentence about where you think this should go. And then we can tee them up, have the discussion, and resolve them. We would have a formal agenda and way of talking about these. Something I constantly face is people in these meetings say things like "wow, this is the first time I'm hearing of this." Having someone take all of the air out of the conversation like that is difficult-- let's make sure this group doesn't have that and we have a beginning, middle, and end for handling these issues.

Pete: we have a process of taking up the issues as they come up, but we also send out a list ahead of time. We should review these again in 2 weeks. Say we'll do a roll call in two weeks. Is there other info I or other chairs can provide to inform that conversation in 2 weeks?

Wendell: I don't have a viewpoint on that.

Pete: let's consider it good as-is, continue conversations in the issues. I like the 1-2-3 system, or tropical storm system, or whatever we wnat to call it. PING things and what we put in the issue thing should probably have overlap but might not necessarily. Establishing what we want to do with a formal vote in 2 weeks-- I think that seems like time well-spent.

#### Make device handles less identifying
*   https://github.com/w3cping/tracking-issues/issues/2
    (Dual key device IDs, don't make them UUIDs) Make device handles less identifying
*   https://github.com/w3cping/tracking-issues/issues/82
    (Don't use UUIDs)
*   https://github.com/w3cping/tracking-issues/issues/21
    (Dual key device IDs)
*   https://github.com/w3cping/tracking-issues/issues/2
    (Dual key device IDs, don't make them UUIDs)

Pete: when a web site asks for more information and acceess to a device through enumerateDevice+getUserMedia, they get something structured as a UUID/GUID and this is super identifying since it's unique to the device and/or user. Discussion is about how can we make this less identifying? Need something unique to the user's browser on that domain that is the agreed-upon goal. How close we can get to the ideal with the web-compat-friendly approach? *describes various schems that might work* Also how difficult it will be for implementers is captured in these issues.

Pete: There is a related discussion that is similar but distinct: how identifying is it if we dual key the identifier within a frame? e.g. top-level-origin.example and media-org.example, media-org.example should get different identifiers when embedded across different origins.

Pete: Let's do a roll call vote in 2 weeks. Will try to make sure the issue stays open until then.

#### Text updates
*  https://github.com/w3cping/tracking-issues/issues/81
   (Update spec text to not refer to no-longer-available, pre gUM, fields) underl

Pete: uncontroversial, issue is tagged to PING looking for clarification in the text, mostly to say that different labels are no longer available. Let's make sure spec text is consistent throughout and doesn't expose inconsistent values across areas. Mostly bookkeeping/text editing rather than substantive. Does seem important to make sure it gets sorted out even when we have alignment with the group.

Pete: something for folks reading issues on their own-- when you get a device you get a UUID, a label which is expected to be provided by manufacturer (e.g. "Apple front facing webcam"), group ID which describes a group of devices (e.g. something that has both mic and webcam together), depending on impl. also additional fields.

Michael Kleber: this isn't specific to the current topic, but to talk about the general roll-call discussion. Would like to figure out how to make it easier for people in PING to come to a more informed opinion about these questions. I don't know a lot about a lot of the topics being discussed. When there are 14 outstanding github issues across scattered specs with prior discussion, I worry it's a high burden to expect people to become intelligently familiar with it. Are there relatively short pointers that could be given out to how other relevant groups have responded when we raised the issue initially? I worry if we only hear "this is a concern side", I worry if PING folks don't hear the group's response about why something else might be a more appropriate response, it will be hard to evaluate other ways forward.

Sam: Thank you Michael, for raising the issue about workload.  my concern about the rollcall is scalability. I want us to be in a model where some people can dig in deeply on a particular topic, and then make the decision. As needed others can look at it and weigh in. But not having 15-25 people weigh in on each of these which seems unnecessary and unlikely to be successful. Not a fan of the rollcall approach.

Michael: I agree it's a heavy workload to ask everyone to be fully cognizant of the issues, but a worthwhile exercise for PING or whoever is in PING that are deeply involved with it, to either point at or produce a summary that describes both sides of the situation that we believe explains the PING worry but also provides a summary of the other relevant group's response is/feelings on proposed mitigations. Both sides should believe it's a fair and reasonable summary. Whether that's for the benefit of folks on PING on the rollcall or if it's as the spec moves in process, having a document about what concerns PING raised and what the response was with an agreeable summary would be valuable going forward.

Pete: if what's being asked for is a further write-up it will be a chunk of work, but I would be happy to write a paragraph pro/con for each of these.

Erik: +1 to Michael's suggestion that we get mutual agreement about the summary.

Pete: Let's discuss more on our Slack channel.

Sam: The group we're discussing with could write the summaries too. Probably better if they do.

### 2. New Web developments and privacy considerations

[no discussion]

### 3. AOB

Tess: Privacy CG virtual f2f is next week! https://github.com/privacycg/meetings/tree/master/2020/05-virtual
