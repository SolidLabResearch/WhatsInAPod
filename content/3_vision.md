## The Solid pod as a permissioned Knowledge Graph # {#graphcentric}
In the previous section, we outlined the current interpretation 
of Solid as a document-centric ecosystem, where the Solid pod takes the role 
of a permissioned document hierarchy. We demonstrated that even when querying
the Solid pod as a Knowledge graph, interoperability in the ecosystem is still
constrained by its document-centric interpretation.

This leads us to conclude, 
that where document sharing as a basis provides a limited innovation surface,
the goal of the ecosystem is to achieve the sharing of data,
which should not be limited by any single document hierarchy.

This leads us to propose the definition of the Solid pod as *fundamentally being a permissioned, hybrid knowledge graph, exposed through Web APIs*.
<!-- permissioned -->
With the term *permissioned*, we express the ability to manage permissions over any individual nodes and relation in the knowledge graph.
Note that we use this term to lean close to the current proposition for user control in Solid, 
but that we recognize the term *parameterized* as a potential evolution, where next to only user permissions,
any number of parameters can be retained for the individual nodes and relations in the knowledge graph. 
<!-- hybdid -->
The term *hybrid* expresses the ability of the knowledge graph to store any kind of data as nodes in the knowledge graph 
in the form of blobs, for which metadata can be maintained in the knowledge graph.
<!-- knowledge grap -->
For the term *knowledge graph*, 
we adopt the definition proposed by [](cite:cites hogan2021knowledge):
"*Herein we adopt an inclusive definition, 
where we view a knowledge graph as a graph of data intended to accumulate and convey knowledge of the real world,
whose nodes represent entities of interest and whose edges represent relations between these entities. 
The graph of data (aka data graph) conforms to a graph-based data model, 
which may be a directed edge-labelled graph, a property graph, etc.*"
<!-- Web APIs -->
And finally, the definition states that this knowledge graph can be exposed using any suitable Web API,
so that we do not constrain the possibilities of the ecosystem to the capabilities of any specific API.

### A fundamentally different interpretation
<!-- The interpretation -->
With the proposed definition, we want to provide a zoomed-out perspective on the current state of the Solid ecosystem.
Where in the current ecosystem, the document hierarchy of a Solid pod is constraining factor,
it can instead be perceived as one of the many possible interfaces
that can be constructed over the internal knowledge graph of the Solid pod.
In this new interpretation of the ecosystem, the document hierarchy then no longer defines the 
authoritative source for the ordering of data on the Solid pod,
but can be used to represent any number of hierarchies over the data in the knowledge graph of the Solid pod,
based on the requirements and assumption of applications interacting with the Solid pod.
In this ecosystem, the innovation surface is no longer constrained by a single 
document hierarchy that forms the authoritative source for the data on the Solid pod, 
but by a knowledge graph that can be exposed over any suitable API and over which you can construct any number of document hierarchies.

<!-- The current Solid protocol as a KG -->
Note that this interpretation of the ecosystem 
does not invalidate the current Solid protocol.
It however changes the implication of the exposed LDP interface of the Solid pod
from the authoritative source of data, 
to an interface over the internal knowledge graph of pod.
Where in the current ecosystem 
permissions are defined based on the document hierarchy of the LDP interface,
in the zoomed-out perspective,
the document hierarchy of the LDP interface 
is based on the permissions of the data in the knowledge graph.
By generating the documents over the internal knowledge graph, 
the interface can only include data for which adequate permissions are given.
In this way, the current protocols are reused,
but their position in the ecosystem is updated to better reflect their function 
as interfaces for the data on the Solid pod.

Similarly, the current authorization protocols in their current state can be reused
to set permissions for the subset of data in a document for which this is allowed,
as they cannot be used to manage permissions for single data entries in a document.

<!-- comparison -->




<!-- conclusion -->
The optional SPARQL interface [](cite:cites sambra_solid_nodate) included in the first versions of the Solid protocol,
as well as the current Inrupt pod implementation of an optional QPF-interface [](cite:cites solid_qpf),
shows a clear sign towards a knowledge-graph interpretation of the Solid pod, at least from a query perspective.
Through this zoomed-out perspective of the Solid pod being fundamentally a knowledge graph,
we see that these innovations are attempts to provide the proposed solution space
within the confines of the document hierarchy of the Solid pods.
Where they are viewed as optional additions to the LDP interface in the current ecosystem,
we propose to view these protocols as equal in their function to provide an interface
over the knowledge graph of the Solid pod.



















