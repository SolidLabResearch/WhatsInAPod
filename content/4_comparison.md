## Comparison # {#comparison}

In this section, we examine possible interpretations of the technological underpinnings, and compared them from the viewpoints of storage, publication and query.


### Comparing interfaces
A common misconception is that a server interface should be identical to the client interface [TODO::cite and word according to Ruben blog](). 
Interfaces however can be abstracted away in a proxy (A web page abstracting an SQL interface in filters), or on the client (Comunica abstracting away a TPF server as SPARQL)[TODO::cite]().

For decentralized networks of data sources such as the Solid ecosystem, these abstractions will mainly be the building blocks for applications to work with data stored on the pods.

We pose that the interface exposing the server Knowledge Graph influences the possibilities and biases for abstractions created over them.
As the Linked Data Platform allows data to be retrieved by retrieving the resources present in the containers and resources advertised by the main index [TODO:: wording??](), consequences of the interface such as public resources in private containers not being discoverable through link traversal of the LDP index will limit the abstractions that can be created over the interface.

Where initiatives such as the Solid Interoperability Specification [TODO::cite]() work to provide answers for these use-cases, they are bound to the organization of data on a pod imposed by the Linked Data Platform specification.


### Data storage comparison
Different interfaces exposing data of a knowledge graph may require different storage solutions to access the underlying data.
Note that again here building blocks providing conversions for different interfaces on specific storage mechanisms may be implemented.

#### Linked data platform interfaces
can use multiple approaches for data storage. The original Solid introduction paper [TODO::cite]() proposed a file-based backend for the storage of non-rdf resources, where rdf resources were stored in a file-based or graph-based system dependent on the optional support for SPARQL over the resources in the pod.

#### [meta-]model-based interfaces
may require more elaborate back-end support depending on the interface exposed. As interfaces such as SPARQL and TPF interfaces rely mostly on an indexed data graph storage mechanisms[TODO:: ...](), 
Support for non-rdf resources must always be taken into account, requiring some sort of organizational structure for these resources to be setup.




### Data publication comparison
The data management interface used by a Solid pod influences how the internal data is published over the Web.
The interface directs how data can be accessed, the granularity of 


#### Linked data platform interfaces
provide a resource-based data organization organized according to the Linked Data Platform specification.

- slash semantics - bias
- data discovery difficulties (type index, interop spec, ...)


#### [meta-]model-based interfaces

- quad / view?-based
- discovery through interface index (SPARQL, TPF, ...)
- non-RDF resource metadata indexing (as in original paper)
- ...



### Data querying comparison
The organizational structure of data published over the interface influences the query resolution and optimization process.
Other differences such as the granularity with which the data can be accessed influences the querying process.

#### Linked data platform interfaces
rely for querying on their data organization, or on derived interfaces to support querying requirements.
As data discovery is hindered by local assumptions made by applications in the organization of data and their shape, either knowledge about the organization of data, or brute forcing of the available resources is required to discover and retrieve data relevant to a query.
The inclusion of optional SPARQL support in the first iterations of the Solid specification [TODO::cite]() supports this.

#### [meta-]model-based interfaces
require the client to discover the exposed interface, and adopt the querying strategy accordingly. A practical example of this is the comunica querying framework, that can adapt its querying strategy according to the datasource interface [](cite:cites Taelman_Van_Herwegen_Vander_Sande_Verborgh_2018).
Querying performance and evaluation is dependent on the exposed interface.
Assumptions on the shape of data contained in the internal knowledge graph still provide the same challenges, but the organizational structure of data should be abstracted away for clients working with and querying the data.


### How does the framing of pods as a Knowledge Graph solve the API integration problem?

In the problem statement, we pose that Linked Data Platform is a meta-API that leads to API integration problems.
How does this solve this issue?

We first pose that API's are a means of syncing data between systems [TODO:: cite](), and data retrieval will always happen over an API (even direct retrieval implicates an API, as you know the location of the resource, etc ...) [TODO:: ...]().

The problem with enforcing Linked Data Platform as the single meta-API for Solid is that biases and 

<!-- 
the APIs are just a means of syncing data between systems 
(see https://ruben.verborgh.org/blog/2021/12/23/reflections-of-knowledge/#abstracting-away-p-4) 
-> Granted but this does not really provide the comforting words that "we will change the API-integration hell into a data-integration opportunity".

cons -> need to support multiple interfaces
pros -> used interface should not have influence on the exposed data, just on how it can be accessed, as the context remains the same? -> something like this but requires some extra thinking? -->