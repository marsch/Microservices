# Introduction
**Attendees:** Hansjörg, Selim, Igor, Philipp

## Creation of Code Repository
- Suggestion create a monorepo for all the code of the openintegrationhub.
- Content of current repositories will be transferred to this repository
- Name suggestion for the new repository: `.../openintegrationhub`

- Much easier to create release out of monorepo
- Tools is needed to know which repo has which version at time of release (when not having a monorepo)
- Monorepo useful when using shared libraries

- Defining packages folder for microservices
- Prominent and successful open source repositories used for comparison
  - [Kubernetes](https://github.com/kubernetes/kubernetes)
  - [npm](https://github.com/npm/npm)
  - [nodejs](https://github.com/nodejs/node)
  - [atom](https://github.com/atom/atom)
  - [ruby](https://github.com/ruby/ruby)
  - [lerna monorepo example](https://github.com/jlegrone/lerna-monorepo-example)

### Decision

- A new repository named `openintegrationhub` will be created
- MVP and further (and already existing) code must be published within the new repository
- Unanimously approved by all committer

## Derived Tasks
- [ ] Check which tools should be used for CI **Selim** & **Igor**
- [ ] Create respoitory **Igor**
