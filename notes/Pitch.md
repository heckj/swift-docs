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

### Swift Docs Repository Content

Based on my review of existing content in Swift.org, I'd propose the following initial collections:

  - API guidelines (moderated/reviewed by the language steering group)
  
  - Server guides (moderated/reviewed by the SSWG)
    - everything under `server/guides`
    - static linux getting started
    
  - C++ Interop Guide (moderated/reviewed by C++ Interop group)
    - wrapping c-cpp library article
    
  - Swift Migration guides (moderated by lang steering group)
    - concurrency migration guide in https://github.com/apple/swift-migration-guide
    - older guides as articles in https://github.com/swiftlang/swift-org-website/ in `migration-guide-*` dirs
    
  - Tools Guides (moderated/reviewed by platform steering group)
    - zero to swift nvim
    - zero to swift emacs
    - getting started with vscode swift

### Existing "standalone" DocC catalogs

The Swift Programming Language:

Content hosted from https://github.com/swiftlang/swift-book/, presented at https://docs.swift.org/swift-book/documentation/the-swift-programming-language/ and linked from swift.org is already well established and likely wouldn't benefit from migrating.
In addition, there are links to translations of that content, hosted at https://www.swift.org/documentation/tspl/, that should absolutely be preserved.

Swift Embedded:

The embedded swift collaborators have assembled a DocC catalog in https://github.com/apple/swift-embedded-examples.
That catalog is closed aligned with Swift code content and projects also in that repository. 
I think it is best to maintain and evolve with the close proximity, rather than breaking the stand-alone content into a separate git repository.

Concurrency Migration Guide:

The content displayed at https://www.swift.org/migration/documentation/migrationguide/ is generated from a standalong DocC catalog in the repository https://github.com/apple/swift-migration-guide.
There are legacy swift language migration guides, for earlier versions of Swift, hosted as articles within swift.org.

I'm uncertain if some allowance to directory structure should be made for example code in a mono-repo style structure such as this. I presumed, like the embedded examples, they were very relevant and should be maintained in sync and proximity. 

## Alternatives Considered

Creating an additional repository per catalog.

This would follow the pattern of what exists today with the repositories https://github.com/apple/swift-migration-guide, https://github.com/apple/swift-embedded-examples, and https://github.com/swiftlang/swift-book/.
Each repository could have it's own set of reviewers and committers, aligned with their relevant workgroup or steering group.

The downside of this scenario is that this would represent a notable growth of repositories, each containing relatively thin content.
The proposed catalogs don't currently have a need to provide examples (or related source code) as a part of what they present.

Because this content doesn't have the constraint of swift packages, which expects a single package per repository, these repositories can be presented more compactly as a mono-repo style configuration.

## Future Directions

I don't have a concrete view for what is warranted to make additional DocC catalogs for, but 
I think there's an good argument for migrating some of the the content in the the Swift repository's [docs](https://github.com/swiftlang/swift/tree/main/docs) directory to provide details about the Swift compiler and how it works.
