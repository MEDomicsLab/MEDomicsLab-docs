---
description: >-
  This section describes where to find the different components for development
  of the remote version of the MEDomics Platform.
---

# 🔧 Development

## New structure

In order to separate the local client component from the backend server component, so that we can run either independently and use the server without a GUI (like in a remote terminal, through SSH), we had to move files and features to a separate folder, labeled `backend` in the repository.

Express is now at the root of all backend operations, and you can find more details about its usage in the [Backend - Server](https://medomicslab.gitbook.io/medomics-docs/~/revisions/z0wFwbRqAmxlgbHR1M4e/tutorials/remote-medomics/development/backend-server) subpage or its own subpage, [Express Endpoints](backend-server/express-request-endpoints.md).&#x20;

Similarly, the parts of the client that have been altered or added to fit this new usage mode will be described in the [Frontend - Client](frontend-client.md) subpage.

## Enabling/disabling remote modules

A lot of the modules haven't been fully tested or refactored yet for remote use and therefore have been "locked" behind a blank screen like this:

<figure><img src="../../../.gitbook/assets/image (116).png" alt=""><figcaption></figcaption></figure>

In order to reenable a module that has been adapted to the new architecture, find the `REMOTE_READY_COMPONENTS` and `REMOTE_BLOCKED_COMPONENTS` variables around line 35 of `renderer/components/layout/layoutContext.jsx`, as well as the `blockedInRemote` set at line 150 of `renderer/components/layout/layoutManager.jsx`. Those sets are what determines whether or not a module is displayed or shows the error page, and therefore can be used to allow access to modules once they are ready for online use.

## Packing and distributing

Using the new GitHub actions files (located under `.github/workflows`), the server and client can now be packed either together or independently:

* A `server-vX.Y.Z` tag will create a release for **only the standalone NodeJS server**, along with scripts to start and stop it.
  * Uses `serverRelease.yml` to start the workflow, which will use the `package.json` file in the backend folder to gather the correct versions, then `pack_server.js` to create ZIP folders with the necessary (GO files, Python files, start/stop scripts, etc.) to run the server on different platforms.
* A `client-vX.Y.Z` tag will create a release for **only the lightweight Electron client.**
  * Uses `clientRelease.yml` and `electron-builder.client.yml` (practically how it was before the client/server split but without any backend parts attached).
* A `vX.Y.Z` tag will package both together like it used to be in previous, local-only versions.
  * The legacy path, that packs both server and client together (through `automaticBuilding.yaml`)

