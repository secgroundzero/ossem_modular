# OSSEM MODULAR

Inspired by [Olaf Hartong's](https://twitter.com/olafhartong) [SYSMON modular](https://github.com/olafhartong/sysmon-modular) and the awesome [OSSEM](https://github.com/hunters-forge/OSSEM) project by the Hunter's Forge.

Started this project for documenting Windows logs and performing threat hunting in a sensible and manageable manner. OSSEM Modular is aimed to help when starting ingesting logs and troubleshoot in an easier way.

I will often only enable specific categories using auditpol and monitor those without having to worry about logs volume. Then i use OSSEM modular to injest only the related logs and perform the threat hunting exercises this way using [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team) i.e in smaller scale and building up on that.

At the moment this project contains Windows Security Logs, Sysmon logs and some Zeek lgos although i plan to add more event providers.

**Security Event Logs categories included in the repo:**

- [Logon / Logoff Events](https://github.com/secgroundzero/ossem_modular/tree/master/Logon-Logoff%20Events)
 - [Account Management Events](https://github.com/secgroundzero/ossem_modular/tree/master/Windows%20Security%20Logs/Account%20Management%20Events)
- [Account Logon Events](https://github.com/secgroundzero/ossem_modular/tree/master/Account%20Logon%20Events)
- [Object Access Events](https://github.com/secgroundzero/ossem_modular/tree/master/Object%20Access%20Events)
- [Detailed Tracking Events](https://github.com/secgroundzero/ossem_modular/tree/master/Detailed%20Tracking%20Events)
- [Privilege Use Events](https://github.com/secgroundzero/ossem_modular/tree/master/Privilege%20Use%20Events)
- [Policy Change Events](https://github.com/secgroundzero/ossem_modular/tree/master/Windows%20Security%20Logs/Policy%20Change%20Events)
- [DS Access Events](https://github.com/secgroundzero/ossem_modular/tree/master/DS%20Access%20Events)
- [System Events](https://github.com/secgroundzero/ossem_modular/tree/master/System%20Events)

**Sysmon Event Logs categories included in the repo:**

- [Event Id 1: Process Creation](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-1.md)
- [Event Id 2: A process changed a file creation time](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-2.md)
- [Event Id 3: Network Connection](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-3.md)
- [Event Id 4: Sysmon service state changed](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-4.md)
- [Event Id 5: Process Terminated](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-5.md)
- [Event Id 6: Driver Loaded](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-6.md)
- [Event Id 7: Image Loaded](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-7.md)
- [Event Id 8: CreateRemoteThread](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-8.md)
- [Event Id 9: RawAccessRead](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-9.md)
- [Event Id 10: Process Access](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-10.md)
- [Event Id 11: FileCreate](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-11.md)
- [Event Id 12: RegistryEvent (Object create and delete)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-12.md)
- [Event Id 13: RegistryEvent (Value Set)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-13.md)
- [Event Id 14: RegistryEvent (Key and Value Rename)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-14.md)
- [Event Id 15: FileCreateStreamHash](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-15.md)
- [Event Id 16: Sysmon Config State Changed](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-16.md)
- [Event Id 17: PipeEvent (Pipe Created)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-17.md)
- [Event Id 18: PipeEvent (Pipe Connected)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-18.md)
- [Event Id 19: WmiEvent (WmiEventFilter activity detected)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-19.md)
- [Event Id 20: WmiEvent (WmiEventConsumer activity detected)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-20.md)
- [Event Id 21: WmiEvent (WmiEventConsumerToFilter activity detected)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-21.md)
- [Event Id 22: DNSEvent (DNS query)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-22.md)
- [Event Id 23: FileDelete (A file delete was detected)](https://github.com/secgroundzero/ossem_modular/blob/master/SYSMON/EventId-23.md)

Events that according to Microsoft Docs are not active or dont produce any logs have been ommited. 

If you want to adopt the complete pipelines config as is you can use either the complete Windows the [Windows Security](https://github.com/secgroundzero/ossem_modular/blob/master/pipelines/windows_security_events.conf) pipeline or the [SYSMON](https://github.com/secgroundzero/ossem_modular/blob/master/pipelines/1001-sysmon_pipeline.conf) pipeline otherwise implement log by log depending on your needs.

All credit for their hard work with OSSEM goes to [Roberto Rodriguez](https://twitter.com/Cyb3rWard0g) and [Jose Rodriguez](https://twitter.com/Cyb3rPandaH)

**Problems**

If you identify any of these open an issue indicating the log ID and the problem. 

**Notes**

Fields marked as TBD in OSSEM have been populated to what i believe is appropriate. When OSSEM is updated i will update those as well.

As i could not generate all Zeek events i relied on sample logs file from [here](https://github.com/brimsec/zq-sample-data/tree/master/zeek-default):



This repo is mainted for now only by me <https://twitter.com/Sec_GroundZero>

## References 
- [OSSEM](https://github.com/hunters-forge/OSSEM)
- [HELK](https://github.com/Cyb3rWard0g/HELK)
- [Ultimate Windows Security](https://www.ultimatewindowssecurity.com/)
- [Microsoft Docs](https://github.com/MicrosoftDocs/windows-itpro-docs/tree/master/windows/security/threat-protection/auditing)
- [TrustedSec Sysmon Guide](https://github.com/trustedsec/SysmonCommunityGuide/blob/master/process-creation.md)
- [Microsoft](https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon)
