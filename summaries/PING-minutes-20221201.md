# Privacy Interest Group meeting (1 December 2022)

## Attendees

* Christine Runnegar (co-chair)
* Sam Weiler, W3C/MIT
* Nick Doty (Center for Democracy & Technology, co-chair)
* Peter Snyder (Brave Software, co-chair)
* Sean Harrison (Google)
* Aram Zucker-Scharff (The Washington Post)
* Darryl Green Jr (The Washington Post)
* Don Marti (CafeMedia)
* Tom Van Goethem (Google)
* Wendy Seltzer (W3C)
* Rosemary Kuperberg (Demandbase)
* Jeffrey Yasskin (Google Chrome)
* Guillermo Movia (Article19)
* Eric Mwobobia (ARTICLE19)

Scribe: Sean Harrison

## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/) 

a couple new folks, welcome!

using the q, and not always talking so quickly

### 2. Privacy review of VISS 2 Core and Transport

* https://github.com/w3cping/privacy-request/issues/102

[Sam] Links
      Specs for how to move information off of a vehicle, and request it for other applications. It could be for applications running on the vehicle, or to some data silo off the vehicle. They are not defining the data being moved, just the mechanism. A lot punted off to other specs, not complete archietecture. [TAG link] They said hard to evalutate, it would be easier if you were talking about use cases from the user perspective, user centered design. Ongoing issue, coming up in the WG charter review a couple years ago, you should have a comprehensive archetecture first. Have asked for a S&P self review. Amy had specifically pointed out a impacts self review. The transport document has no privacy or security mentions. The have multiple transports, new one is HTTP, no guidance for name or IP address to go to, faremd out to undefined ecosystem manager. This is creating a point of centralization that fits car manufatuerer buisness models. Not sure we should be standardizing this or if user centered design dictactes something else. They say their auth is modeled off of OAuth2, but is not OAuth2 itself, and suggest using VINs or psuedo VINs. The first is a static identifier and the second is undefined. Some things point to a best practices doc that says very little about priv/sec, a few things, but very little. Links out to diff privacy, but they are not picking out any of what to do, just pointing out these technologies are interesting. Since they are not doing a top to bottom design, these are just ideas that are not baked into the system.
      
[Aram] Their best practices tie to consent, but that the conesent section is non-existent in the spec. If they are tieing all of their practices to consent it would need to be better defined.

[Sam] How do we want to engage with this WG? looking at their best practices doc it seems they lack the expertise to dig into this. 

[Aram] Part of the problem is that no one on this call has much knowledge on how car data systems work, so we could have some sort of joint brainstorming session with them to chat about changes to the spec and their best practices doc. Without more knowledge it is hard to say how this is insufficent and what they need to fix. It is difficult to give consent without thinking through these system archtectures. eg. does speed info need some sort of psuedo identifier

[Sam] They don't specify what the data elements are, speed, precise geo, who knows

[Aram] We should push them to at least give us some types of data. So if the type of data is this, you need to do this. It will be difficult to push a change without more knowledge of the landscape.

[Sam] I think they are tryint to dodge providing this information, they are saying they will deal with the problems with the data later on, not this layer.

[Nick] Sometimes we see early work at W3C, might not have extensive privacy or really anything if the spec is early. How is this currently depoloyed or used now?

[Sam] I see things in the explainer, but I don't really know. It might be deployed with no interop?

[Nick] This seems like the sort of question we could ask their group, maybe have some people here join their calls.

[Christine] We should at least have a call with them/join one of their calls. The ECRIT WG in IETF have done some work around emergecy calls from vehicles. Not just calls in the traditional sense but also sharing of data. There may be some people in that group who could help us. I can reach out to them.

[Sam] Anyone deeply interested in this?

[Christine] Not deeply interested, but this does have the potential to affect a lot of people and be a model for other technologies, so we should enage with them.

[Sam] I think they have meetings at our time, on Tuesdays

[Aram] Happy to switch out with someone to join the meetings, could see this playing out in smart home space. Don't think I can join all of their meetings, WOT meets like 8 hours a week. Happy to help if someone could switch off.

[Nick] Next step is to join a meeting or ask them for a seperate meeting, send someone to a meeting explicitly to get an overview of current status.

[Pete] Feels very similar to WOT, with 18 specs in the air, hard to help with this many things in the air and some not available but reference.

[Sam] Should we request the diretor not let them publish CR

[Pete] Sounds good

[Sam] They wanted to publish at CR 2 months ago

[Nick] CR feels too early if PING and TAG can't understand the docs well enough to review them.

[Sam] I will reach out and try to join one of their next calls.

[Nick] Thanks Sam!

   https://github.com/w3ctag/design-reviews/issues/768#issuecomment-1283597164

https://github.com/w3c/strategy/issues/240

https://www.w3.org/community/autowebplatform/wiki/Best_Practices#Proposals




### 3. Privacy review of Core-AAM (continued)

* https://github.com/w3cping/privacy-request/issues/95

[Nick] We discussed this at a previous call a few months ago. Joshua had done a review of this accessiblitly API mappings spec, we got some comments, but we had to translate those into specific issues for the WG. After doing a refresher, there are 2 issues that I suggest we open after some feedback. The idea of this is that every OS platform has its own accessbilty services API (screenreader, etc.) it is OS specific APIs, this is the type of button, this is the text, and they are all specific to an OS. This spec is to say you as a browser should translate these HTML things get translated in this way for each OS. The feedback from Joshua is a security risk not addressed in the document, a lot of malware tries to use these accessiblity APIs, because they get a lot of insight into what the computer is doing, read all the test on a webpage, etc. It's a surface, OSes are aware of this and take different protection measures, warning users about some of these capabilites. I'm not sure what changes we should recommend, but it should be a security consideration here. There might be some possiblities for a webpage author to say this is a very sensitive piece of content and might only want it available to UA. That's mostly the security issue, the privacy issue, which is noted briefly in the privacy section. The author of a document can provide different content to someone who is using descriptive technologies to someone who is using these assitive technologies vs someone who isn't. The webiste will then learn you are using these assitive technologies, which could be a fingerpriting surface, but it is exposing this information. This isn't so much fingerprinting, but you are disclosing something about the user.

[Aram] Exporuse vs fingerprinting. I agree that by itself this isn't by itself going to be used for fingerprinting. But fingerprinting is generally using a set of feature to fingerprint, so it could in theory be one of these pieces of information. Not sure how useful it would be as a fingerprinting vector though, might be lower than other detectable features. These ARIA labels are not in fingerprint.js

[Nick] It's not that there is no fingerprintability, but there is a disclosure risk in addition to the fingerprintability.

[Tom] Is it just that the fingerprintability that the user is using a screen reader, or properties of said screenreader, how many bits of entropy could it expose.

[Aram] I don't have a high degree of famility with screen readers, but there are 2 types of fingerprinting risk. Is there a screen reader at all, not that helpful. There is also a differentiation risk, as in this screen reader can deal with this ARIA label but not this one, so it would give you a good idea of the version. I don't know if the ARIA framework is used for something other than screenreaders, changing text size, etc. and if this process is known and be used. Let's say I have a hard time with small text, and so I have something that can increase the size of all ARIA descriptions to 30px. If I know this one UA can take 12px to 30px for these ARIA lables, I can add that text and see if the 30px change happens, I can see this UA is this type, and add it to the overall fingerprint. I don't know if this works this way, but it seems realtively low risk to me.

[Nick] My impression is that the exposure will be binary, on/off. Or maybe it will reveal you are using Apple's tech, but this info is usually revaled in other ways.

[Christine] I may have misunderstood what you said Aram, I accept the principle fingerprinting risk is in the advertising context, but we shouldn't rule out fingerprinting use in other ways such as discrimination.

[Aram] True, but I think the advertising use case is pertinent, if you wanted to ignore these users you could just not add ARIA labels. Governments could try and collect this data and it could flow from advertising. But it is not zero risk from the advertising or non advertising use cases

[Don] In some cases the user who is surveiled is a different person from the individual who the ad is delievered to. There is the chance a user has sensitive info about them collected, and said info is used to deliver targeted ads to their family memebers. Agree with Christine that the fingerprinting risk still also exists for targeted ads

[Aram] Looking through some reference docs, [screen magnifiers are in there](https://www.w3.org/TR/wai-aria/#dfn-assistive-technology), so the use case I described could be in there. I don't know if ARIA properties expose this in any way, but it does still seem relevant.

[Nick] Better sense now of how to describe this privacy risk, I don't know if we have a mitigation in mind, but we can at least describe the threat. I can confirm with the group if the info relaed is binary or not. The security suggestion will just be to descirbe the threat rather than a specific mitigation.

Nick to file 1 privacy and 1 security issue, based on this feedback

### 4. Privacy review of Multi-Screen Window Placement

* https://github.com/w3cping/privacy-request/issues/106

[Pete] This proposal would allow pages to get additional info about screens and their placement. Not a lot of API surface. One is -isextended, saying if there are additional screens. And another for the labels and placement of said screens. 4 issues to file/discuss. The isExtended bit is a passive piece of fingerprinting that is not gated. Part of the API revelas the labels fo the monitors, which seems super high risk, and would recommend they remove it. Need to fix their github before moving to rec. There is a change to clean up permissions around multiple monitors today. If you get neg position back today you can tell there are multiple montiors, or bizarre size. If we are adding an API for additional monitors we can put that info behind the permission for this. And I would suggest this change be made, a rare oppourtunity to clean up an exisitng issue. IsExtended is a true/false if there is additonal monitor, the group says this is needed to determine if they need to ask for mulltiple montiors. It seems this can be handled as when you ask it gives the permission check to silently fail if the user has 1 sceen. This seems like a worthwhile change rather than isextended getting added to fingerprint.js.

[Jeffrey] 2 comments on the IsExtended, I'd understood "passive fingerprinting" as something the browser cannot see, so in this case it would be active. I agree there are 3 levels (browser can't see; browser can see; needs permission) where we only have terms for 2. It would be good to have 3 terms instead of 2. As for couldn't the site just ask for permission, we ask sites to explain the permission they are about to ask for before they ask for it. If the user clicks the permission they should see something happen. Which may be the thinking behind having this info available before the permission

[Aram] I just want to note that window.screen is one of the strongest fingerprinting signals (https://github.com/fingerprintjs/fingerprintjs/search?p=1&q=screen) in use, a bunch of properties are already used for this and adding more info will just make it stronger. The solutions they have here mitigate this in some sense, the additional consent dialog will do more. This is an opporutnity to go back and rethink how this is handled. We don't do a lot of popups anymore outside of identity related stuff. A lot of those now go to an additional tab since popups are blocked by default, outside of the use case they are most worried about, presentations. This may be too late, but they need to specify is this a window or is this fullscreen, and then specify some sort of positioning, right, left, top, bottom. We don't need to expose prescise x/y for any of the use cases in this spec. One example from Google is their slides, and if I say switch to slide mode, I will accept whatever the next popup is. Now Google though the 1st party info knows about the screens and will get this extra info and can associate it. Ironically this risk is smallest in google as they have other identifiers. Let's instead say I use presi and they decide they are running short on money and they sell my username with screen size to data brokers, other things can happen with this data at this point. If this becomes a major vector for indeficiation using slideshoes to try and aquire this screen size info. This seems like a major risk to me, but I don't know if there is a soultion here, but I would love to fuzz window.size in general. There has been a lack of interest as browsers use window placement as some means of differentiation. If we are looking to extend the strongest fingerprinting vector we could look into additinal mitigations.

*Note: existing things they have highlighted themselves - *
- https://github.com/w3c/window-placement/blob/main/security_and_privacy.md
- https://www.w3.org/TR/2022/WD-window-placement-20221101/#privacy

[Nick] I thought you were gonna go a different way with this, that the scope could be narrowed by this as an opporunity, but that it is instead still disclosure. This seems like a time to talk about this opportunity to address window.size that is primarly used for tracking, it is not primarly used for window placement. The other thing is that on the passive fingerprinting, the doc does [specify the 2](https://www.w3.org/TR/fingerprinting-guidance/#passive-0), but it does clarify drive by vs interaction availablity, if there is better distintctions we could have in the terms that would be good..

[Pete] I had not planned on opening the .screen issue today. I had only planned on opnening the issue to just give current screen info until the permission is had. Anything else is beyond the scope of this review.

[Nick] Maybe we will come back to this, if someone wants to take it.

[Aram] I agress that it is out of scope, but for this spec, might we suggest, instead of making screen details available make placement quartiles available.

[Pete] This WG is tasked with multi montior support so probably the wrong place

[Aram] I'll take a look and file the issue if appropriate.

### 5. End of year wrap up and looking forward to 2023

[Nick] 2 things, 1 Christine is taking the lead on a summary of the privacy work done this year in a blog post. Second our charter has been extended, beginning next year we should talk aobut revising or updating our charter, if our group should have the same scope, whether we want to incubate new work, whether we should have WG-style standardization, etc. The charter extension gives us time to have that discussion. If you have any initial thoughts those are welcome.

[Christine] As is tradtion we do a blog post thanking all those who have put in their time and do privacy reviews. If we are able to point to something from outside where someone can say PING made a difference, if you can think through privacy reviews you've done or talked out and instances where we have improved privacy on the web in the next week that would be great.

### 6. AOB

Open reviews looking for reviewers

* CSS View Transitions - https://github.com/w3cping/privacy-request/issues/107

[Nick] The above reviews were opened recently, don't need to assign immediatley, but if they are of interest feel free to let the chairs know, and if it is your first time reach out and we can pair you up with someone to review the specs as well. 

We may or may not skip the next call on the 15th if there is something to discuss or not. 
