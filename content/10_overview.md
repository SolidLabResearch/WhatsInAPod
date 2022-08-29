

<!-- 

-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------

**OVERVIEW -- v1**  

-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------


**intro**

- Solid proposed as a data platform using the open Linked Data Platform spec to organize data.
  - people equate the Solid pod to the LDP interface
  - give a working definition
  - is there an agreed upon definition that is authoritive?
- We see however that the use of the Linked Data Platform specification leads to a lot of ASSUMPTIONS in the organization of data on the pod.
- This leads to difficulties in discovery, querying, semantics? and interoperability of data.
- In this paper, we propose the vision of Solid as a platform of data pods exposing an internal Knowledge Graph supporting multiple interfaces (such as LDP and SPARQL) over their internal Knowledge Graph.

- Promise of Solid: Data and App independent

**Problem statement**

- We see that the definition of a pod gets equated to the LDP interface
  
- We see the use of the Linked Data Platform spec leads to localized ASSUMPTIONS in the organization of data on the pod by applications
- 
  - Granularity is resource based through LDP.
  
  - Hierarchical nature of the LDP spec (same as filesystem) leads to semantics in the data location through slash semantics 
    - e.g. original paper using slash semantics for event storage based on date
    - Leads to semantic context being stored in the data path (not machine readable)
    - WHAT DOES MEAN -> consequence
      - model situations that cannot be captured like this
      - example of meta-API
    - LDP has constraints, real world data modelling has constraints, these may be orthogonal in situations and not match
    - **point 1: mismatch between hierarchy and real world**

    - putting the meaning in the data removes mismatch between semantics and data. semantics should be in the data and in the organizational structure

  - Containers and resources lead to data stored separately (e.g. digita storing data of different applications in different containers, idem as e.g. program files on the filesystem.)
    - This leads to data separation, and implicit context being attributed to storage location (data stored at `/apps/solidbook/` is data from the `solidbook` app.)
    - With the advantage of facilitating permission management for applications
    - **point 2: Data hierarchy is created by applications in contrast to separation of app and data**

  - **point 3: semantics encoded in things that are not data**
    - care of ordering of points
  
  - LDP leads to local assumptions and optimizations for applications(, at the cost of interoperability?).
    - We can see this clearly in the Inrupt Developer Libraries for Solid, where the developer interface only provides functionality to retrieve data for which you know both the location and the used schema, with almost no regard for data discovery.

  - **Coupling with permission**
    - permissioning coupled with container structure
    - one true hierarchy that matches with permissioning is the assumption - does not always hold
    - organization is ordered according to applications -> applications define your permissions indirectly


-----------------

  - solid about **splitting data and apps**
  - key: **semantics in the data**
  - now; ldp **mismatch hierarchy and real world**
  - then: **hierarchy misused** by applications to model things how they like - **semantics outside of data**
  - even worse: applications make **local optimizations** and assumptions creating ecosystem thats not interoperable anymore
  - permissions: as permissions are tied to hierarchy, **indirectly leads to applications defining your permissions.**

-----------------

  - **What were we trying to do**
    - create permissioned knowledge graph
      - all of the above is captured in this concept
      - issues come from the emulation of permissioned knowledge graph through LDP and not from the concept of permissioned knowledge graph

cause::

- LDP is a not a real API (in the same way that a file system is not a real API). It is a meta-api that allows an infinite ways to organize data.
  - In its base form, combined with access controls, it provides little to no functionality for data interoperability.
  - The goal of Linked Data is data integration, where LDP actually still requires a lot of api-integration through assumptions or agreements between applications on certain data organizations (e.g. solid chat in mashlib, ...).
  - **Ldp imposes constrainsts - leaves degrees of freedom that is used to create additional semantics not captured in the data**


**Perspective**

- In this paper, we propose the perspective of Solid being data and app independent. 
- Where currently often used perspective of Solid IS LDP, or Solid is ...
- We propose the perspective of a Solid pod as permissioned knowledge graph ... 

-  if we keep seeing Solid pods as containers and resources we're going to get stuck

- Make sure it stays exemplifying -> 
  - Make point of SPARQL endpoint over the document proposed in paper
  - With this view, we can see the SPARQL endpoint as exposing the RAW data, without requiring the document organization of LDP 
  - Dont go to deep - more of an example


- OH no - what about the API's => Oh no, what about all the local assumptions
  - Solid marks transition from API based integration to data based integration
  - the assumptions are now in the API -> we need to move the assumptions to the data and try to make them specific using semantics -> this is a strong conclusion

- **permissions are a proxy for policies / parameters**
  - permissioned -> we can zoom this out to parameterized / policy based


------

- This as a contrast to the LDP-organization currently used, that organizes data in resources.
- these pods can expose their internal KG over a multitude of interfaces
  - wont this reduce interoperability through not supporting other interfaces?
  - argue currently little to no interoperability without prior agreements on data shape and organization over LDP.
  - original paper includes support for SPARQL for querying -> this goes along with this vision.
- APIs could be built through modular building blocks as is the case now (LDP, WAC/ACP, Solid-OIDC)
  - building blocks should be built with AS LITTLE INTER-DEPENDENCY AS POSSIBLE
- The current implementation of Solid is a specific implementation of this vision that can be expanded upon.
  - As the SPARQL in the original paper does + how Jeroen handles it in the architecture paper, more links???


**Comparison**

- In this step, we compare the frameworks of thinking about Solid as a collection of resources exposed over Linked Data Platform, compared to Solid as a Knowledge Graph exposed over a [meta-]model-based interfaces (SPARQL, TPF, ...).

---------------

- **What do we need? -> A good example**
  - compare 2 cases -> precise examples
    - store address book in classic solid with LDP
      - if you store this LDP API in file system -> straightforward
      - SPARQL endpoint -> encode document in which this is stored


- **make point that query and API are separate!**
  - suggestion of SPARQL endpoint per resource
  - bring some clarity to this point


- Storage
  - LDP
    - File-based and/or SPARQL-based backend
  - KG
    - pretty much same. Graph database for RDF, file based for non-RDF
  
- Publication
  - LDP
    - resource based
    - slash semantics - bias
    - data discovery difficulties (type index, interop spec, ...)
    - ...
  - KG
    - quad / view?-based
    - discovery through interface index (SPARQL, TPF, ...)
    - non-RDF resource metadata indexing (as in original paper)
    - ...

- Query
  - LDP
    - Data organization assumptions (how and where data stored)
    - Data shape assumptions (what predicates, ...)
  - KG
    - Interface negotiation (SPARQL, TPF, LDP, ...)
      - Interface-specific implementations and optimizations
    - Data shape assumptions (what predicates, ...)
    - 


**Conclusion**

- Viewing a pod as a KG does not solve issues in itself, but provides a thinking framework to think about and solve issues focused more on the data than the interface.

- queries and APIs are separate - important to bring this point forward again

- LDP gives us only a limited innovation surfaces

- API based integration to data integration

- (not for here) resources are not well defined units of data. You can see the whole pod as a single resource (all rdf data).

------------

- It does however provide a more robust framework to think about solving challenges for decentralized data pods
- It enables more functionality and optimization though more workload-specific interfaces (cfr databases over a filesystem)
- This vision builds upon the current implementation without any discrediting of work done, but with the hope of building on the existing specifications and ideas to solve even more challenges.

T

 -->

<!-- 

-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------

**OVERVIEW -- v2**  

-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------

**intro**
- Solid proposed as a data platform using the open Linked Data Platform spec to organize data.
  - people equate the Solid pod to the LDP interface
  - give a working definition
  - is there an agreed upon definition that is authoritive?
- We see however that the use of the Linked Data Platform specification leads to a lot of ASSUMPTIONS in the organization of data on the pod.
- This leads to difficulties in discovery, querying, semantics? and interoperability of data.
- In this paper, we propose a perspective of Solid pods as exposing an internal Knowledge Graph supporting multiple interfaces (such as LDP and SPARQL) over their internal Knowledge Graph.
- 
- solid about **splitting data and apps**
- key: **semantics in the data**

- Promise of Solid: Data and App independent


**problem statement**

- solid about **splitting data and apps**
- key: **semantics in the data**
- now; ldp **mismatch hierarchy and real world**
- then: **hierarchy misused** by applications to model things how they like - **semantics outside of data**
- even worse: applications make **local optimizations** and assumptions creating ecosystem thats not interoperable anymore
- permissions: as permissions are tied to hierarchy, **indirectly leads to applications defining your permissions.**



- **What were we trying to do**
  - create permissioned knowledge graph
    - all of the above is captured in this concept
    - issues come from the emulation of permissioned knowledge graph through LDP and not from the concept of permissioned knowledge graph

- **cause?**: LDP is a not a real API (in the same way that a file system is not a real API). It is a meta-api that allows an infinite ways to organize data.
  - In its base form, combined with access controls, it provides little to no functionality for data interoperability.
  - The goal of Linked Data is data integration, where LDP actually still requires a lot of api-integration through assumptions or agreements between applications on certain data organizations (e.g. solid chat in mashlib, ...).
  - **Ldp imposes constraints - leaves degrees of freedom that is used to create additional semantics not captured in the data**


**perspective**

- In this paper, we propose the perspective of Solid being data and app independent. 
- Where currently often used perspective of Solid IS LDP, or Solid is ...
- We propose the perspective of a Solid pod as permissioned knowledge graph. argue this is a goal that has been tried to achieve with LDP but we are getting stuck ... 


- Make sure it stays exemplifying -> 
  - Make point of SPARQL endpoint over the document proposed in paper
  - With this view, we can see the SPARQL endpoint as exposing the RAW data, without requiring the document organization of LDP 
  - Dont go to deep - more of an example


- OH no - what about the API's => Oh no, what about all the local assumptions
  - Solid marks transition from API based integration to data based integration
  - the assumptions are now in the API -> we need to move the assumptions to the data and try to make them specific using semantics -> this is a strong conclusion

- this approach allows us to regard interfaces that are better able to split data and applications, ...7

- **permissions are a proxy for policies / parameters**
  - permissioned -> we can zoom this out to parameterized / policy based

- APIs could be built through modular building blocks as is the case now (LDP, WAC/ACP, Solid-OIDC)
  - building blocks should be built with AS LITTLE INTER-DEPENDENCY AS POSSIBLE


**comparison**

- In this step, we compare the frameworks of thinking about Solid as a collection of resources exposed over Linked Data Platform, compared to Solid as a Knowledge Graph exposed over a [meta-]model-based interfaces (SPARQL, TPF, ...).

- **What do we need? -> A good example**
  - compare 2 cases -> precise examples
    - store address book in classic solid with LDP
      - if you store this LDP API in file system -> straightforward
      - SPARQL endpoint -> encode document in which this is stored


- **make point that query and API are separate!**
  - suggestion of SPARQL endpoint per resource
  - bring some clarity to this point


**conclusion**


- Viewing a pod as a KG does not solve issues in itself, but provides a thinking framework to think about and solve issues focused more on the data than the interface.

- queries and APIs are separate - important to bring this point forward again

- LDP gives us only a limited innovation surfaces

- API based integration to data integration

- (not for here) resources are not well defined units of data. You can see the whole pod as a single resource (all rdf data).

------------

- It does however provide a more robust framework to think about solving challenges for decentralized data pods
- It enables more functionality and optimization though more workload-specific interfaces (cfr databases over a filesystem)
- This vision builds upon the current implementation without any discrediting of work done, but with the hope of building on the existing specifications and ideas to solve even more challenges.

-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------

**OVERVIEW END**

-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------


- LDP creates problems with resources
  - resources are the unit to which permissions are limited
  - resources form a logical way of bundling data where the semantics of this bundling may not be encapsulated in the data.
  - To other applications, resources are little black boxes with only very limited metadata.

- problem with hierarchy
- granularity
- creating an organizational structure



------------------------

- say A pod is a knowledge graph
- every subject in the KG should be dereferencable
  - dereferencing would result in a Subject page for the dereferenced subject
  - This is identical to just randomly storing data in the root with random names 
  - >> what about data OUTSIDE of your namespace?????
  - advertising a query endpoint???
  
  question
  - do we see a pod as a DATA SOURCE? 
  - e.g. pod is a data source KG, it may expose multiple interfaces over its internal knowledge graph.




-->















-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------

**OVERVIEW -- v3**  

-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------

**intro**
- Solid proposes a new ecosystem, where data and application are separated.
- Solid has goal: **splitting data and apps**
- this has key: **semantics in the data**
- to achieve this ecosystem, they propose a set of interfaces to make this happen
- For read, write and interacting with data, the LDP interface is chosen as a way to organize data on a Solid pod.
- The chosen LDP interface leads to localized application-specific assumptions and structuring of data
- As no authoritative definition is present, the definitions for Solid are shifting from the original vision towards the sum of the used specifications 
- In this paper, we propose a perspective of Solid pods as exposing an internal Knowledge Graph supporting multiple interfaces (such as LDP and SPARQL) over their internal Knowledge Graph.
- Using this perspective, we hope to steer the discussion for solid again towards a framing of Solid pods as a knowledge graph, and how the separation of applications and data can take place in this context.



**problem statement**
- The vision of Solid is splitting application and data, made possible by adding the required semantics to the data.
- We see that the proposed LDP specification leads to a mismatch between the imposed bundling of data in resources and putting the resources in a hierarchy <-> real world: data organization between applications does not always make sense
- We see applications (being required to) create localized assumptions and optimizations in the structuring of their data over the LDP interface, leaving semantics outside of the data.
- this structuring also impacts the granularity and organizational possibility for permissions to be set over this data
- We see this as a consequence of LDP, being an API on the sense of resources, being a meta-API. It puts constraints on the organization of data in resources and hierarchical ordering, but apart from this leaves many degrees of freedom, enough so that every application can structure their data in a way that leads to a specific API over the data based on localized assumptions and optimizations.
- This can lead to problems in discovery, interoperability, through a mismatch of assumptions and expectations in the data organization and because of the lack of agreement.
- We argue that LDP with WAC / ACP is a way to emulate a permissioned knowledge graph, but in the process it incurs application biases through assumptions and optimizations, and leaves open a lot of degrees of freedom in the organization of data. This is a consequence of the choice of interface and not of the vision of Solid pod as a KG.
  
  
  



**perspective**

- Repeat the goal of Solid providing ecosystem where applications and data are separated.
- We propose the perspective of a Solid pod as permissioned knowledge graph. 
- argue this is a goal that has been tried to achieve with LDP but we are getting stuck ... 


- Make sure it stays exemplifying -> 
  - Make point of SPARQL endpoint over the document proposed in paper
  - With this view, we can see the SPARQL endpoint as exposing the RAW data, without requiring the document organization of LDP 
  - Dont go to deep - more of an example


- OH no - what about the API's => Oh no, what about all the local assumptions
  - Solid marks transition from API based integration to data based integration
  - the assumptions are now in the API -> we need to move the assumptions to the data and try to make them specific using semantics -> this is a strong conclusion

- this approach allows us to regard interfaces that are better able to split data and applications, ...7

- **permissions are a proxy for policies / parameters**
  - permissioned -> we can zoom this out to parameterized / policy based

- APIs could be built through modular building blocks as is the case now (LDP, WAC/ACP, Solid-OIDC)
  - building blocks should be built with AS LITTLE INTER-DEPENDENCY AS POSSIBLE





**comparison**

- In this step, we compare the frameworks of thinking about Solid as a collection of resources exposed over Linked Data Platform, compared to Solid as a Knowledge Graph exposed over a [meta-]model-based interfaces (SPARQL, TPF, ...).

- **What do we need? -> A good example**
  - compare 2 cases -> precise examples
    - store address book in classic solid with LDP
      - if you store this LDP API in file system -> straightforward
      - SPARQL endpoint -> encode document in which this is stored


- **make point that query and API are separate!**
  - suggestion of SPARQL endpoint per resource
  - bring some clarity to this point





