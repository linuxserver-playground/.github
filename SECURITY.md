# Security policy

## Scope

Everything in the `linuxserver-playground` organisation is a proof of concept of a GitHub-native
LinuxServer.io build system. The container images published under `ghcr.io/linuxserver-playground/`
are **unsupported and not for production use**. They may be rebuilt, retagged or deleted without
notice, and images under `dev/` and `untrusted-pr/` are unreviewed by definition. For images you can
rely on, use the ones published by [LinuxServer.io](https://github.com/linuxserver).

## Reporting a vulnerability

* **A problem in the playground itself** (the shared workflow, the control plane, the hub, the builder,
  the ci harness, an image's init scripts, a leaked credential): open a
  [private vulnerability report](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)
  on the affected repository, or if that is not enabled, contact a maintainer on
  [Discord](https://linuxserver.io/discord) rather than opening a public issue.
* **A vulnerability in an upstream application or a distro package** inside an image: report it upstream.
  Images are rebuilt regularly to pull in distro fixes; scanner output listing CVEs in upstream or distro
  packages is not actionable here and will be closed if filed as an issue.
* **A problem in a LinuxServer.io production image**: follow the
  [LinuxServer.io](https://github.com/linuxserver) repository's own security policy, not this one.

Please include the image name and tag (`<upstream>-ls<N>`), the architecture, how to reproduce, and
what the impact is. Do not include secrets in the report.

## What to expect

This is a volunteer-run experiment with no SLA. Reports are read; fixes land when someone has time.
