## The current document-centric interpretation
<!-- The first interpretation we look at is document-centric. -->
The envisioned Solid ecosystem in its current state is not well defined, 
leaving room for different interpretations of the proposed concepts.
The currently prevailing understanding of Solid
is that of a _document-centric ecosystem_,
where a pod is fundamentally interpreted
as a permissioned document hierarchy.
The separation of application and data is approached
from the perspective of Solid pods as a document storage system.
The pod manages all data as documents in a hierarchical structure of containers,
similar to how a file system organizes data
as files and directories.

Structured data is exposed over HTTP as a document with an RDF representation,
which is typically (although not observably through the HTTP interface)
materialized next to non-RDF resources in a document-oriented backend.
The separation of application and data is realized
by storing data within documents in the pod
rather than in the application itself.
User control is maintained on via document-level permission management.
This document-centric interpretation is
further supported via the concept of *slash semantics*
in the current version of the [Solid Protocol](cite:citesAsSourceDocument Solid_protocol),
where the hierarchical relationships between documents and their parent container are 
explicitly defined through slash characters (`/`) in their URLs.

<!-- read/write interface  -->
The enable users and applications to create and interact with documents stored on the Solid pod,
an adaptation of the [_Linked Data Platform (LDP) specification_](cite:citesAsSourceDocument LDP) was derived.
LDP is a protocol that enables defining custom document interfaces,
and serves to provide a direct view on the document organization of a Solid pod.
<!--  The authorization interface -->
Authorization is similarly based on the document structure,
and can be realized via
[_Web Access Controls (WAC)_](cite:citesAsSourceDocument WAC) 
or [_Access Control Policy (ACP)_](cite:citesAsSourceDocument ACP).
Whereas these specifications differ in their handling of permissions,
both assume the notion of the pod as a document hierarchy,
where the granularity through which data sharing can be managed
is defined by the granularity of data in the documents on the Solid pod.

### Interoperability challenges
<!-- Interoperability problems -->
Since the Solid protocol does not constrain the API exposed through LDP,
app developers are left with many degrees of freedom.
This makes the Solid vision's central concepts of interoperability and control
dependent on application-specific choices.

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
As permissions are directly tied to specific documents in the hierarchy,
the granularity of user control is limited.
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

### Distilled knowledge graph interpretation
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
