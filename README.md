## Level I - Basic
#### Network
* Must use TLSv1.2 for all communications via WAN, preferably via LAN
* [Certificates must be verified on connection](https://en.wikipedia.org/wiki/X.509#Certificates)

#### Software/Firmware
* [No default username/password](http://www.csoonline.com/article/3126924/security/here-are-the-61-passwords-that-powered-the-mirai-iot-botnet.html)  
    * Devices must not ship with a well-known username and/or password
        * Unless the password must be changed on first use
    No backdoor passwords in firmware. This can be dumped and reversed and published.
* Each client or model should have a certificate issued from a vendor-controlled CA to control access
* No credentials stored in firmware besides certificate
    * No non-unique API keys per-device.  
    Storing non-unique private keys or API credentials on a device is unnecessary.
* Each device should have a unique ID that is generated at manufacture time
    * Optionally via a formula provided to the manufacturer
    * Keep registry of existing devices and activated devices if possible
* Remote updates or expiration date
    * Device must be remotely updateable when security patches need to be issued  
    OR  
    * Device must cease functioning after five years since last update  
* Require firmware updates to be signed by manufacturer to prevent drive-by updates
* Basic prevention of brute-force login attacks if applicable

#### Hardware Nice To Have Features
* [TPM](https://en.wikipedia.org/wiki/Trusted_Platform_Module) for secret storage and boot
* Tamper sensors
* Hardware scoped to minimum requirements for operation
* Physical reset to factory settings
* Event stream of device telemetry to cloud
* rfkill; physical switch to disable radios

## Level II - Audit
Additional level of customized auditing and certification that VonGuard Security performs for clients that desire a more comprehensive review.

#### Policy Documentation / Review
* Help drafting a security policy document for internal or compliance purposes.
* Define current security posture and review deficiencies from final goals.

#### Disaster Recovery / Business Continuity
* Ensure your critical business operations are recoverable after catastrophe.
* Be prepared to handle problems immediately. Define an incident response plan.

#### Static Analysis
* [Valgrind](http://valgrind.org/) static analysis for common programmer mistakes
* [llvm](http://llvm.org/) [clang](https://clang.llvm.org/) advanced C compiler with support for run-time safety instrumentation
   * [ADDRSAN](https://clang.llvm.org/docs/AddressSanitizer.html)
   * [MEMSAN](https://clang.llvm.org/docs/MemorySanitizer.html)
   * [AFL fuzzing](http://lcamtuf.coredump.cx/afl/)
   * [OWASP](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)
* If initiating long socket connection to server, keep-alive needed to prevent automatic socket closure by routers etc
* If using open-source project code, the projects should be maintained to provide security updates
* If using software components from a propriatary vendor should have a maintainence contract
