# Swift Docs

## Introduction

Prototype / Experiment to re-work the *existing* [documentation content on swift.org](https://github.com/swiftlang/swift-org-website) into a DocC format

## Motivation

Following along from the [Swift Information Architecture project](https://forums.swift.org/t/swift-high-level-information-architecture/80066), this repository is a potential outcome for the [Documentation focus area](https://forums.swift.org/t/swift-high-level-information-architecture/80066#p-367675-documentation-41).

In particular, to host the source for Swift documentation:
- in a well known location
- provide a single source of truth
- streamlined for community updates 
- support relevant reviewers to maintain technical accuracy

For more details, read [the pitch](./notes/Pitch.md) created for this work.

## Preview commands

Use the following commands to build and locally preview the DocC catalogs:


API guidelines:

```bash
xcrun docc preview APIGuides.docc
``` 

Server guides:

```bash
xcrun docc preview APIGuides.docc
``` 

Interop Guides:

```bash
xcrun docc preview InteropGuides.docc
``` 
  
Swift Language Guides:

```bash
xcrun docc preview SwiftLangGuides.docc
``` 

Tool Guides:

```bash
xcrun docc preview ToolGuides.docc
``` 

## Catalog contents - proposed migration plan

- API guidelines
  
  - [ ] documentation/api-design-guidelines/index.md

- Server guides

  - [ ] documentation/server/index.md
  - [ ] documentation/server/guides/memory-leaks-and-usage.md
  - [ ] documentation/server/guides/packaging.md
  - [ ] documentation/server/guides/allocations.md
  - [ ] documentation/server/guides/libraries
  - [ ] documentation/server/guides/libraries/log-levels.md
  - [ ] documentation/server/guides/libraries/concurrency-adoption-guidelines.md
  - [ ] documentation/server/guides/testing.md
  - [ ] documentation/server/guides/performance.md
  - [ ] documentation/server/guides/linux-perf.md
  - [ ] documentation/server/guides/deployment.md
  - [ ] documentation/server/guides/index.md
  - [ ] documentation/server/guides/deploying/heroku.md
  - [ ] documentation/server/guides/deploying/ubuntu.md
  - [ ] documentation/server/guides/deploying/gcp.md
  - [ ] documentation/server/guides/deploying/digital-ocean.md
  - [ ] documentation/server/guides/deploying/aws-copilot-fargate-vapor-mongo.md
  - [ ] documentation/server/guides/deploying/aws.md
  - [ ] documentation/server/guides/deploying/aws-sam-lambda.md
  - [ ] documentation/server/guides/building.md
  - [ ] documentation/server/guides/llvm-sanitizers.md
  - [ ] documentation/server/guides/passkeys.md
  - [ ] documentation/articles/static-linux-getting-started.md
    
- Interop Guides

  - [x] documentation/articles/wrapping-c-cpp-library-in-swift.md
  - [x] documentation/cxx-interop/project-build-setup/index.md
  - [x] documentation/cxx-interop/status/index.md
  - [x] documentation/cxx-interop/index.md
  
- Swift Language Guides

  - possibly seeding this and re-organizing it with content from https://github.com/swiftlang/swift-migration-guide
  - [ ] documentation/articles/value-and-reference-types.md
  - [ ] migration-guide-swift3/_migration-guide.md
  - [ ] migration-guide-swift3/se-0107-migrate.md
  - [ ] migration-guide-swift3/index.md
  - [ ] migration-guide-swift4/_migration-guide.md
  - [ ] migration-guide-swift4/index.md
  - [ ] migration-guide-swift4.2/_migration-guide.md
  - [ ] migration-guide-swift4.2/index.md
  - [ ] migration-guide-swift5/_migration-guide.md
  - [ ] migration-guide-swift5/index.md
  - [ ] documentation/concurrency/index.md
  - [ ] documentation/lldb/_playground-support.md
  - [ ] documentation/lldb/index.md

- Tool Guides

  - [ ] documentation/articles/zero-to-swift-nvim.md
  - [ ] documentation/articles/zero-to-swift-emacs.md
  - [ ] documentation/articles/getting-started-with-vscode-swift.md

### Background on swift.org content structure

[Swift.org](https://www.swift.org) is primarily backed by a Jekyll template structure.
Using the existing [sitemap.xml](https://www.swift.org/sitemap.xml) to map the site, I broke up the list of URLs into categories:

- [Core and Security](./notes/CoreSecurity.md) 
- [API Endpoints](./notes/APIEndpoints.md)
- [Packages](./notes/Packages.md)
- [Workgroups](./notes/Workgroups.md)
- [Installation](./notes/Installation.md)
- [Getting Started](./notes/GettingStarted.md)
- [Documentation](./notes/Documentation.md)

The content of this repository focuses on [Documentation](./notes/Documentation.md).
