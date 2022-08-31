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


- **An interpretation of Solid as Linked Data Documents**
  - Straightforward interpretation: LDP presents as a document storage system
  - An online system for sharing documents between app - Aha the vision of *i n t e r o p e r a b i l i t y*
  - cause: 
    - lack of understanding of the ecosystem. 
    - lack of definition provided by ecosystem.
    - lack of tooling that guides developers to the envisioned ecosystem
  - consequence: 
    - assumptions in applications and interface
    - no interoperability
    - no understanding for the view of EXTRA semantic enrichment for data, they could as well be writing JSON because of lack of vision

-------------------------

- Solid as LDP hierarchy that can be interpreted as Knowledge graph - a required perpective for solving interoperability
  - You can view the LDP hierarchy as a knowledge graph with resources as subgraphs / you can yeet all resources together as a KG.
  - Make the point viewing the resources in the LDP hierarchy of Solid pod as a KG -> we solve A LOT of interop problems.
    - hierarchical mismatches? -> no problem its a graph
    - different apps different organization -> no problem the resulting graph should be same if data is same
    - ...
  - BUT: We run into some leftover semantic difficulties: is interface part of the KG? 
    - The timestamp for resources for example can be important - this is encoded in the interface
    - The problem of knowing where to look to update / remove a statement in the pod knowledge graph requires keeping context of where statements are being made - consequence of the interface
  - LDP requires additional support for optimization (shape trees / type index), that EITHER have to be handled server side, or its client side but you cannot really trust the results as not all applications may maintain these indexes?
  - Additionally, we still have the massive issue of a mismatch (here we can use it I think) in the handling of permissions. 

-------------------------

- Solid as a Knowledge Graph -  a required interpretation for longevity of the ecosystem
  - this is the final viewpoint we converge at
  - We notice that the viewpoint of Solid as LDP hierarchy that can be interpreted as Knowledge graph solves a lot of problems
  - We notice that leftover problems are not really interoperability (can we say this?) - but are mainly question of leftover semantics of the interface + the BIG issue of permissions.
  - We notice that optimization surface of LDP is limited: either adapt the interface, or rely on applications or you have to make your own optimizations - Even original paper brought these issues forward.
  - Because of all this, final viewpoint is that in eventuality, the ecosystem should converge to the notion of a Solid pod being permissioned knowledge graph that can support any kind of Web APIs (, and should not rely too heavy on LDP as centerpiece? - did we make this point enough?)

-------------------------

- Conclusion
  - ...