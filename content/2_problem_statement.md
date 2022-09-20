## Current document-centric interpretation {#document-centric}
<!-- The first interpretation we look at is document-centric. -->
The currently prevailing understanding of Solid
is that of a _document-centric ecosystem_,
where a pod is considered to be entirely defined
as a permissioned hierarchy of documents and containers.
The pod manages data as a document storage system,
similar to how a file system organizes data
as files and directories.
Structured data is exposed through RDF documents,
which are typically (although not observably for applications)
materialized next to non-RDF resources in a document-based backend.
The separation of application and data is realized
by storing data in documents inside the pod on a separate server,
of which applications are clients.
User control is maintained on via document-level permission management.

### The Solid Protocol

On a specification level,
client access to the server-side document structure
is governed by the [_Solid Protocol_](cite:citesAsSourceDocument Solid_protocol).
Derived from the [_Linked Data Platform (LDP)_ specification](cite:citesAsSourceDocument LDP),
the Solid Protocol is a _client–server specification_
that augments the [_HyperText Transfer Protocol (HTTP)_](cite:citesAsSourceDocument HTTP)
with agreements for accessing and manipulating generic containers and documents
in a [permissioned way](cite:citesAsSourceDocument WAC),
additionally detailing the modification of [RDF documents](cite:citesAsSourceDocument Solid_protocol) specifically.
It thereby enables defining custom document interfaces,
and provides a direct view on the document organization of a pod.
<!--  The authorization interface -->
Authorization is similarly based on the document structure,
and can be realized via
[_Web Access Controls (WAC)_](cite:citesAsSourceDocument WAC) 
or [_Access Control Policy (ACP)_](cite:citesAsSourceDocument ACP).
Even though WAC and ACP differ in their handling of permissions,
both assume a document hierarchy,
where the granularity through which data sharing can be managed
is defined by the granularity of data in the documents on the pod.

Like HTTP and LDP,
the [Solid Protocol](cite:citesAsSourceDocument Solid_protocol)
thus only defines generic rules
to interact with individual resources identified by a URL,
and does not constrain how data is modeled or structured
across these resources.
More formally,
it defines a [protocol](cite:describes Pautasso2014)
consisting of interaction constraints,
but it does not define an [API](cite:describes Pautasso2014)
with specific expectations
of what resources are exposed by this protocol.
For example,
the Solid Protocol provides *slash semantics*
to indicate hierarchical relationships between documents and their parent container
via slash characters (`/`) in their URL,
but it does not impose any specific container identifiers or contents.

Instead,
concrete APIs within this protocol
are de facto created and managed by individual applications.
These will assume that specific contents are to be found
in hard-coded locations such as `/movies/` or `/private/`
(in the latter case even coupling the document organization structure
 of a pod to its permissioning system).
The structure and semantics of these ad-hoc APIs are usually undocumented,
leading to implicit application-to-application contracts.
So-called _client–client specifications_ are underway
to constrain APIs for specific use cases,
such as for [personal profiles](cite:citesAsEvidence WebIDProfile).
However,
continuing this line of work
would imply the creation of such specifications
for every domain model,
given that Solid aims to function for arbitrary kinds of data.
As such,
[other efforts](cite:citesAsPotentialSolution ShapeTrees,TypeIndexes)
instead try to address the problem generically
within the bounds of the document-oriented protocol,
by making some of the document structure of the pod explicit to clients.


### Interoperability challenges
<!-- Interoperability problems -->
Since the Solid protocol
leaves the definition of the API up to individual applications,
app developers are left with many degrees of freedom.
The resulting implicit API semantics endangers the application/data separation,
because the accessibility of the data then depends
on the assumptions made by certain apps.
This cause the Solid vision's central concepts of interoperability and control
to depend on local, application-specific decisions.

<!-- This proposes Solid as a document-centric ecosystem. -->
Let us examine conflicts that arise
via three common applications that use similar data
but impose different demands on an LDP interface to that data.
The first is an **address book app**
where the user views and edits
all details of their professional contacts.
The second is a **birthday app**,
which lets the user message people on their birthday.
The third is a **dating app**
that allows the user to interact with people
on a photo and first-name basis.
To exemplify real-world consequences,
we strive to give each app minimal access.
The address book can access all personal fields for non-dating contacts;
the birthday app can see name, birthdate, and messaging details of all contacts;
the dating app can access first name, profile picture,
and messaging details of dating contacts.
We use these to illustrate that even simple examples
can easily expose four kinds of mismatches
within a interpretation where the pod _is_ the document hierarchy:

<!-- hierarchy mismatch -->
**(i) Internal API modeling mismatches.**
Each app needs to define a single consistent hierarchy
to serialize their data,
which does not reflect the complex nature of real-world organization.
For instance,
the contact app could organize people in categories
such as `/contacts/work/` and `/contacts/sports/`,
which leads to duplication when your colleague
is also a member of your amateur football team.
Hierarchical organizations are thus constrained
in their ability to uniquely represent the real world.

**(ii) External API modeling mismatches.**
Apps can make vastly different assumptions 
on how they structure contact data.
The document hierarchy does not inherently provide interoperability;
this requires either additional interfaces and agreements
or a different interpretation of the documents by applications.
The contacts and birthday apps would need
to store information in the same `/contacts/` container.
Failure to do so would result in apps not being aware of 
the others' data being available on the pod.
Even if they do,
their preferences regarding the organization of that container might vary.
Different contexts might form the basis for address book organization,
whereas the birthday app does not understand
the difference between a colleague or family member,
and would hence not know where to write.
It might instead organize people by birthday month,
which in turn would be nonsensical to the address book.

**(iii) Permission mismatches.**
The coupling of permissions to document organization
provides the main mechanism of control,
but it is based on the flawed assumption
that only one hierarchy exists to organize information.
As permissions are directly tied to specific documents,
the granularity of user control is limited;
and so is that of [_provenance_ and _trust_](cite:describes ProvenanceTrust),
which seem to be implicitly tied to the notion of a document.
For the birthday and dating apps,
address information should _not_ be part of the contact document;
in contrast, the contacts app
would put all contact details into a single document
to apply the same permissioning rules.
As the assumptions do not match,
the user becomes torn between overly granular control
or giving apps too much access.
Similarly, applications sharing the data may assume 
that contact fields are stored in a granular way,
and may wrongly share too many contact details.

**(iv) Local optimization mismatches.**
Current Solid apps are commonly seen
trying to optimize the document-based API
for access patterns that are specific to their needs.
For the contacts app,
one document per contact might be beneficial.
The birthday app might find it more optimal
to have a single document with names and birthdates,
or perhaps one document per month.
The dating app might want the document per contact
to include all exchanged messages,
which would be unnecessary overhead for the other apps.

### Limited knowledge graph interpretation
<!-- The document-centric vision as a KG -->
To improve upon these problems, 
we see attempts at reconciling the document hierarchy
of the Solid pod with the interpretation as a knowledge graph.
Shortcomings of the LDP interface for querying
were already mentioned in early iterations of the Solid protocol [](cite:cites sambra_solid_nodate),
with solutions hinting at per-document SPARQL endpoints
to enable more complex data retrieval.
More recently, the Enterprise Solid Server implementation by Inrupt 
started providing an optional RDF quad-based interface [](cite:cites solid_qpf). 
In this perspective of the Solid pod document hierarchy as a knowledge graph,
the document organization should no longer
be a limiting factor for interoperability.
Applications can query directly RDF data,
even though this data may be spread across 
multiple documents with different organizations within the pod.
This perspective of a Solid pod as a knowledge graph is also 
not limited to the server, as this distillation process
from document hierarchy to knowledge graph
could happen fully on the client side via the LDP interface.

<!-- Still has problems -->
However, even with this perspective on the Solid pod, 
which tries to ignore the document organization of the Solid pod,
we still run into its limitations:

1. The solution only impacts clients going through this optional interface,
whereas other applications coding assumptions against the 
document hierarchy are still limited in their interoperability, 
and do not share the incentive to write rich semantic data to the pod.
2. Writing data is still constrained to the document hierarchy,
as all data must be stored in the context of a document on the pod.
This maintains the problems of writing to common
documents and containers.
3. The distillation process from document hierarchy to knowledge graph
is open to client interpretation, and may be limited by client understanding
or include interface-specific information.
4. The management of permissions is still
tied to the document hierarchy of the Solid pod, and cannot be
defined in terms of the individual statements in the data.

Where the current innovation surface for the Solid ecosystem still leaves options,
we already feel the constraints imposed by the document hierarchy limiting the options.
Even at its currently small scale, 
the ecosystem's interoperability and user control are constrained.
New innovations in the ecosystem
such as the [application interoperability specification](cite:cites interop)
and [research on GDPR compliance](cite:cites Debackere_Colpaert_Taelman_Verborgh_2022)
are limited by the imposed document structure,
and have to work around these limitations.
