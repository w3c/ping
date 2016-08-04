This is to compile our privacy comments regarding the Wake-Lock API.

https://www.w3.org/TR/wake-lock/

Please review the draft specification and share your views.

- If a web application makes a wake-lock request that is implemented by the user agent, what does this mean for other applications that are set to allow access to geolocation, NFC, camera, microphone when the screen is on? 
- Should this feature only be available in secure contexts?

**from *Lukasz Olejnik* https://github.com/w3c/wake-lock/issues/78**

I see several possible security and privacy issues here.

* Malicious popups/ads claiming some resources and making the device to (1) deplete their batteries (2) trick the user to think their hardware is faulty in some way, make them to install some app to fix the issue.

* Potential of cross-origin, even cross-browser or cross-device linking/communication? Scenario:

	* App/tab/device1 keeps a lock for e.g. screen

	* App/tab/device2 takes advantage of Ambient Light Sensors and tries to detect whether there is any light source nearby When feasible, this would make the WL API to behave in possibly unexpected ways from security and privacy point of views. This could allow a possible communication channel to either exfiltrate some data or synchronize identifiers.
	
Therefore I suggest considering the following for this moment:

	Implementations should be wary of possible Wake Lock 
	API abuses. In certain circumstances, abuse of the API 
	could trick the user into performing an otherwise 
	unwanted action. An example could be a malicious popup 
	attempting to convince the user that the (e.g.) the
	screen is faulty
	
	Ability to lock some parts of device peripherals, 
	in particular the screen, could possibly open 
	unexpected channels of communication, leading to 
	cross-domain or cross-device communication and linking
	
	The mechanism SHOULD be subject to permissions.
	-> The entire screen wake lock feature is already 
	polyfillable with a hidden video tag (see e.g. 
	https://github.com/richtr/NoSleep.js) and it 
	requires no permissions at all, AFAIK. So even if 
	we add a superior security model to this spec, 
	malicious site authors will just use other existing 
	methods such as the video tag to achieve the same end.

	I'm not against introducing permissions for Wake 
	Lock API in principle, in fact we considered it 
	(please see https://lists.w3.org/Archives/Public/public-device-apis/2016Jun/att-0046/minutes-2016-06-16.html) 
	but decided to go with a simpler model at this time.
	
	The User-Agent MUST allow to view the past and 
	current Wake Lock usage 
	-> This constitutes a conformance requirement, yet 
	the spec does not define what it means exactly to 
	allow to view the past and current Wake Lock usage
	(what is the UI for viewing, how far into the past 
	etc). It is also hard (if at all possible) to write 
	an automated conformance test for that. I suggest 
	using SHOULD instead of MUST, as is the case e.g. 
	for Vibration API and Battery API.

Are there any other uses of WL API other than screen? 

	-> Not yet