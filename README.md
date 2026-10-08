
# FedPQAuth ProVerif Verification

This repository contains the formal verification models of the **FedPQAuth protocol** implemented using **ProVerif**.

The purpose of this implementation is to formally analyze and verify the main security properties of FedPQAuth under the Dolev–Yao adversary model.

## Tool

The protocol is modeled and verified using:

- **ProVerif version 2.05**

ProVerif is an automated formal verification tool for analyzing security protocols based on symbolic cryptographic models.

## Protocol

**FedPQAuth** is a post-quantum continuous authentication protocol designed for Hierarchical Federated Learning (HFL).

The protocol integrates:

- Post-quantum key establishment using ML-KEM
- Static authentication
- Continuous authentication
- Hierarchical authentication between Client, Cluster Head, and Cloud Server
- HKDF-based key derivation
- Separate behavior and model/data security planes
- Session- and round-based key derivation
- Trust-aware continuous authentication

## ProVerif Model

The main ProVerif model represents the core FedPQAuth protocol in normal operation mode.

The modeled entities are:

- Client (`C`)
- Cluster Head (`CH`)
- Cloud Server (`CS`)

The model includes the following phases:

1. Client and Cluster Head registration
2. Static authentication
3. ML-KEM-based shared-secret establishment
4. HKDF-based key derivation
5. Behavior-plane key establishment
6. Data/model-plane key establishment
7. Continuous authentication
8. CH-to-CS authenticated reporting

The public communication channels are controlled by a Dolev–Yao attacker, while registration is modeled over private channels.

## Verified Security Properties

The ProVerif model verifies several security properties of FedPQAuth, including:

### Secrecy

The model verifies the secrecy of:

- Client real identity (`RID`)
- Client identity key (`K_id`)
- Client registration secret
- Cluster Head registration key
- Client–Cluster Head shared secret
- Client–Cloud Server shared secret
- Cluster Head–Cloud Server shared secret
- Behavior-plane derived keys
- Data/model-plane derived keys

### Authentication

Correspondence queries are used to verify authentication between the participating entities, including:

- Client registration authentication
- Cluster Head registration authentication
- Client authentication at the Cluster Head
- Client authentication at the Cloud Server
- Cluster Head authentication at the Cloud Server
- Cloud Server authentication at the Cluster Head
- Cluster Head authentication at the Client
- Cloud Server acknowledgment authentication at the Client

### Continuous Authentication

The model also verifies that:

- A continuous authentication message accepted by the Cluster Head originates from the authenticated Client.
- A continuous report accepted by the Cloud Server originates from the authenticated Cluster Head.

## Key Derivation

FedPQAuth derives separate cryptographic material for the behavior and data/model planes.


