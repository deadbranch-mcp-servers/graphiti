# Graphiti Roadmap

## Vision
Graphiti will continue to evolve into a reliable, production-grade platform for knowledge graph construction and retrieval. The roadmap below highlights upcoming initiatives that strengthen core graph capabilities, improve developer ergonomics, and broaden model support.

## Near-Term Initiatives (0-3 Months)
- **Entity extraction pipeline optimization**  
  Explore and integrate non-LLM approaches such as spaCy, GoLLIE, mDeBERTaV3, or XLM-RoBERTa (including fine-tuned variants) to reduce processing latency and mitigate hallucinations in entity extraction workloads.  
  _Attribution: [Issue #328](https://github.com/getzep/graphiti/issues/328)_
- **Operational tooling**  
  Enhance observability with additional OpenTelemetry spans, tightening integration with the tracing infrastructure described in `OTEL_TRACING.md`.

## Mid-Term Initiatives (3-6 Months)
- **Graph schema governance**  
  Provide schema versioning tools and migration helpers so teams can evolve their knowledge graphs safely over time.
- **API and SDK improvements**  
  Expand client SDK coverage and add higher-level abstractions that simplify creating, querying, and maintaining graph projects.

## Long-Term Initiatives (6+ Months)
- **Advanced retrieval strategies**  
  Incorporate adaptive query planning and hybrid search models to improve recall and precision for enterprise-scale graph deployments.
- **Ecosystem integrations**  
  Build connectors for additional data platforms and workflow orchestration tools to embed Graphiti in broader data ecosystems.

## Attribution
- Entity extraction enhancement adapted from community feedback in [Issue #328](https://github.com/getzep/graphiti/issues/328).
