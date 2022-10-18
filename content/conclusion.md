## Conclusion # {#conclusion}
Different interpretations of the Solid vision
come with different abilities to support that vision.
The dominant document-centric interpretation,
specified by the [Solid Protocol](cite:citesAsSourceDocument Solid_protocol)
as an LDP derivative with per-document access control,
has the benefit of being conceptually simple
and hence developer-friendly.
However, we argue in this article that the simplicity
of a hierarchical document collection
stems from unsustainable shortcuts taken by applications,
as they burrow their own ad-hoc APIs with implicit semantics
into the container meta-model.
These shortcuts hinder the Solid promise of data and application independence
in the long term.
While the data itself contains explicit semantics that can be interpreted by apps,
the organization of that data is such that its storage and retrieval
necessitates out-of-band agreements between different applications,
resulting in significant app-to-app coupling
and subsequent systematic breakage when the ad-hoc APIs inevitably evolve.
Furthermore, we show that the abstraction easily breaks
when apps pursue slightly conflicting goals.

These issues have largely gone unnoticed so far,
because singular apps only encounter smaller problems,
and different apps in a young ecosystem
can still coordinate behind the scenes.
However,
an emergence of more Solid apps that need to interoperate
has increased the frequency of such conflicts.
Stopgaps that are being created to address them
unfortunately only prolong unsustainable practices,
as many issues are inherent to the implicit semantics within ad-hoc APIs.
Proposals typically focus on [making API semantics explicit](cite:citesAsPotentialSolution TypeIndexes,ShapeTrees),
yet they inherit the abstraction's mismatches
when it comes to aspects such as trust and provenance.
This is why we instead suggest pushing the vision forward
by separating the semantics from the API altogether.

We observe that the document-centric interpretation
seems to act as a proxy for a more fundamental concept,
namely a hybrid, contextualized knowledge graph
that attaches metadata to data as well as documents.
Our proposed graph-centric interpretation
put this concept at the heart of each pod,
and considers the Solid Protocol's document interfaces
to be specialized views of an underlying richer source of truth.
This affords more flexibility—and hence independence—in
how multiple apps can interact with the same data.
Crucially,
it also broadens the solution space
for tackling interoperability challenges.
We are no longer confined to working around problems
inherent to the single hierarchy,
but can create solutions at the knowledge graph level
and mint associated API views tailored to the needs and constraints
of specific applications and use cases.
To continue an earlier comparison:
instead of being restricted to a two-dimensional environment,
we have the full three-dimensional space at our disposition
for modeling solutions,
which can then be projected onto as many two-dimensional surfaces as needed.

The graph-centric interpretation shifts the understanding
from a data graph instantiated from a document organization,
to a dynamically instantiated document interface over a data graph,
paving the way for fundamentally graph-centric data management within Solid.
The separation of pod and APIs
allows apps to seamlessly interact via different interfaces to a pod,
depending on what they are optimizing for.
It also opens the door for authorization
with different granularities beyond one specific document structure,
and even for asymmetric read/write interfaces.
They can eliminate the need for elaborate mechanisms
that [explain where apps should write data](cite:citesAsPotentialSolution ShapeTrees):
graph-centric writing can happen
by posting triples or documents directly to the graph,
since it is the responsibility of _views_
to expose all written information in the correct place within APIs.

The consequences of different interpretations of the Solid vision
are not purely conceptual or theoretical:
although implementers might have been unaware previously,
even an implicit interpretation influences
how the storage, publication, and querying functionality of pods
is realized into concrete products.
For instance,
current implementations of alternative Web APIs to pods
are affected by the document-centric interpretation,
as a [current Quad Pattern Fragments interface](cite:citesAsEvidence solid_qpf)
uses for its quads' graph components
the URI where the document API happens to expose them.
Ironically,
the server thereby unwittingly imposes some of the same constraints and mismatches
on an interface that is supposed to mitigate them.
This explains, for example,
why implementers struggle
to find the right permissioning for such derived APIs.
The graph-centric interpretation helps
by considering document URIs to be ephemeral artifacts of one particular API,
which carry no further meaning in other views or apps.

We stress that the current technical reports,
notably the [Solid Protocol](cite:citesAsSourceDocument Solid_protocol),
support the document-centric as well as the graph-centric interpretation.
This serves as a testament to both the orthogonality of the specifications
and the compatibility of the proposed interpretation with the Solid vision.
Specifically,
the graph-centric interpretation embraces and leverages document-based access
as a core building block for APIs.
What changes is the role played by document hierarchies:
rather than seeing one of them as a pod's absolute source of truth,
we find more value in a native ability to construct many views
of a much richer knowledge graph,
for which Web API resources act as a vessel.
Thereby,
what is in a pod can be in the eye of the beholder:
its knowledge graph facilitates a flexible matching of views to use cases.
