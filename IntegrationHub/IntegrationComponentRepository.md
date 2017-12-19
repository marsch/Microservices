# Integration Component Repository

The integration components are lightweight and stand-alone Docker images that include everything needed to run the
component, including the component's code, a runtime, libraries and dependencies. Each component is based on an OIH
[parent image](https://docs.docker.com/engine/userguide/eng-image/baseimages/) which provides the component runtime.
For example, for Java component the parent images provides the JDK and for Node.js component the parent image provides
[NPM](https://www.npmjs.com/) and [Node.js](https://nodejs.org).

The component images are stored in a [Docker Registry](https://docs.docker.com/registry/). A Docker Registry is a
stateless, highly scalable storage for Docker images. Any open source integration component can be store and
distributed in/from [Docker Cloud](https://cloud.docker.com) so that they would be available to any OIH installations
(cloud or on-prem) out of the box. For `private` components private Docker Registry can be maintained locally so that
no components are exposed to the cloud. Each on prem installation could decide whether to use private repos on Docker
Cloud or installing a private Docker Registry on prem for their private components.