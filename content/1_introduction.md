## The Solid vision # {#introduction}
<!-- problem: your data being everywhere, no control very limited interoperability -->
In the current Web 2.0 ecosystem, 
the concepts of data ownership and privacy have lost a lot of meaning,
as data that is often user generated is stored in centralized data silos
which is often out of user control.
In this system, the user neither has the control nor the knowledge of to how their data is used in the online space [](cite:cites berners2009socially).
<!-- Solid: a vision for a better Web -->
As a response to this, the Solid project was created with the aim of revitalizing the Web [](cite:cites sambra_solid_nodate).
Where centralized data silos create an ecosystem of limited integration, limited availability and limited innovation,
Tim Berners-Lee’s Solid brings a new vision for an ecosystem on the Web,
based on the concepts of application interoperability and user control.
<!-- ecosystem goal: control over data, interoperability over applications and data -->
An ecosystem that empowers integration and innovation 
through the separation of applications and data 
that puts users back in control of their data[](cite:cites berners2009socially).

<!-- the Solid pod -->
Introducing the concept of the personal online datastore (pod), 
the Solid pod forms the foundation of the ecosystem as 
a storage space where users are in control of their data,
creating a decentralized network of Solid pods
where applications can integrate data through user consent,
in contrast to the Web 2.0 architecture where applications are required to integrate data 
through APIs exposed by centralized data silos,
and user control is at the mercy of the platform maintaining the user data [TODO:: good citation](). 

<!-- key for achieving requirement: capture semantics in the data -->
A key component for achieving this decentralized ecosystem 
of separation of application from data 
is the capturing of required semantic information in the data itself,
so that applications can work with the data independent 
of the origin and API over which the data is retrieved.
This in contrast to the current Web 2.0 architecture,
where necessary semantics for the data are often provided out of band,
through agreements in the ecosystem or documentation of a specific APIs
that applications need to integrate in their application logic.
In this way, the Solid ecosystem marks a transition
from a Web ecosystem of API integration towards
a Web ecosystem centered around data integration [](cite:cites rubenv_reflections_2021).

<!-- Now this vision has to be made a reality -->
From the vision of this ecosystem, 
a challenge is now presented for the Web in how these concepts
can be captured in specific specifications that can 
create this envisioned ecosystem for the Web.
<!-- The vision is room for many interpretations -->
As the proposed vision is is based on broad concepts,
the realization of these concepts can take many different forms.
<!-- there is no authoritative definition -->
With no authoritative definition currently available for Solid,
the understanding of the ecosystem is not always shared in the ecosystem,
leading to misunderstandings and mismatching of the existing systems and application assumptions.

With this work,
we describe the two main interpretations of the Solid ecosystem we discern today. 
In [](#documentcentric), we describe the document-centric interpretation of the ecosystem,
the current focus on this interpretation in the majority of implementations,
and the shortcomings in terms of interoperability.
Next, we describe the graph-centric interpretation of the Solid ecosysten in [](#graphcentric),
where we propose the definition of the Solid Pod being fundamentally a permissioned, hybrid knowledge graph
as a necessary interpretation to expand the innovation potential for the ecosystem.
In [](#comparison), we compare the two interpretations and their consequences for the ecosystem, 
after which we bring our conclusions in [](#conclusion).
