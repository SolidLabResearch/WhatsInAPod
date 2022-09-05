## The Solid vision # {#introduction}
<!-- problem: your data being everywhere, no control very limited interoperability -->
In the current Web 2.0 ecosystem, 
the concepts of data ownership and privacy have lost a lot of meaning,
as data that is often user generated is stored in centralized data silos
which are rarely under direct user control.
In this system, the user neither has the control nor the knowledge to manage how their data is being used in the online space [](cite:cites berners2009socially).
<!-- Solid: a vision for a better Web -->
As a response to this, the Solid project was created with the aim of revitalizing the Web [](cite:cites sambra_solid_nodate).
Where the current system of centralized data silos create an ecosystem of limited integration, availability and innovation,
Tim Berners-Lee’s Solid brings a new vision for an ecosystem on the Web.
<!-- ecosystem goal: control over data, interoperability over applications and data -->
Based on the premise of separating applications and data,
the envisioned ecosystem aims to facilitate integration of data and 
bring new opportunities for innovation [](cite:cites berners2009socially).

<!-- the Solid pod -->
It introduces the concept of the personal online datastore (pod)
as an online data space where users are in full control of their data.
These pods form the foundation for the decentralized Solid ecosystem,
where applications can integrate data from a user Solid pod through user consent.
This is in contrast to the Web 2.0 architecture where
the integration of APIs exposed by centralized data silos forms the basis of the ecosystem,
and user control is at the mercy of the platforms maintaining the user data [](cite:cites berners2009socially). 

<!-- key for achieving requirement: capture semantics in the data -->
A key component for achieving this decentralized ecosystem 
of separation of application from data 
is the capturing of required semantic information in the data itself,
so that applications can work with the data independent 
of the origin and API over which the data is retrieved.
This in contrast to the current Web 2.0 architecture,
where necessary semantics for the data are often provided out of band,
through agreements in the ecosystem or documentation of specific APIs
that applications need to integrate in their logic.
In this way, the Solid ecosystem marks a transition
from a Web ecosystem of API integration towards
a Web ecosystem centered around data integration [](cite:cites rubenv_reflections_2021).

<!-- Now this vision has to be made a reality -->
From the vision of this ecosystem, 
the challenge is now presented in how these concepts
can be captured in specifications for the Web.
<!-- The vision is room for many interpretations -->
As the proposed vision is is based on broad concepts,
the realization of these concepts can take many different forms.
<!-- there is no authoritative definition -->
With no authoritative definition currently available for Solid,
the understanding of the ecosystem is not always shared in the ecosystem,
leading to misunderstandings and mismatching of the existing systems and application assumptions.

With this work, we describe two interpretations of the Solid ecosystem.
In [](#documentcentric), we describe the interpretation of the Solid vision as a document-centric ecosystem,
which is the current understanding on which the current Solid ecosystem is based,
and the limitations this brings for the ecosystem.
In response, we present the interpretation for Solid as a an graph-centric interpretation of the Solid ecosystem in [](#graphcentric)
as a zoomed-out perspective of the current ecosystem. 
We describe how this perspective creates a broader base for innovation,
by expanding upon the current state of the ecosystem.
Finally, we present our conclusions in [](#conclusion).
