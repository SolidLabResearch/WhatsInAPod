## Proposed graph-centric interpretation {#graph-centric}

Because of the limitations of the document-centric interpretation of the Solid ecosystem,
we feel that a shift in perspective is necessary 
to evolve in a way that promotes longevity.
Whereas an ecosystem built on document sharing
provides a limited surface for innovation,
an ecosystem built on data sharing
not constrained to a specific API
provides more opportunities for innovation.
Attempts to improve queryablity
through optional [SPARQL](cite:cites sambra_solid_nodate) 
or [quad-based](cite:cites solid_qpf) interfaces,
demonstrate the requirement
for a knowledge-graph interpretation
from at least a query perspective.

### Pod as a knowledge graph

This leads us to propose the definition of the Solid pod as *fundamentally being a permissioned, hybrid knowledge graph, exposed through Web APIs*.
This understanding of the Solid pod shifts the premise from data contained in documents to documents built on top of data.

<!-- permissioned -->
With *permissioned*, we express the ability to manage permissions over any individual nodes and relation in the knowledge graph.
Note that we use this term to lean close to the current proposition for user control in Solid, 
but that we recognize the term *parameterized* as a potential evolution, where next to only user permissions,
any number of parameters can be retained for the individual nodes and relations in the knowledge graph. 

<!-- hybrid -->
*Hybrid* expresses the ability of the knowledge graph to store any kind of data (images, videos, etc.) as nodes in the knowledge graph 
in the form of blobs, possibly with associated metadata.

<!-- knowledge grap -->
For the term *knowledge graph*, 
we adopt an [inclusive definition](cite:cites hogan2021knowledge),
"*where we view a knowledge graph as a graph of data intended to accumulate and convey knowledge of the real world,
whose nodes represent entities of interest and whose edges represent relations between these entities.*"

<!-- Web APIs -->
Finally, the definition allow exposing this knowledge graph using any suitable Web API,
so that the possibilities of the ecosystem are not constrained by the capabilities of any single API.

### One pod, multiple views
<!-- The interpretation -->
With the proposed definition, we want to provide a zoomed-out perspective on the current state of the Solid ecosystem.
Where in the current ecosystem, the document hierarchy of a Solid pod is a constraining factor,
it can instead be perceived as one of the many possibilities
of representing the internal knowledge graph of a pod.
By shifting the interpretation of the document hierarchy from the authoritative source
to a representation on the data in the Solid pod, we can construct any number of hierarchies 
over the pod knowledge graph.
These can be built on the Solid pod server, or can be created at the client
over the APIs the pod exposes.

The mismatches described in the previous section
can easily be resolved by providing each app with a different LDP-based, permissioned API.
That way, the modeling, permission, and optimization constraints
of different apps are not in conflict.
Modeling concerns of a single app can be alleviated
by exposing the same data through multiple hierarchies,
since "duplicates" are simply different views of the same resource.

<!-- The current Solid protocol as a KG -->
The graph-based interpretation
does not obsolete the Solid Protocol.
It changes the role
of the LDP interface from maintaining the Solid pod document hierarchy
to being one possible representation of the internal graph.
Where the current ecosystem restricts permissions to the document
hierarchy of the LDP interface, the zoomed-out perspective
enables the construction of the document hierarchy based on 
the permissions set in the knowledge graph.
By only including data in documents for which permissions are set,
we can reuse the current protocols 
but shift their position in the ecosystem to better 
reflect their function as an interface on the data in a pod.

However, not all translations are seamless.
Where a knowledge graph can be distilled from a document hierarchy,
the inverse operation require additional semantics,
such as the use of named graphs in the data of the pod knowledge graph,
as is currently proposed for the optional query interfaces of the Solid pods.
Similarly, the current authorization protocols in their current state can be reused
only to set permissions for the subset of data in a document for which this is allowed,
as they cannot be used to manage permissions for single data entries in a document.

<!-- Make point that a document FUNDAMENTALLY is built on application assumptions -->

<!-- Synthese: perfect naast elkaar leven -->

<!-- Make harsher point maybe -->

<!-- Mkae point van Comparible on READ - problems of writing and management for data are problematic on document structure -->



















