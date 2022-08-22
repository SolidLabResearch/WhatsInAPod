## A pod as a collection of Linked Data Documents
{:#ldp}
In this section, we go over the current understanding of the Solid Protocol as defined by the current version of the [Solid Protocol Specification (Version 0.9.0, last edited 2021-12-17)]()

The Solid protocol consists of a variety of specifications.

Linked Data Documents

The current version of the Solid Protocol []() defines the Linked Data Platform specification []() as 

The current version defines URI Slash Semantics for relative referencing.



### Introduction to Linked Data Platform (LDP)
In the current version of the Solid Protocol, the Linked Data Platform specification is used to describes the use of HTTP for accessing, updating, creating and deleting resources from servers that expose their resources as Linked Data. 
Using the resource descriptions provided by the Linked Data Platform interface, an agent can navigate the interface as one would traverse directories and files in a file system. 

### LDP as the read / write interface for Solid
LDP was originally envisioned as a read / write interface for the Solid protocol (SOURCE). 

#### A collection of Linked Data Documents
A consequence of using the Linked Data Platform specification is that it provides an interface for interacting with data through the form of resources on a data pod, the same way that a file system provides an interface for interacting with files on a system. 
Because of the LDP interface, all data stored on the Solid data pod is contained in LDP Resources the granularity with which we can interact with the data stored on a Solid data pod is restricted to operations on a resource. 

The Solid protocol supports HTTP PATCH requests on resources contained in a data pod. A PATCH requests cam add, remove or update data triples within RDF resources on a data pod. 

The Solid protocol provides an extension for LDP Paging (SOURCE). 

### What does an interface of Linked Data Documents make possible


### What are the limitations