# OSSEM MODULAR

Inspired by [Olaf Hartong's](https://twitter.com/olafhartong) [SYSMON modular](https://github.com/olafhartong/sysmon-modular) and the awesome [OSSEM](https://github.com/hunters-forge/OSSEM
) project by the Hunter's Forge.

Started this project for documenting Windows logs and performing threat hunting in a sensible and manageable manner. OSSEM Modular is aimed to help when starting ingesting logs and troubleshoot in an easier way.

I will often only enable specific categories using auditpol and monitor those without having to worry about logs volume. Then i use OSSEM modular to injest only the related logs and perform the threat hunting exercises this way using [Atomic Red Team](https://github.com/redcanaryco/atomic-red-team) i.e in smaller scale and building up on that. Using a modular approach makes troubleshooting much easier as well. 

The following log categories are included in the repo:

- Logon / Logoff Events
- Account Management Events
- Account Logon Events
- Object Access Events
- Detailed Tracking Events
- Privilege Use Events
- Policy Change Events
- DS Access Events
- System Events

Events that according to Microsoft Docs are not active or dont produce any logs have been ommited. 

If you want to adopt the entire pipeline as is you can use the full pipeline file in the repo otherwise implement log by log depending on your needs.

All credit for their hard work goes to [Roberto Rodriguez](https://twitter.com/Cyb3rWard0g) and [Jose Rodriguez](https://twitter.com/Cyb3rPandaH)

This repo is mainted for now only by me <https://twitter.com/Sec_GroundZero>

## References 
- [OSSEM](https://github.com/hunters-forge/OSSEM)
- [HELK](https://github.com/Cyb3rWard0g/HELK)
- [Ultimate Windows Security](https://www.ultimatewindowssecurity.com/)
- [Microsoft Docs](https://github.com/MicrosoftDocs/windows-itpro-docs/tree/master/windows/security/threat-protection/auditing)


