## Preliminary definitions

Before describing the interpretations of a Solid pod,
we start with a couple of definitions that we will use as building blocks
throughout the article.

- We consider a <dfn id="dfn-protocol">protocol</dfn> to be
  a generic set of rules for data transmission between systems.
  - The [<dfn id="dfn-http">HyperText Transfer Protocol (HTTP)</dfn>](cite:citesAsAuthority HTTP)
    structures the exchange of data between a server and a client
    as resources identified by a URI.
  - The [<dfn id="dfn-ldp">Linked Data Platform</dfn>](cite:citesAsAuthority LDP)
    constrains HTTP with interaction rules for containers and RDF documents.
  - The [<dfn id="dfn-solid-protocol">Solid Protocol</dfn>](cite:citesAsAuthority Solid_protocol)
    constrains HTTP with [authentication](cite:citesAsAuthority Solid_OIDC)
    and [authorization](cite:citesAsAuthority WAC,ACP),
    and with interaction rules for containers and RDF documents
    (inspired by LDP).
- A <dfn id="dfn-web-api">Web API</dfn> is a specific structuring of resources
  on top of HTTP (or a specialization thereof, such as the Solid Protocol).
- <dfn id="dfn-authentication">Authentication</dfn>
  means identifying the agent making a request to a Web API.
- <dfn id="dfn-authorization">Authorization</dfn>
  means determining to what extent an agent is allowed
  to perform a certain request to a Web API.

Let us exemplify these definitions with a concrete example.
