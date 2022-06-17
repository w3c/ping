# Privacy Interest Group meeting (16 June 2022)

## Attendees

* Pete Snyder (Brave, co-chair)
* Sam Weiler (W3C)
* Wendy Seltzer (W3C)
* Nick Doty (CDT, PING co-chair)
* Theodore Olsauskas-Warren (Google)
* Don Marti (CafeMedia)
* Pragya Seth (Arkose Labs)
* Rosemary Kuperberg (Demandbase)
* Guillermo Movia (Article19)
* Wendell Baker (Yahoo)
* Dan Veditz (Mozilla)
* Eric Mwobobia (ARTICLE19)

Regrets: Christine Runnegar

Scribe: Pete, Wendy

## WebXR Augmented Reality Module 1
Reviewer: Theodore

Theo: This spec builds off the WebXR device API, which defines how sites get access to WebXR devices (audio, video). This spec is small (a few enum values and properties) to bring the WebXR device spec to Augmented Realtity devices. For example, how camera input interacts with existing WebXR APIs. This spec is small since a lot of the existing WebXR device APIs is sufficent to do fill Augmented Realiy features. There are additional related specs coming too to handle things like depth handling / detecting. However, I don't think this immediate spec introduces new privacy concerns.

… Chrome's implementation only allows access to devices (even those the origin already has access to) when there is an active WebXR session.

Nick: Thanks! Is there something potentially idenifying about one's AR device setup (either bc the setup is unique, or the devices are unique)

Theo: yes, these things are revealing, but no more so than hwats already available in the WebXR Device API spec (that this builds off). So, no increase in marginal identifiability

Nick: Anything we need to do to follow up with the group?

Theo: There is an open spec [issue?] asking for a full cateogrization of all possible leakages in the base (Device API) spec.  Theo will follow up on it.

Nick: sounds good, that categorizxation could help structure and make clearer whats being (newly) leaked across specs

https://immersive-web.github.io/webxr-ar-module/


## WebGPU
Reviewer: Pete

https://www.w3.org/TR/webgpu/

Pete: hihg-level, this spec defines a language that can be executed on GPU hardware. Generalizes across different devices and platforms. 
By design, extremely sandboxed, so you don't get access to state outside what you put in. Unlike WASM, no page access. Sandboxed to GPU, result in some drawing on the page. don't have access to much environment beyond what page is explicitly providing. 
... A number of built-in capabilities that runtime provides to the language. Unclear to me whether browser can augument those with language extensions, based on user's hardwarew or configuration. If so, that could introduce fingerprinting. E.g. if the browser sees you have fancy hardware and adds new functions based on those capabilities. if the runtime provides/removes capabilities unique to the user's environment; also some poassibility of timing attacks based on whether it's running on dedicated HW. Not clear the language could be responsible to solve that.

First is a question I need to follow up. Second, if there's a statistical timing attack, sounds like something to note but not needs-resoltuion. 

Dveditz: Do we know if GPUs are vulnerable to same kind of SPECTRE attacks as CPUs? Whether they've updated firmweare to prevent seeing what other processes are running on the GPU. 

Pete: I know there are GPU versions of rowhammer attacks; not sure what opportunities or mitigations

Nick: [shared some references](https://www.w3.org/TR/webgpu/#security-rowhammer). 
... Was curious about cryptomining attack; GPUs can be used in ways that might be bad for the user in new wways. Potential abuse of user resources. 

Pete: general-purpose execution environment, can be abused like other environments, so needs to leave room for mitigations; not sure there's anything language-specific there, though. 

Nick: more power available now making the attack more attractive

Pete: Seems far to ask them to mitigate

Dan: they mention in the security considerations. WebGPU vs WebGl, specifically designed to expose the computation engine. 

Nick: on timing attacks or fingerprinting, "exposing device capabilities" sounds like fingerprint risk

Pete: reminds me of conversations about privacy-preserving path in the standard. Maybe worth saying in text, report default value if you're in privacy mode

Dan: vs what browser could do, would be great to standardize what they should do so developers know what to expect. 
... Really appreciate that security considerations are first, rather than buried in the spec. 

Nick; we should call that out

Pete: should they label it "security and privacy considerations"?

Sam: No need

Nick: Pete, you'll follow up with issues. Thanks!

## TPAC meeting plans

Nick: TPAC is hybrid form this year. Travel and similar are tricky this year. Expecing both lots of remote attendes and in person folks. TPAC is also a good time for privacy folks to meet together AND to connect with other groups, to build relationships, idenitfy issues early, etc.  Nick isn't sure if he'll attend in person, but likely that we'll have some hybrid meeting early in the week.  Dates and locations are on the website.

Sam: If yr coming, come for the whole week. PING is planning on coming on Monday morning, and then spreading to meet with other groups: PrivacyCG, FedID CD, etc. Re logistics: i) registration will open in ~2 weeks, ii) there are registration waivers, iii) no cancelation penalty.

Nick: TPAC will be Sept 12-15 in Vancouver

https://www.w3.org/2022/09/TPAC/ 

## upcoming reviews

Nick: There are open review requests.  Nick and Lubna will work on the DCAT.  MiniApps is in the review queue and we need reviewers.  Baggage API (an enterprise logging system) needs reviews too.  We should have at least one to disucss by our next meeting (in 3 weeks, the first thursday in July). These should be smaller-end reviews.

Sam: MiniApps and tracing are small specs, but could include bigger, interesting disucssions.

https://github.com/w3cping/privacy-request/issues

## any other business

(none)
