## Document-centric interpretation of a pod # {#document-centric}

### Definition

This section discusses the currently prevalent interpretation of a pod,
which is _document_-centric.
As described in [](#definitions),
the Solid Protocol models interactions with data
as recursive containers with RDF and non-RDF documents.
When a server offers this protocol,
clients of this server can define a Web API
by creating containers and documents within those containers.

The document-centric interpretation of a Solid pod is constructed
by assuming that the concrete Web API exposed by the Solid Protocol
_is_ the entirety of pod.
Within this interpretation,
the complete state of the pod is then equivalent
to the single Web API through which it is exposed;
the _ground truth_ of the pod is solely that Web API.
That brings us to the following definition:

_In the document-centric interpretation,
each <dfn id="dfn-document-centric">Solid pod</dfn>
is a single specific hierarchical structure of containers and documents
exposed through the Solid Protocol,
where data and access control rules are stored
in specific RDF and non-RDF documents within that hierarchy._

For example,
a Solid pod would be fully defined
by the following hierarchy and the contents of its documents:

- container `https://sasha.pod/`
  - RDF document `.acl` _(for access control)_
  - container `people/`
    - RDF document `.acl` _(for access control)_
    - RDF document `amal.ttl`
    - RDF document `lucian.ttl`
    - …
  - container `private/`
    - RDF document `.acl` _(for access control)_
    - container `medical-records/`
        - non-RDF document `2022-09-15.pdf`
        - non-RDF document `2022-10-15.pdf`
        - …
  - …

In the above example,
the access control document `https://sasha.pod/private/.acl`
could contain WAC rules
such that only the agent `https://sasha.pod/people/sasha#me`
is allowed to access the container `https://sasha.pod/private/`
and below.

### Practical usage
The above document-centric definition of a pod
leaves several degrees of freedom
as to how the pod is structured
and how the resulting structure is interpreted.
We now describe how today's Solid apps
fill those degrees of freedom in practice.

#### Structure of the main Web API
Importantly,
the current [Solid technical reports](cite:citesAsAuthority solid_technical_reports)
do not impose any specific container structure onto a pod
beyond the presence of a root container `/`.
Some past [suggestions](https://github.com/solid/solid-spec/blob/master/recommendations-server.md)
(such as `/profile`, `/inbox/`, and `/settings/` containers)
are present as defaults in certain server implementations.
Since these are not standardized across the ecosystem,
their presence is not enforced by the server,
and as such cannot be relied upon.

As a consequence,
client-side applications have to define their own (sub-)API
within the URL space available through the Solid Protocol,
by defining a certain container structure
and data distribution across documents within this structure.
Regarding container structure,
we observe two kinds of behavior:

- Some apps use **hard-coded paths**
  to certain containers (e.g., `/contacts/`)
  or documents (e.g., `/profile/card`).
- Some apps use **link traversal**,
  meaning they find the URLs of documents and containers
  by following links from the user's WebID profile document
  and/or via [another index](cite:citesAsExample TypeIndexes).

We also observe _hybrid behavior_,
for instance where an initial path is obtained via traversal
(e.g., `/private/medical/`),
and deeper relative paths are hardcoded
(e.g., `/private/medical/2022/10/`).
In particular,
link traversal is bootstrapped via hardcoded paths:
if no link exists to the certain kind of data,
then a specific document is created at a hardcoded path
and then linked from a profile or index for future usage.

#### Alternative Web APIs to the pod
Given that data under the document-centric interpretation
is structured within a specific document hierarchy,
some applications have encountered practical limitations
when they want to make complex data selections,
especially if the data they require has been structured across multiple documents.
To address such cases,
alternative Web APIs were proposed
in addition to the main Web API on top of the Solid Protocol.

One [proposal](cite:citesAsEvidence sambra_solid_nodate)
suggests exposing a server-side [SPARQL endpoint](cite:citesAsAuthority SparqlProtocol)
over all RDF data in a pod,
enabling fully server-side [SPARQL query](cite:citesAsAuthority SparqlLanguage) processing.
[Another](cite:citesAsEvidence solid_qpf)
suggests to expose this data through a Quad Pattern Fragments (QPF) interface,
to speed up the client-side processing of SPARQL queries
over the entire pod.

Crucially, such alternatives APIs are derived from the main API,
which in the document-centric interpretation is equivalent to the pod.
This concretely manifests itself
in the choice of the data model for the SPARQL or QPF interface.
The RDF 1.1 quads they expose are constructed
by loading the triples from each document,
adding as a graph component the URL of that document.
Take for example the following quad:

- subject: `https://sasha.pod/people/sasha#me`
- predicate: `https://example.org/ontology#birthDate`
- object: `"1984-04-03"`
- graph: `https://sasha.pod/private/medical/2022/10/15.ttl`

Its quad components indicate that
there exists a triple with that specific subject, predicate, and object
in the document with URL `https://sasha.pod/private/medical/2022/10/15.ttl`.
In other words,
the document-centric interpretation of a pod considers
the birthdate statements' occurrence in this specific document on the pod
to be an integral part of the statement itself.

### Consequences
implicit semantics


<span class="todo">Clarify attributes of a document: content grouping, permission, provenance, trust</span>

