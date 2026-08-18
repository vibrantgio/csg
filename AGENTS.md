# AGENTS.md — csg

Constructive solid geometry on polygon meshes, by way of BSP trees: `Cube`,
`Sphere` and `Cylinder` built from functional options — `Center`, `Radius`,
`Size`, `Slices`, `Stacks`, `Start` and `End` — and `Union`, `Subtract` and
`Intersect` over the resulting `*Solid`. A modelling kernel that yields
polygons, not pixels; overlapping coplanar polygons in both solids are
handled.

**Layer.** Outside ADR-001's tier table: a support library, which the rule
binds in one direction only — every tier may import it, and it may import
nothing in the table itself. It is constructive solid geometry over BSP
trees — `Union`, `Intersect` and `Subtract` on a `*Solid` — and it depends
on nothing but the standard library. Its root module imports nothing else
in the organization. That direction is measured rather than typed —
`scripts/check-layers.sh --edges` reports the graph and
`scripts/sync-agents.sh` renders these sentences from it — so correcting
them here changes nothing. The other direction is measured too and
deliberately not written down: the gate checks the graph both ways, but a
public API's consumers are unknowable, so this file says what its module
needs and never who needs it.

**Read the canonical guide before you write code against this module.** It is
the organization's one agent guide — the module inventory with current tags,
the application skeleton, the MVU loop and rx semantics, typography, and the
pitfalls that are not guessable. It lives exactly once, in `vibrantgio/.github`,
and this file links it rather than copying it:

    https://raw.githubusercontent.com/vibrantgio/.github/master/llms.txt

**Module.** `github.com/vibrantgio/csg`, one module at the repository root.

**Build and test.** From the repository root:

    go build ./... && go test ./...
