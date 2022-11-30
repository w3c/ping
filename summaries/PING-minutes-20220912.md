# Privacy Interest Group meeting, TPAC (12 September 2022)

## Attendees 

* Christine Runnegar (PING co-chair, remote)
* Sam Weiler, W3C/MIT
* Nick Doty (Center for Democracy & Technology, co-chair)
* Jeffrey Yasskin (Google Chrome)
* Artur Janc (Google Security)
* Peter Snyder (Brave Software, co-chair)
* Wendell Baker (Yahoo)
* Erik Taubeneck (Meta)
* Anssi Kostiainen (Intel, Devices and Sensors WG co-chair)
* Raphael Kubo da Costa (Intel)
* Risako Hamano (Yahoo Japan)
* Don Marti (CafeMedia)
* Johann Hofmann (Google Chrome)
* Aram Zucker-Scharff (The Washington Post)
* Michael Kleber (Google)
* Max Gendler (News Corp)
* Providence Baraka (Article 19)
* Wendy Seltzer (W3C)
* Ben Savage (Meta)
* Charlie Harrison (Google)
* Alex Turner (Google)
* Jonathan Hao (Google)
* David Dworkin (Google)
* Guillermo Movia (Article 19)
* Don Le (ARTICLE 19)
* Mariana (Google)
* Tim Huang (Mozilla)
* Ben Kelly (Google)
* Arthur Sonzogni (Google)
* Ben VanderSloot (Mozilla)
* Russell Stringham (Adobe)
* Aykut Bulut (Google)
* Chris Lemmons (Comcast)
* Yifan Luo (Google)
* Eric Mwobobia (ARTICLE 19)
* Maria Mandlis (Google)
* Sid Sahoo (Google Chrome)
*John Wilander (Apple WebKit)

Chairs: Nick Doty, Pete Snyder, Christine Runnegar

Scribe: Jeffrey Yasskin

## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/)

Nick: Introduces the meeting and the code of conduct. Follow the health rules.

Introductions around the room.

Nick: This is a bigger crowd than usual.  [Sam: 40 people in the physical room, ~16 more on Zoom]

Nick: We have a broad remit, but our main focus is horizontal review. We try to identify privacy issues to try to improve privacy. We don't have a day-long meeting, but instead we attend other meetings to start conversations. We want to know which meetings are privacy-relevant at TPAC. Identify meetings privacy people should show up to. I identified some sessions in an email. Wednesday is especially dense. Queue up to identify sessions. Artur Janc also put together [a list](https://docs.google.com/document/d/1Iq7i2Rb9MPVddrt3AgHZlpt6ttLY7QenJLkbFqlHqMc/edit).

### 2 meetings to cover over the TPAC week

a partial list of security and privacy related sessions: https://docs.google.com/document/d/1Iq7i2Rb9MPVddrt3AgHZlpt6ttLY7QenJLkbFqlHqMc/edit

Anssi: Devices and Sensors WG privacy session on Thu ~9:00am Vancouver time
https://github.com/w3c/devicesensors-wg/issues/56. We've had exceptional experience working with you. Join us.

Nick: Web Performance

John Wilander: Alex from my team will be presenting some privacy issues to that group. first and third party access to 

Pete Snyder: What time?

Eric: Thurs 9:30-10:30

Nick: We've has a long discussion with webperf, on the level of detail of performance measurements. but also opportunity to discuss analytics and reporting

Jake: 11:15 Wednesday, Multicast CG. Want to think about the privacy concerns. Some differences between multicast and unicast, and need eyeballs.

Artur Janc: Another 11:15 Wednesday session: TAO and opt-outs for public resources

Charlie Harrison: 11:30 Tuesday on WebPerf Aggregated Reporting, which is proposed solution for Timing-Allow-Origin.

Nick: Advertising meetings?

Aram: PAT CG meeting, 1:30-3:30 Tuesday. Focus is on making a group to draft a specification. Talked about requirements + stakeholders, but members want to move forward to propose something. You don't have to sign up to attend.

Michael Kleber: Outside of PATCG: Breakout, 4:30-5:30pm Wednesday on Topics API. WICG on Friday, 9:30-10:30am Ads targeting APIs, FLEDGE + PARAKEET.

Wendy: Improving Advertising BG at 8:30 Tuesday. Federated Identity CG at 10:30 Tuesday; Sam: Also today.

Eric Taubeneck: [Draft Threat model](https://github.com/patcg/docs-and-reports/blob/main/threat-model/Threat-Model-Draft-2022-08-09.md) for PATCG, in docs + reports repo.

Aram: And that's [on the schedule](https://github.com/patcg/meetings/tree/main/2022/09/13-tpac).

Maria: Friday policy protected data for untrusted components

Nick: We often do horizontal privacy reviews, but there's also substantive privacy work. Like threat models. High impact to affect specs ahead of time.

Christine: Let's agree on a place to report back. PING channel? Cryptpad? 

Nick: Chairs will find a way to do that; see mailing list.

Sam: Slack!  Email chairs or team for an invitation (but join PING first, please).

### 3 process of conducting a privacy review
  * any changes to make
  * how to open and track issues, including this week
  
  
Pete Snyder: When a group needs us to review something, they file an issue. Chairs reach out to people to volunteer. We also find a co-reviewer for people who haven't done reviews before. Then the reviewers discuss their findings on a PING call 1-2 weeks after the review was assigned. PING as a group discusses changes to propose. Those issues go in the spec's repo. W3C Team can tag issues with appropriate labels. 2 classes of issues: track and needs-resolution. Discussion happens in the spec's issues, and reviewer closes issues once they've been addressed. If people have done reviews, and it hasn't gone well or process could be approved, please speak up.
  
Nick: https://github.com/w3c/ping/blob/main/howto-conduct-a-privacy-review.md

Anssi: Thanks for the overview. Recently in Devices & Sensors, we've engaged more closely, and looped PING folks in on some PRs. Is that appropriate?

Pete: That's extremely useful. The horizontal review process isn't the only way we can get involved. We usually don't write text ourselves, and leave that to the group.

Christine: Thank you Anssi for the D&S interaction with PING.

Anssi: Maybe you should document how to do the proactive engagement approach.

Nick: Sometimes we've had luck identifying work during incubation. Can't always do it. TAG design review process is also a good time. 

Pete: Don't request a review just by mentioning a spec in the W3C's announcements channel. Open a ticket in the privacy-requests repo in order to start the formal process.

### 4 recruiting more reviewers

Christine: There's a lot of privacy expertise here. Please sign up to do privacy reviews. Do your part!

Aram: We should pair reviewers. There are people who have the expertise+time but don't know how the review process works. Or vice versa.

John: In Webkit, people self-declare expertise, and you request reviews. PING could do the same.

Nick: People could identify as having done reviews of a particular area. e.g. CSS

Pete: We've done some of that, both areas and paired reviews, but we could formalize it more. Make it better known.
  
### 5 lessons learned, guidance and mitigations
  * what to add to questionnaires etc.
  * addressing ecosystem issues
  
Nick: We've done this process for a decade, and we're trying to write down lessons. [Privacy & Security Questionnaire](https://www.w3.org/TR/security-privacy-questionnaire/). [Fingerprinting doc](https://www.w3.org/TR/fingerprinting-guidance/). Let us know where we need to improve that common guidance. EFF kicked off fingerprinting research 15 years ago. Need sustained cooperative work. Haven't made a lot of updates recently.

obituary and review of Peter Eckersley's work: https://www.wsj.com/articles/peter-eckersley-helped-encrypt-internet-traffic-to-foil-snoops-11662732014?st=lz0xgvrjfobgzvs&reflink=desktopwebshare_permalink

Pete: S&P Questionnaire: people self-assess, and then it informs the final S&P Considerations section. As spec authors, if you encounter common questions that aren't in the questionnaire or get surprised by a late concern, tell us to add them.

John: Fingerprinting: When we've been looking at fingerprintability, it's challenging to do it well, beyond just counting bits. You get uniqueness per website or per region. Should we formalize what we're looking for? We'd need to settle it before formally reasoning about it.

Nick: We've cited academic literature, where things vary by user community. We don't have particular guidance on figuring out how important something is. Mitigations are often not tied particularly to that question.

Aram: We might want to add 2 things to the questionnaire: 1) Rising concern about higher privacy standards for children. Age varies. Ask if something's more likely to affect children. 2) Developer experience: we know some things in web standards that users will consent to whose privacy risk can't be completely mitigated. Other things that aren't themselves privacy concerns but that increase the risk of privacy concerns happening. CSS: encourages users to include things that can themselves include things in a way that is not transparent to the developer that transitively create a fingerprinting risk. Actual spec isn't fingerprinting, but behavior can arise from it.

Nick: Children, and vulnerable populations. It's sometimes difficult to determine that, but we should think about vulnerability of users. This has come up around clearing data. Abusive partner.

(Text-only comment, Aram: maybe worthwhile to meet with accessibility group in the W3C to explore the idea of vulnerable audiences in general?)

Christine: Think of privacy implications for all users. Look for different types of users who can have their data exposed. Build to the highest standard for everyone.

Michael Kleber: Composability is the essence of the web. We've gotten a lot of benefit thinking about how to use Permissions Policies and other infrastructure to let developers include 3p resources without giving them as much access to the 1p page as they would have had otherwise. Bring in third parties, but don't give away the whole ballgame in terms of what's allowed.
+1 - Aram

Pete: Ways we can make reviews more predictable. We have some modes, like secure contexts get some features. We should look into other ways to make modes. Privacy/Incognito mode. Resist-fingerprinting mode. Analytics/debugging mode. 

### 6 process for follow-ups post TPAC

Sam: We have 40 people here, and a times we'll have 15 simultaneous things.  To help us track what's going on:

1) Help the group you're visiting. Assume their spec is on GitHub. File an issue in their repo. If you can, add `privacy-tracker` or `security-tracker` label, or if you don't have permission, post to [#ping on Slack](https://w3cping.slack.com/archives/CHVDPV0M7).

Aram: Do we have a more persistent place than Slack, in case Slack messages disappear?

Sam: Send to the email list: public-privacy@w3.org










