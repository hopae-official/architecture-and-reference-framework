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

The wallet ecosystem brings together roles, responsibilities, and lifecycle controls that collectively enable trustworthy issuance, storage, and presentation of credentials at a global scale. A single user device may host multiple Wallet Units from one or more providers, with each Wallet Unit expected to operate independently and meet the ecosystem’s requirements for trust and interoperability.

[Diagram Description: Ecosystem map. Nodes: User, Wallet Instance (WI), Wallet Secure Cryptographic Application (WSCA), Wallet Secure Cryptographic Device (WSCD), Wallet Provider Backend (WPB), Issuer(s), Relying Party Instance (RPI), Intermediary, Trust Registry, Schema/Rulebook Registry, Remote Signing Service. Edges are labeled with interface names (PI, PII/AII, WPI, SCI, WWI, RSI).]

### 3.2 Roles

#### 3.2.1 User

The User (a natural person or authorized representative of a legal entity) is the primary controller of the Wallet Unit. Users can review attributes requested by relying parties, give informed consent for each request, and later consult interaction logs. Wallets also provide mechanisms for reporting suspicious requests and, where applicable, requesting deletion of data from relying parties.

#### 3.2.2 Wallet Provider (WP)

The Wallet Provider develops and operates the Wallet Instance, the WSCA, and the supporting backend services. Providers are responsible for secure management of cryptographic keys in or via the WSCD throughout the lifetime of the Wallet Unit. They also issue Wallet Unit Attestations (WUAs), which describe the security properties of the WSCD and related certifications.

#### 3.2.3 Issuer

Issuers create and sign credentials such as foundational IDs or professional licenses. Issuers are registered in a Trust Registry and issue credentials only within their declared attribute scope, in line with the Rulebooks that govern credential types.

#### 3.2.4 Relying Party (RP)

A Relying Party requests and verifies attributes to deliver services. RPs are registered entities and authenticate requests using Access Certificates linked to a Trust Anchor. Wallet Units validate RP identity, the authenticity and integrity of the request, and certificate chain validity before seeking user approval.

#### 3.2.5 Intermediary

An Intermediary acts as a delegate that represents multiple RPs. Intermediaries register independently, use their own Access Certificates, disclose both their own identity and that of the ultimate RP to the user, and are expected to delete relayed data immediately after use.

#### 3.2.6 Trust Service Provider (TSP)

Trust Service Providers offer services such as signature creation and validation, timestamping, and—where relevant—remote signing or sealing.

#### 3.2.7 Schema Registry & Attribute Schema Providers

A Schema Registry publishes controlled vocabularies and attribute schemas. Attribute Schema Providers define Attestation Rulebooks specifying schema, proof mechanisms, and protocol choices. Multi-stakeholder bodies are encouraged to maintain sector-wide or cross-border Rulebooks to avoid divergent semantics.

#### 3.2.8 Governance Authority

The Governance Authority maintains Trust Registries for Wallet Providers, Issuers, RPs, and Intermediaries. It also oversees certification processes and incident response across the ecosystem.

### 3.3 Privacy & Security Governance

Interoperability and Privacy by Design: Ecosystems rely on common standards and profiles to avoid fragmentation and enable selective disclosure and data minimization by default.

Transparency: Wallets display the identity of the RP, purpose of the request, requested attributes, and any intermediary involvement before user approval.

User Remedies: Wallets include functions for users to request deletion of data from RPs and report suspicious requests.

### 3.4 Rulebooks & Catalogues

Each attestation type (e.g., PID, mDL, diploma) is described by an Attestation Rulebook, which specifies its attribute schema, proof mechanisms, and protocol profiles for issuance and presentation.

A Catalogue of Rulebooks and controlled vocabularies supports consistency, reduces divergence, and enables reuse across sectors. Rulebooks may be sector-wide or organization-specific, with cross-sector governance encouraged to prevent fragmentation.

[Diagram Description: Registry diagram showing Trust Registry (for actors & certificates) and Rulebook/Schema Catalogue (for semantics), with governance workflows for registration, updates, and deprecation.]

## 4. High-Level Architecture

### 4.1 Reference Architecture & Components

The reference architecture decomposes a Wallet Unit into common components and interfaces. The Wallet Unit consists of the User Device, Wallet Instance, WSCA, and WSCD. WSCD options include remote HSMs, external tokens or smartcards, embedded secure elements (SE/eSIM), and OS-backed cryptography.

[Diagram Description: Layered reference architecture (based on EUDI Figure 2). Layers: (1) User & UI; (2) Wallet Instance; (3) WSCA; (4) WSCD; (5) Provider Backend; (6) Ecosystem services (Issuers, RPs, Intermediaries, Trust & Schema registries).]

#### 4.1.1 Wallet Instance

Implements business logic, user interface, and coordination of secure use of WSCA/WSCD.

#### 4.1.2 Wallet Secure Cryptographic Device (WSCD)

A tamper-resistant environment for key storage and cryptographic operations. Possible implementations include remote HSMs, external tokens, embedded secure elements, or OS-native APIs. Providers ensure that chosen architectures meet required security levels, manage keys throughout their lifecycle, and include WSCD certifications in Wallet Unit Attestations.

#### 4.1.3 Wallet Secure Cryptographic Application (WSCA)

Acts as a mediator between the Wallet Instance and the WSCD. Its form depends on the WSCD type, e.g., a Java Card applet for eSIMs or SEs, firmware for HSMs, or OS-native APIs.

#### 4.1.4 Provider Backend

Supports the Wallet Instance by providing attestations, maintenance, and privacy-preserving telemetry based on user consent.

### 4.2 Interfaces

#### 4.2.1 Presentation interface

For remote interactions between relying-party software and wallet units, ecosystems commonly adopt OpenID for Verifiable Presentations in combination with the Digital Credentials API so that invocation, origin binding, and session context are handled consistently across platforms. For proximity interactions (for example near-field communication, Bluetooth Low Energy, or optical codes), ecosystems typically follow International Organization for Standardization and International Electrotechnical Commission standard 18013-5 for authenticated and encrypted channels. Wallet-to-wallet interactions can reuse the same presentation interface patterns.

#### 4.2.2 Secure cryptographic interface

This is the interface between the wallet unit and the wallet secure cryptographic application. Its design and bindings are implementation-specific and may vary by platform and cryptographic substrate.

#### 4.2.3 Wallet secure cryptographic application–wallet secure cryptographic device interface

This interface links the application layer managing cryptographic operations with the underlying secure device or module. It is defined by the manufacturer or provider and is not specific to any one ecosystem profile.

#### 4.2.4 Issuance interfaces for person identification data and other attestations

Issuance commonly uses OpenID for Verifiable Credential Issuance, covering proof of possession, issuance responses, and secure storage within the wallet’s cryptographic environment.

#### 4.2.5 Remote signing and sealing interface

Where qualified remote signatures or seals are required, the wallet connects to remote signature and seal service providers through a dedicated interface that supports strong authentication, signature creation, validation, and timestamping.

### 4.3 WSCD Architecture Types

- Remote WSCD: HSM managed on secure servers used when devices lack secure hardware.
- Local External WSCD: Smartcard or secure token performing cryptographic functions.
- Local Internal WSCD: eSIM or embedded secure element.
- Local Native WSCD: OS-integrated cryptographic APIs.
- Hybrid: Combination of the above.

Security models typically combine device possession with a knowledge factor (PIN/password), verified inside the WSCD/WSCA or via secure channels for remote implementations.

### 4.4 Presentation Flows

#### 4.4.1 Remote (Same Device)

A browser or app invokes the Wallet via the DC API, the user approves the request and the Wallet returns an encrypted response to the relying party.

#### 4.4.2 Remote (Cross Device CTAP 2.2 Hybrid)

A browser displays a QR code, the user scans it with their Wallet device, establishing a secure channel (via BLE proximity checks). The OpenID4VP request is transmitted through the tunnel, and the Wallet returns an encrypted response.

#### 4.4.3 Proximity (Online/Offline)

Proximity interactions (e.g., NFC, BLE, QR) follow ISO/IEC 18013-5.

## 5. Data Model and Data Exchange Protocols

### 5.1 Credential Formats

#### 5.1.1 ISO/IEC 18013-5 / -7 (mDL and generalized mobile documents)

Defines CBOR attribute schemas, selective disclosure mechanisms, and device binding. Though initially designed for mDLs, the model can be extended to other credential types with appropriate schemas.

#### 5.1.2 SD-JWT VC

Uses JSON-based credentials with selective disclosure supported by salted-hash mechanisms. Profiles such as HAIP are needed for interoperability.

#### 5.1.3 W3C VCDM 2.0

Provides an abstract data model but leaves cryptographic mechanisms and transports to companion specifications. Interoperability requires clear profile definitions within Rulebooks.

### 5.2 Presentation Protocols

- Proximity: ISO/IEC 18013-5.
- Remote (same/cross device): OpenID4VP, with CTAP 2.2 hybrid for cross-device channels.

### 5.3 Issuance Protocols

OpenID4VCI is the common protocol for issuing PID and other attestations.

### 5.4 Attribute Schemas & Rulebooks

Each attestation type is linked to a Rulebook defining schema, proof mechanisms, and protocol bindings. Multi-stakeholder governance helps avoid duplication and promotes reuse.

### 5.5 Status, Revocation, Refresh, and Binding

Credentials can be validated through status checks and revocation mechanisms. Offline credentials should be short-lived and refreshed regularly. Presentations are bound to the holder device or Wallet, ensuring authenticity.

### 5.6 DC API

The W3C Digital Credentials API aims to standardize Wallet invocation and strengthen phishing and relay resistance by binding origin and session context.

## 6. Relying Party (RP) Registration and Intermediaries

This section explains how relying parties and intermediaries participate in the ecosystem from registration through day-to-day operation. Registration establishes legal identity, declares intended uses and attribute needs, and results in the issuance of per-instance access credentials that authenticate interactions with wallet units. A single relying party may operate multiple software or hardware endpoints each endpoint is treated as a distinct relying-party instance with its own access credentials.

### 6.1 Relying-party registration

Before requesting attributes from wallet units, a relying party registers with the trust registry maintained by the relevant governance authority or registrar. During registration, the relying party provides its legal identity, contact details, and a clear declaration of intended uses and the attributes it expects to request for each use case. If the relying party will operate through an intermediary, that relationship is declared at registration time as well. Upon successful vetting, each relying-party instance is issued an access certificate that it will use to authenticate presentation requests. If the relying party’s registration is later suspended or cancelled, the associated access certificates are revoked and wallet units are expected to reject new requests originating from those instances.

### 6.2 Authentication and authorization of requests

For every interaction, the relying-party instance authenticates with its access certificate. Wallet units validate the certificate chain to a trust anchor, check status and revocation, and evaluate that the attributes requested are consistent with the relying party’s registered purposes. Prior to user approval, the wallet presents a clear summary showing the verified name and legal identifier of the relying party, the stated purpose, and the specific attributes requested. Remote interactions bind the request to origin and session context, while proximity interactions rely on authenticated and encrypted channels defined by the proximity presentation model.

### 6.3 Intermediaries

An intermediary is a relying party that fronts other relying parties. It registers in the trust registry and uses its own access certificate when initiating requests to wallet units. Every request includes both the intermediary’s identity and the identity of the downstream relying party on whose behalf it is acting, and wallet user interfaces display both so the user can make an informed decision. The intermediary ensures that each downstream relying party is properly registered and that the registry records the association. Depending on contractual arrangements, the intermediary may perform certain verification steps—such as cryptographic validation or status checks—before forwarding results. In all cases, data minimization applies: attributes relayed to the end relying party are deleted by the intermediary immediately after transmission or upon verification failure, and no shadow transaction records of the attribute contents are retained.

### 6.4 Wallet user interface and post-transaction user rights

Wallet applications maintain a local, user-visible history of requests and presentations that records when a request occurred, which relying party (and intermediary, if any) was involved, and which attribute categories were requested. From this history view, users can report suspicious activity to the appropriate authority and initiate deletion requests to relying parties using the contact information published in the registry. These capabilities reinforce transparency and give users practical remedies when issues arise.

## 7. Trust Model

### 7.1 Conceptual Model

The Trust Model anchors all participants—Wallet Providers, Issuers, RPs, Intermediaries—to trust anchors published by governance authorities. Entities authenticate with Access Certificates, while Wallet Units present attestations managed by their providers.

### 7.2 Lifecycle Trust

#### 7.2.1 Wallet Solution and Wallet Unit

Wallet Solutions progress through candidate, valid, and suspended states. Wallet Units associated with suspended or cancelled solutions are no longer accepted.

#### 7.2.2 Issuers and Trust Lists

Issuers are registered and their trust anchors placed in Trusted Lists. Suspension or cancellation invalidates their credentials.

#### 7.2.3 Relying Parties

RPs are registered entities with Access Certificates for each instance. Suspension revokes certificates and prevents interaction.

#### 7.2.4 Intermediaries

Intermediaries act as RPs, register accordingly, and ensure each downstream RP is registered.

### 7.3 Wallet Unit Attestation (WUA)

Wallet Unit Attestations identify Wallet Units to Issuers and others, supporting issuance and lifecycle management. Providers manage attestations over time and ensure revocation mechanisms are available.

### 7.4 Authorization Boundaries and Entitlements

Entitlements specify what Issuers may issue, maintained in Registries or Registration Certificates. Wallets and RPs verify entitlements before accepting credentials.

### 7.5 Revocation & Suspension Propagation

Suspension or cancellation of Issuers, RPs, or Wallet Providers results in revocation of certificates and attestations. Ecosystem participants are expected to reject interactions with revoked entities.

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
