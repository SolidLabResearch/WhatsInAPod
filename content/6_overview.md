
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------

## OVERVIEW  

-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------


### intro
- Solid proposed as a data platform using the open Linked Data Platform spec to organize data.
- We see however that the use of the Linked Data Platform specification leads to a lot of ASSUMPTIONS in the organization of data on the pod.
- This leads to difficulties in discovery, querying, semantics? and interoperability of data.
- In this paper, we propose the vision of Solid as a platform of data pods exposing an internal Knowledge Graph supporting multiple interfaces (such as LDP and SPARQL) over their internal Knowledge Graph.

## Problem statement
- We see the use of the Linked Data Platform spec leads to a lot of ASSUMPTIONS in the organization of data on the pod
  
  - Hierarchical nature of the LDP spec (same as filesystem) leads to semantics in the data location through slash semantics 
    - e.g. original paper using slash semantics for event storage based on date
    - Leads to semantic context being stored in the data path (not machine readable)

  - Containers and resources lead to data stored separately (e.g. digita storing data of different applications in different containers, idem as e.g. program files on the filesystem.)
    - This leads to data separation, and implicit context being attributed to storage location (data stored at `/apps/solidbook/` is data from the `solidbook` app.)
    - With the advantage of facilitating permission management for applications
  
  - LDP leads to local assumptions and optimizations for applications(, at the cost of interoperability?).
    - We can see this clearly in the Inrupt Developer Libraries for Solid, where the developer interface only provides functionality to retrieve data for which you know both the location and the used schema, with almost no regard for data discovery.

- LDP is a not a real API (in the same way that a file system is not a real API). It is a meta-api that allows an infinite ways to organize data.
  - In its base form, combined with access controls, it provides little to no functionality for data interoperability.
  - The goal of Linked Data is data integration, where LDP actually still requires a lot of api-integration through assumptions or agreements between applications on certain data organizations (e.g. solid chat in mashlib, ...).


## Vision
- In this paper, we propose the vision of Solid as platform of data pods containing knowledge graphs of individual data quads.
- This as a contrast to the LDP-organization currently used, that organizes data in resources.
- these pods can expose their internal KG over a multitude of interfaces
  - wont this reduce interoperability through not supporting other interfaces?
  - argue currently little to no interoperability without prior agreements on data shape and organization over LDP.
  - original paper includes support for SPARQL for querying -> this goes along with this vision.
- APIs could be built through modular building blocks as is the case now (LDP, WAC/ACP, Solid-OIDC)
  - building blocks should be built with AS LITTLE INTER-DEPENDENCY AS POSSIBLE
- The current implementation of Solid is a specific implementation of this vision that can be expanded upon.
  - As the SPARQL in the original paper does + how Jeroen handles it in the architecture paper, more links???


## Comparison
- In this step, we compare the frameworks of thinking about Solid as a collection of resources exposed over Linked Data Platform, compared to Solid as a Knowledge Graph exposed over a [meta-]model-based interfaces (SPARQL, TPF, ...).


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


## Conclusion
- Viewing a pod as a KG does not magically solve everything.
- It does however provide a more robust framework to think about solving challenges for decentralized data pods
- It enables more functionality and optimization though more workload-specific interfaces (cfr databases over a filesystem)
- This vision builds upon the current implementation without any discrediting of work done, but with the hope of building on the existing specifications and ideas to solve even more challenges.



-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------

## OVERVIEW END 

-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
-----------------------------------------------
