# Privacy Interest Group meeting (19 May 2022)

## Attendees 

* Christine Runnegar (PING co-chair, invited expert)
* Pete Snyder (Brave co-chair)
* Sam Weiler (W3C)
* Wendy Seltzer (W3C)
* Aram Zucker-Scharff (The Washington Post)
* Sean Harrison (Google)
* Brent Zundel (Evernym)
* Theodore Olsauskas-Warren (Google)
* Don Marti (CafeMedia)
* JoshuaS
* Jeffrey Yasskin (Google Chrome)
* Eric Mwobobia
* Guillermo Movia (Article19)
* Wendell Baker (Yahoo)

Scribe: Sam

## Introductions, and CEPC

https://www.w3.org/Consortium/cepc/

## Web of Things Architecture privacy review

* Editor's: https://w3c.github.io/wot-architecture/
* Last published: https://www.w3.org/TR/wot-architecture11/

Sean: From last time, the in-the-clear issue in TD was a standard DNS link.  It's in the clear because it's DNS. 

Architecture spec is odder than the other two.  Explicitly says it describes what exists rather than being prescriptive.  They don't want to change anything.  Hard to read; few requirements.  Describes configs of WoT devices.  30 use cases.  They justify why no authentication in TD - resource constraints.  I was going to file an issue: if something in a home network, no additional security required, which seems false.  They cover this later, but skip it in security section.  I'll file that later.

Christine: on previous review, similar observation re: hard to review given how this is written.

Guillermo, would you join PING as a member or IE?

Guillermo: I sent application for IE.

Sam: I'll find that and act on it.

Sam: I took an action item to talk to Philippe to make sure that the other two documents are not published before this one. He confirmed that there is a long enough time frame. If I recall correctly, user not really prevalent in the document. What did you see that speaks to that?

Sean: they describe many ways for machines to talk to other machines.  One example with a user.  Much industrial, some home.  

Christine: I looked again at Ethical Web Principles et al and "put users first" is high on the list.  Not sure how to bring that to this group.

Aram: they talk about "remote" "controller", etc, that are in the hands of people.  Maybe instead of a passive voice, maybe "a user might use a remote controller to...".  Hot sure how to bring that to them.  Sean commented on TLS; I see that's an alarming issue.  I'm not sure they've thought about semi-private networks.  Even setting aside the fact that they are often joined by people who might not be intended to be there... they call out use of smart cities, connected cars...  these are all places where it is expected that your private network is not so private.  Lots of WoT use expands into academic situations/campuses.  Crawling these things is a risk.  Not sure how we'd talk about this in the spec.  Fingerprinting networks - use that for ad targeting...  They're not addressing that concern.  We should push them somehow.

Sean: they touch on that in sec section; TLS in public networks.  They split private into two.  Then they handwave.  They poke it, but half-hearted.  

Aram: are there other specs that we should look at as an example?

Christine: geolocation

Jeffrey: there is some institutional memory in Chrome re: how we made that change.  Numbers got high enough.

I filed an issue re: identifiers rotating.  [WG distinguished 3x devices/tracking](https://github.com/w3c/wot-thing-description/issues/1497#issuecomment-1129857998): generic devices not attached to a person v. personal devices.  They might be willing to do something there.  They plan to talk this coming Monday.  Can anyone else go?


Don: risk of repurposing devices for privacy-sensitive purpose, e.g. harmless industrial device, hidden in someone's bag, like an AirTag.  As consumer devices end up with more privacy protection, more risk of repurposing device with industrial use for privacy violation.  

Christine: I'm concerned that devices labeled not-personal are, in fact, quite personally.  Wary of WG taking too narrow of a definition.

Much thanks to Sean; difficult set of specs.  


** PATCG

Aram: Tuesday focused on WG charter changes.  Only one PR left.  CG charter changes also complete.  Apple joined the CG.  Deep-dive into measurement problems & use cases.  This evening looking at TAG privacy principles doc then Robin presenting GARUDA.  Then measurement use cases and requirements and aggregate measurement.  

** WoT charter

Sam: My impression is they do not have someone with privacy experience in the group? Who might be willing to help them?

Aram: Do we have a sense of how difficult it would be to read someone in to this?

Sean: A couple of hours reading into things

Aram: Meeting cadence?

Jeffrey: I did something similar with verifiable credentials. Expect to embarrass yourself a few times. Probably people there worried about privacy risks, your role is to tip the balance for people fighting for privacy.

Sam: Asking the hard questions

Aram: They have a lot of meetings (see: https://www.w3.org/groups/wg/wot/calendar https://www.w3.org/groups/wg/wot/calendar ) I might be able to cover the architecture call

Jeffrey: I didn't go to all of VC mtgs; you can do much by going even to just some and nudging.  

Aram: I could do some; we might need a second person.  I'm interested in the privacy threat from WoT; both in advertising space and @@ increasing FP surface from things that are not browsers.  I suspect that will come in here.  I'm interested; would love it if I had another person.

Wendy: team will be happy to coordinate with Kaz - the W3C Team contact - e.g. to help you decide which meetings might be most productive to join. 

Joshua S: I think the security meetings would be important.

Christine: are you offering to go help, attend those?  

Joshua: I can attend WoT Security calls.

** Upcoming reviews

Christine: WebGPU - we'd love someone with GPU experience.  Do you know anyone in your orgs?


