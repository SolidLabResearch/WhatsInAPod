## The Solid pod as a permissioned document hierarchy # {#documentcentric}
<!-- The first interpretation we look at is document-centric. -->
The envisioned Solid ecosystem in its current state is not well defined, 
and leaves room for different interpretations of the concepts proposed in the vision.
In this section, we present the currently frequently shared understanding of Solid
as a document-centric ecosystem, where the Solid pod is fundamentally understood
as a permissioned document hierarchy.

<!-- data and files stored as documents on the pod -->
In this interpretation of the ecosystem,
the premise of separation of application and data is approached 
from the perspective of the Solid pods as a document storage system.
The Solid pod manages all data as documents in a hierarchical ordering of documents
and containers, similarly to how a file system handles data as files ad directories.
By introducing the concepts of RDF and non-RDF resources (documents),
data in the network can be converted to a document in an RDF format for representing data 
in the network, and non-RDF documents for data that is not in an RDF format.
These documents are then published over the Web in an environment
where the users are in control over how the data is shared 
by managing the permissions of the documents stored on their data pod.
This way, the envisioned Solid ecosystem is presented as a document-centric ecosystem
where interoperability is based on integration of the available documents by applications in the network
and user control is maintained on the document level through the management of permissions.
This interpretation of the ecosystem is supported by the current version of the Solid specification [](cite:cites Solid_protocol)
through the introduction of *slash semantics*,
where the hierarchical relationships between documents and their parent container is defined
through the slash (/) characters in their URIs.

<!-- Solid uses an adaptation of LDP spec to interact with data on pod -->
<!-- The current specifications chosen to build the Solid ecosystem on have a focus on the document-centric interpretation for the ecosystem,
where all data is stored as resources (documents) in a hierarchic system of resources and containers,
similar to how a file system stores data in files and directories.
As a consequence, the specifications currently used to build this ecosystem
and the specifications being developed to solve problems with the ecosystem
are based on the notion of working with data as documents. -->

<!-- read/write interface  -->
The enable users and applications to create and interact with documents stored on the Solid pod,
an adaptation of the Linked Data Platform (LDP) specification [](cite:cites presbrey_linked_2014) was introduced.
This LDP interface represents the authoritative organization of documents on the Solid pod as a
hierarchical organization of resources (documents) and containers.
Apart from the restriction of representing data as documents, 
and organizing these documents in a hierarchical structure,
the interface has no restrictions on the ways 
applications and users can structure their data over the interface
as documents on the pod.

<!--  The authorization interface -->
Similarly, the current authorization mechanisms for the Solid pod are based on the document structure of the pod.
There are currently two specifications that are being used to manage authorization in the Solid ecosystem:
the Web Access Controls specification (WAC) [](cite:cites WAC) and the Access Control Policy (ACP) [](cite:cites ACP) specification.
Where both specifications differ in their handling of permissions,
both work on top of the notion of the Solid pod being a document hierarchy,
where the granularity through which data sharing can be managed
is limited by the granularity of the documents storing this data on the Solid pod.
As these documents can be managed by applications, 
the applications can indirectly control the granularity of permissions on the user data pod.

### Application interoperability in the document-centric ecosystem
<!-- Interoperability problems -->
With the current Solid ecosystem delivering the specifications as is, 
based on an interpretation of the Solid vision as an document-centric ecosystem,
developers are left with many degrees of freedom in their interpretation of the ecosystem,
and how data should be stored in the document structure of the Solid pods.
To develop an ecosystem on these specifications that is centered around the concepts of interoperability 
and user control, applications are forced to integrate the concepts of the Solid vision using the 
available specifications in a way that they assume will conform to these requirements,
where local solutions and optimizations lead to assumptions that are not necessarily shared by the rest of the ecosystem.

<!-- This proposes Solid as a document-centric ecosystem. -->
In a practical example of this concept, we take two applications in this ecosystem
that work with the same type of data, such as contact information, and both write this data to the Solid pod.
<!-- hierarchy mismatch -->
Both applications may make totally different assumptions of how they structure their contact data in documents,
and where they store these documents in the pod document hierarchy.
Because of this, both applications may not know other contact information is available on the pod,
or even if they scout the Solid pod for additional data, the structuring of the other contact information
may be different in structure to a point that it has become unreadable for the other application 
that holds the assumption that contact data should be structured differently.
<!-- writing same location -->
In case both applications want to forcibly write to the same location,
e.g. a container `/contacts/` on the pod, 
they can create problems with overwriting data, 
or may just create extra documents in this container
that follow different rules to data structuring,
creating issues or even crashing other applications that hold specific assumptions 
to the structuring of data on the Solid pod.
<!-- permission management -->
Additionally, the management of permissions is also indirectly connected to the applications writing data to the Solid pod.
As authorization systems are tied to the document hierarchy of the Solid pod,
the sharing of this data is limited to the created document structure by applications.
As one application might split its contact information in different documents, 
creating a more granular system for sharing parts of contact information,
the other application might assume the whole contact to be a single document on the pod.
This creates issues where one application given access to data by another application leads to 
a mismatch in data sharing, as either not enough data is shared, as the assumption that all data for a contact
should be contained in a single resource does not hold,
or inversely it creates the situation where an app that only requests the name and WebID values for your contacts
now must get access to either all or none of the available information on these contacts, 
as contacts are stored as a single document containing all information on that contact.
This mismatch in the granularity of data, combined with the assumptions of applications in the generation of these data documents,
leads to problems in the sharing of data, and limits the control users can exercise on this data.

The above described ecosystem, defined by the interperatation of Solid as a document-centric ecosystem,
invites problems in interoperability between applications,
as data granularity is limited to documents generated by assumptions in application logic,
and the hierarchical organization of these documents on the Solid pod invite assumptions
to the structuring of data on the Solid pod.
It provides an innovation surface that is limited by the capabilities of the document-centric 
interpretation and design for the ecosystem and the interfaces exposed by the Solid pods.

### A distilled knowledge graph representation
<!-- The document-centric vision as a KG -->
To improve upon these problems, 
we clearly see initiatives trying to reconcile the 
document-centric nature of the ecosystem with the perspective
of treating the data stored in these documents as a Knowledge Graph.
Back in the early iterations of the Solid protocol,
the shortcomings of the LDP interface in terms of 
querying were already mentioned. Originally these proposed
the inclusion of extensions to the used LDP specification,
as well as an optional SPARQL interface for the Solid pod 
to resolve these issues [](cite:cites sambra_solid_nodate).
This perspective of the Solid pod document hierarchy as a 
Knowledge Graph solves a lot of issues in terms of interoperability,
as the organization of data in the document hierarchy does not matter
for the knowledge graph distilled from these documents enables
applications to work directly on the data itself without 
requiring any assumptions of the data organization in the document
hierarchy of the Solid pod.
The provision of an endpoint is also not a core requirement, 
as this distillation process can happen fully on the client side.
Recently, the Enterprise Solid Server implementation by Inrupt 
provided another implementation of this concept
by including an optional QPF-endpoint interface 
for the Solid pods hosted over their server implementation. [](cite:cites solid_qpf). 

<!-- Still has problems -->
However, even with this perspective on the Solid pod, 
where the document organization of the data in the Solid pod is ignored,
we still run into limitations caused by the document hierarchy of the Solid pod.
Where the problem of the data organization is mitigated, 
as other applications are free to ignore this perspective,
the incentive to add semantic enrichment to written data is low.
The distillation process is also dependent on client interpretation
as to how to build the knowledge graph on top of the exposed LDP interface,
where applications may want to rely on information only available
over the LDP interface such as resource timestamps
As this perspective only uses the knowledge graph 
in a query context, writing data to the pod still requires
the wrapping of this data in arbitrary document structures,
and may incur problems for other applications when writing to common
containers or documents.
And finally, the management of permissions is still
tied to the document hierarchy of the Solid pod, and cannot be
defined in terms of the individual statements in the data.

The current innovation surface for the Solid ecosystem is far from reached.
Both through innovations steered by the solid community such as application interoperability [](cite:cites interop),
as well as through external research such as 
GDPR compliance of the authorization mechanisms [](cite:cites Debackere_Colpaert_Taelman_Verborgh_2022),
new innovations and industry attention create a rapidly evolving ecosystem.
However, in the current document-centric ecosystem,
these innovations are constrained by the document hierarchy of the Solid pods they operate on,
and may fall short of their inherent potential.
Because of this, we feel that a shift in perspective is necessary 
for the Solid ecosystem to evolve in a way that promotes longevity 
in their solutions, and a way that maximizes the innovations 
we can build on the ecosystem.
