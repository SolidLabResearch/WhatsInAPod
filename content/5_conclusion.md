## Conclusion # {#conclusion}
Different interpretations of the Solid vision
come with different abilities to support that vision.
The dominant document-centric interpretation,
specified by the [Solid Protocol](cite:citesAsAuthority Solid_protocol)
as an LDP derivative with per-document access control,
has the benefit of being conceptually simple
and hence easy to start with for developers.
However, we argue in this article that this simplicity
stems from shortcuts being taking by applications,
which build their own ad-hoc APIs with implicit semantics
on top of the LDP container meta-model.
This hinders the Solid promise of data and application independence:
while the data itself contain explicit semantics that can be interpreted by apps,
the organization of data is such that it its storage and retrieval
necessitates out-of-band contracts between different applications,
resulting in significant app-to-app coupling.
Furthermore, we show that the abstraction easily breaks
when apps have even slightly conflicting goals.

These issues have so far largely gone unnoticed,
because singular apps do not hit such problems
and different apps in a small ecosystem
can still coordinate behind the scenes.
However,
an emergence of more Solid apps that need to interoperate,
has increased the frequency of such conflicts,
and stopgaps are being created to work around problems
that are unfortunately inherent to the implicit semantics within ad-hoc APIs.
Proposals typically focus on [making API semantics explicit](cite:citesAsPotentialSolution ShapeTrees),
yet they inevitably inherit the abstraction's breaking points.
This is why we instead suggest taking the vision forward
by separating the semantics from the API altogether.

We observe that the current interpretation
seems to act as a proxy for a more fundamental concept,
namely a permissioned, hybrid knowledge graph
that accommodates data as well as documents.
In our proposed graph-centric interpretation,
document interfaces such as those that exist today
are considered specialized views of an underlying richer source of truth,
affording more flexibility—and hence independence—in
how multiple apps can interact with the same graph data.
Crucially,
this also broadens the solution space.
We are no longer confined to patching inherent LDP-level problems,
but can create solutions at the knowledge graph level
and mint associated API views tailored to the needs and constraints
of specific applications and use cases.

---

<!-- <span class="todo">Emphasize that the existing Solid Protocol (LDP+WAC) remains untouched! That both the existing and proposed interpretation are implemented with the same spec. What changes is below the boundary of the spec, namely the role the spec (LDP) plays on the server.</span> -->

<!-- Reflection on the current ecosystem -->
In the current Solid ecosystem,
the common interpretation of the ecosystem has moved towards a document-centric vision,
where the Linked Data Platform interface is central to the notion of what constitutes a Solid pod.
It creates a limited space for innovation,
by constraining the interoperability and user control of data
to the document hierarchy on the Solid pod.

<!-- With this work, we propose perspective of Solid as ...  -->
With this work, we proposed the interpretation of the Solid pod 
being fundamentally a permissioned, hybrid knowledge graph, 
exposed through Web APIs. 

<!-- what does it do -->
Through this zoomed-out perspective of the ecosystem
we define an innovation space that is not constrained 
by specific protocols, but that can build upon the current 
protocols to provide more general solutions for the 
challenges faced by the ecosystem.

<!-- how does it build -->
By reframing the current protocols for managing data (LDP) 
and authorization (WAC/ACP) into interfaces exposing an 
internal knowledge graph of the Solid pod,
we can re-use these protocols in a new setting.
By shifting the understanding from a data graph 
created over a document system,
towards a document system,
dynamically created over a data graph,
we can fundamentally shift the understanding of the ecosystem
towards a graph-centric interpretation.

Though we do not propose any specific takeaway as to which interfaces 
may be better suited to provide solutions in the current ecosystem,
we invite the reader to think along in how this zoomed-out perspective of the ecosystem
can lead to better solutions to the problems faced by the ecosystem today.

<br>
What's in a pod? *It's in the eye of the beholder*, not in the constraints of the interface.


