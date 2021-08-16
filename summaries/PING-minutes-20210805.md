# Privacy Interest Group meeting (5 August 2021)

## Attendees 

* Peter Snyder (PING Co-Chair, Brave Software)
* Wendy Seltzer (W3C)
* Sam Weiler (W3C/MIT)
* Wendell Baker (Verizon Media)
* Sean Harrison (Google)
* Peter Lowe
* Theodore Olsauskas-Warren (Google)
* Jeffrey Yasskin (Google)
* Matthew Finkel (Tor)
* Jared Hirsch (observer)
* Kristen Chapoman (Salesforce)
* Shivan Sahib (Brave Software)
* Eric Mwobobia (ARTICLE19) 
* Mallory Knodel (CDT)

Apologies: Christine Runnegar

Scribe: Sam

### 1. Privacy reviews 

## a. HTML Review Draft

• URL of spec: https://html.spec.whatwg.org/review-drafts/2021-01/

• What and when is your next expected transition? CR, 2021-08-24

• What has changed since any previous review? Please look at the list of important changes here: https://github.com/w3c/htmlwg/issues/17

Pete: Of the things the authors had flagged, reviewers didn't see issues.  Found four other things.

@@ ...  if they opt-in, get access to more features.

* Can add cross-origin attribute to HTML tags; spec also mentions that header response is controlling; not clear how attribute interacts with that.  e.g. if you tag a script with a mine type - what doc says is overridden by HTML headers.  So this seems confusing, at the least.

[Matt adds: Some more details about the cross-origin attribute: https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/crossorigin]

* New opt-in gives things at same origin a more restrictive execution environment.  Seems to specify process isolation; seems a big change, mentioned in passing in the text.  Not appl layer protection; OS layer.  I want a clarification, at least.

* References to reporting API; reporting API is still in draft, seems out of order, given priv/sec issues open.  Suggesting they remove references for now.

* "Prevent downloads in iframe sandbox by default" - this is editorial, not substantive.  'substantiator'/initiator' context not clear.

More thorough review will happen; not just things that were labeled as privacy-interesting by WG/authors.  

Comments?

[silence]

## b. Privacy review (request received) for DOM Review Draft

• URL of spec: https://dom.spec.whatwg.org/review-drafts/2021-06/

• What and when is your next expected transition? 2021-08-31, CR

• What has changed since any previous review? Please look at the list of important changes here: https://github.com/w3c/htmlwg/issues/19

Pete: volunteers?

[silence]

Pete: we'll go to the next reviewer on the list.

### 2. Privacy reviewers list
 - https://cryptpad.w3ctag.org/pad/#/2/pad/edit/XFYXN76vmE+W3BTD3M2pFE0s/
 
Pete: look at above list; make sure your own entry is up-to-date.  Any issues with the cryptpad, let me know.  And feel free to solicit colleagues to join.

### 3. AOB

Peter Lowe: thanks to Pete for HTML changes review.  I volunteered for this and am still learning.

Theo: status of reviewers list?

Pete: stale.

Mallory: thanks for keeping meeting short.  In the past, we've used volunteers from that list.  Would be helpful to have a list or count of what people have reviewed.

Pete: history is captured in GH; could reflect it here if that's helpful.

[Adjourned]

