# Privacy Interest Group meeting (19 January 2023)

## Attendees

* Christine Runnegar (co-chair)
* Nick Doty (Center for Democracy & Technology, co-chair)
* Peter Snyder (Brave Software, co-chair)
* Don Marti (CafeMedia)
* Wendell Baker (Yahoo)
* Chris Lemmons (Comcast)
* Ulf (Ford)
* Carine Bournez
* Philippe Le Hegaret (W3C)
* Jeffrey Yasskin (Google Chrome)
* Sean Harrison (Google) (apologies had to drop halfway)
* Aram Zucker-Scharff (The Washington Post)

Regrets:

Scribe: jy for automotive, npd for rest.

## Agenda

### 1. Welcome, introductions, [code of conduct](https://www.w3.org/Consortium/cepc/) 

plh introduces himself as our current staff contact. Doesn't plan to attend all meetings, but we can contact him for problems, including tooling.

Welcome to Automotive WG folks, including chair and editors.

### 2. Visit from Automative WG re: VISS 2 Core and Transport

https://www.w3.org/TR/viss2-core/
https://www.w3.org/TR/viss2-transport/

Nick: We appreciate the overview of your work. This is novel compared to the Web stuff we usually look at, but it's a privacy sensitive area.

Ted: I'm one of the co-chairs of the automotive WG. Been at W3C for 20-some years. Automotive is different. It's an offshoot and hard to reconcile that it's part of the W3C. Automotive is embedded and physical/mechanical engineering. Necessary for the myriad of changes they're going through. Autonomous, need data for fleet management, insurance. Very political. Look at Mass. right-to-repair commercials, which went too far. The interest is to bring different types of stakeholders together; made sense to go with Web technology. VISS started with web sockets, then HTTP. Can look at differences between 1st and 2nd version. Added filtering and access control. Encouraged JWT. First version was very light. Volvo and Uber collaborated using VISS1. Underlying data model (VSS) is in another organization (COVESA). Solid traction: considered in ISO 20078, etc. Extended vehicular server. COVESA and AUTOSAR have next-gen architecture in the vehicle, and VISS is being considered there, with a make-or-break moment in a few months. Wrangling about who owns the data, who can use the data, often not in the interst of the individual. EU parliament has taken a good direction, with the ability to protect individual rights and to bring data to third parties. We're trying to design something that's flexible; remaining in the technical level and avoiding politics and beaurocracies. VISS 2 is more complicated, and was prompted by Volkswagon joining with a different technology. VISS is part of AWS Fleetwise; other companies. Lots more is happening in COVESA than in W3C; trying to figure out what should be in the W3C. Right now VISS and an ontology (VSSo). Also looking to create best practices. Best practices are in the wiki. COVESA agrees that we should come up with best practices.

Carine: I had previous discussion with Sam Weiler, but don't want to shape the debate with that yet.

Christine: Thank you very much for the overview. Before the conversation, I would like a better understanding of what the specs are trying to do functionally.

Ted: Automakers, inside the vehicles, all do data differently. Requires custom integration per auto manufacturerr. Want to normalize the data into a common model, VSS. And VISS is meant to expose that data. Several use cases: 1) Meant for in-vehical. Instead of the data port, with its little network of microcomputeers, which communicate on a broadcast network, which isn't great for security or privacy. This is being changed slowly under AutoSar to use encrypted and signed messages. Intent was to be able to expose normalized data in a lightweight API with web technologies. To let non-embedded engineers, like from insurance company, to have applications that reside on the vehicle. Permissions and legalities have been out of scope, and in control of OEMs until regulators get involved. They usually do good things w.r.t. consent, although that's sometimes embedded in sales agreements.

Ted: Also want to use VSS to offboard the data. Upload data to the cloud. I want data sampling to happen on the vehicle and go out. Maybe there'll be competing standards for the protocol space. The data model has firm traction.

Nick: Attempted summary: Data model is a format so applications on the vehicle or maybe off the vehicle, can use a common format for signals that are sent between modules in the car, or once it's sent elsewhere.

Ted: Core truth for VSS is in YAML, but VISS is JSON (?). Graph schema.

Nick: Maybe it would be useful to have a basic security model. For people coming into vehicle systems for the first time. e.g. here are the systems on and off the vehicle, and who has access. That would make it easier to identify problems and to review.

Ted: There's a lot of interesting stuff for security people w.r.t. in-vehicle networks. Outside of the W3C, I'm in groups that attack vehicles and trucks and make recommendataions. There are broad improvements that need to take place. Different manufacturers will vary, but we want an abstract layer above the vehicle. A lot of the security will remain the manufacturer's responsibility. The various signals like the rate of speed is a signal from multiple sensors. Also actuator driven signals. VSS and VISS support people writing those attributes, e.g. to set a speed goal or to lower a window. But anything control-related shouldn't be changed. That's on the automaker side. Don't see VISS for autonomous vehicle interactions. Needs to be more integrated. Safety remains on the OEMs. They're the end arbitrator. But we do have access control inside VISS. For privacy/security/safety, an insurance application might want to know if there's harsh braking, etc, if they've worked that out with the owner. But some other things would be disallowed. Those policies, like who can read what signals, would be within the scope of the automakers. 

Nick: We have a broader set of considerations than usual on the Web, but you have lots of good examples of how the data shouldn't be misused. Do you feel liek those considerations are described?

Ted: No, it's a years-long process with regulators and courts. We don't say that we expect that the OEM would take responsibility, but it's understood. e.g. an application shouldn't be able to cause uncontrolled acceleration.

Jeffrey: interested in wrirting down a set of best practices, could include OEM responsibility or how user consent is being requested.

Ted: start of a wiki, not getting enough attention. COVESA expert group to take on work on best practices.

Aram: Thank you. I should re-read the spec with that information in mind. I think that while there are best practices in the wiki. Maybe you already have privacy people in the group, or one of us could join. Beyond the best practices, where you're using consent herre, it might make sense to have deeper awareness in the specification. Some kind of standard method by which consent is transferred. Depends on the WG figuring out the form. And consent might be fragmented in some ways. If system is set up so that consent can't be granted over particular subsets of the data ... might want to give the car repair shop information about my average speed, but not to my insurance provider. If the consent is set by the user on the vehicle's built-in device, how is that parsed out. If it's on the app that sets up the device, what controls does that enable. Could change the spec's shape. My big concern here is that there's two areas of consent issues. There are lots of vehicles in use that aren't in use by their owner. How does someone with a rental car get presented with the consent flow? Might fit in a best practices document, coudl also fit into the spec, like with an expiration for consent. Other side is about find-toothed control. The app model is not great here. iOS is all-or-nothing with each application, vs Android is really nothing. Consider how delicate the privacy situation is with a vehicle owner sharing data to entities that can resell it in ways they don't expect. Insurance is interested in data, which means the data is valuable, so it's valuable to get the data in other ways. E.g. an app might track speed and then resell the data. Users will find that either there's a more proactive level of control, or they just want to block everything. Giving them the ability to block all data transmission is important, but something needs to deal with it in a nuanced way. In the browser space, we don't want to present the user a lot of UIs, since they just say no or dismiss it. When we're looking at web specs, we think about how we can shape the specification so we ask for consent as little as possible, and can understand from the user's choices how they consent in other ways. Another way this is applicable is in the adtech space, think about consent signals and how they travel down APIs. Not just granting access but describing consent. My big concern when reading this is the dependency on the vehicle user to give consent, and there's a lot that sits on top of that. But the rest of the structure doesn't handle consent in the way that would be needed for that to happen.

Ted: Makes sense. 1) If PING can point us to tools for capturing and managing consent, we'd like to see it. Right now it's considered out of scope. At the beginning, COVESA was next-gen in-vehicle entertainment. That was the head unit, the stereo+computer. We lost that. QNX and Android Auto got it. COVESA gave up on voice interaction and navigation. The EU is a lot further toward individual rights. Look forward to them shaping this. Power grab with OEMs trying to control the data as part of sales agreements. Couldn't buy the care unless you agree to give them data. State-of-the-art is ["ADEN"](https://www.aidenabled.com/), that have an interface on Android Auto that is good at using lay terms. (It's confusing to explain what happens inside a vehicle) They explain what about the vehicle you might give to different people. The [person from Univ. Malaga has presented on proxy re-encryption](https://www.sciencedirect.com/science/article/abs/pii/S1084804517301078) (right link?). The individual could encrypt data before it leaves the vehicle and say what purposes it's used for. The person could revoke things. Automakers say it's too complicated and don't want it. We need something. We need to see how the power plays shake out. Looking for the best ways to represent this, and we're kinda stuck. The group participation: OEMs aren't getting involved in proxy reencryption, so we're not going that direction. There's still interest in how to do it right, and we can continue to propose things.

Ulf: Aram's comments were quite interesting. Fully agree that right now, the VISS spec is transparent to consent. I was thinking about if it can at all be included in some way. In a vehicle, you don't have 1 compute platform, but many. It's very distributed. Connected in a more ad-hoc way. Every platform can communicate with all others. Consent wouldn't be deployed at only 1 of these platforms, but at multiple. This spec is usually implemented as a server, serving clients on and off the vehicle. Could handle the consent chain from where it gets the information, and ask the driver. Driver coudl be in control of this serrver implementing the standard. In the access control, we can apply access control to single signals. Any signal that's represented in the VSS tree. And there, in the specification, it's described how tags can be applied to signals, which are leaves in the tree. Could apply it to branches higher up in the tree and specify that it's valid for all nodes. One could apply a similar pattern for consent. It's far from true in the spec. Look into the "access control selection", and maybe consent could be applied in a similar way. This information would have to be written through a side-interface. Not VISS directly, but another interface. Not to allow any client to set it. UI would live inside the vehicle. Server would read consent like it reads the access control tags. Could be used to block or not block requests for data. Now that's a big long process. We also need COVESA to agree. But maybe we could wait until then.

Aram: Will take a look in that regard and look for hooks. Consent for the central stack and the ability to have the Android Vehicle thing could hold a user's consent and pass it to the system when it connects. If you're already engaged with regulators, having something built into the spec could help a great deal. Your work here has fallen under the radar of advocates, but as you go toward mainstreaming it, you'll hear from privacy advocates who are involved with regulators. They'll see that this doesn't dovetail neatly with regulatory requirements. Maybe you'll say the OEMs willd eal with it. But migth not work well if you're already engaged with regulators. I'd also add that there's probably a lot of interesting pieces that we might be albe to send examples of how consent is processed in GPC. Or ??? API where it's a signaling process. Felt for the proxy-encryption proposal. They'll resist doing the work now, but they'll have to implement it once the regulators take notice. The proxy-encryption idea you're talking about here is something website authors are looking into for compliance handling. People will use it one way or another. Need space in the spec to expand toward that. 

Nick: Good conversation. Need to keep us on track, and talk about next steps. Some issues are already open. What action is needed there? How do we give you feedback?

Ted: Let's revisit on a followup call, or continue on github on issues. Please raise issues. We're also waiting to see how some things play out, and what the participants are willing to contribute to. True of any spec. Implementers can choose to skip parts of the spec. The more we can use this groups' assistance to influence the auto industry the better. They're big and slow-moving. Let's try to move them in a good direction. We'll follow up on Github.

Nick: Please send to our list or the chairs the issues we need to follow up on, and I'll look into scheduling a future call to continue discussing.

### 3. Privacy review of UI Keyboard Events Core Values and UI Keyboard Key Events

https://github.com/w3cping/privacy-request/issues/109
https://github.com/w3cping/privacy-request/issues/108

Pete: two related specs, objects that you get back when you register a handler for keyup and down events, for example. code property that maps onto a physical button on your device. and key property, the logical value that an application should process, like whether it's a capital Q or lower case. main privacy concern is fingerprintability of the hardware keyboard that they're using. different from the keyboard configuration (qwerty vs dvorak). real, likely concern of identifying fingerprinting input.

right place to deal with that is not dictionary of definitions but in the keyboard events -- UI Events specification, that fires the events themselves.

plh: are we exposing the layout of the keyboard?

jy: in some cases, yes, like when a game wants to provide navigation and not just "wasd" but the up/down/left/right.

pete: keyboard map draft

jy: +1, the right place to handle permissions is in the thing that fires the events. UI would be difficult/intrusive? most websites wouldn't need to use keyboard layouts. would break existing use cases to add that permission, since it's just an event that fires.

pete: event firing is asynchronous, so could prompt the user at that moment.

jy: should talk to anne van k. about the risks of taking new actions at the event listener subscription moment. bluetooth as an example has a separate function.

jy: when you call addeventlistener that requests the extra information, then an async permission UI ... but would cause some breakage


### 4. Privacy review of PNG (postponed)

https://github.com/w3cping/privacy-request/issues/105

Aram working on this, to be discussed on next call.

### 5. Identify a privacy reviewer for CSS View Transitions

* CSS View Transitions - https://github.com/w3cping/privacy-request/issues/107

Looking for a reviewer on this CSS spec. Contact chairs, or we may send emails looking for a reviewer.

### 6. AOB

Slack or mailing list for any further discussions we didn't get to today.