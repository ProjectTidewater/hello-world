# Project Tidewater

A content-addressed world tree for all human knowledge and identity.

- Self-sovereign identity via libp2p PeerID
- Universal data protocol for any application
- Educational proof of work economy
- Equal opportunity by design

## Status
Active development. Core tree engine working.
Follow the journey: (https://www.facebook.com/ProjectTidewater/)

## Vision
The internet was supposed to democratize knowledge and opportunity. Instead data became the property of corporations, identity became controlled by platforms, and billions of people were left behind by systems designed for those who already had power and resources.
Project Tidewater is built on a simple belief — that every human being deserves equal access to their own data, their own identity, and the opportunity to participate in and benefit from the global digital economy.
At its core Project Tidewater is a content-addressed world tree — a universal data structure where any application can store and retrieve any kind of data, where every person owns their own identity, and where contributing to the network is rewarded fairly regardless of wealth, nationality, or circumstance.
The principles are straightforward:
Every piece of data has a permanent, verifiable address. No corporation owns it. No platform can delete it. It belongs to whoever created it.
Every person has a self-sovereign identity rooted in cryptographic keys they control. Not an email address owned by Google. Not a username owned by Facebook. A PeerID that is mathematically and irrevocably yours.
Every contribution to the network is rewarded equally at the base level. A student in rural Philippines running a Raspberry Pi earns the same base rate as anyone else on the network. Wealth buys no advantage.
Education is not a privilege — it is the foundation of the economy. Learning, teaching, and contributing knowledge are first class activities that the network recognizes and rewards.
Any application can participate. Drupal, Moodle, or anything yet to be built — if it speaks the protocol it can read and write to the tree. No vendor lock-in. No proprietary silos. The data belongs to the user not the application.
The long term goal is ambitious:
Every app. All data. On the tree.
Not because it is easy. Because it's the right thing to do.


## Architecture

Project Tidewater is built on a small number of powerful ideas that compose naturally into a global system.

**The World Tree**

All data lives in a content-addressed Merkle DAG — a tree where every node has a cryptographic identifier (CID) derived from its content. Change the content and the CID changes. This makes data permanently verifiable, tamper-evident, and location-independent. Any node on the network can verify any piece of data without trusting a central authority.

Data is organized into a hierarchical path structure that reflects the real world:

```
usa/california/la/usc/drupal_limrock/student/v1/798
```

Geography, institution, application, entity type, version, and identity — all encoded in the path. Any application that knows the path can find the data. Any cluster that holds the branch can serve it.

**Schemas**

Every entity type is defined by a schema stored on the tree itself. Schemas describe the fields, types, and structure of entities. Any application that wants to write data to the tree registers its schema first. This makes the tree self-describing — you don't need external documentation to understand what the data means.

**Identity**

Every person on the network has a PeerID — a cryptographic identity rooted in keys they generate and control. No corporation issues it. No government controls it. It is mathematically yours.

Key management follows a two-tier model:
- A master key generated on a dedicated offline device, used only to issue or revoke delegated keys
- A delegated signing key for day to day operations

If a delegated key is compromised the master key revokes it and issues a new one. If the master key is lost, social recovery allows trusted peers to attest identity and authorize a new master key. The history of key rotations is itself stored on the tree, permanently auditable.

One person. One PeerID. One node. Wealth buys no advantage.

**Applications**

Any application can participate in the world tree by speaking the protocol. Drupal, Moodle, or anything yet to be built registers its schemas, ingests its entities, and reads data back through the tree. The data belongs to the user not the application. Switching applications does not mean losing your data.

Relationships between applications are resolved through PeerID — the universal join key across the entire network. A student's profile in Drupal and their course enrollments in Moodle are linked by the same PeerID, queryable through a view that spans both applications.

**The Oracle Hierarchy**

The network is sustained by nodes operated by real people. One person, one node — no exceptions. To incentivize early infrastructure investment the network recognizes a hierarchy of Oracles who commit more resources and earn proportionally more during the network's first 40 years.

There are a limited number of Oracle slots at each tier, ensuring the hierarchy remains meritocratic and accessible rather than captured by wealth.

After 40 years all proof of work equalizes at the base rate. Oracles transition to a service fee model, operating as decentralized infrastructure providers in a competitive market.

**The Economy**

Proof of work is human. Only verified human PeerIDs can earn. Machines, institutions, and devices have PeerIDs but cannot participate in proof of work. This ensures the economy rewards people not capital.

In the early years proof of work is primarily network contribution — storing data, relaying blocks, maintaining uptime. As the network matures educational proof of work becomes increasingly important — completing courses, passing assessments, teaching others, contributing knowledge.

Coins are spent in the marketplace — on courses, credentials, services, and anything else participants offer. The economy is circular and self-sustaining.

The total coin supply is designed to approach the number of Bitcoin Satoshis at year 40, after which a 2.5% annual inflation rate sustains the economy and rewards continued participation without the deflationary hoarding incentive of fixed supply currencies.

**The Foundation**

Project Tidewater is built on:
- libp2p for peer discovery and networking
- IPFS content addressing primitives
- CBOR and DAG-CBOR for efficient binary encoding
- BoltDB for local state persistence
- A custom Merkle pipeline for tree management

It is designed to run on a Raspberry Pi. But it can run on anything.







