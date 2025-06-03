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

## Proposed Solution

This repository is intended to host collections of documentation content that aren't aligned with exsting repositories that exist in the [github.com/swiftlang] organization. 
For example, DocC, Swift Package Manager, Swiftly, and others have existing repositories that can host documentation relevant to those tools. 

I propose this repository hosts content for a workgroup or steering group that isn't aligned with either an existing repository or that maps to a Swift package as API reference documentation.
Based on my analysis of the content hosted as articles and pages in swift.org, there are several collections that seem well aligned.

Content that's already in external repositories - such as the [Swift concurrency migration guide](https://github.com/apple/swift-migration-guide) or the [swift-embedded-examples content](https://github.com/apple/swift-embedded-examples) - could migrate into this repository if that's convenient, or continue to exist seperately.
Both of those repositories host additional code, and especially in the case of swift-embedded-examples, I suspect keeping their Swift code content and related guides together would have notable benefits when updating.

Within this repository, I propose to align a DocC catalog (a collection of articles and related media) with an identified workgroup or steering group. 
To provide relevant reviewer control, map each catalog (a directory structure) to a [CODEOWNERS](./CODEOWNERS) file that can be tweaked to provide reviewers from those groups for each catalog.
 
What is the plan to not break links to existing content when moved to DocC?



### Swift Docs Repository Content

- Guides - one for each workgroup or steering group that wants to provide them, examples:
  - API guidelines (moderated/reviewed by the language steering group)
  - Server guides (moderated/reviewed by the SSWG)
    - everything under `server/guides`
    - static linux getting started
  - C++ Interop Guide (moderated/reviewed by C++ Interop group)
    - wrapping c-cpp library article
  - Swift Migration guides (moderated by lang/platforms)
    - concurrency migration guide in https://github.com/apple/swift-migration-guide
    - older guides as articles in https://github.com/swiftlang/swift-org-website/ in `migration-guide-*` dirs
  - Embedded Swift (moderated/reviewed by embedded workgroup)
    - currently in https://github.com/apple/swift-embedded-examples
  - Tools Guides (moderated/reviewed by platform & ecosystem)
    - zero to swift nvim
    - zero to swift emacs
    - getting started with vscode swift

I don't have a concrete view for what is warranted to make additional DocC catalogs for, but 
I think there's an good possible argument for the content in the Swift repo's userdocs.
In additional, each of the tools that are included in the toolchain could easily have their own
sets of documentation, although likely hosted in the repositories associated with those tools.

- Swift Language
  - The Swift Programming Language (TSPL - moderated by Doc Workgroup)
  - The standard library -> DocC catalog of the std library
  - (Core Libraries)
    - Foundation  (moderated by Foundation workgroup)
    - Swift Testing (moderated/reviewed by swift testing)

- Swift Toolchain 
  - swift diagnostic messages
  - package manager docs
  - repl and debugger docs
  - docc

## Alternatives Considered

### Existing documentation already in DocC catalog format

- https://www.swift.org/documentation/tspl (documentation workgroup)
- https://docs.swift.org/swift-book/documentation/the-swift-programming-language/
- https://www.swift.org/documentation/docc/ (docc documentation)

- swift compiler diagnostics (swift language steering group)

- swiftly (ecosystem steering group)
- vscode-extension (ecosystem steering group)
- package manager (ecosystem steering group)

- swift embedded examples (embedded steering group - platforms?)


### Background and existing swift.org structure

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
