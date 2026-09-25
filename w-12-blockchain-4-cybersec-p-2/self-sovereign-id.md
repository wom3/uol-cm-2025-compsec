consider w-11* and w-12* and answer the following.

### 1.
Question 1
**Scenario**

A humanitarian aid organisation is developing a digital identity system for refugees in cross-border camps. Many individuals lack official ID documents, and current paper-based processes are slow, insecure and prone to fraud. The organisation wants to use blockchain to provide secure, portable and user-controlled identities that multiple service providers (e.g. healthcare, education, banking) can recognise.

**Task**

Based on what you’ve learned so far, propose a blockchain-based solution to this problem. Your response should address the following points.

1. System overview

- What kind of identity model would you use (e.g. self-sovereign identity, hybrid)?
- Who would issue and verify the credentials?
2. Key features

- How will the system ensure data privacy, security and user control?
- What blockchain features (e.g. encryption, decentralisation, hashes) are most relevant?
3. Implementation considerations

- What challenges might arise in onboarding users or gaining trust from stakeholders?
- How would you address issues of regulation, access or technology literacy?



Feedback
1. System overview 

A self-sovereign identity (SSI) model would be the most suitable approach justified by the need to give displaced individuals control over their identity, particularly when they have no formal documentation. In this model, trusted NGOs or UN agencies would issue identity credentials, while service providers such as clinics, schools or banks would act as verifiers within a permissioned blockchain network.

While SSI is well-suited to decentralised, trust-minimising environments, a federated model (with a few recognised issuers) could also be acceptable if regulatory or operational constraints prevent full decentralisation. 

Either model must clearly justify user needs, risk and technical feasibility.

2. Key features 

The system uses encrypted off-chain identity credentials, anchored to the blockchain via immutable hash references. This design supports data privacy while ensuring auditability.

Identity holders control access using private keys, with suggested alternatives such as physical backups (e.g. QR code cards) for those without mobile access. The model includes verifiable credentials and selective disclosure, which are appropriate for managing sensitive personal data in insecure or cross-border contexts.

These design choices align well with blockchain’s strengths: tamper-evidence, decentralised validation and user control.

3. Implementation considerations 

There are major risks such as:

digital exclusion (low literacy or lack of devices)
key loss and the need for recovery mechanisms (e.g. social guardianship)
regulatory uncertainty, especially across borders.
Realistic mitigation strategies must align with best practices in digital identity deployment, such as assisted onboarding and modular trust frameworks.

Evaluation

This solution prioritises user autonomy, data protection and system interoperability. It demonstrates an understanding of blockchain affordances while remaining grounded in the ethical and practical realities of humanitarian deployment.

Alternative approaches, such as a consortium-led identity registry or centralised issuance with decentralised verification, could also be valid if they are well justified. The key is a defensible match between the identity model, the user context and the technological constraints.