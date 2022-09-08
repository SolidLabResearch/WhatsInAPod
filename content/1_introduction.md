## The Solid vision # {#introduction}
<!-- problem: your data being everywhere, no control very limited interoperability -->
On today's Web,
data privacy and control have lost a lot of ground.
User-generated data is often stored far away in centralized data silos,
in which people have neither the control nor the knowledge to manage how their data is being used in the online space [](cite:cites berners2009socially).
<!-- Solid: a vision for a better Web -->
As a response to this, the Solid project was created with the aim of revitalizing the Web [](cite:cites sambra_solid_nodate).
Where the current system of centralized data silos create an ecosystem of limited integration, availability and innovation,
Tim Berners-Lee’s Solid brings a course correction for the Web.
<!-- ecosystem goal: control over data, interoperability over applications and data -->
The Solid vision presents a vision for the Web,
where centralized data silos are replaced
by a decentralized network of user data stores [](cite:cites rubenv_innovation_2020).
To support this envisioned ecosystem for the Web,
the ecosystem must support some of the core principles
required to enable this vision:

<!-- separate app and storage -->
(i) A first requirement is the separation of applications from data storage [](cite:cites berners2009socially).
This concept captures the need for users
to be able to steer the storage of user data
away from centralized silos on the Web, into a data 
space on the Web that they can control.

<!-- independence through RDF -->
(ii) Next, as data is separated, it should also be *independent*
from the application [](cite:cites berners2009socially). This is a requirement for other applications
to reuse this data in an open ecosystem.
A key driver here is the use of the [Resource Description Framework (RDF)](cite:cites RDF). 
Where currently, semantics are often encoded
in application logic and interfaces on the Web,
RDF provides the infrastructure required to capture
these semantics in the data itself.

<!-- user control -->
(iii) Finally, users should be in control
of how their personal data can be used on the Web [](cite:cites berners2009socially).
By moving user data away from centralized silos
into a space the user can directly manage,
we can give back the control of personal 
data to the user.


<!-- the Solid pod -->
As a culmination of these and other concepts
in the Solid vision, the concept of a _pod_ takes shape:
a personal online datastore where people can store
and control their data on the Web, 
both in RDF and non RDF formats.
These pods form a decentralized Solid ecosystem,
from which applications can directly integrate 
user data with adequate permissions given.

This envisioned ecosystem provides solutions
for the current Web, where integration happens
through the semantics of the API and where
data and the control thereof are at the
mercy of the data platform.
In this way, the Solid ecosystem aims to start a transition
from a Web ecosystem of API integration towards
a Web ecosystem centered around data integration [](cite:cites rubenv_reflections_2021).

<!-- Now this vision has to be made a reality -->
From the vision of this ecosystem, 
the challenge now presents itself in how these concepts
can be captured in specifications for the Web.
<!-- The vision is room for many interpretations -->
The proposed vision is based on broad concepts of interoperability
and user control, so the realization of these concepts can take many different forms.
<!-- there is no authoritative definition -->
As there is no authoritative definition available for Solid,
current initiatives and specifications defining the ecosystem are based on specific interpretations of the Solid vision.

In [](#documentcentric), we describe the interpretation of the Solid vision as a document-centric ecosystem, which is the understanding on which most of the current Solid ecosystem is based.
In response to the limitations of this interpretation, 
we present a zoomed-out perspective of a graph-centric interpretation of the Solid ecosystem in [](#graphcentric).
We describe how this perspective creates a broader base for innovation,
by expanding upon the current state of the ecosystem.
