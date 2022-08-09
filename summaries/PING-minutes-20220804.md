# Privacy Interest Group meeting (4 August 2022)

## Attendees 

* Pete Snyder (Brave, co-chair)
* Nick Doty (CDT, co-chair)
* Wendy Seltzer (W3C)
* Christine Runnegar (invited expert, PING co-chair)
* Guillermo Movia (Article19)
* Rosemary Kuperberg (Demandbase)
* Don Marti (CafeMedia)
* Sean Harrison (Google)
* Wendell Baker (Yahoo)
* Theodore Olsauskas-Warren (Google)
* Joshua Ssengonzi
* Eric Mwobobia (Article 19)
* Providence Baraka (Article 19)

Regrets: Sam

Chair: Christine

Scribe:  Rosemary

## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/)

Guillermo Movia from Article 19 and Rosemary Kuperberg from Demandbase introduced themselves as newer attendees

 [code of conduct](https://www.w3.org/Consortium/cepc/)

### 2. Privacy review of CSS Color 5 

Request: https://github.com/w3cping/privacy-request/issues/92

CSS Color module for presentation of color.  Pete and Nick helped Guillermo with review.  

New functions - name/color mix that lets you make modifications to the color to help designers make better design systems.  One main color and other colors can be mixed and modified after.

Introduces custom color spaces for certain screens/printers/devices to make the color present better.  

Not many things relevant to personal information that a user would give to the website.  

Open questions - CSS put link to ICC files that the user has to download.  When download occurs, does it download everything for all devices or download a specific version per device?  Main concern about having a specific device (e.g., printer) if you are in a country where certain things cannot be printed, could this ICC 5 be used as fingerprinting to track down where something was printed.  

Browsers need to make calculations for color mixing.  If specific browsers calculate in different ways, potentially a problem.  

Otherwise, no privacy concerns.

After call, Guillermo should raise issues and Christine and/or Nick will mark with the appropriate tracker.

### 3. Privacy review of MiniApp Lifecycle and MiniApp Manifest

Requests:

https://github.com/w3cping/privacy-request/issues/93

https://github.com/w3cping/privacy-request/issues/97

Note another MiniApp privacy request received.

Lifecycle one:  one for overall app, can exist possibly embedded in a larger application.  Different views/constrained images represented by its own HTML and JavaScript.   Opening and closing in the background - developers can respond. 

No unique privacy issues in this spec.  5 non-privacy issues:
1- new web IDL for each event define callback to register for each event that happens; not following web convention
2- spec undefined, e.g., 351 - input query is the input query for MiniApp page.  Interlinked set of specs, would be helpful for more specification and less redundant definitions.
3- Some similar but not identical structure theme that don't quite line up with each other; presentation cohesion issue.
4- Privacy considerations non-sequitur-y; these are all user interactions; will ask for clarifications
5-Accessibility considerations seem incorrect

Pete will file these issues.

Nick: Are privacy concerns part of a full screen issue?  Just presented with Miniapp?  How does user know who they are interacting with?  This spec is only dealing with certain events that trigger when certain things happen - on load, on close, etc.  Is the user agent the super app?  Yes, it would be some code limits outside these author-registered callbacks, but that is also outside the scope of the spec.


MiniApp manifest one:  very simple; looks like an extension manifest; JSON etc.  Looks similar to a web extension manifest.  

2 non-privacy sensitive issues and non-blocking concerns
1- very over specified; copy value from here to here, etc.; over verbose and confusing.  E.g., section 162 - term JSON appears several times.  Bad pattern for specs to have redundant and not clarifying terms
2- other places highly underspecified; talk about specified enums but value of those enums is not stated; spec isn't enough to understand whether a manifest follows the spec or not
(enums is pre-specified enumerations of values)

privacy ones
security considerations & privacy considerations section aren't much about the manifest themselves but about what happens after the manifest; but they are stated here so need to be raised/called out somewhere
1-mani ref external files - guarantee sandbox app on the platform; seems like using external resources, that would be breaking out of the sandbox; possible fingerprinting concern; need to understand better

Comment here from Theodore - did you see update mechanism and whether manifest is readable by the larger app; can app update it later and read what is in the manifest later?  Pete - not said it's read only/one way, but it seems like that is what is intended.  Only describes one-way/one-time read behavior but not said explicitly in the spec.  Pete:  example of it being Hard to review mega-specs in pieces and this is a piece of a bigger thing'; issues need to be flagged somewhere

2-term "sessions" appears for the first time and not defined; unclear what this mean or is used; needs to be clarified in some way.

3-like webapps mini apps can be installed using UI dialogues - means to reference maybe progressive webapps or the ability to pin an app on a home screen; will ask for clarification

Nick - looks very similar to webapp manifest spec, much of it copy and pasted.  Do we need 2 parallel ones?  Could we just use webapp manifest?  Pete - not that he can pinpoint.  Nick - webapp manifest has clear concept of ID - URL that it came from - but Miniapp manifest doesn't.  no explanation of who author of Miniapp is, where it came from, why you should trust it.  Pete - there is an app ID; section 1.6.1; just a string or reverse domain name string; Nick - could type in anything to that string; Pete- validating provenance of the thing should occur somewhere, Nick - pretty important that is validated; Pete - confirmed; Christine - it is a privacy concern to do with transparency

Christine - picking up on question of why we aren’t using webapp manifest.  Unless there is a compelling reason, seems preferable to have one.  Does Wendy know history?  Wendy - lots of conversations in particular with TAG, about web architecture.  Doesn't know where those conversations ended up or the possibility of using a combined one; might group be open to talking again about how to re-use existing specs.  Wendy will talk with team contact for that group to see if there's a conversation to be had about architectural question.

Wendy notes this [TAG design review](https://github.com/w3ctag/design-reviews/issues/752)



### 4. Further discussion of Web Neural Network API (tentative)

Christine - made more notes in the issue in privacy review tracker based on last meeting.  Next steps - reach out to working group to work through various comments and raise issues as appropriate

Anyone with more specific feedback should reach out to Christine

### 5. AOB

IETF meeting last week with a number of privacy-focused sessions

Pete- owe a response to the Web Share API folks need to know whether PING concerns have been resolved.  Anyone want to get that resolved?  Pete can help.  Joshua - requested a privacy review task; can take on another one and help with this.  Christine - This one was a privacy review someone did a few months ago who can no longer finish it, if you're familiar with WebAPI that would be fantastic.  Joshua - will be in touch at the end of this week or early next week after looking at it

Christine - Need as many volunteers as possible doing privacy reviews. Please help by doing them and also by convincing others in the community to help a well.  Group needs help.

Anything from IETF last week that attendees recommend that this group look at? Nick - quite a bit of privacy-relevant stuff; will overlap IETF and W3C; intersection between internet and the web; privacy preserving measurement (ppm) had a long meeting - related to advertising work at W3C; trying to define mechanisms for multi-party computation or mechanism to calculate values without identifying individual data; more detailed proposals now that group can look at.  Privacy Pass - getting more established protocol and proposed extensions; for device attestation, rate limiting, that will be relevant for anti-fraud related work or just trying to measure ad traffic at a large scale or bot traffic.  That privacy pass work is worth looking at; more specific documents about device attestation and rate limiting coming soon for this group to consider.  Messaging things at IETF - openpgp and encryption - more modernized email encryption that it was.  Messaging layer security (mls) is getting close to the conclusion; interest in follow-up work on interoperable messaging apps; How you would discovery and deliver messages across messaging apps; application layer and this group would be interested.

Christine - privacy-preserving measurement group - interesting materials shared before the meeting that this group would find interesting

thanks very much to reviewers.  

Next meeting in 2 weeks. Please share in agenda or minutes topics for next time.




