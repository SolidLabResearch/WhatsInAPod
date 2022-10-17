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
While the creation of multiple views has been attempted for Solid pods
with SPARQL and QPF interfaces,
their direct derivation from the main API
leads them to still inherit that API's mismatched constraints
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

### Implementation considerations # {#graph-centric-implementation}
<span class="todo"></span>

### Aspects of RDF data in the graph # {#graph-centric-aspects}

- **Context**:
  <span class="todo"></span>
- **Policies**:
  <span class="todo"></span>
- **Provenance**:
  <span class="todo"></span>
- **Trust**:
  <span class="todo"></span>
- **Performance**:
  <span class="todo"></span>

### View-based use case modeling

#### Single-app modeling # {#single-app-modeling}
<span class="todo">compare to [](#single-app-mismatches)</span>

#### Cross-app modeling # {#cross-app-modeling}
<span class="todo">compare to [](#cross-app-mismatches)</span>

#### Permission modeling # {#permission-modeling}
<span class="todo">compare to [](#permission-mismatches)</span>
