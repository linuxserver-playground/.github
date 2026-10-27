# LinuxServer.io v2 playground

This organisation is a proof of concept of a GitHub-native [LinuxServer.io](https://linuxserver.io):
what the project would look like with no Jenkins, no per-repo pipeline files and no hand-maintained
README. Each container image lives in a thin `docker-<name>` repository that holds two Dockerfiles, a
`root/` tree and one manifest, `image.yml`. Everything else in an image repo is generated from that
manifest. One shared GitHub Actions workflow builds, tests and releases every image, attaching a
machine-readable bundle to each GitHub Release. A hub ingests those bundles and generates every
downstream artefact (docs pages, store templates, proxy confs). A public control plane schedules builds
and shows the whole fleet at [ci.thelamer.duckdns.org:8443](https://ci.thelamer.duckdns.org:8443).

The written contract behind all of it is
[`CONVENTIONS.md`](https://github.com/linuxserver-playground/builder/blob/main/CONVENTIONS.md) in the
`builder` repository, with JSON Schemas as the machine-checkable half. Contributions follow
[`CONTRIBUTING.md`](https://github.com/linuxserver-playground/.github/blob/main/CONTRIBUTING.md), and
every repository carries an `AGENTS.md` for the AI coding agents and the humans driving them.

**Want to help?** LinuxServer.io needs people more than money. The
[Contribute page](https://linuxserver-playground.github.io/site/contribute/) shows the ways in, and the
[harness](https://github.com/linuxserver-playground/harness) gives your AI coding agent everything it needs to
know, so you can fix an image, make a mod or propose an app without learning the whole system first.

> **Not for production use.** Images published under `ghcr.io/linuxserver-playground/` are experimental
> and unsupported. They can be rebuilt, retagged or deleted at any time. Anything under `dev/` or
> `untrusted-pr/` is unreviewed. For images you can rely on, use the ones published by
> [LinuxServer.io](https://github.com/linuxserver).

## Repositories

| Repo | What it is |
| --- | --- |
| [harness](https://github.com/linuxserver-playground/harness) | **Start here:** clone it and start your AI coding agent at its root. It works out whether you are on the team or contributing from outside, maps every repo, reads the live fleet, tests in your local Docker and drafts the issue, PR or review for you to file. |
| [builder](https://github.com/linuxserver-playground/builder) | The contracts (`CONVENTIONS.md`, `schemas/`), the `image.yml` validator and renderer, and the AGENTS.md templates. |
| [workflows](https://github.com/linuxserver-playground/workflows) | The reusable GitHub Actions workflows and composite actions every image repo calls at `v1`. |
| [ci](https://github.com/linuxserver-playground/ci) | The container test harness that runs each built image and emits the release bundle. |
| [hub](https://github.com/linuxserver-playground/hub) | Ingests release bundles, keeps the fleet data and generates docs pages, stores, proxy confs and the mods index. |
| [control](https://github.com/linuxserver-playground/control) | The GitHub App, scheduler, notifications and public dashboard for the whole fleet. |
| [docker-sonarr](https://github.com/linuxserver-playground/docker-sonarr) | Sonarr, the first image ported to the one-manifest layout. |
| [docker-swag](https://github.com/linuxserver-playground/docker-swag) | SWAG, the nginx reverse proxy with certbot, ported to the one-manifest layout. |
| [.github](https://github.com/linuxserver-playground/.github) | This repository: org-wide issue forms, PR template, contributing guide and security policy. |

Questions go to [Discussions](https://github.com/orgs/linuxserver-playground/discussions) or
[Discord](https://linuxserver.io/discord).
