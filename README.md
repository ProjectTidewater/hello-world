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

Current entity types include students, teachers, courses, events, media, comments, clubs, sports, games, tournaments, achievements, UI components, templates, views, and credentials. Any entity type can be defined and registered by any application.

**Identity**

Every person on the network has a PeerID — a cryptographic identity rooted in keys they generate and control. No corporation issues it. No government controls it. It is mathematically yours.

Key management follows a two-tier model:

- A master key generated on a dedicated offline device, used only to issue or revoke delegated keys
- A delegated signing key for day to day operations

If a delegated key is compromised the master key revokes it and issues a new one. If the master key is lost, social recovery allows trusted peers to co-sign a key rotation request through Shamir's Secret Sharing or web of trust attestation. The full history of key rotations is stored on the tree — permanently auditable and cryptographically verifiable.

One person. One PeerID. One node. Wealth buys no advantage.

Institutions and devices also have PeerIDs for signing and verification purposes but cannot participate in proof of work. Identity is human.

**The Registry**

A global registry branch maps PeerIDs to their entity paths across all applications:

```
registry/peers/PEER-809/drupal_limrock → usa/california/la/usc/drupal_limrock/student/v1/798
registry/peers/PEER-809/moodle → usa/california/la/usc/moodle/user/v1/445
```

This makes PeerID the universal join key across all applications. A view that spans Drupal, Moodle, or any other application resolves relationships through the registry without applications needing to know about each other.

**Applications**

Any application can participate in the world tree by speaking the protocol. Drupal, Moodle, or anything yet to be built registers its schemas, ingests its entities, and reads data back through the tree. The data belongs to the user not the application. Switching applications does not mean losing your data.

The first reference implementation is a Drupal school yearbook application — student profiles, event photos, sports records, club activities, graduation videos, and comments — all stored permanently on the tree with content-addressed media that can never be lost or altered.

**Views**

Views are first class entities on the tree. A view defines a query — what entity types to retrieve, how to filter them, how to sort them, how to aggregate them, and how to display them. The router executes views against the in-memory tree, following relationships through the registry to join data across multiple applications.

Views support:
- Field selection and filtering
- Sorting and pagination
- Relationships across entity types and applications
- Aggregation and grouping
- Exposed filters for user-driven queries
- Multiple display modes

**UI Components and Templates**

Page layout is data-driven. UI components are entities on the tree that define which blocks appear in which regions on which routes, for which roles, in what order. Templates are entities that define how data is rendered. Changing a page layout means ingesting new UI component entities — no code deployment required.

**The Oracle Hierarchy**

The network is sustained by nodes operated by real people. One person, one node — no exceptions. To incentivize early infrastructure investment the network recognizes a hierarchy of Oracles who commit more resources and earn proportionally more during the network's first 40 years.

Oracle tiers consist of 262,144 nodes each — a number that is itself a power of 2 (2^18) — earning from 2^13 coins per hour at the highest tier down to 2^2 coins per hour, with all other participants earning 3 coins per hour base rate.

After 40 years all proof of work equalizes at the base rate. Oracles transition to a service fee model, operating as decentralized infrastructure providers in a competitive market. The total coin supply at year 40 is designed to approach the number of Bitcoin Satoshis, assuming global participation of 9-10 billion people.

Thereafter a 2.5% annual inflation rate sustains the economy, encourages circulation over hoarding, and rewards continued participation.

**The Economy**

Proof of work is human. Only verified human PeerIDs can earn. Machines, institutions, and devices cannot participate in proof of work regardless of resources. This ensures the economy rewards people not capital.

Proof of work tasks are specifically designed to resist automation:

- Real time information gathering requiring physical presence
- Human verifiable content creation demonstrating genuine authorship
- Video proof of real world activities over verified time periods
- Wiki contributions, editing, and fact-checking
- Community participation requiring genuine understanding
- Educational activities — completing courses, passing assessments, tutoring others
- Peer attestation — verifying the humanity and identity of others

Educational proof of work follows a completion-time model. Domain experts set a benchmark completion time for each course. Students earn coins for actual time spent learning up to the benchmark maximum. Rushing through earns less. Taking longer than the benchmark earns no additional coins. Genuine learning is rewarded. Gaming is not.

Course verification uses a 100% comprehension model for objective knowledge — videos pause at key moments requiring correct answers before continuing. Incorrect answers require rewatching. Only verified comprehension time counts toward earnings.

Human verified proof of work — essays, practical skills, creative work, teaching — is validated by tutors, teachers, and domain experts who themselves earn coins for verification.

**Credentials**

Credentials are entities on the tree, cryptographically signed by verifying peers and institutions. They are permanently verifiable, portable across any application, and linked to the student's PeerID not to any institution's database.

Some credentials require periodic renewal as knowledge evolves. Foundational credentials never expire but can be optionally retaken after a minimum time period has passed, earning additional coins for genuine relearning.

The credential hierarchy reflects demonstrated competence:
- Learner — completed verified coursework
- Tutor — demonstrated knowledge, peer verified
- Teacher — sustained contribution, expert verified
- Domain Expert — highest credential, governance participant

**Knowledge Quality**

All content on the tree can be rated. Ratings are transparent, attributable, and timestamped. Domain experts carry the highest rating weight in their field. Teachers carry weight for educational content. Community ratings reflect broader sentiment.

Nothing is suppressed or deleted. Rating history is preserved — you can see how expert consensus on any topic evolved over time. Experts can update their ratings as understanding changes. The velocity and direction of rating changes signals shifting consensus and can trigger governance review.

Assessment questions are contributed by teachers and domain experts, rated for quality by the community, and validated by statistical performance data. Questions that consistently confuse students who otherwise pass are flagged for review.

**Governance**

Project Tidewater governance is hierarchical and meritocratic:

- **Core Protocol Council** — long term contributors with demonstrated commitment. Fundamental protocol changes require their approval.
- **Domain Governors** — experts responsible for specific domains. Education, economics, technical infrastructure, identity.
- **Oracle Validators** — infrastructure contributors with governance weight proportional to but capped by their tier.
- **Community Voice** — every human PeerID has equal vote on community matters.

  Everyone earns their position but must continuosly earn it also. Anyone can be replaced by lack of performance or vote. That includes the Governance and Oracle structure.

Proof of work validity is governed by domain experts who determine what tasks qualify, what they are worth, and how they are verified. As AI capabilities advance the governance system evaluates and updates valid proof of work tasks to maintain genuine human resistance. The governance system is itself the immune system against AI capture of the economy.

**The Technical Foundation**

Project Tidewater is built on:
- libp2p for peer discovery and networking
- IPFS content addressing primitives
- CBOR and DAG-CBOR for efficient binary encoding
- BoltDB for local state persistence
- A custom Merkle pipeline for tree management
- Go for the core engine

It is designed to run on a Raspberry Pi. But it can run on anything.

--- 







