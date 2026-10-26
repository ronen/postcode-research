# Cross-paradigm stress tests for architectural representations

Recorded: 2026-10-26  
Status: exploratory research note; not scheduled work or an application-language commitment

## Motivation

PostCode deliberately begins with established software-design and architecture concepts—such as responsibility, boundary, ownership, state, interaction, contract, and concurrency—rather than waiting for a common vocabulary to emerge from code analysis alone. This is useful, but it risks overfitting the human-facing vocabulary and retained architectural accounts to familiar imperative or object-oriented programs.

Trying another conventional imperative language may validate language-adapter portability without seriously testing conceptual portability. A contrasting language paradigm could expose assumptions before they harden into PostCode's representations or data structures.

The key possibility is that **architectural questions generalize more readily than architectural entities**. The human may still ask where responsibilities lie, how information or control propagates, which effects and failures matter, or how a proposed change affects guarantees, while the appropriate entities and presentations differ substantially by paradigm.

## Candidate contrasts

| Language | Potential pressure on architectural concepts |
| --- | --- |
| **Elixir** | Processes, message passing, supervision trees, distributed state, fault recovery and explicit concurrency boundaries. A strong early candidate for a bounded conceptual exercise. |
| **Haskell** | Pure functions, effect boundaries, types, laziness and composition; challenges routine assumptions about mutation, ownership and execution order. A useful complement to Elixir. |
| **Datalog** | Relations, rules, derivations and recursive dependencies; motivates questions such as *which facts and rules contribute to a result?* rather than *who calls this?* |
| **K / q** | Compact array-oriented or tacit computation and implicit transformations; a more extreme stress test that could be confounded by the difficulty of presenting unfamiliar notation. |

These are hypotheses about useful contrasts, not findings about PostCode or assessments of particular implementations.

## A bounded early exercise

Before implementing a new language adapter, select a modest real program in one contrasting paradigm, plausibly Elixir first. Have a capable agent inspect it and construct a **partial, evidence-qualified architectural account** using the concepts under consideration for PostCode. Explore a genuine architectural question or change, using several perspectives where helpful.

Ask which familiar concepts transfer, require qualification, distort the explanation or should be replaced; which paradigm-specific concerns become important; whether retained understanding supports movement between architectural perspectives; and whether the account permits architectural reasoning without exposing programming-language source to the human.

A manually constructed account and presentations may suffice for this *conceptual* investigation. Such an exercise can identify pressures on product design, but **does not demonstrate that PostCode can generate, retain or validate the account**. Maintain the distinction between agent interpretation, derived evidence and observed behavior; independently check consequential claims where appropriate.

Avoid attributing every difference to language: different paradigms are commonly used for different kinds of software. Include a comparable architectural concern where meaningful, as well as a native problem exercising the language's distinctive semantics. Do not force identical programs or architectural categories across languages.

## Timing and implications

**Not part of the immediate first-journey or graphical-interface roadmap.** Continue toward a useful initial PostCode investigation in the currently supported language. Revisit a bounded conceptual stress test once there is a concrete architectural representation or retained-account design whose generality is worth challenging—ideally *before* those concepts become difficult to revise.

Full language integration is a separate, later decision, informed by the questions and limitations revealed by exploration. Supporting multiple languages is not itself evidence of architectural generality.

This note adds detail to the questions already identified under [additional languages](../ROADMAP.md#45-additional-languages), [unfamiliar-language challenge](../ROADMAP.md#46-unfamiliar-language-challenge), and [programming-language integration](../product-design.md#programming-language-integration). It does not revise their priority or establish a universal architecture model.
