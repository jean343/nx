# `@nrwl/nx-cloud`

## 14.2.0

- Feat: Add NX_CLOUD_SILENT_RECORD environment variable for use with `nx-cloud record`
- Feat: Add NX_CLOUD_AGENT_TIMEOUT_MS environment variable to configure task timeouts

## 14.1.2

- Fix: Provider nicer failure message when version of Nx is incompatible with @nrwl/nx-cloud
- Fix: Use Nx task graph if provided

## 14.1.1

- Fix: Handle **overrides_unparsed** property for nx:run-commands executor

## 14.1.0

- Fix: Gracefully handle errors with corrupted tarballs
- Fix: Resolve issue where tasks run with read-only DTE would cause 404s on artifact retrieval
- Feat: Allow specifying Nx Cloud installation source through generator

## 14.0.5

- Fix: Workspace name for new Nx Cloud workspaces is pulled from package.json instead of nx.json
- Fix: @nrwl/nx-cloud can be run from directories other than workspace root
- Fix: Correctly infer NX_BRANCH and NX_RUN_GROUP from Jenkins
- Fix: Ignore errors related to excess whitespace in tarballs

## 14.0.3

- Fix: Enable caching for all inner commands

## 14.0.2

- Fix: Remove dependency on @nrwl/devkit for init generator

## 14.0.1

- Fix: Correctly infer NX_BRANCH and NX_RUN_GROUP from Vercel

## 14.0.0

- Feat: Nx 14 Compatibility
- Fix: Exit with status code of child process when recording commands with `nx-cloud record`

## 13.3.1

- Feat: Store output for non-Nx commands in Nx Cloud. Check out https://nx.dev/nx-cloud/set-up/record-commands for more information.

## 13.2.1

- Fix: Newer version of chaulk was required, so the package didn't work with older versions of Nx.
- Feat: Prepare the package to work with Nx 13.10.0

## 13.0.3

Cleanup: Handle issues with the network and the api in a consistent fashion.

## 13.0.1

- Fix: Print detailed errors when an agent is not able to upload file artifacts.

## 13.0.0

- Feat: Support Nx 13.3 new life cycle API

## 12.5.2

- Feat: GitHub Actions handle DTE reruns without requiring `npx nx-cloud start-ci-run`

## 12.5.1

- Fix: DTE main job properly copies files after DTE is finished
- Fix: Increased Node version compatibility for DTE Agents

## 12.5.0

- Fix: Correctly print unexpected exceptions
- Fix: Gracefully handle the case when tasks-hashes are missing
- Fix: Agents should wait for the main job to start a rerun of a run group
- Fix: Retry requests if we receive a 503

## 12.3.13

- Fix: DTE could get stuck when trying to execute tasks with different configurations

# Nx Private Cloud

## 2.4.8

IMPORTANT: The default container mode has changed from COMMUNITY to ENTERPRISE. If you are running a Community version of the container, you will need to make sure the `NX_CLOUD_MODE=private-community` is explicitly set (otherwise your container will fail to start-up).

- Fix: Web app performance improvements
- Fix: issue with Github logged in admins not being able to download logs
- Fix: issue with billing page when multiple access tokens were attached to the same org
- Fix: multiple Mongo DBs used to be created if a default DB was not provided in the connection string. Now it always defaults to the provided `NX_CLOUD_MONGO_DB_NAME§

## 2.4.7

- Misc: performance improvements to DB indexes
- Misc: improvements to hash differ to use regex
- Misc: export more collections for debug purposes (workspaces and organizations)

## 2.4.6

- Fix: issue with navigating to orgs/workspaces in the web app

## 2.4.5

- Feat: filters to branch and run list pages
- Fix: improved MD5 cache artifact archiving
- Misc: various UI and UX improvements to the NxCloud dashboards

## 2.4.4

- Fix: Missing artefact retrieval error when using read-tokens
- Fix: Performance improvements to the branch page and run groups sorting
- Fix: better handling of artefact .tar archiving

## 2.4.3

- Feat: Billing page messaging improvements
- Fix: runs sorting on branch page

## 2.4.2

- Feat: DTE post-run report
- Feat: Hash Detail tool flow improvements

## 2.4.1

- Feat: Admins can now easily export debug info for error investigation
- Fix: branch screen run group sorting

## 2.4.0

- Feat: [GitLab Auth Support](https://nx.app/docs/private-cloud-gitlab-auth)/private-cloud-gitlab-auth
- Feat: Hash diffing tool improvements
- Feat: show message on branch page if workspace is unclaimed
- Fix: Agent out of memory warning
- Feat: cache inner runs
- Fix: include correct github workflows path
- Fix: default to most recent run group on branch page
- Fix: handle DTEs with no tasks
- Fix: await process checkout sessions

## 2.3.1

- Feat: Increase file-server default cached artifact limit. If you are not using an external file storage (such as S3), then the cached assets will now be kept by default from 2 weeks to 4 weeks, increasing the chance of cache hits.
- Feat: "Download cache usage" data from the "Time saved" workspace page

## 2.3.0

- Feat: Github Integration - no token is now necessary in "`nx.json`" for the Github integration to work (you still need to provide as an env var for caching to work). To connect your workspace to Github without an access token in "`nx.json`" just pass in the "`NX_CLOUD_INTEGRATION_DEFAULT_WORKSPACE_ID=<your-workspace-id>`" env var
- Misc: better error handling (report less false positives)
- Fix: Scheduled tasks locking

## 2.2.16

- Misc: DB performance improvements (old records clean-up aggregator, indexes etc.)

## 2.2.15

- Feat: Add options to control database load
- Fix: Better exception handling in the API

## 2.2.14

- Feat: Optimize event processing to increase the throughput of workspaces with a very high number of agents.
- Fix: Gracefully recover when stats aggregation fails

## 2.2.13

- Feat: Hash diffing tool enhancements

## 2.2.12

- Feat: DTE visualisation improvements for larger workspaces
- Fix: billing page not displaying subscriptions for Private Community

## 2.2.11

- Feat: Better error handling for scheduled tasks
- Fix: branch screen not loading

## 2.2.10

- Feat: Various UI improvements to the NxCloud screens
- Feat: Hash detail diff tool
- Feat: GitHub app comment revamp
- Feat: DTE visualisation

## 2.2.9

- Fix: DTE bug fixes caused by incorrectly batched tasks

## 2.2.8

- Fix: various DTE bug fixes
- Feat: Add `NX_CLOUD_DISTRIBUTED_EXECUTION_AGENT_COUNT` env var for more explicitly optimising DTEs
- Feat: Send GitHub workspace membership invites by email
- Fix: improve container start-up time
- Feat: If Mongo connection fails during container start-up it keeps retrying up to a max number of times (configurable via `MONGO_MAX_RETRIES`)
- Feat: expose "/ping" endpoint (can be useful for K8s readinessProbe)
  - `curl --fail http://localhost:8081/nx-cloud/ping --header "authorization: your-nx-cloud-access-token"`
- Feat: billing estimator (on billing page)
- Fix: ignore ending slash on `NX_CLOUD_APP_URL` (in case it's added by mistake)

## 2.2.7

- Feat: `VERBOSE=1` env variable option to output extra information during container initialisation
- Feat: `MONGO_REPAIR=1` env variable option to trigger a [Mongo Repair](https://docs.mongodb.com/manual/tutorial/recover-data-following-unexpected-shutdown/) if the container data gets corrupted

## 2.2.3

- Fix: Reset the memory limits to best work on an instance with 8GB of RAM.
- Fix: Set the default `NX_CLOUD_MODE` to "community".

## 2.2

- [Nx Private Cloud 2.2](https://blog.nrwl.io/%EF%B8%8F-nx-cloud-2-2-%EF%B8%8F-b7656ed5ce7c)

## 2.0

- [Overview of Nx Private Cloud 2.0](https://blog.nrwl.io/introducing-nx-cloud-2-0-f1e5c2002a65)
