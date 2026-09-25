# Question 1. Case Study: University Assessment Platform

A university operates a cloud-based assessment platform that supports online exams, coursework submission, feedback distribution, and access to student academic records. Students and staff access the system using Single Sign-On (SSO), while academic administrators use a separate management portal to manage assessments and user accounts. The platform stores sensitive personal information, assessment submissions, and examination records in cloud-hosted databases and file storage services.

Following a recent security review, several weaknesses were identified. User accounts are protected only by passwords, with no multi-factor authentication in place. Some academic and administrative staff have been granted permissions that exceed their job requirements. Security logs are collected inconsistently, making it difficult to investigate suspicious activity. Configuration files containing database connection information have been found on publicly accessible servers, and critical security patches have not always been applied promptly. The university is concerned that these weaknesses may increase the risk of unauthorised access to student records and compromise the integrity of assessment data.

## 1(a) Principle of least privilege

The principle of least privilege means that users and systems should only be given the minimum access required to perform their job functions. In the university platform, this would mean that lecturers should only be able to view and grade their own modules, administrators should only access the functions relevant to their role, and support staff should not have unrestricted access to student records or assessment data.

This improves security because it reduces the impact of accidental misuse, insider threats, and compromised accounts. If a lecturer account is breached, the attacker should not automatically have rights to change student records, alter marks, or manage system settings. It also supports better accountability, because roles are easier to audit and harder to abuse. In an environment with highly sensitive academic data, least privilege is a core control because it limits both lateral movement and the scale of damage following a successful attack.

## 1(b) Why secure logging matters

Secure logging is important in application security because it helps the organisation detect suspicious activity, investigate incidents, and prove what happened after a breach. Logs provide evidence of failed logins, unusual access patterns, privilege changes, and attempted misuse of systems. Without consistent logging, an organisation may not realise that data has been compromised until it is too late.

One clear benefit is incident investigation: if a student record is accessed without authorisation, the organisation can trace who accessed it, when it happened, and from which system or device. One risk of logging sensitive information is that logs themselves become a valuable target. If full passwords, emails, or card numbers are stored in plain text, an attacker who gains access to log files could use that data directly or expose the organisation to legal and compliance consequences.

## 1(c) Four most important improvements

### 1. Enforce multi-factor authentication (MFA) for all user accounts

This addresses the weakness that user accounts are protected only by passwords. Password-only authentication is vulnerable to phishing, credential theft, and brute-force attacks. MFA adds a second factor, such as a one-time code or authenticator app, so that even if a password is compromised, the attacker still cannot easily gain access. This reduces organisational risk because it directly protects student and staff accounts, reduces the chance of unauthorised access, and supports compliance with good security practice.

Over time, MFA creates a stronger baseline for all digital services. It reduces the likelihood of account takeover, limits exposure to exam manipulation, and makes suspicious login behaviour easier to detect and investigate.

### 2. Implement role-based access control and least privilege

This addresses the weakness where some staff have excessive permissions. The university should assign access according to role, not personal preference or convenience. For example, only a small number of authorised users should manage exam records, while ordinary lecturers should not have administrative rights outside their modules.

This reduces organisational risk because it reduces the blast radius of a compromised account and limits accidental changes to sensitive data. It also helps prevent insider misuse and strengthens governance. Over time, it creates a cleaner and more defensible access model, making audits easier and reducing the chances of unauthorised data exposure.

### 3. Put secrets and configuration data into a secure management system

This addresses the issue of database credentials and other sensitive values being stored in config files on publicly accessible servers. These files expose critical secrets to attackers and can be used to access systems or steal data. Secrets should be stored in a dedicated provider such as a secrets manager, with restricted access, encryption at rest, and access logging.

This reduces organisational risk because it removes the common weakness of hardcoded credentials and reduces the chance of a breach caused by configuration exposure. Over time, centralised secret management improves consistency, supports credential rotation, and makes it easier to detect and respond to misuse.

### 4. Improve patch management and logging/monitoring

This addresses the weaknesses of inconsistent logging and delayed patching. Unpatched systems create an easy route for attackers, while weak logging makes it harder to detect or respond to suspicious activity. The university should create a patching schedule, prioritise critical system updates, and monitor authentication, access, and administrative events with a consistent logging standard.

This reduces organisational risk because it closes known vulnerabilities and improves early detection. Over time, the university gains stronger resilience, faster detection of attacks, and better evidence for forensic review if a breach occurs.

## 1(d) MFA pseudocode

```text
function authenticateUser(username, password, otp):
    if username not found:
        return "Access denied"
    if password invalid:
        incrementFailedAttempts(username)
        return "Access denied"
    if otp invalid:
        incrementFailedAttempts(username)
        return "Access denied"
    if failedAttempts(username) >= 5:
        lockAccount(username)
        return "Account temporarily locked"
    grantAccess(username)
    resetFailedAttempts(username)
    return "Authentication successful"
```

## 1(e) DAC vs RBAC

Discretionary Access Control (DAC) is an access model in which the owner of a resource decides who may access it. In practice, a file owner or system administrator may grant permissions directly to other users. This model is flexible and can be convenient in small or informal environments, but it is also difficult to manage at scale and can lead to inconsistent permissions if users grant access without sufficient control.

Role-Based Access Control (RBAC) assigns permissions based on a user’s role within the organisation. For example, all student support officers may have access to a defined set of student record functions, while module leaders have different access rights. The advantage of RBAC is that it is more structured, easier to audit, and supports least privilege more reliably. The limitation is that it can be less flexible when unusual or temporary access is required, and it may require careful role design.

For this university platform, RBAC is the more suitable option. The environment contains different user groups with different responsibilities, and the university needs consistent, auditable, and scalable access management. A hybrid model may still be used in some cases, but RBAC is the stronger default for a large academic setting because it reduces privilege creep and supports secure governance.

## 1(f) Secure management of secrets and configuration data

If an attacker gains access to a configuration file containing database connection details and API credentials, the organisation should assume that the exposed secrets are potentially compromised and respond quickly. To manage secrets securely, configuration data should not be stored in plain text in source repositories or on public servers. Instead, the university should use a dedicated secrets manager, such as a cloud-based vault or enterprise secret store, to securely store database credentials, API keys, and internal tokens.

Access to secrets should be strictly controlled using identity-based policies, least privilege, and multi-factor authentication for administrators. Secrets should also be protected in transit and at rest using encryption, and all access should be logged for monitoring and audit. Credential rotation should be regular and automatic wherever possible, especially for API keys, database passwords, and service accounts. If a secret is suspected to be exposed, it should be revoked, rotated immediately, and reissued to the relevant services.

Monitoring is also essential. The university should deploy alerting for unusual access, secret use, and configuration changes, and should include secret scanning in development pipelines so insecure values are detected before deployment. This reduces the risk of repeated compromise and helps maintain a clearer security posture for cloud-hosted systems.

## 1(g) NIST Incident Response Lifecycle response

The university should respond using the NIST incident response lifecycle, which has five main stages: Preparation, Detection and Analysis, Containment, Eradication and Recovery, and Lessons Learned.

During Preparation, the university should ensure that roles are defined, response plans are tested, and the right tools and evidence-handling processes are in place. This includes secure logging, backups, communication channels, and an escalation procedure for suspected breaches.

During Detection and Analysis, the university should identify signs of unauthorised access, confirm whether records were accessed, and gather forensic evidence. This includes reviewing authentication logs, database access, configuration changes, and any abnormal patterns in student records or admin activity. The team should determine the scope of the breach and whether other systems were affected.

During Containment, the organisation should isolate compromised systems, revoke suspicious access, disable affected accounts, and block known malicious connections. It may also restrict access to the assessment platform while the investigation continues. The goal is to prevent further damage while preserving evidence.

During Eradication and Recovery, the university should remove malicious changes, patch vulnerable systems, rotate compromised credentials, restore clean backups, and rebuild affected services where necessary. It should validate that the platform is secure before students and staff can resume normal access.

Finally, during Lessons Learned, the university should document what happened, how the incident was detected, what controls failed, and how the response can be improved. This may lead to stronger patching policies, new monitoring rules, better access reviews, and revised secure configuration controls. This stage is important because it turns a breach into a long-term improvement cycle.

# Question 2. Blockchain-Based Citizen Identity Platform

## 2(a) Digital signatures vs hash functions

A cryptographic hash function takes an input and produces a fixed-size output, known as a hash or digest. It is used to verify integrity because even a tiny change in input produces a completely different hash. An example is SHA-256, which is widely used to check whether data has been modified.

A digital signature uses asymmetric cryptography. The sender signs a message or a hash using their private key, and the recipient verifies the signature using the corresponding public key. This provides authenticity, integrity, and non-repudiation. An example is an ECDSA signature, which is commonly used in secure systems to prove that a message came from a trusted party.

The key difference is that a hash confirms whether data changed, while a digital signature proves who signed it and whether the signer is trusted.

## 2(b) Why post-quantum cryptography matters

Post-quantum cryptography is becoming increasingly important because quantum computers are expected to break widely used public-key algorithms such as RSA and ECC through algorithms like Shor’s algorithm. This matters because many digital identity systems and blockchain transactions rely on these algorithms for confidentiality and authenticity. If these algorithms are weakened in the future, identity credentials, digital signatures, and protected transactions may become vulnerable.

One affected algorithm is RSA. One post-quantum alternative is CRYSTALS-Kyber, which is designed for key encapsulation and is intended to resist quantum attacks. Another valid example is Dilithium for digital signatures.

## 2(c) Four key cybersecurity risks and mitigations

### Risk 1: Smart contract vulnerabilities

A smart contract could contain bugs or logic flaws that allow unauthorised modification of identity records, manipulation of verification rules, or denial of service. This would affect citizens by allowing false credentials or altered records, and it would affect council services by undermining trust in the system and potentially causing legal or operational disruption.

Mitigation: the authority should require formal code review, independent security testing, and model-based verification before deployment. Smart contracts should be designed with least privilege, fail-safe conditions, and upgrade controls that are properly governed. The recommendation is strong because smart-contract defects are a direct and high-impact risk to trust and data integrity.

### Risk 2: Privacy and legal compliance issues, including the right to erasure

The case study highlights concerns about data protection and the right to erasure. Blockchain is difficult to amend because records are difficult to delete once written. If personal data is stored on-chain without careful design, the authority may struggle to comply with privacy law and may expose citizens to long-term data retention problems.

Mitigation: use privacy-by-design, store only minimal data on-chain, keep personal data off-chain in encrypted storage, and use verifiable credentials rather than raw personal records. The authority should also define governance processes for deletion, revocation, and lawful data retention. This is the correct recommendation because public-sector identity systems must satisfy legal accountability, fairness, and privacy obligations.

### Risk 3: Accessibility and digital skills barriers

Some citizens may not have smartphones, reliable internet, or the digital confidence to use a blockchain wallet or manage private keys. If the platform is designed without accessible alternatives, it could exclude older citizens, low-income residents, or people with limited digital literacy. This may undermine equal access to essential services such as housing support or social care.

Mitigation: provide assisted onboarding, multilingual instructions, user support, fallback methods, and offline or low-tech alternatives. The authority should also test the platform with real citizens and design for accessibility from the start. This recommendation matters because public services must be inclusive and usable by all citizens, not only digitally fluent users.

### Risk 4: Future quantum risk to cryptographic protection

The case study also notes concerns about the long-term impact of quantum computing on the algorithms used to protect identities and blockchain transactions. If the platform relies on current public-key cryptography, future quantum advances could threaten its security over the system’s lifespan.

Mitigation: adopt crypto-agility, use hybrid cryptography where possible, and plan a migration strategy toward post-quantum algorithms as standards mature. The authority should assess the lifetime of the identity system and ensure it can update cryptography without a full rebuild. This is justified because identity systems need to last for years and must remain safe in a future cryptographic environment.

## 2(d) Evaluate blockchain for digital identity management

Two advantages of blockchain-based digital identity are user control and portability. Citizens can manage their own credentials and share only the necessary information with a service, which reduces repeated disclosure of personal data and gives them more control than traditional systems. Blockchain can also provide a transparent and tamper-evident record of credential issuance and verification, which may increase trust across organisations.

Two limitations are scalability and privacy regulation. Public blockchains can be slow and expensive, while even private or consortium systems require careful governance and infrastructure. In addition, blockchain does not automatically solve privacy issues because identity data can still be sensitive and the technology raises legal challenges concerning data minimisation, consent, and erasure. For public-sector systems, these limitations are significant and must be managed carefully.

## 2(e) Centralised digital identity vs SSI

Traditional centralised systems rely on a trusted authority, such as a government registry or council database, to store identity records and validate user access. This gives a clear governance model and is familiar to users, but it creates a single point of failure. A breach of the central database could affect many citizens at once, and the organisation often holds a large amount of personal data, which increases privacy risk.

Self-Sovereign Identity (SSI) gives users control over their digital identities and credentials. The user stores credentials in a digital wallet and shares only the information required for a specific service. This supports privacy and data minimisation, and reduces the need for repeated disclosure of the same information. However, SSI depends on digital literacy, secure key management, and user recovery mechanisms. If a user loses their private key or wallet access, there may be serious operational consequences unless there are safe recovery options.

For this council context, the most appropriate approach is a hybrid model rather than a fully public blockchain-only model. A hybrid SSI approach with trusted issuers and a governed identity framework would provide better privacy, stronger user control, and better legal accountability while also addressing accessibility and operational recovery. This approach is more suitable because the council must serve a wide range of citizens, many of whom may not be comfortable with complex digital key management.

## 2(f) NIST incident response for a smart contract vulnerability

When a smart contract vulnerability is discovered in a deployed system, the organisation should respond using the NIST incident response lifecycle.

During Preparation, the authority should already have governance processes, secure development practices, contract review policies, emergency response roles, and a communication plan for affected citizens and partner organisations. It should also have a defined method for halting or freezing critical functions if a vulnerability is discovered.

During Detection and Analysis, the security team should confirm the nature of the vulnerability, assess whether it could allow unauthorised record changes, and determine the impact on affected citizens and services. The team should review transaction data, contract logic, signatures, logs, and any evidence of malicious activity. This phase should answer three questions: what is vulnerable, how severe is it, and who may be affected.

During Containment, the authority should restrict or pause affected functions, disable risky contracts if possible, and revoke or block access to vulnerable workflows. This may involve stopping identity verification actions until the vulnerability is addressed. The goal is to reduce further harm while preserving evidence for investigation.

During Eradication and Recovery, the team should fix or replace the vulnerable contract, review governance on upgrade and deployment permissions, and restore the system to a known-good state. The organisation should also communicate remediation steps to affected parties and validate the new code in a controlled environment before redeployment.

Finally, during Lessons Learned, the organisation should document the root cause, review whether secure coding and deployment controls were sufficient, and improve future governance. This may include stronger code audits, formal verification, multi-signature controls, and clearer incident escalation procedures. The aim is to reduce the chance of recurrence and improve resilience.

## 2(g) Executive briefing: most significant cybersecurity concern and first actions

The most significant cybersecurity concern is not just blockchain itself, but the combination of smart contract vulnerability, data protection obligations, and the risk of excluding citizens who cannot use digital identity tools. A breach in the credential verification logic could allow unauthorised modification of identity records, which would directly threaten trust in council services and could undermine the legitimacy of the whole system. This should be prioritised because digital identity systems affect access to housing, finance, healthcare, and public services, so even a small defect can have major social and legal consequences.

The first three actions management should authorise are:

1. Independent security review of the smart contract and identity infrastructure, including code review, testing, and formal verification before deployment.
2. Privacy and governance controls, including data minimisation, lawful retention, secure storage of personal data, and a clear process for credential revocation and erasure where legally required.
3. Accessible, inclusive rollout and recovery design, including digital support, assisted onboarding, fallback access, and user-friendly recovery options for lost credentials.

These actions support both security and accessibility. Security protects the integrity of the system and the rights of citizens, while accessibility ensures that the public service remains usable and fair. A digital identity platform that is secure but inaccessible, or accessible but insecure, would fail its purpose.

## Overall conclusion

The university case study shows that many major risks arise from weak access control, poor secret management, inconsistent logging, and delayed patching. The blockchain case study demonstrates that blockchain can help with trust and user control, but it does not remove the need for security design, legal compliance, usability, and governance. In both cases, the strongest answer is not technology alone: it is a security model built on least privilege, appropriate controls, clear governance, monitoring, and a realistic understanding of the organisation’s risks.


     
