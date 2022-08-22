## Conclusion # {#conclusion}

These insights are crucial to eliminate
the dependency of Solid apps on concrete APIs
and local assumptions about the shape and organization of data
and the resulting performance.


What we fundamentally want is to reduce local assumptions and optimizations in apps for reasons of longevity

I know you allude to this on your latest blogpost, 
but will this approach not create more issues with clients not being able 
to access stored data because of no support for the API when you just allow random APIs?

There needs to be a base layer of course. And some LDP interface can be a good one. But it all starts from realizing that the pod is not an API but a KG, that the API is a means to an end.


Data shape and organization are two facets of data storage that impact how applications can work with data on a Pod.
Certain APIs may provide specific solutions to these question.
Interfaces built upon a Linked Data Platform (view / interface?) of a Solid pod may provide agreed upon organizations for stored data.
On the other hand, interfaces can as well agree upon certain data shapes for given problems.
With this work, we do not propose any specific takeaway as to which interfaces may optimize these problems, but want to provide a framework with which these problems can be tackled in a way that is not restricted to only what the LDP interface allows.
