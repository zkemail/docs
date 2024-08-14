# Packages

This document provides an overview of the three main packages that make up ZK Email Verifier. The packages are **zk-email/circuits**, **zk-email/helpers**, and  **zk-email/contracts**. Each package serves a specific purpose in the process of verifying DKIM signatures in emails using zero-knowledge proofs.

### 2024 Audit by zksecurity

We completed a second audit in May 2024 of all of our ZK circuits, including our latest ZK regex rewrite. The audit deemed that EmailVerifier was safe, but people using sub-components for custom circuits require extra changes and validations. We have fixed all of the high/medium issues, and you can see the full report here and use the fixed circuits via using version 6.1.1 from npm.

Fixes committed at [95cd90](https://github.com/zkemail/zk-email-verify/commit/95cd90) for zk-email-verify

Fixes committed at [5396ec](https://github.com/zkemail/zk-regex/commit/5396ec) for zk-regex

{% file src="../../.gitbook/assets/zk_email_zksecurity_audit.pdf" %}

### 2023 Audit by Y Academy

We completed our first audit on our circom helper templates. Below, you'll find a detailed PDF report of the findings. We've addressed each issue raised in the audit and have listed the corresponding PRs below for you to see the fixes in detail.

* Missing constraint for illegal characters: [PR#103](https://github.com/zkemail/zk-email-verify/pull/103)&#x20;
* Incorrect use of division operation: [PR#104](https://github.com/zkemail/zk-email-verify/pull/104/commits/531f9c2b811cc06a935cb80a17311d28e3662871)
* Missing range checks for output signals: [PR#104](https://github.com/zkemail/zk-email-verify/pull/104/commits/9c14d51f130bb0cb0cf6eecb4945cbc5ff72f48a)
* Missing constraints for a signal input: [PR#104](https://github.com/zkemail/zk-email-verify/commit/4d4128c9980336d7f6dc0dcc7e1458203af15b4d)
* Missing constraints for output signals: [PR#104](https://github.com/zkemail/zk-email-verify/commit/4d4128c9980336d7f6dc0dcc7e1458203af15b4d)
* Issue with value retrieval in the LongToShortNoEndCarry: [PR#104](https://github.com/zkemail/zk-email-verify/pull/104)

{% file src="../../.gitbook/assets/zkemail-audit (2).pdf" %}
