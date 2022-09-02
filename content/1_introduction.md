## The Solid vision # {#introduction}
<!-- problem: your data being everywhere, no control very limited interoperability -->
In the current Web ecosystem, the concepts of data ownership and privacy have lost a lot of meaning with user data being captured by corporations in walled data silos.
In this system, the user neither has the control nor the knowledge to manage how their data is being used online. [TODO:: good citation]()
<!-- Solid: a vision for a better Web -->
As a response to this, the Solid project [TODO:: cite]() was created with the aim of revitalizing the Web.
Where centralized data silos create an ecosystem of limited integration, limited availability and limited innovation,
Tim Berners-Lee’s Solid brings a new vision for the Web.
<!-- ecosystem goal: control over data, interoperability over applications and data -->
An ecosystem that empowers integration and innovation through the separation of data away from services and applications, 
where users are put back in control of their data.
Introducing the concept of the personal online datastore (pod), 
the Solid pod forms the foundation of the ecosystem as a decentralized network of data,
where applications integrate data from the available sources in the decentralized network,
in contrast to the traditional Web where applications integrate data through APIs exposed by centralized data silos [TODO:: cite reflections of knowledge](). 
<!-- key for achieving requirement: capture semantics in the data -->
Where essential information for applications to work with data
is traditionally often encoded in assumptions of the application
or in the semantics of specific interfaces [TODO:: cite? sources?],
the envisioned ecosystem relies on the availability of this information
encoded in the semantics of the available data.
<!-- enables: data integration instead of interface integration -->
Through the transition from semantics encoded in interfaces and application assumptions,
an ecosystem is created based on the separation of data and applications.

<!-- Now this vision has to be made a reality -->
From the envisioning of an ecosystem that can form the next step for the Web,
a challenge is posed in how these concepts interoperability and innovation can be 
captured in specific systems for the Web. [TODO:: wording choice?]()
<!-- The vision is room for many interpretations -->
As the vision proposed above is broad in terms of concepts,
the understanding of these concepts be equally divided.

{:.comment data-author="RD"}
Where the vision for interoperability can be understood as the ability for applications to seamlessly integrate data from multiple sources,
others may understand this concept as simply the sharing documents over the Web.

<!-- there is no authoritative definition -->
Additionally, there is currently no authoritative definition for Solid, nor the concept of the Solid pod.
Because of this, initiatives in the Solid ecosystem currently work on definitions for the ecosystem
that are a reflection of their interpretation of the vision and their understanding of the current ecosystem.
<!-- leads to misunderstandings that confuse the product of the Solid pod with the envisioned ecosystem. -->
This leads to a rapidly evolving ecosystem, 
where individual assumptions are made that are not shared by the ecosystem,
and where proposed solutions may lack longevity in the context of the evolving ecosystem.
<!-- work proposition -->
In this work, 
we describe two interpretations of the Solid pod in the envisioned ecosystem.
in [](#documentcentric), we describe the document-centric interpretation that is supported by the current implementation, 
as well as an evolution of the ecosystem towards a more graph-centric perspective.
In [](#graphcentric), we describe a graph-centric of the Solid Pod as fundamentally a permissioned, hybrid knowledge graph
as a necessary interpretation to expand the innovation surface for the ecosystem.
[](#comparison) provides a comparison on the consequences of the chosen interpretation on the ecosystem,
after which we bring our conclusions in [](#conclusion)
