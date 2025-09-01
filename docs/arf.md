# Architecture and Reference Framework

## 1. Introduction

### 1.1 Background

In digital environments, secure and trustworthy identity is a fundamental enabler for accessing services, conducting transactions, and exchanging data among individuals, organizations, and devices.
As a result, governments, international bodies, and industry stakeholders have been developing a variety of digital identity standards and technologies. Examples include Decentralized Identifiers (DIDs), Verifiable Credentials (VCs), Public Key Infrastructure (PKI), and electronic identity (eID) frameworks, all designed to address this growing need.

However, these standards and implementations are often built on different technical foundations and regulatory assumptions, which leads to fragmentation and silos when applied globally. To ensure that digital identity ecosystems can scale and operate effectively across borders, there is a strong need for a common reference architecture and set of requirements that guarantee interoperability beyond jurisdictions and technologies.

### 1.2 Purpose of the document

The purpose of this document is to provide a reference architecture and framework for digital identity ecosystems.
It is intended to:

- Define common principles, roles, and high-level requirements for digital identity systems.
- Serve as a technology-neutral and jurisdiction-agnostic reference, applicable across different contexts worldwide.
- Support governments, organizations, and service providers in designing, adopting, and implementing digital identity solutions in a secure, privacy-preserving, and interoperable way.

Rather than prescribing detailed technical implementations or legal rules, the document aims to act as a guidance and reference point for stakeholders who are planning or developing digital identity infrastructures.

### 1.3 Scope

#### In Scope

- Definition of conceptual architecture and high-level requirements for digital identity ecosystems
- Description of roles and functions such as Identity Holder, Identity Provider (IdP), and Relying Party (RP)
- References to technical components such as DIDs, VCs, PKI, and their applicability
- Governance framework, including trust models, policies, and compliance requirements
- Representative use cases demonstrating the application of digital identity systems
- Principles and guidelines to support interoperability, security, and privacy protection

#### Out of Scope

- Detailed technical implementations of specific technologies
- Jurisdiction-specific legal and regulatory compliance details
- Designs tied to vendor-specific solutions or platforms
- Operational procedures and management guidelines for deployment

### 1.4 Terminology

See [Appendix A](appendix/a.terminologies.md) for the list of terms used in this document.

## 2. Wallet Functionalities

This chapter describes the core functionalities of digital identity wallets within broader identity ecosystems. Wallets serve as secure, user-controlled environments that allow individuals and organizations to manage and present identification data and credentials across both public and private services.

The functionalities outlined here are centered on principles of security, privacy, and user empowerment. They illustrate how wallets can support real-world interactions such as accessing government services, proving qualifications, or conducting payments while ensuring trust, interoperability, and protection of personal data.

### 2.1 Identification and Authentication

Digital wallets enable individuals to authenticate themselves across a wide range of services, from community platforms to government portals and financial institutions. Authentication can combine possession of the device with additional factors such as biometrics or PINs, giving flexibility across different assurance levels. Users also benefit from transparency through access to their authentication and transaction history.

### 2.2 Attribute Presentation with Selective Disclosure

Wallets allow users to share only the specific information required by a relying party. For example, when proving age, a user can disclose “over 18” without revealing their full date of birth. This selective disclosure enhances privacy, while cryptographic mechanisms ensure that activity cannot be correlated across different services.

### 2.3 Digital Signature

Wallets provide the ability to create digital signatures for agreements, transactions, or approvals. These signatures can be bound to specific contexts such as a contract amount, counterparty, or date ensuring integrity, legal validity, and trust in digital interactions.

### 2.4 Pseudonyms

Wallets can generate service specific pseudonyms that allow users to engage with different platforms without being tracked across them. This supports privacy preserving authentication while still enabling strong security, for example through integration with passkeys or WebAuthn.

### 2.5 Organizational Wallet

In addition to personal use, wallets can represent organizations and allow delegation of rights. An employee may act on behalf of their company, or a public official may sign a document in the name of their agency. Such delegations are verifiable, providing clarity and accountability in organizational processes.

### 2.6 Payment

Wallets can integrate identity with payment capabilities, enabling streamlined experiences where verification and payment occur in one flow. Examples include online shopping, where a user verifies their age, completes payment, and confirms delivery details all within the wallet, or paying public fees through digital currency or open banking connections.

### 2.7 Travel and Mobility

Wallets can hold credentials related to travel and mobility, such as electronic passports, visas, or driving licenses. Travelers may use their wallet for identity verification at airport checkpoints or to confirm driving eligibility when renting a car. This reduces reliance on physical documents and creates more seamless travel experiences.

### 2.8 Health Credentials

Wallets can securely store and present health-related credentials, such as vaccination records, insurance entitlements, or medical summaries. These can be used for international travel, accessing healthcare services, or simplifying insurance verification. Users gain efficiency while maintaining control over sensitive health information.

### 2.9 Education and Professional Qualifications

Wallets can carry digital representations of diplomas, transcripts, and professional licenses. Graduates can quickly prove their degrees to employers, and professionals can demonstrate their qualifications abroad. This reduces fraud, streamlines hiring, and builds trust in educational and professional achievements.

## 3. Wallet Ecosystem

TBD

## 4. High-Level Architecture

TBD

## 5. Data Model and Data Exchange Protocols

TBD

## 6. Relying Party (RP) Registration and Intermediaries

TBD

## 7. Trust Model

TBD

## 8. Assurance Levels

TBD

## 9. Risk Management

TBD

## 10. Certification

TBD

## 11. References

TBD

## 12. Appendices

TBD
