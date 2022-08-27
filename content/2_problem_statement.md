## Problem statement # {#problem_statement}
To achieve the envisioned ecosystem of data integration and interoperabiltiy, the Solid project provides a platform based on a set of open standards to manage and interact with data in Personal Online Datastores (POD) [](cite:cites sambra_solid_nodate).

### Solid as Linked Data Platform

The protocol to read, write and organize data on Solid data PODs is based on the Linked Data Platform (LDP) specification [](cite:cites presbrey_linked_2014). 
This specification defines a set of rules for HTTP(S) operations on web resources to provide a read-write architecture for Linked Data on the Web. It provides an organizational structure of resources and containers, much in the same way that a file system is organized through files and directories. These resources can either be non-RDF resources storing regular files, images and more, where RDF resources store a collection of Linked Data Quads in a specified RDF format.

#### A mismatch in data organization
As the Linked Data Platform specification organizes data as containers and resources, it imposes an inherent hierarchical ordering of resources and containers in the same way that files and directories in a file system create a hierarchical ordering.
It requires all (RDF) data to be bundled as resources and stored using the hierarchical structuring of container and resources. 
These organizational constraints provide challenges for applications that need to store data on a Solid pod.


However, real world data will not always be easily mapped to a structure that adheres to these constrainst.
As event-based 

As the specifications of the Solid Platform do not impose any specific limitations on how applications must interact with the Linked Data Platform interface exposed by a Solid data POD, any application (given the permission) is free to organize their data in any way they see fit.


#### Data is bundled into resources
As data needs to be bundeled into resources, 
The concept of a resource does not pose any constraints on its contents. The contents can either be non-rdf, such as images, or it can container any amount of RDF data quads. 



#### LDP as a meta-API
The above problems can be derived from the essence of the Linked Data Platform interface. Where LDP can be described as an API within the scope of working with resources on an LDP server, defining how to read, write add and remove resources over HTTP(S), it should be seen as a **meta-api** from a data-modeling perspective.
The LDP specification can represent data in an infinite amount of ways.
It imposes constraints on the way data can be organized, by requiring data to be bundled in resources and requiring these resources to be organized in a hierarchical structure.
On the other hand, LDP leaves degrees of freedom to where every application can through localized assumptions create their own API on top of the LDP interface.
Through the decisions of how the data should be bundled in resources on the pod, sharing the same permissions for all data bundled in a single resource, and the decisions of the hierarchical structuring of this data on the pod, each application in essence creates their own API on top of the LDP interface of a Solid POD through local assumptions and optimizations in the organization of data.
Additionally, in this paradigm, applications themselves are indirectly responsible for the permissions that can be set on the data in a Solid POD. As applications structure data in resources, and structure the organization of resources on a POD, users are limited in the granularity over which they can give access to data on their pod to the granularity of the resources created by the used applications. Because of the organizational structure, permissions that are shared between a container and all members (child containers and resources) of that container are also limited to the assumptions made by the application structuring the data and may not make sense for other use-cases for the same data.

These consequences go against the vision of Solid providing an ecosystem where data and applications are separated and where API integration is abolished for data integration where applications and services are enabled to directly integrate existing data.

### A need for definition
Where above we posed that the Linked Data Platform specification defines an interface that promotes local assumptions and organizational structures for applications storing data on a Solid POD, we see that the line between Solid and Linked Data Platform has been blurred over time [TODO:: CITATIONS AND EXAMPLES](). 
As no authoritive definition of Solid exists (that we know of), we find that multiple initiatives in the Solid ecosystem provide their own vision on the Solid ecosystem, which over time equates more to the idea of Solid as a Linked Data Platform  set of specifications for an online platform than as a vision for a

In the initial paper, Solid is presented as: "a decentralized platform for social Web applications" 
  
On the website of the Solid project, we find that: "Solid is a specification that lets people store their data securely in decentralized data stores called Pods. Pods are like secure personal web servers for data. When data is stored in someone's Pod, they control which people and applications can access it." [https://solidproject.org/]()

On the Inrupt website [https://inrupt.com/solid/](), Solid is defined as "a technology for organizing data, applications, and identities on the web. Solid enables richer choices for people, organizations and app developers by building on existing web standards."

We notice that where these definitions differ in the identity of Solid as a platform, technology or specification / protocol, we see that there is no specific mention of Linked Data Platform. 
In contrast, the current specifications (WAC, ACP), research [TODO:: find something good here??]() and tooling is all focused on viewing Solid as a Linked Data Platform interface.
[TODO:: we need more content here to prove this point]().

Because of this notion of a Solid POD being equated to the Linked Data Platform interface is exposes, in contrast to viewing this interface as a means to an end to achieve the original goal of splitting applications and data while providing semantics in the data itself, we argue that this current perspective enforces the problems that currently exist with using the Linked Data Platform specification as a base for the Solid ecosystem and limits the potential for innovation and solutions that the Solid ecosystem can bring to the Web.


<!-- 
It puts constraints on the data - resource granularity, hierarchical structuring, but also leaves degrees of freedom used to create additional semantics not captured in the data.
This freedom is used to create API's in the data through local assumptions creating semantics that may not be captured 
However, if we look at the implementation these definitions differ We notice a lack of proper definition for Solid, nor a guideline for used terminology (protocol, platform, ecosystem, ...).in the data itself.
Little support for interoperability in its base form.

#### Resources are organized in a hierarchical structure using containers.
This hierarchical structure 


#### Resources do not impose any structure on data



In this bundling of data in resources and organizing these resources in a hierarchical structure, we see a mismatch with how 

In this bundling of data in resources

In this hierarchical structuring of data, we see a mismatch with the structuring of real-world data.
As applications 
As data must be collected in resources and placed in a hiera
 -->


<!-- 


-----------------

### Solid as a Linked Data Platform interface

LDP as a meta-API where applications are able to model their data needs.
It puts constraints on the data - resource granularity, hierarchical structuring, but also leaves degrees of freedom used to create additional semantics not captured in the data.
This freedom is used to create API's in the data through local assumptions creating semantics that may not be captured 
However, if we look at the implementation these definitions differ We notice a lack of proper definition for Solid, nor a guideline for used terminology (protocol, platform, ecosystem, ...).in the data itself.
Little support for interoperability in its base form.

#### A mismatch between data organization and the real world
is often caused by the Linked Data Platform interface being restrictive in the way data can be organized over the interface.
The Linked Data Platform specification organizes data in a hierarchical structure, where real-world data does not always follow a hierarchical structure.



#### Semantics in data organization
in applications and 


#### Localized assumptions and optimizations
made by applications in the structure of data stored on a data pod leads to ...

#### Applications indirectly dictate the permission structure
in their structuring of data on the data pod.
As applications structure data stored on the data pod, 
the resulting data organization on the pod dictates how permissions can be set over this data.
As the data is structured in resources using the hierarchical structuring of the Linked Data Platform interface,
permission granularity over this data is limited to the size of the chosen resources, and not on individual data triples in these resources (in case of RDF resources).
Additionally, interactions with this data is limited to the structuring of these resources, as [TODO:: what more should we put here??]().
 -->




<!-- 


--------------------------------------------

#### Data granularity
A consequence of using this specification is that data must be organized in resources, as this is the only form of data that can be managed using Linked Data Platform. This requires applications to make local assumptions as to what constitutes a resource and how application data should be distributed over resources in a data pod. As resources are the only interface, other data structures such as databases are impossible, and must be emulated on the client side over the resources exposed by the LDP interface.

#### Organizational semantics
As resources are stored in a hierarchical way due to the nature of the Linked Data Platform specification, the organization of data in a hierarchical order may carry implicit semantics in the organization of resources on a data pod. We see this return in the original paper[](cite:cites sambra_solid_nodate), where the example is given of an application storing events using a URI path structure based on dates (i.e., /2016/05/01/event1). The problem with these localized assumptions is they do not hold for the ecosystem, and form an application specific API built on Linked Data Platform [TODO:: what more?]().

#### Hierarchical bias
The hierarchical organization of data on a pod also leads to data separation between applications. We see this with e.g. Digita [TODO::source]() providing a separate container for each app, in the same way that the `Program Files` folder provides a location for applications to store data. While this mitigates issues of overwriting data, and adds implicit context to data based on its location (at least for the application managing a certain data space), this comes at the cost of data discovery and integration [TODO:: what more?]().

#### LDP as a meta-API
We argue that the Linked Data Platform interface is not an API, but a meta-API that can organize data in an infinite amount of ways. In the current environment, applications are forced to make local assumptions, and create application-specific API's on the Solid data pods through localized assumptions that do not hold for the ecosystem. This comes at the cost of data discovery and interoperability with different applications that do not share the same assumptions.

### API-integration versus data-integration

As the goal for interoperability of online data spaces is to move from the paradigm of API integration to mode data integration centered approaches of data publishing, we see that Linked Data Platform in it's current state creates API integration issues for applications through localized assumptions in data organization and format / shape [TODO:: maybe also make the point of format / shape integration a bit more]().



The original paper proposes a solution for data discovery through providing a SPARQL interface that runs on top of the data organized in the Linked Data Platform, where every resource serves as its own SPARQL endpoint (https://github.com/nodeSolidServer/node-solid-server/issues/962) which has since been removed from the spec -> this was no solution after all so maybe this should be casually mentioned as a sidenote?
 -->


<!-- 

As a consequence of these decisions, using the Linked Data Platform interface, reading this contact data requires the knowledge of where the data is stored, and the formatting in which the data is stored to work with the data.

As a consequence of using LDP for the organization of resources on a data pod, the main discovery mechanism over this interface is link traversal through the LDP interface.
This is however a limited approach, as in case an agent tries to retrieve information stored in a public resource at at `&lt;pod_uri&gt;/private/public`, where the parent container `&lt;pod_uri&gt;/private/` is set to be private, the resource cannot be discovered unless the exact URI can be discovered through another means.

In their "extensions to LDP" part of the paper, they propose the "PUT" extension to LDP, with the example of a calendar application
that uses a URI path structure based on dates (i.e., /2016/05/01/event1). A PUT request is to create a new resource called event1,
as well as the missing month (i.e., 05) and day (i.e., 01) containers under /2016.
Here we see again the reliance on the LDP bias (using the slash semantics as semantic information over the stored data instead of explicitly tagging the data with the information), that leads to assumptions being required to discover the data.

The complex data retrieval proposed through SPARQL mentions that optionally a SPARQL endpoint can be provided on a data pod, enabling more complex data queries from a pod, where rdf-resources and metadata for non-rdf resources can be exposed over the interface.
This is to address shortcomings in the LDP interface of not being able to express complex data retrieval operations such as filtering and aggregation. Also proposed here is that pod servers may be responsible for evaluating queries spanning multiple pods by forwarding requests for additional data to other pod servers.

In their related work, it states:
Solid has a strong focus on decoupling data from
applications and in addition ensuring that applications have a simple, generic
and well defined way to access the data stored in the users’ pods.




In Section 5, the paper presents the POD Management system. It defines that pods use LDP to organize data in containers that group resources with every resource and container having their own URI. A pod server should support 
- LDP
- patching (N3-patch, former SPARQL update)
- access control lists (ACL), potentially to be updated to access control policies (ACP).
- live updates
- optionally SPARQL

They advise storage mechanisms for RDF data to use triple stores to facilitate querying.

From all this information, we infer that their approach is focused on data discovery and querying happening mainly over a SPARQL interface that has a full index of all data that is available to the agent querying over the pod and can fulfill these requirements on the server side.



### LDP as an API
Additionally, we also argue that LDP is not an API: it’s a meta-API. 
There are still an infinite amount of ways to expose knowledge over LDP. 
We notice existing work and apps get this wrong[TODO::cite]().


Because of this, we see that the promise of Solid moving the equation from API-integration to data-integration does not hold.
As LDP cannot be viewed as a simple API, the problem of integrating different API's to access data from different sources 
has been translated into requiring knowledge of different writing / storage methods to access data stored on different pods by different applications,
leading to a different kind of API integration, without providing the data-integration that was promised. -->

<!-- 


------------------------------------------------------------------




A disconnect exists between the practical notion of a Pod and the protocol that provides access to its data, creating confusion as to what exactly a Pod is and how it relates to the technical specifications.

- LDP creates biases in the stored data?
- data integration issues w LDP?


- spec updates evolved the understanding of Solid pods
- the technical specifications put limits on the way data can be interacted with
- to attain the goal of replacing the API integration with data integration, have to work around the limitations of LDP or build alternative interfaces on top.




The current state of LDP makes us think of pods as collections of Linked Data Documents

We see a fundamental mismatch with usage.
We see different apps making local assumptions and optimizations that do not hold for the ecosystem and essentially because of ACL reasons

LDP creates a BIAS in the stored data? e.g. data has to be grouped at a certain location in a resource?
Also the notion that LDP is not an API. It’s a meta-API; there are still infinity ways to expose knowledge through LDP. So existing work and apps get this wrong.

-> The promise of data integration instead of API integration is not satisfied? - This was a point we came up with, however this can be (kinda) solved in the tooling used so ?
-> ...

The Mansouroriginal Solid paper already alluded to shortcomings of the LDP interface (globbing, a separate SPARQL interface for RDF data / metadata)
-> And we will make the argument / take the position that it is more fundamental, that LDP is the problem/limitation rather than the solution. We reframe by seeing one LDP API (there are multiple!) as a possible view on the Pod, which fundamentally is a KG. 

-->
