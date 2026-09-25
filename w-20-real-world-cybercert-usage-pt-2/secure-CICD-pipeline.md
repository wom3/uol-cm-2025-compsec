
Question 1
In the SolarWinds incident, attackers compromised the build environment and inserted malware before release, which was then digitally signed and shipped to customers. Your job is to design a continuous integration/continuous deployment (CI/CD) pipeline that would have prevented, detected or limited this outcome.


# Feedback

| Pipeline stage | Failure point (SolarWinds) | Risk | Proposed control |
| --- | --- | --- | --- |
| Source control | Limited checks on changes to code and dependencies | Malicious or unverified code could be introduced | Enforce signed commits, peer review and automated dependency scanning |
| Build environment | Shared, long-lived, high-privilege build servers | Attackers could tamper with builds and persist inside systems | Use isolated, ephemeral build runners with least privilege and hardened configurations |
| Signing/provenance | Signing trusted a compromised build | Customers received malware that appeared legitimate | Generate provenance/attestations and verify builds before signing |
| Release/deployment | Updates pushed broadly without staged rollout | Malicious updates quickly reached thousands of organisations | Use gated releases with canary/staged deployment and rollback mechanisms |
| Monitoring/response | Weak anomaly detection; breach discovered by a third party | Delayed detection and response amplified damage | Centralised logging, SIEM, anomaly detection and rapid incident response procedures |
