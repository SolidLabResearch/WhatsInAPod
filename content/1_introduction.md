## Introduction # {#introduction}
In the current state of the Web, companies gather and store large amounts of data on centralized locations, inaccessible for the public and other companies. 
The concepts of data control and privacy have since lost a lot of meaning, as user data is scattered over these centralized data silos with little to no opportunity for users to reuse this data.
<!-- The Solid Proposal --> 
Through the Solid project, Sir Tim Berners Lee, the inventor of the World Wide Web, has aimed to revitalize these concepts of identity and data ownership and privacy for the Web [](cite:cites Solid).
Proposed in 2016 as a decentralized platform for social Web applications [](cite:cites sambra_solid_nodate), Solid defines the concept of personal online datastores (pod) as online data spaces that enable the storage and management of personal data over the Web, where users control the permissions for applications and agents to interact with their data pod.
<!-- Permissions and splitting apps and data -->
To create such an ecosystem of a decentralized network of data pods over the Web, 
the concept of separation of data and application is an important premise.
<!-- Semantics are key -->
Where historically applications can rely on implicit assumptions in the structuring, context and other semantics of data, in the context of online data stores shared by applications and users, assumptions that do not hold for the ecosystem are broken and must be captured in the semantics of the data.
These semantics form the basis for interoperability of data between applications, as these semantics can be interpreted by other applications to reuse this existing data, where prior local assumptions required for the processing of this data may have prevented this.

<!-- Solid as a set of interfaces -->
To achieve these goals, Solid is based on a set of specifications that define the protocol to interact with Solid data pods on the Web.
These interfaces define how to add, read and remove resources data on a Solid pod, how to authenticate and how to set permissions for data on your pod for agents and applications on the network.
<!-- Especially the LDP interface -->
To interface with the data stored on a Solid pod, the Linked Data Platform (LDP) specification [TODO::cite]() is used. 
The LDP specification proposes an organizational scheme where data is bundled into resources.
These resources are then organized in a hierarchical structure of resources and containers on the data pod.

<!-- That lead to application bias in the data -->
As this organization of data in resources and the organization of these resources on the Solid pod is currently done by application, the local assumptions and optimizations made by applications in this organizational structure that is not shared by the ecosystem leads to 
difficulty

<!-- Made worse by lack of authoritative definition -->
Next to this, we also notice a lack of an authoritative definition for Solid. 
As the solid ecosystem expands through new initiatives and industry attention is starting to pick up, the lack of an authoritative definition for Solid is starting to show as new initiatives, as the definition shifts more from the original vision towards an understanding of Solid as a sum of the currently used specifications to achieve this vision.



<!-- We propose a new perspective -->
With this work, we propose the perspective of viewing a Solid pod as a permissioned knowledge graph that can be exposed over the Web using a multitude of interfaces.
We argue that the organizational structure that the Linked Data Platform specification imposes on the Solid ecosystem through its constraints and degrees of freedom for applications to structure their data, separation of application and data and hence data interoperability is limited.
<!-- With hopes of steering discussion to original vision -->
- Using this work, we hope to steer the discussion over Solid towards the goals of separating application and data through use of semantics in the stored data with the perspective of Solid pods as permissioned knowledge graphs that can be exposed over the Web using a multitude of interfaces.

<!-- Sections -->
In [](#problem_statement), we define how a mismatch in organization and real-world structure of data can lead to problems through local assumptions and optimizations by applications.
[](#vision) shows the proposed perspective of viewing Solid data pods as permissioned knowledge graphs that can be exposed over a multitude of APIs.
In [](#comparison), we argue through comparisons of specific use-cases how interfaces influence the organization and structure of the data, and can lead to coupling between application and data through localized assumptions, after which a conclusion is formulated in [](#conclusion).












<!-- 



The goal of the Solid platform is to present a platform that separates applications and data, creating an ecosystem where multiple applications can seamlessly work with the same data [TODO::cite from somewhere? ask Ruben V?]().
For such an ecosystem to exist, the concept of separation of data and application is an important premise.
Through the separation of data and application, implicit assumptions between application and data are broken and must be captured in the semantics of the data.
These semantics then form the basis of the interoperability of this data between applications, as other applications may now use these semantics to make sense of and reuse existing data, where prior local assumptions by applications may have prevented this.

The Solid project provides a platform based on a set of open standards to manage and interact with data in a Personal Online Datastore (POD) [](cite:cites sambra_solid_nodate).
With the goal of facilitating the integration of data for applications over the Web, 
through giving individuals control over this data through deciding access rights and choosing the applications and services allowed to interact with this data, 
new paradigms are needed.

However, as the specifications evolved, we see an evolution in direction of Solid being equated to the specifications used to implement the vision, as opposed to the original vision of a next step for the Web to provide separation between data and applications. -->

<!-- A definition for Solid -->

<!-- ### Separating data and applications
To achieve an ecosystem where different applications can work with the same data, the separation between the data and the applications / services working with the data is an important premise. -->

<!-- ### Semantics and data
A key enabler of this separation is the use of RDF and the adding of semantics to data.
The semantic Web was introduced as an extension to the Web to make data machine-readable [](cite:cites BERNERS-LEE_HENDLER_LASSILA_2001).
Two decades later, the standards introduced are more relevant than ever in the goal to creating ecosystems that enable data integration and interoperability for applications.
Where large portions of the semantics of currently available data over the web are  historically stored in documentation of APIs scattered over the internet, semantics in data allow the expressiveness of storing these semantics in the data itself. Instead of requiring to read the documentation of a data source to know that `api.com/users/1234/contacs/` results in a JSON list of contacts for user 1234, the Relational Data Format (RDF) enables us to write these semantics in the data itself, where `</users/1234/> foaf:knows </users/1235>`. Irrespective of the interface exposing this data, the relation between both users can be discovered from the semantics in the data without requiring specific understanding of how the data was retrieved and the implicit semantics that were captured in the exposing API.
 -->




<!-- 
1. werkt dereferencability nog?
2. persistent URIs
3. openlijk toegeven dat het een discussion document is

bezwaren par heijs - wat doe je met blank nodes?
blank nodes -> resource | is vrij contained
blank nodes -> graph | goed weten wat ermee bedoeld wordt - scoping van KG - belangrijk voor updates 

5. contradicting data

framen als discussion

wat als - perspective
 -->
