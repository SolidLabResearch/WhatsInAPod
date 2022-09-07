## Abstract 
<!-- Context      -->
The Solid vision aims to make data independent of applications
through technical specifications,
which detail how to publish and consume permissioned data
across multiple autonomous locations called <q>pods</q>.
<!-- Need         -->
The current document-centric interpretation of Solid,
wherein a pod is solely a hierarchy of Linked Data documents,
cannot fully realize this envisaged independence,
leading to fundamental interoperability and query problems
and the need for associated workarounds.
The broader longterm vision for Solid is confounded
with the concrete HTTP interface to pods today,
leading to a narrower solution space to address these core issues.
<!-- Task         -->
We examined the mismatch between the vision
and the prevalent document-centric interpretation,
and propose a reconciliatory graph-centric interpretation
wherein a pod is fundamentally a knowledge graph.
<!-- Object       -->
In this article,
we contrast the existing and proposed interpretations
in terms of how they support the Solid vision.
We argue that the knowledge-centric interpretation
improves pod access through different Web APIs
that act as views in a database sense.
<!-- Findings     -->
We show that our zoomed-out interpretation
provides improved opportunities for
storage, publication, and querying of decentralized data
in more flexible and sustainable ways.
<!-- Conclusion   -->
These insights are crucial to reduce
the dependency of Solid apps on implicit API semantics
and local assumptions about the shape and organization of data
and the resulting performance.
<!-- Perspectives -->
The suggested broader interpretation can guide Solid
through its evolution into a heterogeneous yet interoperable ecosystem
that accommodates a multitude of read/write data access patterns.
