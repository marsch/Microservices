# Introduction
**Attendees:** Hansjörg, Selim, Igor, Philipp, Franz, Susanne, Dennis <br>
**Absent:** -


# DevelopmentPlan
- Partner overwhelming backlog should be filled with 8.8
  - Igor is on vacation next week
  - Hansjörg is on vacation next two weeks


# Basaas
## SecureKeyManagement
- Evaluation of Hashicrop Vault is ongoing
- Analysis how to work with vault
- Decision for usage of Vault is still open

## IAM
- Work on expanding IAM middleware
- Rework on service accounts

# SharedNpmModules
- Within monorepo or within seperated repositories?
- Suggestion: Define a location for sharedModules within monorepo
  - Create GitHub Issue for this topic

# Wice
## ConnectionIAMandICR
- Working local version that will be published in the near future

# Elasticio
## Monorepo
- Built an internal prototype for a monorepo to practice the usage of monorepos
- CircleCI is very useful to track changes via diffs
- Lerna is restriced to npm modules and is therefore not sufficient because we want to build docker images
- Internal prototype is able to build monorepo and is able to get dependent npm modules

- Lerna in combination with yarn is possible to also cover docker images

## Derived Tasks
- [ ] Create Issue for _sharedNpmModules_ topic **Selim**
- [ ] Expand documentation of mvp within monorepo **Igor**
- [ ] Fill github monorepo backlog with open issues **Hansjörg**
- [ ] Fill github monorepo backlog with open issues **Igor**
- [ ] Fill github monorepo backlog with open issues **Selim**
