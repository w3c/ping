# Privacy Interest Group meeting - 6 June 2019

## Agenda:

1. Privacy considerations of:

	* Web of Things (WoT) description - https://www.w3.org/TR/2019/CR-wot-thing-description-20190516/
	* Web of Things (WoT) architecture - https://www.w3.org/TR/2019/CR-wot-architecture-20190516/

(carried forward from the May meeting)

2. Privacy consideration of Data Catalog Vocabulary (DCAT), draft version 2

	* https://www.w3.org/TR/2019/WD-vocab-dcat-2-20190528/ 
	* https://www.w3.org/TR/vocab-dcat-2/

Peter Winstanley, chair of the W3C Dataset Exchange Working Group will be joining us to provide an overview of the spec

3. Pete’s draft blog post on privacy anti-patterns in standards and next steps

	* https://github.com/w3cping/blog-posts/blob/master/privacy-anti-patterns.md


4. AOB

## Attendees

* Peter Winstanley
* Sam Weiler
* Christine
* Tara
* David Singer
* Tom Lowenthal
* Mike O'Neill
* Craig Spiezle
* Wendy Seltzer
* James Fishback
* Nat
* Jason Novak
* Pranjal Jumde
* Peter Snyder
* Pranjal Jain

## Introductions

Peter: I'm the chair of the W3C Dataset Exchange Working Group WG.  I'm here because we're asking for wide review of DCAT.

David Singer: I lead the standards group at Apple.  Joined today because I saw in Slack that I should.

James: I'm at WikiMedia Foundation, new to W3C.  I'm a privacy engineer.


## Data Catalog Vocabulary (DCAT), draft version 2

Peter: Requirement to publish data catlogs on the web - comes from work in Ireland - developed into W3C standards in 2014 - at the same time, work in European Commission related to the publication of public sector information and other open data recognised needs for data vocab + other things - made an application profile (DCAT-AP)

other countries in EU realised that European community output not enough - made own application profiles - various domains found not appropriate, e.g. statistical profile and geospatial people needs for date services so they modifications (StatDCAT, GeoDCAT)

led to a large number of different modifications - standard in practice, it needed tweaks

the work of the WG was brought about to update the data catloging vocab from 2014 form and the people involved in it had experience with semantic sensor network ontology as well - a lot of merit in creating a more flexible form with less rigorous axiomisation for use in wide range of uses of model

model 2 - two sorts of areas of work - lessons learned from operational work - e.g. including services as well as downloadable data sets in the model -express in different referential forms + use properties in different parts of the model (e.g. key word properties used for different components)

working on for a couple of years - versioning and other pieces will come forward in version 3 and subseq - W3C move to evergreen standards, opportunity for uptake from interest and community groups

getting to stage for enough for significant improvement

not sure where the privacy interest group focus might lie, but when describe data sets, points at which we identify individuals or agents (e.g. who is publisher, or funder, or ...) origins for support for creation of a particular data set - push for this from academic community (desirable to have prominance being known as maintainer of a particular dataset, or came from funding from specific grounds)

notice Orcids by the editors on standard in addition to name indicates that people are interested in being recognised in their work

different things are going on - prominance rather than privacy

welcome your review - in case we missed something

want his degree of discoverability of data sets + link in machine-reable form different data

Mike ONeill: Some people might not want their names posted.  Any consent capability?

Peter: deal with this in application profile, not in vocabulary for data set cataloging.  because of flexibility of the model, the creation of application profiles will be more prevalent. Publisher of info provides filter

Mike: any centralized facility re: user conent?

Peter: You might want to make that comment to group.  maybe provide a methodology.  e.g. a guidance note for implementors

Christine: imagine that data sets might contain personal data or data that is at risk

Peter: People can describe in full ways what might be possible - in the model - in the additional metadata from this catelog - look within vocab at example 33 - quality, etc. can be provided, such as data usage vocabulary - can also be added to the catalog

Christine: could the group offer guidance that users of the model should flag privacy and conditions with use?

Peter: aspiration is to write a primer which would include these good practice guidance - that is the appropriate place for that information - it would be helpful to have input on that type of doc

Peter: would like your comments on the specification on the public comments mailing list please ( public-dxwg-comments@w3.org )

Tom: where is background on data spec - why is this at W3C rather than some other SDO?

Christine: Peter can answer that better; he didn't address that specific question.  Will put Tom in touch with Peter
Peter: replying to Tom. this is a data catalog vocabulary, but it is about interoperability of data catalogues published on the web - that is why it is W3C and not another standards development org.


## Blog post on anti-patterns

 https://github.com/w3cping/blog-posts/blob/master/privacy-anti-patterns.md

Pete: recap: describes three anti-pattern: locally-useful stuff being made available globally, privacy considerations section often vague.

Christine: nice piece; thank you Pete; may use this as the start of a series.  ANy concerns about Pete or PING posting this?

Sam: would be on W3C blog - propose under Pete's name (if okay with Pete) - therefore does not need PING approval

Jason: spec speaks about global availability of features (e.g. first and third) - global availability might have different meanings to different audiences - maybe treat all parties equivalently

Pete: happy to work on that.  

Jason: I'll file PR.

Tom: re: publishing under Pete's name.  If this represents PING's rough consensus, I'd like to to be Pete speaking for PING - representing group's view.

Sam: fine with that.  everyone in agreement?

Mike: yes.

David: great doc.  I don't think a blog post is a good place to put it.  needs to be on GH in PING space or wiki so that others can offer improvements.  I push back on publication path.  Great advice.

Christine: sounds like you think this should be a group note.

David: yes.  @@

Christine: i'm leaning toward this being a group note ultimately, what do you think Sam?

Sam: we need to build awarness across W3c. We need more publicity.  Which is hy we targetted blog post.  Waiting for a group note THEN blog post defeats that.

David: I'm fine with blog post first

Mike: I agree with Sam

Pete: this will have more force coming from PING than just me.  this is a line in the sand - the new set of standards we expect docs will meet.

Christine: we have consensus that it's a great post.  we want it out as PING's thinking.  we have consensus that it is another step in the process.... David's AC pitch ... we could turn it into official guidance later.  Any problems?  [silence]  Part 2: Pete's list in slack channel.  to improve existing standards.

Pete: to improve existing specs.  Sequence it as "blog post" then chane to CSS standard to bring it into line.  proposal: repsond with a list; any other font needs to be included in page.  

Christine: do we all agree that that's the right approach (ignore process) re: font enum? 

Pete: details are in fotn enum channel in slack.

Christine: hearing no disagreement.  Process: we'll sort it on slack channel then move to email.

Pete: another item was how to move "privacy mitigations must be mandatory" into process.  David?

David: process CG discussed making privacy consideration section mandatory.  It will be more effective if team and AC refuse to approve docs.  ... Making it mandatory results in boilerplate; it passes automated check.  We'll do better with culture than rule.

Christine: I may have misunderstood ... I thought you wanted mitigations tobe mandatory, not the text section?

Pete: right now the sections read like boilerplate..  laudnry list of "we goofed here" is not good enough. 

Sam: there is a cultural problem.  Docs are getting through with issues.   e.g. High Resolution Time has put in a transition request for PR without addressing a concern that I put it - also Web of Things group - someone said we always published CR, are you going to find big changes?  We have a cultural problem with the director letting docs through - maybe changing the process will help give the director cover to block docs.

David: I'm not opposed to a change in the rules, but I think changing culture will drive change in rules

Tom: For any type of privacy oversight to be effective, it must be sufficient for this group to object and articulate a specific problem. That has to be enough for the director to block a standard.  If it's anything more complex than that, it will always be an edge case judgement and PING will generally lose any complex political process. PING represents a wide diffuse constituency (people who want to maintain their privacy), while spec authors are a narrow and focused constiuency: they want to get their specific use case working. We have a small number of engaged people to are trying to deal with privacy issues across all standards, and we have a responsilibity to uphold this common privacy need.  The amount of labor required for us to do this across every standard is quite substantial. Increasing the workload for this group so that we not only have to identify these issues but then fight for them over and over for each standard is a most unfortunate dynamic. And it will mostly lead to the wasted effort of us reading and analyzing and finding the privacy issues and then spec authors publishing their standards anyway. That's not oversight, and it's not useful.

Jason: I'll f/u w/ Pete re: blog post in GH.

Christine: let's keep thinking aout how to deal with cultural problem in scalable way.  encourage new people.  Next call?

David: at AC meeting, about six hands went up re: will send new people.  We need to f/u w/ AC.

Christine: yes. Tara will reach out. Also good if David could use his influence

Pete: calendaring on slack?

Christine: we will sort out next call on Slack











