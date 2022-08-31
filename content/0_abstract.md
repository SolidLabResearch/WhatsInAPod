## Abstract 
<!-- Context      -->
The Solid vision aims to make data independent of applications
through specifications for publishing and consuming permissioned data,
which is stored decentrally across large numbers of locations called <q>Pods</q>.
<!-- Need         -->
The current interpretation of a Pod as
a collection of Linked Data documents
falls short in realizing this vision of independence,
leading to fundamental interoperability and query problems.
Furthermore,
the broader vision for Solid
is confounded with the concrete HTTP interface to Pods today,
leading to a narrower solution space for these problems.
<!-- Task         -->
We examined the mismatch between the vision
and its currently prevalent interpretation,
and constructed a wider interpretation of a Pod as a knowledge graph
that provides improved opportunities for
storage, publication, and query.
<!-- Object       -->
In this article,
we contrast the existing and proposed interpretations
in terms of how they realize the Solid vision.
We argue that a Solid Pod is fundamentally a knowledge graph,
which can be accessed through various Web APIs
that act as views in a database sense.
<!-- Findings     -->
We show that our zoomed-out interpretation
provides improved opportunities for
storage, publication and query of decentralized data
in more flexible and sustainable ways.
<!-- Conclusion   -->
These insights are crucial to reduce
the dependency of Solid apps on implicit API semantics
and local assumptions about the shape and organization of data
and the resulting performance.
<!-- Perspectives -->
The suggested broader interpretation supports Solid with
is evolution into a heterogeneous yet interoperable ecosystem
that accommodates a multitude of read/write data access patterns.
