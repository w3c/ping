# Privacy Interest Group meeting (18 March 2021)

## Attendees 

* Peter Snyder (PING Co-Chair, Brave Software)
* Sam Weiler (W3C/MIT)
* Christine Runnegar (Co-chair) 
* Lionel Basdevant (Criteo)
* Terri Oda (Intel)
* Shivan Sahib (Salesforce)
* Kris Chapman (Salesforce)
* Kelda Anderson
* Basile Leparmentier
* Sean Harrison (Google)
* Don Marti (CafeMedia)
* Leparmentier Basile (Criteo)
* Tess O'Conner
* Jade Kessler
* Tanvi
* Nick Doty
* Michael Kleber (Google Chrome)
* Eric Mwobobia (ARTICLE19)
* Roy (Mu Lei)
* Shaun Gilmore

Scribe: npdoty

## Privacy reviews

### 1. Federated Learning of Cohorts (FLoC)

Reviewer: Pete
Reviewer: Kris Chapman

#### Background

FLoC is a draft in WICG. It proposes "a new way that browsers could enable interest-based advertising on the web, in which the companies who today observe the browsing behavior of individuals instead observe the behavior of a cohort of similar people".

Link: https://github.com/WICG/floc

#### Discussion


Kris: browser has a model in the browser, organizing people into cohorts/groups. biggest concern was the fingerprinting vector: additional interface to fingerprint/identify the browser. how often will someone's cohort change? mobility or persistence? how unique will the cohorts be? don't necessarily have the details about what would be a privacy issue and what is just a possible privacy issue.

Kris: generally in favor of flocks/cohorts, but concerned about the black box nature, lack of transparency. auditing behind the scenes, for example.

Kris: how will others implement this if other browsers don't collect all the same information? and if every browser had their own algorithm ... could make the browsers more unique environments, which could lead to fragmentation for web authors. (scribe tried to interpret that concern but may have missed.)

Kris: "sensitive cohorts", as a goal, are not created or targeted. who is determining what is a sensitive cohort, and who is able to audit?  regarding user controls, users are proposed to have the possibility to opt in or out. but could users indicate what they think is sensitive, what information or what domains they wouldn't want to be used. and users could control to whom the cohort identifiers are sent.

Kris: abuse protection, could a malicious site change cohort id or use it against the end user?

Kris: I find it acceptable as a privacy matter to have a cohort where the specific user can't be identified.
Pete: privacy protections re fingerprinting seems to be tied to the privacy budget project, still in early stages about whether it could be feasible or not. FLoC is most useful when it's most distinguishing among customers, a FLoC is perhaps most valuable when a large group cohort is easily distinguishable by other browser characteristics.

Pete: most concerning is adding more cross-site information that's being disclosed by the browser to sites. if I broadcast to most/all sites new information about me -- seems like an inherent privacy loss. if I'm shopping for a particular type of clothing, I might not want that information shared with my bank or other sites that I visit. nothing inherently sensitive about any particular set of info, depends on the user's thoughts.

kleber: haven't published all the details yet, but more information is forthcoming, agree that not everything is disclosed yet. so many open questions will be clarified. we started an early TAG review, but understand there aren't enough details yet for a wide review.

kleber: should maybe separate from whether targeted advertising is an okay thing to do at all. it is a widely used technique. chrome is generally very supportive of the ability to target ads, and for websites to make money. think it's an improvement to be able to remove third party cookies without most websites losing most of their revenue.

hober: TAG initial design review: https://github.com/w3ctag/design-reviews/issues/601#issuecomment-783780556
almost entirely re privacy concerns, similar to what kris/pete raised in this privacy review. those comments might be useful in raising issues.

kleber: chrome working on a response to the tag review, more info coming soon.

basile: concern about targeting a marginalized group/subcategory, concerned that because there is a potential for abuse, that cannot be realisticaly solved, that we will spend a lot of time moving from third party cookies to FLoC, and that FLoC will be removed (as it is abused), meanign a lot of work for nothing. What categories are sensitive in one country won't be in another country. impossible to completely remove the risk of grouping together people in a marginalized group. because it will be generally available, might be easier to abuse (than the current system where an attacker needs a large infrastructure of ads/tags). could become a low-cost way to discriminate against people. it would be very cheap to start a new browser, browse sites of particular interest/concern and observe the resulting FLoC. 
Issue link: https://github.com/WICG/floc/issues/36

donmarti: what about training sensitive cohorts on apparently non-sensitive pages? for example, the language of a page could be revealed (even if the topic is simple/non-sensitive) identifying the user as a likely member of a language-speaking group within a multi-lingual country. some sites are more or less usable by people with particular disabilities, and so pattern of usage of non-sensitive sites (or non-usage of sites) could create a cohort that is correlated with a particular disability.

kleber: very interested in this and will publish more. t-closeness: will identify that some pages are sensitive based on their content, and advertisers already have tools for classifying sensitive pages, but a FLoC is sensitive if the fraction of people who go to a sensitive page is larger than the population at large. if a particular cohort visits, for example, medical pages more often, then the cohort id itself is sensitive.

donmarti: looking forward to seeing more research on that. (Remaining question is whether people who are long-term members of a sensitive group actually visit pages related to that topic often enough to be within the FLoC training window)

weiler: what threshold size is important? some significant things can be learned if only 1% more significant.

kleber: t-closeness is a tunable parameter. current implementation is just a very beginning. currently using pre-existing list of google rules about what ads can't be targeted at. currently looking at t = 0.05, whether it's 5% larger than the population at large.

pete: concerned about revealing information (like my diet) to sites who might judge me based on whether I have diet.

kleber: always the case that there will be different proportions based on FLoC (even if the flocs were generated randomly) and whether you can actually correctly infer browsing history from the cohort. you could have an elevated probability to thinking something about someone, while still not having a good sense of whether the person definitively did visit a site. that's why it's useful for ad targeting, but not very accurate for drawing conclusions about an individual.

basile: some categories (diet, language, etc.) will be sensitive in some places and not sensitive in other countries. if you currently work with a sensitive category, then you won't be able to do business with google-based advertising, where it was possible in a more constrained/safe way with 3rd-party cookies. concerned about how easy FLOC can be setup, compared to building a third-party cookie network.

kleber: 3rd-party cookie might have been done in a much _less_ safe way (because it could be down to the URL level). but alternative systems for targeting (turtledove etc.). floc is just intended to be useful for some use cases.

### 2. ARIA in HTML

Reviewer: Shivan
  
#### Background

Spec: https://www.w3.org/TR/2021/WD-html-aria-20210301/

This specification defines the web developer rules (author conformance requirements) for the use of Accessible Rich Internet Applications (WAI-ARIA) 1.1 and Digital Publishing WAI-ARIA Module 1.0 attributes on [HTML] elements. It also defines requirements for Conformance Checking tools. 

Link to raise issues: https://github.com/w3c/html-aria/issues

https://github.com/w3c/html-aria/issues/295 was the issue filed

#### Discussion

Shivan: We had previously filed an issue for [WAI-ARIA](https://github.com/w3c/aria/issues/1371) and after discussion with the ARIA folks the consensus was to add a privacy considerations section in v1.3. My suggestion for this doc is to have a pointer to that privacy considerations section. 

shivan: when the new ARIA version comes out -- issue raised in github: https://github.com/w3c/html-aria/issues/295

weiler: suggest separate security and privacy considerations sections, even if they're basically empty. to give people consistent guidance.

### 3. Media Capabilities

Reviewer: Lei Mu 

#### Background

Spec: https://w3c.github.io/media-capabilities/

This specification intends to provide APIs to allow websites to make an optimal decision when picking media content for the user. The APIs will expose information about the decoding and encoding capabilities for a given format but also output capabilities to find the best match based on the device’s display.

Security and Privacy Considerations: https://w3c.github.io/media-capabilities/#security-privacy-considerations

Answers to Self-Review Privacy and Security Questionnaire: https://github.com/w3c/media-capabilities/blob/master/security-privacy-questionnaire.md

Link to raise issues: https://github.com/w3c/media-capabilities/issues
  
#### Discussion

roy: real-time feedback about playback in order to do adaptive streaming, for example, to react to cpu/gpu usage spikes on the user device

roy: power-efficiency field: could that reveal the user's device battery status? or does this field make it possible for a site to intentionally heat up the device?

roy: is the capabilities api broken if the user disables webrtc in the browser?

Issue filed: https://github.com/w3c/media-capabilities/issues/170

weiler: seems like there might be a architectural issue here re: negotiation.  Why not expose the available media types and let the browser pick?  See:
https://github.com/w3c/media-capabilities/issues/170#issuecomment-802024277

Nick: the came up in WebRTC in the past; they generally rejected that approach.  We should look at that previous discussion.

Pete: WebRTC is doing similar things re: enumerating devices, v. browser-mediated device choice.  We talked w/ WebRTC - they seem inclined to move toward what Sam suggested.

Sam: these are somewhat different.  User more involved in the device choices

npd: yeah, maybe more similar to content negotiation/img sets.

Sam: which of these pieces do we flag as -needs-resolution?

weiler: similar idea as the issue we raised re: sample rates as in web audio, only expose a least-common-denominator rate unless given permission.

npdoty: media capabilities spec already has some non-normative analysis, including suggestions of choosing common device class identifiers.
weiler: good analysis in that section, but doesn't have normative mitigations.

pete: also want to note that fingerprinting vectors should be marked.


