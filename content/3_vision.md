## The Solid pod as a Knowledge Graph # {#vision}

<!-- 
The Solid paper already alluded to shortcomings of the LDP interface (globbing, a separate SPARQL interface for RDF data / metadata)
-> And we will make the argument / take the position that it is more fundamental, that LDP is the problem/limitation rather than the solution. We reframe by seeing one LDP API (there are multiple!) as a possible view on the Pod, which fundamentally is a KG

 -->

With this work, we argue that it is not per se the interface of Linked Data Platform that is the cause of issues, but the notion that a Solid pod must adhere to the notion of being an online data space that organizes data as resources over a Linked Data Platform interface.
We pose that the assumptions described above that stem from the use of this organizational structure and the limitations it poses on the data it stores.

We propose the vision of Solid as a platform serving data pods that organize data as a Knowledge Graph [](cite:cites fensel_introduction_2020) [](cite:cites rubenv_reflections_2021).

A network of Solid pods can be seen as a decentralized knowledge graph. 

If a pod can be seen as a Knowledge graph, exposing the contained knowledge can take many forms, as knowledge graphs traditionally have supported multiple interfaces to add, manage and query data [TODO::sources](). 

Say something about integrating interfaces for authorization, data management and querying as building blocks in the ecosystem.

In this vision, a pod can be considered a permissioned, hybrid Knowledge graph that can be accessed through various Web APIs.
### Interface building blocks

In this context, we can view the current state of Solid as pods that expose their internal knowledge graph over building blocks for authorization (WAC / ACP), data management and querying (LDP) and authentication (Solid-OIDC).
In this context, interface building blocks in the ecosystem should try to be minimally interdependent, to promote reuse over multiple interfaces for other components of Solid.

As a practical example, where the original paper advertised SPARQL as a possible interface to optimize querying on top of the Linked Data Platform data management layer [](cite:cites sambra_solid_nodate), we propose that a SPARQL endpoint may serve as a querying and data management interface on top of the knowledge graph, requiring new building blocks to be researched for authorization over such an interface.








<!-- 

In the original paper for Solid, there was alluded on exposing all data over a SPARQL endpoint

Wat is solid?
- is het een set van protocols?
- is het een concept geimplementeerd met een set protocols?


Solutions can be found through:

extensions to the LDP interface:
- in spec 
- out of spec client managed?
- out of spec client sided?




### Authorization

- Resources are a straightforward way of combining data triples for authorization purposes.
- autorization systems can be adapted to work on a triple basis OR
- other ways of combining triples in resources can be used that do not include LDP biases (slash semantics)
 -->
