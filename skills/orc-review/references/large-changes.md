# Large or incomplete changes

Read when sizing limits are exceeded or patches are incomplete.

1. Reconcile inventory/totals, including renamed, deleted, generated, vendored, binary, and unavailable content. Changed-line counts exclude headers, context, and surrounding source.
2. Separate bulk output before sizing substantive packets. Assess relevant dependency, generator, provenance, and compatibility evidence; filename patterns permit no blanket exclusion.
3. Group by behavior/dependencies, keeping contracts, callers, consumers, and tests together where practical. Split large files by symbols/hunks with source context, not arbitrary line cuts.
4. Fit packets to selected limits and host capacity. Record scope ID, base/head, requirements/source, owner, dependencies, and any smaller limits needed.
5. Track changed paths/hunks → packet/reviewer/revision → evidence/gaps. Reading summaries or file lists is not coverage.

Review bounded packets while preserving findings/coverage. The general reviewer
traces cross-packet interactions and whole-PR criteria; packet completion alone
is insufficient.

Recover missing/truncated patches through read-only source/comparison access,
using both sides where needed. Pagination does not remove platform caps. If
required access/capacity remains missing, return partial/blocked with uncovered
behavior and next bounded scope. Ask only for consequential scope decisions;
a reviewed subset cannot establish whole-PR completion.
