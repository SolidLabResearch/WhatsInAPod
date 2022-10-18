## The Solid vision of data interoperability and control # {#introduction}
<!-- Introduction of Solid -->
Data privacy and control have lost ground on today's Web.
User-generated data is stored in centralized data silos,
in which people have neither the control nor the knowledge to manage how their data is being used [](cite:cites berners2009socially).
As a response to this, the _Solid_ project was created with the aim of revitalizing the Web [](cite:cites sambra_solid_nodate,verborgh_timbl_chapter_2022).
Where the current system of centralized data silos create an ecosystem of limited integration, availability and innovation,
Solid brings a course correction for the Web.
Based on the _separation of data and applications_,
the vision defines an ecosystem that facilitates the integration of data in different applications, while keeping people in direct control of their data.

<!-- the Solid pod -->
To this end,
Solid introduces the concept of a _pod_
as an online data space for an individual to control and manage their data on the Web.
Together, these pods form a decentralized Solid ecosystem,
from which applications can directly integrate data from a person's Solid pod,
after receiving their permission.
This contrasts with current Web applications, where
this data first had to be collected in a centralized location,
after which the platform-specific API had to be integrated,
where all the while user control is at the mercy of the platforms maintaining the data. 

<!-- key for achieving requirement: capture semantics in the data -->
In order to separate applications from their data,
the semantic contents of the data must be captured
such that they can be accurately interpreted and reused in different contexts.
Semantics allow applications to interpret data without 
requiring specific knowledge encoded in the API over which the data is retrieved.
A key driver is the use of the [Resource Description Framework (RDF)](cite:cites RDF),
which provides an infrastructure for the capture of this semantic information.
This again contrasts with current Web APIs,
where data is served in formats that require additional semantics to be captured in the documentation of the API.
By shifting the focus from the API to the data,
the Solid ecosystem aims to transition the Web
from an ecosystem of API integration towards
an ecosystem of data integration [](cite:cites rubenv_reflections_2021).

<!-- The problem: no API-independence -->
Unfortunately, we observe a significant gap between theory and practice:
current Solid apps do not succeed in API-independent reuse of data
across use cases.
Rather than only relying on the data and its semantics,
apps resort to implicit knowledge
about how this data is structured across documents in a pod's API.
Furthermore,
different use cases impose conflicting requirements
on that structure in order to satisfy their constraints.
As such,
application developer struggle to make sustainable decisions
on how to structure data for reuse,
since their individual choices impact the interoperability of the entire ecosystem.

<!-- Article purpose -->
In this article,
we identify the root cause of this interoperability problem
as the mismatch between Solid's current single hierarchical API
and the modeling requirements of real-world use cases.
We describe the properties of this document-centric interpretation on a Pod,
and introduce a graph-centric interpretation
that can bridge differences between use cases.
We compare both interpretations,
explain the consequences for concrete Solid implementations,
and argue why we consider the graph-centric interpretation
a more sustainable candidate to realize the Solid vision
of data and application independence under control of the user.
