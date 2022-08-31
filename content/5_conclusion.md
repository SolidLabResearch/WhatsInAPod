## Conclusion # {#conclusion}
<span class="todo">Emphasize that the existing Solid Protocol (LDP+WAC) remains untouched! That both the existing and proposed interpretation are implemented with the same spec. What changes is below the boundary of the spec, namely the role the spec (LDP) plays on the server.</span>

<!-- With this work, we propose perspective of Solid as ...  -->
With this work, we proposed the perspective that a Solid Pod is fundamentally a permissioned hybrid knowledge graph, exposed through Web APIs. 
<!-- Argue this perspective in itself does not solve the existing difficulties in interoperability  -->
To create the envisioned ecosystem, where through semantic enrichment the separation of applications and data can be accomplished, 
we argue that this perspective is necessary to develop meaningful solutions that promote longevity in their approach.
<!-- Make case that LDP limits the innovation surface for Solid -->
We argue that the current attitude of the Linked Data Platform specification being central to the notion of what constitutes a Solid pod 
promotes a development process of applications making local assumptions and optimizations in their data organization, 
leading to difficulties in creation of the envisioned ecosystem.
<!-- Where LDP can promote assumptions over the API -> we need to get these assumptions in the data as semantics  -->
Additionally, we argue that the current lack of an authoritative definition for what a Solid pod is leads to 
a shift in understanding of the original vision of an ecosystem of application and data interoperability to an
ecosystem defined as the sum of its specifications, limiting the potential innovation surface of the ecosystem 
to the specific choice of specifications.
<!-- The perspective continues from the current state of solid and is completely compatible with the current state -->
We note that perspective proposed in this work does not go against the current state and use of Solid,
but must be seen as an attempt to zoom out the current perspective on Solid,
and provide a framing of the ecosystem that promotes solutions aimed at the interoperability and longevity of the ecosystem.
<!-- The goal of this work is to provide a perspective on the identity of Solid that can help in future work on the topic -->
We do not propose any specific takeaway as to which interfaces may provide solutions for faced difficulties, 
but we hope that the ideas proposed can form the base of new discussions and solutions to tackle the difficulties faced by the ecosystem.






<!-- -------------------

The insights proposed in this work are crucial to eliminate 
the dependency of Solid apps on concrete APIs.
Local assumptions about the shape and organization of data creating localized APIs for applications over the Linked Data Platform interface exposed by Solid data pods provide local optimizations for data discovery, querying performance and more, but hurt the ecosystem as a whole, as assumptions and biases in the organization and discovery of data are not shared across the ecosystem.

The framing of Solid pods as a Knowledge Graph exposed over a multitude of APIs contrary to a data source organized using the Linked Data Platform specification enables us to think more about 
with the goal of reducing local assumptions and optimizations in apps for reasons of longevity. The API over which data is exposed over the Web is a means to an end, and should not define the platform. -->

<span class="todo">What's in a Pod? It's in the eye of the beholder.</span>
