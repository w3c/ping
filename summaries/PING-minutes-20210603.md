# Privacy Interest Group meeting (3 June 2021)

## Attendees 

* Peter Snyder (PING Co-Chair, Brave Software)
* Christine Runnegar (Co-chair)
* Pranjal (Brave Software)
* Michael Lysak (Carbon, possibly independent soon?)
* Newton K. (Magnite)
* Joe Lukas (Magnite)
* Brad Rodriguez (Magnite)
* Kris Chapman (Salesforce)
* James Rosewell (51Degrees)
* Jeffrey Yasskin (Google Chrome)
* Peter Lowe
* Valentino Volonghi (NextRoll)
* Wendy Seltzer (W3C)
* Nick Doty
* Eric Mwobobia (ARTICLE19) 
* Brent Zundel (Evernym)
* Mallory Knodel (CDT)
* Sam Weiler (W3C/MIT)
* Sanketh Menda
* Hitesh Lad
* Tanvi Vyas
* Wendell Baker (Verizon Media)

### 1. Privacy review - CSS multi-column Layout Module Level 1 (Pranjal)

Scribe: Jeffrey Yasskin

#### Background

CSS Multi-column layout is a layout specification for taking content and breaking it into multiple columns. This specification was in CR and was moved back to WD status after a long period of no updates. It is already well implemented in browsers and print user agents.

Link to spec: https://www.w3.org/TR/css-multicol-1/

Privacy and Security Considerations: "Multicol introduces no new privacy leaks, or security considerations beyond "implement it correctly"."

#### Discussion

Pranjal: This is a small spec. It defines a way for content layout to be divided into columns, and associates properties with each column. E.g., column width, gaps, count. It's a pretty standard way of using CSS values. Didn't find anything privacy-harming.

Christine: Thank you Pranjal. Curious about the Priv Sec considerations: what could go wrong if someone doesn't implement it correctly. 

Pranjal: There's a couple sections that go through the algorithm for handling 'auto' counts and widths. Looks pretty straightforward. Doesn't look unusually easy to mess up. 

Pete: Closing that review out.

### 2. Privacy threat model (Jeffrey/Michael L)

Scribe: Pranjal

#### Background

Link for discussion: https://github.com/w3cping/privacy-threat-model/pull/41

#### Discussion

Jeffrey - Pull request for the privacy thread model. Michael describes school of thoughts - regulations vs control theory. Regulations are required by companies. Second axis - privacy threats by browsers and operating systems only. Interface between users/browsers can harm user privacy. Not sure if its within w3c scope. Is it appropriate to start talking about that.

Michael - Two definitions of privacy. Not exhaustive. Concept of privacy definitions should be included in the privacy threat model. [Kitten Cluster](https://github.com/carbondmp/Kitten_Cluster) is discussed. Tracking methods for OS/Browser are powerful. Is user-agent/os threats in scope?

Pete: Other working group need guidance in terms of privacy reviews. Lessons learnt from previous reviews.

Christine: Self-review security/privacy review, primary source for guidance on how to do with privacy considerations in web standards. Privacy considerations for internet protocol (IETF RFC 6973), what is the sensible way of thinking of privacy in terms of IETF protocols. (2.) Unsure about scope. (Link to IETF RFC 6973 Privacy considerations for Internet protocols - https://datatracker.ietf.org/doc/html/rfc6973)

Wendy: No definitive answer. W3C focusses on interoperatibility. Same APIs and protocols necessary to interact. Focus of web technologies and specificiations.

Nick: Different concepts of privacy is interesting. No tracking theory has compatibility issues. Seems to suggest a strawman argument. 

Michael: We need more definitions. Individuals should write their privacy definitions.

Jeffrey: 
* Definitions can be fixed in GitHub. Want to focus this discussion on do we want this general direction and if so where?
* W3C can't really "require" browsers to do things: the influence is more social.
* Privacy threat model goal is to write better web specs. The aspects of this PR that try to constrain browsers don't really apply to any web specs, so it's awkward to include them in the threat model.

James: Direction rather than detail. Interoperability is a focus of W3C. Entropy can be viewed as a threat from a privacy perspective. Bring what privacy means for different groups to PING. Do Not Track case study, should bring the learnings to the group. We need definitions of privacy from a wider group of people. I would like to see Sam Weiler or another W3C Team person consult with a wider group of stakeholders and gain their input into the definitions in the threat model.

[UK ICO and CMA position](https://www.gov.uk/government/news/ico-and-cma-set-out-blueprint-for-cooperation-in-digital-markets)
[The Promise and Shortcomings of Privacy Multistakeholder Policymaking: A Case Study](https://core.ac.uk/download/pdf/234109764.pdf)

Michel: 

* @James - It'll take time. Initial draft for privacy definitions can be authored quickly.
* @Nick - If it sounds like a strawman that shows how little we can speak about each other's definitions of privacy. How little we understand each other. We need to write them out clearly for communication. Also, we can iterate
* @Pes - PCG says go to PING. Relatively important.

List of privacy requirements for browsers is needed. Writing the standard is important to apply same privacy we are working towards to the biggest tracking cases.

Nick: Interested in privacy issues of web browsers/operating systems. Do not involve web standards. Might not be relevant to web standards.

Wendy: Challenge of finding all definitions of privacy and consensus is hard. Assignment to W3C team is not possible.

Christine: Hear you Michael about feeling bounced around. Also note concern raised by Jeffrey about dual role as editor of document and Google Chrome employee. EFF/CDT and other organisations do work regarding Web privacy that complements the work that W3C does with web standards. No standard definitions of privacy. Definitions exist around personal data and then laws about how it can be used or not used. Practical - Work on what are the privacy principles for web standards, which was already envisaged in the privacy threat model work.

James: Raise awareness by W3C. Involve other groups and stakeholders. Use PR resources (1.7 FTE) to engage with wider industry. Get their input. [Security/Privacy questionnaire](https://w3ctag.github.io/security-questionnaire/) - As a business owner I embraced GPDR in May 2018 and ensure my business complies. Created [SWAN.community](https://swan.community/) - helps improve privacy, but others here would have a different definition and seek to prevent such legitimate and legal solutions. Security/Privacy questionnaire is flawed and has been flagged by TAG: 1st party vs 3rd party. https://w3ctag.github.io/security-questionnaire/ - Bounced around groups as well.

Michael: Thoughts about consensus are contradictory. PING operates within 1 or 2 definitions of privacy. But W3 itself does not commit to these definitions. May or may not be compatible. Every proposal can use strawman or other methods to hide privacy concerns because it is not defined and they use their own definitions. Using definitions of PING may not align with other groups. Browser based targeting methodology is a real concern, especially as our current proposals could give browsers tracking monopoly. This would shift publisher revenue away from small groups, force login walls, etc. Browser tracking should not be dropped as a concern. By not defining privacy we are allowing these massive user and business concerns to be silenced.

Mallory: Privacy threat model is the applications vs definition for privacy. It’s okay to not have cohesion. Privacy threat model should be specific.

Wendell: @Verizon - What needs to be stopped and business continuity is the focus. This group should focus on the threats that can be documented.

### AOB

Pete: Continue discussion on PR; more privacy reviews have come in - will be reaching out to people to take on reviews; issue outstanding on CSS colour-module
