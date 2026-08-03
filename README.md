# Vitund package index

A [PEP 503](https://peps.python.org/pep-0503/) "simple" package index serving
the Python client libraries for **Vitund Sandboxes**:

| Package | What it is |
|---|---|
| `vitund-cli` | The `vtd` command-line client |
| `vitund-sdk` | The generated Python SDK the CLI is built on |

Only client-side libraries are distributed here. The sandbox supervisor,
router and host components ship separately as `.deb` packages and are not
part of this index.

## Install

```bash
pip install --extra-index-url https://vitund-ai.github.io/pypi/simple vitund-cli
```

`vitund-cli` depends on `vitund-sdk`, and both resolve from this index.
Everything else (`httpx`, `pydantic`, and friends) comes from PyPI as normal,
which is why this is an `--extra-index-url` rather than a replacement for it.

## Versioning and stability

These are **`0.x`, pre-1.0 releases and the API is not yet frozen.** Expect
breaking changes between versions. Do not pin production systems to them yet.

Client versions are stamped from the same build as the server components they
talk to, so a `vitund-cli` version corresponds to the router version it was
built alongside.

## Why not PyPI

It will be, once the API is frozen. PyPI versions are permanent and can never
be reused — so publishing there while the API is still moving would burn
version numbers on releases we intend to break, and leave anyone who installed
them pinned to a surface that no longer exists. An index we control can be
re-cut freely; that freedom stops being worth anything the moment the API
stabilises, which is the point we move.

The `vitund-cli` and `vitund-sdk` names on PyPI are held by this project.
