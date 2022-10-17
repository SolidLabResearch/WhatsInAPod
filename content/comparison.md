## Comparative analysis # {#comparison}
<span class="todo">intro</span>

### Storage # {#comparison-storage}
<div class="todo" markdown="1">
document-centric:

- likely document store
- quad store, but fourth element always document

graph-centric:
- quad store will work best
- possibly RDF-star
</div>

### Publication # {#comparison-storage}
<div class="todo" markdown="1">
document-centric:

- straightforward from document store

graph-centric:
- needs high-performance view definitions and applications
</div>

### Querying # {#comparison-storage}
<div class="todo" markdown="1">
document-centric:

- link-traversal-based query processing
- possibly aided by indexes

graph-centric:
- LDF with Comunica, choose most appropriate interfaces
- automatically generate relevant interfaces
- just a SPARQL endpoint will not be sufficient because of federated queries
</div>
