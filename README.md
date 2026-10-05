# interactor-ufbx-to-openusd

Reads FBX files through ufbx, reporting each file's stated conventions and checking them against its geometry, on the way to OpenUSD.

## What it is for

Every FBX file states its own up axis, front axis, unit scale and frame rate. This interactor parses them rather than assuming them, checks them against the mesh and skeleton, and returns what the file said beside what was requested. The fabric reaches it over the iceoryx2 bus through `bus_server.py`; `server.py` serves the same interface over HTTP for standalone testing. The USD write itself is not implemented; the probe and the geometry checks run.

## Build and test

    docker build -t ufbx-to-openusd .
    python test_validate_geometry.py

The image runs the HTTP server. The tests need the `usd-core` and `numpy` Python packages.

## Licence

Apache-2.0 OR MIT, at your option: [LICENSE-APACHE](LICENSE-APACHE), [LICENSE-MIT](LICENSE-MIT). ufbx is MIT and is fetched at build time rather than vendored.
