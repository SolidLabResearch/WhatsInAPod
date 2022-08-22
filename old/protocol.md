## The Solid Protocol



### Necessity



### Optimization


### Consequences

#### Implicit trust.
Data stored on the Solid pod in its current implementation requires on the data consumer trusting the origin of the consumer data. This will most likely in its current form mimic the way applications on a personal computer trust data, by reading data written by the application itself, of by prompting the user to select a data source that is trusted by the user (e.g. select the file you wish to read the data from, ...). This form of implicit trust is usable if you have sole control over a data space, but becomes obsolete in a system where the goal is the sharing of data.

Currently there are researches into the topic of blockchains for data trust (CITE), But this may provide a scaling issue (SOURCE???) if all different kinds of data have to be trusted, and requires monetary compensation (in most cases?? source??). 

If we look at the data pod as a knowledge graph published over a SPARQL endpoint, one of the first big problems that arise is that we lose this implicit trust in the read data, as we do not have any context of what data originates from which source.

As a quick pracitcal example might be a case where some application asks for a name. Say you are uncomfortable with this, and create a different name for this application specifically. Now the knowledge graph of your data pod has two different names. Applications using your data pod now need a way to discern these two conflicting data points. An example implementation of this might be showing the available names, and the application that originally wrote this data, so the user can quickly decide the name they want to use, and where the other data points originate from. Or the user may blacklist certain data sources from showing up. Or many other practical implementations of this can be thought of. 
