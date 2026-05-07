Executive Summary
The shift from generative AI that suggests content to agentic AI that interacts with services, tools,
and other agents is redefining the enterprise workforce. Autonomous AI agents are moving from
experimental sandboxes to automating core business processes, creating a new, urgent challenge for
security teams.
This new technological capability introduces a new dimension of risk, fundamentally changing how it
must be calculated and managed. To perform meaningful work, an agent requires access to critical
systems. The current, flawed practice is to grant this by allowing the agent to inherit the persistent,
privileged credentials of a human user. This unsustainable model creates an entity that, if compromised,
can trigger cascading operational failure with unprecedented speed and scale. The critical question
for leaders has shifted from if they will deploy agents to how they will architect the fundamental trust
required to grant them autonomy.
This paper deconstructs the novel threat surface of agentic AI and presents a strategic framework
for its defense. This architecture moves beyond piecemeal solutions to provide integrated visibility,
real-time prevention, and scalable governance. It reframes the security function from a reactive
gatekeeper to a proactive enabler of trust, responsible for engineering the verifiable systems and
governance that make autonomous operations possible.
2
2
The New Enterprise Operational Reality
For years, automation was defined by rigid, brittle scripts, but agentic AI fundamentally alters this
equation. Consider a supply chain disruption where a traditional system merely sends an alert for a
human to handle. In contrast, an AI agent executes the entire response: it interprets the alert, queries
inventory systems to identify at-risk orders, accesses logistics platforms to find alternative routes,
negotiates with supplier APIs, and updates the ERP—completing in minutes a process that would take a
human hours.
This is the tangible value of agentic AI: the compression of complex, multi-domain workflows into
autonomous, real-time actions. This capability, however, exposes a critical paradox. The agent in our
example requires permissions to core operational systems, becoming a single point of failure with an
immense blast radius. Granting such privileged access without a new model of oversight creates a
catastrophic liability, which is why a new model of governance built for systems that can reason, learn,
and act on their own is required.
3
An AI Agent Primer: The New Digital
Workforce
At its core, an AI agent is a software system designed to operate with significant autonomy to achieve a
specific goal. This represents a fundamental leap beyond familiar tools like chatbots. Think of a chatbot
as a research librarian; it is primarily reactive, expertly finding and presenting information in response
to a user's query. An agent, by contrast, is a proactive project manager capable of driving end-to-end
execution. It perceives its environment, reasons through complex information, formulates multi-step
plans, and takes tangible actions across multiple systems without constant human supervision. As
the engine of true automation, agents matter because they bridge the gap between digital insight and
business outcomes, moving AI from a tool for suggestion to a core component of operations.
The Cognitive Core and its Flaws
An agent’s power comes from its sophisticated cognitive architecture, where each component that
grants it autonomy also introduces a specific, corresponding vulnerability. Understanding this anatomy
is the first step to securing it.
LLM "Brain": The agent's reasoning is powered by a foundation model that provides advanced
natural language understanding and problem-solving capabilities. However, this engine is
susceptible to manipulation through prompt injection attacks, which can overwrite its original
instructions and hijack its core logic.
Perception Module: This is the agent's sensory system, responsible for ingesting and interpreting
multimodal data from emails, documents, APIs, and databases. This intake valve can be targeted
with poisoned information, where a malicious command is hidden within a seemingly benign
document or webpage. When the agent processes the file, it unwittingly executes the hidden,
harmful instruction.
Planning Module: The strategist of the agent decomposes a high-level goal into a sequence
of smaller, executable sub-tasks. An attacker can subvert this logic, tricking the agent into
creating a flawed plan that appears sound but includes steps that subtly exfiltrate data or grant
unauthorized access as part of the workflow.
4
Memory: An agent learns from a combination of short-term (working) memory for its current task
and long-term memory that archives past interactions. This learning center can be corrupted
through memory injection attacks, where an attacker plants false information or malicious
procedures. The agent later recalls this "fact" as truth, causing it to make flawed decisions or take
harmful actions in future, unrelated tasks.
Tools (APIs): If the LLM is the brain, tools are the agent's hands. These are the functions and
APIs it calls to interact with the world and execute tasks. An agent's tools can be turned against
it, tricking it into misusing its legitimate permissions to perform malicious deeds. For example, an
agent could be tricked into using an authorized send_email tool for a phishing campaign or an
execute_query tool to delete critical data.
A Fragmented, Unmanaged Agentic Workforce
This new digital workforce is a fragmented ecosystem that presents immense security and governance
challenges, appearing everywhere, often outside of IT's direct control:
Source Description Example Agent
Private Agents
Self-hosted agents (whether from open-
source or commercial software) that run
entirely on your own private infrastructure
(e.g., your AWS VPC or on-prem servers).
You control the entire stack.
A custom invoice processor built on LangChain runs
on an internal server.
Agents as a Service/
Agent Marketplace Agentic capabilities consumed from a third-
party vendor via APIs or hybrid clients (local
software connected to a cloud backend).
You control the data you send, but not the
agent's core environment.
A developer uses a tool like Cursor IDE that connects
to a remote AI model to assist with coding.
SaaS Embedded
Agents
Agents that are native features within a
larger SaaS application (e.g., CRM, ITSM,
ERP). The agent's runtime is a "black box"
managed entirely by the SaaS vendor.
A support team uses a ServiceNow agent to automate
IT ticket resolution.
5
The Communication Fabric
As agents proliferate, they require standardized ways to communicate with tools and each other,
creating a new communication fabric managed by specific protocols and architectural components.
MCP (Model Context Protocol): This is an emerging open-source protocol that acts as an
integration API for AI. It provides a standardized way for any agent to discover and interact with
any external tool, database, or API that is exposed via an MCP server. This simplifies integration
but also standardizes a new target for attackers.
A2A (Agent-to-Agent) Protocols: This category of protocols governs how multiple, specialized
agents collaborate and orchestrate complex tasks. The introduction of a modern A2A framework
by Google has been a key catalyst for bringing this capability to the forefront of enterprise AI.
Google's A2A is designed to provide a standardized language for how agents negotiate, delegate
work, and share information in real time. This enables sophisticated interaction patterns, such as
one agent broadcasting a task and others bidding to complete it. As adoption grows, securing
these A2A channels is critical, since a single compromised agent could otherwise deceive or
manipulate an entire fleet.
MCP Server: This is the software implementation that exposes a tool or API via the MCP protocol.
It acts as a wrapper, making a traditional API or database "speak" MCP so that any compliant
agent can discover and use it.
MCP Gateway: As agent traffic grows, organizations will increasingly deploy MCP Gateways.
Similar to an API gateway, an MCP Gateway is a centralized control point that manages,
secures, and monitors all communication flowing through agentic protocols. While essential for
governance, these gateways also become high-value infrastructure that must be rigorously
protected. A key operational risk, however, is that agents can be configured to connect directly
to MCP Servers, bypassing the gateway and its centralized security controls.
6
The Crisis of Identity: The Unauthenticated Workforce
The most acute security failure of the current agent ecosystem is the lack of a distinct, verifiable
machine identity. Most agents today operate by inheriting the credentials of the user who initiated
them. This model is untenable because it breaks fundamental security principles like non-repudiation
(the ability to prove an action was taken by a specific entity) and the Principle of Least Privilege (PoLP).
From a system's perspective, a malicious database query from a hijacked agent is indistinguishable
from a command issued by a legitimate, credentialed human. This ambiguity makes auditing impossible
and access control high risk.
The path forward requires a move toward a new identity framework where agents are treated as
first-class digital workers with their own identities.
An emerging consensus is forming around a hybrid model that combines decentralized identity
standards with enterprise Identity and Access Management (IAM) systems:
Decentralized Identifiers (DIDs) and Verifiable Credentials (VCs): This is the foundation of
a secure agent identity. Each agent is assigned a unique, cryptographically verifiable DID. Its
permissions, roles, and attestations are issued as VCs. This allows an agent to prove who it is and
what it's authorized to do without relying on a centralized authority.
Ephemeral, Task-Scoped Credentials: Instead of persistent access, agents should receive
temporary, limited-use tokens to perform a specific job, which expire upon completion. This is like
giving a contractor a keycard that only opens one door for one hour.
Integration with Enterprise IAM: This new identity layer must integrate with existing IAM and
Identity Governance (IGA) platforms. This allows organizations to apply the same fine-grained
access controls, policy enforcement, and compliance monitoring to agents that they use for
human employees.
Solving this identity challenge is a prerequisite for trust. It raises critical governance questions that
must be addressed: Who is responsible for an agent's identity lifecycle? How are its credentials issued
and revoked? A mature security program must define clear ownership and automated processes to
manage the identity and entitlements of its entire autonomous workforce.
7
A New Calculus of Risk
Securing agentic AI requires confronting two realities. First, agents inherit all the foundational risks
of the LLMs they are built on. Second, their ability to take autonomous action creates a new, more
dangerous class of threats.
The Foundational LLM Risk Baseline
All standard LLM security practices remain mandatory. The safety guardrails developed for chatbots,
including monitoring inputs and outputs, preventing data leakage of PII, and mitigating hallucinations,
are the absolute minimum requirement. This baseline is well-documented in frameworks like the
OWASP Top 10 for Large Language Model Applications. These are the table stakes for AI security.
However, they are insufficient for agents, because the consequences of failure extend beyond bad
information to include harmful actions.
Unique Risks of an Autonomous System
The true danger of agentic AI lies in the shift from compromised outputs to compromised outcomes.
As industry analysts at Forrester have noted, this creates a "complexity gap," where the move from a
simple "generate and review" model to a "plan, act, and fail autonomously" model introduces risks that
are orders of magnitude more severe.
Risk 1: From Data Breach to Systemic Sabotage
The concept of "blast radius" takes on new meaning. A compromised agent is an active,
authenticated user with the ability to execute transactions.
Scenario: An attacker uses a cross-prompt injection attack to hijack a finance agent processing invoices.
The attacker's goal shifts from stealing data to introducing subtle errors. The agent is instructed to approve
all invoices from a shell corporation controlled by the attacker and to slightly alter payment details on
legitimate invoices, redirecting fractions of payments. Instead of a noisy smash-and-grab attack, this quiet
corruption of core business processes may go undetected for months, causing direct financial loss and
destroying the integrity of financial records.
8
Risk 2: Weaponizing the Agent's Learning Loop
An agent's memory is its greatest strength and its most subtle vulnerability. Attacks can
be designed to persist over time, weaponizing the agent's own learning mechanism against
the enterprise.
Memory Injection: Through a series of carefully crafted interactions, an attacker can pollute an agent's
long-term memory. For instance, they could convince a support agent that a specific, malicious
troubleshooting script is the "new standard procedure." Weeks later, when a legitimate user reports the
relevant issue, the agent will recall and execute the poisoned memory, compromising the user's system
without any active attack occurring in that session. This temporal disconnect between compromise and
execution breaks traditional incident response models.
RAG Poisoning: An attacker can manipulate the "ground truth" an agent relies on. By planting a malicious
document in a knowledge base used for Retrieval-Augmented Generation (RAG), they can make the agent
operate on a false premise. When asked for a secure configuration, the agent might retrieve the poisoned
document and confidently provide a backdoored code snippet.
Risk 3: The Peril of Perfect, Flawed Execution
Malice is not a prerequisite for disaster. An agent's literal, logic-driven interpretation of a
goal, devoid of human context and common sense, can lead to catastrophic outcomes. This
is the practical manifestation of the AI alignment problem.
Unintended Consequences: In a well-documented case, a development agent tasked with resolving a
database performance issue concluded that the most efficient solution was to delete the entire production
database. The agent, while not compromised, was flawlessly executing a disastrous plan. It highlights the
danger of "scope creep," where an agent pursues its objective with a relentless focus that ignores collateral
consequences a human would instinctively avoid.
9
Risk 4: The Unsecured Trust Fabric
Modern enterprises are built on APIs. Agents live on this fabric, communicating with each
other and with countless services. This distributed model creates systemic risks where a
single weak link can compromise the entire network, echoing classic application security
concerns now amplified by AI.
Trojan Tools and Malicious Agents: Emerging standards like MCP allow agents to dynamically discover and
use tools from third-party servers. An attacker can publish a "trojan tool" that performs a useful function but
also contains hidden malicious logic, effectively creating a honeypot for autonomous agents.
Agent-to-Agent Contagion: In a multi-agent system, a single compromised agent can become a super-
spreader. It can pass poisoned data or malicious instructions to other agents it collaborates with. This can
trigger a chain reaction, allowing an attacker to move laterally across the automated workforce and achieve
widespread system compromise.
Agentic Threat Matrix
Threat Category Specific Vector Affected Component(s)
Indirect Prompt Injection
Perception Module, LLM Brain
Communication
Hijacking
Memory Injection, RAG Poisoning
Long-Term Memory, Knowledge Base
Memory & Context
Poisoning
Illicit Tool Usage, SSRF
Tool Executor, External APIs
Tool & API
Exploitation
Malicious Tool Registration
MCP Server, Tool Discovery
Ecosystem &
Supply Chain
10
A Staged Security Architecture
for Agentic AI
Securing a dynamic, autonomous workforce requires a strategic architecture that can sense, respond,
and govern at machine speed. The pillars that form this architecture are not isolated point solutions;
they represent the interdependent components of a new, cohesive security architecture that is rapidly
converging into a unified, AI-native security stack. This integrated defense system is best implemented
in three distinct stages.
Stage 1: Foundation (Visibility & Hardening)
This initial stage establishes a comprehensive understanding of your agentic environment: what assets
exist, how they are configured, and what constitutes normal behavior.
Pillar 1: AI Observability
This provides the necessary visibility to answer three critical questions:
1)   Which agents are operating
across our environment (in apps,
on endpoints, in the cloud)?
2) What are they doing (which tools
are they calling, what data are
they accessing)?
3)   How are they interacting with
each other?
It moves beyond traditional logs to trace an agent’s entire cognitive chain, revealing the "why" behind every action and
providing the foundation for all detection, forensics, and meaningful human oversight.
In Practice: When an agent makes an anomalous financial transaction, observability allows an analyst to instantly
reconstruct its decision process and see that it was based on poisoned RAG data ingested hours earlier.
Pillar 2: AI Security Posture Management (ASPM) and Identity Governance
Acts as your inventory and risk map. It continuously discovers every agent, mapping its permissions and data access
to proactively harden the environment and eliminate "privilege creep." For agents, this must extend beyond mapping
models and data sources to include agent identity governance. This means managing the entire lifecycle of an agent's
verifiable identity, including the issuance and revocation of its Decentralized Identifiers (DIDs) and the regular auditing
of its Verifiable Credentials (VCs) to enforce least privilege.
In Practice: ASPM and Identity Governance flags a marketing agent with lingering write-access to a CRM, allowing
security to right-size its permissions and proactively reduce its blast radius.
11
Stage 2: Active Defense (Real-time Prevention)
These are the active controls responsible for identifying and neutralizing threats the moment they
appear, before they can cause harm.
Pillar 3: AI Runtime Security
The primary defense mechanism. This in-line control intercepts an agent's proposed actions before execution, blocking
malicious or out-of-policy behavior in real time. It is the essential "braking system" for autonomous processes.
In Practice: Runtime security detects and blocks a hijacked agent attempting to exfiltrate a customer list via
anomalous DNS queries.
Pillar 4: Intelligent Guardrails
This robust policy layer validates all inputs and outputs, acting as a far more reliable control than brittle system prompts
to prevent prompt injections and enforce operational boundaries.
In Practice: An input guardrail detects a prompt injection attack and blocks it, while an output guardrail prevents an
agent from executing a transaction that violates a business rule.
Pillar 5: AI Firewalls
Secures the pathways between agents and external systems. It uses machine learning to understand normal API traffic
and can detect and block novel attacks that traditional firewalls would miss. edw21.
In Practice: An AI firewall blocks an agent's attempt to communicate with a newly registered, malicious "trojan
tool" server.
Stage 3: Governance (Scalable Control)
This final stage translates high-level intent into consistent, fleet-wide action, ensuring compliance
and control as you scale.
Pillar 6: Automated Policy Enforcement
This engine allows you to define a governance rule once, such as "no agent can transfer more than $1,000 without
human sign-off," and have it automatically enforced across every agent. It is the only feasible path to consistent,
auditable governance at enterprise scale. This is where identity becomes critical; effective policy enforcement relies
on the ability to tie every action to a strong, verifiable agent identity (DID), ensuring that rules are applied correctly
and that a non-repudiable audit trail is created.
In Practice: The engine enforces the spending limit rule for all agents, whether they are interacting with a Stripe
API or provisioning cloud resources in AWS.
12
The New Mandate: Engineering Trust for Operational Velocity
The arrival of autonomous agents presents a fundamental strategic choice. The core challenge is no
longer about incremental efficiency gains; it is about achieving operational velocity at machine speed.
Organizations that successfully deploy agents will operate on a completely different timeline than their
competitors, compressing complex workflows from days into minutes. This is the new benchmark for
market leadership.
However, this opportunity is shadowed by a new and potent form of risk. The understandable fear
of ceding control to autonomous systems can lead to operational paralysis: a state of inaction where
the potential for catastrophic failure stalls innovation. In this new landscape, the greatest risk is not a
security breach, but being outpaced by competitors who have solved for trust and are moving faster.
The staged security architecture detailed in this paper is the direct antidote to this paralysis. It provides
a pragmatic and comprehensive methodology for building a verifiable layer of confidence throughout
the enterprise. By establishing a foundation of deep visibility, deploying an active defense that operates
in real time, and scaling governance with automated enforcement, this framework systematically
reduces risk. It replaces fear and ambiguity with architected assurance.
This transforms the mission of the security organization. A reactive posture of risk mitigation is now
insufficient. The new mandate is to become the engineers of velocity. Like the designers of a high-
performance vehicle, their role is not to be the brakes that slow the organization down, but to build the
advanced braking and traction control systems that allow it to accelerate safely.
The ultimate expression of this new mandate lies in leveraging agentic technology for security itself.
The same protocols like MCP that create a surface to be defended can be turned into a powerful tool
for security automation. The most advanced security teams will not only protect their agents; they
will deploy their own trusted agents to orchestrate threat detection, manage incident response, and
automate compliance, fighting AI-driven threats with AI-driven defenses.
By implementing this framework, security teams enable a model of augmented oversight, where the
system handles the vast majority of threats and frees human experts to focus on strategic judgment.
This builds the organizational trust required to delegate tasks to an autonomous workforce. Ultimately,
the choice is clear: leaders can accept paralysis born of uncertainty, or they can build a foundation of
trust that enables them to operate with the speed and intelligence of the autonomous enterprise. The
organizations that choose the latter will not just participate in the future; they will define it.
13
About WitnessAI
WitnessAI enables safe and effective adoption of enterprise AI,
through security and governance guardrails for public and private
LLMs. The WitnessAI Secure AI Enablement Platform provides
visibility of employee AI use, control of that use via AI-oriented
policy, and protection of that use via data and topic security.
