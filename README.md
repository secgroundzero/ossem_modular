# OSSEM MODULAR

Inspired by [Olaf Hartong's](https://twitter.com/olafhartong) [SYSMON modular](https://github.com/olafhartong/sysmon-modular) and the awesome [OSSEM](https://github.com/hunters-forge/OSSEM) project by the Hunter's Forge.

Started this project for documenting Windows logs and performing threat hunting in a sensible and manageable manner. OSSEM Modular is aimed to help when starting ingesting logs and troubleshoot in an easier way.

I will often only enable specific categories using auditpol and monitor those without having to worry about logs volume. Then i use OSSEM modular to injest only the related logs and perform the threat hunting exercises this way using [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team) i.e in smaller scale and building up on that.

At the moment this project only contains Windows Security Logs and Sysmon logs although i plan to add more providers.

**Security Event Logs categories included in the repo:**

- [Logon / Logoff Events](https://github.com/secgroundzero/ossem_modular/tree/master/Logon-Logoff%20Events)
- Account Management Events
- [Account Logon Events](https://github.com/secgroundzero/ossem_modular/tree/master/Account%20Logon%20Events)
- [Object Access Events](https://github.com/secgroundzero/ossem_modular/tree/master/Object%20Access%20Events)
- [Detailed Tracking Events](https://github.com/secgroundzero/ossem_modular/tree/master/Detailed%20Tracking%20Events)
- [Privilege Use Events](https://github.com/secgroundzero/ossem_modular/tree/master/Privilege%20Use%20Events)
- Policy Change Events
- [DS Access Events](https://github.com/secgroundzero/ossem_modular/tree/master/DS%20Access%20Events)
- [System Events](https://github.com/secgroundzero/ossem_modular/tree/master/System%20Events)

**Sysmon Event Logs categories included in the repo:**

- Event Id 1: Process Creation
- Event Id 2: A process changed a file creation time
- Event Id 3: Network Connection
- Event Id 4: Sysmon service state changed
- Event Id 5: Process Terminated
- Event Id 6: Driver Loaded
- Event Id 7: Image Loaded
- Event Id 8: CreateRemoteThread
- Event Id 9: RawAccessRead
- Event Id 10: Process Access
- Event Id 11: FileCreate
- Event Id 12: RegistryEvent (Object create and delete)
- Event Id 13: RegistryEvent (Value Set)
- Event Id 14: RegistryEvent (Key and Value Rename)
- Event Id 15: FileCreateStreamHash
- Event Id 16: Sysmon Config State Changed
- Event Id 17: PipeEvent (Pipe Created)
- Event Id 18: PipeEvent (Pipe Connected)
- Event Id 19: WmiEvent (WmiEventFilter activity detected)
- Event Id 20: WmiEvent (WmiEventConsumer activity detected)
- Event Id 21: WmiEvent (WmiEventConsumerToFilter activity detected)
- Event Id 22: DNSEvent (DNS query)
- Event Id 23: FileDelete (A file delete was detected)

Events that according to Microsoft Docs are not active or dont produce any logs have been ommited. 

If you want to adopt the entire pipeline config as is you can use the [full pipeline file](https://github.com/secgroundzero/ossem_modular/blob/master/pipeline_skeleton) in the repo otherwise implement log by log depending on your needs.

All credit for their hard work with OSSEM goes to [Roberto Rodriguez](https://twitter.com/Cyb3rWard0g) and [Jose Rodriguez](https://twitter.com/Cyb3rPandaH)

This repo is mainted for now only by me <https://twitter.com/Sec_GroundZero>

## References 
- [OSSEM](https://github.com/hunters-forge/OSSEM)
- [HELK](https://github.com/Cyb3rWard0g/HELK)
- [Ultimate Windows Security](https://www.ultimatewindowssecurity.com/)
- [Microsoft Docs](https://github.com/MicrosoftDocs/windows-itpro-docs/tree/master/windows/security/threat-protection/auditing)
- [TrustedSec Sysmon Guide](https://github.com/trustedsec/SysmonCommunityGuide/blob/master/process-creation.md)
- [Microsoft](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon)
