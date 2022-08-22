## Introduction
{:#introduction}
In 2016, Solid was introduced to the world as [a decentralized platform for Social Web, based on RDF and Semantic Web technologies](cite:cites sambra_solid_nodate).
Using these existing Web standards, the Solid platform aims to provide an ecosystem that facilitates the development of social applications, where user data is accessible over the Web under the governance of an access control mechanism. 
Users can store their data in online storage spaces called a "pod" (for personal online datastore), where they can manage and share their personal data over the Web.

As the user data is made available over the Web using open standards as an interface, Solid [provides applications with interoperability at the data level instead of the API level](cite:cites sambra_solid_nodate), where instead of having to integrate different APIs per platform to reuse data, now personal data from multiple applications are combined in the user data pod to create a personal knowledge graph where data can be added and queried by applications.

However, application interoperability requires the platform to provide the functionality required to make it possible for applications to make use of the available data and for all actors in the network to agree on the set of standards that make the interoperability possible.

At this point, we see how the decisions of the specifications that define the Solid pod constrain the possible interactions.


The original Solid paper introduced Solid as a decentralized platform for social Web applications.


The notion of a Solid pod has become intertwined with the practical implementation. In the original paper, the concept of LDP was introduced as a "Read-write interface" for a pod, but no specification of that 
















In [](#ldp) we go over the current state of the Solid specifications, after which we propose a wider definition in [](#kg).
[](#comparison) we provide an overview of the the two approaches.




Solid was introduced in 2016 by sir Tim BL as a data platform w. 

cite
{:.todo}

Solid is defined on the [solidproject website](cite:cites solidproject) as 
_"a specification that lets people store their data securely in decentralized data stores called Pods. Pods are like secure personal web servers for your data."_
with further specification that 
_"Any kind of information can be stored in a Solid Pod. You control access to the data in your Pod. You decide what data to share and with whom. Furthermore, you can revoke access at any time. To store and access data in your Pod, applications use standard, open, and interoperable data formats and protocols."_

This definition shows us that the definition of what constitutes a "data pod" is very openended. 






[_"In Solid, the pod servers are application-agnostic, so that new applications can be developed without having to modify the servers. For example, even though LDP 1.0 contains nothing specific to ”social”, many of the Social Web Working Group User Stories can be implemented in Solid, using only LDP and application logic, with no need to change code on the server."_](cite:cites sambra_solid_nodate)

