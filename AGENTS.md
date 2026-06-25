# AGENTS

## Build Rules

- Always build firmware with Docker, never with host-installed `west`, `cmake`, or other local toolchains.
- Use the `Makefile` targets in the repo root for all firmware builds.
- Preferred targets:
  - `make left` builds the left half in Docker.
  - `make right` builds the right half in Docker.
  - `make uf2` launches both half-build Docker jobs in parallel and copies `urchin_left.uf2` and `urchin_right.uf2` to the repo root.
  - `make firmware` regenerates SVGs, launches both half-build Docker jobs in parallel, and refreshes the root UF2 artifacts.
- When a task requires new firmware outputs, run `make firmware` unless the user explicitly asks for only one half.
