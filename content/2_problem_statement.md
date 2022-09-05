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


To develop applications that are robust and built for longevity,
applications can try to use these available concepts and implementations
to provide local solutions and optimizations for these concepts that may not be shared by the rest of the ecosystem.


<!-- This proposes Solid as a document-centric ecosystem. -->
Where two applications A and B may work with the same data,
both applications may make totally different assumptions of how to structure this data in documents,
and where in the hierarchy to store these documents.
By arbitrarily allowing applications to write data to the Solid pod,
problems in terms of discovering written data, 
multiple applications writing documents to the same location,
applications or users overwriting or moving data from other applications
and other interoperability challenges are commonplace.
In this ecosystem, currently applications are limited in interoperability 
based on their own effort do actively discover more data stored in documents on the pod,
taking care of not overwriting data of other applications and more, 
calling for local assumptions and solutions in these applications 
that may not be shared by the whole ecosystem.

Additionally, the management of permissions forms an additional challenge for applications in the ecosystem.
Where the current authorization systems in the ecosystem are based on the document hierarchy of the Solid pod,
the sharing of data between to and between applications should be managed under user control.
However, the control users have over these permissions is limited to the granularity of the documents containing the data,
which can be generated by the applications working with the Solid pod.
Concretely: a contacts application keeps your contacts and all their information stored on your Solid pod,
but stores all this information in a separate document per contact in the pod.
A new chat application you start to use now wants to find your existing contacts to invite them for a chat.
It looks at a the documents available to the application
that it may suspect to contain relevant information that may have been discovered through other methods
and ask user permission to read these documents containing what it assumes to be contact information.
If the user now allows the chat application to see these contact, 
the user inadvertently has shared *all* the information they have on these contacts with the application,
as there is no granularity in which the user can only share the name or WebID of their contact.
This mismatch in assumptions in how applications distribute data in resources
can lead to problems with sharing too much information, or not enough information,
as the sharing of resources is limited to the document structure of the Solid pod.

The above described ecosystem, dominated by the perspective of a document sharing system
invites the assumptions associated with document-centric systems such as the file system.
These systems are characterized by assumptions encoded in application logic and document structure,
that are not encoded in the data and may not be shared by the whole ecosystem.
It provides an innovation surface for the ecosystem that is limited to the capabilities of
the document-centric nature of the ecosystem and the interfaces exposed by the Solid pods.



<!-- 
### A graph-based understanding
As described above, the document-centric nature of the current Solid ecosystem
invites the assumptions associated with document-centric systems such as the file system.
Here, assumptions are often encoded in the application logic and the resulting document structure, 
where data stored at `/contacts/` is contact information and should be stored with a single document per contact,
even though these assumptions are in no way encoded in the data or shared by the whole ecosystem.
As these assumptions make interoperability a challenging concept, 
it often limits interoperability to asking the user to open documents that they assume to be compatible with applications.

For the Solid ecosystem, we view these interpretations of as a mismatch with the original proposition for Solid,
that proposed an ecosystem of interoperability build on the separation of application and data [TODO::cite]().
Where the perspective of the Solid pod as a document hierarchy limits interoperability and innovation for the ecosystem,
we want challenge this perspective with the perspective of the 
Even in the original paper, 
In the document-based vision of interoperability,
applications are required to integrate semantics shared between applications
and captured in the document hierarchy, 
where further innovations are lost.
To capture the concept of interoperability on a larger scale,
the perspective of graph based interoperability becomes a requirement.

With the understanding of the data stored on the Solid pod as forming a Knowledge Graph,
the problem of interoperability can be solved with new approaches.
Instead of requiring assumptions about a specific hierarchy of documents, 
or a specific structuring of application data into different documents,
by taking the perspective of all available data forming a knowledge grape,
solutions can be 
this perspective takes all  available data 
any application working on the data stored in the Solid pod can first distill the available documents

If we want to achieve interoperability on a greater scale,
a new perspective on the Solid pod is necessary.
In the document-centric understanding of the Solid pod, 
If we are limited by the encoding of specific semantics into the document hierarchy
of the Solid pod, applications must be built on these shared understandings,
leading to an ecosystem of applications being required to integrate the semantics
captured in the APIs instead of being able to integrate the data as is.

where applications can be interoperable without
the requirement of understanding specific semantics encoded in the document hierarchy,
 we need to switch the understanding of the Solid pod to that of a knowledge graph.
 -->

