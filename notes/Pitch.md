# Swift Docs Repository

## Introduction

Migrate some article content from Swift.org and host them in a seperate repository as DocC catalogs. 

## Motivation

Following along from the [Swift Information Architecture project](https://forums.swift.org/t/swift-high-level-information-architecture/80066), this repository is a potential outcome for the [Documentation focus area](https://forums.swift.org/t/swift-high-level-information-architecture/80066#p-367675-documentation-41).

In particular, to host the source for Swift documentation:

- in a well known location
- provide a single source of truth
- streamlined for community updates 
- support relevant reviewers to maintain technical accuracy

I've taken inspiration from what [Rust language website describes as "Books"](https://www.rust-lang.org/learn).
Collections of in depth content digging into aligned areas, available in a consistent place.
This keeps the content available and discoverable by browsing and skimming, while allowing us to avoid "clogging up" the pages relevant to new-to-Swift users getting started, or presenting an overwhelming amount of information for a new developer.

## Proposed Solution

The repository is intended to host collections of documentation content that aren't aligned with exsting repositories that exist in the [github.com/swiftlang] organization. 
For example, DocC, Swift Package Manager, Swiftly, and others have existing repositories that can host documentation relevant to those tools. 

Each documentation collection hosts content for, and is aligned with, an existing workgroup or steering group.
It's not intended to host content that is aligned with existing swiftlang repositories or tools, or that presents as API reference documentation for a Swift package.

In terms of community updates, I propose to align a DocC catalog (a collection of articles and related media) with an identified workgroup or steering group. 
To provide relevant reviewer control, map each catalog (a directory structure) to a [CODEOWNERS](./CODEOWNERS) file that can be tweaked to provide reviewers from those groups for each catalog.
 
Based on my analysis of the content hosted as articles and pages in swift.org, there are several collections that seem well aligned.

The DocC archives generated from the catalogs can be hosted on docs.swift.org, and referenced at a high level to provide click-through discoverability from swift.org pages.

For content that exists today on swift.org as an article, leverage the Jekyll redirectTo capabilities, updating the front matter of those articles to provide a redirect when the DocC archives are located through a front-end site (swift.org or docs.swift.org) and published with a defined URL.

## Detailed Design

### Catalogs and reviewers

Have a DocC catalog that provides a collection of documentation for each workgroup or steering group with a desire to host one.
These documentation catalogs are meant to be separate from API reference documentation, so in DocC terms - they're "bare" catalogs with only articles, or potentially hosting both articles and tutorials.
Viewed from a "type" of documentation, for example referencing [diátaxis](https://diataxis.fr), the contents are meant to host, [explanation](https://diataxis.fr/explanation/), [tutorials](https://diataxis.fr/tutorials/), and [how-to guides](https://diataxis.fr/how-to-guides/); not [reference](https://diataxis.fr/reference/) content.

Each catalog is expected to be associated by an existing workgroup or steering group.

  - API guidelines - moderated/reviewed by the language steering group.
  - Server guides - moderated/reviewed by the SSWG.
  - C++ Interop Guide - moderated/reviewed by C++ Interop group.
  - Swift Migration guides - moderated by lang/platforms.
  - Embedded Swift - moderated/reviewed by embedded workgroup.
  - Tools Guides - moderated/reviewed by platform & ecosystem.

The workgroup or steering group chooses and provides guidance for who should be included as reviewers for catalogs they "own".
From a mechanical perspective, reviewers are listed in a [CODEOWNERS](../CODEOWNERS) file, leveraging the GitHub groups that Swift provides, or listing GitHub usernames individually.

If, for some reason, a group dissolves, any catalogs can be associated with another group, or revert to direct control by the Swift core team if they prefer.

### Swift Docs Repository Content

Based on my review of existing content in Swift.org, I'd propose the following initial collections:

- API guidelines
  
  - documentation/api-design-guidelines/index.md

- Server guides

  - documentation/server/index.md
  - documentation/server/guides/memory-leaks-and-usage.md
  - documentation/server/guides/packaging.md
  - documentation/server/guides/allocations.md
  - documentation/server/guides/libraries
  - documentation/server/guides/libraries/log-levels.md
  - documentation/server/guides/libraries/concurrency-adoption-guidelines.md
  - documentation/server/guides/testing.md
  - documentation/server/guides/performance.md
  - documentation/server/guides/linux-perf.md
  - documentation/server/guides/deployment.md
  - documentation/server/guides/index.md
  - documentation/server/guides/deploying/heroku.md
  - documentation/server/guides/deploying/ubuntu.md
  - documentation/server/guides/deploying/gcp.md
  - documentation/server/guides/deploying/digital-ocean.md
  - documentation/server/guides/deploying/aws-copilot-fargate-vapor-mongo.md
  - documentation/server/guides/deploying/aws.md
  - documentation/server/guides/deploying/aws-sam-lambda.md
  - documentation/server/guides/building.md
  - documentation/server/guides/llvm-sanitizers.md
  - documentation/server/guides/passkeys.md
  - documentation/articles/static-linux-getting-started.md
    
- Interop Guides

  - documentation/articles/wrapping-c-cpp-library-in-swift.md
  - documentation/cxx-interop/project-build-setup/index.md

- Swift Language Guides

  - possibly seeding this and re-organizing it with content from https://github.com/swiftlang/swift-migration-guide
  - documentation/articles/value-and-reference-types.md
  - migration-guide-swift3/_migration-guide.md
  - migration-guide-swift3/se-0107-migrate.md
  - migration-guide-swift3/index.md
  - migration-guide-swift4/_migration-guide.md
  - migration-guide-swift4/index.md
  - migration-guide-swift4.2/_migration-guide.md
  - migration-guide-swift4.2/index.md
  - migration-guide-swift5/_migration-guide.md
  - migration-guide-swift5/index.md
  - documentation/concurrency/index.md
  - documentation/lldb/_playground-support.md
  - documentation/lldb/index.md

- Tool Guides

  - documentation/articles/zero-to-swift-nvim.md
  - documentation/articles/zero-to-swift-emacs.md
  - documentation/articles/getting-started-with-vscode-swift.md
  
### Existing "standalone" DocC catalogs

The Swift Programming Language:

Content hosted from https://github.com/swiftlang/swift-book/, presented at https://docs.swift.org/swift-book/documentation/the-swift-programming-language/ and linked from swift.org is already well established and likely wouldn't benefit from migrating.
In addition, there are links to translations of that content, hosted at https://www.swift.org/documentation/tspl/, that should absolutely be preserved.

Swift Embedded:

The embedded swift collaborators have assembled a DocC catalog in https://github.com/apple/swift-embedded-examples.
That catalog is closed aligned with Swift code content and projects also in that repository. 
I think it is best to maintain and evolve with the close proximity, rather than breaking the stand-alone content into a separate git repository.

Concurrency Migration Guide:

The content displayed at https://www.swift.org/migration/documentation/migrationguide/ is generated from a standalong DocC catalog in the repository https://github.com/swiftlang/swift-migration-guide.
There are legacy swift language migration guides, for earlier versions of Swift, hosted as articles within swift.org.

I'm uncertain if some allowance to directory structure should be made for example code in a mono-repo style structure such as this. I presumed, like the embedded examples, they were very relevant and should be maintained in sync and proximity. 

## Alternatives Considered

Instead of using a mono-repo layout, create an additional repository per catalog.

This would follow the pattern of what exists today with the repositories https://github.com/apple/swift-migration-guide, https://github.com/apple/swift-embedded-examples, and https://github.com/swiftlang/swift-book/.
Each repository could have it's own set of reviewers and committers, aligned with their relevant workgroup or steering group.

The downside of this scenario is that this would represent a notable growth of repositories, each containing relatively thin content.
The proposed catalogs don't currently have a need to provide examples (or related source code) as a part of what they present.

Because this content doesn't have the constraint of swift packages, which expects a single package per repository, these repositories can be presented more compactly as a mono-repo style configuration.

## Future Directions

I don't have a concrete view for what is warranted to make additional DocC catalogs for, but 
I think there's an good argument for migrating some of the the content in the the Swift repository's [docs](https://github.com/swiftlang/swift/tree/main/docs) directory to provide details about the Swift compiler and how it works.
