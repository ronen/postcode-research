# PostCode: Program Projection Environment
## Research Direction and Initial Development Plan

**PostCode** is the current working project name.

---

## 21. Research Practice: Speculative Papers

An occasional useful research exercise is to write the paper **before the research is complete**, explicitly as speculative fiction.

Rather than writing only the hoped-for paper, imagine incompatible outcomes. See [`research.md` — “What Might We Learn?”](research.md#possible-findings) for examples of possible findings the project might produce.

For each speculative result, ask:

> **What observations would make this paper impossible to write?**

---

## 23. Publication-Aware Prioritization

Publication opportunities are legitimate factors in research planning.

The distinction is:

> **Publication-aware prioritization is useful; publication-driven distortion is dangerous.**

At suitable checkpoints ask:

- What coherent contribution do we have now?
- What additional work would make it a credible submission?
- Is an appropriate venue/deadline approaching?
- Is that additional work independently useful, or at least inexpensive?
- What useful work would be postponed?

---

## 24. Collaboration Strategy

Collaboration should initially be demand-driven.

Reasons to seek collaborators later might include:

- missing static-analysis/PL expertise;
- software visualization/InfoVis;
- HCI study design;
- runtime/debugger systems;
- empirical software engineering;
- particular language ecosystems;
- independent users becoming necessary;
- a research result crystallizing;
- open-source contributors naturally becoming collaborators.

The guiding principle is:

> **Add collaborators when there is a concrete reason the work will become better with them.**

---

## 25. Impact Checkpoints

Reconsider dissemination and collaboration periodically.

Useful checkpoints include:

- after PostCode-on-PostCode;
- after Enblog;
- after unfamiliar same-language OSS;
- after second-language OSS;
- after an unfamiliar-language challenge;
- after multiple languages;
- before a comparative user study.

At each checkpoint ask separately:

> **Could this be useful enough to affect how people work?**

and:

> **Have we learned something general enough that other researchers should know it?**

Either can be true without the other.

---

# Appendix A — Initial Related-Work Bibliography

This is a **working bibliography**, not a systematic literature review.

Its purpose at this stage is to identify nearby research traditions, potentially overlapping systems, useful methodological precedent, and work that may sharpen PostCode's eventual research questions.

The bibliography should evolve as the project does.

## A.1 Agentic software engineering and changing human roles

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

## A.2 Human oversight of software agents

**Dhanorkar, S., Passi, S., & Vorvoreanu, M. (2026). _Human oversight of agentic systems in practice: Examining the oversight work, challenges, and heuristics of developers using software agents._ FAccT 2026 / arXiv:2606.05391.**

Empirical study of experienced developers identifying forms of oversight including a priori control, co-planning, real-time monitoring and post-hoc review.

Especially relevant because developers report difficulty reviewing agent-generated code and use artifacts such as test results as proxies or guarantees during oversight.

Potentially important empirical motivation for PostCode's attempt to provide better human-facing supervisory representations.

## A.3 Code comprehension and software visualization

**Gao, J., Xue, Y., Xie, X., Cao, J., et al. (2026). _Understanding Codebase like a Professional! Human–AI Collaboration for Code Comprehension._ ICPC 2026.**

Introduces CodeMap, an LLM-supported environment for hierarchical codebase understanding informed by interviews with professional code auditors.

CodeMap provides dynamic information extraction and interactive switching between abstraction levels.

Very close prior art for PostCode's projected codebase views.

Important distinction: its usage scenario still treats source inspection in VS Code as the verification surface; PostCode deliberately asks whether qualified projections themselves can support sustained investigation and supervision.

**Merino, L., Ghafari, M., & Nierstrasz, O. (2018). _Towards Actionable Visualization for Software Developers._ Journal of Software: Evolution and Process, 30, e1923.**

Important software-visualization background.

Merino et al. begin from the observation that many studies have found visualization useful for software developers, while adoption in ordinary development remains limited. They identify the effort involved in finding an appropriate visualization as an important barrier and argue for better support in connecting visualizations with developers' immediate tasks.

This suggests a particularly relevant hypothesis for PostCode.

Historically, software visualization has often involved a nontrivial acquisition cost: finding the right tool, configuring it, choosing the appropriate visualization, generating it, and interpreting a representation that may contain considerably more information than the developer's current question requires.

Agent-mediated generation may alter that cost structure.

A PostCode projection can potentially be:

- requested for one particular question;
- generated on demand;
- narrowly scoped to the relevant entities or relationships;
- discarded once it has served its purpose;
- regenerated automatically as the program changes.

Under this model, a visualization becomes less like a separately designed artifact and more like a **query result over the program**.

Moreover, PostCode may reduce not merely the cost of generating a visualization but the cost of **selecting an appropriate representation in the first place**.

The developer need not necessarily know whether the current question is best answered by a dependency graph, call tree, table, timeline, behavioral summary, or some other representation.

The developer can instead express the information need:

> What depends on this?

> What changed here?

> Why does this exist?

PostCode can potentially choose an appropriate lens, derive the projection, and select a view suited to the resulting information.

This changes the interaction from:

> **Which visualization tool should I use?**

toward:

> **What do I need to know about the program right now?**

There may also be a second and independent change in the economics of visualization.

In conventional development, developers continuously read and manipulate source. In doing so, they acquire and refresh a detailed source-grounded mental model of the program as a side effect of implementation work. A separate visualization must therefore provide enough additional value to justify leaving or supplementing an already-familiar representation.

This does not imply that developers can always maintain adequate mental models from source; large and unfamiliar systems have long made program comprehension difficult. The hypothesis concerns the **marginal value** of additional representations when source is already the developer's everyday working surface.

Agent-mediated development may weaken that incidental acquisition of source-level knowledge. If an agent performs much of the implementation, the human may increasingly need to reconstruct only those aspects of the program relevant to the decision currently being made.

This suggests at least three reasons why earlier conclusions about the limited adoption of software visualization may deserve reconsideration:

1. **The cost of obtaining a task-specific projection may fall dramatically.**
2. **The cost of choosing the appropriate lens and presentation may also fall dramatically.**
3. **The human may no longer acquire a detailed source-level model automatically through the act of implementation.**

Put differently:

> **In conventional development, visualization competes with source. In agent-mediated development, visualization may instead compete with having to reconstruct the program from source at all.**

A working PostCode hypothesis is therefore:

> **Software visualization may become more valuable in agent-mediated development because generative systems reduce the cost of producing and selecting task-specific views while delegation of implementation reduces the developer's incidental acquisition of detailed source-level knowledge.**

PostCode can test whether those changes are sufficient to move projected representations from **occasional comprehension aids** toward a **routine working surface**.

This is a hypothesis, not a distinction that should be assumed in advance.

PostCode may instead reproduce the historical pattern: source may remain sufficiently efficient and information-dense that even cheap, automatically selected, targeted projections provide too little additional value.

That possibility makes the Merino et al. work particularly useful prior art rather than merely historical background.

**Văduva, et al. (2026). _Code2UML: Agentic LLMs with Context Engineering for Scalable Software Visualization._ arXiv:2605.24453.**

Generates multiple UML views from repositories across Java, JavaScript, PHP and Python using deterministic IR processing plus specialized agents.

Especially interesting for PostCode because it demonstrates multi-language projection generation while reporting high relationship precision but deliberately limited entity recall.

This provides a concrete nearby example of useful projections whose incompleteness matters.

**CodeSkyline (VISSOFT 2026). _A Code-Map Visualization with Juxtaposed Views for Program Comprehension and Navigation._**

Provides multiple simultaneous code-map views and abstraction levels, with a four-week adoption study in which some participants continued using the system occasionally.

Relevant precedent for multi-view and sustained-use software visualization, while remaining primarily within the conventional program-comprehension/navigation framing.

## A.4 Architecture and agent-generated software

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

## A.5 LLMs and software architecture — broader background

**Schmid, L., Hey, T., Armbruster, M., et al. (2025). _Software Architecture Meets LLMs: A Systematic Literature Review._ arXiv:2505.16697.**

Reviews LLM applications to software-architecture tasks including design generation, classification and pattern detection.

Useful starting point for mapping the broader architecture/LLM literature and locating older work that may overlap individual PostCode projections.

## A.6 Human–AI debugging and evidence presentation

**Shen, S., Lu, S., Shen, L., & Luo, Y. (2026). _Debugging Defective Visualizations: Empirical Insights Informing a Human–AI Co-Debugging System._ CHI 2026.**

Not directly about source-code projection, but potentially useful methodological prior art concerning how humans and AI divide investigative/debugging work and how evidence is presented during that process.

This should be read before deciding how strongly it belongs in PostCode's eventual related work.

## A.7 Potentially relevant but more peripheral

Work on:

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

In particular, the **epistemological-status discipline** should eventually be compared not only with contemporary LLM systems but with older work on static-analysis guarantees, provenance, uncertainty visualization and evidence-bearing software tools.

That literature may prove more relevant to this aspect of PostCode than current AI-programming work.

---

# Appendix B — Related-Work Positioning Hypotheses

These are provisional distinctions to test against the literature, not novelty claims.

### Versus conventional software visualization

PostCode is not primarily asking:

> Can a visualization make source easier to understand?

It asks:

> Can multiple trustworthy projections become a viable primary human investigation surface?

It additionally asks whether agent-mediated selection and generation can make task-specific projections cheap enough to alter the historical economics of software visualization.

### Versus conventional LLM code summarization

PostCode overlaps superficially with an already common AI interaction:

> Summarize this code.

The distinction is not that PostCode can produce prose summaries while existing LLMs cannot.

Instead, PostCode asks whether program summarization can become part of a **qualified, navigable projection system**.

A PostCode summary may:

- compose mechanically defined lenses;
- incorporate recorded assertions and behavioral evidence;
- expose provenance;
- distinguish derived facts from interpretation;
- state limitations and unavailable information;
- link directly into deeper projections;
- remain associated with a particular repository revision;
- be compared across revisions.

Thus `summarize(root)` is not intended merely as a better prompt for an LLM.

It is a candidate entry point into a structured investigation of the program.

This may also provide a useful bridge between familiar contemporary AI use and PostCode's broader research question:

> **Can the adaptive representation pattern people increasingly use for documents and other information become trustworthy enough to serve as a routine human interface to software?**

### Versus AI code review

PostCode is not primarily asking:

> Did the agent's patch contain a defect?

It asks:

> What does the program now look like at the levels relevant to the human supervising it?

### Versus architecture recovery

PostCode does not assume that one recovered architecture is the privileged higher-level representation.

Different questions may require different lenses and projections.

### Versus agent knowledge representations

PostCode does not initially attempt to improve the representation consumed by coding agents.

It investigates the representation presented to humans.

### Versus model-driven development

PostCode does not initially make a higher-level model authoritative or generate implementation from it.

Conventional source remains canonical during the experiment.

### Potential distinctive conjunction

The current working hypothesis is that the less-occupied research territory lies in the combination of:

- sustained software development rather than one-shot comprehension;
- source as a secondary rather than assumed-primary human representation;
- multiple task-dependent lenses and projections;
- automatic selection of lenses and views from human information needs;
- epistemological status and provenance visible at the point of every claim;
- explicit accommodation of incomplete and language-dependent analyses;
- tests treated as projected evidence rather than merely pass/fail gates;
- revision/projection comparison for agent-mediated changes;
- empirical pressure across unrelated projects and eventually languages;
- explicit willingness to discover that source remains superior for some classes of work.

Whether that conjunction is genuinely novel remains an empirical literature question and should continue to be checked as PostCode develops.
