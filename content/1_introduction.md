## The Solid vision # {#introduction}
In the current ecosystem of the Web where data is mainly stored in centralized data silos exposed over APIs, applications are reliant on integrating various interfaces to work with the data available on the Web.
<!-- The Solid Proposal --> 
With the Solid project, Sir Tim Berners-Lee, the inventor of the World Wide Web, has aimed to revitalize the Web by proposing an ecosystem where applications and data are made interoperable through semantics, and where the concepts of identity, data ownership and privacy for the Web are central.
Solid was proposed in 2016 as a decentralized platform for social Web applications [](cite:cites sambra_solid_nodate).
It defines the concept of personal online datastores (pod) as online data spaces that enable the storage and management of personal data over the Web, 
creating an ecosystem promoting interoperability between applications and user data stored on these Solid pods, 
where users are in control of how their data is shared on the Web.
<!-- Permissions and splitting apps and data -->
To create such an ecosystem,
the concept of separation of data and application is an important premise.
<!-- Semantics are key -->
Historically the semantics of data have often been tied to the assumptions made in applications or interfaces. 
Applications rely on assumptions such as events are stored in the *events* directory, to the point that if this data is moved to the *important_events*, the application may not work or not find the data.
Similarly, interfaces can carry semantics that when you query an endpoint *events*, you will retrieve event information in a specific format defined by the interface as described by the documentation.
By moving these semantics away from the applications and interfaces and capturing them in the data itself,
interoperability no longer requires integrating these assumptions in the application logic and the application can work directly with the data.

<!-- Solid as a set of interfaces -->
To create such an ecosystem, Solid is based on a set of specifications that define how users and applications can interact with Solid pods on the Web.
For the core requirements of authentication, authorization, data access and more, these specifications express the implementation of these core concepts of the vision for the ecosystem.
<!-- Especially the LDP interface -->
To interface with the data stored on a Solid pod, the Linked Data Platform (LDP) specification [](cite:cites presbrey_linked_2014) was chosen. 
The LDP specification dictates an organizational scheme where data is bundled into resources and these resources are then organized in a hierarchical structure of resources and containers on the data pod.
It then provides an interface that can be used to interact with these resources over the Web.
This provides a similar interface to how file systems organize data as files in a hierarchical ordering of files and directories.

<!-- That lead to application bias in the data -->
The use of LDP as the interface for applications to interact with the data stored on a Solid pod, the organization of data in resources and the organization of these resources on the Solid pod becomes the responsibility of the application. 
Through the similarity of the resources and containers defined by the LDP interface and the directories and files defined by a file system,
applications can encode the same assumptions in the LDP interface they use to interact with a Solid pod that they use to interact with files on a file system.
We already see this leading to problems in interoperability between applications in the Solid ecosystem, even though the ecosystem is still very small.

<!-- Made worse by lack of authoritative definition -->
Additionally, a lack of an authoritative definition for Solid also poses problems.
As the solid ecosystem expands through new initiatives and industry attention, the lack of definition leads to different interpretations of the ecosystem and in turn these different interpretations lead to concrete technical difficulties in the development of the ecosystem.
As the concept of a Solid pod is often confused with the LDP interface it implements to interact with the data on a pod,
problems arise where applications see the ecosystem as a network of LDP nodes.

<!-- We propose a new perspective -->
With this work, we propose the interpretation of a Solid pod being fundamentally a permissioned hybrid knowledge graph, exposed through Web APIs.
This interpretation of a Solid pod provides a way out for a lot of interoperability problems that are being faced in the Solid ecosystem.
Where the notion of a Solid pod being an LDP interface means limiting the potential of the ecosystem by the limits of the interface, 
the proposed interpretation articulates the notion of a Solid pod decoupling the data from the interface, which is a vital perspective for the ecosystem to create solutions that promote longevity.


<!-- Sections -->
In [](#problem_statement), we define how the use of LDP can lead to problems through the organization of data on Solid pods.
[](#vision) provides our proposed perspective of how viewing Solid data pods as permissioned knowledge graphs that can be exposed over a multitude of APIs can provide a framing of Solid that can lead to better long term solutions.
In [](#comparison), we compare the different viewpoints through a practical example, after which a conclusion is formulated in [](#conclusion).












<!-- 



The goal of the Solid platform is to present a platform that separates applications and data, creating an ecosystem where multiple applications can seamlessly work with the same data [cite from somewhere? ask Ruben V?]().
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
The semantic Web was introduced as an extension to the Web to make data machine-readable [](cite:cites semanticweb).
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
