Equifax Data Breach Explained: A Case Study
Josh Amishav
·
Last updated May 20, 2026
·
10 min read
Learn how to prevent catastrophic breaches like Equifax by understanding what went wrong.

• Attackers exploited an unpatched Apache Struts vulnerability and an expired security certificate to steal 147.9 million records over two months undetected.
• Stolen data from nation-state attacks rarely surfaces on dark web markets. If a breach never produces credentials publicly, intelligence collection is the likely motive, not financial gain.
• Catastrophic breaches end careers and reshape regulation. The CEO, CIO, and CSO all left within weeks, and credit freezes became free nationwide as a direct result.
• Patching one Apache Struts CVE or renewing one expired certificate would have stopped this entire breach. Sophistication wasn’t the problem.
In 2017, Equifax suffered a data breach that exposed the personal information of 147.9 million Americans. That’s roughly 40% of the U.S. population.

The attackers exploited a known vulnerability that had a patch available for months. They remained undetected for 78 days because an SSL certificate had expired and nobody noticed. When Equifax finally discovered the intrusion, executives sold stock before going public.

The Equifax breach became a case study in how basic security failures led to catastrophic outcomes. Every failure was preventable with standard practices.

This analysis covers exactly how the attack unfolded and what security teams can learn to prevent similar breaches.

What Happened in the Equifax Data Breach?
The Equifax breach started with a web application vulnerability that had been public knowledge for months.

A data breach occurs when attackers gain unauthorized access to systems and steal sensitive information. Unlike data leaks from misconfigurations, breaches require attackers to actively exploit vulnerabilities to access protected systems.
On March 7, 2017, Apache disclosed CVE-2017-5638, a critical vulnerability in the Apache Struts web framework. The flaw allowed remote code execution through a malicious HTTP Content-Type header. Apache released a patch the same day.

Three days later, on March 10, attackers exploited this exact vulnerability on Equifax’s online dispute portal. The company’s security team received alerts about the patch but failed to apply it across all systems.

For the next two months, the attackers moved laterally through Equifax’s network. They found plaintext credentials stored on internal systems. These credentials gave them access to databases containing consumer financial records.

Between May and July 2017, the attackers exfiltrated data on 147.9 million people. They encrypted the stolen data to avoid detection by network monitoring tools.

Here’s why they got away with it for so long.

Why Did the Equifax Breach Go Undetected for 78 Days?
Equifax had network monitoring tools designed to detect exactly this type of data exfiltration. The tools were supposed to decrypt and inspect traffic leaving the network.

They weren’t working.

A critical SSL certificate had expired in January 2017. Without a valid certificate, the monitoring tools couldn’t decrypt traffic. The attackers’ encrypted exfiltration looked like normal HTTPS traffic.

Nobody noticed the expired certificate for over six months.

On July 29, 2017, administrators finally renewed the certificate. The monitoring tools immediately flagged suspicious activity. By then, the attackers had been inside for 78 days and stolen data on 40% of U.S. adults.

The GAO investigation report documented these failures in detail. Equifax had security tools but failed to maintain them.

Who Attacked Equifax?
This is where the Equifax breach gets interesting. The stolen data never showed up on dark web markets. That’s unusual for a financially motivated attack.

Attribution is the process of identifying who conducted a cyberattack based on technical evidence and attack patterns. Nation-state attackers typically don’t sell stolen data because their goal is intelligence gathering, not profit.
On February 10, 2020, the U.S. Department of Justice charged four members of China’s People’s Liberation Army with the Equifax hack. The indictment named Wu Zhiyong, Wang Qian, Xu Ke, and Liu Lei from PLA Unit 54398.

The evidence suggests Equifax was part of a broader Chinese intelligence operation. The 2015 Office of Personnel Management breach exposed 22 million federal employee records. The 2018 Marriott breach exposed 500 million hotel guest records. Neither dataset appeared on dark web markets.

Investigators believe China combined these datasets to build dossiers on U.S. government officials and intelligence officers. Financial records from Equifax reveal who has money problems and might be vulnerable to recruitment or blackmail.

The attackers were patient. They gained initial access in March but waited until May to begin data exfiltration. This patience is typical of nation-state operations focused on intelligence gathering rather than quick financial gain.

What Were the Key Impacts of the Equifax Breach?
The Equifax breach hit the company from every angle.

Financial Impact

The total cost of the breach reached $1.38 billion. This included:

Settlement costs: Equifax agreed to pay up to $700 million to settle with the FTC, CFPB, and 50 state attorneys general. The fund included $425 million for consumer compensation.

Security improvements: The settlement required Equifax to spend $1 billion improving its information security practices over five years.

Insurance recovery: Equifax had $125 million in cybersecurity insurance coverage, which it collected in full.

Stock impact: Equifax shares dropped 35% in the week following disclosure. The company’s market cap fell by $5 billion.

Executive Consequences

The breach ended multiple careers at Equifax:

CEO Richard Smith resigned in September 2017
CIO David Webb retired immediately after the breach
CSO Susan Mauldin retired days after the disclosure
Jun Ying (CIO of U.S. Information Solutions) was charged with insider trading for selling stock before the public announcement
Regulatory Changes

The breach triggered new requirements for credit bureaus:

Free credit freezes became mandatory nationwide (previously some states charged fees)
Annual credit report access expanded
Consumer Impact

For the 147 million affected individuals:

Increased risk of identity theft and fraud
Seven years of free credit monitoring through the settlement
Permanent exposure of Social Security numbers that can’t be changed
What Is the Equifax Data Breach Timeline?
Here’s exactly when each event occurred and how the attack progressed.

DATE	EVENT
March 7, 2017	Apache discloses CVE-2017-5638 and releases patch
March 10, 2017	Attackers exploit vulnerability on Equifax dispute portal
May 13, 2017	Attackers begin lateral movement and data exfiltration
July 29, 2017	Expired SSL certificate renewed, suspicious activity detected
July 30, 2017	Equifax takes their dispute portal offline
August 2017	Multiple executives sell company stock
September 7, 2017	Equifax publicly discloses the breach
September 26, 2017	CEO Richard Smith resigns
February 10, 2020	DOJ indicts four Chinese military officers
The 78-day detection gap matters. IBM’s 2025 Cost of a Data Breach Report puts the mean time to identify a breach at 181 days. Equifax was faster than average but still gave attackers nearly three months of access.

Equifax breach timeline showing how the attack unfolded

How Did Equifax Respond to the Breach?
Equifax’s incident response became a case study in what not to do.

Confusing websites: Equifax created equifaxsecurity2017.com to help affected consumers. The domain looked like a phishing site. Their social media team accidentally directed people to securityequifax2017.com, a parody site.

Waiving legal rights: The original terms on the response website required consumers to waive their right to sue in exchange for checking if they were affected. Equifax removed this after public backlash.

Executive stock sales: Several executives sold shares between learning about the breach and the public announcement. Only one was charged with insider trading.

Delayed notification: Equifax discovered the breach on July 29 but waited until September 7 to disclose it, a 40-day gap.

The FTC settlement website now handles consumer claims, not Equifax.

Equifax settlement website screenshot

What Security Lessons Can We Learn From the Equifax Breach?
The Equifax breach was entirely preventable. Here’s what security teams should take away.

Patch Faster

CVE-2017-5638 had a patch available for two months before the attack. Equifax’s security team was aware of it but didn’t apply it to all systems.

What to do differently:

Maintain an up to date asset inventory of all systems and their software versions
Set SLAs for patching critical vulnerabilities (24-48 hours for actively exploited CVEs)
Verify patches are actually applied, not just scheduled
Monitor Your Security Tools

Equifax had the right monitoring tools. They just weren’t working because of an expired certificate.

What to do differently:

Set alerts for expiring certificates months in advance
Monitor that your security tools are actually functioning
Run regular tests to verify detection capabilities work
Segment Your Network

Once attackers got inside, they moved freely through the network. Credentials found on one system gave access to many others.

What to do differently:

Implement network segmentation between systems with different sensitivity levels
Don’t store credentials in plaintext anywhere
Assume a breach will happen and design systems to limit lateral movement
Implement Zero Trust

The attackers used legitimate credentials to access sensitive databases. The systems had no way to distinguish between authorized and unauthorized use.

What to do differently:

Require multi-factor authentication for all sensitive system access
Monitor for unusual access patterns even from authenticated users
Implement least privilege so compromised accounts have limited reach
Don’t Store Credentials in Plaintext

Attackers found plaintext credentials on internal systems after getting in. Those credentials unlocked access to sensitive databases.

What to do differently:

Never store credentials in plaintext anywhere
Use a secrets management system
Rotate credentials if you find out they’ve been leaked or suspect compromise
How Does the Equifax Breach Compare to Other Major Breaches?
The Equifax breach ranks among the largest data breach examples in history.

By records exposed: Yahoo (3 billion), First American (885 million), and Marriott (500 million) exposed more records. But Equifax exposed Social Security numbers and financial data, making each record more damaging.

By financial impact: The $1.38 billion cost exceeds most breach settlements. Only the Capital One breach ($190 million fine plus remediation) and Yahoo ($117.5 million settlement) approach this scale.

By systemic importance: Equifax is one of three major credit bureaus. Unlike a retailer breach, consumers can’t choose to stop doing business with Equifax. The company has your data whether you want them to or not.

The breach shares common elements with other major incidents. Like the Target breach, attackers exploited vendor relationships and moved laterally through insufficiently segmented subnets. Like many breaches, basic security hygiene failures made this attack possible.

What Has Changed Since the Equifax Breach?
Almost a decade on, several of the security and policy gaps that let Equifax happen have closed. Several others haven’t.

Vulnerability disclosure has accelerated. CISA’s Known Exploited Vulnerabilities catalog launched in November 2021 partly in response to incidents like Equifax. An Apache Struts-style remote code execution today gets federal-civilian patching SLAs measured in days, not months, and most enterprises mirror those expectations internally.

Credit freezes are free everywhere. The 2018 Economic Growth, Regulatory Relief, and Consumer Protection Act made credit freezes free in all 50 states. That’s now a baseline consumer right, not an Equifax-era reform that consumers had to fight for.

Software supply chains have more visibility. Executive Order 14028, signed in May 2021, pushed federal vendors toward software bill of materials requirements. Most enterprises now track which open-source components live inside their stack, which means an Apache Struts blind spot is much harder to maintain than it was in 2017.

Nation-state attribution is faster. The PLA Unit 54398 indictment came in February 2020, nearly three years after disclosure. Today, attribution for state actors often happens within months rather than years, in part because intelligence agencies have invested heavily in tracking specific units across operations.

Static personal data is no longer a secret. Eight years on, the Equifax data has been joined by data from countless other breaches. Social Security numbers and dates of birth circulate so widely on criminal markets that banks and credit issuers are moving toward identity verification that doesn’t rely on data anyone could buy for a few dollars.

What’s still broken. Patch-management SLAs are still inconsistently enforced inside large enterprises. Certificate-monitoring blind spots still cause outages and detection gaps. The 2024 Snowflake breach showed that credential reuse and missing multi-factor authentication still drive some of the largest incidents. Most of those Snowflake credentials came from infostealer malware, the same category of threat that’s grown explosively since Equifax.

How Can You Protect Your Organization From Similar Breaches?
The Equifax breach succeeded because of multiple preventable failures. Here’s how to avoid the same fate.

Treat vulnerability management as critical infrastructure. Don’t just track patches, verify they’re applied. Run regular vulnerability scans and treat unpatched critical systems as incidents.

Monitor your monitoring. Security tools only work when they’re functioning. Build dashboards that show tool health, not just threat detections. Alert on monitoring gaps.

Assume a breach in your architecture. Design networks expecting attackers will get in. Segment sensitive systems. Monitor for lateral movement.

Watch for your credentials on the dark web. Attackers often obtain credentials from previous breaches before launching new attacks. Run a dark web scan to see which of your credentials are already exposed, then use dark web monitoring to catch new leaks and reset them before attackers exploit them.

Practice incident response. Equifax’s response made a bad situation worse. Run tabletop exercises. Have pre-approved communication templates. Know who makes decisions before a crisis hits.

How Can Breachsense Help Detect Credential Exposure?
The Equifax breach shows what happens when credentials aren’t protected. Attackers who get inside your network will hunt for credentials to expand their access.

Many attacks start with credentials leaked in previous breaches. Employees reuse passwords, and attackers exploit that. Breachsense monitors dark web markets and hacker forums for your organization’s credentials. When employee passwords appear in new breaches, you can reset them before attackers try using them.

Book a demo to see how credential monitoring fits into a layered security approach.

Equifax Data Breach FAQ


What happened in the Equifax data breach?
Attackers exploited an unpatched Apache Struts vulnerability (CVE-2017-5638) to access Equifax systems in March 2017. They moved laterally through the network and stole data on 147 million Americans over 78 days. The breach went undetected because an expired SSL certificate disabled network monitoring. Equifax disclosed the breach in September 2017.

Could the Equifax breach have been prevented?
Yes, the breach could have been prevented with timely patching of the Apache Struts vulnerability, proper network monitoring, and robust credential management practices. Implementing a comprehensive vulnerability management program and regular security audits could have mitigated the risk.  

How much did people get from the Equifax settlement?
The Equifax settlement provided up to $425 million to compensate affected individuals. Eligible consumers could receive up to $20,000 for actual damages, including lost money or time spent dealing with the breach, and free credit monitoring services for up to 10 years. The exact amount varied depending on individual claims and the total number of claimants.

Who was behind the Equifax hack?
The Equifax hack was carried out by attackers exploiting a known vulnerability in the Apache Struts framework. While the specific individuals or groups responsible were not publicly identified, it is believed to have been a sophisticated cybercriminal operation targeting sensitive consumer data.

What vulnerability caused the Equifax breach?
The breach was caused by an unpatched vulnerability in the Apache Struts web application framework, specifically CVE-2017-5638. This allowed attackers to execute remote code on Equifax’s servers and gain unauthorized access to sensitive data.

How long did the Equifax breach go undetected?
The Equifax breach went undetected for approximately 78 days, from mid-March 2017 until it was discovered in late May 2017. The breach remained unnoticed partly because an expired SSL certificate disabled network monitoring.

What data was stolen in the Equifax breach?
The attackers stole sensitive personal information of approximately 147 million Americans, including names, Social Security numbers, birth dates, addresses, and, in some cases, driver’s license numbers. Additionally, some credit card numbers and dispute documents were also compromised.

## Redesigning Equifax’s System

To prevent a breach like this, I would redesign Equifax around a zero-trust, modular architecture. Instead of a large monolithic web portal connected to sensitive databases, the public-facing dispute portal would be isolated in a dedicated microservice with no direct access to customer records. Authentication and authorization would be enforced centrally using least-privilege policies, MFA, and short-lived service tokens. Critical data stores would be segmented by sensitivity and stored encrypted at rest and in transit using modern key management, with secrets never kept in plaintext. A separate identity and access layer would verify every request, so even if one app were compromised, lateral movement would be limited. Patch management would also be automated through a controlled CI/CD pipeline that blocks deployment of vulnerable components and enforces rapid remediation for critical CVEs. In addition, all systems would be inventory-tracked and continuously scanned for known vulnerabilities.

To detect or prevent the Apache Struts issue, Equifax needed continuous vulnerability scanning, dependency monitoring, and a formal patch SLA for critical CVEs. The Struts flaw should have been identified by automated scanners, SBOM checks, and threat intelligence feeds tied to asset inventory. Regular penetration testing and red-team exercises would have exposed the exposed web app path, while security monitoring and certificate health checks could have flagged the expired SSL certificate before it disrupted detection. A robust incident response process with daily patch review, canary deployments, and dashboards for tool health would have reduced the time to detect and contain the compromise.

