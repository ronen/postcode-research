# PostCode Research Project

> *Humans should be able to practice the discipline of software design and architecture in collaboration with agents that implement the software, without needing to be programmers themselves.*

The PostCode Research Project investigates how best to support that practice. Capable coding-agent conversations can already support substantial software-design work without reading source code, at least for experienced developers. The research asks what further representations, interactions, and tools—if any—can improve that collaboration, including for people who have not learned to read or write programming-language source.

One leading hypothesis is that shared architectural representations, grounded in partial, qualified, retained understanding, can help people reason about designs, examine implementations, and revisit architectural questions from different perspectives. These may take textual, structured, or visual forms, drawing where useful on established software-architecture concepts and notations without assuming a complete or authoritative account of the software.

The project explores these questions by building the [PostCode application](https://github.com/ronen/postcode), which presents task-appropriate views of program structure, behavior, history, rationale, and other evidence while preserving the provenance, epistemological status, and limitations of their content.

The research proceeds by studying PostCode during real software development. The application is intended to record and export observations, including relevant interaction events and contemporaneous user reports. This evidence stream will support later analysis of how PostCode is used, where it succeeds or fails, and how the design should evolve.

The application is developed in a separate repository so that it can stand alone as a software project. Once minimally functional, it will be used to help understand, design, and evaluate changes during its own continued development.

## Status

See [`STATUS.md`](STATUS.md) for the project's current status.

See [`ROADMAP.md`](ROADMAP.md) for planned work and candidate directions.

## Documents

- [`research.md`](research.md) defines the research motivation, questions, and possible contributions.
- [`product-design.md`](product-design.md) describes the conceptual product design. It is copied verbatim into the application repository as `foundation/product-design.md`, where the adopted version governs application design and development. Revisions are adopted explicitly; see [application repository setup](application/repository-setup.md).
- [`methodology.md`](methodology.md) describes how building and using PostCode can produce research evidence.
- [`research-strategy.md`](research-strategy.md) describes how findings may shape the broader research direction and publication strategy.
- [`related-work.md`](related-work.md) records relevant prior work and comparisons.
- [`application/repository-setup.md`](application/repository-setup.md) describes the minimal requirements for the application repository to participate in the PostCode research project.

The [`notes/`](notes/) directory holds not-yet-adopted ideas, background material, and other non-primary documents:

- [Candidate conventions for PostCode-mediated development](notes/candidate-conventions.md), retained for consideration rather than as endorsed practices.
- [Cross-paradigm stress tests for architectural representations](notes/cross-paradigm-architectural-concepts.md), an exploratory proposal for testing conceptual portability across language paradigms, not scheduled work or an application-language commitment.

## License

This project is licensed under the [Apache License 2.0](LICENSE).
