## The Solid vision # {#introduction}
<!-- problem: your data being everywhere, no control very limited interoperability -->
In the current Web 2.0 ecosystem, 
data ownership and privacy have lost a lot of ground.
Data that is often user generated is stored far away in centralized data silos
and is rarely under direct user control.
In this system, the user neither has the control nor the knowledge to manage how their data is being used in the online space [](cite:cites berners2009socially).
<!-- Solid: a vision for a better Web -->
As a response to this, the Solid project was created with the aim of revitalizing the Web [](cite:cites sambra_solid_nodate).
Where the current system of centralized data silos create an ecosystem of limited integration, availability and innovation,
Tim Berners-Lee’s Solid brings a course correction for the Web.
<!-- ecosystem goal: control over data, interoperability over applications and data -->
Based on the separation of applications and data on the Web,
the vision defines an ecosystem that facilitates the integration of data in applications, while keeping users in direct control of their data [](cite:cites berners2009socially).

<!-- the Solid pod -->
It introduces the concept of the personal online datastore (pod)
as an online data space for users to control and manage their data on the Web.
These pods form a decentralized Solid ecosystem,
from which applications can directly integrate data from the user Solid pod,
after receiving permission from the user.
This is in contrast to the Web 2.0 architecture where
this data first had to be collected in a centralized location,
after which the platform-specific API had to be integrated,
where all the while user control is at the mercy of the platforms maintaining the data [](cite:cites berners2009socially). 

<!-- key for achieving requirement: capture semantics in the data -->
A key premise for enabling the separation of application and data
is the capture of semantic information in the data itself.
This way, applications can interpret the data without 
requiring specific knowledge encoded in the API over which the data is retrieved. A key driver here is the use of the Resource Description Framework (RDF) [](cite:cites miller1998introduction), that provides an infrastructure that enables the capture of this semantic information in the data.
This again stands in contrast to the current Web 2.0 architecture,
where data is often served in formats that require additional semantics to be captured in the documentation of the API.
In this way, the Solid ecosystem marks a transition
from a Web ecosystem of API integration towards
a Web ecosystem centered around data integration [](cite:cites rubenv_reflections_2021).

<!-- Now this vision has to be made a reality -->
From the vision of this ecosystem, 
the challenge now presents itself in how these concepts
can be captured in specifications for the Web.
<!-- The vision is room for many interpretations -->
The proposed vision is is based on broad concepts of interoperability
and user control, so the realization of these concepts can take many different forms.
<!-- there is no authoritative definition -->
As there is no authoritative definition currently available for Solid,
the current initiatives and specifications defining the ecosystem are based on specific interpretations of the Solid vision, and how this can be translated into specifications for the Web.

In [](#documentcentric), we describe the interpretation of the Solid vision as a document-centric ecosystem, which is the understanding on which most of the Solid ecosystem is based.
In response to the limitations of this interpretation, 
we present a zoomed-out perspective of a graph-centric interpretation of the Solid ecosystem in [](#graphcentric).
We describe how this perspective creates a broader base for innovation,
by expanding upon the current state of the ecosystem.
Finally, we present our conclusions in [](#conclusion).
