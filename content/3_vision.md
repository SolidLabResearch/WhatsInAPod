## Proposed graph-centric interpretation {#graph-centric}

Because of the limitations of the document-centric interpretation of the Solid ecosystem,
we feel that a shift in perspective is necessary 
to evolve in a way that promotes longevity.
Whereas an ecosystem built on document sharing
provides a limited surface for innovation,
an ecosystem built on data sharing
not constrained to a specific (implicit or explicit) API
provides more opportunities for innovation.
Attempts to improve queryablity
through optional [SPARQL](cite:cites sambra_solid_nodate) 
or [quad-based](cite:cites solid_qpf) interfaces,
demonstrate the desire
for a knowledge-graph interpretation
from at least a query perspective.

### Pod as a knowledge graph

This leads us to propose the definition of the Solid pod as fundamentally being a *permissioned, hybrid knowledge graph, exposed through Web APIs*.
This understanding of the Solid pod shifts the premise from data contained in documents to documents built on top of data.

<!-- permissioned -->
- *Permissioned* expresses the ability to manage permissions over any individual nodes or relation in the knowledge graph.
  Rather than being narrowly restricted to basic read/write/control permissions,
  the underlying knowledge graph could express more complex [usage policies](cite:describes kirrane2018policies,Debackere_Colpaert_Taelman_Verborgh_2022).
  Even more widely,
  rather than just permissioned or policy-aware,
  data could in general be *parameterized*
  such that any number of parameters can be retained for nodes and relations in the knowledge graph. 
<!-- hybrid -->
- *Hybrid* emphasizes that the knowledge graph can store any kind of data (images, videos, etc.) as nodes in the knowledge graph 
in the form of blobs, possibly with associated metadata.
<!-- knowledge graph -->
- *Knowledge graph* is to be interpreted following an [inclusive definition](cite:cites hogan2021knowledge) as
"*a graph of data intended to accumulate and convey knowledge of the real world,
whose nodes represent entities of interest and whose edges represent relations between these entities.*"

<!-- Web APIs -->
The definition further allows exposing this knowledge graph using any suitable Web API,
so that the possibilities of the ecosystem are not constrained by the capabilities of any single API.

### Multiple APIs as views
<!-- The interpretation -->
With the proposed definition, we want to provide a zoomed-out perspective on the Solid ecosystem that allows for multi-perspective interpretations.
Whereas in the current ecosystem, one specific document hierarchy is considered to be _the_ pod and hence a constraining factor,
we instead contend that a specific API over the Solid Protocol
can be interpreted as just one of many possibilities
to represent the internal hybrid knowledge graph of a pod.
By shifting the interpretation of a document hierarchy from _the_ authoritative source
to _one_ representation of a pod's data, we can construct any number of hierarchies 
(or other interfaces) over the underlying knowledge graph.
These can be built on the Solid pod server,
by a client, or even an intermediary.

The mismatches described in the previous section
can then be resolved
by providing apps with a corresponding API
such that the modeling, permission, and optimization constraints
of different apps are no longer in conflict.
Modeling concerns of a single app can be alleviated
by exposing the same data through multiple hierarchies,
since "duplicates" simply become different views of the same resource.

<!-- The current Solid protocol as a KG -->
Importantly,
a graph-based interpretation
is fully compatible with the Solid Protocol,
and in fact recognizes that this protocol
gives rise to _multiple_ APIs.
It changes the role of the Solid Protocol
from the mechanism to expose the API that _is_ the pod,
to being one mechanism for exposing APIs
that _represent_ the pod as one relevant view of its underlying graph.
Whereas the current ecosystem restricts permissions
to a singular document hierarchy,
the zoomed-out perspective
enables the construction of the document hierarchy based on 
the policies in the knowledge graph.
By only including data in documents for which permissions are granted,
we can reuse the current protocols 
but shift their position in the ecosystem to better 
reflect their function as an interface to the data in a pod.

However, not all translations are seamless.
While a knowledge graph can be distilled by merging documents in a hierarchy,
the inverse operation requires explicit view definitions and semantics,
detailing for instance the use of named graphs
(as is currently proposed for an [optional query interface](cito:citesAsEvidence solid_qpf)).
Similarly, the current authorization mechanisms
only apply to documents,
so different mechanisms are necessary to express policies
over the underlying knowledge graph.

<!-- Make point that a document FUNDAMENTALLY is built on application assumptions -->

<!-- Synthese: perfect naast elkaar leven -->

<!-- Make harsher point maybe -->

<!-- Mkae point van Comparible on READ - problems of writing and management for data are problematic on document structure -->



















