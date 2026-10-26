# PostCode: Related Work

This is a working account of research related to PostCode, not a systematic literature review.

Its purpose is to identify nearby research traditions, potentially overlapping systems, useful methodological precedent, and work that may sharpen PostCode's research questions. The bibliography and positioning hypotheses should evolve together as the project and literature review develop.

Review-basis notes identify the material checked for particular entries. An abstract or project description supports an account of what its authors report; it does not establish implementation maturity, analysis guarantees, or human usefulness. Entries without a review-basis note retain their earlier working status and should be checked before supporting a formal comparison. Dated notes below record the checks made for each entry.

## 1. Working Bibliography

### 1.1 Agentic software engineering and changing human roles

**Davis, J. C., Kalu, K., Peng, H., & Patil, P. V. (2026). _Model-Based Agentic Software Engineering (MAGE)._ arXiv:2608.25174.**

Particularly close conceptually. MAGE argues that increased implementation capacity makes explicit abstractions, evidence and engineering obligations increasingly important, and proposes externalizing purposeful representations rather than repeatedly reconstructing consequential properties.

Relevant distinction: MAGE primarily addresses governed agentic engineering and durable engineering structure; PostCode experimentally investigates the human inspection surface while initially leaving conventional code canonical.

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

### 1.3 Code comprehension and software visualization

**Gao, J., Xue, Y., Xie, X., Cao, J., et al. (2026). _Understanding Codebase like a Professional! Human–AI Collaboration for Code Comprehension._ ICPC 2026.**

Introduces CodeMap, an LLM-supported environment for hierarchical codebase understanding informed by interviews with professional code auditors.

CodeMap provides dynamic information extraction and interactive switching between abstraction levels.

Very close prior art for PostCode's projected codebase views.

Important distinction: its usage scenario still treats source inspection in VS Code as the verification surface; PostCode deliberately asks whether qualified projections themselves can support sustained investigation and supervision.

**Merino, L., Ghafari, M., & Nierstrasz, O. (2018). _Towards Actionable Visualization for Software Developers._ Journal of Software: Evolution and Process, 30, e1923.**

Merino et al. identify the effort involved in finding an appropriate visualization and connecting it to a developer's immediate task as barriers to the adoption of software visualization.

This is particularly relevant to PostCode's hypothesis that agent-mediated generation and selection may reduce the cost of obtaining task-specific representations. It provides prior art against which to test whether those changes, together with reduced incidental source familiarity during agent-mediated development, can make projections a routine working surface. The full rationale appears in [`research.md`](research.md#4-why-this-question-may-be-different-now).

**Merino, Ghafari, & Nierstrasz (2026). _Towards Actionable Visualization: Ten Years Later, What Generative AI Changes and What It Cannot._ VISSOFT 2026, Visions track; author version arXiv:2608.22151.** [Paper](https://arxiv.org/abs/2608.22151) · [Conference program](https://vissoft.io/2026/program.html)

Revisits actionable visualization in light of generative AI, discussing the sharply reduced cost of purpose-built, question-specific views, AI assistance in translating developer questions into representations, visualization within agentic workflows, and requirements for faithful, traceable evidence.

Exceptionally close conceptual prior art for PostCode's rationale. The overlap extends beyond visualization economics and automatic selection to continuous, question-driven exploration and navigable views embedded in agent-mediated development. The paper explicitly points to Glamorous Toolkit and moldable development as existing work in this direction. Sustained conceptual interaction therefore cannot be assumed to distinguish PostCode on its own. PostCode should investigate particular interaction choices, epistemological contracts, and conditions of usefulness against this prior work. Read alongside the authors' 2018 paper and [`research.md`](research.md#4-why-this-question-may-be-different-now).

Review basis: full author-version text and official conference program. This is a vision and research-agenda paper; its arguments about changed economics are not themselves evidence that PostCode's workflow is effective.

**Nierstrasz, O., & Gîrba, T. (2024). _Moldable Development Patterns._ arXiv:2409.18811; Glamorous Toolkit, an ongoing software project.** [Paper](https://arxiv.org/abs/2409.18811) · [Project](https://gtoolkit.com/) · [Method](https://book.gtoolkit.com/moldable-development-ejn67l5cdqh83kegi9umt1mdd)

Moldable development makes contextual analysis and interaction tools inexpensive to construct so that developers can investigate software through a live, explorable domain model. The patterns paper draws on several years of experience with open-source and industrial systems. Current Glamorous Toolkit materials explicitly address reducing code reading, constructing contextual tools with AI, and incorporating those tools into human–agent interaction.

Close prior art for task-specific representations, conceptual investigation, and tools that evolve with the software and the questions asked of it. It is relevant to PostCode's questions about sustained use, development from inception, and the distinction between independently useful conceptual clarity and tool-relative projectability. A comparison should examine who constructs and selects tools, how qualifications reach users, how views remain grounded as inputs change, and when source is used. These are comparison questions, not established advantages for PostCode. Glamorous Toolkit merits assessment as a possible interaction comparator alongside systems focused on analysis infrastructure.

Review basis: paper abstract and project/method documentation; the full patterns paper, implementation, and reported experience have not been independently assessed here.

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

Extends Architecture as Code with an agent that drafts documents from a versioned C4 model, typed element catalog, scoped context, and templates, followed by mandatory human review. In one large organization the study scores 45 documents, including 13 matched source-to-regeneration pairs, and interviews 13 practitioners after a task. Generated drafts were more uniform and scored higher on the study rubric, while traceability remained weakest and trust stayed conditional.

This is direct prior art for persistent shared architectural representations and for concentrating human attention where an agent must infer beyond repository evidence. It also demonstrates a quality–trust gap: structurally polished documentation does not establish that its design is sound. Compare a bounded PostCode architectural investigation with A-SAW's catalog grounding, explicit gap marking, versioned review, and treatment of intended versus implemented architecture.

Review basis (26 October 2026): selected full-text sections on the workflow, evaluation design, results, boundary conditions, and threats to validity. The comparison is associational; regenerated documents had rich existing context, one non-blind rater from the generator model family scored them, and templates, catalog, context, and agent effects are confounded. The study does not test greenfield design or a source-independent human interface.

**Sas, C., Mitrović, S., Barth, F., Rehm, G., & Salani, M. (2026). _The Code of Theseus: Can Agents Rebuild Software from Recovered Design Documents?_ Preprint, arXiv:2610.20068; submitted 14 October and revised 15 October 2026 (v2).** [Paper](https://arxiv.org/abs/2610.20068) · [Artifacts](https://github.com/SasCezar/code-theseus)

Recovers aligned stakeholder-intent, requirements, and C4-style architecture artifacts from static dependency graphs and contextual files, releasing generated artifacts for 10,764 repositories. In a round-trip evaluation on 29 small Python libraries, adding recovered requirements and architecture did not significantly improve held-out test pass rate (33.7% to 35.8%) but did make rebuilt module sets more similar to the originals (non-contract module F1 0.54 to 0.63).

The result supplies evidence that architectural artifacts can influence implementation structure while conveying something different from test-observed behavior. It also provides a candidate evaluation pattern: compare whether representations preserve behavior, structure, or both. Similarity to one recovered implementation is not evidence that the architecture is good, that a human understands it, or that the recovered stakeholder intent is historically true.

Review basis (26 October 2026): metadata and selected v2 full-text sections on representation construction, artifact generation, LLM judging, agent reconstruction, results, discussion, and threats. Artifact quality was judged by a model rather than people; the round trip uses one agent and small Python libraries, and architecture has no unique reference. The artifacts and released pipeline were not run.

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

### 1.7 Potentially relevant but more peripheral

Relevant traditions include:

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

## 2. Positioning Hypotheses

These are provisional distinctions to test against the literature, not novelty claims.

### 2.1 Versus conventional software visualization

PostCode is not primarily asking:

> Can a visualization make source easier to understand?

It asks:

> Can multiple trustworthy projections become a viable primary human investigation surface?

It additionally asks whether agent-mediated selection and generation can make task-specific projections cheap enough to alter the historical economics of software visualization.

This describes PostCode's emphasis, not a boundary of software-visualization research. Merino et al. (2026) and moldable development also address continuous, contextual interaction; their overlap must be considered when evaluating any claimed distinction.

### 2.2 Versus conventional LLM code summarization

PostCode overlaps superficially with an already common AI interaction:

> Summarize this code.

The distinction is not that PostCode can produce prose summaries while existing LLMs cannot.

Instead, PostCode asks whether program summarization can become part of a **qualified, navigable projection system**.

A PostCode summary view may:

- coordinate projections produced by mechanically defined lenses;
- include a synthesized summary projection where a new qualified account is useful;
- incorporate recorded assertions and behavioral evidence;
- expose provenance;
- distinguish derived facts from interpretation;
- state limitations and unavailable information;
- link directly into deeper projections;
- preserve the repository state associated with each projection;
- be compared across revisions.

Thus the request **Summarize the project** is not intended merely as a better prompt for an LLM. It is one candidate entry point among others into a structured investigation of the program.

This may also provide a useful bridge between familiar contemporary AI use and PostCode's broader research question:

> **Can the adaptive representation pattern people increasingly use for documents and other information become trustworthy enough to serve as a routine human interface to software?**

### 2.3 Versus AI code review

PostCode is not primarily asking:

> Did the agent's patch contain a defect?

It asks:

> What does the program now look like at the levels relevant to the human supervising it?

These questions overlap in practice. Whiteboard's conceptual explanations and decision records, for example, extend beyond defect detection. Comparisons should identify the actual supported investigation and supervision tasks rather than treating code review as a uniformly narrower activity.

### 2.4 Versus architecture recovery

PostCode does not assume that one recovered architecture is the privileged higher-level representation. Different questions may require different lenses and projections.

### 2.5 Versus agent knowledge representations

PostCode does not initially attempt to improve the representation consumed by coding agents. It investigates the representation presented to humans.

### 2.6 Versus model-driven development

PostCode does not initially make a higher-level model authoritative or generate implementation from it. Conventional source remains canonical during the experiment.

### 2.7 Potential distinctive conjunction

The following combination describes PostCode's intended research emphasis and provides dimensions for comparison with related work:

- sustained software development rather than one-shot comprehension;
- source as a secondary rather than assumed-primary human representation;
- multiple task-dependent lenses and projections;
- automatic selection of lenses and presentations from human information needs;
- epistemological status and provenance visible at the point of every claim;
- explicit accommodation of incomplete and language-dependent analyses;
- tests treated as projected evidence rather than merely pass/fail gates;
- revision/projection comparison for agent-mediated changes;
- empirical pressure across unrelated projects and eventually languages;
- explicit willingness to discover that source remains superior for some classes of work.

Several of these dimensions already overlap with moldable development and the other work above. Whether any particular conjunction, mechanism, or finding is distinctive requires a specific comparison; this list does not establish an unoccupied research territory.

### 2.8 Implications of recent prior art

Recent publications and project descriptions reinforce PostCode's existing empirical focus and require precise attribution of overlapping ideas. Repository representations, provenance categories, task-specific views, evidence graphs, semantic change representations, and test-to-code evidence have precedents. Their broad existence should not be presented as a PostCode invention. The entries above distinguish what was checked from what remains to be established about implementations, guarantees, and usefulness.

The central research question remains the one already stated in [`research.md`](research.md#5-research-questions):

> **Can task-adaptive, epistemically qualified representations provide a viable primary conceptual interface through which humans understand, direct, and supervise software development, without routinely relying on conventional programming-language source?**

As [`research.md`](research.md#31-creation-continued-development-and-existing-software) emphasizes, this includes investigation of unfamiliar programs, continued development of existing software, and development from inception. In the last case, intentions, rationale, and implementation may co-evolve, rather than requiring conceptual structure to be recovered after the fact. Related spec-driven work is therefore relevant, not categorically separate.

This question overlaps with existing research agendas; it is not a residual territory established as novel by this bibliography. Possible contributions remain those described in [`research.md`](research.md#8-research-and-impact-goal) and [`research-strategy.md`](research-strategy.md#1-strategy-stance). They may include particular guarantees, compositions, interaction designs, and evidence about conditions of usefulness, even where the broad mechanisms have precedents. Each contribution needs comparison at the level of the actual claim. Negative, mixed, and conditional findings remain valid outcomes.

Assessing reuse and assessing a comparison interface are separate opportunities. Archbird is a candidate for both; Whiteboard and Glamorous Toolkit are also candidates for interaction comparisons. A bounded assessment could establish which capabilities are implemented, which guarantees hold, what integration would require, and which human tasks permit a meaningful comparison. These are candidates for the [roadmap](ROADMAP.md#37-assessing-related-systems), not implementation commitments or decisions to replace existing PostCode machinery. The [methodology](methodology.md#84-comparisons-and-reuse-assessments) distinguishes the evidence each assessment can supply.
