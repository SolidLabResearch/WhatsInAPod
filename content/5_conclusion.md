## Conclusion # {#conclusion}
<span class="todo">Emphasize that the existing Solid Protocol (LDP+WAC) remains untouched! That both the existing and proposed interpretation are implemented with the same spec. What changes is below the boundary of the spec, namely the role the spec (LDP) plays on the server.</span>

<!-- With this work, we propose perspective of Solid as ...  -->
With this work, we proposed the interpretation of the Solid pod being fundamentally a permissioned, hybrid knowledge graph, exposed through Web APIs. 
<!-- Argue this perspective in itself does not solve the existing difficulties in interoperability  -->
To create the envisioned ecosystem, 
where we can move assumptions captured in the application logic and the document structure
into the semantics of the data itself,
we argue that this zoomed out perspective is necessary to develop meaningful solutions that promote longevity in their approach.
<!-- Make case that LDP limits the innovation surface for Solid -->
We argue that the current document-centric interpretation of the Solid ecosystem,
where the Linked Data Platform specification is central to the notion of what constitutes a Solid pod,
promotes a development process of applications making local assumptions and optimizations over the document hierarchy of the Solid pod.
<!-- How do we impove -->
In contrast, the interpretation of the Solid pod as a permissioned, hybrid knowledge graph,
provides a wider innovation surface, that builds upon the current ecosystem without invalidating the protocols in place. 
<!-- A practical example -->
By changing the role of the LDP interface
from defining the authoritative organization of data 
to providing an interface over an internal knowledge graph,
we can construct any hierarchy over the data suitable for the application,
and are not limited by assumptions of other applications when writing their data.
This way, we change the interface from a limiting factor of the ecosystem,
to enabling interoperability by not restricting the internal data to a single hierarchy.
<!-- An enabler of innovation -->
Through this zoomed out perspective on the role of the Solid pod in the Solid ecosystem, 
we hope to inspire the reader to think along for the innovations that this interpretation of the ecosystem enables,
and to view the current ecosystem as a subset of the possible innovations that Solid can enable.

<!-- The perspective continues from the current state of solid and is completely compatible with the current state -->
We note again that this interpretation proposed in this work does not go against the current Solid protocol,
and should be viewed as an attempt to zoom out the current perspective on Solid,
and provide a framing of the ecosystem that promotes solutions aimed at interoperability and the longevity of the ecosystem.
<!-- The goal of this work is to provide a perspective on the identity of Solid that can help in future work on the topic -->
We do not propose any specific takeaway as to which interfaces may provide solutions for faced difficulties, 
but we hope that the ideas proposed can form the base of new discussions and solutions to tackle the difficulties faced by the ecosystem.

<br>
What's in a Pod? *It's in the eye of the beholder*, not in the constraints of an interface.


