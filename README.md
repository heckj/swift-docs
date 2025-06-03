Prototype / Experiment to re-work the *existing* [documentation content on swift.org](https://github.com/swiftlang/swift-org-website) into a DocC format

[Swift.org](https://www.swift.org) is primarily backed by a Jekyll template structure.
Using the existing [sitemap.xml](https://www.swift.org/sitemap.xml) to map the site, I broke the URLs down into a variety of categories:

- [Core and Security](./notes/CoreSecurity.md) 
- [API Endpoints](./notes/APIEndpoints.md)
- [Packages](./notes/Packages.md)
- [Workgroups](./notes/Workgroups.md)
- [Installation](./notes/Installation.md)
- [Getting Started](./notes/GettingStarted.md)
- [Documentation](./notes/Documentation.md)

Of this, I want to focus on URLs from [Documentation](./notes/Documentation.md).

My ideal state is Swift Documentation -> 

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

Tooling docs in DocC catalogs:

https://www.swift.org/documentation/tspl (documentation workgroup)
https://docs.swift.org/swift-book/documentation/the-swift-programming-language/
https://www.swift.org/documentation/docc/ (docc documentation)

swift compiler diagnostics (swift language steering group)

swiftly (ecosystem steering group)
vscode-extension (ecosystem steering group)
package manager (ecosystem steering group)

swift embedded examples (embedded steering group - platforms?)

