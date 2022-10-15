## Document-centric interpretation of a pod # {#document-centric}

### Definition # {#document-centric-definition}
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

#### Structure of the main Web API # {#document-centric-api}
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
  which means they find the URLs of documents and containers
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

#### Implicit and explicit meanings of RDF document boundaries # {#document-centric-meaning}
From the way current apps organize data in RDF documents,
we can observe the meaning they ascribe to such a document.
Noting that Solid typically uses RDF 1.0 documents
(so only triples, and not quads as in RDF 1.1),
we consider the occurrence of an RDF triple in a document
to carry the following meanings:

- _(implicit)_ **Context**:
  the occurrence of certain triples within the same document
  often implies that they are somehow interrelated,
  and that those triples somehow relate to the document.
  This latter aspect is sometimes visible within certain triples,
  whose subject (e.g., `https://sasha.pod/people/sasha#me`)
  defines a URL fragment (e.g., `#me`)
  on the document identifier (e.g., `https://sasha.pod/people/sasha`).
- _(explicit)_ **Permissions**:
  both the [WAC](cite:citesAsAuthority WAC)
  and the [ACP](cite:citesAsAuthority ACP) specifications
  assign authorizations on a document level of granularity.
  Either the document can be accessed by a given agent in its entirety or not,
  thus resulting in all triples within a document
  sharing the same authorization rules.
- _(implicit)_ **Provenance**:
  the document somehow captures the notion
  that its triples originate from a specific source or event,
  of which the document was a result.
- _(implicit)_ **Trust**:
  the document defines a single boundary of trust for all of its triples.
  For example,
  a user's profile document is typically fully trusted by the user
  (because they are usually the only party with write access to it),
  whereas inbox documents created by third parties
  might contain triples that are not trusted.
- _(implicit)_ **Performance**:
  the document groups together a number of triples
  because it improves the performance of certain use cases.
  For instance,
  triples that are often used together might be in the same document,
  and triples that are less needed might be in extension documents,
  in order to optimize the number of HTTP requests and the used bandwidth.

We remark that of these 5 aspects,
only the _permissions_ on the document are modelled explicitly.
The _context_ is implicitly assumed
because triples occurring in the same place
typically were created by the same or related write operations,
and because those triples are necessarily read together by apps.
The _provenance_ and _trust_ are similarly derived
from implicit assumptions about a shared origin,
and the knowledge of specific permissions
and thus agents that could have written to the document.
Notably,
the fact that an identifier (e.g., `https://sasha.pod/people/`)
is contained within a certain pod root container (e.g., `https://sasha.pod/`)
does encode some explicit provenance about the document and its triples
(e.g., “they were found in Sasha's pod”),
but not necessarily about its creator or level of trust
(e.g., multiple actors might have write access to the document).
Finally,
the _performance_ is typically the result of educated guesses,
but seldom the result of actual performance measurements.

#### Alternative Web APIs to the pod # {#document-centric-alternative-apis}
Given that data under the document-centric interpretation
is structured within a specific document hierarchy
with the aforementioned explicit and implicit meanings,
several applications encounter practical limitations
when the data they require happens to be structured across multiple documents.
In an attempt to address such cases,
alternative Web APIs were proposed
in addition to the main Web API on top of the Solid Protocol.

[One proposal](cite:citesAsEvidence sambra_solid_nodate)
suggests exposing a server-side [SPARQL endpoint](cite:citesAsAuthority SparqlProtocol)
over all RDF data in a pod,
enabling fully server-side [SPARQL query](cite:citesAsAuthority SparqlLanguage) processing.
[Another proposal](cite:citesAsEvidence solid_qpf)
suggests to expose this data through a read-only Quad Pattern Fragments (QPF) interface,
to speed up the client-side processing of SPARQL queries
over the entire pod.
Whereas these alternative APIs can alleviate
part of the _context_ and _performance_ constraints of the main API,
they come with challenges to implement _permissions_
and to adequately model _provenance_ and _trust_ in their responses.

Crucially, such alternative APIs are always derived from the main API,
because it is equivalent to the pod in the document-centric interpretation.
The derived APIs thereby unavoidably inherit some of the explicit and implicit meanings
from the document-based main API.
Concretely, the direct derivation from the main API manifests itself
in the choice of the data model for the SPARQL and QPF interfaces.
The RDF 1.1 quads they expose are constructed
by loading the triples from each document,
adding as a graph component the URL of that document.
The following example quad reflects this:

- subject: `https://sasha.pod/people/sasha#me`
- predicate: `https://example.org/ontology#birthDate`
- object: `"1984-04-03"`
- graph: `https://sasha.pod/private/medical/2022/10/15.ttl`

Its components signify that
there exists a triple with that specific subject, predicate, and object
in the document with URL `https://sasha.pod/private/medical/2022/10/15.ttl`.
In other words,
the document-centric interpretation of a pod considers
the birthdate statements' occurrence in this specific document on the pod
to be an integral part of the statement itself.

### Consequences of the single hierarchy
In this section,
we will examine and critique the consequences
of the document-centric interpretation of a pod.
Specifically,
we study the limitations of the single hierarchy it causes ([](#document-centric-definition)),
and the effects of the implicit semantics in its structure ([](#document-centric-api))
and documents ([](#document-centric-meaning)).
While some consequences could in theory
be mitigated by alternative APIs ([](#document-centric-alternative-apis)),
the effectiveness thereof is hindered
by the necessity of those alternatives to derive from the main API structure.

#### Single-app modeling mismatches
Each app needs to define a single consistent hierarchy
to serialize their data,
which does not reflect the complex nature of real-world organization.
For instance,
the address book app could organize people in categories
such as `/contacts/work/` and `/contacts/sports/`,
which leads to duplication when a person's colleague
is also a member of their badminton team.
A similar situation occurs when we need to decide
to group health measurements by date (`/medical/2022/10/15.ttl`)
or by topical evolution over time (`/medical/vitamine-d-levels.ttl`)

Hierarchical organizations are thus either
constrained by their necessity to commit to a single representation of the real world,
or in need of mechanisms to cope with the effects of data duplication or virtualization.
An alternative API circumvents some of these limitations
when it comes to reading,
although the provenance and trust of the resulting responses
are even less explicitly defined than in the main API.
Writing is still fully coupled to the destination documents in the main API,
since the quad components of each triple need to contain a specific document URL.

#### Cross-app modeling mismatches
The document-centric view of the Solid Protocol
does not inherently provide interoperability,
because apps are still responsible
for determining the specific API that defines
the document and container structure they will access.
To make matters worse,
different apps and use cases can have competing interests
that lead them to prefer one API structure over another.

For example,
interoperability requires the address book and birthday apps
to store their data in the same place,
for instance, the `/people/` container.
Failure to do so would result in apps not being aware of 
the others' data being available on the pod.
However,
their preferences regarding the organization of that container vary.
The address book app,
which lets the user edit contacts one by one,
has a _context_ and _performance_ incentive to
place all of the attributes of a contact in a single RDF document,
leading to an organization such as:

- `/people/work/dani.ttl`
- `/people/work/kiran.ttl`
- `/people/personal/kai.ttl`
- `/people/personal/luka.ttl`
- …

In contrast,
the birthday app aims to quickly determine
which celebrations are coming up,
probably preferring a structure more like:

- `/people/work/birthdays.ttl`
- `/people/personal/birthdays.ttl`

Or possibly even:

- `/people/birthdays/january.ttl`
- `/people/birthdays/february.ttl`
- …

Similarly,
whether medical records are organized by date
or by measurement over time,
depends on the specifics of a current use case.

#### Permission mismatches
Contextual- and performance-based grouping
are trade-offs that can be overcome with compromises,
such as accepting that certain use cases will be slower than others.
Unfortunately,
the imposed grouping of multiple different aspects in the same document
can also lead to more sensitive and insurmountable conflicts
for the _permissions_, _provenance_, and _trust_ aspects.

Since the coupling of permissions to document organization
provides the only mechanism of control in the document-centric view,
some use cases with conflicting requirements
cannot effectively be realized today.
For example, assume that the address book app
indeed organizes contacts as one person per document:

- `/people/dani.ttl`
- `/people/kiran.ttl`
- …

In that case, the birthday app would be able to read
(and needing to parse)
people's personal details such as addresses and phone numbers,
whereas the expectation is that
it should only access names and birthdays.

Insurmountable conflicts become even more apparent with the medical use case.
The results of a given blood test might be stored in a single document,
and thus have a single permission boundary associated with it.
If that test result contains both vitamin levels and an HIV status,
then the document-based access control
prevents users from only giving access to their vitamin levels.

The fact that conflicting requirements between aspects
would necessitate the complexity of copies,
flags a strong limitation of any single hierarchical API.
One partial solution is to split these pieces of data into different documents,
but this results in suboptimal boundaries
for purposes of context, provenance, and trust.
Users thus find themselves torn between giving apps too much access,
or having to deal with overly granular control—in the extreme case causing situations
that necessitate managing micro-documents with only one or a handful of triples.
Whereas the degrees of freedom in the Solid Protocol
allow for any such structures,
the resulting API would be highly impractical for humans and machines alike.
Another solution involves creating and maintaining
a copy of the document with a subset of the data,
which—in addition to the overhead of managing such copies—would also
generate a different associated context, provenance, and trust,
especially if writing to such derived documents is needed.
Furthermore,
all these aspects would necessarily be reflected in any derived APIs,
which are tied to the main API's document-based structure and boundaries.
