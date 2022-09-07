## The Solid pod as a permissioned document hierarchy # {#documentcentric}
<!-- The first interpretation we look at is document-centric. -->
The current focus of the Solid the Solid ecosystem
is based on the interpretation of the vision in
an ecosystem that is centered on the exchange of documents,
as is the case for the current Web.

<!-- The Role of the Solid pod -->
In this system, the role of the Solid pod
becomes that of a document management system.
The Solid pod becomes fundamentally 
a permissioned document hierarchy,
where user data is stored as documents
that can be managed and shared by the user.
In this way, it is similar to a remote file system
that the user and application can use to store documents.
This concept is made explicit in the Solid protocol [](cite:cites Solid_protocol)
though the inclusion of *slash semantics*, 
where the slash (/) characters in the URIs
of documents and containers represent their
position in the document hierarchy.

<!-- The separation of app and data -->
To enable the separation of application
and data, users and applications must be able
to store and interact with their data on their pod.
For this, an adaptation of the Linked Data Platform (LDP) 
specification [](cite:cites presbrey_linked_2014) was introduced.
This LDP interface provides a direct
view on the authoritative structure
of data as documents on the pod.
It defines the hierarchical document structure
as relations of resources (documents) and containers,
similar to files and directories on a file system.
The user can then use the set of HTTP(s) operations 
provided by the specification to interact with the documents.
`
<!-- user control -->
In this system, authorization for the Solid pod
is similarly based on the document structure of the pod.
There are two available specifications: 
the Web Access Controls specification (WAC) [](cite:cites WAC) 
and the Access Control Policy (ACP) [](cite:cites ACP) specification.
Both enable user control in the permissions they can control
for both the documents and the containers (directories) in the pod document hierarchy.
In broad terms, these allow the user 
(or application if given permission) to control
which actors can read, write edit and control
these documents and containers in the Solid pod.

<!-- the encoding of semantics -->
The final concept we are look at here is the 
ability for applications to encode 
semantic information in their data.
itself  to encode semantics into the
data on a Solid pod is made possible by the 
distinction between RDF-documents and non-RDF documents.
Documents stored in an RDF format are handled by the 
pod as data documents. They support the updating of
data in the document via HTTP(S) PATCH and mark 
their presence for applications as data documents.
Data can be stored in other formats, but these 
formats such as JSON usually do not include enough
context for other applications to work with this data.

### The problem of assumptions in applications
<!-- problem statement -->
The current Solid ecosystem 
is still very limited in scale,
and only span a handful of working solutions 
and prototypes [TODO::cite??]().
However, even on this limited scale,
we can perceive how the current interpretation
of the vision for the Web as a document-centric ecosystem
leads to mismatched expectations [TODO::wording]().

<!-- #### the separation of application and data -->
<!-- mismatch in storage -->
The current implementation of the Solid pod
provides a way for users to control the storage
of their personal data on the Web.
However, as it bases itself on a document hierarchy
for data storage, we end up in a situation that
invites local assumptions of applications.
Applications in the current ecosystem often require
additional information for integrating data data.
They include in their application logic that the
`/contacts/` folder contains documents with contact information,
or how the `/contacts/` URI returns contacts of the current user.
This information is not available in the data itself, 
but is encoded in the context of its retrieval over 
specific interfaces or from specific documents.
In the same way, the degrees of freedom left open
by the LDP interface allows applications to encode 
their data in any way they please over the interface. 

Assumptions can be encoded in how data is transformed into separate
documents or how these documents are structured in the pod hierarchy. 
Through this document system and its ability to encode assumptions,
the ecosystem is easy to adopt for applications,
but results in a tight coupling between applications and their
published data on the pod. Integrating data from many 
pods in such an environment may again require the
integration of all these assumptions, bringing us back 
to the current situation.
Solutions are being developed to work around the limitations
of the current document-centric implementation, 
such as the TypeIndex specification [TODO::cite]().
However, these are often still too focused on solving
problems created by the design choices of the implementation,
rather than being a natural consequence of the envisioned ecosystem.


<!-- #### user control -->
<!-- mismatch of user control -->
In terms of user control in the ecosystem,
the current authorization systems are restricted to 
the documents and containers of the Solid pod document hierarchy.
This limits user control of their data to the
documents over which this data is spread.
Additionally, the granularity is now indirectly
controlled by how applications decide to store
user data on their Solid pod as documents.
Because of this, applications may try 
to optimize their data structuring for 
maximum control over specific data,
where others might just write everything as one document.
Next to problems with user control,
applications are now invited to encode 
additional assumptions as to how the control
of the data should managed in the document structure.
This exacerbates the problem of local decisions 
leading to further mismatched assumptions between applications.


<!-- #### enriching data through semantics -->
In addition to separating apps and data,
the data must also be independent of the application.
In the case of Solid, applications can store their information
in an RDF formatted document on the pod.
These documents provide additional functionality
for the updating of data through PATCH requests.
However the document structure does 
invite applications to place assumptions
in the data based on the context of the document.
Where an application will see a profile in a 
document in a location that they assume to be
their space on the pod, they may assume
that profile to be from their app, instead
of encoding these semantics in the data itself.

### A shift in interpretation
In this document-centric interpretation,
we see the requirement of a more data-focused
vision appearing through multiple initiatives.
Native to the Solid LDP specification,
documents containing only RDF data are
provided with additional functionality to update
the contained data without changing the resources.
Other optimizations try to work around the
limitations of the LDP interface by providing
other query interfaces over the Solid pod.
An optional SPARQL interface for the Solid pod
was originally included in the Solid specification [](cite:cites sambra_solid_nodate)/
Similarly, the Enterprise Solid Server [TODO::cite]()
provides an optional Quad Pattern Fragements 
endpoint interface to their Solid pods.
These additional interfaces clearly show 
an interest in moving the ecosystem to be less 
document focused, and put the querying of data 
more central in the process.


### A distilled knowledge graph interpretation
<!-- The document-centric vision as a KG -->
To improve upon these problems, 
we see attempts at reconciling the document hierarchy
of the Solid pod with the interpretation as a knowledge graph.
Already in the early iterations of the Solid protocol,
the shortcomings of the LDP interface in terms of 
querying were already mentioned [](cite:cites sambra_solid_nodate).
To combat this, extensions to the LDP specification were proposed,
and an optional SPARQL interface could be provided
by the Solid pod to enable more complex data retrieval.
More recently, the Enterprise Solid Server implementation by Inrupt 
also started providing an optional QPF-endpoint interface
over the documents in their Solid pods. [](cite:cites solid_qpf). 
In this perspective of the Solid pod document hierarchy
as a knowledge graph, the document organization is no longer
a limiting factor for interoperability.
Applications can query directly on the (RDF) data that is present
in these documents, even though this data may be spread across 
hundreds of documents with different organizations of data in the pod.
This perspective of a Solid pod as a knowledge graph is also 
not limited to the server, as this distillation process
from document hierarchy to knowledge graph
can happen fully on the client side over the LDP interface.

<!-- Still has problems -->
However, even with this perspective on the Solid pod, 
where the document organization of the Solid pod is ignored,
we still run into its limitations:
(i) The problem of the organization of data
is removed, but other applications coding assumptions against the 
document hierarchy are still limited in interoperability, 
and do not share the incentive to write rich semantic data to the pod.
(ii) Writing data is still constrained to the document hierarchy,
as all data must be stored in the context of a document on the pod.
This maintains the problems of writing to common
documents and containers.
(iii) The distillation process from document hierarchy to knowledge graph
is open to client interpretation, and may be limited by client understanding
or include interface-specific information such as document last modified information.
(iv) The management of permissions is still
tied to the document hierarchy of the Solid pod, and cannot be
defined in terms of the individual statements in the data.

Where the current innovation surface for the Solid ecosystem is far from reached,
we already feel the constraints imposed by the document hierarchy limiting the options.
Even in its current small scale, 
the ecosystem is limited in interoperability 
and user control of their data.
New innovations in the ecosystem
such as the application interoperability specification [](cite:cites interop)
and research in the possibility for GDPR compliance [](cite:cites Debackere_Colpaert_Taelman_Verborgh_2022)
are limited by the imposed document structure,
and have to work around these limitations.

Because of this, we feel that a shift in perspective is necessary 
for the Solid ecosystem to evolve in a way that promotes longevity 
in their solutions, and a way that maximizes the innovations 
we can build on the ecosystem.
