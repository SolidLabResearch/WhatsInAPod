

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














<!-- 
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

 -->






**Questions::**

ch02.


(i) There is no single way to organize data in a hierarchy. 

-> granted data can be organized in infinite # ways over a hierarchy.
My question is: are we organizing data as a hierarchy, or as a graph?
data can inter-reference between resources.
you can query the pod by extracting ALL available RDF data and converting it in graph representation, you don't have to but you kinda can.

What data / semantics are ACTUALLY lost here? A good example?
what semantics are often encoded by an application in the LDP hierarchy?

THe point we need to be able to make here is to say that THERE IS NO GOOD WAY to convert this hierarchical structure to 

Can we make the point that LDP inhibits the inclusion of Semantic information in the pod data graph, as they remain stuck in the interface / application logic.


Optimizations encode semantic meaning over the interface? -> 
shape trees and type index also encode this in the data graph itself


pod is a Knowledge Graph
Addressable subjects (e.g. those within the namespace of your pod) are abstracted as resources.
these resources contain a sub-knowledge graph.

What is exactly the point we are making

LDP wordt fout gebruikt door developers?

en LDP leid tot problemen met de opsplitsing in resource?

permissioned KNowledge Graph -> mismatch very difficult to make without duplication -> no synchronization





Version 4:
----------------------------------

**Intro: Solid vision**







**Solid pod as an LDP hierarchy of Linked Data Documents**

argumentations:

- Problem in the permission structure of LDP 
  - application bias leads to permission granularity and assumption mismatch

- Problem in optimizations:
  - optimizations are currently done in hierarchy of data instead of in semantics
    - **We can make the point that this is not a problem, as it does not change the data per se for other applications and does not per se make it worse?**
    - **not even sure we can make this point**


I think in the current 





I think we might need to rescope the vision of the What's in a pod paper from the notion of 

- Solid envisioned ecosystem
  - goal: separation of apps and data
  - key: semantics in our data
  - enables: data integration instead of interface integration

- Mismatch between LDP interface and Solid vision
  1. world is not a hierarchy - no single way to organize in a hierarchy
     - *counter argument: LDP hierarchy does not inherently influence the KG of the data pod? the resulting KG will still be the same as the original graph even distributed over resources?*
  2. different apps might disagree - hierarchy might mismatch
     - *counter argument: LDP *
  3. reason for differences: mismatch in assumptions in structuring data in resources w.r.t. permissions
     - very valid point
  4. reason for differences: local optimizations through assumptions in app and interface for query.
     - *counter argument: again these do not appear in the KG created of the LDP interface.  *

  Main problem I have with this point is that we equate LDP with the vision that some applications have of LDP as Linked Data Documents.
  If you have the vision of we should work with the LDP data as a KG, these problems disappear -> is this really a mismatch in interface? or is this a mismatch in understanding?


- 


what we need


- Intro: Solid envisioned ecosystem
  - goal: separation of apps and data
  - key: semantics in our data
  - enables: data integration instead of interface integration

- Solid as LDP hierarchy of Linked Data Documents
  - cause: 
    - lack of understanding of the ecosystem. 
    - lack of definition provided by ecosystem.
    - lack of tooling that guides developers to the envisioned ecosystem
  - consequence: 
    - assumptions in applications and interface
    - no interoperability
    - no understanding for the view of EXTRA semantic enrichment for data, they could as well be writing JSON because of lack of vision

- Solid as LDP hierarchy that can be interpreted as Knowledge graph
  - You can view the LDP hierarchy as a knowledge graph with resources as subgraphs / you can yeet all resources together as a KG.
  - Make the point viewing the resources in the LDP hierarchy of Solid pod as a KG -> we solve A LOT of interop problems.
    - hierarchical mismatches? -> no problem its a graph
    - different apps different organization -> no problem the resulting graph should be same if data is same
    - ...
  - BUT: We run into some leftover semantic difficulties: is interface part of the KG? 
    - The timestamp for resources for example can be important - this is encoded in the interface
    - The problem of knowing where to look to update / remove a statement in the pod knowledge graph requires keeping context of where statements are being made - consequence of the interface
  - LDP requires additional support for optimization (shape trees / type index), that EITHER have to be handled server side, or its client side but you cannot really trust the results as not all applications may maintain these indexes?
  - Additionally, we still have the massive issue of a mismatch (here we can use it I think) in the handling of permissions. 

- Solid as a Knowledge Graph
  - this is the final viewpoint we converge at
  - We notice that the viewpoint of Solid as LDP hierarchy that can be interpreted as Knowledge graph solves a lot of problems
  - We notice that leftover problems are not really interoperability (can we say this?) - but are mainly question of leftover semantics of the interface + the BIG issue of permissions.
  - We notice that optimization surface of LDP is limited: either adapt the interface, or rely on applications or you have to make your own optimizations - Even original paper brought these issues forward.
  - Because of all this, final viewpoint is that in eventuality, the ecosystem should converge to the notion of a Solid pod being permissioned knowledge graph that can support any kind of Web APIs (, and should not rely too heavy on LDP as centerpiece? - did we make this point enough?)

- Conclusion
  - ...






What are the points we want to bring:


**Intro**

The Web is not made for interoperability.
Solid promises ecosystem of data privacy and application interoperability.

what are the key drivers behind such an ecosystem.

**The current state**
To achieve this vision, Solid proposes the use of a set of specifications to create this envisioned ecosystem of interoperability. 








A pod is a way to manage identities and data on the Web.