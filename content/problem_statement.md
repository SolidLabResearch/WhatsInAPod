## Problem statement
With the goal of facilitating the integration of data for applications over the Web, 
the Solid protocol defines a set of open standards that can be used to interact with the data stored on a pod [TODO::cite]().
In their proposal paper [TODO:: cite](), a read / write protocol is proposed based on either Linked Data Platform or SPARQL queries. 
The Linked Data Platform specification defines a set of rules of HTTP operations on Web resources, providing a Web interface for interacting with resources stored on the Pod.
The paper proposes extensions to the LDP interface in the form of globbing for combining multiple resources in a container, as well as using HTTP PUT for direct control over resource naming and location.

For data retrieval, the paper argues that LDP cannot express complex data retrieval operations, and they propose leaving complex data retrieval tasks to the server would facilitate application development through an optional possibility of supporting SPARQL queries.

This is in line with the goal of Solid being to move the problem space for applications working with data away from API integration issues, and focus on the data through direct data integration, bypassing the API integration step.



In practice however, we see a fundamental mismatch with usage: We see different apps making local assumptions about how and where to store data on a data pod. We see optimizations that do not hold for the ecosystem [TODO::CITATION]()

The use of LDP as a storage medium creates bias in the data stored because of the influence of slash semantics.
As an example: the main application providing an overview of the data stored in a Solid pod for Inrupt (the inrupt PodBrowser application), stores contacts using an overview resource stored at a set uri at `&lt;pod_uri&gt;/contacts/people.ttl`, from where the individual contacts can be retrieved using link-traversal by following the availabe `vcard:inAddressBook` predicates.

We notice this approach in a lot of applications, where the Linked Data Platform interface used to write data to a Solid Pod requires assumptions on the developer side to provide a working application.
Where to store data on a pod? 
How to format the data that is written?

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
leading to a different kind of API integration, without providing the data-integration that was promised.

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
