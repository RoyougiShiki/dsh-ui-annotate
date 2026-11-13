# Domain docs

- **Layout**: single-context
- **Glossary**: [`GLOSSARY.md`](../../GLOSSARY.md) at the repo root
- **ADRs**: [`docs/adr/`](../adr/), one file per decision, `Status` required (`proposed | accepted | deprecated | superseded by ADR-NNNN`)

## Reading rules

- Read `GLOSSARY.md` before naming anything new. A term that is not in it and matters to the design gets added there, not invented inline.
- Read every ADR under `docs/adr/` that touches the area before changing it. An accepted ADR is a constraint until superseded, not a suggestion.
- Implementation detail belongs in code and tests, not in an ADR.
