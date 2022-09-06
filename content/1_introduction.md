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
based on the concept of separation of application and data,
user control of their data in the online space
and the encoding of semantic information in the data itself,
the concept of the Solid pod is introduced.
Introduced as the personal online datastore (pod),
the Solid pod forms the foundation of the envisioned Solid ecosystem.
The pod provides an online data space for users to manage and store their
personal data on the Web.
In the vision of separating applications and data storage,
users are enabled to direct applications storing or reading data 
to their own Solid pod as authoritative data source on their data.
In this space, the user has control over the data
and is free to share it with the Web.
The Solid pod includes the concepts of RDF,
as the storage of semantic information forms
the basis over which the decentralized network 
of Solid pods can be queried.
Through these semantics, the requirement of integrating
API specific semantics is removed, leading to more scalable applications.
In this way, the Solid pod forms the basis for the envisioned Solid ecosystem for the Web (cite:cites berners2009socially). 

<!-- Now this vision has to be made a reality -->
From the vision of this ecosystem, 
the challenge now presents itself in how these concepts
can be captured in specifications for the Web.
<!-- The vision is room for many interpretations -->
The proposed vision is is based on broad concepts,
so the realization of these concepts can take many different forms
and is largely based on interpretations.
<!-- there is no authoritative definition -->
As there is no authoritative definition available for Solid,
the current implementation of the ecosystem is based on specific
interpretations of the vision.
These interpretations are not universally shared in the ecosystem,
and limit the potential of the implementation of the ecosystem
to that of specific interpretations.

In [](#documentcentric), we describe prevalent interpretation of the Solid as a document-centric ecosystem,
made popular by the available implementations for the ecocystem,
and address the limitations of this interpretation.
As a response, we present a zoomed-out interpretation of Solid as an ecosystem of decentralized knowledge graphs in [](#graphcentric).
We explore how a fundamental definition of the Solid pod being a knowledge graph changes the ecosystem
and creates a broader base for innovation by expanding upon the current state of the ecosystem.
Finally, we present our conclusions in [](#conclusion).
