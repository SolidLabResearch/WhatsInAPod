## The Solid pod as a permissioned Knowledge Graph # {#vision}
<!-- Repeating the premise -->
The concept of the separation between application and data made possible by the capture of semantics in the data itself forms the premise for the proposed Solid ecosystem.
<!-- The current problem in 2 sentences -->
The current implementation and lack of authoritative definition for Solid is shifting the understanding of the Solid ecosystem and may cause limitations in the development of long term solutions to the problems faced with with the realization of the ecosystem.
<!-- The proposed perspective !!!! -->
To frame the understanding of Solid in a place that is closed to its core premise, we take the perspective that a Solid Pod is fundamentally a permissioned hybrid knowledge graph, exposed through Web APIs. 
Multiple Solid Pods together form a decentralized, permissioned, hybrid knowledge graph.

Make sure we agree on this perspective
{:.comment data-author="RD"}

<!-- Solid as a platform serving data Pods that provide sufficient views on the data **available to the entity interacting with the pod** that it can be organized as a permissioned knowledge graph. -->


<!-- What is a permissioned knowledge graph -->
With the term *permissioned* knowledge graph, we express the concept of a knowledge graph, where the data contained in the knowledge graph is managed through permissions set over the data.
A permissioned knowledge graph implies that all data 

{:.comment data-author="RD"}
This part still needs a good amount of work. This defintion needs to be on point, and a good explanation is required

Note that while we use the term *permissioned* knowledge graph, as this leans close to the original proposition for Solid, we recognize that in the same way permissions are can be seen as specific implementations of policies, the concept of a permissioned knowledge graph serves as a base for more dynamic means of managing access to the Solid pod knowledge graph such as policies.


<!-- Make the point that Solid as LDP emulates a permissioned knowledge graph, but leads to getting stuck on certain points -> problem statement -->
In our proposed definition, the current landscape of Solid as a platform serving data pods that provide a Linked Data platform interface as a view on its internal data satisfies this perspective 

<!-- Make the point that interfaces can be thought of as independent building blocks for management of data, permissions, ... -->
In the context of viewing pods as permissioned knowledge graphs that allow for mutliple interfaces, the specifications used to provide the functionality required for the Pods on the Solid platform to operate can be seen as building blocks for the Solid ecosystem. 
In this sense, we can view the existing specifications for Web Access Controls (WAC) [TODO::cite]() and Access Control Policies (ACP) [TODO::cite]() as two building blocks for managing permissions in the Solid ecosystem.
Similarly, the existing LDP implementation is can be seen as an available building block that fit in the proposed perspective as an interface to manage data on a data pod.
In this context, interfaces that serve as building blocks in the Solid ecosystem should be developed to be minimally interdependent to facilitate combining multiple different interfaces.


























<!-- 


### Permissioned Knowledge Graphs
With the goal in mind of separating the data and applications, we propose the perspective of Solid as a permissioned knowledge graph.

Note that where permissioned knowledge graph, we understand a knowledge graph that can assign permissions for any data quads contained in the knowledge graph. We see the permissions set here as a proxy for policy-based authorization for data, where policies can dynamically describe permissions over data [TODO:: redo this]().


in our perspective is a Knowledge Graph where any collection of data can be grouped under a specific set of user permissions or policies.


### API integration
A consequence of an ecosystem where knowledge graphs can be exposed over the Web over multiple interfaces, is that this brings us back to the problem of interface-integration.

For this perspective to work, we must strive to transition from an ecosystem of API integration towards an ecosystem of data integration.

We argue that the use of Linked Data Platform as an organizational structure for data on a Solid pod relies too much on applications creating localized assumptions and optimizations for the structuring of their data that do not hold for the ecosystem, leading to applications requiring to do API integration on top of these structures, where semantics of the data may encoded and lost in this structuring instead of the data itself.

Where assumptions are currently contained in the API used to organize the data on a data pod, we need to move these assumptions to the data and explicitly encode them into the semantics of the data.

In the perspective as a pod being a permissioned Knowledge Graph that can be exposed over a multitude of APIs, we argue that exposing data over well-defined APIs can alleviate API integration problems.
[TODO:: HOWW???]()



### Interface building blocks

In this context, we can view the current state of Solid as pods that expose their internal knowledge graph over building blocks for authorization (WAC / ACP), data management and querying (LDP) and authentication (Solid-OIDC).
In this context, interface building blocks in the ecosystem should try to be minimally interdependent, to promote reuse over multiple interfaces for other components of Solid.

As a practical example, where the original paper advertised SPARQL as a possible interface to optimize querying on top of the Linked Data Platform data management layer [](cite:cites sambra_solid_nodate), we propose that a SPARQL endpoint may serve as a querying and data management interface on top of the knowledge graph, requiring new building blocks to be researched for authorization over such an interface.




-------------------

With this work, we propose the view of Solid as being data and application independent. 

With this work, we argue that it is not per se the interface of Linked Data Platform that is the cause of issues, but the notion that a Solid pod must adhere to the notion of being an online data space that organizes data as resources over a Linked Data Platform interface.
We pose that the assumptions described above that stem from the use of this organizational structure and the limitations it poses on the data it stores.

We propose the vision of Solid as a platform serving data pods that organize data as a Knowledge Graph [](cite:cites fensel_introduction_2020) [](cite:cites rubenv_reflections_2021).

A network of Solid pods can be seen as a decentralized knowledge graph. 

If a pod can be seen as a Knowledge graph, exposing the contained knowledge can take many forms, as knowledge graphs traditionally have supported multiple interfaces to add, manage and query data [TODO::sources](). 

Say something about integrating interfaces for authorization, data management and querying as building blocks in the ecosystem.

In this vision, a pod can be considered a permissioned, hybrid Knowledge graph that can be accessed through various Web APIs.

 -->


<!-- 
The Solid paper already alluded to shortcomings of the LDP interface (globbing, a separate SPARQL interface for RDF data / metadata)
-> And we will make the argument / take the position that it is more fundamental, that LDP is the problem/limitation rather than the solution. We reframe by seeing one LDP API (there are multiple!) as a possible view on the Pod, which fundamentally is a KG

-->


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