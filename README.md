# gamma-driver

Gamma-Driver is a library for driving the WebGL API: installing shaders, setting up buffers, issuing draw commands, etc. It ships with a driver that greatly simpifies the majority of common use cases, and also allows for increased composition of and reasoning about resources. Because customized needs inevitably arise, it also offers a set of pragmatic mechanisms for creating customized drivers that embody additional semantics or optimizations.

Gamma-Driver is suitable both for beginners looking to get up and running quickly, and by experts needing to implement specialized needs and optimizations. 

Benefits:
 - reduce boilerplate, incidental complexity 
 - decouple graphics pipeline from state & resource managment strategies
 
WIP. API design still being assessed. 

# getting new semantics without breaking the world

Graphics drivers contend with two issues: the complexity of resource managment, and the complexity of API migration due to changes in resource capabilities and demand for new abstractions. 

Gamma-Driver solves these problems by providing an operational interface whose arguments are data representations. In other words, there are a set of interfaces (protocols in Clojure) for operations like creating a WebGL buffer or texture, but the interface's arguments and return values are data descriptions of the resource, not necessarily the resource itself. So to create a buffer, you pass a description of the buffer (a clojure map) you want to create, and get back a description of what was created (another clojure map).

This design allows extensibility of the API through a generic data representation. Adding new semantics entails adding a key to the representation, and swapping out to a driver that implements the those sematics in the way it implements the interface. It also allows for reasoning and manipulation of the type necessary for optimizing resource allocation. 


