# Name: Agent Use of Delegation and Interaction Traceability (AUDIT)

# Description
Autonomous and semi-autonomous software agents are increasingly acting on behalf of users across multiple services and administrative domains. These agents interact across multiple administrative or trust domains and can initiate actions without direct human oversight at each step. The increased use of complex agent communications introduces significant challenges for auditability, accountability, transparency. Existing mechanisms, such as system logs, tracing systems, and authorization frameworks, capture individual aspects of system behavior but lack interoperable support for correlating user intent, delegation chains, authorization state, and resulting actions across domains. This creates challenges for fundamental questions required for compliance, operational debugging, and user trust, such as who initiated an action, under which authority it occurred, and how permissions evolved during execution.

To support governance, compliance, transparency, and trust in such environments, auditing is required that collects and correlates evidence across participating domains rather than relying solely on local agent logs, where no single party has complete visibility into a multi-domain interaction. The scope of such auditing is the observable behavior of agents, including user intent, agent or tool interactions, invoked or declined actions, exchanged data, and resulting outcomes across trust boundaries, but not the auditing of the underlying AI model, training data, or inference mechanisms. Cross-domain agent auditing over the whole action chain, including subagents or tool calls in other domains, requires interoperable communication and records containing an identifier to link user intent to resulting system actions across protocol and administrative boundaries.

The AUDIT effort aims to define interoperable protocol mechanisms and data models for auditing and accountability of agents and delegated systems to record, exchange, and verify audit-relevant information across Internet protocols cross all interactions in a communication chain including the user, one or multiple agents or subagents, and tools. This includes an architectural concept, common models for audit records, propagation of audit context across interactions, and integration with existing IETF protocols such as OAuth, HTTP, and attestation and transparency frameworks.

## Required Details
- Status: WG forming (proposed chairs: Yaroslav Rosomakho)
- Responsible AD: SEC ADs
- BOF proponents: Mirja Kühlewind <mirja.kuehlewind@ericsson.com>, Henk Birkholz <henk.birkholz@ietf.contact>, Pam Dingle <Pamela.Dingle@microsoft.com>
- Number of people expected to attend: 100
- Length of session (1 or usually 2 hours): 1.5-2 hours
- Conflicts (whole Areas and/or WGs)
  - Chair Conflicts: TBD
  - Technology Overlap: OAUTH, WIMSE, SCITT, RATS, HTTPbis, Webbotauth, DAWN, AgentProto
  - Key Participant Conflict: SPICE, IOTops, SCONE, MASQUE, QUIC, MAPRG, probably more...

## Information for IAB/IESG
- Any protocols or practices that already exist in this space:
  - OAuth 2.0 (Token Exchange for delegated authorization), e.g. OAuth txn_id, identity/authorization chaining
  - SCITT (transparency service)
  - RATS (remote attestation)
  - HTTP and W3C Trace Context (request correlation and propagation)
  - vCon (conversation record format)
  - WIMSE (workload identifiers)
  - Non IETF protocols:
    -  SSF/CAEP and OpenTelemetry might provide useful building blocks such as https://github.com/open-telemetry/semantic-conventions-genai/blob/main/docs/registry/attributes/gen-ai.md

- Which (if any) modifications to existing protocols or practices are required:
  - Potentially profiles for RATS and SCITT
  - Extensions to HTTP (conext header) and potentially oauth (conext in tokens)
  - If possible, reuse of identifiers proposed by AgentProto
  - Profiling vCon WG Verifiable Agent Conversation Records (vacr)

- Which (if any) entirely new protocols or practices are required:
  - Data model for records
  - Protocol(s) to store and retrieve records in the record store

- Open source projects (if any) implementing this work:
  - Please see following issue on Github: https://github.com/mirjak/audit-bof-preparation/issues/9
  - Consider and discuss collaboration with logging frameworks, such as OpenTelemetry (TBD)

## Agenda
- Intro and Motivation (10 mins)
- Architecture overview und use cases (20 mins)
  - Overview
  - User e-commerce use case
  - Auditing in Identity Management systems
  - Tracking Production Ticketing systems
- Relation to other IETF work (10 mins)
  - Profiling Verifiable Agent Conversation Records (con)
  - SCITT profiling
- Review of proposed charter and discussion (45 mins)

## Links to the mailing list, draft charter if any (for WG-forming BoF), relevant Internet-Drafts, etc.
- Mailing List: audit@ietf.org
- Side meeting at IETF 126: https://github.com/mirjak/audit-bof-preparation/blob/main/IETF-126%20side%20meeting_%20Agent%20Use%20of%20Delegation%20and%20Interaction%20Traceability%20(AUDIT).pdf
- Draft charter: https://github.com/mirjak/audit-bof-preparation/blob/main/audit-charter.md
- Relevant Internet-Drafts:
  - Architecture: https://www.ietf.org/archive/id/draft-kuehlewind-audit-architecture-00.html
  - Solutions:
    - Verifiable Agent Conversation Records: https://www.ietf.org/archive/id/draft-birkholz-verifiable-agent-conversations-00.html
