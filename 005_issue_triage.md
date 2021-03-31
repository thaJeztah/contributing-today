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

## Issue triage


## Issue triage

- What _is_ triage?
- What procedures do we follow? [issue-triage](https://github.com/moby/moby/blob/master/project/ISSUE-TRIAGE.md)


## What is triage?

- Get the right information
- Find duplicates
- Label issues to make them easier to find
- TL;DR in many cases "adding metadata"


## What procedures do we follow?

- Procedures for issue-triage are described in [issue-triage.md](https://github.com/moby/moby/blob/master/project/ISSUE-TRIAGE.md)


## How to get started?

- Any time!  
  Being a curator starts with "being" one (just like any maintainer)
- Subscribe to the GitHub repository
  - check new issues, and new comments
  - (warning: be prepared to get spammed)
- Go through old issues; see if they need to be followed up
  - issues labeled `status/more-info-needed`


## Examples

- The GitHub issue tracker is not for "support" questions (see our [issue template](https://raw.githubusercontent.com/moby/moby/master/.github/ISSUE_TEMPLATE.md)). If a user arrives on GitHub with a question,
  that's clearly not a "bug" or "feature request";
  - If possible, give some hints, or refer to the correct [location in the documentation](https://github.com/moby/moby/issues/29817#issuecomment-269947478).
  - Point the user to the preferred channels for other type of questions
<br><br>
It generally helps to provide some pointers; perhaps the user's question
is already answered by your reply, and other users arriving on the issue
may benefit from that.


## Examples (2)

- Issues sometimes get opened by mistake [fun fun, GitHub keyboard shortcuts](https://github.com/moby/moby/issues/29812)
  - Leave a note, and close
  - Try to always communicate why you performed an action. It helps reduce "noise" ("why was this closed?")
- Issues can start living a life on their own. Multiple issues start
  to pile up, and there is no clear resolution
  - Summarize the situation, and provide follow up steps for users
    that arrive at the issue (e.g., through Google), after that,
    [lock the issue](https://github.com/moby/moby/issues/1295#issuecomment-269058662)
  - Generally, we try to avoid locking, but sometimes it helps


## Examples (3)

Check if issues are opened in the right issue tracker. It's easy to
be confused, so help users find the right location, for example:

-  Docker for Mac https://github.com/docker/for-mac/issues
-  Docker for Windows https://github.com/docker/for-win/issues
-  Docker CLI https://github.com/docker/cli/issues


## Examples (4)

Getting the right information is important. For example, the output
of `docker version` and `docker info` can provide information about
the _kernel_ someone is running on, and if they're running the official
packages, or a version that's built by [a third party](https://github.com/moby/moby/issues/26862).

- Check if the kernel version matches what's expected (e.g. on RHEL/CentOS, kernel 3.10.x is expected, other versions can result in issues)
- It may be worth asking if they modified their `systemd` unit files
- Logs and reproduction steps are always useful

These steps can be time consuming, and the end result may be that it's
"not a bug"


## Feature requests

There's many ways people use Docker, and we receive a lot of feature
requests.

- Does the feature request benefit just a narrow use case?
- Is it consistent with other features?
- Is it actually something that should be part of Docker's core functionality?
- Look for _use cases_, not _solutions_
