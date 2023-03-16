# Privacy Interest Group meeting (16 March 2023)

## Attendees

* Christine Runnegar (co-chair)
* Peter Snyder (Brave Software, co-chair)
* Nick Doty (CDT, co-chair)
* Daniel LaLiberte (Google Chrome)
* Philippe Le Hegaret (W3C)
* Tom Van Goethem (Google Chrome)
* Don Marti (CafeMedia)
* Jeffrey Yasskin (Google Chrome)
* Eric Mwobobia (ARTICLE19)
* Guillermo Movia (Article19)
* Wendell Baker (Yahoo)
* Diego C

Regrets:

Scribe: Don Marti

## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/) 
 
Welcome, Daniel, participant from P3P days!, but now working on Privacy Sandbox standardization at Google 

Positive Work Environment CG is working on updates to the CEPC, and guidance for moderation, in case anyone is interested.

### 2. Privacy review of Compute Pressure API 

Pete: overview, this api allows for infomation about state of the CPU, future will include GPU

register for events, receive notifications, responses are bucketed, receive info about the user visible effects of why there is
compute pressure, might be battery?

quite a few concerns

not a blocking concern: formattting errors, everything nested under a subsection, will note as to be fixed 

security and privacy concerns should be broken out

vague but similar to chrome use of motion sensors -- you get a symbol in url bar. Not descriptve, where is this prompt going to appear, more information needed to make this useful

you can get some information on why compute presure is going on -- not clear why this is useful to page, also a fingerprinting vector, not clear why this is useful if the point is to select less intense code paths

3 subconcerns in security and privacy section

timing effects -- this is a broad term, need to be more precise here, what kind of timing attacks?  Cover channel? Ephemeral fingerpringint?

3b. No side channels is a goal not a feature. this text appears unrelated to side channels

3c. first party context -- this seems confusing. Usually refers to site, text mentions origin, need to clarify origin or site?

1st paragraph says only 1st parties can use, later 1st parties only by default

4th and broadest concern, this feature can be hijacked to create a covert channel

can be used to link two devices in separate context

limit which sites can receive noticications, but if 1 site is reading a channel the other site can "write" to the channel by pegging the cpu 

seems to be fundamental to the proposal, need to understand how to prevent this

last and related, the privacy benefit of the events model relies on the UA queuing events and releaseing them to the page strategically. If the `takeRecords()` method allows the site to drain the queue arbitrarily, this seems to undo the privacy benefits of the "event broker" defense

not clear what role this is playing, needs clarifications

1 non blocking issue, 4 other issues

will add notes

Jeffrey: question about whether exposed to 3rd parties

there is a mistake in teh spec, only exposed to same origin. Permission policy in section 6, 1st party can delegate to other origns, expliciti if 1st party wants

rate limit of 1 per second for foreground pages, 1 per 10 seconds for backgroudn pages, seems like a low rate, 2 pages would have to be open for a long time to transfer much information. Open to changes in rate limit if we can figure out

Pete: permission policy address concern, needs to be made explicit in text (can restrict sub frames of same origin) Still ambiguity, good to have clear in spec

rate limit is not robust sounding, some times in video conferencing, a page woudl be open for more than 30 s and could transfer 30 bits -- writing to the channel is not limited 

Jeffrey: knowing that you're receiving a message is harder than receiving a message, not an expert on signaling to recognize that a message is being sent. Need to identify that someone is sending info

Pete: 60 bits still practical

Nick: risk of identifying users across multiple origns, empemeral fingerprinting -- protect by jst firing events for active window

video conferenceing often in a background window, so events still fire there

complicated algorithm for which window/frame is able to receive compute pressure notifications. Can someone explain?

can all background windows get this or a limited subset of background windows?

Pete: my understangin is that any window can get this but only 1 at a time. need to look at algorithm to see if this is accurate

Nick: any backfround window can do it but foreground gets priority? Seems like it introduces risk but maybe that is the only way to accompdeate background video conference window

clear on action items: Pete to open issues -- blocking and non-blocking (w3c Privacy Slack or follow in GitHub)

### 3. Privacy review of Web Content Accessibility Guidelines changes

Christine: not ready to cover today, have reached out to Leonie but not ready 

Nick: follow up later


### 4. Privacy re-review of EPUB 3.3. changes

Nick: new version to update 

2021 review of privacy and security issues, group has addressed, plans to move as a candidate recommendations.

did not have much on how web documents can learn about people, now there are noremative recommeendations in spec, this is positive

had been an epub reading duplicate user ageent string, a model that we are moving away from -- has been changed to feature detection, improved design

added info on threats including DRM, which requires closed source plugin to decrpt content, those plugins require PII and often log with a drm provider -- very little that the spec does to address this, group cannot address DRM in current charter but did note substantial privacy threat

also integrity and authenticity of content, on teh web we use HTTPS and Certificate Authority system to detect that content is not modifid on the way to you

but epub does not have a way to know if it is the same original as what the author of the book intended. noteed as a concern, there will need to be some kind of signature capability in the future. You will need to be careful about sideloading books, this is a use of the term "sideloading" but with no signatures then sideloading is no different from any other kind of loading an ebook

those are major issues raised previously, some have been addressed and some are open issues that are not addressed in this version of spec but noted for future reference

will need to review specific issues from prior review, and open issues as necessary


### 5. Privacy review of Web of Things (WoT) Profile

Pete: sending their review on their behalf -- a pretty wide set of wot specs

number of requests that it would be good to make sure are authenticated

second: is there some way to ensure enforcemetn, if someone is following api can we be sure of behavior. Will work with Mu Lei to make sure I understand issues correctly

Nick: more on enforcemetn?

Pete: I thnk he means what kind of client side guarantees you can give

Nick: sounds like this is issues that we can be opening


### AOB

Any open reviews?

Reviews are currently all in progress or assigned! Great work all.

Next meeting scheduled for April 6, but will provide an update closer to that time, based on agenda items and privacy reviews needed.

Thanks Don for scribing.

Thanks all.