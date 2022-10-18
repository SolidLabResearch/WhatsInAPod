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
This hinders the Solid promise of data and application independence:
while the data itself contains explicit semantics that can be interpreted by apps,
the organization of that data is such that its storage and retrieval
necessitates out-of-band contracts between different applications,
resulting in significant app-to-app coupling
and subsequently systematic breakage when ad-hoc APIs eventually evolve.
Furthermore, we show that the abstraction easily breaks
when apps pursue slightly conflicting goals.

These issues have so far largely gone unnoticed,
because singular apps do not hit such problems,
and different apps in a small ecosystem
can still coordinate behind the scenes.
However,
an emergence of more Solid apps that need to interoperate
has increased the frequency of such conflicts.
Stopgaps that are being created to address them
unfortunately only prolong unsustainable practices,
as many issues are simply inherent to the implicit semantics within ad-hoc APIs.
Proposals typically focus on making API semantics explicit [](cite:citesAsPotentialSolution TypeIndexes,ShapeTrees),
yet they inevitably inherit the abstraction's mismatches
when it comes to aspects such as trust and provenance.
This is why we instead suggest pushing the vision forward
by separating the semantics from the API altogether.

We observe that the document-centric interpretation
seems to act as a proxy for a more fundamental concept,
namely a hybrid, contextualized knowledge graph
that provides flexible metadata to data as well as documents.
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
Continuing an earlier comparison,
instead of being restricted to a two-dimensional solution,
we have the full three-dimensional space at our disposition
for modeling our solutions,
which can then be projected onto as many two-dimensional surfaces as needed.

The graph-centric interpretation shifts the understanding
from a data graph instantiated from a document organization,
to a dynamically instantiated document interface over a data graph,
paving the way for fundamentally graph-centric data management within Solid.
The separation of pod and APIs
allows apps to seamlessly interact
via different read and write interfaces to a pod,
depending on what they are optimizing for.
It also opens the door for authorization
with different granularities one specific document structure,
or in fact for asymmetric read/write interfaces.
This can eliminate the need for elaborate mechanisms
that [explain where apps should write data](cite:citesAsPotentialSolution ShapeTrees):
graph-centric writing can happen
by posting triples or documents directly to the graph,
since it is the responsibility of _views_
to expose all written information into the correct place within APIs.

Consequences from interpretation differences are not purely conceptual or theoretical.
For instance,
current implementations of alternative access APIs to pods
are still tainted by the document-centric interpretation:
the current Quad Pattern Fragments interface
uses for its quads' graph components
the URI where the _document-centric_ API happens to expose them.
Ironically,
the server thereby imposes some of the same constraints and mismatches
on the very API that is supposed to mitigate them.
In a graph-centric interpretation,
document URIs are ephemeral artifacts of one particular API
that carry no further meaning in the graph,
nor in other views or apps.

We stress that the document-centric as well as the graph-centric interpretation
are supported by the current technical reports,
notably the [Solid Protocol](cite:citesAsSourceDocument Solid_protocol),
which is a testament to both the orthogonality of the specification
and the compatibility of graph-centricity with the Solid vision.
Specifically,
the graph-centric interpretation of the Solid vision
embraces document-based access as a core building block for APIs.
What changes is the role played by the document hierarchy:
rather than the one absolute source of truth of a pod,
we recognize more value in seeing it as one of many views
into a much more elaborate knowledge graph,
for which APIs act as a vessel.
Thereby,
what is in a pod is essentially in the eye of the beholder:
all depends on which view offers the best fit for a specific purpose.
