# Metabase business intelligence

Analytics application with a Clojure backend and a TypeScript/React frontend, supporting database queries, dashboards, and embedding.

This repository is a separately imported source snapshot of [metabase](https://github.com/metabase/metabase). Upstream contributors created the imported application; local work is recorded in the commits after the source import. See [Upstream source](UPSTREAM_SOURCE.md) for attribution.

## Read the history accurately

The local history starts with a source import on November 3, 2026. The parent year directory and the “Original project year” field do not establish a historical contribution date or a release tag. The imported upstream commit and release are not recorded in the available provenance file.

## Navigate the source

| Path | Responsibility |
| --- | --- |
| [src/](src/) | Clojure backend namespaces |
| [frontend/](frontend/) | Client application and frontend guidance |
| [test/](test/) | Backend tests |
| [enterprise/](enterprise/) | Separately licensed enterprise components |
| [docs/](docs/) | Product and developer documentation |

## Prepare development

Read `AGENTS.md`, `deps.edn`, `mise.toml`, and `package.json` before installing dependencies. The JavaScript package manager is pinned in `package.json`; backend tests use the repository test wrapper. Consult the developer guides under `docs/` for database and JVM setup.

The commands below are existing project entry points, to run after their toolchain, dependency, and service prerequisites are ready:

```sh
bun run build
./bin/test-agent :only '[metabase.session.core-test]'
```

## Validation scope

The documentation change was checked for local link targets, manifest command references, and whitespace errors. Application builds, dependency installation, and service-backed test suites were not run for this documentation change. These instructions do not establish deployment readiness.

## Preserve upstream licensing

Read [LICENSE-AGPL.txt](LICENSE-AGPL.txt), [LICENSE-EMBEDDING.txt](LICENSE-EMBEDDING.txt), [LICENSE-MCL.txt](LICENSE-MCL.txt), [LICENSE.txt](LICENSE.txt) and the notices in individual source files. This documentation does not change the license of imported code.

The `enterprise/` subtree has commercial terms; [Enterprise license](enterprise/LICENSE.txt) does not grant use merely by source access. Publication of this imported snapshot is held pending verification of redistribution rights.

## Install and run locally

Match the runtimes in `mise.toml` and `package.json`, including the JVM/Clojure tooling, then install the locked JavaScript dependencies and launch the development entry point:

```sh
bun install --frozen-lockfile
bun run dev
```

The development command starts the backend and frontend compilation processes. Use `config.yml.sample` and `.env.example` to choose local configuration values; do not put real database credentials in committed files. Backend dependency resolution and frontend builds require network access on first use.

## Plan a deployment

`Dockerfile` describes the container build. Keep the application database persistent and separate from queried analytics databases. The `enterprise/` tree and embedding components carry additional license terms; verify redistribution rights before building or publishing an image containing them. The imported source revision remains unknown.
