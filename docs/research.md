# PostCode: Research Direction

The current PostCode design and its terminology are described in [`design.md`](design.md).

## 1. Motivation

The long-term question motivating PostCode is:

> **What does programming become when humans increasingly delegate implementation to agents?**

A particularly interesting version is:

> **If humans are no longer routinely reading or writing TypeScript, Python, Rust, etc., why should conventional human-readable programming languages remain the primary persistent representation of a program?**

This is a motivating research curiosity, not a premise of PostCode.

It is entirely possible that conventional programming-language source remains an excellent canonical representation even when humans rarely inspect it. It is also possible that source contains information that cannot usefully be replaced by higher-level views, or that agents themselves continue to work best with conventional languages.

PostCode should be capable of producing evidence against the motivating intuition.

The immediate question is deliberately narrower:

> **Can trustworthy projection-based views become a viable way for humans to understand, direct, and supervise software development instead of routinely working through conventional programming-language source?**

This includes both understanding software that already exists and supervising the creation or continued development of software implemented by coding agents.

Natural follow-up questions include:

> **When are projection-based views preferable to source, and when is source preferable to projection-based views?**

and:

> **Can humans effectively direct software development while interacting primarily at the level of higher-level concepts rather than conventional programming-language source?**

PostCode need not demonstrate that projection-based views are preferable to source in general. Discovering which activities and questions are well served by them—and which continue to send the developer back to source—is itself useful.

### 1.1 Learning to supervise

A related motivation concerns not the representation used by experienced programmers, but how future programmers acquire the knowledge needed to direct and supervise software development.

Programming has historically been both a means of producing software and a means of learning how software works. Much of the judgment required to design and supervise software is acquired through the experience of implementing, debugging, modifying and maintaining it.

If implementation is increasingly delegated to agents, an important question follows:

> **How do humans acquire the skills and judgment needed to supervise software that they no longer learn primarily by implementing themselves?**

One possibility is that substantial implementation experience remains necessary: the concepts and judgment required for effective supervision may be inseparable from learning conventional programming and practicing it.

Another possibility is that some of what programmers currently learn through implementation can instead be learned and exercised more directly at the level of the important computational and software-design concepts.

This raises two related questions:

> **Can humans learn to reason effectively about software while interacting with agents primarily at the level of higher-level concepts rather than conventional programming-language source?**

and, more fundamentally:

> **What are those concepts?**

PostCode does not initially investigate programming education or skill acquisition. However, its investigation of which concepts and representations prove useful for understanding, directing and supervising real software may provide evidence relevant to those questions.

If a stable vocabulary of concepts emerges through use, those concepts may eventually be candidates not only for how experienced programmers interact with agent-written software, but also for how people learn to reason about and direct software development in an agent-mediated world.

Conventional programming-language source has historically served simultaneously as an **implementation medium**, an **inspection medium**, and a **learning medium**. Agent-mediated programming may allow—or force—those roles to separate.

PostCode primarily investigates the human-facing interaction and inspection role, while remaining motivated in part by the larger question of what happens to the other roles.

## 2. Adaptive Representation as a Familiar AI Interaction

PostCode's proposed interaction has an analogue in an increasingly ordinary use of AI outside programming:

> **Inspect this larger artifact and give me the representation of it that is useful for my current purpose.**

For example:

> Read this paper and summarize it for me.

> Compare these two documents.

> What changed between these reports?

> What matters in this email thread?

The human does not necessarily want to navigate the complete underlying artifact. Nor do they necessarily specify in advance exactly how the result should be represented. They express an information need and delegate some combination of inspection, selection, compression and presentation.

PostCode asks whether this increasingly familiar interaction can usefully extend to software:

> **Don't require me to reconstruct the program from conventional programming-language source. Inspect it and give me the projection appropriate to what I need to know.**

This makes PostCode less radical as an interaction model than it might initially appear. What is unusual is the degree of trust required.

Ordinary summarization can often tolerate approximation, omission and interpretive compression. Software investigation frequently cannot.

For example:

> These are the three callers.

is materially different from:

> These are the three direct callers established by static analysis; additional calls through escaped closures cannot be exhaustively determined.

Thus PostCode can be thought of, in part, as applying AI-mediated adaptive representation to programs while imposing a stronger epistemological discipline on the resulting claims.

This also provides another possible explanation for why the timing may matter.

Developers are increasingly becoming accustomed to delegating **representation selection and compression** to AI in other domains. At the same time, coding agents are reducing the amount of conventional source developers necessarily inspect as a side effect of implementation.

PostCode asks whether these two changes make a source-secondary software-development workflow newly practical.

## 3. What PostCode Investigates

There are at least three distinct representation questions:

1. **Human representation:** Through what representations should humans understand, direct and supervise software development?
2. **Agent representation:** What representation is most useful for coding agents to consume and manipulate?
3. **Persistent program representation:** What should be the canonical durable representation from which the program is built?

PostCode directly investigates the first.

Even a maximally successful PostCode—one in which developers can conduct sustained software work without routinely inspecting conventional programming-language source—would not establish that source should disappear.

Agents might still work best with conventional source. Conventional source might still be the best canonical representation. Alternatively, some future system might use a different human-readable or machine-oriented representation as its persistent source.

Those are separate research questions.

PostCode may weaken one historical reason for the privileged status of conventional programming-language source: that humans need to work directly with it in order to understand and supervise programs.

A related but separate question is whether working directly with conventional source is also necessary for humans to **learn** the concepts and acquire the judgment required for effective software development. PostCode does not initially investigate that educational question, although the concepts that prove useful for supervision may eventually provide evidence relevant to it.

This separation is methodological rather than a claim about the eventual programming system.

PostCode investigates the **human conceptual interface to software development**.

It does not initially investigate whether coding agents themselves would benefit from a richer semantic representation, nor whether such a representation should eventually become the persistent program.

### 3.1 Creation, continued development, and existing software

There is another distinction within the human-facing question.

PostCode can participate in software development at different points in a program's lifecycle:

- a program may be developed through PostCode-mediated supervision from its inception;
- PostCode may be introduced during the continued development of an existing codebase;
- PostCode may be used to investigate and supervise changes to an unfamiliar codebase whose development it has never participated in.

These cases may behave differently.

When PostCode participates from the beginning, concepts, intentions, rationale and other information may be available as part of the development process rather than reconstructed later from implementation artifacts.

When introduced into an existing project, some such information may already exist in source, tests, documentation, version history or previous development context, while other information may need to be recovered or may simply have been lost.

When applied to an unfamiliar codebase, PostCode must derive useful projections from whatever evidence the repository and its history provide.

The project should investigate all three situations rather than assuming that results from one generalize to the others.

It is plausible, for example, that PostCode proves awkward or limited when reconstructing conceptual structure from arbitrary existing software, while projects developed through PostCode from their inception work well because their conceptual structure and development history co-evolve with the interface.

The reverse is also plausible. Existing implementations may provide exactly the concrete ground truth from which useful projections can be derived, while directing the creation of software primarily through projections and higher-level concepts may prove awkward, ambiguous, or less useful than current prose + source-code interaction with coding agents.

Or the different cases may reveal different strengths.

This makes the point at which PostCode enters a program's lifecycle a research dimension in its own right.

### 3.2 Does PostCode change the software?

PostCode-mediated development may also affect the software being produced.

This raises a further question:

> **Does software created or evolved under PostCode-mediated human supervision differ in significant ways from software produced through current prose + source-code interaction with coding agents?**

Differences might appear in the implementation itself, in the information preserved alongside it, or in both.

For example, sustained interaction at a conceptual level might create pressure for implementations whose structure corresponds more clearly to the concepts through which humans reason about the software.

Such software might exhibit greater **conceptual clarity**: architectural boundaries, responsibilities, effects, invariants, behavior, tests or other implementation properties might correspond more clearly to the conceptual structure through which the human supervises development.

That could be an independently useful property of the software.

But another possibility is merely **tool-relative projectability**: software developed with PostCode becomes unusually easy for PostCode's particular analyses and projections to interpret without becoming clearer or better according to any independently useful criterion.

This distinction matters.

PostCode and PostCode-native software could co-adapt in ways that make the environment appear highly successful while reducing its ability to generalize to arbitrary software. Conversely, pressure toward projectability might turn out to encourage properties—such as clearer conceptual structure—that remain valuable even outside PostCode.

Whether either effect occurs is an open question.

## 4. Why This Question May Be Different Now

Software visualization, architecture recovery, program-comprehension tools and higher-level program representations long predate coding agents.

PostCode does not assume that agent-mediated development invalidates what has already been learned from those fields.

Relevant literature and provisional distinctions from neighboring work are recorded in [`related-work.md`](related-work.md).

Instead, it investigates whether the economics have changed.

In conventional development, developers continuously read and manipulate source. In doing so, they acquire and refresh a detailed source-grounded mental model of the program as a side effect of implementation work. A separate visualization or higher-level representation must therefore provide enough additional value to justify supplementing an already-familiar representation.

Agent-mediated development may weaken that incidental acquisition of source-level knowledge.

At the same time, generative systems may substantially reduce the cost of obtaining a task-specific representation. A useful projection need not be a separately designed artifact or require the developer to find, configure and learn a specialized visualization tool. It may instead be generated for one particular information need, narrowly scoped to the relevant entities or relationships, and discarded or regenerated when no longer useful.

Generative systems may also reduce the cost of **selecting the representation itself**. Rather than deciding in advance that a dependency graph, call tree, table, timeline or behavioral summary is required, the developer may be able to ask:

> What depends on this?

> What changed here?

> Why does this exist?

and delegate some combination of choosing the relevant information and choosing how to present it.

This suggests three possible changes:

1. **The cost of obtaining a task-specific projection may fall dramatically.**
2. **The cost of choosing the appropriate projection and presentation may also fall dramatically.**
3. **The human may no longer acquire a detailed source-level model automatically through the act of implementation.**

Put differently:

> **In conventional development, alternative representations compete with source. In agent-mediated development, they may instead compete with having to reconstruct the program from source at all.**

This is a hypothesis, not an assumption.

PostCode may simply reproduce the historical pattern: source may remain sufficiently useful and information-dense that even cheap, automatically selected, targeted projections add relatively little.

## 5. Research Questions

The central initial question is:

> **Can trustworthy projection-based views become a viable primary conceptual interface for humans understanding, directing and supervising agent-mediated software development?**

That question leads to several subsidiary questions:

- Which kinds of software questions and development activities are well served by projections?
- Which continue to require or strongly favor source?
- Which projections repeatedly prove useful during real development?
- Can a system usefully select projections and their presentation from a human's information need?
- How much epistemological qualification is necessary for projected information to be trustworthy?
- Can derived facts, recorded assertions, behavioral evidence and interpretation be combined without obscuring their different epistemological status?
- Do projection comparisons provide a useful way to supervise agent-generated changes?
- Which program concepts survive across languages, and which remain inherently language-specific?
- Can useful continuity of human attention be maintained without solving persistent semantic identity?
- When should views preserve implementation names, translate them into descriptive language, or use language-independent terminology, and how do those choices affect understanding, continuity, and trust?
- Which aspects of tests can usefully be projected above their source-language realization?
- Does agent-mediated development materially change the usefulness of software visualization and other alternative program representations?
- How does PostCode's usefulness depend on when it enters a program's development lifecycle?
- Does PostCode work differently when it participates in a program's development from its inception than when it is introduced later?
- Does PostCode-mediated supervision change the resulting implementation or the information preserved around it?
- Do programs developed with PostCode become more readily projectable, and if so, does that reflect independently useful conceptual clarity or merely adaptation to PostCode?
- If humans encounter a program primarily through an evolving collection of task-specific projections, can they nevertheless develop and maintain a sufficiently coherent sense of what the program “really is”?
- Is a durable overall mental model necessary for effective direction and supervision, or can task-specific understanding largely replace it?
- Are there projections or concepts that should provide a relatively stable core around which more ephemeral projections are organized?
- If such a core is useful, what belongs in it, and should it be designed explicitly or emerge from repeated use?
- What conceptual knowledge does a human need in order to supervise agent-mediated software development effectively?
- Do the concepts that prove useful for inspecting and supervising software suggest a useful level at which people could learn to reason about software?

These are research directions, not requirements that PostCode answer every question.

In particular, questions concerning education and skill acquisition are motivating questions rather than an initial empirical remit for PostCode.

The project should allow actual use to determine which questions turn out to matter and to generate new questions as the work proceeds.

<a id="possible-findings"></a>
## 6. What Might We Learn?

PostCode does not have a predefined experimental endpoint at which the project as a whole succeeds or fails.

It is intended as an ongoing development and research programme in which building and use produce a stream of findings—positive, negative, mixed and unexpected—that influence what is investigated and built next.

Some possible findings include the following.

### Projections become a routine working surface

Developers supervising agents substantially reduce routine source inspection because task-specific projections often provide the information they need.

### Source remains a primary representation

Higher-level projections help in particular circumstances, but source remains extraordinarily useful and information-dense for broad classes of software investigation and development.

This would be an important finding rather than a failure of the research.

### Greenfield and existing-code use differ

PostCode proves substantially more useful when it participates in development from a project's inception than when reconstructing conceptual structure from arbitrary existing code—or the reverse.

The circumstances under which PostCode enters the development lifecycle may turn out to matter as much as the particular projections it provides.

### PostCode changes the resulting software

Software developed under PostCode-mediated supervision develops measurably or observably different characteristics from software developed through conventional prose + source-code interaction with coding agents.

Those differences might be beneficial, harmful, neutral, or merely adaptations to PostCode itself.

### Projection diffs become particularly useful

Comparing projections across revisions proves useful for supervising agent-generated changes even if projections do not replace source for ordinary comprehension.

### Trust becomes particularly important

The most valuable contribution turns out to be explicit epistemological guarantees about what program views do and do not establish, rather than any particular representation.

### A cross-language vocabulary emerges

Experience across multiple language adapters reveals a stable set of useful language-independent program concepts, alongside language-specific extensions.

### Provenance becomes particularly important

A useful alternative to source turns out to be an environment that allows derived facts, recorded rationale, behavioral evidence and interpretation to be investigated together without collapsing their distinctions.

### Tests become a bridge

Behavioral test intent can often be separated usefully from source-language realization, while cases that resist abstraction expose important boundaries between language-independent behavior and implementation-specific properties.

### Representation selection becomes particularly important

The important capability turns out not to be any particular visualization or projection, but automatically selecting useful information and presentation for the developer's current question.

These are examples of discoveries the research could plausibly make, not outcomes PostCode is required to produce.

Different parts of the work may support different or even apparently conflicting findings. A projection may be useful for one class of investigation and actively unhelpful for another. A technique that works well in one language or codebase may fail to generalize. A workflow that works for PostCode-native software may work poorly for unfamiliar software, or vice versa.

Such boundaries are themselves part of what the project is intended to discover.

## 7. Negative and Limiting Findings

Negative evidence is not necessarily evidence that PostCode as a whole has failed.

A finding may instead establish the limits of a particular projection, technique, interaction model, abstraction or research hypothesis. Such findings should be treated as first-class results and allowed to redirect subsequent work.

Potential negative or limiting findings include:

- for broad classes of questions or development activities, projections prove less useful than source—for example by requiring more effort, taking longer, producing poorer understanding, or simply causing developers to prefer opening source;
- useful analyses cannot provide adequate guarantees;
- qualification necessary for trust makes projections cumbersome or difficult to interpret;
- automatic projection or presentation selection frequently chooses badly;
- developers must understand the available projection vocabulary well enough that automatic selection adds little;
- recorded rationale is too stale or unreliable to contribute usefully;
- test intent cannot be projected usefully without source-level detail;
- cross-language abstractions prove shallow or misleading;
- important implementation facts routinely escape projection;
- projection comparisons often fail to provide information developers find useful beyond conventional source diffs;
- PostCode works well only on projects whose development it has influenced;
- pressure toward projectability produces implementations optimized for PostCode's analyses without improving—and perhaps while degrading—other desirable software properties;
- conceptual-level interaction proves useful for understanding software but too awkward or underspecified for directing its creation;
- conceptual-level interaction works well for creating software but cannot reliably recover enough information from arbitrary existing code;
- prose + source + existing coding agents already provide most of the useful workflow, leaving little role for a dedicated projection environment.

Other negative findings will almost certainly arise from things that have not yet been anticipated.

Mixed results may be especially interesting.

The goal is not to prove that conventional programming-language source should cease to be the human interface to software.

It is to keep asking:

> **What happens when conventional programming-language source stops being assumed to be the primary human representation?**

## 8. Research and Impact Goal

If the work proves worthwhile, it should make a meaningful contribution to understanding how programming evolves in an agent-mediated world.

Possible contributions may concern:

- projections as substitutes or complements for source inspection;
- conceptual interfaces for directing agent-mediated software development;
- epistemological contracts for program views;
- automatic projection and representation selection;
- combining derived facts, recorded assertions, observations and interpretation;
- tests as projected behavioral evidence;
- projection diffs for supervising agent changes;
- persistence of human attention without semantic identity;
- language-independent versus language-specific abstractions;
- conceptual clarity and projectability as properties of software;
- differences between PostCode-native, continued-development and unfamiliar-codebase use;
- circumstances in which source remains necessary.

The strategy for recognizing, communicating, and strengthening these contributions is described in [`research-strategy.md`](research-strategy.md).

The long-term question remains open:

> **What should the persistent program ultimately be?**

PostCode does not answer that question.

It investigates one part of the larger problem:

> **What happens when conventional programming-language source stops being assumed to be the primary human representation through which people understand, direct and supervise software development?**
