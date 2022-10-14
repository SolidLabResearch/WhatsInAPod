## Conclusion # {#conclusion}
<span class="todo">Discuss transition from RPC to REST to graph?</span>

Different interpretations of the Solid vision
come with different abilities to support that vision.
The dominant document-centric interpretation,
specified by the [Solid Protocol](cite:citesAsSourceDocument Solid_protocol)
as an LDP derivative with per-document access control,
has the benefit of being conceptually simple
and hence developer-friendly.
However, we argue in this article that the simplicity
afforded by a hierarchical document collection
stems from shortcuts taken by applications,
which are burrowing their own ad-hoc APIs with implicit semantics
into the container meta-model.
This hinders the Solid promise of data and application independence:
while the data itself contains explicit semantics that can be interpreted by apps,
the organization of that data is such that it its storage and retrieval
necessitates out-of-band contracts between different applications,
resulting in significant app-to-app coupling
and subsequently systematic app breakage when ad-hoc APIs eventually evolve.
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
Proposals typically focus on making API semantics explicit [](cite:citesAsPotentialSolution ShapeTrees,TypeIndexes),
yet they inevitably inherit the abstraction's mismatches.
This is why we instead suggest pushing the vision forward
by separating the semantics from the API altogether.

We observe that the document-centric interpretation
seems to act as a proxy for a more fundamental concept,
namely a permissioned, hybrid knowledge graph
that accommodates data as well as documents.
Our proposed graph-centric interpretation
put this concept at the heart of each pod,
and considers document interfaces such as those that exist today
as specialized views of an underlying richer source of truth.
This affords more flexibility—and hence independence—in
how multiple apps can interact with the same graph data.
Crucially,
this also broadens the solution space
to tackle interoperability challenges.
We are no longer confined to working around inherent LDP-level problems,
but can create solutions at the knowledge graph level
and mint associated API views tailored to the needs and constraints
of specific applications and use cases.
The same app can seamlessly interact
via different read and write interfaces to a pod,
depending on what it is optimizing for.
This also opens the door for authorization
with different granularities beyond the scope of
one specific LDP interface's document organization.
We thereby shift the understanding
from a data graph instantiated from a document organization,
to a dynamically instantiated document interface over a data graph,
paving the way for fundamentally graph-centric data management within Solid.
Through the zoomed-out perspective of the pod
as a knowledge graph exposed over Web APIs, 
we refocus on the data itself
and reframe the interfaces as means to an end.

Consequences from interpretation differences are not purely conceptual or theoretical.
For instance,
current implementations of alternative access APIs to pods
are still tainted by the document-centric interpretation.
A concrete consequence manifests itself
in the current [Quad Pattern Fragments API](cito:citesAsEvidence solid_qpf),
meant to facilitate complex queries over a pod.
This _quad-centric_ API offers pattern-based access to RDF quads,
whose graph component is defined as
the URI where the _document-centric_ API happens to expose them.
Ironically,
the server thereby imposes some of the same LDP constraints and mismatches
on the very API that is supposed to mitigate them.
This happens because the additional API is built on top of the LDP-based API,
which this interpretation considers to _be_ the pod.
In a graph-centric interpretation,
the pod is instead a knowledge graph with multiple APIs as views.
Document URIs are ephemeral artifacts of one particular API
that carry no meaning in the graph,
nor in other views or apps.
Therefore,
a Quad Pattern Fragments API within the graph-centric interpretation
would never use the document URL from another API as fourth quad component.

We stress that the document-centric as well as the graph-centric interpretation
are supported by the current Solid specifications,
notably the [Solid Protocol](cite:citesAsSourceDocument Solid_protocol),
which is a testament to both the orthogonality of the specification
and the vision compatibility of graph-centricity.
Specifically,
the graph-centric interpretation of the Solid vision
still embraces document-based access as a core building block for APIs.
What changes is the role played by the document hierarchy:
rather than the one absolute source of truth of a pod,
we recognize more value in seeing it as one of many views
into a much more elaborate knowledge graph,
for which APIs act as a vessel.
Therefore,
what is in a pod is essentially in the eye of the beholder:
all depends on which view offers the best fit for a specific purpose.
