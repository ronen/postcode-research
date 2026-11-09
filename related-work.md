# PostCode: Related Work

This is a working account of research related to PostCode, not a systematic literature review.

Its purpose is to identify nearby research traditions, potentially overlapping systems, useful methodological precedent, and work that may sharpen PostCode's research questions. The bibliography and positioning hypotheses should evolve together as the project and literature review develop.

Review-basis notes identify the material checked for particular entries. An abstract or project description supports an account of what its authors report; it does not establish implementation maturity, analysis guarantees, or human usefulness. Entries without a review-basis note retain their earlier working status and should be checked before supporting a formal comparison. Dated notes below record the checks made for each entry.

## 1. Working Bibliography

### 1.1 Agentic software engineering and changing human roles

**Davis, J. C., Kalu, K. G., Peng, H., & Patil, P. V. (2026). _Model-Based Agentic Software Engineering (MAGE)._ Preprint, arXiv:2608.25174.** [Paper](https://arxiv.org/abs/2608.25174)

Particularly close conceptually. MAGE argues that increased implementation capacity makes explicit abstractions, evidence and engineering obligations increasingly important, and proposes externalizing purposeful representations rather than repeatedly reconstructing consequential properties.

The overlap includes shared human–agent knowledge, retained intent, and reducing repeated reconstruction, not just human inspection. MAGE couples representations to authoritative engineering obligations; PostCode contributes qualified architectural investigation within a larger design process without making its accounts authoritative. Compare how each exposes unsettled intent, maintains evidence, and separates knowledge from decision authority.

Review basis updated 5 November 2026: selected [v1 full text](https://arxiv.org/html/2608.25174v1), including framing, representation/authority distinctions, project states, and research agenda. This is a theory and research agenda with case-based grounding, not a controlled demonstration of PostCode-like account superiority or human architectural outcomes.

**Hassan, A. E., et al. (2025). _Agentic Software Engineering: Foundational Pillars and a Research Roadmap._ arXiv:2509.06216.**

Broad framing of Agentic Software Engineering and the emerging distinction between software engineering for humans and software engineering for agents.

Particularly relevant to PostCode's explicit separation between the representation humans need and the representation agents may need.

**Fowler, M. (2026). _Agentic Programming._**

Discusses the transition from humans directly writing source toward humans overseeing agents that generate it.

Useful contextual motivation rather than direct technical prior art.

**de Halleux, P., Syme, D., & Zorn, B. (2026). _Repositories Are Human/Agent Knowledge Factories._ SIGPLAN Blog.**

Argues that repositories in agent-driven development should become explicit knowledge structures supporting agents and human supervision, including formalized conventions, specifications and validation.

Strongly adjacent to PostCode's motivating problem, but focuses more on repository structure and agent-consumable knowledge than on replacing source as the human inspection surface.

**Rosa, G., Linares-Vásquez, M., & Robles, G. (2026). _Re-Imagining Software Visualization for Spec-Driven Development._ VISSOFT 2026, Visions track; final proceedings details to verify.** [Author page](https://shiftmanifesto.com/research/spec-visualization/) · [Conference program](https://vissoft.io/2026/program.html)

Proposes visualizing specifications, relationships among specifications, traceability to generated code, and their evolution in AI-assisted development. Relevant because it explores a human-facing representation beyond source during software creation, not only retrospective comprehension.

Its specification-first approach differs from PostCode's qualified projections of the evolving actual program, but the boundary is not sharp: as [`research.md`](research.md#31-creation-continued-development-and-existing-software) notes, PostCode also investigates development from inception, where recorded intentions and implementation may co-evolve. This makes it meaningful conceptual prior art for that part of PostCode's research direction.

Review basis: author-page abstract and official conference program; full paper not assessed.

**Tavantzis, T., Trinkenreich, B., Greiler, M., et al. (2026). _Cognitive Debt in the GenAI Era — Listening to Practitioners' Voices on the Loss of Understanding._ Preprint, arXiv:2610.37888; submitted 27 October 2026.** [Paper](https://arxiv.org/abs/2610.37888)

Reviews 76 practitioner sources about the gap between working software and the understanding people retain when using generative AI. The synthesis distinguishes lost design rationale from gaps in developers' mental models and reports proposed practices including comprehension gates, review-sized changes, explicit assumptions, design records, and knowledge-sharing work.

This is direct motivation for testing whether PostCode helps people form durable, usable architectural understanding rather than merely presenting plausible explanations. It also suggests that a successful task or passing test is not evidence that a person can explain, modify, or supervise the resulting system. A bounded study should measure those outcomes separately and test whether an apparently helpful representation transfers to later work.

Review basis (2 November 2026): metadata and selected full-text sections on the grey-literature method, findings, implications, and validity threats. The sources are practitioner accounts rather than observations of a controlled workflow; definitions vary, recommendations are not evaluated, and the study concerns software practitioners rather than people without programming expertise.

**Zhu, H., Xu, G., Yang, Z., Wang, J., & Zhang, Q. (2026). _Precedent or Intent? What Coding Agents Follow When Evolving Existing Code._ Preprint, arXiv:2610.38244; submitted 28 October 2026.** [Paper](https://arxiv.org/abs/2610.38244)

Separates model preference, repository precedent, and explicit task instructions in 5,625 controlled trials across four coding agents and six implementation choices, with follow-up in four open-source repositories. Agents followed conflicting local precedent in 359 of 360 controlled trials; explicit priority rules outperformed examples alone, and a harness-loaded rule redirected the studied open-source changes in 117 of 120 runs.

For PostCode, an implemented pattern is evidence of what exists, not necessarily why it exists or whether it should govern the next change. Retained architectural intent should preserve rationale, priority, scope, and revision separately from recovered precedent, while making conflicts visible to the human. This supplies a concrete evaluation pattern for whether an agent follows an explicit architectural decision when nearby code points elsewhere.

Review basis (2 November 2026): metadata and selected full-text sections on design, results, open-source validation, discussion, and threats. The experiments cover selected choices, one controlled task family, four repositories, and two providers; they measure implementation choice and functional success, not maintainability, architecture quality, human understanding, or autonomous discovery of rules.

**Granitzer, M., Ghosh Dastidar, K., Einwiller, A., Mitrović, J., & Zerhoudi, S. (2026). _Getting a Grip: Operating Human-Agent Software Teams Through Governed Messages._ Preprint, arXiv:2611.00689; submitted 31 October 2026.** [Paper](https://arxiv.org/abs/2611.00689)

Studies a message-governed human–agent software team in 926 controlled runs (899 analyzable) and a four-week field deployment involving up to 19 agents and two people. The system treats humans and agents as authenticated principals exchanging typed, addressed acts in rooms with goals, rules, routing, and an append-only attributable record. Revising which messages started work, bundled with limits on repeated messages, was followed by a drop in coordination failure from 42% to 13%; instructed roles and votes were unreliable, and no conversational defense reliably stopped the studied backdoor.

For PostCode, this supplies constructive and field-based evidence that a shared working environment needs enforceable distinctions among information, request, decision, authorization, and completion, while preserving provenance and critical state across compaction. The field record also makes human attention and decision latency explicit constraints. These results concern team operation rather than a human architectural interface, and the bundled intervention and convenience field setting do not isolate which mechanism caused each effect.

Review basis (9 November 2026): primary metadata and selected full-text sections on architecture, controlled studies, field operation, lessons, instrument failures, and validity. The findings support design knowledge and comparison conditions for collaborative practice; they do not establish PostCode's account quality or human usefulness.

### 1.2 Human oversight of software agents

**Dhanorkar, S., Passi, S., & Vorvoreanu, M. (2026). _Human oversight of agentic systems in practice: Examining the oversight work, challenges, and heuristics of developers using software agents._ FAccT 2026 / arXiv:2606.05391.**

Empirical study of experienced developers identifying forms of oversight including a priori control, co-planning, real-time monitoring and post-hoc review.

Especially relevant because developers report difficulty reviewing agent-generated code and use artifacts such as test results as proxies or guarantees during oversight.

Potentially important empirical motivation for PostCode's attempt to provide better human-facing supervisory representations.

**Sun et al. (2026). _What Did the Agent Actually Do? Evidence-Grounded Oversight for Long-Horizon Agents._ Preprint, arXiv:2610.06406.** [Paper](https://arxiv.org/abs/2610.06406)

Introduces an Evidence-Grounded Behavior Graph organizing evidence about agent behaviors and relationships into task-oriented oversight views, with links to supporting evidence. Its evaluation includes scenarios involving consequential changes that may not be exposed by ordinary test results.

Close prior art for evidence-grounded oversight, structured relationships, and task-specific representations. Its primary object is agent behavior and verification decisions; PostCode's is the evolving software and the human conceptual interface used to direct and supervise it. Its benchmark may provide useful evaluation scenarios. AgentMonBench comprises SpecGAP, SilentSwap, and FeedbackTrace; SilentSwap specifically introduces behavioral substitutions that preserve existing test outcomes. This resolves the historical handover's benchmark-name discrepancy: SilentSwap is a component, not an alternative name for the whole benchmark.

Review basis: abstract and selected full-text sections on the method and evaluation; benchmark composition and SilentSwap construction rechecked in sections 3 and Appendix B on 12 October 2026. The reported experiments evaluate monitors across eight models, with illustrative real-world cases; they do not establish the effectiveness of a sustained human development interface.

**Ferris & Bonilla (2026). _A Case Study in Assuring AI-Written Software._ Preprint, arXiv:2610.08651; reported as accepted to the NeurIPS 2026 Meta-Agents Workshop.** [Paper](https://arxiv.org/abs/2610.08651)

Retrospective case study of a production healthcare platform built with coding agents and governed by an operator without formal software-engineering training. Two structured interviews and six months of project records describe a workflow in which the operator approved plans, durable rules, staging behavior, and production releases while tests, monitors, fresh-context reviewers, and meta-audits supplied much of the technical evidence.

The case is directly relevant to PostCode's premise that human control need not consist of exhaustive source inspection. It also shows the second-order problem for any alternative representation or review mechanism: some checks observed proxies rather than intended outcomes, missing checks vanished from aggregate reports, and an automated repair caused disruption. A useful PostCode comparison should therefore connect the intended outcome, observed evidence, its limitations, agent permissions, and the consequential human decision instead of treating an extra reviewer or a passing signal as ground truth.

Review basis updated 26 October 2026: selected full-text sections on the case, workflow, control boundaries, assurance failures, discussion, and limitations. This single observational case does not establish fewer defects, security or compliance, or transfer to other people and systems; the operator helped create both the platform and its governance process.

**Manji, A. (2026). _Who Approved This? Coding Agents, Human Accounts, and Merge-Gate Evidence at a Fintech Startup._ Preprint, arXiv:2610.28683; submitted 19 October 2026.** [Paper](https://arxiv.org/abs/2610.28683)

Reports twelve weeks of agent-driven development at one three-person startup and recomputes whether each merge had a non-author approval and passing required check on the exact revision before integration. In the enforced period all 263 merges to the main branch met that platform-visible gate, but 71 relied only on an approval that an agent submitted through the technical lead's account; the retained records cannot establish whether the person or the session made the acceptance decision.

This exposes a provenance distinction relevant to PostCode's supervision records: account identity, acting process, decision authority, evidence reviewed, and repository revision are separate facts. Interaction logs can preserve available actions and evidence without proving an unrecorded human judgment. A future evaluation should check whether PostCode's records let a reviewer reconstruct those distinctions at the consequential revision.

Review basis (26 October 2026): abstract and selected full-text sections on the data, exact-revision gate reconstruction, action traces, findings, and validity threats. This is a participant-authored observational study of one repository; missing audit-log and transcript coverage, changing controls, inferred agent association, and the author's operational role limit causal and population claims.

**Khan, M. N., & Kumar, K. S. S. (2026). _Soei: Structured Observability of Evidence and Intent for Multi-Agent AI Software Engineering._ Preprint, arXiv:2610.39468; submitted 29 October 2026.** [Paper](https://arxiv.org/abs/2610.39468)

Proposes a read-only observability substrate that records acknowledged events, content lineage, project intent, claims, and proof in a hash-chained local ledger and a W3C PROV-aligned graph. On 45 Copilot agent-mode sessions from one developer's workstation, its audited classifier estimates that 23.4% of code-editing episodes ended without an independent check after the last edit and 57.8% of edit-backed to-dos marked complete had no intervening proof.

Soei closely overlaps PostCode's need to separate an agent's account of completion from the evidence available to a supervisor. Its distinctions among claim, proof, artifact revision, inferred lineage, acknowledgement, and unavailable evidence are useful comparison dimensions for a human-facing architectural interface. The prototype primarily observes work history rather than the software's architecture, and it does not establish that its proposed views improve human decisions.

Review basis (2 November 2026): metadata and selected full-text sections on positioning, event and evidence models, corpus, measurements, supervisory views, governance proposal, and validity threats. The corpus comes from one developer and one harness; verification outside the transcript is invisible, lineage is path-based, the classifier is rule-based, and the implementation and released artifacts were not run.

**Goel, A., Capponi, A., Gliozzo, A., & Shah, C. (2026). _Measuring Where Intent Gets Lost in Agentic Smart Contract Synthesis._ Preprint, arXiv:2610.37830; submitted 27 October 2026.** [Paper](https://arxiv.org/abs/2610.37830)

Audits the instruments used to evaluate contract-writing agents, then compares generation from incomplete descriptions with an elicitation-first pipeline. Planted-error tests expose failures in LLM judges, static analysis, and LLM testing; exact transaction replay and explicit interface coverage expose omissions hidden by looser scoring. Answers from a simulated client raise implementation fidelity by 19–23 points across three generator families, while later review and repair add little and automated security rewriting often removes requested behavior.

This offers two concrete PostCode lessons. Direction should surface high-value ambiguities before implementation, especially permissions and failure behavior, and evaluation instruments must be tested against known failures rather than treated as ground truth. Verification disagreements should be presented as qualified questions when the evidence cannot adjudicate intent. A useful PostCode comparison would measure elicitation burden, retained intent, exact behavioral evidence, and omissions separately.

Review basis (2 November 2026): metadata and selected full-text sections on study design, instrument validation, elicitation, pipeline ablations, results, discussion, and limitations. The study measures agreement with an existing Solidity implementation, not human author intent; descriptions and client answers were generated from that implementation, no person answered the questions, one corpus and language were used, and the reported elicitation gains are optimistic under the simulator.

**Qiao, Y., Haque, S., & Hundhausen, C. (2026). _Beyond the Prompt: Linking What Developers Ask, Do, and Understand with Coding Agents._ Preprint, arXiv:2609.33712; submitted 27 September 2026.** [Paper](https://arxiv.org/abs/2609.33712)

Provisional methodological lead. Reports a workflow combining prompt analysis, recorded activity, and separate process/solution explanation rubrics, applied to ten experienced developers using Copilot on unfamiliar software. Task performance and understanding diverged for two participants. Understanding scores assess participants' elicited explanations, graded by models using researcher-refined rubrics; they do not measure everything participants may know. This small observational sample does not support population claims.

Relevant to PostCode's questions about mental models and supervision, and to distinguishing interaction traces from evidence of understanding. Evaluate the instruments' suitability before adapting them to sustained formative episodes.

Review basis (12 October 2026): indexed arXiv abstract and metadata in the initial watch; subsequent PR review accessed the primary abstract and [versioned full text](https://arxiv.org/html/2609.33712v1), inspecting the explanation rubrics, grading procedure, study setting, and limitations. Instruments and grading were not independently validated; publication status beyond the preprint remains unverified. Newly found outside the watch's main coverage window.

**Whiteboard (/dev/fast) (2026). Open-source technical project.** [Repository](https://github.com/devdotfast/whiteboard)

Describes a read-only workspace for explaining and inspecting agent-made changes using source-linked diagrams, semantic/AST-aware change presentations, and records of design decisions. Close implementation prior art for non-source supervision and conceptual diffs.

Its declared scope is a shared workspace in which humans and agents architect software together; the documented examples emphasize explaining and reviewing particular changes. This makes it a candidate for comparing conceptual interaction as well as change review. The extent of sustained investigation support and the guarantees of its explanations remain questions to assess, rather than established boundaries separating it from PostCode.

Review basis: repository README; implementation and sustained-use behavior not assessed.

**Xu, G., Zhang, R., Wu, X., & Chen, H. (2026). _What Coding Agents Leave Unsaid: Measuring Task-State Gaps Between Execution and Reports._ Preprint, arXiv:2610.20003; submitted 14 October, revised 15 October 2026 (v2).** [Paper](https://arxiv.org/abs/2610.20003)

CTXGAP measures task-state recoverability from accumulated agent reports versus recorded execution context. Across a non-random 37-task cohort, model readers recovered substantially less from reports, even after successful fixes. Probes, relevance judgments, and much grading are model-generated; human audits examine parts of the instrument, not end-user supervision.

Relevant to whether PostCode preserves information needed to discover and investigate consequential changes. A possible evaluation dimension is recoverability of failures, assumptions, and unresolved risks alongside task success; recoverability is not itself human understanding or good decisions.

Review basis (19 October 2026): metadata and selected v2 sections 3–7, limitations, and selected appendices on measurement and release scope. Full context can include private reasoning unavailable in a public execution view; cached-score reproducibility differs from reusing complete trajectories. No replication performed.

**Gullstrand Heander, L., Sergeyuk, A., Zakharov, I., Söderberg, E., & Mukhortov, N. (2026). _Trust-Calibrated Code Review: A Participatory Design Study of Review Workflows for LLM-Generated Multi-File Changes._ ESEM 2026, LIPIcs 394, 89:1–89:21; published 5 October 2026.** [Paper](https://doi.org/10.4230/LIPIcs.ESEM.2026.89) · [Earlier preprint](https://arxiv.org/abs/2606.01969)

Participatory design with 17 practitioners (seven returning for co-design) proposes overview, file-analysis, and snippet-review levels, including chunking and risk signals. A 43-person survey assessed a prototype walkthrough: anticipated effort reductions are expectations, not observed improvements in review or calibrated trust.

Close interaction-design precedent for conceptual change review and allocating human attention. Compare how risk signals are justified and how evidence reaches each level; risk estimates should not be equated with PostCode's epistemological qualifications.

Review basis (19 October 2026): publisher metadata and selected proceedings sections 3–6, including recruitment, synthesis, survey method, and validity threats. Newly found; the June preprint is the same work, not an additional finding. No functioning prototype or longitudinal use independently assessed.

**Deng, H., et al. (2026). _SWE-Journey: Towards More Realistic Evaluation of Coding Assistants through Long-Horizon, Multi-Turn Interaction._ Preprint, arXiv:2610.11559; submitted 8 October 2026.** [Paper](https://arxiv.org/abs/2610.11559)

Combines synthesized development sequences with persona-conditioned simulated users. Its persona comparisons vary expertise, information, control, goals, and verification together; they do not isolate programming expertise or measure real humans' understanding.

Relevant to constructing sustained direction/supervision tasks, including the source-language-unfamiliar case in [research.md](research.md#5-research-questions). Its task-generation approach merits inspection separately from any human-interface evaluation; successful interaction with a simulator cannot establish PostCode's human usefulness.

Review basis (19 October 2026): metadata, PDF sections 3 and 5, and Appendix A.3–A.4 on persona construction and task checks. Synthetic tasks and simulated behavior constrain transfer. No artifacts run or comparative human study assessed.

**Yan, X., Lei, J., Shi, D., Wang, Z., & Cao, N. (2026). _From Watching to Steering: Enabling Human-Coding Agent Collaboration through Execution Traces._ Preprint, arXiv:2611.04466; submitted 3 November 2026.** [Paper](https://arxiv.org/abs/2611.04466)

VibeTrace presents coding-agent work as hierarchical execution traces and lets a user inspect intermediate states, fork from an earlier step, and retain validated progress. A formative study involved 12 experienced coding-agent users; a controlled questionnaire study with 20 participants reported higher accuracy and lower time on ten trace-comprehension questions than OpenCode's native logs; eight further experts used the prototype on two tasks. Its skill-distillation benchmark is evidence about agent performance, not human understanding.

This is direct prior art for selective oversight, trace provenance, intervention, and reuse of prior investigation. An execution trace remains different from a qualified architectural account: it records how an agent acted, not necessarily what the software means or which inferred relationship is valid. The short tasks and experienced-user samples do not establish sustained architectural practice or usefulness without programming-language source.

Review basis (9 November 2026): primary metadata and selected full-text sections on formative interviews, system design, controlled and expert studies, benchmark results, discussion, and limitations.

**Albu, R., Khval, A., Orlova, M., Music, D., Rosa, F. A. V., Yi, L., & Khojah, R. (2026). _Tracybot: Preserving Developer Intent by Tracing Agent-Generated Code to Prompts._ Preprint, arXiv:2611.09395; submitted 6 November 2026.** [Paper](https://arxiv.org/abs/2611.09395)

Tracybot groups planning and build prompts with agent responses into Tasklets, maps them to changed lines through repository history, and can export a Tasklet as an architectural decision record. Two design-science iterations included a seven-person focus group and a 24-person screenshot-based survey; 21 participants rated the Tasklet representation clear at four or above on a six-point scale.

The mechanism is close prior art for retained conversation provenance and for connecting a recorded assertion to the implementation it influenced. The recorded prompt is evidence of communicated intent, not proof that the rationale is sound or current; human-judgment decision-record fields remain for people to complete. Participants did not use the tool directly, and the evaluation does not establish better understanding, intent accuracy, architecture quality, or source-independent practice.

Review basis (9 November 2026): primary metadata and selected full-text sections on Tasklets, mapping and history, decision-record export, design iterations, participant evidence, and limitations.

### 1.3 Code comprehension and software visualization

**Gao, J., Xue, Y., Xie, X., Cao, J., et al. (2026). _Understanding Codebase like a Professional! Human–AI Collaboration for Code Comprehension._ ICPC 2026.**

Introduces CodeMap, an LLM-supported environment for hierarchical codebase understanding informed by interviews with professional code auditors.

CodeMap provides dynamic information extraction and interactive switching between abstraction levels.

Very close prior art for PostCode's projected codebase views.

Important distinction: its usage scenario retains a conventional VS Code verification workflow; PostCode instead aims to support architectural investigation without presenting programming-language source to the human.

**Merino, L., Ghafari, M., & Nierstrasz, O. (2018). _Towards Actionable Visualization for Software Developers._ Journal of Software: Evolution and Process, 30, e1923.**

Merino et al. identify the effort involved in finding an appropriate visualization and connecting it to a developer's immediate task as barriers to the adoption of software visualization.

This explains part of the changed economics of obtaining representations in agent-mediated development, rather than a distinctive benefit over capable agent chat. See [`research.md`](research.md#4-why-agent-mediated-development-changes-the-problem).

**Merino, Ghafari, & Nierstrasz (2026). _Towards Actionable Visualization: Ten Years Later, What Generative AI Changes and What It Cannot._ VISSOFT 2026, Visions track; author version arXiv:2608.22151.** [Paper](https://arxiv.org/abs/2608.22151) · [Conference program](https://vissoft.io/2026/program.html)

Revisits actionable visualization in light of generative AI, discussing the sharply reduced cost of purpose-built, question-specific views, AI assistance in translating developer questions into representations, visualization within agentic workflows, and requirements for faithful, traceable evidence.

Exceptionally close conceptual prior art for PostCode's rationale. The overlap extends beyond visualization economics and automatic selection to continuous, question-driven exploration and navigable views embedded in agent-mediated development. The paper explicitly points to Glamorous Toolkit and moldable development as existing work in this direction. Sustained conceptual interaction therefore cannot be assumed to distinguish PostCode on its own. PostCode should investigate particular interaction choices, epistemological contracts, and conditions of usefulness against this prior work. Read alongside the authors' 2018 paper and [`research.md`](research.md#4-why-agent-mediated-development-changes-the-problem).

Design implication: the proposed division between AI-assisted question formulation and established rendering machinery, together with checkable mappings and navigable evidence, supplies design rationale to compare—not just a prediction of cheaper visualization. For PostCode, a useful question is which parts of an investigation need interpretation and which can preserve a directly checkable connection to evidence. Deterministic rendering alone does not establish the architectural meaning of its input.

Review basis: full author-version text and official conference program in the earlier review; [v1 sections III–IV](https://arxiv.org/html/2608.22151v1) rechecked for design rationale on 5 November 2026. This is a vision and research-agenda paper; its arguments about changed economics are not themselves evidence that PostCode's workflow is effective.

**Nierstrasz, O., & Gîrba, T. (2024). _Moldable Development Patterns._ arXiv:2409.18811; Glamorous Toolkit, an ongoing software project.** [Paper](https://arxiv.org/abs/2409.18811) · [Project](https://gtoolkit.com/) · [Method](https://book.gtoolkit.com/moldable-development-ejn67l5cdqh83kegi9umt1mdd)

Moldable development makes contextual analysis and interaction tools inexpensive to construct so that developers can investigate software through a live, explorable domain model. The patterns paper draws on several years of experience with open-source and industrial systems. Current Glamorous Toolkit materials explicitly address reducing code reading, constructing contextual tools with AI, and incorporating those tools into human–agent interaction.

Close prior art for task-specific representations, conceptual investigation, and tools that evolve with the software and the questions asked of it. It is relevant to PostCode's questions about sustained use, development from inception, and the distinction between independently useful conceptual clarity and tool-relative projectability. A comparison should examine who constructs and selects tools, how qualifications reach users, how views remain grounded as inputs change, and whether architectural work requires implementation-language proficiency. These are comparison questions, not established advantages for PostCode. Glamorous Toolkit merits assessment as a possible interaction comparator alongside systems focused on analysis infrastructure.

Design precedent: the patterns organize experience into problems, competing considerations, solutions, examples, and consequences. Simple View and Throwaway Analysis Tool prioritize the immediate information need before richer presentation or reuse; Project Diary connects investigation with retained working material. For PostCode, these suggest examining when retention earns its cost and when a temporary view suffices. They also provide a model for articulating design knowledge beyond a feature inventory.

Review basis: earlier abstract and project/method documentation review; extended on 5 November 2026 to selected [v1 text](https://arxiv.org/html/2409.18811v1): introduction, Moldable Tool and Custom View, the process patterns, and conclusion. The patterns are grounded in authors' reported experience and GT examples; implementations and underlying experience were not independently validated. Their live-programming setting does not establish source-independent architectural practice or general effectiveness.

**Hansen, M., Issa, K., & Hasselbring, W. (2026). _A Chat Assistant for Software Exploration in a 3D Software Visualization._ VISSOFT 2026 research-track program; author version arXiv:2610.09901, submitted 7 October 2026.** [Paper](https://arxiv.org/abs/2610.09901) · [Program](https://vissoft.io/2026/program.html) · [Artifacts](https://doi.org/10.5281/zenodo.20729543)

ExplorViz integrates natural-language questions and tool-triggered navigation, highlighting, settings, and visual restructuring. An eleven-person study, mostly students, reports favorable perceptions for simpler operations and mixed restructuring results. Restructuring concerns the visualized model; this does not establish implementation changes or sustained software development.

Direct prior art for delegating interaction with program views. A bounded comparator could distinguish choosing information, manipulating a presentation, and changing a conceptual model. Perceived explanation correctness does not establish factual accuracy or an equivalent epistemological contract.

Review basis (19 October 2026): selected author-version sections IV and VI, including tasks, discussion, and validity threats; official September program. Study conducted December 2025; indexed artifact v2 dates to June 2026, so October's preprint is not evidence of a new implementation release. Artifact contents and implementation not independently assessed.

**Kim, S. G., & Kim, H. (2026). _ABRA: Agent-Bound UI for Human–Agent Communication beyond Chat with Reusable Views._ Preprint, arXiv:2610.30780; submitted 22 October 2026.** [Paper](https://arxiv.org/abs/2610.30780) · [Prototype](https://github.com/megagonlabs/abra)

Introduces shared interactive canvases in which reusable graph, table, text, and display views receive task-specific semantic bindings published as state. Humans and agents can act on the same referents through direct manipulation as well as chat, while local presentation effects are separated from consequences that an owning agent resolves.

This is close conceptual prior art for representations as a two-way human–agent working surface, rather than generated explanations alone. A bounded PostCode comparison could test whether explicit interaction meanings and cross-view referents help express architectural intent, and what additional provenance and qualification are needed when a manipulation may cause a software change.

Review basis (26 October 2026): selected full-text sections on the interaction model, prototype, demonstration, experiments, results, and limitations. The experiments test four models' one-turn ability to author and operate canvases using structural checks and an LLM judge. They do not evaluate human interpretation, user experience, software-development outcomes, or sustained use.

**Archbird (2026). Technical software project.** [Website](https://archbird.org/)

Describes a deterministic, language-neutral repository model with provenance, uncertainty and completeness information; query-oriented projections; an explorer; live updates; test evidence; and structural comparison across repository states.

Exceptionally close technical prior art for PostCode's proposed machinery. Its documentation also describes human-facing exploration and structural planning, so the extent of interaction overlap should be investigated rather than inferred from an architecture-tool label. Two separate assessments may be useful: whether its analyses could supply PostCode with information while preserving PostCode's contracts, and whether its existing interface offers a useful comparison for particular human development tasks. The former requires checking captured evidence, qualifications, language semantics, and integration with PostCode's observation requirements; the latter requires suitable tasks and outcomes. Neither suitability is established by the advertised feature set.

Review basis: project documentation; implementation, maturity, and actual guarantees not independently assessed.

**Roteiro (2026). Technical software project.** [Website](https://roteiro.dev/)

Describes a repository knowledge graph that distinguishes deterministically *derived* relationships, *authored* assertions, and *inferred* semantic relationships with provenance. It exposes structured and natural-language queries and generated views for humans and agents.

Close prior art for provenance categories overlapping PostCode's derived facts, recorded assertions, and interpretation. PostCode's [epistemological contract](product-design.md#22-epistemological-contract) additionally distinguishes how information was obtained from what it establishes, including scope, completeness, observed executions, and unavailable analysis. Deterministic extraction alone does not establish semantic correctness or completeness. Whether Roteiro preserves equivalent distinctions and how they reach human-facing views require further assessment; the shared taxonomy alone establishes neither equivalence nor a distinctive PostCode contribution.

Review basis: project documentation; implementation and analysis guarantees not independently assessed.

**SwiftUI Semantic Audit (2026). Technical software project.** [Website](https://swiftui-audit.dev/)

Describes deterministic extraction of SwiftUI architecture and ownership/data-flow evidence, qualified analysis, live freshness checks, and semantic differences between repository snapshots.

Direct overlap with epistemologically qualified projections, semantic diffs, and supervision of agent changes, though in a narrower language ecosystem. Inspect actual implementation and analysis guarantees before drawing detailed distinctions.

Review basis: project documentation, including its stated analysis limits; implementation not independently assessed.

**Cygnus (2026). In-development technical project.** [Overview](https://www.river.io/cygnus/)

Describes provenance-bearing repository observations, a persistent knowledge graph, disposable projected views, immutable revisions, and relationships between tests, coverage and program elements across several languages.

Strong architectural overlap with evidence-bearing projections. Because the system is described as in development, advertised capabilities should not automatically be treated as demonstrated results.

Review basis: project overview; implementation, maturity, and actual guarantees not independently assessed.

**tt-a1i/archify (ongoing). _Archify._ Open-source technical project; newly inspected 12 October 2026, release date not established.** [Repository](https://github.com/tt-a1i/archify)

Documents agent-generated interactive diagrams from descriptions or repositories, typed intermediate representations, revision-pinned source links, and iterative refinement. Its stated validation covers artifact structure and presentation; those checks must not be mistaken for proof of architectural meaning or runtime behavior.

A concrete candidate for assessing presentation reuse and question-driven interaction separately. It adds a practical comparison opportunity to PostCode's representation-selection questions, without establishing equivalent epistemological contracts or sustained-use effectiveness.

Review basis: repository README sections on source-backed architecture, interaction, and validation; implementation not inspected or run. Newly found, not established as newly released.

**Graphify — provisional lead (not yet verified as identified).**

An earlier research-watch report described a cross-language code knowledge graph joining extracted and inferred relationships with provenance and interactive architecture views. The supplied Graphify URL was not confidently attributable to that code-analysis project. **Do not treat as confirmed prior art until the specific repository or publication is identified.**

**Văduva, et al. (2026). _Code2UML: Agentic LLMs with Context Engineering for Scalable Software Visualization._ arXiv:2605.24453.**

Generates multiple UML views from repositories across Java, JavaScript, PHP and Python using deterministic IR processing plus specialized agents.

Especially interesting for PostCode because it demonstrates multi-language projection generation while reporting high relationship precision but deliberately limited entity recall.

This provides a concrete nearby example of useful projections whose incompleteness matters.

**CodeSkyline (VISSOFT 2026). _A Code-Map Visualization with Juxtaposed Views for Program Comprehension and Navigation._**

Provides multiple simultaneous code-map views and abstraction levels, with a four-week adoption study in which some participants continued using the system occasionally.

Relevant precedent for multi-view and sustained-use software visualization, while remaining primarily within the conventional program-comprehension/navigation framing.

**Parveen, R., Arora, N., Zhang, Z., Mäkelä, K., & Abrahamsson, P. (2026). _Req-Space: A User Study of Interactive Visualisations for Requirements Review._ Preprint, arXiv:2611.05437; submitted 3 November 2026.** [Paper](https://arxiv.org/abs/2611.05437)

In a fixed-order two-phase study, 20 participants reviewed a fictional 40-requirement specification and change request using source documents and then revisited the tasks with interactive semantic and traceability views. Seventeen added at least one source-supported item or pair; 58 of 69 assessable additions were supported, and seven decision rationales were stronger in the second phase, including five without a changed decision category. Some participants misread proximity as dependency or treated trace links as inferred effects.

The study offers a useful direct-human evaluation pattern for PostCode: distinguish broader recorded coverage, changed decisions, and stronger justification; keep relationship meanings and source context visible; and test false completeness explicitly. Its fixed order prevents causal attribution to Req-Space, and a fictional requirements review does not establish architectural practice, collaborative use, or usefulness without source materials.

Review basis (9 November 2026): primary metadata and selected full-text sections on study design, results, relationship misinterpretation, discussion, and threats to validity.

**Storey, M.-A. (2026). _Cognitive Tours: Making Understanding a Deliverable in AI-Assisted Development._ Preprint, arXiv:2611.08456; submitted 5 November 2026.** [Paper](https://arxiv.org/abs/2611.08456)

Cognitive Tours is a web prototype for human-curated paths connecting goals, user needs, design decisions, code, tests, and open questions. AI functions audit possible staleness and suggest candidates, while people verify evidence, write rationale, and choose a route. Six months of author self-use, including one detected contradiction between a decision and implementation, ground the design proposition.

This is a close constructive comparator for making partial understanding persistent and revisable. It proposes productive friction, human curation, and explicit open questions as design knowledge rather than claiming an automatically recovered or complete account. The self-use episode and planned evaluation do not yet establish reduced cognitive debt, human effectiveness, or superiority over chat, diagrams, or ordinary notes.

Review basis (9 November 2026): primary metadata and full paper, including design goals, interactions, self-use episode, risks, and proposed evaluation agenda.

### 1.4 Architecture and agent-generated software

**Konrad, P. M., Adam, T. L., Terrenzi, R., & Ayvaz, S. (2026). _Architecture Without Architects: How AI Coding Agents Shape Software Architecture._ arXiv:2604.04990.**

Argues that coding agents make consequential architectural decisions implicitly through implementation and prompt interpretation.

Relevant motivation for PostCode's supervisory goal: humans may need representations that expose architectural consequences without reconstructing them manually from source.

**Vasilevski, K., Dong, X., Rombaut, B., et al. (2026). _Beyond Correctness: Enhancing Architectural Reasoning in Code LLMs via Scalable Labeling with Agentic Judgment._ arXiv:2606.14948.**

Examines architectural understanding and architectural quality of agent-generated patches rather than functional correctness alone.

Relevant to the broader distinction between source-level correctness and higher-level program properties.

**Sapunov, G. (2026). _Theory of Code Space: Do Code Agents Understand Software Architecture?_ arXiv:2603.00601.**

Studies whether agents construct and maintain structured beliefs about codebase architecture while exploring repositories.

Particularly relevant to the distinction between repeatedly reconstructing relationships from source and externalizing useful program structure.

Unlike PostCode, the subject is primarily the agent's architectural understanding rather than the human-facing representation.

**Irion, J., Leugers, M., Hartwig, P., et al. (2026). _Architectural Constraints Alignment in AI-Assisted, Platform-Based Service Development._ CAiSE Workshops 2026 / arXiv:2605.04973.**

Addresses architectural constraints that general-purpose coding agents may miss and uses structured retrieval/scaffolding to improve alignment.

Relevant to the growing recognition that functional source generation alone is insufficient for reliable agent-mediated engineering.

**Klatt, F., Di Grazia, L., & Schneider, J. (2026). _A-SAW: The Agentic Software Architecture Workflow._ Preprint, arXiv:2610.13647; submitted 9 October 2026.** [Paper](https://arxiv.org/abs/2610.13647)

Agents draft architectural documents from a versioned C4 model, typed catalog, context and templates under mandatory human review. In one organization, a study of 45 documents, including 13 matched regenerations, and 13 practitioner interviews reports stronger rubric scores but conditional trust.

Direct prior art for retained architectural artifacts and qualified human review. Compare grounding, gap marking and revision history, while independently assessing factual fidelity and useful scope: regenerated documents can narrow their inherited scope and are scored against it. Polished documentation does not establish sound design.

Design contribution: section 5.2 separates principles the authors derive from their study—typed naming contracts and directing review toward inference—from literature-supported but untested principles. It presents their composition as the contribution. This gives PostCode a concrete precedent for stating a mechanism's evidence separately from the rationale for combining mechanisms; the study's confounds still limit causal attribution.

Review basis: selected full text reviewed 26 October; [v1 sections 3.6, 4.1 and 6](https://arxiv.org/html/2610.13647v1) rechecked 5 November 2026. Rich-context regeneration, a non-blind rater from the generator's model family, and bundled template/catalog/agent changes limit causal interpretation. Neither greenfield design nor source-independent human practice was tested. Sections 3.1–3.2 and 5.2–5.3 additionally inspected on 5 November for design rationale, principle provenance, and boundary conditions. No replication.

**Sas, C., Mitrović, S., Barth, F., Rehm, G., & Salani, M. (2026). _The Code of Theseus: Can Agents Rebuild Software from Recovered Design Documents?_ Preprint, arXiv:2610.20068; submitted 14 October and revised 15 October 2026 (v2).** [Paper](https://arxiv.org/abs/2610.20068) · [Artifacts](https://github.com/SasCezar/code-theseus)

Recovers intent, requirements and architecture artifacts. Reconstruction on 29 Python libraries found no significant held-out test improvement (33.7% to 35.8%); non-contract module F1 rose from 0.54 to 0.63 on 24 eligible libraries. Co-location of shared classes/functions did not significantly improve.

A candidate test of what architectural accounts convey to another agent, separating structural fidelity from observed behavior. Recreating a module set does not establish better design, human understanding, or historically true stakeholder intent.

Review basis: selected v2 text reviewed 26 October; [section VI-C, Table V and section VIII](https://arxiv.org/html/2610.20068v2) rechecked 5 November 2026. Artifact ratings use a model judge; the round trip uses one agent and small libraries, and architecture has no unique reference. Artifacts and pipeline not run.

**Golatkar, A., Achille, A., Zabounidis, R., et al. (2026). _Skeleton Coding: Program Structure as a Specification for Agents._ Preprint, arXiv:2610.38214; submitted 28 October 2026.** [Paper](https://arxiv.org/abs/2610.38214)

Skeletons constrain modules, types, interfaces and signatures alongside behavior. Across four models and three reconstruction benchmarks, the best structural specifications reduce mean test error by 48.4% relative to the best behavioral specifications.

Prior art for architectural structure as an active constraint. An agent-facing experiment could compare equivalent commitments supplied as skeletons, PostCode accounts or prose, controlling information and tool access. A human-practice comparison must keep both human-facing conditions source-independent; skeletons can be agent inputs, not a requirement that humans read code. Fidelity, author effort and understanding need separate measures.

Review basis: selected text reviewed 2 November; [v1 section 4 and Appendices A, B and D](https://arxiv.org/html/2610.38214v1) rechecked 5 November 2026. Native skeletons use source-language syntax. Reconstruction and tests do not establish human architectural practice; public-project training contamination remains possible. The proposed comparison is ours, not a tested human workflow. No replication.

**Zhang, Z. (2026). _Architectural Debt Enforcement under Incomplete Observation: A Controlled Study of Ratchets and Evidence Qualification._ Preprint, arXiv:2610.41276; submitted 30 October 2026.** [Paper](https://arxiv.org/abs/2610.41276)

Studies an architectural-debt decision contract that separates observation qualification, prohibited relation identity, inherited debt, and authorized baseline updates. In four TypeScript repositories, a programmatic reference qualified 166 of 240 fixed files with exact edge agreement while leaving 74 as unknown; constructed scenarios and preserved failures test why successful execution or a narrow integrity check cannot substitute for qualified observation.

The work is a concrete comparison for PostCode's epistemological status discipline. A structural constraint view should expose what was observed, what policy applies, what prior debt is tolerated, who may change the baseline, and which relations remain unknown. The result also cautions against turning one observer's agreement with a reference into a language-wide guarantee or a human semantic judgment.

Review basis (2 November 2026): metadata and selected full-text sections on the decision contract, controlled scenarios, diagnostics, release provenance, human-review boundary, discussion, and threats. The reference shares TypeScript-resolution assumptions, was corrected after observing outcomes, repository sampling is not probabilistic, and the study does not establish language completeness, natural maintenance effectiveness, or human usefulness.

**Jabeen, R., Ericsson, M., Duan, Y., & Wingkvist, A. (2026). _What Carries Architectural Signal? A Code-to-Architecture Mapping Study._ Preprint, arXiv:2610.41628; submitted 30 October 2026.** [Paper](https://arxiv.org/abs/2610.41628)

Studies assignment to reference modules in ten Java/C/C++ systems. Directory-based prediction already performs strongly; richer graph processing does not consistently correct its errors. This motivates simple baselines and separate evaluation of architectural exceptions when testing PostCode's account quality. Matching one decomposition is not recovering unique architectural truth or design intent.

Review basis (5 November 2026): metadata and selected [v1 text](https://arxiv.org/html/2610.41628v1), including problem formulation, evaluation implications and validity threats. Transductive access to the observed graph, one reference per system, and imperfect source/reference alignment limit transfer to evolving repositories. Artifacts not run. Reassessed from the 2 November screened leads because account-quality evaluation is now explicit; not a new publication alert.

**Wang, W., Jin, Z., Li, J., Jin, D., Tian, H., Fang, Y., Ye, W., & Zhao, T. (2026). _ASNER: Software Architecture Recovery with Adaptive Semantic Neighborhoods and Evidence-Grounded Refinement._ Preprint, arXiv:2610.36894; submitted 27 October 2026.** [Paper](https://arxiv.org/abs/2610.36894)

Four read-only architecture tools expose recovered responsibilities and evidence to LocAgent, which retains its source tools. In 24 issues from two repositories, localization improves on Dask and ties on pypdf. This is a concrete comparator for specialized investigation supplied to another agent, beyond potential analysis reuse.

Review basis (5 November 2026): metadata, [v1 method overview, section 5.4 and Appendices H.6/I](https://arxiv.org/html/2610.36894v1). Reference agreement and localization do not establish human usefulness or design quality. Mandatory initial architecture retrieval changes the workflow alongside added tools; static evidence and generated responsibilities have omissions. Artifacts not run. Reassessed from the 2 November leads.

**Tacheny, N., Mens, T., & Mahmoudi, S. (2026). _Mind the Intent Gap: A Methodology for Collaborative Agent-Driven Software Engineering._ Preprint, arXiv:2610.37340; submitted 27 October 2026.** [Paper](https://arxiv.org/abs/2610.37340)

CAIA separates shared stated intent, implementation, validation, and reviewed knowledge-base updates. Assistant, build and knowledge-agent roles make it a conceptual comparator for PostCode's contribution within an external design process. Assess how rationale survives a change and how accepted intentions remain distinguishable from observed implementation; shared records do not themselves establish either correctness or agreement.

Design proposal: consolidation is an explicit, reviewed part of a change, including decisions made during implementation. This provides a candidate mechanism for preventing retained intent from lagging behind development. For PostCode, inspect one change where implementation revises an assumption: what should be retained, who endorses it, and how does it remain distinct from implementation evidence? This is a proposed comparison, not an observed benefit.

Review basis (5 November 2026): metadata and [v1 sections 3–6](https://arxiv.org/html/2610.37340v1); sections 5–6 reread during the design-knowledge reassessment. Reported industrial use and subjective reception precede a planned controlled evaluation. Retained as a provisional process comparison, not efficacy evidence. Reassessed from the 2 November leads because retained knowledge and external collaboration now have explicit roles; no new empirical result is claimed.

**Sepidband, M., Shin, J., Wang, S., & Hemmati, H. (2026). _How Should Agents See Code? Rethinking Code Representations for Agentic Software Engineering._ Preprint, arXiv:2611.07286; submitted 5 November 2026.** [Paper](https://arxiv.org/abs/2611.07286)

Compares AST, call-graph, dependency, documentation-enriched, and hybrid repository maps with raw repository tools for one Claude Code configuration across four benchmark families. All maps improved fault-localization recall@10 and reduced tokens, while repair, test-generation, and security-patching effects varied by task and every map increased latency in the reported security setting. The study argues that a representation helps when its relations match the current bottleneck; a broader hybrid can also add distracting material.

This is useful evidence for task-dependent analysis selection and for exposing reusable repository projections to agents within a shared practice. The treatment combines representation content, instructions, and a map-first hook, and uses one model configuration with one run per instance. Benchmark success and token use do not establish account fidelity, patch quality, human usefulness, or the no-source premise.

Review basis (9 November 2026): primary metadata and selected full-text sections on workflows, benchmarks, results, behavioral analysis, discussion, and validity threats.

### 1.5 LLMs and software architecture — broader background

**Schmid, L., Hey, T., Armbruster, M., et al. (2025). _Software Architecture Meets LLMs: A Systematic Literature Review._ arXiv:2505.16697.**

Reviews LLM applications to software-architecture tasks including design generation, classification and pattern detection.

Useful starting point for mapping the broader architecture/LLM literature and locating older work that may overlap individual PostCode projections.

### 1.6 Human–AI debugging and evidence presentation

**Shen, S., Lu, S., Shen, L., & Luo, Y. (2026). _Debugging Defective Visualizations: Empirical Insights Informing a Human–AI Co-Debugging System._ CHI 2026.**

Not directly about source-code projection, but potentially useful methodological prior art concerning how humans and AI divide investigative/debugging work and how evidence is presented during that process.

This should be read before deciding how strongly it belongs in PostCode's eventual related work.

**Liang et al. (2026). _Test-Driven Approaches to Software Engineering with Large Language Models: A Survey of Phases, Tasks, and Agent Skills._ Preprint, arXiv:2609.12012.** [Paper](https://arxiv.org/abs/2609.12012)

Surveys how tests provide feedback and evidence in LLM-assisted software engineering. Emphasizes distinctions among test availability, feedback validity, evaluation independence, and the conclusions justified by passing tests.

Relevant to PostCode's separation of test intent, test realization, execution evidence, and confidence in inferred behavior. This does not itself propose test intent as a human-facing program projection, but it cautions against treating test success as a generic correctness guarantee.

Review basis: arXiv abstract; full survey not assessed.

**Qi, Z., Li, H., Chen, J., Chen, H., Zhao, Y., Zhu, D., Cerny, T., Liu, B., & He, S. (2026). _Merged, Not Measured: An Empirical Study of Performance Issues Fixed by Coding Agents._ Preprint, arXiv:2609.37985; submitted 29 September 2026.** [Paper](https://arxiv.org/abs/2609.37985)

Studies 1,262 performance fixes and re-executes selected accepted and rejected changes. The merged re-execution sample was purposive, not representative; passing tests and merge decisions did not establish claimed performance or preservation of untested behavior.

Relevant to qualified test evidence and conceptual change review: distinguish a claimed benefit, the property a test checks, and the behavior actually observed. This supplies candidate evaluation cases, not evidence that a projection interface improves supervision.

Review basis (12 October 2026): arXiv metadata and selected full-text sections, including re-execution design, test evidence, and validity threats; artifacts not executed.

**Peng, H., Calvo, R., Kalu, K. G., & Davis, J. C. (2026). _How Do Coding Agents Optimize Software and Report Performance Validation? A Large-Scale Empirical Study of Open-Source Pull Requests._ Preprint, arXiv:2610.03969; submitted 2 October 2026.** [Paper](https://arxiv.org/abs/2610.03969)

Compares 1,130 agentic and 1,130 human-authored performance PRs. Validation reports often lack quantitative metrics or quantified trade-offs. The study analyzes reported evidence; it does not execute changes or verify performance claims.

Relevant to PostCode's distinction between recorded assertions and observations: a benchmark mentioned in a PR is not an independently established measurement. Read alongside Qi et al.; the studies use different sampling and validation methods, so their percentages are not interchangeable.

Review basis (12 October 2026): arXiv metadata, abstract, and selected full-text sections on reported metrics and validity threats; no independent replication.

### 1.7 Established traditions requiring further assessment

These traditions contain potential conceptual precedents, methods, and comparators. Their relevance depends on the particular research question, rather than on whether they address coding agents:

- explainable AI and uncertainty/provenance visualization;
- information provenance;
- proof-carrying or evidence-carrying systems;
- abstract interpretation and soundness/completeness of static analyses;
- software architecture recovery;
- architecture conformance;
- program comprehension;
- software cartography;
- live programming;
- projectional editors;
- bidirectional transformations/lenses;
- model-driven engineering;
- literate programming;
- intentional programming;
- structure editors;
- semantic IDEs;
- software visualization;
- change-impact analysis;
- conceptual/semantic diffs.

These traditions predate agentic programming but may contain important prior art for individual PostCode ideas.

In particular, the **epistemological-status discipline** should eventually be compared not only with contemporary LLM systems but with older work on static-analysis guarantees, provenance, uncertainty visualization and evidence-bearing software tools. That literature may prove more relevant to this aspect of PostCode than current AI-programming work.

### 1.8 Architectural descriptions, multiple perspectives, and evaluation

**ISO/IEC/IEEE (2022). _42010:2022 — Software, systems and enterprise — Architecture description._ Edition 2, November 2022.** [Official record and scope](https://www.iso.org/standard/74393.html)

Distinguishes an architecture from a description expressing it and specifies requirements for descriptions, viewpoints and related description mechanisms without prescribing a particular notation, process or tool. This is foundational vocabulary for comparing PostCode's accounts, not evidence that a conforming description is factually correct or useful.

Review basis (5 November 2026): ISO's public scope and edition metadata only; the full standard was not reviewed. No conformance claim or detailed mapping of PostCode concepts to standard requirements is made. Newly assessed older work; detailed comparison remains open.

**Nuseibeh, B., Kramer, J., & Finkelstein, A. (1994). _A Framework for Expressing the Relationships Between Multiple Views in Requirements Specification._ IEEE Transactions on Software Engineering.** [Author-hosted paper](https://finkelstein.live/papers/tse94.icse.pdf)

ViewPoints retain partial specifications, their notations, development processes and histories. Explicit relationships support checks and information transfer across separately maintained perspectives, including inconsistency handling. This is direct conceptual precedent for overlapping retained accounts and cross-perspective investigation without a required global representation. PostCode's inferred correspondence and evidence qualifications still need comparison with those rule-governed relationships.

Design precedent: detecting inconsistency need not force its immediate removal; premature consistency can discard useful information. Section 6.1 also describes deriving general interaction rules from implemented, hard-coded checks, while acknowledging that the general integration extension remained unimplemented. This is a concrete construction-to-concept example. For PostCode, compare how a conflicting pair of retained accounts can remain usable while its disagreement and resolution status stay visible.

Review basis (5 November 2026): selected author-version sections 1–2 and 5 on the framework and interaction rules; extended to sections 5.3–5.4 and 6.1–6.2 during the design-knowledge reassessment. Tool and case-study claims were not independently assessed. The work concerns requirements specification, not contemporary coding-agent collaboration. Newly assessed older work; compare one conflicting-account example before claiming a distinctive mechanism.

**Kazman, R., Klein, M., & Clements, P. (2000). _ATAM: Method for Architecture Evaluation._ CMU/SEI-2000-TR-004, August 2000.** [Official report](https://sei.cmu.edu/library/atam-method-for-architecture-evaluation/) · [Full text](https://sei.cmu.edu/documents/629/2000_005_001_13706.pdf)

Uses stakeholder goals, prioritized scenarios and quality attributes to investigate architectural risks, sensitivity points and trade-offs. It supplies a methodological precedent for deciding what to investigate and how to evaluate alternatives, beyond describing structure. A bounded PostCode task could test whether qualified accounts help expose consequential trade-offs and missing evidence.

Review basis (5 November 2026): report metadata, overview, method steps and conclusions. This is an evaluation method, not proof that PostCode improves decisions or that architecture can be practiced without programming experience. Its dependence on stakeholder participation, architectural expertise and adequate inputs remains material. Newly assessed older work; adapting scenarios does not require adopting the full organizational process.

## 2. Positioning Hypotheses

PostCode approaches **software design and architecture as human practices in collaboration with coding agents**, without requiring proficiency in conventional programming-language source. A leading hypothesis concerns shared architectural representations and partial, qualified retained accounts; visual artifacts are one candidate form. Investigating that form calls for closer assessment of established architectural viewpoints and notations (including C4, UML behavioral views, and ISO/IEC/IEEE 42010), architecture description, model-driven approaches, and visual programming systems. These are established lines of work, not PostCode novelty claims. The [foundational entries](#18-architectural-descriptions-multiple-perspectives-and-evaluation) begin this assessment; detailed notation comparisons and evidence of useful interaction remain open.

Assessments should distinguish the [three analytic levels](research.md#specialized-architectural-expertise): direct human investigation, architectural-account quality, and contribution to collaborative architectural practice. These are not mandatory efficacy endpoints; the [likely contribution model](research.md#likely-contribution-model) also guides comparison of design requirements, mechanisms, implementation insights, and bounded lessons. PostCode may contribute specialized investigation to conversations conducted elsewhere; it need not host the collaboration.

The practical baseline includes **capable agent chat with repository access, ordinary agent-generated diagrams, and maintained notes**. Comparing PostCode against a deliberately limited text-only chat would not isolate its contribution.

These are provisional distinctions to test against the literature, not novelty claims.

### 2.1 Versus conventional software visualization

PostCode is not primarily asking:

> Can a visualization make a program easier to understand?

It asks:

> What is required for shared, qualified architectural representations to support human reasoning and design with coding agents, and what do they contribute beyond capable agent chat, including ordinary diagrams and notes?

It also asks what systematic, qualified and retained representations contribute when capable agents can already generate and select inexpensive task-specific visualizations.

This describes PostCode's emphasis, not a boundary of software-visualization research. Merino et al. (2026) and moldable development also address continuous, contextual interaction; their overlap must be considered when evaluating any claimed distinction.

### 2.2 Versus capable conversational coding agents

Capable coding agents can already inspect repositories, answer questions, explain behavior, propose designs, generate diagrams, and maintain ordinary architectural notes. These capabilities are not unique to PostCode, nor is generating a structured description sufficient to establish a contribution.

PostCode investigates what is required to incorporate such explanations into a **qualified, navigable projection system**, and when doing so helps or hinders human architectural reasoning and collaboration. Candidate mechanisms include preserving the captured program basis of an account, distinguishing mechanical analysis from recorded intent and interpretation, retaining supporting evidence and limitations, enabling follow-up investigations through stable referents, recording corrections, and comparing architectural perspectives and revisions.

Some or all of these practices may be reproduced through careful prompting, ordinary documents, and existing agent tools. Actual architectural tasks and that strong conversational baseline should inform claims about usefulness. Construction and bounded use may also reveal requirements, implementation constraints, or failures without establishing comparative superiority; a separate interface or machine-readable model does not itself establish a contribution.

### 2.3 Versus AI code review

PostCode is not primarily asking:

> Did the agent's patch contain a defect?

It asks:

> What does the program now look like at the levels relevant to the human supervising it?

These questions overlap in practice. Whiteboard's conceptual explanations and decision records, for example, extend beyond defect detection. Comparisons should identify the actual supported investigation and supervision tasks rather than treating code review as a uniformly narrower activity.

### 2.4 Versus architecture recovery

Architecture recovery can supply methods, candidate accounts, and account-quality comparators for PostCode. PostCode does not assume that one recovered architecture is the privileged higher-level representation: different questions may require different lenses and projections, including accounts of proposed and intended designs. Agreement with a reference decomposition, usefulness for direct investigation, and effects on architectural decisions are separate evaluation questions; multiple perspectives alone do not establish novelty.

### 2.5 Versus agent knowledge representations

PostCode studies human architectural practice, including shared accounts that design and implementation agents can consume within that practice. It does not pursue optimal agent representations as an independent objective. Agent-facing work may nevertheless inform account quality, investigative methods, and collaborative outcomes; its relevance should be judged at those levels rather than excluded by who consumes the representation.

### 2.6 Versus model-driven development

PostCode does not initially make a higher-level model authoritative or generate implementation from it. Conventional source remains canonical during the experiment.

### 2.7 Potential distinctive conjunction

The following dimensions describe PostCode's intended research emphasis and support comparison with related work. They are not a checklist that every contribution must demonstrate:

- direct human architectural investigation and sustained human–agent design and evaluation;
- specialized architectural accounts available within external design processes;
- architectural practice without presenting programming-language source to the human;
- multiple task-dependent lenses, qualified projections, and partial retained architectural accounts;
- automatic selection of lenses and presentations from human information needs;
- epistemological status and provenance visible at the point of every claim;
- explicit accommodation of incomplete and language-dependent analyses;
- tests treated as projected evidence rather than merely pass/fail gates;
- qualified comparisons among implemented states, hypothetical alternatives and intended designs;
- contrasting formative contexts across projects and, as opportunities arise, languages;
- explicit comparison with capable coding-agent chat, including diagrams and notes, and willingness to find that chat is sufficient for some work.

Several of these dimensions already overlap with ViewPoints, architecture-description and evaluation methods, moldable development, and the other work above. Whether any particular conjunction, mechanism, or finding is distinctive requires a specific comparison; this list does not establish an unoccupied research territory.

### 2.8 Implications of recent prior art

Recent publications and project descriptions inform PostCode's constructive research and require precise attribution of overlapping ideas and design lessons. Repository representations, provenance categories, task-specific views, evidence graphs, semantic change representations, and test-to-code evidence have precedents. Their broad existence should not be presented as a PostCode invention. The entries above distinguish what was checked from what remains to be established about implementations, guarantees, and usefulness.

The central research question is stated in [`research.md`](research.md#5-research-questions):

> **What supports the effective practice of software design and architecture by humans collaborating with coding agents without requiring programming-language proficiency—and what does a shared, qualified architectural working environment contribute beyond capable agent chat?**

As [`research.md`](research.md#31-creation-continued-development-and-existing-software) emphasizes, this includes investigation of unfamiliar programs, continued development of existing software, and development from inception. In the last case, intentions, rationale, and implementation may co-evolve, rather than requiring conceptual structure to be recovered after the fact. Related spec-driven work is therefore relevant, not categorically separate.

This question overlaps with existing research agendas; it is not a residual territory established as novel by this bibliography. Possible contributions remain those described in [`research.md`](research.md#8-research-and-impact-goal) and [`research-strategy.md`](research-strategy.md#1-strategy-stance). The [constructive contribution model](research.md#likely-contribution-model) includes design and implementation knowledge, particular guarantees, compositions, interaction designs, and evidence about conditions of usefulness, even where the broad mechanisms have precedents. Each contribution needs comparison at the level of the actual claim. Negative, mixed, and conditional findings remain valid outcomes.

Assessing reuse and assessing a comparison interface are separate opportunities. Archbird is a candidate for both; Whiteboard and Glamorous Toolkit are also candidates for interaction comparisons. A bounded assessment could establish which capabilities are implemented, which guarantees hold, what integration would require, and which human tasks permit a meaningful comparison. These are candidates for the [roadmap](ROADMAP.md#37-assessing-related-systems), not implementation commitments or decisions to replace existing PostCode machinery. The [methodology](methodology.md#84-comparisons-and-reuse-assessments) distinguishes the evidence each assessment can supply.

