# Privacy Interest Group meeting (16 September 2021)

## Attendees (sign yourself in)

* Christine Runnegar (PING co-chair)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C/MIT)
* Dave Cramer (Invited Expert, Hachette Book Group)
* Wendy Reid (Rakuten)
* Matthew Finkel (Tor)
* Kris Chapman (Salesforce)
* Wendell Baker (Yahoo)
* Helen C (Google)
* Nick Doty
* Shivan Sahib (Brave)
* Kelda Anderson (Microsoft)
* Theodore Olsauskas-Warren (Google)
* Jeffrey Yasskin (Google Chrome)
* Joey Salazar (A19)
* Philippe de Lurand Pierre-Paul 
* Eric Mwobobia (ARTICLE19) 

Apologies: Pete Synder, Sean Harrison

Guests: Dave Cramer, Wendy Reid

Scribe: Sam

### 1. EPUB 3.3

URLs of specs: https://w3c.github.io/epub-specs/epub33/core/ and https://w3c.github.io/epub-specs/epub33/rs/

This is issue [#52](https://github.com/w3cping/privacy-request/issues/52) in the PING privacy-request repo.

Review assigned to Nick Doty. 

#### Discussion

Christine: background?

Dave Cramer: orig epub spec from 1999.  Package up a bunch of tech.  Specialized user agents use web techs to display.  XML package file behind the scenes with metadata and manifest.  Developed for 20 years outside of W3C in a group later absorbed into w3c.  Some work published as a note, but this is widely used enough that we thought it should be a Rec.  This is our first time through the process, with HR.  So it's an old spec going through process for the first time.

Nick: interesting set of specs.  I felt I could understand it.  Dave gave some useful context.  Technology has moved a bit.  Is this going to be an ongoing process or publish and done?

Dave: pretty committed to backward compatibility in epub 3.  changes tend to be editorial, edge cases, bug fixes, maybe new media types as web evolves.  Will continue to evolve after Rec, but slowly.  No major changes in functionality.  Unless there were a new ebook format that was not backward compatible.  In which case we might use more standard manifests.  

Wendy Reid: this is the backbone of the digital publishing industry.  Any change we make puts at risk many publishers, reading platforms, and users.  Very conscious of breaking changes.

Dave: we don't break the web and the don't break the ebook world.

Nick: tricky to review for privacy.  We've gotten good at reviewing new features re: browsing the web.  This is different.  You may have noticed in our self-review questions, some assume a different context.  We'll do the best we can.

I saw this as a great opportunity for privacy - rather than pulling from many sites, have a single bundle.  Reader will have less privacy concerns.  Once I dug in, though, that's not the impression I got.  Maybe I was over optimistic.  Situation seems more dire than I realized.  Big potential of modes for books where they're more like a book at the library 0- everyone has the same one, no one knows you're reading it.  But that would have to be a new profile.  Lots of remote resources.  Scripting is a capability.  In some ways less privacy protections than on the web.  Users may not be able to inspect what's happening.  Not common models.  And some security topics around origin.

Interactivity - scripting is allowed.  Scripts can do what they can in the web world - contact services, change content, accept user-generated content.  Is that right?

Dave: We've struggled with this. Most user agents don't support any of that.  or they highly restrict it.  One odd thing about epub - we've spent much time on file format and not much on UA behavior.  "here's a package of content; UA decides how to present it."  Conventions have evolved.  e.g.  Most reading systems add pagination.  - by adding markup into the content.  They control UI a lot.  They're likely to block most forms of scripting; they don't want user to change DOM.  And could destroy performance.  We don't really know what's going on.  e.g. timers in cookbooks.  Mot reading systems don't support local storage.  Huge restrictions in what could happen.  Send same file to 10 retailers; no way for publisher to get ebook to phone home - disintermediated.  

Nick: does the user know who they're communicating with?  seems like author could put in scripts so that you could know when user opens book, with what reading system, how far they are.

Dave: in general, publisher gets nothing.  Retailer gets everything.  I work for a publisher; Wendy works for a retailer.  Publisher knows when they're reading.  Publisher gets none of that unless I _buy it back from them._

Nick: because retailer can strip out resources that you put in?

Dave: or we never try, because we expect they'd be blocked.  

Nick: useful to describe who gets info. 

Dave: 1st/3rd party is weird here.  As publisher, someone else gets all the analytics.  

Nick: big issue.  not clear on how it works w/ retailer.  seems like publisher could put in resources to get data.  

Wendy: some things, while in spec, like remote resources, not used much.  e.g. because of offline reading mode.  So, while remote resources exist, they're not common.  still hosted by creator.  also have link degradation problems.  which is another reason it's not commonly used. 

Nick: are they commonly implemented by the reading system?

Wendy: I've seen in depend on the content type, e.g. media content more supported, text/file/PDF/Excel not.

Nick: If i were author of epub and wanted to know what people were doing with my book, I could figure out what resource types are supported and add them to my book.  

Wendy: yes

Nick: So, we should document that.

Wendell: in another industry, Q is who owns the info/telemetry.  What's your industry's view?  Sounds like seller/retailer for you.

Wendy: @@ user most likely uses software from retailer.  Culture of "I choose where I consume file I purchase".  Piracy common. Telemetry is lost when taken outside of ecosystem.

Nick: "lost" meaning user could read w/o being surveilled?

Wendy: yes.

Nick: want to describe in privacy considerations.  e.g. who is gathering data.  In many cases, I think user will have no idea and no capability of learning.  and it sounds like multiple layers could be getting that data?

Dave: that's fair.  Maybe much less awareness here than on web in general re: tracking cookies, etc.  People may intuit it.  We also don't have the concepts of the web - origin, visible URL.

Nick: related to that, advantage we have re: origin of web is secure transport, so you know it arrived unadulterated.  Any way to show authenticity?

Dave: in general, no.  Designed as an interchange format.  For publishers to provide materials that would then present them to end user.  Generally involves DRM; spec is deliberately silent on that.  Hooks for that.  To the best of my knowledge, publishers don't do that, but retailers may.  No mechanism for me to know that file is unadulterated.  Almost certainly adulterated.  

Nick: big area of concern is around DRM.  last night I bought a book ... it was hard to look at files.  Format is that there are rights.xml and encrypted.xml files - every content file is a binary encrypted blob.  Had to load decrypter.  As a result, user is providing PII to DRM provider.  and they're constantly surveilling user.  And a transparency problem.  User can't use open source software.

Dave: correct

Nick: so limits on transparency and control.  can't see who I'm contacting.  and additional software does tracking.

Dave: sometimes decryption code contains sensitive data - e.g. credit card #, to disincentivize sharing.

Nick: w3c has some experience with DRM and related vulnerabilities.  Common harm reduction approach - we know DRM will be used.  We could put constraints on type of identifiers, amount of data, ability to clear.  Looks like you haven't done that.

Wendy: we've avoiding discussion of that entirely.

Dave: there has been effort in epub ecosystem to develop a more open DRM system.  ISO standard.  I think is used by some epub reading systems, more in EU than American, more in library than retail.  DRM is what makes library lending of books possible.  Some social good in that, in imposing time limits.

Nick: I thought I bought a book

Dave: you bought a license.

Matt: How is telemetry collected?  The information that the retailer gains (when the file was read, how long, which page, etc.), does that come from the user agent or is that coming from the epub file?

Wendy: from the UA, not from the file itself.

Dave: nothing in the epub spec about that.  If you build a browser, you can get a lot of into about how your user is using your software.

Nick: could also construct an epub file that even w/o collab w/ retailer would reveal info.

Dave: possible to build a reading system as a website.  Could probably inherit some of HTML and CSS's fingerprintability and security issues.

Sam: You can push information back to the publisher. Documenting this is not sufficient. This is not a common use case. While wanting to prevent breaking changing, the only way to protect users is to lockdown the spec more.

Dave: The ePub is designed to be read/used offline. These documents should not contain external resources because that breaks the assumption. There could be other use cases, such as in high education.

Sam: concern that DRM hampers auditability.  If the user can't pass the file through on audit tool, you're hamstringing their ability to protect themselves.

Dave and Wendy: valid

Wendy: we lock down scripting because of these security issues.  If we let files in, it opens up....  We've made lots of decisions to not tell the UA what to do.  The reason we haven't seen it is there's lot of self-interest in being secure.

Nick: which is part of why it's good to document in the standard.  would benefit authors to tell them X doesn't work.  So people don't try to do things that aren't implemented.

Christine: next steps?

Nick: I can try to organize thoughts and send thoughts in email to WG and PING.  

Sam: was this a pre-CR review?

Dave: goal was CR in November.

Sam: you have a lot of work to do, including likely some breaking changes.  Nick, will you file a tracking issue?

Christine: thank you.

### 2. Privacy review of CSS Masking Module Level 1

URL of spec: https://www.w3.org/TR/2021/CRD-css-masking-1-20210805/

This is issue [#50](https://github.com/w3cping/privacy-request/issues/50) in PING privacy-request repo.

Review assigned to Mu Lei. 

#### Discussion

Christine: Roy did the review; this call time is a terrible time for him (given time zones).  He's been discussing the issue above with Pete.

See: https://github.com/w3cping/privacy-request/issues/50

Pete’s synopsis: "While CSS capabilities like those defined in CSS Masking Module Level 1 can be used to hide content from a site visitor, Web developers should not use these features to hide sensitive content from users or page scripts. Content that is hidden from a user's display via CSS can still be accessed and read from page scripts or form submissions. Web developers should treat the capabilities in this spec (as with all CSS specs) as cosmetic changes only, and not imposing or defending a privacy boundary."

Any comments? If you have any feedback, please provide that in the issue.

<silence>
  
Sam: Roy needs to file that as an issue or a PR with the WG.

## Upcoming reviews (to be discussed on future calls)

#### a. Secure Payment Confirmation (to be reviewed by Pranjal, Pete and Sam)

* URL of spec: https://w3c.github.io/secure-payment-confirmation/
* Link to privacy considerations: https://w3c.github.io/secure-payment-confirmation/#sctn-privacy-considerations
* Response to self-review questionnaire: https://github.com/w3c/secure-payment-confirmation/blob/main/security-privacy-questionnaire.md
* Explainer: https://github.com/w3c/secure-payment-confirmation/blob/main/explainer.md



#### b. CSS Display 3 (to be reviewed by Kris)

* URL of spec: https://www.w3.org/TR/2021/CRD-css-display-3-20210903/
What has changed since any previous review?

	• Copied over order property definition from Flexbox. (No change since last a11y review of Flexbox except some editiorial improvements.)
  
	• Copied over visibility property definition from CSS2 and expanded it to explain interactivity and a11y implications.
  
	• See full Changes list at https://www.w3.org/TR/css-display-3/#changes
  
	• See Disposition of Comments at https://drafts.csswg.org/css-display-3/issues-cr-2020
  
* Response to self-review questionnaire: https://lists.w3.org/Archives/Public/www-archive/2021Sep/0002.html

## 3. Privacy issue tracker triage

New issues #245 to #247 in our tracker (here: https://github.com/w3cping/tracking-issues/issues?q=is%3Aopen)

#247 - https://github.com/w3cping/tracking-issues/issues/247

Sam: From Secure Payment Confirmation, opened by WG, team contact flagged as "privacy tracker". Assigned to Pranjal, Pete and Sam for follow-up.
  
#246 - https://github.com/w3cping/tracking-issues/issues/246
  
Sam: relates to geolocation. WG opened issue. Trying to take to take spec to CR, PR. I was asked to review some open issues. Pete will follow-up. Assigned to Pete.
  
#245 - https://github.com/w3cping/tracking-issues/issues/245

Sam: From the personalization semantics spec. Pranjal had been involved in the review thread almost 2 years ago. Asked Pranjal to follow-up.




