## Graph-centric interpretation of a pod # {#graph-centric}
This section introduces a new interpretation of the concept of a Solid pod,
which is _graph-centric_.

### Design considerations # {#design-considerations}
We start from the limitations of the document-centric pod interpretation,
which essentially assumes the Web API exposed by a pod
to be equivalent to the pod itself.
On the one hand,
we acknowledge the _universality_ and _simplicity_
of document-based APIs,
and in particular of the Solid Protocol,
which offers the building blocks to construct such APIs
with the appropriate authentication and authorization.
On the other hand,
we showed concrete evidence in [](#document-centric-consequences)
that no single such hierarchy is able to
reconcile the conflicting constraints of different use cases,
especially given that core aspects such as policies and provenance
can only be applied with a document-level granularity.

So while we recognize the importance of document-based Web APIs,
we also observe that the simultaneous support for multiple use cases
clearly requires multiple perspectives into the same data,
each satisfying the constraints of particular cases.
Even though the creation of multiple views has been attempted for Solid pods
with SPARQL and QPF interfaces,
their direct derivation from the main API
still leads them to inherit that API's mismatched constraints
on the modeling of policies, provenance, and trust.

In other words,
aiming to derive richer views from the main pod API
is akin to using a real-world object's _two-dimensional projection_
to derive alternate two-dimensional projections of that same object.
Because any two-dimensional projection
is inherently designed to discard information of the original,
the creation of complementary alternative projections
actually requires the object's underlying _three-dimensional reality_ instead.
The two-dimensional projection was only ever meant
as a helpful approximation of the three-dimensional object.

Translating this dimensionality metaphor to the world of pods,
we conclude that today's single hierarchical API to a pod
serves as a _proxy_ for the underlying knowledge graph
formed by the union of the pod's interlinked RDF documents—except that
this union cannot adequately be reproduced
because significant parts of its semantics are being discarded by that API.
Solid applications looking to leverage
the potential of this Linked Data knowledge graph,
will thus always be hindered by
the limitations of one arbitrarily formed document API
acting as its sole access gateway.

### Definition # {#graph-centric-definition}
Given the above observations within the document-centric interpretation,
we create a new interpretation
that shifts the function of a pod's main API
from being the pod itself
to acting as _one of many_ possible interfaces
to an underlying knowledge graph,
which _is_ the pod.
The _source of truth_ is a knowledge graph
consisting of documents as well as RDF statements,
from which multiple Web APIs can be derived.
Hence, no particular API is more prominent than any other.
We define it as follows:

_In the graph-centric interpretation,
each <dfn id="dfn-graph-centric">Solid pod</dfn>
is a hybrid, contextualized knowledge graph,
wherein “hybrid”
indicates first-class support for both documents and RDF statements,
and “contextualized”
the ability to associate each of its individual documents and statements
with metadata such as policies, provenance, and trust._

### Example
For example,
the pod `https://sasha.pod/` could be a hybrid knowledge graph
consisting of:

- RDF triples expressing contact details of `https://sasha.pod/people/amal#me`
- RDF triples expressing contact details of `https://sasha.pod/people/lucian#me`
- a PDF document containing medical images dated 2022-09-15
- RDF triples representing a blood test result dated 2022-10-15
- …

Examples of associated metadata within this pod are:

- The RDF triples about Amal form a shared context with specific trust and provenance.
- A policy states that professional contact names can be publicly readable.
- A policy states that contacts' phone numbers are only visible to Sasha.
- The provenance of Lucian's phone number is a specific email.
- We trust that the test result is unmodified and accurate,
  because it is certified by a medical professional.

Below is one possible Web API on top of this pod
that conforms to the Solid Protocol:

- container `https://sasha.pod/`
  - container `contacts/work/`
    - RDF document `.acl` _(for access control)_
    - RDF document `amal.ttl`
    - RDF document `lucian.ttl`
    - …
  - …

The same pod could simultaneously offer other Web APIs through the Solid Protocol:

- container `https://sasha.pod/`
  - container `people/birthdays/`
    - RDF document `.acr` _(for access control)_
    - RDF document `january.ttl`
    - RDF document `february.ttl`
    - …
  - …

Furthermore, the pod could have SPARQL and QPF interfaces on top of its knowledge graph,
in addition to other Web APIs.

### Aspects of RDF data in the graph # {#graph-centric-aspects}
Importantly,
the “hybrid” and “contexualized” qualifiers
are equally important as the “knowledge graph” term in the definition.
This means that off-the-shelf triplestores or quadstores
do not qualify as implementations of a pod.
Whereas they could possibly be used as physical storage for such a pod
(see [](#comparison-storage)),
any implementation requires native support for documents and metadata.

The ability to generate multiple Web APIs
that act as views on the data
is required functionality for the pod.
Below,
we discuss how the aspects from [](#document-centric-aspects)
are modeled in the pod and the resulting APIs.

- **Context**:
  Each triple or document in the pod
  can be associated with multiple contexts.
  For instance,
  users could assign triples to specific resources in Web APIs
  (“this triple is in the documents `/records/2022-15-10.ttl`
   and `/records/2022-15-10-summary.ttl`”),
  or smaller ad-hoc groupings could be created
  (“these triples have a topical relationship”).
  An API can reflect this context
  through it resource structure,
  or by including explicit metadata in its response.

- **Policy**:
  Policies could be assigned to resources in a Web API
  and/or to individual triples.
  In case the policies are assigned to individual triples,
  their inclusion in a response can be conditionally determined
  by whether or not the requesting agent has access.

- **Provenance**:
  Provenance can be associated with individual triples or groups of triples,
  similar to how generic context is modeled.

- **Trust**:
  Trust can be expressed either as a function of provenance,
  or explicitly assigned to (groups of) triples, like context.

- **Performance**:
  The performance is no longer a function of the pod structure itself,
  but rather reflected in how well a specific API
  matches the access patterns of a given use case.
  In other words,
  performance concerns can be addressed
  by defining relevant APIs on top of the underlying knowledge graph.

The implementation of those aspects
differs from the document-centric interpretation
in two crucial ways:

1. All 5 aspects are **modeled _explicitly_**:
    either as metadata in the knowledge graph
    that can then be reflected in an API
    (for _context_, _policy_, _provenance_, and _trust_),
    or in the definition of a specific API
    (for _performance_).
2. Each aspect can have a **different granularity**.
    For instance,
    a certain group of triples could share the same provenance,
    but have different policies applied to them.

### View-based use case modeling
We will now revisit how the graph-centric interpretation
addresses the mismatches of the document-centric interpretation
([](#document-centric-consequences)).

#### Single-app modeling # {#single-app-modeling}
Applications are no longer restricted to a single hierarchy
for modeling information,
because the view-based approach allows overlapping resources
without requiring copies.

For example,
if a person is both a colleague and a badminton player,
their details can be available through both
the documents `/contacts/work/amal.ttl` and `/contacts/sports/amal.ttl`,
wherein
the containers `/contacts/work/` and `/contacts/sports/`
could have different policies associated with them.
From the perspective of a consumer,
neither document is more authoritative than the other,
as they are generated from the same triples in the underlying knowledge graph.
Similarly,
medical records can be organized
by both date (`/medical/2022/10/15.ttl`)
and topical evolution (`/medical/heart-rate-2021-2022.ttl`),
allowing them to have different provenance and trust.

#### Cross-app modeling # {#cross-app-modeling}
Every app can choose the modeling that best fit its use case,
as the same knowledge graph can be exposed through multiple Web APIs.
This allows applications to find the API that best matches its access patterns
or, conversely, the pod to define APIs based on the needs of use cases.

For example,
the address book app can be built using an API
that organizes the attributes of a person in a single document,
whereas the birthday app can group all birthdays together.
That way, neither application downloads more data than necessary.
Similarly,
medical data can be grouped depending on the analyses that will be performed.
Note that exact matches of access patterns to APIs
will not always be possible nor desired;
the idea is rather to offer a couple of core APIs
that minimize overhead
across a number of use cases [](cite:citesAsRecommendedReading verborgh_jws_2016).

#### Permission modeling # {#permission-modeling}
Finally,
the granularity of resources in a given API
can be aligned with the granularity of policies,
since this granularity does not have to be shared with the other aspects.

For example,
the birthday app could have a read/write API to the contacts
that does not include access to their email addresses or phone numbers.
A derived medical report could only display vitamin levels
but leave out highly sensitive information such as HIV status,
while leaving intact the provenance and trust of the original context.
