# Account Recovery

ZK EMAIL DOCS HAVE MOVED TO [docs.zk.email](https://docs.zk.email). THE FOLLOWING DOCS ARE OUTDATED.

Account recovery allows users to regain access to their Ethereum smart wallets using their email addresses. This system leverages ZK Email technology to verify email replies and trigger account recovery processes, all while maintaining high levels of security and privacy.

Our Account Recovery system is compatible with both [ERC-4337](https://www.erc4337.io/) and [ERC-7579](https://erc7579.com/) standards, making it versatile for various smart wallet implementations.

You can try our account recovery demo at [recovery.prove.email](https://recovery.prove.email/) and read about it at [prove.email/blog/recovery](https://prove.email/blog/recovery).

## Key Features and Benefits

* **Email-based Recovery**: Recover your wallet by simply responding to an email.
* **No Need for Seed Phrases**: Eliminate the risk of losing access due to misplaced seed phrases.
* **Privacy-Preserving**: Utilizes zero-knowledge proofs to maintain user privacy.
* **Customizable**: Developers can define custom recovery logic.
* **User-Friendly**: Simplifies the recovery process for non-technical users.

## How It Works

The Account Recovery system facilitates a secure, email-based recovery process for ERC-7579 compatible smart contract accounts, leveraging ZK Email technology for privacy and security.

### Key Components

1. **Relayer**: An off-chain server facilitating communication between emails and on-chain contracts.
2. **Smart Contracts**: Handle on-chain logic for account recovery.
3. **ZK Email Verification**: Ensures email response authenticity without revealing sensitive information.
4. **Subject Handlers**: Define and validate email subjects for recovery processes.

### Recovery Process Overview

The account recovery process involves four main steps:

1. **Install Recovery Module**: Configure guardians, threshold, recovery timelock, etc.
2. **Accept Guardian**: Guardians confirm control of their email addresses.
3. **Process Recovery**: Guardians approve recovery requests until the threshold is met.
4. **Complete Recovery**: A separate step allowing for recovery delays to protect against malicious attempts.

<figure><img src="../.gitbook/assets/how-works-account-recovery (2).png" alt=""><figcaption></figcaption></figure>

### Detailed Recovery Flow[​](http://localhost:3000/docs/account-recovery/overview#detailed-recovery-flow) <a href="#detailed-recovery-flow" id="detailed-recovery-flow"></a>

1. **User Initiates Recovery**: When a user needs to recover their account, they interact with a front-end application that communicates with the off-chain Relayer.
2. **Relayer Processes Request**: The Relayer, an off-chain component, receives the recovery initiation request. It prepares the necessary data and interacts with the on-chain components.
3. **EmailRecoveryManager.sol Orchestrates**: The Relayer communicates with the EmailRecoveryManager.sol contract, which serves as the central orchestrator for the recovery process. This contract inherits from EmailAccountRecovery.sol, an abstract contract providing core email recovery functionality.
4. **Subject Validation**: The EmailRecoveryManager uses the EmailRecoverySubjectHandler.sol to validate the email subjects related to the recovery process. This ensures that the email commands are correctly formatted and authorized.
5. **Guardian Interaction**: The system then interacts with the EmailAuth.sol contracts, which represent individual guardians. Each guardian has their own EmailAuth instance, preserving privacy and security.
6. **Module Execution**: Once the EmailRecoveryManager has processed the recovery request and received sufficient guardian approvals, it interacts with the EmailRecoveryModule.sol. This module is an ERC-7579 executor module installed on the user's account.
7. **Account Recovery**: The EmailRecoveryModule.sol executes the recovery operation on the 7579 Account. It interacts with the OwnableValidator (a 7579 validator module) to update the account's ownership or access controls as necessary.
8. **Completion**: Once the recovery is executed on the 7579 Account, the process is complete, and the user regains access to their account.

This architecture ensures a modular, secure, and privacy-preserving account recovery process. It combines off-chain components for user interaction and data preparation with on-chain contracts for trustless and verifiable execution, providing a flexible recovery solution for modern Ethereum wallets.
