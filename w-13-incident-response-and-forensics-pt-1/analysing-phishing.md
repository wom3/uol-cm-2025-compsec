A hospital receives a targeted phishing email. An employee clicks a link that installs malware, giving attackers remote access. They move laterally across the network, encrypt medical records and demand ransom.

Task

1. Map the attack to the cyber kill chain.

Identify which of the seven stages are represented (e.g., delivery, exploitation, command and control, actions on objectives).

2. Identify matching ATT&CK techniques

For each stage, list at least one relevant ATT&CK tactic/technique (e.g., initial access via phishing, persistence via malicious scripts).

3. Link to forensic artefacts

For each stage, suggest one piece of digital evidence you would collect (e.g., email logs, registry entries, system images).

Submission format

Create a table with three columns with the headings: ‘Kill chain stage’, ‘ATT&CK technique’ and ‘Forensic evidence’.
Keep your table to around one page long.
Self-check questions

Does my mapping cover all key stages of the cyber kill chain?
Have I selected ATT&CK techniques that reflect real adversary behaviour?
Do my suggested forensic artefacts show clear links to the attack activity?

| Kill chain stage | MITRE ATT&CK technique | Forensic evidence |
| --- | --- | --- |
| Reconnaissance | T1598: Phishing for information | Evidence of targeted spearphishing emails sent to staff |
| Weaponisation | T1566.001: Spearphishing attachment/link | Malicious email attachment or link in email header logs |
| Delivery | T1204: User execution | Mail server logs showing delivery; user click records |
| Exploitation | T1059: Command and scripting interpreter | Execution logs, PowerShell logs, event logs from infected machine |
| Installation | T1547: Boot or logon autostart execution | Registry modifications, persistence artefacts on infected system |
| Command and Control (C2) | T1071: Application layer protocol | Network traffic logs showing outbound connection to malicious server |
| Actions on objectives | T1486: Data encrypted for impact | Encrypted medical record files, ransom note on infected systems |


