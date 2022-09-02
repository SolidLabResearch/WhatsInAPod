**Structure of What's in a pod - v4**
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


- **An interpretation of Solid pod as Linked Data Documents**
  - Solid uses an adaptation of LDP spec to interact with data on pod
  - Straightforward interpretation: LDP presents as a document storage system
  - The vision can be misconstrued as an online ecosystem for sharing documents / resources - which can interpreted as the vision for interoperability in the Solid ecosystem.
  - interpretation leads to limited interoperability
    - invites assumptions in applications to data structure, resource location, etc ...
  - Enrichment of data through semantics is no driver in this interpretation - these are captured in local assumptions of applications.
    - leads to a lack of necessary semantic information to make data interoperable in the data produced by these applications. 
  - LDP+WAC seems to be a (awkwardly constrained) proxy for a permissioned hybrid KKG
    
-------------------------

- **An intepretation of Solid pod as a Knowledge Graph**
  - A second interpretation of the Solid ecosystem sees the Solid pod as fundamentally a KG/
  - This interpretation forms the base for the interoperability promised by the Solid ecosystem.
  - Make the point that the pod as a KG solves separation of data and app:
    - hierarchical mismatches? -> no problem its a graph
    - different apps different organization of data? -> no problem as a KG does not require any structuring
  


  - We can try to make the current ecosystem of Solid and LDP fit this interpretation
    - Interpreting the data stored in the resources over the LDP hierarchy creates a KG of the data stored in the pod.
    - KG interpretation is compatible with non-RDF documents
    - However, there is no definition as to what constitutes the KG in an LDP environment: 
      - only the resources?
      - the full interface data + resource data?
      - what about statements made about a resource that is a collection of statements?
      - what about building apps on resource timestamps, ...
      - -> no clear conversion!
      - No clear inverse correlation as well, going from a KG to an LDP interface is not always possible, as LDP requires encapsulation of statements in resources, ...
    - Additionally, the permission structure that is tied to the LDP structure makes sense in LDD interpretation, but loses its meaning in a KG interpretation, as permissions are now tied to arbitrary collections of statements.
    - Other requirements for the ecosystem for application interoperability (asking access, ...), are tied to the constraints of the LDP interface.
  
  - We conclude that this interpretation is necessary for achieving the goals for the Solid ecosystem of API integration -> data integration, but in the current ecosystem we run into the boundaries of what the current specifications allow us to do.

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
  - We present two common interpretations: one of Solid pod as collection of individual LDDs, other as Solid pod as a KG
  - We showed that the interpretation of Solid pod as collection of LDDs leads to problems in interoperability.
  - We showed that the interpretation of Solid pod as a KG can solve these interop problems (alsready alluded in first paper -> optimize query with SPARQL requires this assumption), but runs into the restrictions of LDP on the ecosystem.
  - We argue that for the interpretation of Solid as KG, LDP limits the innovation surface of what we can achieve on this path.
  - If the ecosystem wants to move in this direction, it is preferable to not equate the Solid ecosystem to the current specifications.




<!-- 


-------------------------

- Solid as a Knowledge Graph -  a required interpretation for longevity of the ecosystem
  - this is the final viewpoint we converge at
  - We notice that the viewpoint of Solid as LDP hierarchy that can be interpreted as Knowledge graph solves a lot of problems
  - We notice that leftover problems are not really interoperability (can we say this?) - but are mainly question of leftover semantics of the interface + the BIG issue of permissions.
  - We notice that optimization surface of LDP is limited: either adapt the interface, or rely on applications or you have to make your own optimizations - Even original paper brought these issues forward.
  - Because of all this, final viewpoint is that in eventuality, the ecosystem should converge to the notion of a Solid pod being permissioned knowledge graph that can support any kind of Web APIs (, and should not rely too heavy on LDP as centerpiece? - did we make this point enough?)
