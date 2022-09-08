**Structure of What's in a pod - final**
-------------------------

- **Intro: Solid envisioned ecosystem**
  - problem: your data being everywhere, no control very limited interoperability
  - Solid: a vision for a better Web
  - ecosystem goal: control over data, interoperability over applications and data
  - requirement: separation of apps and data
  - key for achieving requirement: capture semantics in the data
  - enables: data integration instead of interface integration
  - BUT: the understanding of what a pod is varies wildly
  - there is no authoritative definition
  - leads to misunderstandings that confuse the product of the Solid pod with the envisioned ecosystem.

  - something about data privacy and permissions / policies?

-------------------------


- **A document-centric interpretation of the Solid pod**
  - Solid uses an adaptation of LDP spec to interact with data on pod
  - This proposes Solid as a document-centric ecosystem.
  - Straightforward interpretation: LDP presents as a document storage system
  - In this interpretation, the documents are the ground truth of the data in the pod.
  - Interoperability on top of the document structure is very limiting
    - Apps built on the assumption of the interface are very limited
    - mismatch in hierarchy, assumptions, permissions (i, ii, iii)
    - limiting in the achievable interoperability
    - Enrichment of data through semantics is no driver in this interpretation - these are captured in local assumptions of applications.
  - Interop requires understanding of Solid pod as a KG.
    - Solid documents can be distilled into a KG
    - This allows us to work on the full information space in the data pod
  - There are issues though
    - documents are the ground truth of the pod, KG is only a derived view
    - There is no definition as to what constitutes the KG in an LDP environment: 
      - only the resources?
      - the full interface data + resource data?
      - what about statements made about a resource that is a collection of statements?
      - what about building apps on resource timestamps, ...
      - -> no clear conversion!
      - No clear inverse correlation as well, going from a KG to an LDP interface is not always possible, as LDP requires encapsulation of statements in resources, ...
    - Additionally, the permission structure that is tied to the LDP structure makes sense in LDD interpretation, but loses its meaning in a KG interpretation, as permissions are now tied to arbitrary collections of statements.
    - Other requirements for the ecosystem for application interoperability (asking access, ...), are tied to the constraints of the LDP interface.
    - requirement for documents means inherent reliance on implicit assumptions that are not captured in the data itself, but are tied to specific understanding of what a document is by applications. (e.g. this is data from this app, this should only be managed by this app, ...). 
    - writing data to the pod KG is only possible by wrapping statements in a resource somewhere on the pod
    - interpretation of apps as a document centric ecosystem may lead to lack of semantic info in the data, as it is interpreted as document system where these assumptions are encoded in the API, leading other apps to miss out on important aspects of the data.

  - We see signs of the original vision being construed to this view of Solid as a permissioned KG
    - as they proposed an optional SPARQL interface on top of the pod, 
    - and a QPF from inrupt now currently
    - leading to a vision that the interpretation of Solid as a KG would be necessary from the start.
  - The current LDP + WAC seem to currently form an environment that is designed as an (awkwardly constrained) proxy for a permissioned hybrid KKG
  - Where document-centric vision can provide an simple mechanism for data management for a single app, it provides many challenges for a Web ecosystem where interoperability and the separation of app and data are central concepts.
    
-------------------------

- **A graph-centric interpretation of the Solid pod**
  - We see that the current implementation of Solid as fundamentally document-centric, that can be distilled into a KG leads to issues.
  - In this work, we want to propose an interpretation of the Solid pod as fundamentally a permissioned, hybrid, knowledge graph.
    - Permissioned: we can store permissions per entity in the knowledge graph -> but more fundamentally we can expand this vision to parameterized KG, where we can store permissions, provenance, and other information for triples in the KG.
    - Hybrid: triples and blobs(documents) are first-class citizens in the KG
    - KG: definition from paper linked by RUben V on mm.
  - In this interpretation, the KG is the ground truth of the data in the pod.
  - Interfaces interoperate with the KG, and not though a proxy of working with documents
  - This vision focuses mainly on management issues (perms, writing, ...) with the document-centric interpretation as a KG, but is in terms of querying fuly compatible with the document-based interpretation -> all data you can access in KG -> query
  

-------------------------
- **comparison**
  - We compare the different interpretations of Solid pod in the capabilities of the current ecosystem.
  
  - we compare using a contact-list-app, a birthday-list-app and a car sharing app.
    - compare on the point of hierarchy: 
      - mismatch in hierarchy leads to limited to no interoperability for 2 apps intepreting it as LDDs, but third app interpreting pod as KG can query all data from all 3 apps.
    - compare from point of permission:
      - 2 apps interpreting as LDDs just write contact info as full contacts. Third app writes public and private resource per contact for information. However, when sharing the available contacts, through a mismatch of permission structure, it shares all contact details of the contacts written by other apps -> permission structure DOES NOT MAKE SENSE in the KG interpretation
    - compare from point of optimization:
      - 2 apps interpreting as LDDs can set the structuring of the data to optimize data retrieval.
      - 3d app may make use of systems such as type index, but other apps dont use it because they know where their data is, so optimization is very limited for app 3.


  - We see that  even in the LDP-based ecosystem, the KG interpretation solves the data interop issues in the examples.
  - We show that the interpretation of Solid as a KG actually ignores all the indexing of the Solid LDP API, and only uses it to build its internal KG representation.
  - We show that the LDP API is limiting in terms of permissions and optimization.
  - In short: the LDP API did not really help us at all and only sets (in the term of the KG representation) arbitrary constraints on the permissions that can be set


-------------------------

- **Conclusion**
  - The current Solid ecosystem is open to interpretation
  - In this work, we presented two interpretations
  - Currently, we notice a lot of application development and initiatives adopting the document-centric interpretation.
  - Where the document centric interpretation of Solid provides a straightforward interface, it leads to limitations in interoperability proposed in the vision.
  - To move towards an interoperable ecosystem, we move towards the understanding of a pod as a knowledge graph to solve these interop problems (even the initial Solid paper shared this vision through their optional SPARQL, later removed from spec)
  - We argue that even through this understanding, the interpretation of Solid as a document-centric ecosystem limits the innovation surface to the constraints of the document system (perms, assumptions, adaptations to the KG cannot always be translated back into the documents, ...).
  - We proposed the interpretation of a pod as a fundamentally a knowledge graph.
  - We argue that the KG-centric interpretation of Solid provides an innovation space that is much larger than a document-centric interpretation.
  - Hybrid knowledge graph manages documents and data
  - With this work, we hope to guide future discussion and innovation in the Solid ecosystem to consider the consequences of their interpretation of the ecosystem
  - and we propose that where both interpretations can have their merits, the KG interpretation leads to a larger innovation surface for a fully interoperable ecosystem with separation of application and data.
  - In future work, we plan to look into how these interpretations can be reconciled, or made to work together in a single ecosystem.
  

  - We conclude that: 
    - (i) For interoperability purposes, the understanding of Solid as a KG is key
    - (ii) The document-centric interpretation of Solid leads to a limited innovation surface, certainly in terms of management of personal data (perms, writing, ... all the issues).
    - (iii) For the understanding of Solid as a KG to work from a management perspective where we make multiple applications interoperable on our data, we need to interpret Solid fundamentally as a permissioned, hybrid knowledge graph.
    - (iv) Document-centric use cases largely compatible with KG vision in cases where data management does not need to be interoperable.
  








---------------------------------
- separation of app and data
- semantics in data
- user control


in document structure: 
- separation is NOT achieved
- semantics captured in documents
- user control IS limited

in graph query
- separation still not achieved
- document semantics cause lack of required semantics
- user control STILL limited

fundamentally graph
- separation  is achieved, interface independence is required.
  - must be captured in tooling
- semantics that can be queried SHOULD be captured in data
- user control can be modelled in an infinite amount of ways over the data

