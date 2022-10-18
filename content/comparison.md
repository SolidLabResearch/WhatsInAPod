## Comparative analysis # {#comparison}
In this section,
we compare the impact of the document- and graph-centric pod interpretations
in terms of
[storage](#comparison-storage),
[publication](#comparison-publication),
and [query processing](#comparison-querying).

### Storage # {#comparison-storage}
In the document-centric interpretation,
the underlying storage of a pod is typically managed
as a document-based system,
as evidenced by current Solid server implementations
that leverage the file system or document-oriented databases.
This preference is explained by
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
such as images or movies.

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
The generation of API resources in the document-centric interpretation
is relatively straightforward.
Assuming the underlying storage system is indeed document-based,
then each public-facing pod URL corresponds to an internal document identifier.
Responding to an HTTP request involves looking up the internal document,
verifying whether the document-based policies allow access,
possibly performing a format translation,
and sending it back to the client.
Offering alternative APIs might involve more computations,
depending on the underlying storage system.

The generation of API resources in the graph-centric interpretation
involves a more complex process.
First,
we need the notion of a _view definition_,
which essentially specifies how public-facing pod URLs
correspond to triples or documents from the underlying hybrid knowledge graph.
Next,
a _view application_ process is necessary
to materialize the view definition
to generate a response to concrete requests for resources.
Furthermore,
a _policy definition_ is required to express
the allowed operations per triple,
and a _policy application_ process
to apply this policy to the specific request.
For the view aspect,
technologies such as [RDF mappings](cite:citesAsEvidence dimou_ldow_2014),
specifically [from Web APIs to triples](cite:citesAsEvidence RML_API),
can be extended to support the reverse direction.
Existing work on [policies](cite:citesAsEvidence kirrane2018policies,SolidPolicies),
as well as the existing
[WAC](cite:citesAsAuthority WAC) and [ACP](cite:citesAsAuthority ACP) specifications,
can be applied on the triple or shape level,
rather than to documents.

### Querying # {#comparison-querying}
In the document-centric interpretation,
the complexity of the required query processing
is a direct function of whether or not the data resides in a single document,
i.e.,
whether the concrete API of the pod
happens to coincide with the access patterns of a specific use case.
Any mismatch requires a multi-document selection,
which might involve [traversal-based query processing](cite:citesAsAuthority LinkedDataQueryStrategies),
possibly [guided by the pod's known indexes or structure](cite:citesAsEvidence bogaerts_rulemlrr_2021).
Furthermore,
in order to arrive at a complete result set,
all relevant data and intermediary links need to be accessible by the client,
which might not be the case if there is a mismatch
between the granularity of the documents and the policies on the data.

Since the graph-centric interpretation
allows for multiple APIs,
client can select those APIs
that [best match the access patterns of their use case](cite:citesAsEvidence verborgh_jws_2016).
[Query engines for heterogeneous interfaces](cite:citesAsEvidence Comunica)
can identify relevant APIs,
and over time,
servers might analyze data usage
to determine new API structures that might improve performance.
This includes hierarchical Solid Protocol interfaces,
where the partitioning in resources is largely driven by the server,
or more expressive interfaces such as QPF and SPARQL,
whose resources are more client-driven.
We note that no particular interface is expected
to become the best or ultimate choice.
Since performance is essentially a function
of the match between server-side API partitioning
and client-side request patterns,
a document-based API might outperform an expressive query-based API
if cached documents happen to align with a client-side request.
Furthermore,
the needed data for any given use case
could be located across a small or large number of different pods,
and more expressive interfaces do not necessarily outperform
less expressive interfaces for [federation](cite:citesAsEvidence verborgh_jws_2016).
Hence,
a combination of different APIs
will likely always be needed for high query performance,
in addition to the other aspects favoring a graph-centric interpretation.
