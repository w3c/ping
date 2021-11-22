# Privacy Interest Group meeting (18 November 2021)

## Attendees 

* Christine Runnegar (PING co-chair)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C/MIT)
* Pete Synder (Brave, PING co-chair)
* Nick Doty (CDT, co-chair)
* Jeffrey Yasskin (Google Chrome)
* Eric Mwobobia (ARTICLE19) 
* Sean Harrison (Google)
* Theodore Olsauskas-Warren (Google)
* Aram Zucker-Scharff (The Washington Post)
* Kris Chapman (Salesforce)
* Wendell Baker (Yahoo)
* Joshua Ssengonzi (Invited expert)

Scribe:  Sean Harrison 

### 1. Privacy review of Incremental Font Transfer (reviewer: Pete Synder)

* Spec: https://w3c.github.io/IFT/Overview.html

* Results of self review - https://github.com/w3c/IFT/issues/35

* Spec explainer: https://www.w3.org/TR/PFE-evaluation/

Peter - Purpose is to allow browser to request subsets of fonts, and incrementally request more and more of the font as needed. Background is fonts can be very large (e.g. Japanese, Mandarin). The idea is the browser can observe what subset of the font has already been cached and request more characters from the server as needed. 3 issues came up. First 2 called out in the Priv/sec section, browser can tag onto the request the current network conditions (high/low bandwidth), seems like a weird fingerprinting risk to include. Particularly odd since the browser is fully in control and aware of network conditions, so no reason to include this additional fingerprinting information.

Nick - There seem to be other specs that propose revealing network information, and makes sense to keep it in the network information spec, rather than including it in individual specs.

Jeffrey - Even if we include it in these specs it should only use the existing buckets from the network information spec

Peter - I am not aware of a current proposal in front of the W3C for this, but that Chromium does implement it itself

(maybe https://wicg.github.io/netinfo/ ?) [Jeffrey: Also https://github.com/tomayac/netinfo/blob/relaunch/README.md]

Jeffrey - It is important enough even for Chromium to have it match, we shouldn't expose any additional information

Peter - 2nd issue identified in Priv/Sec is that the server can learn new things about what the user is doing by observing what fonts are being requested. Not something these server can normally observer about a users browsing. It is called out in their analysis, they point out that including unnecessary characters while they are building up the complete font it will obscure what the user is actually browsing. But this seems odd as the browser will pick up these common fonts over time anyways, as the server is only gaining information from the rare fonts that browsers are requesting. Fonts in this line refer to glyphs/characters not full font sets

Sam - Is this partitioned by site?

Peter - This is distinct from the partitioning concern, the page is learning how the user is interacting with the document. I am not sure of the way to handle this, maybe like bucketing the glyphs together. Further analysis is needed I will post it for the team.

[ npd: +1 ]

Peter - 3rd point, the fonts being fetched are partitioned by document. It is unclear to me if the fonts are being shoved in the http cache. This is worth stating explicitly, so that sites can't correlate across visits/time. Something they should add in the document explicitly, as there are many other places this information could live.

Nick - From reading I'm not sure how this is being partitioned. "this should not be available in another document". Is this that previous glyph requests can't be used in a new document or that the font isn't there.

Peter - This seems to me as eTLD + 1 partitioning. The wording of document is not totally unambiguous here.

Sam - They have modified the text quite a bit in the last week.

Peter - I believe I have seen the most up to date text.

Jeffrey - My skim says they are light on details of how this fetching and catching works. There is no call out to the fetch spec. They need to tighten all of this up and privacy aspects will fall out.

Peter - What happens in a document stays in a document, if they instead say do normal fetch stuff these issues go away. I will follow up with these issues.

Nick - It seems we are uncovering how caching should be done, etc. Is this written down anywhere. This will come up a lot, is this in our guidance.

Peter - I don't think we have a best practices for specs atm. We have the priv/sec questionnaire and others. But we don't have any general best advice. The TAG may have that, not necessarily in the PING wheelhouse.

Jeffrey - What we have is in the privacy CG storage partitioning. We should have something that says call to the fetch spec, don't rewrite a fetch spec.
https://github.com/privacycg/storage-partitioning

Peter - More broadly if you don't need new functionality link into existing functionality. We need to be able to point to some guidance somewhere.

Christine - My suggestion is as part of the privacy request repo, we start a place where we can put this advice/learnings and we can figure out if it goes into priv/sec questionnaire. I would be looking for someone to write something, any takers?

Peter - Happy to write something if needed, but I will check with the TAG first if they have it already. Regardless I can own this task.

### 2. AOB

Peter - Nick joining as 3rd cochair of PING 

Christine - Very delighted by this, a lot of work for the PING and this will be a great help

Nick - [IETF 112](https://datatracker.ietf.org/meeting/112/agenda/) some work 1/2 weeks ago, a few privacy relevant things, some of them will be relevant for work for the PING. 2 things that came up were various proxy proposals ([MASQUE](https://datatracker.ietf.org/wg/masque/about/)), and [OHAI](https://datatracker.ietf.org/doc/charter-ietf-ohai/) is being suggested for transactions / not general web browsing. This depends on lack of collusion between parties. Potential new WG on privacy preserving measurement ([PRIV BOF](https://datatracker.ietf.org/wg/priv/about/). This would be good for browsers or clients in general to send data to servers (or set of servers) to get useful aggregate information (if no collusion).

Nick - audio-output requested a re-review to become a candidate, anyone remember [this review from last year](https://github.com/w3c/mediacapture-output/issues/116)?

Peter - I think I did the review, haven't checked if there are any outstanding reviews, they haven't requested a review from PING yet. I will double check if they have addressed the issues raised

Wendell - Amplification of what nick said. talking about Masque and [gnatcatcher](https://github.com/bslassey/ip-blindness), and the conversation was about coverage and scope. The discussion was narrowly scoped to advertising. This may be a subtle flaw in coverage in W3C. In this oblivious http stuff, there is an encryption scheme for the proxy. It may be good for us to give an overview of this before it comes to us so it doesn't come up out of the blue. There is an IETF session with some slides. Current state of addressing and where it wants to go, and removing addresses from the web, and how this is going to manifest. Call for justifications for preserving it, it is on Brad Lassey’s explainer.

https://github.com/ShivanKaul/draft-ip-address-privacy
(npdoty: IP address privacy draft includes details on different use cases for user IP addresses, which is useful for evaluating which need to be supported by different potential replacements or changes that might hide IP address. )

Wendell - There were 3 surveys in the slides that went over it in the address privacy draft, it touches on everything from the oblivious world all the way to Huawei's new IP https://www.huawei.com/us/technology-insights/industry-insights/innovation/new-ip

Theo - Is this the correct forum for this question - long story short BFCache, browser pulls from different cache than the https cache for back forward navigation. Some issues have come up as the chrome team looks to push the boundaries of BFCache. Is the PING interested in looking at this sort of non-spec work that likely won't come through W3C

Peter - If there are new proposals coming up we would be interested in these discussions even if they are not necessarily occurring in W3C.

Theo - I'll post in the slack as they explore the spec for discussions

Nick - Yes we would like to learn more

Jeffery - The [Anti-Fraud CG](https://www.w3.org/community/antifraud/), they are in tension with privacy concerns in a lot of areas, so we should be aware

Peter - XSLeaks: Series of workshops 1/2 weeks ago. Mozilla/Google/Large websites, looking at ways to close ways for information to leak out of sites. Some interest in changing specs around size of network pools to prevent sites from coordinating across boundaries. Extremely excited to hear from the Chrome team about partitioning [`:visited`](https://developer.mozilla.org/en-US/docs/Web/CSS/:visited), which is an explicit cross-origin leak that is well overdue for a full fix. Other things brought up around dealing with cross-site leaks from deep linking into documents, timing issues etc. Very clear privacy implications, even if not all of it is "change to specs" focused.

[XS-Leaks Summit links in the WebAppSec minutes](https://github.com/w3c/webappsec/blob/main/meetings/2021/2021-11-16-minutes.md)






