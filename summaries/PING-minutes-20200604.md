
# Privacy Interest Group ad hoc meeting on the draft privacy threat model


## Attendees 

* Peter Snyder (co-chair, Brave)
* Christine Runnegar (co-chair)
* Sam Weiler (W3C)
* Theresa O'Connor (Apple)
* Jeffrey Yasskin (Google Chrome)
* Shaun Gilmore (Apple)
* Dave Harbage (DuckDuckGo)
* Brad Slayter (DuckDuckGo)
* Konrad Dzwinel (DuckDuckGo)
* David Benjamin (Google Chrome)
* Brad Lassey (Google)
* Wendell Baker (Verizon Media)
* Charlie Belmer (DuckDuckGo)
* Michael Kleber (Google Chrome)
* Lucas Adamski (DuckDuckGo)
* Nick Doty
* John Wilander (Apple)
* Wendy Seltzer (W3C)

scribing: Christine

## Draft privacy threat model

Link to document: https://w3cping.github.io/privacy-threat-model/

Github: https://github.com/w3cping/privacy-threat-model

#### Overview of document

Jeffrey: There is a long list of PRs, eager for feedback. It would be nice to point folks to this document when they're designing new features.I am working on how many bits get leaked when doing a navigation. It would be ideal to collect information on this. 

Pete: Could you please clarify the motivation for taking about entropy bits rather than anonymity sets?

Jeffrey: Two aspects. Bits is appropriate for one and anonymity sets for the other. Fingerprinting allows uniquely identify user over time - there anonymity set makes sense. Entropy bits simpler to think about but less accurate. Cross-site tracking, need to establish user ID is the same across sites, can do with 3rd party cookies and link decoration. Don't need to send all at once, can send bits at different times. It is not the same as cutting down an anonymity set. There is some time-based user correlation that does use user-based anonymity sets.

(Jeffrey showing screen share of https://w3cping.github.io/privacy-threat-model/#model)

If can look at timestamps of link and load, can shrink user anonymity sets.

Don't know how to quantitatively describe that

Brad Lassey: Should we add a section to discuss different measures of privacy?  (k-anonymity, differential privacy, etc.)

Jeffrey: TODO: File an issue on this; will not file an issue now, but record that we need to discuss anonymity sets, vs. entropy bits vs. differential privacy things (Brad filed https://github.com/w3cping/privacy-threat-model/issues/35)

#### Discussion of overall perspectives on the privacy threat model document

Pete: Before we jump into the substance, it would be good to hear what everyone wants to get out of the document

Tess (Apple): We are interested - like to see a more rigorous approach to evaluating the privacy implications of different Web technology - we would like to ensure that the threat model is sufficiently complete to describe threats that most browser and Web communities are concerned about - with Apple hat off, but with TAG and PING hat, would like a good document to reference for design reviews with a shared vocabulary

Konrad (DuckDuckGo): We want to understand document well, to reference in future reviews, learn from people here re: tracking. We also have our mobile browsers and want to make sure we implement them correctly

Wendell (Verizon Media): Same sort of message. We are talking about a safe harbour API in the advertising users group - codify what is in the line, and over the line - people in business like to go to the line so having it documented is super useful

Jeffrey (Google): We are trying to add a bunch of new features and trying not to violate privacy principles. We ran into a lot of trouble with people not knowing where the line is, with privacy advocates and others.

John (Apple WebKit): At a recent Privacy CG meeting, I shared Apple position on anti-tracking on the Web. I don't think it is covered in the threat model currently. We think autonomy is an important thing, i.e. owning one's self-image and how one presents oneself, how I like myself to be presented on the Web. If machine learning is applied to collected data, other things might be deduced. This kind of data can be used for manipulation, e.g. for voter suppression, political manipulation or to gambling or other addiction. I would like to see this in model - it is a real threat.

Jeffrey: I have an issue about manipulation in GitHub, but not yet about autonomy. This needs to go in document. Please do a pull request.

John: Please ping us if you don't hear form us

Michael (Google Chrome): I'm interested in the document because we want to add new APIs to the Web to do things in a more private way. It’s useful to have a way to talk about what is private and what is not, and which is more and which is less.

Pete: 3 different ways to approach document =>
* categories of threats; 
* quantified approach (don't care so much about capability, but rather how revealing, e.g. on anonymity sets); 
* set of principles, e.g. if there is a more private way to do it, we should do it.

Pete: We should discuss which the document intended to capture.

Wendell: The notion of identification and entropy will be easy to solve because scientific, easy to measure. Manipulation will be more contentious because there is social context etc. We've experienced the notice of the nudge and how important defaults are, e.g.  re: 401K. But the notion that there is bright line or that it is well understood as what is right and wrong will be difficult.  Verizon Media has a promotional relationship with a gambling enterprise - question whether this group wants to have an opinion on that. To wrap up, entropy is easy, others harder.

Nick: I’m not sure that entropy is as easy as people think. I am mostly led to the idea that it will not be an easy result. Things are so contextual that it is difficult to come down to a single number. However, we should still continue to work on entropy. But, we shouldn’t expect numbers to be the answers. I’m glad to see the document move in the direction of going beyond the issue of identification and re-identification. It should not be the only privacy concern. It should include manipulation, but also disclosure (e.g. access to camera to take compromising pictures)

(Pete: seconding the above, entropy is not easy, and marginal-identification is much much harder)

Jeffrey: Agree with Nick.  All 3 approaches will be needed. The part that is fleshed out most currently is anti-tracking which relies on quantification. Other pieces may be less useful for people writing APIs because they would need to discuss with the privacy group to understand how far to go.

Pete: Regarding principles – these could also be principles to spec authors (like the questionnaire) or more general like goals for the platform. We need to sort out these high-level things now to help move the document forward.

Jeffrey: Regarding the principle you gave - if there is a more private way, use it – as an observation, it doesn't always just give an answer because it might mean less functionality, which we'll have to trade off - a starting point for discussion.

Pete: How do people want to proceed?

Wendell: What did we just decide? Did we decide numeric approach? But, with the manipulation things, we probably won't see agreement.

Christine: Not in response to Wendell, but if we have time, I think we all agree that the document needs a combination of all 3 approaches. Is it useful to spend some time with the more high-level things, talk about what might be some principles for the document?

Jeffrey: Let's look at the grid with the concrete threat model first and see if we all actually agree with it.

Pete: Distinct from the overall goals of the document, there are also 2 different approaches we could take – (1) reason in the abstract or (2) take a case law approach, keep doing reviews and finalising with the results of that process.

Tess: The latter is what we do in for the TAG Design Principles

Jeffrey: We should do both

(Christine +1 to both)

Wendell: what Jeffrey said

Pete: How do people want to proceed going forward? GitHub, calls, or ... some calls might be useful

Jeffrey: I want to encourage others to weigh in on what we have. We haven't had enough discussion on issues to justify a lot of calls. Let's write text in issues first. We need more text before spending call time on the issues.

Wendy: Picking up from what Tess said, we could tag issues from privacy reviews that raise a new point for threat model or helps consideration of what is in the model. In other words, build up a set of examples. Perhaps people doing reviews or who have seen reviews could add these.

Pete: I can take on an action item to summarise lessons learned from privacy reviews for discussion. As to the point of quiet repo, it’s hard to have high-level conversation split across GitHub issues. It would be helpful for me to know more about how we feel about high-level issues.

Sam: The first point, most belongs in the Self Review: Security and Privacy Questionnaire we publish jointly with the TAG and which you have become an editor. Consider if it belongs there.

Pete: Once done, threat model will be principles and the questionnaire will be the check-list.

Tess: agreed (as editor from TAG side)

Pete: I'll take that action item on and prepare by next week or so. Is there anything else procedural to discuss?

Wendell: Was John's question in chat answered?

[notes from Zoom chat] Free from manipulation and personal intrusion. Independence if you will. Power over your own self and how you are treated. Affects how we view APIs. Can the user be tricked or harassed or pressured? To give some concrete examples: You may want to present yourself with one gender, age, race, background, or talent. However, ML applied to your browsing habits may categorize you differently and if you can for instance be targeted with ads or messages based on what the ML has concluded (with all the flaws statistical models have), you lose your autonomy. The other kind of example is trying to quit a bad habit or an addiction. You should have reasonable power over that on the web. 

John: I was answering Nick's question, will add issues.

Nick: That would be helpful.

Jeffrey: [cross-site recognition grid] (https://w3cping.github.io/privacy-threat-model/#model-cross-site-recognition) (being displayed) we have x for not allowed and some √ for things that are irretrievably allowed. I want to make sure √ are correct, so turning to the first one

#### Discussing the table in the document

Pete: What is the goal of this conversation?

Jeffrey: To make sure the √ in the grid are accurate

Pete: What is the goal of table?

Jeffrey: If an attacker has particular capabilities, he/she will also be able to achieve these goals, don't think we can fix it.

[blank]: Cross-site recognition, see the title, this is what this is all about.

Wendy: I am trying to understand. Is this the ordinary browser, and ordinary user? For example, a Tor browser might do more to obfuscate, and users might be willing to have more delay for less click-through tracking.

Jeffrey: You can take some extreme measures to block tracking, but the question is could this be extended to the Web? So, this is mainly mainstream browsers and users.

Brad: Un-mitigatable or mitigatable with bad user experience?

Jeffrey: If we can ship by default, this is target threat model. This is what we want to achieve. If can't do by default then it should be out of bounds.

Brad: Pre-fetch - to make uncorrelatable, would that work?

Jeffrey: User id transfer with and without a navigation - this line is in unclear way - transfer of timestamp with the fetch only if navigation - other ways for pre-fetch, maybe turn box to x

Wendell: This seems to touch on first party sets. My company wants to do this because we own a bunch of domains, brands like branding in the DNS system. If there is an approved method for doing it, it would be much easier to achieve. How big is a first party set?

Pete: I’m not sure I understand. I see the title. Is the principle that the sites should not be able to track across first party sites? I need the high-level goal to understand the table. 

Jeffrey: We write down overall principle earlier in the document. It does not say actors should not be able to track users across sites, but should. But, you can't make it universal because of capabilities of attackers identified below. Feature designers don't have to achieve the impossible. The x and √ define what is possible and impossible.

Pete: That means we should change the principle then to what is achievable. 

Jeffrey: If we can define as a principle, great, but not easy, so we need this section to elaborate.

Wendell: Another perspective. Someone from outside this group might read into document that a group of people made a decision about what should happen with a site - points to a principle - a site is an origin is a single DNS name - what you have in the current system - √ are fine, but codifies, and things change, would √ evolve or fixed, if principle changed?

Jeffrey: Site definition matches html definition, use the public suffix list. If a site can be not under same public suffix, I don't think the grid changes, just change site, not what can do within sites and across sites

Wendy: Thanks. As I am getting back into the context, we might want to be clear whether grid is descriptive or prescriptive. It is useful as descriptive for most users and most browsers, and I can see how to change √ or accept some as immutable and work around them.

Jeffrey: I think the table is a mix of both, argued with myself whether should add “this is possible today, but should get rid of it”.

John: Similar question to Wendy. A combination of problems we see with no solutions today. Maybe we need 3 => problem with solution, without, or already fixed. We need to first settle on what the threat is. Cross-site tracking (at least without user control) is a problem, then we can decide what we can or cannot fix today.

Jeffrey: Agree

Michael: We need to recognise threat, but the value in what Jeffrey has done in grid is a sufficiently powerful attacker and the current Web. We don't see a way to address that now. Maybe in the future there are big changes that prevent powerful attackers from getting access, but that seems unimaginable. Given the Web today and reasonable incremental change, if sufficiently powerful they can still get. Useful to describe.

Brad: +1 regarding the 3-state approach mentioned above

Wendall: +1

Jeffrey: I think we can get the 3-state approach. Some green x might need to say not achieved yet. We can even have some information for API designers that will keep what Michael wants.

Pete: We still need these are the goals we are trying to achieve.

John: We get to tri-state. It can serve as a useful starting point for research => here are the unsolved privacy problems of the Web platform that “I'm going to research for my PhD”

Pete: I’ll do my action item, more discussion in GitHub. Could someone capture the discussion today as issues?

Jeffrey: I'll do that.

Pete: Let’s continue monitor the state of document to keep it going.

Wendell: Once the document is stabilised to a reasonable level, is there interest or value in having a signatory concept for companies that think this is a good thing? It will have some W3C status, but not required. How do we show that this is relevant and that businesses abide by it?

Jeffrey: I don't think there is a definite way to do that. PING can publish as a note. TAG has findings, and there was some discussion about how TAG in future might issue documents more reflective of W3C consensus. This document is intended for browsers to enforce, so I’m not sure why companies would sign. Maybe they could say will not try to circumvent?

Wendell: Agree on idea of saying not to circumvent. In the ad world, there is lots of self-regulation.

Jeffrey: Organisations could do that, but I’m not sure what they would need from us.

Pete: end of meeting
