# Candidate Conventions for PostCode-Mediated Development

This document lists candidate language-agnostic conventions that may help humans understand, direct and supervise software through PostCode without routinely working through conventional source.

These are candidates to keep in mind during PostCode development, not conventions PostCode currently endorses. They were initially extracted from conventions used while developing [the author's pre-existing project](methodology.md#existing-project-development) by separating their underlying language-independent intent from their TypeScript-specific realization.

Some candidates may also be adopted as project-specific conventions while developing PostCode; others may remain possibilities that are not currently followed. Local adoption and general recommendation are separate decisions. The conventions initially adopted for application development are recorded in [`application/baseline-conventions.md`](application/baseline-conventions.md).

The methodological safeguards for evaluating proposed conventions are described in [`methodology.md`](methodology.md#4-interpreting-formative-use).

## 1. What Would Make a Convention Relevant?

A convention is of particular interest here when it may make software or its recorded development context more conceptually supervisable under PostCode-mediated development. For example, it might make important boundaries, effects, invariants, behavior, rationale or verification easier to discover and project without requiring the human to reconstruct them from source.

Language independence is not sufficient by itself. Many ordinary engineering practices apply across languages without being especially relevant to source-secondary supervision. Project-specific architectural decisions may also be language-independent without being appropriate recommendations for other projects.

The candidate set concerns language-agnostic properties of software design and recorded development context rather than source-level style or coding technique.

Candidate conventions should therefore be evaluated by asking:

- whether the convention improves PostCode-mediated supervision;
- whether it produces independently useful conceptual clarity or only tool-relative projectability;
- whether it generalizes across projects and languages;
- whether it compensates for a weakness in PostCode that should instead be addressed in the tool;
- what costs or distortions it creates when the software is developed or understood outside PostCode.

## 2. Candidate Convention Set

### 2.1 Conceptual boundaries correspond to implementation boundaries

- Keep core domain behavior independent of user interfaces, command interfaces and other delivery mechanisms.
- Make dependencies between major components follow declared architectural boundaries.
- Expose a component through its intended public boundary rather than requiring consumers to know its internal organization.
- Do not expose internal helpers or coordination types as part of a component's public interface.
- When implementation repeatedly cuts across an intended boundary, reconsider the boundary rather than concealing the mismatch.

These properties may allow projected conceptual structure to correspond to real implementation structure rather than to an interpretation imposed by PostCode.

### 2.2 Effects and external dependencies are identifiable at boundaries

- Separate parsing, validation, formatting and external I/O when those concerns are conceptually distinct.
- Keep transformations that need no external state independent of external I/O.
- Keep external effects in small, identifiable operations at system or component boundaries.
- Keep dependency use within the architectural regions for which it is approved.
- Translate the data and failure models of external dependencies at the boundary when they should not become part of domain behavior.

The purpose is not to prescribe a universal architecture. It is to make effects and external dependencies discoverable as concepts rather than leave them diffusely entangled with computation.

### 2.3 Expected failures, defects and diagnostics remain distinct

- Represent expected failure modes explicitly in an operation's contract.
- Preserve the distinction among expected failures, defects or broken invariants, successful results that contain diagnostics, and failures that prevent the intended result from being produced.
- Translate expected failures from external systems into the program's declared failure model.
- Associate diagnostics with the affected subject and available source information.

The particular result and diagnostic types are language-specific. The semantic distinctions among expected failure, defect, successful observation and attributed diagnostic are not.

### 2.4 Important domain concepts and behavior are represented explicitly

- Represent important domain concepts explicitly rather than repeatedly encoding them as primitive values.
- Centralize parsing, formatting, comparison and transformation rules for a domain concept.
- Compare domain values according to their defined semantics rather than incidental serialized representations.
- Give values with physical or logical units explicit units in their names or types.
- Name fixed domain values according to their meaning rather than leaving unexplained literals in implementation logic.

Explicit domain concepts may provide more stable and meaningful subjects for projections and agent conversations than incidental implementation constructs.

### 2.5 Components and operations have coherent responsibilities

- Give each component one coherent primary responsibility and a name that makes that responsibility apparent.
- Separate an independently meaningful responsibility when it has its own behavior, concepts or need for verification.
- Prefer operations that expose a comprehensible sequence of named conceptual steps.

These conventions concern conceptual decomposition rather than any preference for classes, functions, modules or another language-specific mechanism.

### 2.6 Computation produces structured information

- Separate computation from presentation.
- Return structured information from computation and format it only at presentation boundaries.
- Preserve meaningful distinctions in results rather than collapsing them prematurely into text.

Structured results may allow PostCode to project behavior, evidence and diagnostics without recovering their meaning from presentation-specific output.

### 2.7 Verification corresponds discoverably to behavior and boundaries

- Verify non-trivial behavior.
- Test pure logic without external fixtures where possible.
- Test internal behavior close to the component that owns it.
- Test public behavior through public component boundaries.
- Use end-to-end interface tests primarily to verify integration rather than duplicate detailed domain testing.
- Prefer real objects and representative data over mocks when practical.
- Keep fixtures small, legible and representative.
- Before creating new fixtures or test infrastructure, look for existing assets that express the same concept.
- Make tests that preserve important behavior discoverable from the component or concept they protect.

These properties may help tests serve as projected behavioral evidence rather than merely as pass-or-fail gates.

### 2.8 Implementation anomalies are treated as evidence

- Prefer simple, explicit implementations over clever ones.
- Avoid retaining unused implementation elements unless they serve a necessary structural or explanatory purpose.
- Treat newly unused existing elements as possible evidence that a change broke a connection.
- Surface recurring violations of a declared conceptual structure rather than routinely working around them.

An implementation anomaly may reveal a defect, a poorly expressed implementation or an inaccurate conceptual model. Treating it as evidence allows any of those possibilities to be investigated instead of presupposing which one is at fault.

### 2.9 Changes preserve traceable development context

- Preserve connections among the human request, affected concepts, implementation changes, rationale and verification where practical.
- Record material uncertainty and deviations from the requested change.
- Keep recorded assertions distinguishable from facts derived from the implementation or observed behavior.
- Associate development context with the relevant task and repository state.

This candidate overlaps with PostCode's task protocol and agent-context design. It extends beyond code structure to the recorded development context through which later human and agent work may understand a change.

## 3. Exclusions

This candidate set does not include:

- project-specific architecture and component boundaries;
- project-specific domain types or approved dependencies;
- source-language and toolchain choices such as module syntax, import paths, visibility syntax, test-framework mechanics or compiler settings;
- preferences for a particular implementation construct, such as classes as the primary unit of organization;
- operational task workflow, which PostCode addresses separately through its task protocol.

PostCode may eventually project or check project-specific constraints and target-language profiles. That would not make the content of those constraints or profiles universal PostCode-mediated development conventions.
