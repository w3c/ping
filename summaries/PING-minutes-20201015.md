# Privacy Interest Group meeting (15 October 2020)

## Attendees 

* Christine Runnegar (PING co-chair)
* Pete Snyder (Brave, co-chair)
* Tara Whalen (Cloudflare)
* Konrad Dzwinel (DuckDuckGo)
* Sam Weiler (W3C/MIT)
* Melanie Richards (Microsoft)
* Theodore Olsauskas-Warren (Google)
* Alex Cone (IAB Tech Lab)
* Jeff Wieland (Magnite)
* Wendy Seltzer (W3C)
* James Rosewell (51Degrees)
* Jukka Ranta (Comscore)
* Kris
* Wendell Baker (Verizon Media)
* Valentino Volonghi
* Karima Boudaoud
* Jeff Jaffe (W3C)
* Brent Zundel (Evernym)
* Shaun Gilmore (Apple)
* Dave Harbage (DuckDuckGo)
* Tess O'Connor (Apple)
* Harneet Sidhanna
* Eric Portis
* Terri Oda
* Karima Boudaoud (University of Nice Cote d'Azur)
* Sean Harrison (Google)
* Paul Jensen (Google)
* vainteya

Scribe: Sam

Christine: open meeting for TPAC; we have some guests

### 1. Privacy review of WebRTC Priority Control API

* Spec: https://www.w3.org/TR/2020/WD-webrtc-priority-20200922/
* Explainer: https://github.com/w3c/webrtc-priority/blob/master/explainer.md
* Privacy considerations: https://github.com/w3c/webrtc-priority/blob/master/security-privacy-questionnaire.md
* Repo: https://github.com/w3c/webrtc-priority

Pete: I did this review.  WebRTC extension, say e.g. 'this stream is high priority - drop bits elsewhere'.  No capabilities revealed.  No issues.  This one was easy.  

### 2. Privacy review of CSS Conditional 3

* Spec: https://drafts.csswg.org/css-conditional-3/
* Privacy and security considerations: https://drafts.csswg.org/css-conditional-3/#priv-sec
* Answers to the Self-Review Questionnaire: Security and Privacy: w3c/csswg-drafts#5567
* Changes since 2013 CR: https://drafts.csswg.org/css-conditional-3/#change

Pete: Jeffrey did this review; he's not here.  Revisit this in two weeks.

### 3. Privacy review of CSS Text Module Level 3

* Spec: https://www.w3.org/TR/css-text-3/
* Privacy and security considerations: https://www.w3.org/TR/css-text-3/#priv-sec
* Answers to Self-review: security and privacy questionnaire: https://lists.w3.org/Archives/Public/public-privacy/2020OctDec/0004.html

Konrad: Dave and I did this review.  Covers line breaking, est transformation, alignment, etc.  does not cover fonts.  current rec is 2.1.  ten new properties.  four properties have new values available.  many of these already out there e.g. wordbreak. spec leaves many details to UA.  examples: "The UA may enable or break optional ligatures or use other font features such as alternate glyphs or glyph compression to help justify the text under any method. This behavior is not controlled by this level of CSS. "  "CSS Text Level 3 does not define the exact rules for hyphenation; however UAs are strongly encouraged to optimize their choice of break points and to choose language-appropriate hyphenation points."  "The guidelines in this level of CSS do not describe a complete justification algorithm. They are merely a minimum set of requirements that a complete algorithm should meet."

Privacy concerns appear from details left to UA.  Can probably already ID UA in other ways, so I'm not concerned. 

A lot of those details are covered by dictionaries (e.g. word breaking).  Those rules can be complicated and vary by language.  Concern is that a site can figure out which dictionaries are installed.  We don't fully understand these.  If all browsers using same, it's fine.  If it varies, it's a problem.  but having e.g. German and Chinese might be unique.  Any spec editors here?  

Tess: were the CSS text modules editors invited?

Pete: not specifically.  we don't normally do that (anymore) - took much time.  Instead we schedule calls after the fact if needed.

Pete: thank you Konrad.  Does spec anticipate cases where dictionaries don't match installed languages?  if they match, less concerned.  

Konrad: I'm wondering that also.  I'll ask authors.

Pete: You focused on things new to this revision.  Any issues that we need to pay attention to from previous versions?  

Konrad: we went for the whole thing.  We focused on the diff.  diff useful for reviewers to focus attention, but we looked at whole thing.

Pete: thank you again.

Konrad: ….

Sam: when you add the question to Github, can you mention the new issues in slack?

Konrad: the whole review, or just the new issues?

Sam: just the issues

Konrad: sounds good

Konrad: are we concerned about features that reveal browser and version?

Pete: We haven't historically been that concerned because it's advertised in UA string.  IF we get to a rosier world...  We might be able to roll that into future work.  Non-zero concern, but could be bigger in future

Sam: Concerned about how painful it would be to mitigate that in the future? examples from other domains saying, "we don't have to worry about X now because it's already leaked in Y" but then we fix Y.  We have seen cases of people fixing those other leaks, which then raises the question of how hard it is to mitigate X's leak. Does that make sense?

Konrad: it would be difficult to specify this intensely, but we should be concerned with browser version fingerprinting in general, where possible

Sam: Do you have a sense of how difficult it would be to address this in the future?

Konrad: very

James Rosewell: I think I heard is that how individual browser implements ….. .  Other things from other SDOs.  Opens the Q of "what's the baseline we're working to?"  Could become unwieldy.  is that baseline being documented anywhere?

Pete: we don't have a 'ten commandments of web privacy', but we have guidelines.  We'll explore this more on Friday.  No crisp answer. But, being worked on in several docs: threat model, self-review questionnaire; other TAG docs (web principles doc).  

James: So, they some base guidance, but it isn't a line?

Pete: this is a mix of process and thoughts of individuals doing review and thoughts of group.  increasingly principles we aim.

James: seems like a lot of docs to view to learn how to do a privacy review.

Christine: please pass on invite to Friday session.  PING didn't exist in early years - we came along while ship was in motion.  we've been tasked to make the Web more privacy protecting.  Incremental progress and ongoing journey.  As we do more reviews, specs are changing, e.g. new sensors.  Field evolves, we find new things.

Sam: seconding Christine, the field is evolving, and research is identifying new threats too.  So, the field is changing too.  Re # of docs, there are many docs everywhere, it’s the pit stop to bottom :)

Jukka: if you take this to extreme, any behavior different from other devices is a risk.  doesn't that take us to world of no progress, lowest common denominator?

Pete: closing q, since we're going far afield from CSS text module items.  Let's put them in another agenda item.  But good concerns.  More comments on this review?  Thanks again to Konrad.

### 4. Adding permissions

* https://www.w3.org/blog/2019/07/adding-another-permission/

Pete: Nick did this.

Tess: fall 2018 w/s on permissions and user consent.  Great workshop.  One of the artifacts were these notes from Nick on Q of "when adding a feature that you think needs a permission, what do you need to think through"?  This was published as a ping blog post.  this is still the best resource re: adding a permission to the web platform.  Comes up in TAG reviews.  In TAG hat, we think this is great, and we want to be able to cite it.  Two ideas: integrate it into design principles doc. Or, separate PING note.

with no TAG hat, I think #2 makes more sense.  PING should own this.  Does group agree to take this up and that it should be maintained?  (Separate or combined.)  I want to be able to cite this going forward.

Christine: Nick is unable to be here today.  I agree - this is a good idea.  No preference re: separate or in questionnaire or elsewhere.

Pete: +1.  Happy to spend time on this.  What format would be most useful?  My understanding of IG Note is that it's not official.

Tess: but it's in TR space.  Guarantees around lifetime, longevity of URL.  That's the main thing.

Pete: explain TR space.

Tess: [done]

Jeff: thanks Tess for raising the question and Nick, in absentia, for writing this.  Aside from blog post asking Q, does this group thinks formal spec work needs to be done, or already underway?

Tess: permissions API work ongoing.  Some features asked for permissions before that API existed.  

Pete: Jeffrey was working on additional docs.

James: when we look at permissions, important to look at default bias.  e.g. when installing Windows, it asks 5 questions.  on wbe, I get annoyed at pop-up asking for notification permissions and location permissions - I want to be able to set default.  Important to not overload users w/ permissions prompts - see that on GDPR consent.  Should consider default bias.

Tess: excellent point.  That was well taken into account by designers of permissions API.  allows for defaults.  doesn't specify browser UI, but architecture allows different approaches.

Pete: I'll talk to Nick.  

Tess: one option is to integrate it in questionnaire - that's not terrible - it's a reasonable home - but I'm a little worried re: length of questionnaire.  We want that doc to be easily digestible.  If we add more text, we run risk of people glossing over it.  long enough on its own... it might be too big.

Pete: since we frame questionnaire as entry point, maybe point to it.

Christine: I think we should write it up as group note, and point to it from questionnaire.

sam: i) should we also do whatever we do with this, do to the fingerprinting doc
     ii) let’s put them in as appendices in the security + privacy questionnaire
     
...: putting them in a joint PING+TAG doc might cause previous editorial battles.  James, are more shorter docs, or fewer longer docs, easier?

Christine: can we do both?  Separate and appendix? (effectively incorporate group note in questionnaire)

Sam: worried about sync.  Let's focus on having a set of docs and make them work together well and easy to find.

Jeff Jaffe: in web accessibility, in W3C, we have branded ourselves as the place to come to, to find a set of docs.  Maybe we can aspire to do similar thing for Web privacy. think of idea of doing that - to raise flag as the go-to place to find this.

### AOB

James: Jukka's point re; conformity of browsers.  

Pete: warrants more time and good to have a different audience than this call re: implications of three specs.

Jukka: good for this WG (sic) to have forum for people who aren't regularly part of group to participate.  I thought we'd be doing that in this TPAC session.

Pete: worth thinking through these things.  PING has narrow focus.  largely these biweekly calls are us reviewing specs.  

Jeff: TPAC breakouts in 2 weeks - could propose one for there.  

James: I've proposed 3 or 4; someone else?  [silence.] I'll give it a go.

Sam: just remember there are only 5 slots...

Wendy: For people not regularly here, encourage to join in the future.  where to see agenda for future items?

Christine: we do a lot of technical work, ... Pete made it sound boring, but it's interesting.  There is an open invitation to join us.  Otherwise send chairs email w/ ideas.  Also thanks to WebRTC for inviting us to their mtg immediately before this.  Made good progress with them.

Pete: good conversations with Payments, WebXR recently.  Should give updates soon.
