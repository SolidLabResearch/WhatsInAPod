## The Solid vision # {#introduction}
<!-- problem: your data being everywhere, no control very limited interoperability -->
In the current Web 2.0 ecosystem, 
user data is often stored far away in centralized data silos,
hidden away behind the interfaces of large data platforms
and rarely under direct user control.
In this system, the user lacks both the control and the knowledge to manage their data in the online space [](cite:cites berners2009socially).
<!-- Solid: a vision for a better Web -->
As a response to this, the Solid project was created with the aim of revitalizing the Web [](cite:cites sambra_solid_nodate).
Where the current Web is characterized by limited integration, availability and control of data,
Tim Berners-Lee’s Solid brings a course correction for the Web.
<!-- a decentralized vision -->
It defines the vision for a decentralized ecosystem
where users are in control of their data in the online space
and centralized data platforms are replaced
by a decentralized network of smaller data sources.
<!-- enabled through data integration -->
In this ecosystem, the integration of specific APIs
provides no scalability, and the ecosystem shifts
away from API-integration, towards a more scalable
ecosystem based on data-integration [](cite:cites rubenv_reflections_2021)].

<!-- separation of application and data -->
In the current Web 2.0 ecosystem, applications manage data storage,
leading to centralized data silos with limited user control.
In contrast, the Solid vision is built on the notion
of the separation of applications and data on the Web.
In this vision, users can guide applications in where to 
retrieve and store their data, moving the data away
from centralized data silos into user-managed data spaces.

<!-- data under user control -->
Through this externalizing of data storage and retrieval
into user-managed space, users can be put in control
of their data in the online space.
From here, users are now free to share
their data over the Web with other applications
and users at will.

<!-- key for achieving requirement: capture semantics in the data -->
The current Web 2.0 ecosystem does not support this process.
Currently, applications are reliant on the integration of APIs to 
learn the semantics of the data returned over the API.
This leads to scaling issues when working with multiple data sources,
as this requires the application to integrate multiple APIs over which
data is retrieved.
In contrast, the Solid vision for the Web envisions applications
integrating data from large numbers of data sources,
where this limited scaling is not an option.
To enable this Solid ecosystem,
semantics must be captured outside of the API and application logic,
an in the data itself.
To enable this vision, the Resource Description 
Framework (RDF) [](cite:cites miller1998introduction) was introduced.
This framework provides the infrastructure required 
to capture semantics in the structuring of the data itself.

<!-- the Solid pod - user control -->
As a summation of the vision for a new Web ecosystem,
based on the concepts of separation of application and data,
user control of their data in the online space
and the encoding of semantic information in the data itself,
the concept of the Solid pod takes form.
Introduced as the personal online datastore (pod),
the pod is provides the backend over which the separation 
of application and data is achieved.
By storing user data on their personal pod,
it is in a space they can manage and control 
and from where they can share their data over the Web.
It provides support semantically enriched RDF data
to enable applications to integrate data of many pods at once.
As such, it serves as the backbone 
on which the current re-decentralization 
of the Web is built [](cite:cites rubenv_redecentralizing_2019).

<!-- Now this vision has to be made a reality -->
From this vision,
the challenge now presents itself in to capture 
these concepts as specifications for the Web.
<!-- The vision is room for many interpretations -->
As the vision is broad in its concepts,
the realization of these concepts 
is largely based on interpretation
and can take many forms.
<!-- there is no authoritative definition -->
With no authoritative definition available,
the current implementations for the ecosystem
are based on shared interpretations of the vision
that may end up being a limiting factor for future innovation.

In [](#documentcentric), we describe the interpretation 
of the Solid as a document-centric ecosystem as currently
the central focus, and how its imposed document hierarchy limits innovation.
As a response, in [](#graphcentric) we present a zoomed-out perspective of the ecosystem
where the Solid pod is interpreted as fundamentally being a knowledge graph.
We explore how this definition fundamentally expands upon the ecosystem
and creates a broader base for innovation.
Finally, we present our conclusions in [](#conclusion).
