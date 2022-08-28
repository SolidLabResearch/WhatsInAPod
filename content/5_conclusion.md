## Conclusion # {#conclusion}
<!-- With this work, we propose perspective of Solid as ...  -->
With this work, we propose the perspective of Solid as a platform serving data Pods that provide sufficient views on the data available to the entity interacting with the pod that it can be organized as a permissioned knowledge graph.
{:.comment .reference.needed data-author="RD"}

{:.comment data-author="RD"}
Be sure to adapt this to the final expression we come up with


<!-- Argue this perspective in itself does not solve the existing difficulties in interoperability  -->
The perspective proposed in this work does not in itself provide a solution for the difficulties faced for the Solid ecosystem to provide the separation of applications and data.
But we argue that this perspective is necessary for solutions to be created that promote longevity in their approach to achieve this separation and provide an ecosystem centered around the concept of data-integration.

<!-- Make case that LDP limits the innovation surface for Solid -->
We argue that the current choice for the Linked Data Platform specification as the de facto interface for managing with data in a Solid pod requires developers to make localized assumptions and optimizations in applications in cases where the imposed structure of the interface do not match the real world.
<!-- Where LDP can promote assumptions over the API -> we need to get these assumptions in the data as semantics  -->
Where the LDP interface can promote the custom of encoding assumptions about data in the bundling of data in resources and the structuring of these resources on the pod, as if they are coding against a file system, we pose that this goes contrary to the development of an interactive ecosystem of applications and data.
Using the proposed perspective, we hope to provide a framework that may lead to improvements in how these assumptions can be encoded in the semantics of the stored data.

Maybe this should be worded a bit different?
{:.comment data-author="RD"}

<!-- The perspective continues from the current state of solid and is completely compatible with the current state -->
We note that the proposed perspective does not go against the current state and use of Solid, but must be seen as a zoomed out attempt at providing a good framing for the issues that are being encountered working on the ecosystem.
<!-- The goal of this work is to provide a perspective on the identity of Solid that can help in future work on the topic -->
We do not propose any specific takeaway as to which interfaces may provide solutions for faced difficulties, but we hope that the provided perspective can focus the discussions on the topic in a frame that allows for a way to tackle difficulties in a way that is not restricted by a specific interface on the data.






<!-- -------------------

The insights proposed in this work are crucial to eliminate 
the dependency of Solid apps on concrete APIs.
Local assumptions about the shape and organization of data creating localized APIs for applications over the Linked Data Platform interface exposed by Solid data pods provide local optimizations for data discovery, querying performance and more, but hurt the ecosystem as a whole, as assumptions and biases in the organization and discovery of data are not shared across the ecosystem.

The framing of Solid pods as a Knowledge Graph exposed over a multitude of APIs contrary to a data source organized using the Linked Data Platform specification enables us to think more about 
with the goal of reducing local assumptions and optimizations in apps for reasons of longevity. The API over which data is exposed over the Web is a means to an end, and should not define the platform. -->
