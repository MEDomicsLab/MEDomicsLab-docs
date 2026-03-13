---
description: A list of currently useable endpoints to send requests to the backend server.
---

# Express Request Endpoints

#### Status and Service Lifecycle

| Method | Endpoint        | Purpose                                          | Input                                          | Success Response                                         | Notes                                    |
| ------ | --------------- | ------------------------------------------------ | ---------------------------------------------- | -------------------------------------------------------- | ---------------------------------------- |
| GET    | /status         | Get full backend runtime status                  | None                                           | success, expressPort, serverIdentity, go, mongo, jupyter | Probes live status before returning      |
| POST   | /stop-express   | Stop Express and best-effort stop child services | None                                           | success, stopped or message                              | Also attempts to stop Go, Mongo, Jupyter |
| POST   | /run-go-server  | Start or restart Go service                      | None                                           | success, running, port                                   | Kills existing Go process first          |
| POST   | /ensure-go      | Ensure Go is running (idempotent)                | preferredPort optional                         | success, running, port                                   | Preferred modern route                   |
| POST   | /ensure-mongo   | Ensure Mongo is running (idempotent)             | workspacePath optional                         | success, running, port                                   | Waits for port readiness                 |
| POST   | /ensure-jupyter | Ensure Jupyter is running (idempotent)           | workspacePath optional, preferredPort optional | success, running, port                                   | Default preferredPort is 8900            |

#### Workspace and File Tree

| Method | Endpoint               | Purpose                        | Input                        | Success Response          | Notes                                                  |
| ------ | ---------------------- | ------------------------------ | ---------------------------- | ------------------------- | ------------------------------------------------------ |
| POST   | /set-working-directory | Set active workspace on server | workspacePath required       | success, workspace        | Marks workspace as remote, reinitializes related state |
| GET    | /get-working-dir-tree  | Get directory tree for a path  | requestedPath query required | success, workingDirectory | Uses recursive directory tree output                   |

#### Mongo Data Import and Export

<table><thead><tr><th>Method</th><th width="132">Endpoint</th><th>Purpose</th><th>Input</th><th>Success Response</th><th>Notes</th></tr></thead><tbody><tr><td>POST</td><td>/insert-object-into-collection</td><td>Import file content into Mongo collection</td><td>objectPath required, medDataObject required (id, type)</td><td>success, insertedCount</td><td>Supports csv, html, png, jpg, jpeg, pkl</td></tr><tr><td>POST</td><td>/download-collection-to-file</td><td>Export collection content to file</td><td>collectionId, filePath, type required</td><td>success</td><td>Supports csv, html, json, images, pkl</td></tr></tbody></table>

#### Exploratory Services

| Method | Endpoint                      | Purpose                           | Input                                                                                                        | Success Response                                   | Notes                                        |
| ------ | ----------------------------- | --------------------------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------------------------- | -------------------------------------------- |
| POST   | /exploratory/dtale/start      | Start D-Tale and wait until ready | dataset required (id, name), requestId optional, pageId optional                                             | success, requestId, remotePort, webServerUrl, name | Starts Go automatically if needed            |
| POST   | /exploratory/dtale/progress   | Poll D-Tale startup/progress      | routeId required                                                                                             | success, progress                                  | Route-level progress                         |
| POST   | /exploratory/dtale/stop       | Stop D-Tale session               | requestId optional, remotePort optional                                                                      | success                                            | Calls D-Tale shutdown endpoint when possible |
| POST   | /exploratory/sweetviz/start   | Generate SweetViz report          | mainDataset required (id, name), compDataset optional, target optional, htmlFileID optional, pageId optional | success, htmlFileID, reportPath, expressPort       | Report served by report endpoint             |
| POST   | /exploratory/ydata/start      | Generate ydata-profiling report   | mainDataset required (id, name), compDataset optional, htmlFileID optional, pageId optional                  | success, htmlFileID, reportPath, expressPort       | Report served by report endpoint             |
| GET    | /exploratory/report/:reportId | Serve generated HTML report       | reportId path required                                                                                       | HTML response body                                 | Content-Type text/html                       |

#### Mongo Runtime and Diagnostics

| Method | Endpoint        | Purpose                        | Input                  | Success Response    | Notes                       |
| ------ | --------------- | ------------------------------ | ---------------------- | ------------------- | --------------------------- |
| POST   | /start-mongo    | Start Mongo directly           | workspacePath required | success, message    | Legacy direct route         |
| POST   | /stop-mongo     | Stop Mongo directly            | None                   | success             | Legacy direct route         |
| GET    | /get-mongo-path | Resolve mongod executable path | None                   | success, path       | 404 if not found            |
| GET    | /mongo-debug    | Get Mongo debug info           | None                   | success, mongoDebug | Useful for startup failures |

#### Jupyter Runtime

| Method | Endpoint              | Purpose                     | Input                  | Success Response   | Notes                    |
| ------ | --------------------- | --------------------------- | ---------------------- | ------------------ | ------------------------ |
| GET    | /check-jupyter-status | Check if Jupyter is running | None                   | running, error     | Lightweight status route |
| POST   | /start-jupyter-server | Start Jupyter directly      | workspacePath required | running, error     | Legacy direct route      |
| POST   | /stop-jupyter-server  | Stop Jupyter                | None                   | stop result object | Legacy direct route      |

#### Python and Requirements

| Method | Endpoint                          | Purpose                             | Input                     | Success Response         | Notes                                                                  |
| ------ | --------------------------------- | ----------------------------------- | ------------------------- | ------------------------ | ---------------------------------------------------------------------- |
| GET    | /get-bundled-python-environment   | Get bundled Python env path/details | None                      | success, pythonEnv       | Used before Go/python workflows                                        |
| GET    | /get-installed-python-packages    | Get installed Python package info   | None                      | success, packages        | Current implementation appears to return env-derived data              |
| POST   | /install-bundled-python           | Install bundled Python runtime      | None                      | success                  | Backend installer path                                                 |
| POST   | /install-required-python-packages | Install required Python packages    | pythonPath optional       | success                  | Installs required deps for backend workflows                           |
| GET    | /check-python-requirements        | Validate required Python deps       | pythonPath query optional | success, requirementsMet | Boolean result                                                         |
| GET    | /check-requirements               | Check global requirements           | None                      | success, result          | Includes Mongo/Python checks                                           |
| POST   | /install-mongo                    | Install MongoDB                     | None                      | success                  | Error response may include installerExitCode and windowsInstallerError |

### Error Behavior (Common Pattern)

* 400 for invalid or missing required inputs
* 500 for runtime/internal failures
* Typical error payload: success false, error message
* Some routes include extra diagnostics (for example mongoDebug, installerExitCode)

### Recommended Usage Pattern

1. Call /status to inspect current state.
2. Use /ensure-go, /ensure-mongo, /ensure-jupyter instead of legacy start routes.
3. For exploratory reports, start via exploratory endpoint then read via /exploratory/report/:reportId.
4. Use /mongo-debug and /check-requirements when setup fails.

<br>
