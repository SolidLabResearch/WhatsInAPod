## Problem statement # {#problem_statement}
<!-- Solid requires splitting of apps and data through semantics -->
To achieve the envisioned ecosystem of data integration and interoperability, Solid relies on the premise that it is possible to separate applications and data in a meaningful way, so that different applications can work with the same data stored in a Solid pod. The key here is that the semantics of the stored data can help applications to discover the data they need in a pod, and can reuse, adapt and work with this data without requiring the integration of a new interface for every new data source they want to interact with [](cite:cites rubenv_reflections_2021). 

### The LDP interface
<!-- LDP leads to mismatch between the restrictions imposed on how data can be stored, and the real world  -->
As the specification chosen to define the protocol to interact with data stored on a Solid pod, the Linked Data Platform (LDP) specification [](cite:cites presbrey_linked_2014) holds a central role in the current Solid ecosystem in enabling the promise of data interoperability. 
The specification organizes data using the concepts of resources and containers and defining the protocol to create, read, modify and delete these resources and organize them in a hierarchical structure of resources and containers.
The definition of what constitutes these resources is very loose, and they take the form of either RDF resources containing an RDF data graph in an RDF format, or non-RDF resources such as images.

<!-- applications are required to make localized assumptions and optimizations to read and write data on a Solid pod over LDP -->
The LDP interface restricts the way applications can store data by requiring the bundling of data into resources and the organization of these resources in a hierarchical structure. The responsibility of this organization of data lies entirely with the applications.
This situation leads us to the following problems we witness in the current Solid ecosystem:
(i) as the authorization mechanisms for Solid limit the expressiveness of permissions to the granularity of resources and containers, applications indirectly dictate the structure over which the user can control access to this data.
(ii) the imposed hierarchical structure may not conform to real-world requirements for the structuring of data. This may encourage local assumptions in the application to model this data, where these assumptions should be captured in the semantics of the data itself. 
(iii) as the LDP interface leaves a lot of freedom in how data can be written to the pod, and because of the similarities between the LDP interface and a file system, developers are allowed to encode local assumptions and optimizations of the storing of data in the organizational structure of data as can be done on file systems. Where these assumptions do not hold for the rest of the ecosystem, this leads to problems with interoperability or loss of optimizations by this information not being stored in the semantics of the data.

<!-- We see this as a consequence of LDP certain restrictions, but also leaving a lot of degrees of freedom, leaving developers free to use a Solid pod as a remote file system -->
We notice that a common source for the problems stated above can be derived from the Linked Data Platform interface behaving as an interface that applications can us to encode their own interfaces on top through local assumptions and optimizations that are not shared by the rest of the ecosystem.
This makes the core premise of the Solid ecosystem more difficult, as the requirement for separating applications and data is adding sufficient semantic information to the data in the ecosystem so that it becomes interoperable for other applications in the ecosystem.
As the Linked Data Platform specification provides an interface that does not promote these concepts, it limits the innovation surface of the solutions that can be developed for long term sustainability of the ecosystem.
Where Solid can mark the transition from classic ecosystems with applications relying on API-integration to gather data from different sources to a new type of ecosystem where applications focus on integrating data exposed over a variety of different interfaces, made possible by the available semantics present in the data.

### A lack of definition
As the Solid project evolved over time, we start to notice that the lack of an authoritative definition for Solid (that we know of) has had the consequence that the understanding of what Solid has started to shift.
From being initially described as "*a decentralized platform for social Web applications*" [](cite:cites sambra_solid_nodate), over time initiatives within the Solid ecosystem started providing their own definitions as to what Solid is based on their vision of the ecosystem.
On the Solid project (https://solidproject.org/) website, we find that "*Solid is a specification that lets people store their data securely in decentralized data stores called Pods.*".
The Inrupt website (https://inrupt.com/solid/) states that "*Solid is a technology for organizing data, applications, and identities on the web.*".
As these definitions start to diverge in terms of terminology and viewpoint, we fear that the definition of the Solid ecosystem may become more tied to the specifications used to implement its goals and miss the original promise of an interoperable ecosystem for applications and data.


How do I do a full citation style for the part of: the initial description in (sambra et al.)[] . And additionally how do we give the references through footnotes? I heard this cant be done - do i do it inline?
{:.comment data-author="RD"}


<!-- 
----------------------------
OLD STUFF
----------------------------
 -->




<!-- 
Additionally, we notice that the inconsistency in used terminology to the identity of Solid as a platform, technology, specification or protocol. Next to this, from our experience with the tooling and initiatives,
In contrast, the current specifications (WAC, ACP), research [TODO:: find something good here??]() and tooling is all focused on viewing Solid as a Linked Data Platform interface.
[TODO:: we need more content here to prove this point]().

Because of this notion of a Solid POD being equated to the Linked Data Platform interface is exposes, in contrast to viewing this interface as a means to an end to achieve the original goal of splitting applications and data while providing semantics in the data itself, we argue that this current perspective enforces the problems that currently exist with using the Linked Data Platform specification as a base for the Solid ecosystem and limits the potential for innovation and solutions that the Solid ecosystem can bring to the Web.

 -->

<!-- Missing the point: We argue that LDP with WAC / ACP has the goal of creating a developer-friendly approach of presenting developers with a file-system like interface to use data over the Web, with a we'll fix it later attitude. But this leads to developers using this interface just like a file system and missing the point of adding semantics to their data to help the interoperability. -->



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
