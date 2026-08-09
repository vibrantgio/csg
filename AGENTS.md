# AGENTS.md — csg

Constructive solid geometry on polygon meshes, by way of BSP trees: `Cube`,
`Sphere` and `Cylinder` built from functional options — `Center`, `Radius`,
`Size`, `Slices`, `Stacks`, `Start` and `End` — and `Union`, `Subtract` and
`Intersect` over the resulting `*Solid`. A modelling kernel that yields
polygons, not pixels; overlapping coplanar polygons in both solids are
handled.

**Layer.** Outside ADR-001's tier table: a support library, which the rule
binds in one direction only — every tier may import it, and it may import
nothing in the table itself. That nothing here consumes it is deliberate:
seen carries an adaptation of the same algorithm as its own `solid`
package, rewritten onto seen's `point`, `face` and `transform` types so
that a solid is a `seen.Object`, rather than importing this module. Its
root module imports nothing else in the organization. Nothing in the
organization imports it. Both directions are measured rather than typed —
`scripts/check-layers.sh --edges` reports the graph and
`scripts/sync-agents.sh` renders these sentences from it — so correcting
them here changes nothing.

**Read the canonical guide before you write code against this module.** It is
the organization's one agent guide — the module inventory with current tags,
the application skeleton, the MVU loop and rx semantics, typography, and the
pitfalls that are not guessable. It lives exactly once, in `vibrantgio/.github`,
and this file links it rather than copying it:

    https://raw.githubusercontent.com/vibrantgio/.github/master/llms.txt

**Module.** `github.com/vibrantgio/csg`, one module at the repository root.

**Build and test.** From the repository root:

    go build ./... && go test ./...
