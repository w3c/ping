Privacy IG (PING) minutes, 16 May 2019

Present (sign yourself in)
* Tara
* Christine
* npdoty
* pes
* Brent
* wseltzer
* pranjal

Scribe: Brent

Agenda



### 1. Web of Things and privacy

  Web of Things (WoT) Thing Description:
  https://www.w3.org/TR/2019/CR-wot-thing-description-20190516/

  Web of Things (WoT) Architecture:
  https://www.w3.org/TR/2019/CR-wot-architecture-20190516/
  
  Web of Things (WoT) Security and Privacy Considerations
  https://w3c.github.io/wot-security/
  
### 2. Improving Web privacy - next steps

#### 2.1. Font enumeration limiting

#### 2.2. Process proposal for normative mitigtions

### 3. Any other business (AOB)

### Discussion

#### Topic: Normative Privacy Mitigations
Pete: Privacy mitigations need to be in normative text.
Currently, often only non-normative text appears in specifications.
Not sure where to go with the standards proposal, does this seem appealing?
Does anyone have a template?

Wendy: I will add a link to the Process Group. Like spec text, we are drafting the process through github issues.
https://github.com/w3c/w3process/
If you have specific text to propose, put it there.
(note a related issue: https://github.com/w3c/w3process/issues/264, requiring horizontal review at FPWD)

Pete: does the substance of the proposal sound interesting?

Christine: I think it has merit. One of the challenges, is when mitigations should be normative or not.
At some times it may be clear, but other times making it normative may cause problems.
Apart from going to the process group, we probably want the TAG to add this to the Security and Privacy questionaire

Sam: I don't know how making that a hard requirement will fly.

Nick: I like the general idea of getting more affirmative requirements. We hesitated before because it is not good to add hard requirements without sufficient guidance. Maybe we've gotten to the point where we can put the S&P questionaire more firmly forward.
I don't know about saying the text needs to be normative would mean. The best case would be for the design of features to include privacy considerations from the outset.
Don't know how we want to frame that the privacy sections are normative.

Pete: Point taken. Coming from the implementers side, non-normative text is effectively not useful. The takeaway is someone adding it to a privacy section, which is essentially a blog post. This doesn't actually help privacy.

Mike: maybe a template of what the text would look like
Nic

Nick: with you on that that if a feature needs a design change for privacy, then non-normative text doesn't help.

Brent: Issue for specifications that are data models.

Mike: template includes a list of new privacy risks that the spec introduces

Pete: maybe we need some examples of when non-normative text is actually useful in the privacy considerations section

Sam: There is a lot of good advisory stuff that doesn't need to be normative. Nothing concrete to show right now

Christine: I don't think we are in disagreement. There are some cases where privacy mitigations need to be normative because we need the spec editors to change the API. In other cases, non-normative guidance may be sufficient. The tricky part is figuring out when the normative text should be there.

Mike:I think privacy needs to raised in importance. i.e. specs should not introduce new privacy risks, unless specific mitigations are specified


Pete: That is useful, but may be confusing. Maybe we could provide guideline where we would expect normative text?

Christine: I think you are right

Nick: We also need to look at a good example of a non-normative privacy considerations section.
Some implementers look at the privacy considerations section as a summary of different things spread through the spec that may or may not be normative

Sam: the real concern is giving implementers rope with which to do bad things. The point is we need to make the mitigations mandatory.  This is not about a particular section of the document. We need to say that a particular mitigation is mandatory. I think we should spin this with different language. Does that make sense?

Pete: Yes. The use case here is where there is one implementer with a loose view of privacy, another with an indifferent view. I think we can push more on those who are indifferent.

Sam: We want to make the mitigations mandatory. I don't know where this fits. this isn't process as much as principles. Where

Mike: +1 for mandatory
Brent: +1 for mandatory
(npdoty: +1, and this is more clear than what I had been interpreting the proposal as before, regarding the text of the privacy/security considerations section)

Same: Where should that lie in order to be respected.

Wendy: Either in the process, or in a charter making reference to the exit criteria of the spec. I don't think process is a bad place for directing the director to look. Then it can be raised in review, and block transition if reviewers aren't satisfied that a mitigation wasn't mandatory.

Sam: Making sure that the mitigations for privacy are by default not optional.

Pete: The goal here is to keep the P&S section from being a hairshirt, but that they are actually useful

Christine: not sure if this is for the process group or not. It is certainly for us as we give reviews. Should something be added to the S&P questionaire to say that these things are mandatory

Sam: It was suggested to make a blog post about the shift from "not making things worse" to "actually doing things as badly as everyone else is a problem" We need to be public about what we are doing and why. Perhaps we need to write these things up ourselves. And sell this more broadly. Is that more reasonable than going straight into the process block?

Pete: I'm skeptical if that will be useful, but I'm willing to try.

Nick: To Sam's point: that may be a good explanatory argument, which would makje it easier to push the procedural changes. We have a thread of bigger ideas, not doing this as bad as everyone else. We need to keep thinking about how to explain those things, so we can be better than the status quo

Pete: Talk at WWW, happy to morph that into a blog, talk about privacy anti-patterns. I'll dump that in the slack

Sam: I would love to see that.
(npdoty: +1)
Brent: +1

Christine: I think we have a way forward, we can continue in slack and on the next call. If people are ready, perhaps we can move to font enumeration

#### Topic Font Enumeration
Pete: how can we fix currrent standards to be better? Start with font enumeration fingerprinting.
Two different docuemnts in web standards handle fonts: CSS and WebGL.
It should be easy to introduce text to the font selection algorithm in the CSS spec to limit the fonts a browser looks for to the defualt fonts shipped.
The goal is not to have multiple vendors mitigate in their own way, but to standardize the mitigation.

Nick: It seems like getting the exact text right may be pretty tricky. Not sure how we would specify the default fonts in the spec.

Pete: I know safari does it, brave does not, chrome does not, not sure about edge

Nick: there are bugs reported in bugzilla about Firefox, not sure if its implemented yet.
https://bugzilla.mozilla.org/show_bug.cgi?id=1336208

Pete: Is your sense that this is more or less necessary?

Nick: not sure about necessity, but it could be useful.
Mike: +1 for useful

Christine: Sounds like there is interest in pursuing this, but may not be exactly sure the language we want to see. does it make sense to scrum in slack and see, with a channel just for this discussion.

Pete: that would be great, haven't written spec text before

Christine: lets do that. Then others can join, we can make a decision and move on.
Next topic could be WOT spec which just went to CR. Appreciate people may not be fully ready to talk about this now. The other topic, what is the next step for PING work beyond the individual privacy reviews of specifications as they come up.
It seems we have two concurrent objectives: 1) very discrete conecrete things we can wrok on now to improve things. 2) Other is big ping ideas. I think we need to continue along both tracks. Propose multiple slack channels. One for big ideas, then a temporary channel for each specific thing that comes up.
Does that sound sensible?

Brent: +1

Nick: slack may be low traffic enough that we may not need separate channels, or only for longer discussions.

Christine: we will exercise our discretion as chairs.
WOT today or move to next call?

Mike: I would like to hear about the Thing ID what are situations it is visble


Pete: my intitial feedback, there ought to be a guiding principles section to frame the rest of the considerations.

Sam: sonds like we give them that feedback. do we need to do more right now?

Christine: should we take a closer look at their Security and Privacy considerations section?

Pete: I didn't mean a principles section as much as a privacy requirements section.

Sam: I think you're right, we should have alonger one about that document. I say we punt until next time.

Christine: We should be seeing privacy in the requirements section, not only in its own section.
To your comment in zoom, Nick. There are a lot of documents. I will try to send out a roadmap of what to look at where.
Anything else to cover today?

Nick: Is there an explainer doc for the WOT spec? I would benefit from an overview. Especially for a longer spec.

Christine: we can always invite someone from the group to join the call. in advanbce of that we can ask them for a brief docuemtn that gives a summary in advance of them coming.

Pete: This privacy considerations sections has all the hallmarks of not being useful. I.e., PII should be stored as minimally as possible. Tha punts everything to implementations.

Nick: You're tlaking about this high-level abstract thing that isn't implementable. I wonder if this is because the spec is high level.

Pete: then what are the ACs voting on?

Nick: I gueass what I'm saying is that I agree, we need something more concrete.

Mike: yes i have

Mike: agree weak but at least its a start. I like the selfdeclaration aspect



#### Topic: Any other business
Nick: Has anyone looked at the google announcement about cookies?

Pete: pretty weak sauce. Doesn't put limits on what third party's can opt into. it adds 7 characters to the 

npdoty: so it's about the defaults rather than the capability.
here's the I-D under discussion: https://tools.ietf.org/html/draft-west-cookie-incrementalism-00

Bennet: other part that is interesting: they are going to clamp down on fingerprinting. What does that mean?

Pete: I don't know.

Christine: Any other business?

### Scheduling

Sam: Any conflicts to avoid for the next call?

Mike: id rather next meeting wasnt on 30th may

Sam: chairs and I will come up with something

