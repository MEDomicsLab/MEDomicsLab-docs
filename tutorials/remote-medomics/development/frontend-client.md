---
description: >-
  A list of the edited and created files to allow the client to connect to the
  backend.
---

# Frontend - Client

## Connection modal and helpers

### Connection UI

* `renderer/components/mainPages/connectionModal.jsx` contains the modal used for connecting to a server and setting up a remote workspace. This uses the following file a lot:
* `main/utils/remoteFunctions.js` contains most of the functions used for establishing SSH tunnels, doing operations on the remote computer using SSH (installing the server, renaming files/folders, etc.) and managing the local state of the established connection. That state is stored and synced in 2 files:&#x20;
  * `renderer/components/tunnel/TunnelContext.jsx` for React components&#x20;
  * `renderer/utilities/tunnelState.js` for other components
* `renderer/components/mainPages/remoteServer.tsx` contains the panel that shows the status, logs and established tunnels to the remote server.
* `main/sshKeygen.js` is used for SSH keypair generation used during remote connection setup.

### Requests and utils

* A few request helper files (`requests.js`, `mongoDBUtils.js`, `workspaceUtils.js`) have been modified to adjust their behavior depending on whether the workspace is marked as remote (`workspace.isRemote`) or if a tunnel is connected (to route the requests to the correct port, using `tunnelState.js`)
* `renderer/utilities/fileManagement/fileOps.js` becomes the new entry-point for all the functions in `fileManagementUtils.js`, which will still be used if the workspace is local. Otherwise, it uses the SSH-based alternative present in `fileOps.js`.

## Bridge for remote architecture

* `main/background.js` has been updated to change the client's boot process, checking for whether the server is found locally and then running it if so. It lost some IPCs that were related to starting specific servers (such as Mongo and Go, which are now in the backend files) and gained some for installing, finding and updating the local server.
* `main/preload.js` is a safe renderer API surface which exposes backend/tunnel request methods via IPC, in order to send Express requests easily through code. Here's an example:\
  `const response = wait window.backend.requestExpress({ method: 'get', path: '/status', host: '127.0.0.1', port: 5000, timeout: 3000 })`
