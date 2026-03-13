---
description: >-
  A run-down of the files and tools used in the backend part of the new
  remote-capable architecture.
---

# Backend - Server

## Base Server (NodeJS/Express)

A lot of logic and files have been moved to the `"/backend"`  folder to facilitate them running remotely, especially when they use local file management logic or start servers for example.

The **Express** server acts as the entry point for managing and keeping all other servers in check. It can be located in the `backend/ExpressServer.mjs` file, which contains its start up logic as well as its [endpoints for requests](express-request-endpoints.md).

## CLI / Headless control

In the `cli` folder, the `medomics-server.mjs` file allows for usage of the Express server in remote deployments through command line, which the client uses to start and stop a remote backend. It surfaces the start, status, ensure, install and stop server commands and helps manage the state of the backend process.

| Command | Main Purpose                                                  | Preconditions                                                      | Internal Actions                                                                                                                                    | Backend Endpoint Calls                                                                                                                      | State/Files Changed                                    | Success Output                                | Failure/Exit Behavior                                                              |
| ------- | ------------------------------------------------------------- | ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ | --------------------------------------------- | ---------------------------------------------------------------------------------- |
| start   | Launch Express backend child process and record runtime state | Express entrypoint path must resolve and exist                     | Resolves backend path, writes starting placeholder state, forks child, tails stdout/stderr, waits for EXPRESS\_PORT IPC message, sets running state | None directly; child backend starts itself                                                                                                  | Writes state file and server-child.log under state dir | JSON line with success true and expressPort   | Exits non-zero if path missing, child exits early, or startup timeout              |
| status  | Query current backend status snapshot                         | State file must exist and include expressPort                      | Reads state file, performs HTTP GET to backend status route                                                                                         | GET /status                                                                                                                                 | No writes on normal path                               | JSON with pid, expressPort, status payload    | Exits non-zero if state missing or HTTP status query fails                         |
| ensure  | Idempotently ensure selected services are up                  | State file must contain expressPort; flags indicate which services | Reads state, conditionally calls service ensure endpoints                                                                                           | POST /ensure-go, POST /ensure-mongo, POST /ensure-jupyter                                                                                   | No direct state-file updates in CLI                    | JSON with ensured object per selected service | Exits non-zero if state missing or any ensure call throws                          |
| install | Install missing runtime requirements via backend API          | Express must be running or start-able                              | Auto-starts if needed, checks requirements, conditionally installs Mongo/Python env/Python packages using heuristics, re-checks requirements        | GET /check-requirements, POST /install-mongo, POST /install-bundled-python, POST /install-required-python-packages, GET /check-requirements | May update state if it auto-starts first               | JSON summary with initial, actions, final     | Exits non-zero on any check/install step failure                                   |
| stop    | Stop backend process recorded in state file                   | State file with pid                                                | Checks pid alive, sends SIGTERM, waits, escalates SIGKILL on timeout, removes stale state                                                           | None                                                                                                                                        | Removes state file when process stops or is stale      | JSON success with stopped or forced result    | Exits non-zero when no running state; may report forced false if kill unsuccessful |

## Backend utility modules

A few previously-frontend files have been moved to the `backend/utils` folder and modified to exclude all usage of Electron.

* `server.mjs`: Previously _server.js_ in the frontend, still is used to run and manage the GO server, but also has the `findAvailablePort()` helper.
* `serverInstallation.js`: Previously _installation.js_ in the frontend, used to check the server requirements (MongoDB and Python) and install MongoDB.
* `serverPathUtils.js`: Replacement for Electron's `app.getPath()` and `app.setPath()` functions.
* `serverWorkspace.js`: Previously _workspace.js_ in the frontend, used for creating a workspace and its folders.
* `mongoDBServer.js` _(NEW)_: MongoDB detect/start/stop/path logic used by backend endpoints.
* `jupyterServer.js` _(NEW)_: Jupyter detect/start/stop logic used by backend endpoints.
* `pythonEnv.js`: Python environment setup/check helpers for backend-managed workflows. Was previously in the frontend, and has been adjusted to no-longer use Electron dependencies.
* `medomics.server.dev.js`: Development-mode backend server helper/entry support, a copy of `medomics.dev.js` for use in the other backend helpers.

## OS service integration

The `/service` folder contains OS-specific files for running the backend as a service, also that has not been tested yet.
