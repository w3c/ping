# Privacy Interest Group meeting - 07 November 2019


## Attendees (sign yourself in)

* Anthony Nadalin
* Brad Lassey
* Brent Zundel
* David Harbage
* Erik Anderson
* Jeffrey Yasskin
* Melanie Richards
* Michael Kleber
* Pete Snyder (co-chair)
* Pranjal
* Sam Weiler
* Scott Low
* Tanvi Vyas
* Tara Whalen (co-chair)
* Theresa O'Connor
* Wendy Seltzer 

## Minutes:

scribe: kleber

### Outstanding privacy reviews

Pete: It's important to have multiple people invovled in these reviews to get a breadth of experience.  Please talk to Pete and volunteer to be involved.

#### TTML review, by jyasskin
* https://docs.google.com/document/d/1115LZYzMXc9ZwOA8mjePtk3Bb4ID3AOk0n8_Q4tMrw4/edit#heading=h.7zy3ua9hwhc
* jyasskin: Nobody implementing this in a browser, so not as relevant for user-agent-focused folks
... PII like Names of scribes might appear
... There might be a fingerprinting surface if clock is used directly as part of automated annotation
... Web sockets should maybe use the secure versions, wss
... What are next steps?
* pete: Open github issues for anything relevant, otherwise all done unless there is anything PING ought to object to
* jyasskind: inclined to email their mailing list first, in case there is an opportunity to clear up any misunderstandings, then convert to issues afterwards
* erik anderson: Note that IE/Edge implemented a limited version of this, so it does have _some_ user agent relevance

#### Fingerprinting via device sensors API
* Pete: paper documenting fingerprinting via accelerometer on devices with high-precision sensors
... Proposed mitigations invovling putting permission behind a prompt
... device fingerprinting attack could be addressed by adding noise.  Working group is receptive to capping resolution on sensors, but is looking for guidance to help understand usability-privacy trade-off.  Original reserarchers not available to do the work themselves
* jyasskind: from reading the paper, looks like the sensor has much less precision than the values that are being reported out by the API, and that's what makes it easy to pick apart the sensor reading from the calibration adjustment.  Could fuzz within the range of the original sensor.
* Pete: That is the mitigation Apple deployed in Safari.  But would be easier if we could just do it by capping resolution.
... Q: Has Google looked at this?
* Brad: Google has looked at both capping resolution and noise in other instances, and found noise too destructive of utility.  But we haven't looked at this case yet.  No firm date on when we will look at this; may have update by next PING call.
* Pete: Group has been extremely receptive to the PING feedback.

#### Upcoming reviews:
* Intersection Observer
* Verifiable Claims

Pete: Looking for reviewers.  Please volunteer.  Time frame: Next two weeks

* Anthony Nadlin -- able to do Verifiable Claims, with help from Pete.  Will coordinate over email

Pete: Expect more cases where we will need volunteers

* Brent Zundel -- will sit and watch Pete do the Intersection Observer review, hope to be able to do reviews in the future


### Updates on WebRTC and font fingerprinting conversations

#### WebRTC
* Pete: Risk: Hardware identifiers exposed via API.  Group is receptive to putting the API behind a prompt.  Pete's ask: reveal only the device labels for devices that the user has granted access to, not giving out all labels.  In progress

#### Font fingerprinting / CSS
* Pete: In progress, getting small groups together to coordinate, let Pete know if you want to be invovled.

### Call for next FP surface to tackle

* Pete: Ongoing project to find backlog of fingperinring surface in the platform that can be addressed in ways that are less controversial.  Open to suggestions
... Mozilla folks have done some great work on enumerating all fingerprinting surfaces
* jyasskind: Is there any reasearch on what surfaces are actually being used in the wild?  (Rather than just asking what exists in the platform)
* Pete: Will add links to papers that might be useful
* Sam Weiler: Arvind Narayanan might have some research about FP in the wild. I suggest tackling the largest number of bits, even if they are not being used right now, since fingerprinters can move around.
* Pete: Would like easy wins too.  A small number of big wins are great, but a large number of small wins are good too, may be easier to move forward.


### Machinery for academic collaboration / reporting privacy issues to PING

* Pete: We should consider outreach to academics, making PING a friendly place for them to come with their thinking, to get their work incorporated into underlying standards, pushing towards vendors etc. that way.
* Brad Lassey: Coordinate with IETF PEARG?  Pete: Maybe, though not clear they have that pipeline in place either
* Sam Weiler: Lightning talks at academic conferences (e.g. Usenix Security, IEEE S&P, NDSS) can be a good way for such outreach, raise awareness and visibility.  Doesn't even require coordination with the group.



### Charter reviews

* Sam Weiler:
https://github.com/w3c/strategy/labels/Horizontal%20review%20requested
... Recall that anyone can weigh in on charter reviews, from any perspective
* Brad Lassey: Machine Learning seemed like it could be interesting in privacy implications.
* Sam: That was a workshop proposal, not a working group.
* Repo where we keep pointers to the PING issues we've raised against other groups:
https://github.com/w3cping/tracking-issues/issues <- tracking issues for PING concerns


### AOB

* Sam: Privacy Community Group -- still in progress, should get it up and running soon.

* Sam: New PING call schedule: 1st / 3rd Thursdays of the month.  Expect the Community Group to slide into the 2nd/4th Thursdays at the same time.


## Agenda:

1. Outstanding privacy reviews
2. Updates on WebRTC and font fingerprinting conversations
3. Call for next FP surface to tackle
4. Machinery for academic collaboration / reporting privacy issues to PING
5. Charter reviews
6. AOB

## Queue:


## other comments

