# Privacy Interest Group meeting (6 May 2021)

## Attendees 

* Peter Snyder (PING Co-Chair, Brave Software)
* Sam Weiler (W3C/MIT)
* Christine Runnegar (Co-chair) 
* Jonathan Kingston (DuckDuckGo)
* Michael Lysak (Carbon)
* Peter Lowe
* Chris Cunningham (Google, WebCodecs co-editor)
* Shivan Sahib (Brave)
* Sean Harrison (Google)
* Jeffrey Yasskin (Google Chrome)
* Sam Macbeth (DuckDuckGo)
* Konrad Dzwinel (DuckDuckGo)
* Newton (Magnite)
* Theodore Olsauskas-Warren (Google)
* Jade
* J Lukas
* Nick Doty
* Phillip Eligio
* Wendy Seltzer (W3C)
* Wendell Baker (Verizon Media)
* Paul Jensen
* Kris Chapman (Salesforce)
* Mallory Knodel (CDT)
* Eric Mwobobia (Article 19)
* James Rosewell (51Degrees)

Scribe: Michael Lysak

## Privacy review of Web Codecs (reviewer: Jonathan Kingston)

#### Background

Spec: https://w3c.github.io/webcodecs/

Privacy considerations: https://w3c.github.io/webcodecs/#privacy-considerations

Response to Self-review questionnaire: https://github.com/w3c/webcodecs/blob/main/security-privacy-questionnaire.md
    
Where to file issues: https://github.com/w3c/webcodecs/issues

Explainer: https://github.com/w3c/webcodecs/blob/main/explainer.md

#### Discussion

Peter: 1 item today, reviewing web codecs spec

John Kingston: js access to low level codecs of browser, coding and decoding
The draft has several use cases in the explainer. Gives examples of the api. 
The draft has a privacy section outlining capabilities including media api, webrtc etc.
Increased fingerprint exposure of codec included. Hardware acceleration increased on most devices. Mitigation of fingerprintability suggested using privacy budget. 
Some undeclared pieces includes timing attacks on the encoding, performance analysis.
Reading buffer data bytes also missing information. EAh browser may return a different result for image data.
Spec has no notion of 'origin clean' An attack could place a cross origin image into canvas and read data in video frame.
Explainer suggests this should allow for high res bandwidth of encoding/decoding. Uncertain if browser should protect against.
Spec does not discuss implementation details. VP9 support, etc. differences between browsers could affect fingerprintability.
The draft also specifies a memory model, unclear is this is a surface area for spector attacks. Cross site headers.
While testing the current code in chrome on web dev, using several different Mac machines with same canvas fingerprint, vp8 rendering makes fingerprints unique. 
API not extensively tested, but clear rendering different. Not compared to similar spec like media recorder. 
TOR, BRAVE do not disable media recorder. 
A line in the spec says: 'underlying codecs are implemented in software' but there is no mention of statistical analysis of output data. Unclear how privacy budget would be implemented without impacting web compatibility.
Suggests User agent common set of features to promote privacy, but not in the draft. Should be in the spec.
This was a high level of findings in spec.

Peter Snyder: Anybody who worked on the spec pls comment

Chris Cunningham: First for timing attacks, yes, there is a possibility, for example, you can decode as fast as possible and observe output rates to detect latency of decoder and pipeline depth. This is not mentioned yet in considerations. I agree it should be. 
The next issue codec specific bytes: A given codec says 'these are the tools in your toolbelt to compress data' but it never specifies which tools or the order of use. This is why JPEG has improved with better tool use. A new codecs, like a reference encoder, is functional but not the best, and over time things improve. On a per implementation basis of a given codec the bytes it emits will vary. I agree it’s not mentioned I'd be happy to add it to considerations.
The next issue was 'origin clean'

Sam W: Lets treat these as separate issues to figure out which to follow up on. Let’s go back to timing attacks.

***Concern 1: Timing Attacks***

John Kingston:  think the timing attacks could be addressed in privacy considerations.

Chris: We have to think what could be done. If your windows decoder has a pipeline depth defined, that is a decision that windows made no control over it. Could force a pipeline flush for every frame, but this would be bad for performance. It is a fingerprinting surface but there are technical reasons for it. Adding to considerations makes sense.

Let’s go to the queue.

Nick: Regarding different codec implementations producing different output, what are the variables? Chip, hardware, etc.? 

Chris: It will vary widely with some overlap. Drivers, hardware, things will vary if they were used to do encoding. Browsers build in common libs for encoding, decoding, but the version may be different in a given release. There will be some equivalence.

Regarding mobile processors, they are released in generations for a given year, with some codec acceleration facilities. They likely have the same encoder output.

Nick: We need more detail on likely differences. There might be a high granularity detection of user's hardware + software.

Chris: Yes, I agree. What information on this can we provide?

[ npdoty: maybe some basic statistical analysis would be useful, which things are likely close to unique and which are for entire classes of hardware or major browser version. and then on mitigations, can a software-implemented encoding prevent revealing those hardware-specific differences? ]

Peter: This can be discussed in Github.

Chris: this is also present in existing media recorder api. 

Jeffery Yasskin: We should be clear what surface exposure is new. Browsers already expose version numbers and timing of cpu can measure the cpu speed, but you can time js execution. This is not new. The new pieces are the choices the browser makes based on the hardware the user owns. The ability to time chips might be new, but web api can provide same timing. We should make distinctions.

Chris: I agree. There are also some new timing attacks. 

***Concern 2 Origin Clean***

Chris: The next issue on my list, we only operate on origin clean inputs on chrome. You can construct an image pixel by pixel, or use the canvas image source constructor, several things have a notion of 'origin clean.' If the provided input is not origin clean the codec should reject it. 
This was addressed in spec update.

John: Does not specifically mention [origin clean](https://html.spec.whatwg.org/multipage/canvas.html#concept-canvas-origin-clean). Only refers to the image, but the canvas could be cross origin. 

Chris: That makes sense. The spec should be updated to exclude that case.

There is a separate piece; html spec update. I believe it has done the right thing for origin clean, encourage folks to double check.

***Concern 3 Diversity by Chip***

Chris: One mitigation if concerned of exposing chips, use software fallbacks. More power, less performance. May want to not support codec to avoid exposing. Can be discussed on github issue.

***Concern 4 Memory Model***
Is this resolved in origin clean?

John: Its related. This is shared in process memory; worrying. A piece of media is in a different processor, and it must be communicated to a different processor. 

Chris: Should not have ability to make it available. ... We are considering making it asynchronous, if video frame is gpu packed causes issues. If api is async, may mitigate the buffer attack with a precise timing via array buffer. I recommend file an issue, chrome experts can respond.

***Concern 5 Demo Code***

Chris: Not clear on what was meant

John: web.dev demo is modified. draws to canvas, encodes it into a different canvas. Kept he frame the same, did a canvas fingerprint on the initial image data. These macs gave the same fingerprint until transposed through encoder/decoder. 

Chris: From encoder to decoder to new canvas, what I expect on any machine, the canvas hash will be slightly different. Are you saying between different macs, the hash on the decode canvas was different? Given the canvas source is changing rapidly, we want to be certain the source canvas image was frozen at the exact image of bitmap.

John: I hardcoded it. I removed the canvas rendering. Same source data.

Chris: vp8? on mac this is vpx software?

Peter: Is this a spec issue or an implementation question?

John: Not sure. Suggested to me something was missing from privacy section. Should highlight decoder encoder result as fingerprinting threat. We can provide code to Chris to check. 

Chris: I do expect different results in these cases. Privacy section should mention, but hardware acceleration is not used so I am surprised. I would expect this not to be the case and will take a look.

***Concern 6 Privacy Budget Impact on Capabilities***

Chris: Let’s assume we ignore privacy budget. Browsers close off hardware acceleration. Firefox has such a button, but do not always have software fallbacks. 

Sam: I want to make sure we are happy with mitigations with everything not privacy budget. Make sure looking at mitigations we can ship today.

Chris: Offering common subset of features; I would be happy to add this and ties into what I had said that for some common definition, different user agents have different abilities.

Peter: I know privacy budget is not a crisp spec or even a proposal. It is saying, you can only be recognized to a point. So, it more useable by more generic people. Discrimination concerns possibly, also targeting more for US users? Needs more clear specifications.

Chris: hardware acceleration for a given codec very common. Constantly changing. In the past media capabilities could expose a great deal. Now the specific chip will vary and make different decisions. I have no conclusion, but worth mentioning.

Peter: Agree fingerprinting is not extremely useful, but will be useful in some cases for bucketing users.

Nick: I wanted to see does the api support prompting the user, etc., or would this hang main thread?

Chris: Some apis in this path are asynchronous. To the extent that private budget can be used here, happy to replace mention of privacy budget with more clear wording on what is implied. 

Nick: Would be useful. Also, are we expecting error messages?

Chris: No, well it depends. Lets say you turn off hardware acceleration without software fallback. In this case you would query is config supported; no. But if you later attempted to query it, denied. 

Nick: would you let dev know why it didn't work?

Chris: I don't see value in saying 'didn't work because privacy or didn't work because technical issue

Nick: I thought the whole point was to expose to developers entropy issues.

Chris: I don't know what that would look like.

Nick: Might be worth talking about. Do Chrome folks who suggest privacy budget want features to be designed with error messages or asynchronous designs?

Peter: I think making them more general and not hanging on particular system that is not defined yet is a good change. Keep mitigations general.

***Concern 7 Media Capture Spec on fingerprinting***

John: I think it’s a good guide. It does handwave 'privacy budget' so please clarify. One more point I wanted to touch on. You mentioned codec registry spec, but it doesn’t exist. Its TBD. 

Chris: The registration we have so far reference back to main document. The thinking is that would be sufficient. The different codec registrations don’t change what is in the main section, even if there is a gap in the main section. Privacy impact of extensions should not be different between codecs. Would favor updating main privacy section with whatever is missing.

Agree, codec registry is full of TODOs. It does reflect state of chrome. Our plan to add more knobs for more codecs will be updated over time.

John: Interested in the configuration of the codec. How much does it impact fingerprintability of browser?

Chris: It will have some impact. For example, there is a codec has a format property that varies. They won’t differ by chip. Does impact fingerprinting if encoder does not support one format. 

Peter: going to queue

Sam: One reason for call, everyone to take a look. Everyone is welcome to file issues and put links in #privacy-reviews in Slack.

Peter: Be crisp, thoughtful, and thorough about what new information is exposed. 

Christine Runnegar: Thanks to folks for conversation, participation.

Peter: Move on to other business. Anything else?

## AOB


### [Threat Model](https://w3cping.github.io/privacy-threat-model/)

Nick: Do we have a sense of the current status of the privacy threat model and what we need to be doing next. 

Jeffrey: Welcoming PRs. More expert privacy folks need to write details of threats. Need more help.

Nick: Anything depending on it?
  
Jeffery: Would make it clear what existing threats we accept are versus those that are new.

### 

Michael Lysak: I've been trying to join PING for ~a month.  Working on something to check internal consistency of privacy proposals.

Pete: follow up on Slack? 

Michael: Thanks

Pete: Thanks for everyone!




 

