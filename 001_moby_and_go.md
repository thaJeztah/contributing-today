<!--
Copyright 2021 Sebastiaan van Stijn

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
-->

## Go at Docker and the Moby project

Contributing Today, March 31, 2021
<br /><br />
*Sebastiaan van Stijn*
**@thaJeztah** on GitHub, Twitter, and Slack


## About me

- PHP developer in a former life 👴🏻
- Contributor to Docker since 2013 (version 0.5)
- Moby and Docker open source maintainer 🐳
- Reviewer for the containerd projects
- .. and any other repository I get my hands on 😅
- Senior Software Engineer at Docker (since 2015)


## What is the Moby project?

- Upstream open source projects for Docker
- The "docker engine" [github.com/moby/moby](https://github.com/moby/moby)
- BuildKit (also used to drive `docker build`) [github.com/moby/buildkit](https://github.com/moby/buildkit)
- Various other libraries and projects


## A history of Go in Moby and Docker

- Originally written in Python
- Early adopter, means "rough edges"
- Building Go from source
- Stability not a guarantee yet, and due to our use, we usually found
  "interesting" corner cases with each release.
- No dependency management or vendoring (DYI)


## Why Go?

- Static binaries meant we could ship fast and often (less important now)
- Extensive set of tools out of the box (test framework, `go fmt`, dependency management)
- Basics are easy to learn, making it easy to contribute
- Opinionated (`go fmt`) helps for a consistent codebase with many contributors
- Huge time-saver when dealing with many contributors
- Cross platform (because Docker would likely never run on Windows 😅)


## Dependency management

(in a fast-moving landscape)<br /><br />

- Dependency management can be hard. Go modules _can_ make life easier, but there are pitfalls
- A single line of code can cause [a ripple effect on your dependency tree](https://github.com/microsoft/hcsshim/pull/984)
- If `go mod why` doesn't help, `go mod graph` can come to the rescue
  
  For a quick search who's "asking" for a dependency:<br />
  ```
  go mod graph | grep ' k8s.io/kubernetes'
  # github.com/Microsoft/hcsshim@v0.8.7 k8s.io/kubernetes@v1.13.0
  ```
  <br />(note the space before the dependency)<br /><br />


## Review your dependencies

- Dependencies are "your code" as well; don't be tricked by go modules "hiding them" for you: review changes in your dependencies, and
- ["tagged"](https://pkg.go.dev/github.com/thaJeztah/mod@v0.2.0) isn't [always "tagged"](https://github.com/thaJeztah/mod/tags)
- Beware of [**replace** rules](https://github.com/containerd/containerd/blob/v1.5.0-beta.4/go.mod#L68-L75); they are non-transitional!
- SemVer is really _hard_: a projects "minor" change may be a breaking change for you (_hopefully_ apparent immediately)


## Maintain a project?

- Set expectations right; describe things such as:
    - Scope of your project
    - Stability
    - What parts are intended for "external consumption"?
- Go makes it easy to use someone else's (your) code
- Maintaining a library? Use Aliases and `//Deprecated` comments if needed (but strictly, deprecations require a Major release)


## Don't forget the legal stuff

- Pick the right license and [apply it the correct way](https://github.com/kubernetes/kubernetes/commit/d30db1f9a915aa95402e1190461469a1889d92be)
- Accepting contributions? [Who owns the copyright?](https://github.com/kubernetes/kubernetes/blob/9b8247e5ddb15f3fb9ffe59871172d9a3268af55/cmd/clicheck/check_cli_conventions.go#L2)
- Perhaps you need a CLA, or [require a DCO](https://developercertificate.org) (and a [DCO check](https://github.com/apps/dco))
