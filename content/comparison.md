## Comparative analysis # {#comparison}
In this section,
we compare the impact of the document- and graph-centric pod interpretations
in terms of
[storage](#comparison-storage),
[publication](#comparison-publication),
and [query processing](#comparison-querying).

### Storage # {#comparison-storage}
In a document-centric interpretation,
the underlying storage of a pod is typically managed
as a document-based system,
as evidenced by current Solid server implementations
that leverage the file system or document-oriented databases.
This preferences is explained by
the direct match of the interface to the pod;
in some ways,
the document-centric view on a pod
can be seen as a permissioned file system for the Web.
Of course,
quadstore-based storage can also be applied,
in which case the fourth element of each quad
typically indicates the document to which it belongs
(and, hence, the associated metadata such as permissions).
The benefit of the latter
is that they might enable higher performance for derived APIs,
although there is still the requirement of supporting non-RDF documents,
such as for instance images or movies.

The graph-centric interpretation imposes stronger requirements
on the underlying storage.
On the one hand,
different metadata might have different granularities,
so there is no longer a natural document grouping.
On the other hand,
different selections need to be created from the raw data,
so there specific document organizations provide no universal benefit across APIs.
Consequently,
document-based storage systems are not a good technological fit.
In the long term,
native implementations of hybrid, contextualized will be a necessity.
In the medium term,
they can be emulated on top of quadstores
and [RDF-star stores](cite:citesAsAuthority RDFstar).
Whereas quadstores can easily associate metadata with RDF 1.0 triples,
RDF-star stores could extend this functionality to RDF 1.1
when Solid pods start using graphs to model data.

### Publication # {#comparison-publication}
<div class="todo" markdown="1">
document-centric:

- straightforward from document store

graph-centric:
- needs high-performance view definitions and applications
</div>

### Querying # {#comparison-querying}
<div class="todo" markdown="1">
document-centric:

- link-traversal-based query processing
- possibly aided by indexes

graph-centric:
- LDF with Comunica, choose most appropriate interfaces
- automatically generate relevant interfaces
- just a SPARQL endpoint will not be sufficient because of federated queries
</div>
