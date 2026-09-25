Question 1
This activity gives you the opportunity apply the content you have learned in this lesson. You will practise identifying different types of digital artifacts, mapping them to lifecycle phases and considering which forensic tools you can use to analyse them.

Task

1. Artifact identification 

Make a list of at least six digital artifacts that investigators might encounter.

Use the video examples: hard drives, USB activity, emails, chat logs, browsing history, log files, memory dumps, mobile app data, etc.

Organise them into categories: file system, memory, network, logs/events and mobile/cloud.

2. Lifecycle mapping 

For four of your chosen artifacts, decide at which stage of the incident response lifecycle (listed below) they would be most useful.

Stages

Preparation

Detection and analysis
Containment, eradication and recovery
Post-incident activity.
Write 1–2 sentences explaining your choice for each artifact.

Example: You could analyse browser history during the detection and analysis phase to confirm whether a user clicked a malicious link.

3. Tools and artifact matching

Choose three forensic tools from the videos (e.g., FTK Imager, Volatility, Wireshark, Splunk, Cellebrite). For each tool:

name the type of artifact it can help you recover or analyse
give a short scenario (2–3 sentences) showing how that artifact might be important in an investigation.
Example: You could use Volatility to analyse a RAM dump to uncover malicious processes running in memory during a ransomware attack.

4. Reflection 

Write a short paragraph (5–6 sentences) reflecting on the following questions.

Why is it important to maintain the integrity of artifacts (think: write blockers, chain of custody, documentation)?
How could mishandling an artifact affect the legal admissibility of evidence?
Which artifact type do you personally think is most challenging to investigate, and why?

1. Artifact identification and 2. Lifecycle mapping

| Artifact | Category | Relevant lifecycle phase | Why this phase? |
| --- | --- | --- | --- |
| Browser history | File system/logs | Detection and analysis | Helps identify if a user accessed phishing sites or malicious links |
| RAM dump | Memory | Containment, eradication and recovery | Allows removal of malicious processes still running in memory |
| Authentication log | Log/event | Detection and analysis | Reveals unusual login attempts or brute-force activity |
| Archived incident report | Documentation/log | Post-incident activity | Serves compliance needs and supports organisational learning |

3. Tools and artifact matching

| Forensic tool | Artifact(s) analysed | Scenario example |
| --- | --- | --- |
| FTK Imager | Disk images | Used to create a bit-for-bit copy of a hard drive in an intellectual property theft investigation, preserving evidence |
| Volatility | RAM dump | Identifies ransomware processes and extracts encryption keys active in memory |
| Wireshark | Network traffic packets | Captures outbound data exfiltration, confirming a breach and identifying malicious IP addresses |

4. Reflection

Maintaining the integrity of artifacts is crucial for their admissibility in legal proceedings. Write blockers and careful imaging preserve originals, while chain of custody documentation ensures accountability. If artifacts are mishandled, the court could throw out the evidence. The most challenging artifacts are memory artifacts because they are volatile and can be lost if not collected immediately. This makes the use of tools like Volatility essential during live investigations.

