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
  - container `private/`
    - RDF document `.acl` _(for access control)_
    - container `medical-records/`
        - non-RDF document `2022-10-15.pdf`

In the above example,
the access control document `https://sasha.pod/private/.acl`
could contain WAC rules
such that only the agent `https://sasha.pod/people/sasha#me`
is allowed to access the container `https://sasha.pod/private/`
and below.

### Practical usage

<span class="todo">Clarify attributes of a document: content grouping, permission, provenance, trust</span>

<span class="todo">derived interfaces</span>
