# Privacy Interest Group meeting - 21 May 2020

## Attendees 

* Peter Snyder (co-chair, Brave)
* Christine Runnegar (co-chair)
* Sam Weiler (W3C)
* Wendell Baker (Verizon Media)
* Ben Savage (Facebook) 
* Shaun Gilmore (Apple)
* Nick Doty (UC Berkeley)
* Tara Whalen (in transition...)
* Erik Anderson (Microsoft)
* Jeffrey Yasskin (Google Chrome)
* Michael Kleber (Google)
* Joel Odom (Salesforce)
* Joey Salazar (ARTICLE 19)
* Brad Lassey (Google)
* Chris Wilson (Google)
* Terri Oda (Intel)
* Wendy Seltzer (W3C)
* Theresa O'Connor (Apple)


apologies: 
* Sean Bedford
* Chris Wilson will be 15-20 minutes late due to AB/TAG call.  Would like to be there for Web Audio issues.
* Wendy Seltzer (ditto to cwilso)
* Tess (ditto)

scribing: Wendell

## Agenda and Minutes:

Sam: seeing Chris's request for WebAudio to be later, would the chairs like to reorder agenda?  (Though we might be done with the agenda before then.) [CW: thanks Sam!]

Christine: We can re-arrange the agenda

### 1. Deciding next steps for PING tracking issues for Web Audio and Media Capture (continued from 7 May 2020)

Christine: As set out in the email, we will not being doing a roll call. We will be discussing the tracking issues on Web Audio and Media Capture and Streams. You should have read ahead :-)  But, please ask questions if you are unclear or need further explanation of any of the issues. 

### Media Capture

Media Capture and Streams (aka GetUserMedia): https://w3c.github.io/mediacapture-main/

Pete Snyder has done the detailed review.  Three large groups of issues across the ten-ish detailed issues.

#### Changes in # of Devices Per Category
*   https://github.com/w3cping/tracking-issues/issues/96

[Continuing with Peter Snyder].  Pre-permission UX can leak significant device capabilities.  Requesting a solution to not leak these capabilities before the UX permission is displayed.

Wendell: what level of detail are we looking for? what level of importance?

The solution should be at the high/medium/low is a framework to use.  PING should have a diversity of voices here.  But there should be some explanation of the importance issue.

Nick Doty:  Where are the views of the Media WG / WebRTC.

Pete: All converstion with WG has been through the issues and is captured in the issues; there does not seem to be a single viewpoint in the Media WG.

Michael Kleber.  Surprised by the level as High.  The other issues in subsequent issues were expected to be higher.  This should be low / lowish.  It merely leaks a "few bits" of information.  It doesn't leak a whole identifier.

Christine.  Thank you Wendell. We discussed a "traffic light approach" last year (for privacy reviews).  But, today we are triaging tracking issues.  Triage being: examine the issues (a) if nothing further is needed close the issue (b) watching (so leave it open) (c) there is an issue that still needs to be resolved so the PING should mark as Needs Resolution.

Michael. OK (Understood)

Sam: thanks to Micheal for clarifying the difference between between things that leak a full identifier v. just a few more bits of entropy for FP.  Important distinction. 

Christine: based on the discussion (above) we will mark as Needs Resolution.

#### Don't reveal available hardware w/o permission
*   https://github.com/w3cping/tracking-issues/issues/83
*   https://github.com/w3cping/tracking-issues/issues/61
    (only reveal device info for devices in same category as permissioned devices)
*   https://github.com/w3cping/tracking-issues/issues/60
*   https://github.com/w3cping/tracking-issues/issues/10
    (don't reveal any device info before permission)    
*   https://github.com/w3cping/tracking-issues/issues/59
    (don't reveal any device info before permission, move device selection to browser UX)
*   https://github.com/w3cping/tracking-issues/issues/23
    (only reveal device info for specific permissioned devices)

Pete: one can learn all of the devices that are plugged in.  PING does not have a single resolution for how to deal with this.  There is a spectrum of resolutions: (lowest) leave it (middle) modify (high) most private means no learning of the device names & hardware.  

Pete: PING should continue nudging the Media WG to have a better solution.  Their solution is All Information is available.

Jeffrey.  Question to the PING.  Is PING happy with the current solution or is it really necessary to block everything.  What is the sense?

Pete: Suggests quetsion should be that the current situation is sufficiently severe to block the specification ratification.  Suggesting that the question should be whether or not current specification is sufficient.

Jeffrey:  I would be good to give the WG some indication of what possible solutions PING would still object to, but on the question of whether the current situation needs to change, Yes, the specification should change.

Nick:  PING has gone back and forth on this specification because of the nuances and details.  Does PING know whether the Media WG has a definition of what level of privacy they are attempting to achieve?  For example, one guarantee to give is that there shall be zero bits of information before permission occurs.  That is a possible standard.

Pete:  Yes, acknowledged.  There should be a suggestion that the browser should mediate some part of the UX here.  There is a consideration of how similar the 1.0 and 2.0 versions of the specifications are from the desired end state of privacy guarantees.

Michael:  I have concerned around the procedural approach of PING only taking a viewpoint once any change has occurred in a WG.  This leaves PING open to having fluid standards of privacy definition.  There exists a privacy checklist which ahs been developed.  We, PING, have asked that groups look over and respond to that checklist before asking for horizontal review.  The checklist should be PING's starting point for the review response.

Christine: The Self-review: Security and Privacy Questionnaire and the PING Note on Mitigating Browser Fingerprinting [cite] are an excellent starting point for a review.  The questionnaire is annotated and provides some suggested mitigations which are known.  However, the privacy vulnerabilities and mitigations change over time as do the features in a developing standard so it is difficult to give a fixed view ahead of time for WGs.  But, we should give as much guidance as possible ahead of review.  The domain experts are the specification authors themselves, so they are probably in the best position to be the developers of the mitigation in the spec.

questionnaire: https://w3ctag.github.io/security-questionnaire/

mitigating fingerprinting: https://w3c.github.io/fingerprinting-guidance/

Sam.  Unless you're saying that THIS group is experiencing a problem with the goalposts moving - and I don't think I have heard that concern - I would like to focus on the concrete issues in front of us, consistent with our agenda today, and save process discussions for later.  I think these issues are all pretty crisp and clear, with clear proposed resolutions. 

Christine:  Based on the discussion, we will mark this as PING will represent that this as Needs Resolution.  

(npd: on this subcategory, per the Mitigating Browser Fingerprinting, I think enumerateDevices in a pre-permission mode is fingerprinting surface with severity factors of cross-origin, drive-by context, permanent/persistent. And so mitigations of permissions or reducing granularity would be recommended.)

Pete.  Will continue following the issue

Christine.  This is just triage today.  We should make sure to figure out how we can help resolve the issues.

#### Make device handles less identifying
*   https://github.com/w3cping/tracking-issues/issues/2
    (Dual key device IDs, don't make them UUIDs) Make device handles less identifying
*   https://github.com/w3cping/tracking-issues/issues/82
    (Don't use UUIDs)
*   https://github.com/w3cping/tracking-issues/issues/21
    (Dual key device IDs)
*   https://github.com/w3cping/tracking-issues/issues/2
    (Dual key device IDs, don't make them UUIDs)

Pete:  There are four sub-issues here.  Web sites refer to devices by UUIDs (globally unique identifiers) which necessarily identifies more than just the device.  The Media WG has offered that the device names (numbers) can be reset when Local Storage is cleared.    However, some extensions intervene to prevent Local Storage clearing.  In this case, the UUID can be used to recover the previously cleared cookies or local storage.  The suggestion to mitigate is to use small(ish) integers or other non-unique numbering s ystem.

Jeffrey: This should be a Level 2 (medium) issue.  There is a partitioning scheme [merged](https://github.com/w3c/mediacapture-main/pull/674), cited above) that provides a redress to the concern.

Pete: This is good.  However this does not address everything in the concern set.  Partitining of the Storage would address this but most browsers are not performing that technique at this point.  This set of issues should continue to be watched as the solutions evolve in the Media WG.

Christine: It is unclear how to address this issue.  It is between Needs Resolution and Needs Watching.

Sam:  It looks like the WG has a PR that might resolve the issue.  Someone needs to poke PING to have us look at that.  In general, that should be by saying something in the issue, but Jeffrey has brought it to our attention today.

Christine:  Let's put it in the Checking category. 

Sam: Let's not downgrade it until PING does re-review it.

Brad Lassey:  Is there any issue with the specification allowing for storage partitioning. If partitioning is already being used then there is no new leakage occurring.  

Pete: There are times when the browser loses cookies but not the rest of the persistent state.  So the concern is that there is risk of reassociation via the handles to relink across the storage partitions.

Nick: there have been discussions about clearing all storage in an atomic act so that this reassociation cannot occur.  Question: is this documented anywhere that storage needs to be cleared in one API place and atomic.

Christine We should check that his is covered in the self-review: security and privacy questionaire. Nick, would you be willing to take a look.

Nick:  There should be an issue to ensure the atomicity of storage destruction.  Will open an issue to track.

Christine: Okay, based on the discussion.  Will leave a Needs Resolution tag.  Pete will follow up on the PR and Jeffrey's pointers (above).

### Web Audio

Web audio API: https://webaudio.github.io/web-audio-api/

Sam: These were reviewed two weeks ago and there has been no further discussion in the Issues.  Last call for issues?

Sam:  The WG closed two of the issues; I've aseked them to reopen.  Waiting to hear back.  

Chris Wilson: It is unclear what progress the Audio WG can make on the inaudible sounds issue.   It is possible to make it visible with UX such as "tab is playing" icons but there does not seem to abe an obvious mitigation.

Sam:  That's why we marked it as a "tracker", not "needs-resolution".

Chris:  The issues seem conflated.

Sam:  There were three things that came up in one WG thread.   The PING tracking issues have been retitled to clarify.  

Chris:  What should be resolved?

Sam: enumerating
1. Sample Rate Fingerprinting
2. Gateway platform Default
3. Floating-Point Fingerprinting

Chris:  There are solution possibilities.   For example force-clamping the audio sample rate to 44.1kHz to "the Web" to ensure that there is privacy.  There are other examples.    Should the Audio WG be pushed towards one or other possible mitigation.  But converting 48kHz to 44.1kHz will cause audio artefacts.

Sam: The WG discussion seemed to conclude "platform default is okay; gatekeep other things", but the Audio WG seems to have closed the issue without writing that into the doc.

Christine:  The PING task is to highlight privacy vulnerabilities.  Secondarily to show possible mitigations (if we can).  Having the conversations with the WG on both aspects is an important role. Today we are performing triage:
1. close, no need
2. seems to be trending well, will continue watching
3. identified privacy vulnerability not yet addressed; Needs Resolution
  there may or may not be WG activitiy to redress.
  
Christine: This discussion on is important but we should make sure it is set out  in the Issues.  The focus today (and conscious of time) continues on the triage procedure.
  
Sam: We reviewed these in depth two weeks ago.  Further discussion can happen in the GH Issues.

Sam:  The triage was:
1. Inaudible Sounds: Tracker, needs more discussion.  Needs more exploration.
2. Sample Rate: Needs Resolution.
3. Floating Point Fingerprinting: Needs Resolution.

Christine: How should the discussion on inaudible sounds proceed?

Sam: The problem is described well in the Issues.  WG needs to dig into the mitigation space a bit more; see if there is anything they can do.  The Audio WG has it on their agenda today to decide where to have that discussion.

Brad:  If no resolution on inaudible sounds, is that OK?

Sam: I would not be surprised if we can't fix it, and would cope. but I want to see more exploration of the space first.

Christine: Inaudible Sounds is Tracking, watch for later. If can't be resolved, should be documented in privacy considerations section.

(npdoty: +1, I think we should document known vulnerabilities, even if there isn't a current good mitigation.)
(pete: +1 too, seconding 👆)

Joey:  Would like to see a warning. in the UX.  Would like to see Needs Resolution.   All three issues 

Chistine. Thank you Joey. To clarify, #2 & #3 are already Needs Resolution.  #1 is Tracking, but as noted above it should be documented in the privacy considerations of the spec to advise implementors and oths, and because infuture a mitigation might be possible.

Sam:  Will take an action to review the sec&priv section re: inaudible.  If it has an inadequate exploration of the inaudible sounds issues, I will upgrade this issue again.  (After-meeting note: it is not documented.  Sam updated the issue to say that.)

Christine: And if PING can be clear about what PING intends.

#### Sample Rate fingerprinting
*   https://github.com/w3cping/tracking-issues/issues/50


#### Generated Wave form / floating point implementing fingerprint 
*   https://github.com/w3cping/tracking-issues/issues/53


#### Inaudible Sounds
*   https://github.com/w3cping/tracking-issues/issues/89
    (https://github.com/WebAudio/web-audio-api/issues/2191) 

#### Older closed issues
*   https://github.com/w3cping/tracking-issues/issues/13

Note: This is just a placeholder. Nothing we need to do today.

### 2. New Web developments and privacy considerations

Pete:  At PRIVACY CG, a review of the Privacy Threat Model was reviewed.  TAG was shown the work as well.  There should be more involvement in the Privacy Threat Model document.

### 3. AOB

(No items)
