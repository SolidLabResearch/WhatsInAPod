## The Solid pod as a permissioned document hierarchy # {#documentcentric}
<!-- The first interpretation we look at is document-centric. -->
The envisioned Solid ecosystem in its current state is not well defined, 
and leaves room for different interpretations of the concepts proposed in its vision.
In this section, we present the general understanding of Solid
as a document-centric ecosystem, where the Solid pod is fundamentally understood
as a permissioned document hierarchy.

<!-- data and files stored as documents on the pod -->
In this interpretation,
the separation of application and data in the ecosystem is approached 
from the perspective of the Solid pods as a document storage system.
The Solid pod manages all data as documents in a hierarchical structure 
of documents and containers, similar to how a file system organizes data
as files ad directories.
Structured data can be stored on the Solid pod by 
converting it to a document in an RDF format,
and storing this document on the Solid pod.
Similarly, other non-RDF documents can be stored in the 
Solid pod document hierarchy.
These documents are then exposed over the Web by the Solid pod.
In this way, the ecosystem achieves the separation of application and data
by storing the application data as (non-)RDF documents on the Solid pod.
User control is maintained on the document level through the management of permissions.
This interpretation of the Solid pod as fundamentally a document hierarchy is
further supported in the concept of *slash semantics* in the current version of the Solid protocol [](cite:cites Solid_protocol),
where the hierarchical relationships between documents and their parent container are 
explicitly defined through the slash (/) characters in their URIs.


<!-- read/write interface  -->
The enable users and applications to create and interact with documents stored on the Solid pod,
an adaptation of the Linked Data Platform (LDP) specification [](cite:cites presbrey_linked_2014) was introduced.
This LDP interface provides a direct view on the document organization
of data on the Solid pod. It defines the terminology of the document structure
as a hierarchy of resources (documents) and containers
and defines the set of valid HTTP(s) operations on this hierarchy.
<!--  The authorization interface -->
Authorization for the Solid pod is similarly based on the document structure of the pod.
There are currently two specifications that are used to manage authorization in the Solid ecosystem:
the Web Access Controls specification (WAC) [](cite:cites WAC) 
and the Access Control Policy (ACP) [](cite:cites ACP) specification.
Where both specifications differ in their handling of permissions,
both work on top of the notion of the Solid pod being a document hierarchy,
where the granularity through which data sharing can be managed
is defined by the granularity of data in the documents on the Solid pod.
As these documents can be managed by applications, 
the applications indirectly define the granularity 
of control users have over their data.

### Interoperability in a document-centric ecosystem
<!-- Interoperability problems -->
The current Solid protocol [](cite:cites Solid_protocol) provides these specifications as is, 
developers are left with many degrees of freedom in their interpretation 
of how to build on this ecosystem.
Where concepts of interoperability and user control are central in the Solid vision,
their current implementation makes them very dependent
on how applications decide to integrate them.
Where the LDP interface of a Solid pod 
enables some forms of interoperability,
applications are free to use it
as a remote document management system.
Similarly, the authorization interfaces 
enable users to manage the permissions,
but in a way that is limited to how applications
store their data as documents on the pod.

<!-- This proposes Solid as a document-centric ecosystem. -->
In a practical example, we examine a set of problems 
faced by two applications  that manage contact information 
in an RDF format on the user Solid pod.

<!-- hierarchy mismatch -->
(i) Both applications can make totally different assumptions 
on how they structure their contact data as documents in the pod hierarchy.
This can results in both applications not being aware of 
the others data being available on the pod.
Additionally, even if they scout the pod for additional data, 
the way the applications structure their contact information entries
as documents on the pod may not conform to the assumptions made by 
other applications in the ecosystem.
The document hierarchy does not inherently provide interoperability
of data of applications.
This requires either additional interfaces and agreements
or a different interpretation of the documents by applications.
<!-- writing same location -->

(ii) Issues arise when both applications 
want to write to the same location in the document hierarchy.
Where storing contact information in a `/contacts/` container 
on the pod makes sense, this can create problems 
where different applications may overwrite data of other applications.
Assumptions on the structuring of contact information 
can also become problematic, as application storage locations
can overlap and documents written to containers used by other applications
may break assumptions and crash applications.
<!-- permission management -->

(iii) The permission management system may cause wrong assumptions by applications.
As permissions are directly tied to specific documents in the hierarchy,
they limit the granularity of control that users have.
One application may try to optimize this, 
by storing their data in small resources 
that can be individually permissioned.
The other application may decide to write 
their contact information as just 
one single resource on the pod.
As assumptions here do not match,
when sharing contact information with other applications,
the user now either has granular control, 
or it has to give access to all the information of a contact,
depending on the application that wrote the data.
Similarly, applications sharing the data may assume 
that contact information is stored in a granular way,
and may wrongly share contact information that 
has all the information visible because of 
wrong assumptions on the data structuring.
These assumptions limit user control over their data
and problems in interoperability with other applications.

We see that in the above ecosystem, 
defined by the interpretation of Solid as a document-centric ecosystem,
interoperability still faces a lot of hurdles as
problems arise from assumptions made by applications.
It limits the innovations surface
to the capabilities of the document hierarchy
of its Solid pods.

### A distilled knowledge graph representation
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
