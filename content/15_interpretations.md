# Possible interpretations of A Solid pod as a Knowledge Graph

## A list of possible interpretations of a Solid pod

### A pod is a Linked Data Documents management system that can be distilled into a KG
In this section, we look at the interpretation where the Solid pod is fundamentally a collection of Linked Data Documents

This interpretation is based on the idea of a pod as a document managment system.

**general statements**
- authorization is ((probably)) linked to document structure
    - does not really make sense to pull outside of document structure, though you could make something ugly with partial permissions and PATCH.
- adding statements to the KG means they MUST be encapsulated in a document
- **no defined way of how to distill KG from a set of Linked Data Documents**
    - add resource as graph? 
    - what about statements about a resource?
- non-RDF resources are just represented as a URI in the KG


#### The distilled KG should be query only

- no need to change RDF documents
- retrieve documents as you posted them
- KG expands by adding documents, remove info by deleting documents
- Solid can serve as a document management system

#### The distilled KG should be **partly** query only, and the rest may be edited

- You can decide whether or not an RDF document may be edited
- These documents can be retrieved as is
- rest can be made ugly
- **no real logic as to which part of the KG can be edited**
- Solid can serve **partly** as a document management system


#### The distilled KG should be fully editable

- HTML+RDFa documents must be chosen to be **either** treated as RDF **or** as HTML, and not included in the KG in case of non-RDF choice
- All documents can be changed
- Not really usable as a document management system anymore, but has become a data management system.


### A pod is a Knowledge Graph
In this section, we look at the interpretation where the Solid pod is fundamentally a Knowledge Graph

This interpretation is closer to the pod being a graph store than the pod being a file system.

**general statements**
- This interpretation does not provide any inherent functionality for documents
    - non-RDF resources are just a URI in the pod KG
    - there can be support over certain interfaces to add a document to a pod as a URI
    - document metadata can be stored in the KG linking to this URI

- This is **not consolable with the concept of RDF resources**
    - either it's a document, or it's DATA
    - data is inherently part of the KG, not of a certain document.
    - you **can** create documents of the KG
        - you can create concrete views of the KG
        - cfr Linked Data Fragments 
- permissions management can happen on any level and over any collection of statements
    - document permissions still work as this is permissions for a single URI of the data graph
- URI minting requires interface support (not sure how to tackle this tbh):
    - e.g. I want to add the data of a new event to the pod -> any blank nodes in this scheme are persisted in the namespace of the pod, after which they can be referenced to by that URI
    - how do you return this knowledge to the app as to which URI was assigned to this?


