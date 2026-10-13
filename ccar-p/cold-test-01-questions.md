# CCAR-P Cold Test 01 — 20 questions

Suggested time: 38 minutes (same per-question pace as the real exam: 63 items / 120 min).
Closed book. No AI assistance. Each multiple-response item states how many to select.

---

## Domain 1 — Solution Design & Architecture

**Q1.** A logistics operator wants to automate exception handling for delayed shipments. Analysis of 14 months of tickets shows 80% of exceptions follow one of six documented resolution playbooks, while 20% require judgement across three systems with an unpredictable number of steps. The business requires a p95 of under 5 seconds for the common cases and accepts minutes for the rest. Which architecture best fits? (Select ONE)

A) A single agentic loop with tools for every system, handling all exception types uniformly.
B) A deterministic workflow that classifies the exception, executes the matching playbook inline, and routes unclassified cases to an agentic path.
C) One augmented-LLM call containing all six playbooks in the system prompt, returning the resolution in a single turn.
D) A multi-agent system with one specialist subagent per playbook, coordinated by an orchestrator.

**Q2.** A market-intelligence product must produce a competitive analysis report from roughly 40 sources. The sub-questions (pricing, hiring signals, product launches, patent filings) are independent of one another and must be synthesised into one narrative. Report latency of several minutes is acceptable. Which orchestration strategy is most appropriate? (Select ONE)

A) A sequential chain where each step's output feeds the next step's prompt.
B) A single agent looping over sources one at a time, accumulating notes in its context window.
C) An orchestrator that dispatches parallel subagents per sub-question, each returning a structured finding, followed by a synthesis step.
D) A peer swarm of agents sharing one scratchpad with no coordinator, converging by consensus.

**Q3.** The CFO is funding your programme on the basis of cost avoidance. The operations director, who owns adoption, is judged on cycle time. You are defining the success criteria in the solution design document. Which TWO metrics should be the headline success criteria? (Select TWO)

A) Average tokens consumed per request.
B) Fully-loaded cost per successfully resolved case.
C) Mean handling time per case, end to end.
D) Model accuracy on the golden evaluation set.
E) Percentage of prompt tokens served from cache.

---

## Domain 2 — Claude Models, Prompting & Context Engineering

**Q4.** A classification service assigns one of 12 labels to 2 million inbound messages per day. The contractual p95 latency is 300 ms and the accuracy floor is 94%. The current implementation uses the largest available Claude model with chain-of-thought reasoning: it achieves 97% accuracy at 2.1 s p95 and is over budget. What is the best next step? (Select ONE)

A) Move to the smallest Claude model with few-shot examples curated from the large model's correct outputs, then validate against the 94% floor before rollout.
B) Keep the current model and reasoning, and add prompt caching to the static portion of the prompt.
C) Keep chain-of-thought but switch to the mid-tier model with extended thinking enabled.
D) Keep the current configuration and stream the response so the first token arrives sooner.

**Q5.** A support assistant sends an 18,000-token static policy preamble on every request, followed by a short conversation turn. Volume is 40,000 requests per day. The policy must be applied in full on every call for compliance reasons. Which change delivers the largest cost and latency improvement? (Select ONE)

A) Move the policy into a RAG index and retrieve the top five relevant passages per request.
B) Place the static policy first and set a cache breakpoint between it and the dynamic content.
C) Ask Claude to compress the policy into a 2,000-token summary and use that instead.
D) Move the policy to the end of the prompt, immediately before the user's turn.

**Q6.** A banking assistant is scoped to product information only, but in about 3% of sessions it answers customer questions about legal liability. Legal has demanded this stop. Which intervention is most effective? (Select ONE)

A) Reduce the temperature to 0 so responses become more conservative.
B) Append "do not answer legal questions" to every user message before sending it.
C) Define the scope boundary in the system prompt with in-scope and out-of-scope examples plus a structured refusal-and-handoff path, and assert scope in the output schema.
D) Post-process every response with a regex blocklist for legal terminology.

---

## Domain 3 — Integration

**Q7.** An operations agent has accumulated 47 tools across six internal systems. Evaluation shows it selects the wrong tool in roughly 20% of runs, usually picking a superficially similar tool from an unrelated system. Which remediation addresses the root cause? (Select ONE)

A) Partition the tools into task-scoped sets exposed through progressive discovery or delegated subagents, so only relevant tools are in context for a given task.
B) Expand every tool description with more detail and more usage examples.
C) Increase the thinking budget so the agent deliberates longer before each call.
D) Rename the tools with a consistent prefix convention and order them alphabetically.

**Q8.** A manufacturer is building retrieval over 12,000 engineering standards documents. The documents are long, heavily cross-referenced, and structured with numbered clauses. Virtually all queries are precise clause lookups such as "what is the torque specification for fastener class 8.8 in assembly line C". Which retrieval design fits best? (Select ONE)

A) Embed each document as a whole and return the single highest-scoring document.
B) Use 8,000-token chunks with pure dense-vector semantic search.
C) Summarise each document with Claude, embed the summaries, and retrieve against those.
D) Chunk at clause and section level, carry heading and document-ID metadata on each chunk, and use hybrid keyword plus dense retrieval with a reranking pass.

**Q9.** Five internal teams each own a data source. Two different Claude surfaces must reach all of them: Claude Code for engineers and a custom chat application for analysts. Access must be evaluated against the individual end user's permissions, and each team wants to own its own integration. Which integration mechanism should you select? (Select ONE)

A) A single monolithic REST façade in front of all five sources, with hand-written tool definitions duplicated in each client.
B) An MCP server per data source, owned by the team that owns the data, with OAuth-based user authorisation, consumed by both clients.
C) An agent-to-agent protocol between the chat application and Claude Code, with one of them acting as the data gateway.
D) Direct database connections configured in each client, with credentials supplied in the system prompt.

**Q10.** A user-facing HR assistant calls the internal HR API with one service account that holds broad read access across all employee records. The requesting user's identity is passed only as a string inside the prompt. Which TWO are the genuine security gaps? (Select TWO)

A) The agent can act beyond the requesting user's own entitlements, a confused-deputy exposure.
B) The service-account credential is rotated every 90 days rather than every 30 days.
C) Traffic uses TLS 1.3 rather than mutual TLS.
D) There is no propagation of per-user authorisation, for example a token-exchange or on-behalf-of flow.
E) Tool results are not written to the prompt cache.

---

## Domain 4 — Evaluation, Testing & Optimisation

**Q11.** An insurance assistant summarises claim files. In about 6% of outputs it states policy clause numbers that do not exist. You have verified that retrieval returns the correct source documents in every one of those cases, and the correct clause number is present in the retrieved text. What is the correct diagnosis and fix? (Select ONE)

A) The model is too small for the task; move to the largest available Claude model.
B) Retrieval recall is insufficient; increase top-k and widen the chunk overlap.
C) The output is ungrounded by design; require span-level citations tied to retrieved chunk IDs, and add a verification step that rejects claims whose citation does not resolve.
D) Sampling noise is causing the fabrication; set temperature to 0.

**Q12.** You are building the evaluation suite for a contract-review assistant. Outputs mix objective extractions (dates, parties, values) with subjective judgements (whether a clause is unusually onerous). Which TWO choices should shape the dataset and framework? (Select TWO)

A) Mine adversarial and edge cases from production failure logs and add them as labelled cases.
B) Rely exclusively on human expert review so that no automated-judge bias enters the metric.
C) Generate every case synthetically from the documented happy path to maximise coverage quickly.
D) Combine programmatic checks for the objective dimensions with rubric-driven LLM-as-judge scoring for the subjective ones.
E) Report one aggregate accuracy number so stakeholders have a single figure to track.

**Q13.** A rewritten system prompt scores 6 points higher than the incumbent on your offline evaluation set of 50 cases. The service handles 90,000 requests per day. What should happen before full rollout? (Select ONE)

A) Ship to 100% of traffic, since the offline evaluation improved and the change is prompt-only.
B) Run a staged online rollout against a holdout, with a pre-registered primary metric, guardrail metrics for cost and latency, and a sample size powered to detect the expected effect.
C) Circulate both versions to three senior stakeholders and adopt the one they prefer.
D) Run both variants for a day and keep whichever consumed fewer tokens.

---

## Domain 5 — Governance, Safety & Risk Management

**Q14.** A hospital group wants Claude to draft discharge summaries from clinical notes. The workload is squarely within HIPAA scope. Which approach is correct? (Select ONE)

A) Rely on the model's built-in safety behaviour to refuse inappropriate handling of health data.
B) Retain complete request and response transcripts indefinitely so that clinical quality can be audited.
C) Use a consumer-tier Claude subscription, since clinicians are the only users and they are already bound by HIPAA.
D) Operate under an executed BAA on a covered deployment, minimise and de-identify PHI where clinically possible, scrub PHI from logs and telemetry, and enforce role-based access with an audit trail.

**Q15.** An agent drafts and issues customer refunds. Values range from $4 to $50,000, and issued refunds cannot be reversed without a manual finance ticket. Throughput matters: 4,000 refunds a day. Where should the human sit? (Select ONE)

A) Risk-tiered control: auto-execute below a value threshold with full audit logging, require human approval above it, and hard-block execution on ambiguous or unresolvable cases.
B) A human reviews and approves every refund before it is issued.
C) A human reviews a random 5% sample of issued refunds each week.
D) Fully autonomous execution with a monthly post-hoc reconciliation report.

**Q16.** In a risk register for an LLM-based system, which TWO entries are inherent limitations of the model itself, requiring architectural mitigation rather than a prompt fix? (Select TWO)

A) A downstream tool intermittently returns HTTP 500.
B) Identical inputs can produce materially different outputs across runs.
C) The model's parametric knowledge has a training cutoff and becomes stale.
D) Users submit typos and abbreviations in free-text fields.
E) Cross-region network hops add 80 ms to each call.

---

## Domain 6 — Stakeholder Communication & Lifecycle Management

**Q17.** In a first discovery session, the VP of Sales opens with: "We want an agent that does everything in our CRM." What is the best next move? (Select ONE)

A) Scope a proof of concept against the broadest interpretation so the VP sees ambition matched.
B) Present a reference architecture for CRM agents to anchor the conversation in what is technically possible.
C) Run structured discovery to surface specific high-volume, high-pain tasks, their current baselines, and what measurable outcome would count as success.
D) Ask for the list of CRM API endpoints so you can enumerate the available tool surface.

**Q18.** An executive sponsor states three non-negotiables: 99% accuracy, sub-second responses, and the lowest possible cost. Your analysis shows any two can be met but not all three. How should you handle it? (Select ONE)

A) Present the trade-off frontier as two or three costed, specified options and ask the sponsor to prioritise them against business impact.
B) Commit to all three and plan to renegotiate once the pilot data makes the conflict self-evident.
C) Optimise for accuracy, since it is the dimension that protects the business from harm, and report on it.
D) Escalate to the sponsor's manager for a decision on which constraint to drop.

**Q19.** A pilot lands at 92% task accuracy. Stakeholders had understood "human-level performance" as the goal and are now questioning the rollout. Internal benchmarking shows the human baseline on the same task is 89%. What should you do? (Select ONE)

A) Delay the rollout and continue iterating until accuracy reaches 99%.
B) Reframe the SLA around the task-level business outcome, show the measured human baseline as the comparator, route low-confidence cases to human review, and agree explicit acceptance criteria and a review cadence.
C) Report the aggregate figure without the per-domain breakdown, to avoid undermining confidence during the rollout decision.
D) Re-run the pilot on an easier case mix so that the headline number clears the stakeholders' expectation.

---

## Domain 7 — Developer Productivity & Operational Enablement

**Q20.** Forty engineers across four repositories have adopted Claude Code. Output quality varies widely, engineers repeatedly re-explain the same project conventions, and each developer approves the same tool permissions by hand. What should you put in place? (Select ONE)

A) Commit per-repository project memory capturing conventions, plus shared skills and slash commands and a reviewed permission allowlist in checked-in project settings.
B) Circulate a prompt-writing guide and let each engineer maintain their own personal configuration.
C) Standardise on one shared account so that all engineers inherit the same settings and history.
D) Restrict use to a small enabled group until conventions emerge organically from their practice.
