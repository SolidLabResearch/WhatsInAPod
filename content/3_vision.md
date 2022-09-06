## The Solid pod as a permissioned Knowledge Graph # {#graphcentric}
In the previous section, we outlined the current interpretation 
of Solid as a document-centric ecosystem, where the Solid pod takes the role 
of a permissioned document hierarchy. We demonstrated that even when querying
the Solid pod as a Knowledge graph, interoperability in the ecosystem is still
constrained by its document-centric interpretation.

Where an ecosystem built on the sharing of documents on the Web
provides a limited surface for innovation,
an ecosystem built on the sharing of data,
not limited to a specific document hierarchy
provides more opportunities for innovation.

This leads us to propose the definition of the Solid pod as *fundamentally being a permissioned, hybrid knowledge graph, exposed through Web APIs*.
This understanding of the Solid pod shifts the premise from data contained in documents to documents built on top of data.

<!-- permissioned -->
With *permissioned*, we express the ability to manage permissions over any individual nodes and relation in the knowledge graph.
Note that we use this term to lean close to the current proposition for user control in Solid, 
but that we recognize the term *parameterized* as a potential evolution, where next to only user permissions,
any number of parameters can be retained for the individual nodes and relations in the knowledge graph. 
<!-- hybdid -->
*hybrid* expresses the ability of the knowledge graph to store any kind of data as nodes in the knowledge graph 
in the form of blobs, for which metadata can be maintained in the knowledge graph.
<!-- knowledge grap -->
For the term *knowledge graph*, 
we adopt the definition proposed in [](cite:cites hogan2021knowledge):
"*Herein we adopt an inclusive definition, 
where we view a knowledge graph as a graph of data intended to accumulate and convey knowledge of the real world,
whose nodes represent entities of interest and whose edges represent relations between these entities. 
The graph of data (aka data graph) conforms to a graph-based data model, 
which may be a directed edge-labelled graph, a property graph, etc.*"
<!-- Web APIs -->
And finally, the definition states that this knowledge graph can be exposed using *any suitable Web API*,
so that the possibilities of the ecosystem are not constrained by the capabilities of any specific API.

### A fundamentally different interpretation
<!-- The interpretation -->
With the proposed definition, we want to provide a zoomed-out perspective on the current state of the Solid ecosystem.
Where in the current ecosystem, the document hierarchy of a Solid pod is constraining factor,
it can instead be perceived as one of the many possibilities
of representing the internal knowledge graph of a Solid pod.
By shifting the interpretation of the document hierarchy from the authoritative source
to a representation on the data in the Solid pod, we can construct any number of hierarchies 
over the Pod knowledge graph.
These can be built on the Solid pod server, or can be created at the client
over the APIs that are exposed by the Solid pod.

<!-- The current Solid protocol as a KG -->
Note that this interpretation of the ecosystem 
does not invalidate the current Solid protocol.
It however changes the implication
of the exposed LDP interface of the Solid pod
from maintaining the Solid pod document hierarchy,
to being a possible representation of the internal data state.
Where the current ecosystem restricts permissions to the document
hierarchy of the LDP interface, the zoomed-out perspective
enables the construction of the document hierarchy based on 
the permissions set in the pod knowledge graph.
By only including data in documents for which permissions are set,
we can reuse the current protocols 
but shift their position in the ecosystem to better 
reflect their function as an interface on the data in the Solid pod.

However, not all translations are seamless.
Where a knowledge graph can be distilled from a document hierarchy,
the inverse operation require additional semantics,
such as the use of named graphs in the data of the pod knowledge graph,
as is currently proposed for the optional query interfaces of the Solid pods.
Similarly, the current authorization protocols in their current state can be reused
only to set permissions for the subset of data in a document for which this is allowed,
as they cannot be used to manage permissions for single data entries in a document.




<!-- conclusion -->
The attempts to improve queries on top 
of the current Solid ecosystem 
through optional SPARQL [](cite:cites sambra_solid_nodate) 
or QPF [](cite:cites solid_qpf) interfaces,
demonstrates the requirement
for a knowledge-graph interpretation
of the Solid pod in at least a query perspective.
We conclude that where the current Solid protocol,
built on the LDP and WAC/ACP specifications,
tries to emulate a permissioned knowledge graph
but falls short of its intended goals.
Where the document hierarchy fails to capture the
essence of the free sharing of structured data on the Web
and ends up being a limiting factor for the ecosystem,
the interpretation of the Solid pod as a knowledge graph
frames the current ecosystem and future innovations
in a system where data is the central focus
and interfaces are a means to an end.



















