## Preliminary definitions # {#definitions}

Before describing the interpretations of a Solid pod,
we start with a couple of definitions that we will use as building blocks
throughout the article.

- We consider a <dfn id="dfn-protocol">protocol</dfn> to be
  a generic set of rules for data transmission between systems.
  - The [<dfn id="dfn-http">HyperText Transfer Protocol (HTTP)</dfn>](cite:citesAsAuthority HTTP)
    structures the exchange of data between a server and a client
    as _resources_ identified by a URI.
  - The [<dfn id="dfn-ldp">Linked Data Platform (LDP)</dfn>](cite:citesAsAuthority LDP)
    constrains HTTP with interaction rules
    for recursive containers of RDF and non-RDF documents.
  - The [<dfn id="dfn-solid-protocol">Solid Protocol</dfn>](cite:citesAsAuthority Solid_protocol)
    constrains HTTP with _authentication_ and _authorization_,
    and with interaction rules
    for recursive containers of RDF and non-RDF documents
    (inspired by LDP).
- A <dfn id="dfn-web-api">Web API</dfn> is a specific structuring of resources
  on top of HTTP (or a specialization thereof, such as the Solid Protocol).
- <dfn id="dfn-authentication">Authentication</dfn>
  means identifying the agent issuing a request to a Web API.
  - The [<dfn id="dfn-webid">WebID</dfn>](cite:citesAsAuthority Solid_OIDC)
    is an HTTP URL that identifies an agent.
    When dereferenced,
    it leads to a <dfn id="dfn-profile-document">profile document</dfn>
    describing various agent details.
  - [<dfn id="dfn-solid-oidc">Solid-OIDC</dfn>](cite:citesAsAuthority Solid_OIDC)
    establishes some authoritative identification of an agent by a specific WebID.
- <dfn id="dfn-authorization">Authorization</dfn>
  means determining to what extent a server can respond
  to a certain Web API request from a specific agent.
  - [<dfn id="dfn-wac">Web Access Control (WAC)</dfn>](cite:citesAsAuthority WAC)
    is an Access Control List (ACL) mechanism
    that allows assigning inheritable permissions to documents and containers
    through so-called _ACL documents_.
  - [<dfn id="dfn-acp">Access Control Policies (ACP)</dfn>](cite:citesAsAuthority ACP)
    is a policy-based mechanism
    that allows assigning inheritable permissions to documents and containers
    through so-called _Access Control Resources (ACR)_.

Let us exemplify some of these definitions through our use cases:

- An HTTP interface at `https://sasha.pod/` implements the Solid Protocol
  when its containers and documents follow the interaction rules,
  and when it correctly authenticates users using their WebID
  and applies authorization to each resource.
- A Web API within `https://sasha.pod/` structures documents in containers.
  - Contacts are stored in `https://sasha.pod/people/`
  as individual documents:
    - `https://sasha.pod/people/sasha.ttl`
    - `https://sasha.pod/people/lucian.ttl`
  - Medical records are stored in `https://sasha.pod/private/acme-hospital/`
  by date, such as:
    - `https://sasha.pod/private/acme-hospital/2022/10/15/test-results.ttl`
- The WebID `https://sasha.pod/people/sasha#me` identifies a person named Sasha.
- The agent identified by `https://sasha.pod/people/sasha#me`
  is allowed to access all documents on `https://sasha.pod/`.
