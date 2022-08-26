## Introduction # {#introduction}
In the current state of the Web of large platforms storing enormous amounts of data in their own data silos, 
the Solid project brings a revitalization of the concepts of data ownership and identity on the Web.
Proposed in 2016 as a decentralized platform for social Web applications [](cite:cites sambra_solid_nodate), 
[TODO:: more]()

As the specifications evolved over the years, the definitions on what Solid actually is have evolved as well.

The use of the Linked Data Platform specification as the interface to interact with the data stored on a Solid pod ...

The current Web has come a long way from it's initial vision.
Originally designed as a decentralized network of computers serving and retrieving data form and to the network, 
data has become more centralized as data traffic converged to centralized platforms that span billions of accounts.

As a response to this, the Solid project was introduced by sir. Tim Berners Lee, the inventor of the original Web[TODO:: this is a weak intro]().
Solid was presented as a data platform enabling a decentralized Web of personal online datastores(PODs)
by building on existing web standards [TODO:: cite]().
The Linked Data Platform specification was chosen as a way to organize data on a data pod.
[TODO:: write some good flavour text above. Maybe yoink some from other papers]()

<!-- 
We see that in the current state, the specification has started to define the platform, where the use of Linked Data Platform to organize data on a data pod leads to local assumptions being made in applications on how data organization in a data pod should be handled.

In this work, we propose the vision of Solid as a platform of data pods containing an internal Knowledge Graph that can expose this knowledge graph over a multitude of interfaces. 
-->


The goal of the Solid platform is to present a platform that separates applications and data, creating an ecosystem where multiple applications can seamlessly work with the same data [TODO::cite from somewhere? ask Ruben V?]().

However, as the specifications evolved, we see an evolution in direction of Solid being equated to the specifications used to implement the vision, as opposed to the original vision of a next step for the Web to provide separation between data and applications.

Next to this, we also notice a lack of an authoritative definition for Solid. 

This lack of a proper definition, combined with the evolution of the implementation of Solid, has as a consequence that people start to equate their definitions and expectations of the Solid platform and ecosystems to the implementations, [more than on the original vision of what Solid can do for the Web. TODO:: ...?]()

### What is Solid

The Solid project provides a platform based on a set of open standards to manage and interact with data in a Personal Online Datastore (POD) [](cite:cites sambra_solid_nodate).
With the goal of facilitating the integration of data for applications over the Web, 
through giving individuals control over this data through deciding access rights and choosing the applications and services allowed to interact with this data, 
new paradigms are needed.

### Separating data and applications
To achieve an ecosystem where different applications can work with the same data, the separation between the data and the applications / services working with the data is an important premise.

### Semantics and data
A key enabler of this separation is the use of RDF and the adding of semantics to data.
The semantic Web was introduced as an extension to the Web to make data machine-readable [](cite:cites BERNERS-LEE_HENDLER_LASSILA_2001).
Two decades later, the standards introduced are more relevant than ever in the goal to creating ecosystems that enable data integration and interoperability for applications.
Where large portions of the semantics of currently available data over the web are  historically stored in documentation of APIs scattered over the internet, semantics in data allow the expressiveness of storing these semantics in the data itself. Instead of requiring to read the documentation of a data source to know that `api.com/users/1234/contacs/` results in a JSON list of contacts for user 1234, the Relational Data Format (RDF) enables us to write these semantics in the data itself, where `</users/1234/> foaf:knows </users/1235>`. Irrespective of the interface exposing this data, the relation between both users can be discovered from the semantics in the data without requiring specific understanding of how the data was retrieved and the implicit semantics that were captured in the exposing API.




In [](#problem_statement), we define how a mismatch in organization and real-world structure of data can lead to problems through local assumptions and optimizations by applications.
[](#vision) shows the proposed perspective of viewing Solid data pods as permissioned knowledge graphs that can be exposed over a multitude of APIs.
In [](#comparison), we argue through comparisons of specific use-cases how interfaces influence the organization and structure of the data, and can lead to coupling between application and data through localized assumptions, after which a conclusion is formulated in [](#conclusion).



