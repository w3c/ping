# Privacy Interest Group meeting (6 January 2022)

## Attendees (sign yourself in)

* Christine Runnegar (PING co-chair)
* Sam Weiler (W3C/MIT)
* Pete Synder (Brave, PING co-chair)
* Nick Doty (CDT, co-chair)
* Sanketh Menda (N/A)
* Katharina Koerner (IAPP)
* Wendell Baker (Yahoo)
* Matt Liu (The Washington Post)
* Aram Zucker-Scharff (The Washington Post)
* Jeffrey Yasskin (Google Chrome)
* Ted Thibodeau (OpenLink Software)
* Eric Mwobobia (ARTICLE19) 
* Shivan Sahib (Brave)
* Brent Zundel
* Wendy Seltzer (W3C)

Scribe: Sanketh

Code of Ethics and Professional Conduct: https://www.w3.org/Consortium/cepc/

## 1. Privacy review of IMSC Hypothetical Render Model

Spec: https://www.w3.org/TR/imsc-hrm/

Background: The WG has conducted a self-review of spec IMSC-HRM (ED), and the results can be found at https://github.com/w3c/imsc-hrm/issues/19. 

- Review by Pete Synder.
- This document describes how sites render text captions along with video
- Not many unique threats.
- At a meta level, the rendering model is both well-defined in terms of data, and ill-defined in terms of 
- There were some policy issues, typos, and other nitpicks.
- Otherwise, there are three high-level substantive points.
- There is a privacy and security considerations section, but it includes inaccuracies like it saying that "No information is exposed by the algorithm to any origin" but that doesn't account for side-channels like time to load fonts, etc.
- The other subtantiative point is that the spec is vague and has statements like "Implementers of this specification should capture and meet privacy and security requirements for their intended application." Some of that is unavoidable since this API may be implemented outside browsers. But we have worked with WGs in the past to have defined privacy functionality when being implemented inside browsers.
- The third point is that the spec does not have an error model; how pages react to the error seems undefined. It would be nice to be have this be defined in the spec.

- [added later by Pete Snyder] the following issues were filed as part of this review:
  - [Typos, formatting, and clarity suggestions](https://github.com/w3c/imsc-hrm/issues/28)
  - [Define the error model](https://github.com/w3c/imsc-hrm/issues/29)
  - [Privacy and Security section over claims (I think origins can use this functionality to learn about the system)](https://github.com/w3c/imsc-hrm/issues/30)
  - [Spec needs to define interaction with the web platform](https://github.com/w3c/imsc-hrm/issues/31)

- Sam: This is an error in self-analysis [...]
- Pete: Self-questionnaire [...]
- Sam: How tricky was it to identify the issues.
- Pete: It was very confusing because the citations were to large specifications rather than specific documents.

- Aram: The Sync Document also seems to have similar functionality, does that also have similar issues?
- Pete: This was another confusing point with some portions being ill-defined.
- Aram: Not cited here, but there are standards in ad-tech for companion video, this may be a good drop-in replacement there.
  - https://www.iab.com/wp-content/uploads/2015/06/VPAID_2_0_Final_04-10-2012.pdf
  - https://iabtechlab.com/wp-content/uploads/2019/06/VAST_4.2_final_june26.pdf
  - https://iabtechlab.com/standards/vast/
- Pete: It is possible that this system is compatible with similar systems. This however seems like an alternative system.

- Nick: I did a review of a different spec in the IMSC area and we had similar issues with external resource loading allowing tracking of users. That could be a general issue with IMSC.
- Aram: That is a common issue with these tracking pixels.

- Jeffrey: The ability to track users' reading/viewing progress versus saving bandwidth by loading incrementally seems like a tension we should consider, it appears in multiple places
- Nick: It seems like these issues should at least be raised and there may be other functionality that may be worth the tradeoff.

- Christine: Thank you for rasing that tension. It is importantt to be mindful of tradeoffs. Perhaps not this group for developing the balance. This group is focused on privacy, and others groups may be more suited to the balancing of interests.
- Nick: Makes sense.

- Aram: Consent is also a useful signal. This doc does not include consent mechanisms: if there are privacy considerations having a consent step at the beginning may be worthwhile.
- Jeffrey: The users may prefer User Agents that are configured one way or another, loading all at once or incrementally, and the spec should point out that it's possible for UAs to vary on this point.
- Pete: The iternative font transfer comes up, it was a good example of being able to well tradeoff the privacy and functionality considerations.

- Nick: We also want to build a body of general considerations that we can reuse in other reviews. It seems like incremental loading is one of them, caching/timing attacks is another. Are those documented elsewhere so the group can be consisent?
- Pete: The privacy self-questionnaire talks about it but we (Pete and Tess) and working on making it more precise.

- Nick: In terms of action items, it seems like Pete and Sam will open issues in the IMSC github, and link them to PING so we can track them.

- Christine: Going back to Nick's point about generalizing this experience. Pete, do we have general guidance on incremental loading?
- Pete: The privacy self-questionnaire has text on it, but it is tricky here because this spec is designed for browsers and not-browsers.
- Christine: We are increasingly seeing specs that are designed for both, so it may be worth having a section on them.
- Pete: That is a great idea.

- Nick: We'll close this Zoom call then and move to the issue triage.
- Pete: The reason we are switching is because we don't typically use this call for triage.

- Nick: The next Privacy CG call is at a different time.
- Sam: 7pm ET.

- Nick: Thanks everyone for coming, PING will meet again in two weeks.

## AOB

Meeting again in 2 weeks. Next week's Privacy CG is meeting at an Asia/Pacific-friendly time (evening US Eastern).

## Issue Triage

Separate Zoom call for working through tracking issues: https://mit.zoom.us/j/98784170796?pwd=dnIreEw2blJrcFkzdURPSlBvcVpEUT09

Several of us worked through the maybe-ready-to-close backlog of tracking issues and closed many.

We can try to keep an eye on newly created privacy-tracker issues, and remove the "pending" label once they are triaged (e.g. if it was one opened by our review process, or if it was a new issue that needed our attention and we assigned it to someone).

