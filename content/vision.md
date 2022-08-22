## The Vision

<!-- 
The Solid paper already alluded to shortcomings of the LDP interface (globbing, a separate SPARQL interface for RDF data / metadata)
-> And we will make the argument / take the position that it is more fundamental, that LDP is the problem/limitation rather than the solution. We reframe by seeing one LDP API (there are multiple!) as a possible view on the Pod, which fundamentally is a KG

 -->

Where the current specifications define Solid as a platform where data is managed in a RESTful way, 
as defined by the Linked Data Platform (LDP) recommendation.

The vision we propose is to fundamentally consider a pod as a permissioned, hybrid Knowledge graph that can be accessed through various Web APIs.



### How to support any kind of API?
This can be done through the orthogonal building blocks provided by the Solid specifications! (WebACL, ACP, ...)

### How does this solve the API integration problem?
the APIs are just a means of syncing data between systems 
(see https://ruben.verborgh.org/blog/2021/12/23/reflections-of-knowledge/#abstracting-away-p-4) 
-> Granted but this does not really provide the comforting words that "we will change the API-integration hell into a data-integration opportunity".

cons -> need to support multiple interfaces
pros -> used interface should not have influence on the exposed data, just on how it can be accessed, as the context remains the same? -> something like this but requires some extra thinking?


### The current state of Solid in this vision
The current state of Solid provides a practical notion of the vision, where the Knowledge Graph of a data pod is exposed over a concrete LDP API.

The original paper proposed an extension through the possibility of evaluating SPARQL queries over the data in the pod that is organized according the the LDP interface of the pod.
We note that this interface is still dependent on the bias introduced by LDP (slash semantics, permissions, ...), and can be seen as an optimization (was proposed as optimization kind of in the original paper).


### Integrating the interface in the data retrieval strategies
A commonly made mistake is that the server interface should be identical to the client interface [TODO::cite and word according to Ruben blog]().
At the heart of our solution is the notion that client and API abstractions can differ.

An example of this is that in the current notion of the knowledge graph of a data pod being exposed over LDP, a client running the comunica querying framework [TODO:: cite]() may abstract away this interface, by providing a SPARQL querying interface that makes a translation from the SPARQL query to specific HTTP(S) queries over the data pod by following any found LDP contains relations. 
Note however that in this setup, any public resources contained in a private container may not be discovered as no public links may be available to the public resource from the starting point of the user link traversal.

Where multiple initiatives [TODO:: cite - Type Index, Interop spec, ...]() try to work around these problems in the pod interface through the inclusion of extensions in the form of indexes managed by either clients or the pod server, we argue that as the pod is a permissioned knowledge graph, alternative interfaces could be used to resolve these issues. [TODO:: Make a STRONGER ARUGMENT here]()

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
