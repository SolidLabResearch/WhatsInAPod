## A Solid pod as an LDP interface # {#problem_statement}
<!-- Solid requires splitting of apps and data through semantics -->
To achieve the envisioned ecosystem of data integration and interoperability, 
Solid relies on the premise that it is possible to separate applications and data in a meaningful way, 
so that different applications can be interoperable through the semantics stored in the data. 
To achieve this envisioned ecosystem, the Solid project has chosen for the Linked Data Platform (LDP) specification [](cite:cites presbrey_linked_2014) specification to define the protocol of how applications can interact with data on a Solid pod. 
This specification defines a platform that organizes data using the concepts of resources and containers, similar to how a file system defines a platform that organizes data using files and directories.
It also defines the protocol to create, read, modify and delete these resources and organize them in the hierarchical structure of resources and containers.
Similar to files on a file system, the definition of what constitutes these resources is very loose and generally take the form of either a resource containing a set of statements in RDF (RDF resource) and other resources that do not contain RDF such as images (non-RDF resources).

### A mismatch between LDP and the envisioned ecosystem
<!-- LDP leads to mismatch between the restrictions imposed on how data can be stored, and the real world  -->
Where LDP has the appearance of a simple interface to make data interoperable over the Web using HTTP(S) protocols, 
it leads to a mismatch with the envisioned ecosystem in the way it restricts the way data can be stored over the interface, 
as well as in the degrees of freedom it leaves open for applications to encode semantic information in the application logic and the interface.

<!-- mismatch -->
We can define four points where we see a clear mismatch in the context of two simple applications: a *contact list application* and a *birthday list application*, that are built on top of the Solid ecosystem where pods expose their data using LDP:

<!-- orgization -->
(i) There is no single way to organize data in a hierarchy. 
Data graphs can be modeled in an infinite amount of ways using LDP, by distributing a data graph over different resources and by structuring these resources in different ways over the LDP hierarchy. 
In our example, the contact list application can encode their contacts as separate resources for each contact in its data graph, after which it adds these resources in the LDP hierarchy. 
In this hierarchy, the birthday list application has no option but traversing the entire LDP hierarchy to look for contact data, 
as the data can be stored anywhere and is entirely dictated by the logic in the contact application and the LDP hierarchy.

<!-- mismatch in hierarchy -->
(ii) Different application can disagree in how the same data should be organized in the hierarchy.
Where the contact list application and the birthday list application work on the same data, 
the applications may have different assumptions on how this data should be organized.
The contact list application may assume that contact data should be organized as separate resources, 
where for each contact extra information such as birth dates is stored in an separate extra resource.
In contrast, our birthday list application assumes all contact information should be stored in a single resource.
Because of these assumptions the birthday list application may decide, after navigating the entire LDP hierarchy,
that the contact information it found just does not include birth date information.
In this example, because of the mismatch in assumptions between the applications, data interoperability cannot not achieved.

<!-- hierarchy for permission -->
(iii) In the current Solid ecosystem, the permission structure is linked to the data granularity and hierarchy.
The current Solid ecosystem has two specifications that can be used to manage authorization of data on a Solid pod.
There are two specifications that can be used to manage permissions on a Solid pod: the Web Access Controls specification (WAC) [](cite:cites WAC) and the Access Control Policy (ACP) [](cite:cites ACP) specification.
Both specifications limit the granularity with which permissions can be set on data to individual resources.
In the LDP hierarchy, this means that applications and the pod owner are limited in how they can set permissions over their data
by the structuring chosen by the application writing the data to the Solid pod.
In our example, the contact application may decide to separate all information of each contact as separate resources.
This way, the application and the pod owner can have very fine-grained control over the permissions set over the data.
The birthday list application is not that concerned with this, and decides to just write a single resource for every contact it has.
We see that even more assumptions may break here, as even with access to the contact, the birthday list application may assume it has access to the contact birth date, which may not be the case.
Additionally, the contact information may assume it is sharing only partial information by sharing a contact, while this data was actually written by the birthday list application that just dumps all contact information in a single resource!
In this example, we see how the authorization mechanisms in the Solid ecosystems make problems worse as even more assumptions need to be made in applications.

<!-- hierarchy for optimization -->
(iv) Finally, applications may choose to make local assumptions for optimization purposes.
As the contact list application may want to prepare itself in case a users adds thousands of contacts, 
the application may optimize the way it stores is data on a Solid pod to improve queries for data.
The application may create a *contacts* container, in which creates resources for every letter of the alphabet, 
in which it stores all contact data of contacts whose name property begins with that letter of the alphabet.
In contrast, the birthday list application may create a separate hierarchy for each month of the year, 
over which it stores its resources.
Where both applications try to optimize queries for their application,
their structuring of the data become incompatible and may actively make queries for other applications worse than when just writing all data to a single resource,
because the assumptions that the applications take in their optimization of the structuring of the data that they query do not hold for all applications in the Solid ecosystem.


<!-- We see this as a consequence of LDP certain restrictions, but also leaving a lot of degrees of freedom, leaving developers free to use a Solid pod as a remote file system -->
The common source of these problems can be found in applications using the the LDP interface of a Solid pod to encode their own interface through the structuring of their data on the Solid pod.
In these instances, applications are not really using LDP as an interface, but as a tool to define their own views on their data on the Solid pod.
By encoding these local assumptions and optimizations in the application logic and the LDP interface, 
the resulting data often lacks the required semantic information to be interoperable for applications in the ecosystem.
In this way, the LDP interface of a Solid Pod limits the innovation surface of the ecosystem, as in many cases it fails to get the assumptions encoded in the application logic and the LDP interface as semantic information in the data stored on the Solid pod.

We find that the optimizations done by applications to solve problems in the LDP hierarchy they work with, 
lead to solutions that are either localized in the application logic and LDP interface, 
or lead to solutions based on encoding more semantic information in the LDP interface, 
such as agreeing to store contact information in the */contacts/*  container, 
that miss the long term goals for the Solid ecosystem.


<!-- 
----------------------------
OLD STUFF
----------------------------
 -->


<!-- applications are required to make localized assumptions and optimizations to read and write data on a Solid pod over LDP -->
<!-- The LDP interface restricts the way applications can store data by requiring the bundling of data into resources and the organization of these resources in a hierarchical structure. The responsibility of this organization of data lies entirely with the applications.
This situation leads us to the following problems we witness in the current Solid ecosystem:
(i) as the authorization mechanisms for Solid limit the expressiveness of permissions to the granularity of resources and containers, applications indirectly dictate the structure over which the user can control access to this data.
(ii) the imposed hierarchical structure may not conform to real-world requirements for the structuring of data. This may encourage local assumptions in the application to model this data, where these assumptions should be captured in the semantics of the data itself. 
(iii) as the LDP interface leaves a lot of freedom in how data can be written to the pod, and because of the similarities between the LDP interface and a file system, developers are allowed to encode local assumptions and optimizations of the storing of data in the organizational structure of data as can be done on file systems. Where these assumptions do not hold for the rest of the ecosystem, this leads to problems with interoperability or loss of optimizations by this information not being stored in the semantics of the data.

 -->


<!-- 
### A lack of definition
As the Solid project evolved over time, we start to notice that the lack of an authoritative definition for Solid (that we know of) has had the consequence that the understanding of what Solid has started to shift.
From being initially described as "*a decentralized platform for social Web applications*" [](cite:cites sambra_solid_nodate), over time initiatives within the Solid ecosystem started providing their own definitions as to what Solid is based on their vision of the ecosystem.
On the Solid project (https://solidproject.org/) website, we find that "*Solid is a specification that lets people store their data securely in decentralized data stores called Pods.*".
The Inrupt website (https://inrupt.com/solid/) states that "*Solid is a technology for organizing data, applications, and identities on the web.*".
As these definitions start to diverge in terms of terminology and viewpoint, we fear that the definition of the Solid ecosystem may become more tied to the specifications used to implement its goals and miss the original promise of an interoperable ecosystem for applications and data.


How do I do a full citation style for the part of: the initial description in (sambra et al.)[] . And additionally how do we give the references through footnotes? I heard this cant be done - do i do it inline?
{:.comment data-author="RD"} -->





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
- access control lists (ACL), potentially to be updated to access control policy(ACP).
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
