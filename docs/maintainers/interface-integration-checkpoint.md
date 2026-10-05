# Interface Integration Checkpoint

This is the living evidence appendix for the forward-merge guide, not a release
approval or a complete site-audit claim. Read `AGENTS.md`, UI Style Standard and
UI Fix-It first. Preserve earlier accepted work while reviewing small batches.
Never infer human acceptance from test success or a journal's implementation note.

## Preservation and coverage map

| Work to preserve                                                       | Established owners and existing checks                                                                                                                                                                            | Review boundary                                                                                                                                                      |
| ---------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Request Status and request-modal layout, filters, actions, title roles | `globals.css`, Request components; `src/styles/buttonGeometry.test.mjs`, `requestLayout.test.mjs`, current-batch contract                                                                                         | Earlier work is in scope for the contribution; a Series-first batch does not remove it. Final accepted references and current narrow renders remain to be assembled. |
| Shared page titles/headings, typography and spacing                    | `page-title`, `page-heading`, card/table families; `buttonGeometry.test.mjs`, current-batch contract                                                                                                              | Preserve role owners and existing acceptance, not retired experimental values.                                                                                       |
| Aggregate loading/searching/mutation status                            | `page-title-row`, `page-status`, shared status/spinner; `buttonGeometry.test.mjs` and component tests                                                                                                             | Keep one real activity indicator; completion/unmount must clear contributions.                                                                                       |
| Poster dimensions, buttons, media slots and hover                      | `poster-layout`, poster frame/region/control roles; `buttonGeometry.test.mjs`, `iconOnlyButtons.test.mjs`                                                                                                         | Fixed browsing geometry is distinct from detail/credit posters. Trace all affected renderers.                                                                        |
| Series tree, quality, native controls and disclosure ordering          | Series components, shared selection/tree/ratings/disclosure owners; `seriesDetailsStyle.test.mjs`, native-action suites and reorder suites                                                                        | Selection and permissions remain functional contracts. Mocked drag tests do not prove physical drag/touch acceptance.                                                |
| Current Plex Collection repair                                         | `server/api/plexapi.ts`, native collection routes/client; `server/api/plexCollections.test.ts`, `src/styles/mediaServerCollectionsClient.test.mjs`, `mediaServerCollections.test.mjs`, `plexCollections.test.mjs` | Optional smart marker is accepted only with remaining exact identity checks. Remove only membership, never the collection.                                           |
| Mutable Watchlist/Collection state                                     | `server/middleware/apiResponseCache.ts`, native clients, `ServiceWorkerSetup/sw.ts`; cache/client/service-worker tests                                                                                            | Fresh initial/pre-write reads and confirmed desired state; local Seerr watchlist and Plex Watchlist remain distinct.                                                 |
| Dropdown opacity, overflow and ancestor framing                        | Shared dropdown/menu surface and detail-card open state; `seriesDetailsStyle.test.mjs`, `Common/Dropdown/playbackStyle.test.tsx`                                                                                  | Parsed source ownership is not rendered paint-order proof. Compare open and closed desktop/narrow states.                                                            |

The broader [Interface Preservation Inventory](interface-preservation-inventory.md)
has been reconciled against the journal and original chat. It covers the Request
page and shared roles, poster/browse prototypes, dropdown/mosaic cleanup, final
tree/table/workspace, ratings, ordering and native actions. It distinguishes
explicit acceptance, pending review, retired trials and opt-in references.
Neither document replaces the final three-way changed-file inventory. Rolled-back
successor changes must not be resurrected because an older log mentions them.

## Confirmed provider evidence before this batch

- Plex Collections: authorized Seerr Add, Remove and Add again with matching
  provider and Seerr membership readback. The test collection was retained for
  John's manual trial, not deleted. This was a bounded own-account verification.
- Plex Watchlist: the stale mismatch was reproduced; authorized removal of the
  reported series reduced membership by one and a fresh Plex reload confirmed
  absence. Adding it back restored membership and the Remove action. The item
  remains saved. This is live evidence, separate from mocks.
- Jellyfin/Emby native actions: mocked tests only; no live write pass claimed.
- Previous focused passes do not establish a full cumulative suite/build pass.
  Human visual acceptance and physical drag/touch review remain pending.

## Current bounded batch

Approved: improve portable instructions, regression checks and merge evidence;
repair only clear existing visual-rule violations in the Series/shared controls.
Not approved: broad backend/security repair, new design presets, NAS deployment,
GitHub push/PR or production-account tests as part of a visual audit.

The original public `dev`, `build`, validation and hook bindings remain intact.
Focused checks support iterative previews; finalization requires one complete
gate on the exact candidate. `pnpm build` runs validation then compilation, so
do not run another identical full validation immediately beforehand.

Known remaining visual debt: legacy Series/shared `@apply` and competing card
padding owners require a later bounded consumer audit. A long action-menu list
needs an approved bounded-viewport preset; do not invent dimensions here. This
batch does not establish that the page or application is Tailwind-free.

Current isolated focused batch: **117 tests passed**, zero failures, skips,
cancellations or todos. Suites: local-validation bindings/discovery/isolation,
buttonGeometry, iconOnlyButtons, requestLayout, Series style and saved-item
client. New negative fixtures reject competing clipping/surface/gap owners and
retired icon geometry; Watchlist Remove tests confirm explicit desired false
and fresh already-completed state. Two old icon assertions were superseded by
the documented shared-padding/native poster-role contract, not waived.

Isolation: separate candidate source, disposable `/tmp` config, Docker network
mode `none`, dependencies/store mounted read-only; no live config/DB mount.
Formatting and discovery plan passed. All 12 explicit files matched the mounted
source readback. Desktop/narrow menu inspection confirmed the shared black surface,
open content above its parent frame, keyboard access to the last option, and Escape
restoring normal clipping/layers/focus. Narrow tree headings still crowd; physical
drag/touch and final human visual acceptance remain pending.

The one full `pnpm build` attempt passed translations, current-batch and shared-
style validators, formatting, lint, server/client types and all 85 Vitest files
(395 tests). **Blocked:** during the native TypeScript lane, the network guard
failed after AvailabilitySync because of an unstubbed TMDB attempt. The related
test, implementation and guard match the pre-batch source. This is an unchanged
test-isolation failure, not proof of a production backend defect.

The isolated run was stopped after that required failure. Native TS is incomplete;
the cumulative native JS/tooling lanes and production compilation were not run.
No complete gate/build pass, exception or waived failure is claimed. No unrelated
backend/test repair was made in that attempt. Preserve the failed receipt
separately from focused passing evidence.

John subsequently authorized repairing that suite's test isolation with production
backend code untouched. The focused failure was reproduced with the guard enabled;
the test now mocks the actual retained TMDB client with typed season fixtures and
per-test restoration. Unexpected fixture IDs fail outside the production catch.
A new unavailable-enrichment case checks the exact lookup and preserved status.
All 18 focused tests pass, with no skips/cancellations/todos. This test-only repair
is not a production backend fix or a complete cumulative gate/build pass. The
final gate and human acceptance remain pending; unrelated failures still require
scoped direction before further repair.

The visual/client fixtures were also tightened: negative CSS/role fixtures must
fail with their intended diagnostics, wrong icon padding is checked without a
duplicate declaration, and Watchlist Remove rejects a valid response that still
reports saved membership. Recovery remains read-only. The six focused visual/
client/runner suites now pass **119 tests**, zero failures/skips/cancellations/
todos; the separate AvailabilitySync focused suite passes 18. Production backend,
network guard, package/hook bindings and lockfile remain unchanged. The complete
candidate is being verified separately; these focused receipts are not a waiver
or full-gate claim. Internal-only test hardening adds no user-facing feature.

## Subsequent isolated verification and input blockers

The repaired cumulative retry passed the preliminary validators, formatting,
lint, server/client types and all85 Vitest files/395 tests. AvailabilitySync
passed within the native TS lane. A different required after-hook then failed
following the Plex scanner suites: the guard caught an attempted request to a
fake Plex test host. That scanner source and guard are unchanged from the
preserved baseline. This is isolation evidence, not a production bug diagnosis.
The long run was stopped there; exit137 records the stop, separately from the
hook failure. Native TS remains partial; no production compilation was reached.
No scanner/guard repair or failure waiver was made.

The previously unrun native JavaScript lane was executed separately on the same
frozen candidate: all46 selected files ran,391 tests,357 passed,34 failed, zero
skips/todos/cancellations. This is a failing partial receipt, not a complete gate.
Failures include superseded source/utility assertions and unresolved contracts;
replace only clearly superseded assertions with equivalent role/behavior tests
and negative fixtures. Do not restore retired layouts or normalize uncertain
palette/ordering decisions merely to increase the pass count.

Full tooling inputs are also unavailable: the mounted app source contains only
the CI workflow, while tests read other chart/release/preview workflows and root
release fixtures. The bare Node/Alpine image lacks required native tools.
The earlier snapshot additionally omitted an existing Unraid template fixture;
that omission is corrected in future manifests, not inserted into the frozen
receipt. Establish complete authoritative pinned Git inputs and a suitable
disposable toolchain before another final run. Plan discovery is not proof of
fixture/tool availability. No borrowed fixtures, installed live tools or suite
exclusions convert these blockers into a pass.

## Bounded visual-contract follow-up

One established implementation violation was repaired: the single-option
Request icon's local16px utility is removed only after its real branch is
attached to the existing shared14px content-size owner. No new geometry or
palette was designed, and production backend code is unchanged.

Seven visual test files now follow the current Requests consumer, accepted
semantic table/gap owners and Series saved-order/controlled-disclosure behavior.
Superseded source/utility assertions were replaced with property/role/callback
coverage and diagnostic-specific negative fixtures. The affected nine-suite
execution (including shared button/icon checks) ran157 tests:153 passed, four
failed, no skips/todos/cancellations. Three failures were in the new icon checker:
it initially audited unrelated root palette aliases and mishandled PostCSS's
separate important flag. After correcting that checker, only its changed six
tests were rerun: all six pass. The other required Book ordering failure is
unchanged and unresolved; no full affected or cumulative pass is claimed.

Current-batch/shared-style validators and changed-component lint pass;
formatting passes. The actual PostCSS configuration compiles the shared CSS
with zero warnings. Palette/theme, Book-order and other unreconciled failures
remain recorded. The earlier frozen full/native-JS receipts are retained;
this follow-up has only focused evidence and still needs rendered/human review.
Repository/toolchain prerequisites and full gate/build remain blocked.

## Latest bounded preview checkpoint — October 2, 2026

This section supersedes earlier current-status descriptions above, not their
preserved diagnostic receipts. John limits further preview verification to the
Requests page, Series page, Discover's Recent Requests slider, and shared poster
styles across their consumers. A poster-role check does not authorize a whole-page
audit of each consumer. No broad backend repair or site-wide page sweep is approved.

The two inherited network-isolation failures also reproduce on untouched upstream
v3.44.1 and the subsequently tested main. They do not establish that the visual
changes introduced a production defect. Original tests and failed receipts are
backed up. John's exact-file/target temporary diagnostic deferrals are opt-in;
outbound requests remain blocked and strict default behavior remains intact.
Deferred required failures are not a passing release gate. Reconcile the original
tests and the maintainer's coverage before final contribution acceptance.

The retired CSS-representation assertions have been reconciled with the current
shared classes, variables and accepted semantic roles, retaining meaningful
behavioral safeguards and negative coverage. That source lane passed 410 tests
in 47 files, with no failures or skips. The previously completed component lane
passed 395 tests. These are separate receipts from an earlier exact source state,
not a complete cumulative pass for the final tree. The three broad native
receipt-recovery partitions were intentionally stopped when John narrowed scope;
their partial reports must not be counted as passing or restarted automatically.
Unrelated tooling findings remain documented rather than repaired or waived.

A subsequent narrow cleanup removes competing card-padding ownership: main media
cards retain the existing shared main-padding owner rather than also consuming
inset padding. The overwritten local padding utility and duplicate blur declarations
were removed. The shared poster layout retains positioning while the shell retains
only its independent stacking role. Current main/inset padding remains 8px;
browsing posters remain 169.2px wide with a 2:3 frame. No component, production
backend, dependency, live configuration or provider data changed in this cleanup.

Current focused receipts, executed once per final affected selection:

1. Seven card/poster owner and menu checks passed, including negative mutation
   checks (`mediaCardOwners.test.mjs` and the two selected menu contracts).
2. Thirteen native frontend poster badge/link and slider tests passed in three
   files: `TitleCard/statusBadges.test.ts`, `TitleCard/bookDetailQuery.test.ts`,
   and `utils/mediaSlider.test.ts`.
3. Nine native frontend Requests user-filter and Series availability-tone tests
   passed in `Requests/requestStatusQuery.test.ts` and
   `MediaDetails/AvailabilityValue.test.ts`.

Those 29 tests have zero failures, skips, cancellations or todos. Native runs used
isolated source/config, read-only dependencies, no network, strict network guards,
and no temporary network-deferral flag. Formatting passed. Published CSS/test
readback matched the tested files; the complete source comparison found no
unexpected component/backend changes or deletions.

Rendered review confirms Requests at 1440px and 390px, Series at the existing
desktop-sized viewport and 390px, and the request slider at 390px. Requests uses
36px/40px page-title typography above the breakpoint and 24px/28px below it;
cards retain 8px padding. Neither reviewed narrow page has page-wide horizontal
overflow. Poster positioning and frame dimensions remain intact. The desktop
collection-menu capture shows an opaque black surface extending beyond the main
card without clipping; Escape closes it. Request-slider Next moved the track by
one compact-card width, and Previous restored its disabled-at-start state.
The landscape request-summary cards are not portrait browsing posters.

Legacy compact request-card utilities and remaining shared `@apply` are explicitly
not a Tailwind-free claim. Loading/error/empty variants, every alternate theme,
physical drag/touch, and unaudited pages are not newly certified by these captures.
No live provider mutation was repeated during this visual cleanup. Detailed source
hashes, receipts, recovery files and screenshot locations are in the recovery
journal.

John explicitly accepted the visual test for this scoped cleanup on October 2,
2026, while on his phone, based on the previously proven CSS and absence of major
visual changes beyond utility/duplicate-owner cleanup. This is his approval of
the current bounded visual batch, not a claim that he newly inspected every
desktop/narrow screenshot or certified unreviewed themes, states or pages.
Earlier review gaps above remain recorded; this approval does not silently
certify physical drag/touch or other untested interactions.

The complete strict gate/build, GitHub checks and publication authorization
remain pending. Visual acceptance does not waive deferred required test failures
or authorize a PR. CI success must be matched to the actual shared-gate inventory,
not assumed to cover every local check.

## Finalization authority and latest accepted scope — October 3, 2026

John explicitly accepted the current preview and authorized final checks, a
contribution to `snapetech/seerrng`, monitoring relevant CI failures, deployment
of the tested preview build to his server, and bounded nightly cleanup. These
instructions supersede the earlier pending publication/deployment authority;
they do not waive a required failure or authorize unrelated backend repairs.

The accepted candidate now uses the newer upstream 3.46.1 main at
`e7305281797cd7527c3b1c0a83ff144218ad506a`. Later accepted work includes shared
blue pinnable catalog filters and titles, the yellow watchlist visibility action,
the reused Series request tree and adjacent Episode Queue, a single Series
request entry, six-role Overview disclosure/order, and native shared CSS cleanup
for active Series detail/request/browse controls. The latest focused receipts
are not the cumulative release gate. Remaining utility-dependent conditional
overlays, settings-specific controls, physical drag/touch, and unaudited pages
are not newly certified or claimed Tailwind-free.

Final independent review identified an API-contract mismatch: Overview expanded
the Series role set to six while the OpenAPI order schema still described five.
The schema must match the same six-role server owner before final validation,
including persisted user settings, request payloads and normalized responses.

Publication must also follow the current contribution guide's requirement that
John supplies his own-word PR description and accurate AI disclosure. Automated
code/testing evidence does not supply that human-authored publication input.
If that input is absent, preserve the contribution on a verified remote branch
and report publication as pending rather than misrepresent authorship.

## Required evidence at contributor finalization and maintainer integration

Fill these fields with observed facts; unknown means pending, never assumed.

1. Contributor remote/branch/commit; pinned maintainer target remote/branch/commit;
   actual common ancestor; integrated commit; exact tested commit/source digest.
   All commit IDs are pending until the actual authorized Git integration.
2. Pinned Node/pnpm identities, lockfile SHA-256, environment/platform, isolated
   source/config/dependency mounts and actual network boundary.
3. Three-way changed-file inventory and conflict ledger: owner, newer upstream
   behavior/security requirements, preserved interface rule, resolution and check.
   Do not wholesale restore an older backend, component or lockfile.
4. Discovery plan versus executed logs: test file inventory, test totals, failures,
   skips/todos, platform exclusions, lint/type/static/style results and build result.
   `pnpm test` is test partitions only; `test:ci` is Vitest-only. Browser/Cypress
   suites are separate. Linux is required for complete POSIX tooling coverage.
5. Desktop/narrow reference locations and John's acceptance per page/state,
   including loading/error/empty, keyboard/focus/disabled, open menus and reorder.
   An automated screenshot or computed-style result is not human acceptance.
6. Live Plex evidence separately from mocked native coverage; safe prerequisites
   for unverified providers. Never copy credentials, runtime DBs or live config.
7. Explicit deferrals, unresolved failures and next gate. A failed required gate
   blocks finalization; report unrelated backend failures before expanding scope.
8. Recoverable refs/archive identity and checksums, final source readback, and
   applicable publication authority. Local preview publication is not PR approval.

The contributor and Keith's AI must use the same checked-in instructions and
gate, adapted to the newer target without discarding its valid security/backend
fixes. If the target advances, pin the new head and repeat invalidated checks.

## Preview merge and validation — October 4, 2026

This section supersedes earlier descriptions of the current command bindings and
publication authority; historical receipts above remain unchanged. John selected
the accepted preview and authorized integration with Keith's current main,
scoped Fix-it repairs, source-specific engine validation, separate guarded
compilation, and a laptop preview on port 5071 with an independent copy of the
5070 configuration/database. The final preview is shown only after those checks
complete. John's visual review remains required before any PR.

The pinned upstream base is `a96fafa07c77a2d6d95badeb9f60c32a6b4a47c9`
(3.48.3). The exact accepted working-byte checkpoint is
`d9338138acf269a37018d2fedc7b7daa8dce2d2d`, whose common ancestor with upstream
is `e7305281797cd7527c3b1c0a83ff144218ad506a`. The three-way inventory contains
311 accepted paths and 361 upstream paths, 308 overlapping paths, and eight
manual conflicts. The accepted screen semantics are already present upstream;
MediaSlider retains its newer TMDB stale/error retry notice and poster fallback.
Testing instructions are reconciled to the reviewed engine, while actual public
package commands and hooks preserve their existing bindings.

The reviewed combined engine uses this integrated candidate's existing tests and
supplemental checks with fresh inventory, case ledger and source/environment
pins. The archived comprehensive runner is not an additional mandatory test run.
`pnpm build` runs translation/shared-visual guards and compilation separately.
The saved 3.48.1 engine receipt remains historical and cannot certify this source.
All iterative source, dependencies, evidence, caches, test and compile work remain
in Docker-managed Linux storage. The original accepted preview remains preserved.

Current evidence and the bounded Fix-it repair ledger are being recorded in the
owned Linux evidence volume. Final tests, compile, deployment health and visual
acceptance remain pending until their actual receipts are verified. No live
provider writes are authorized by this validation.

## Theme adoption and publication authority — October 4, 2026

John subsequently requested a one-time switch to SeerrNG for new installations
and existing accounts upgrading to this build or a later build containing this
migration. The stable migration adds an account palette default and clears old
active advanced-theme overrides once. After login, another supported palette
can be selected and saved to that account. Later logins and upgrades retain that
choice; the migration is not a per-version or per-login reset. Appearance mode
and unrelated account preferences are preserved.

John explicitly authorized submission to `snapetech/seerrng` after passing tests,
using his previously approved AI disclosure, and automatic follow-up repairs
for relevant PR failures. This supersedes the earlier pending preview-review
publication gate. It does not certify new physical drag/touch, browser/Cypress,
live-provider or PostgreSQL-service testing. The accepted visual decisions remain
his; no new whole-site visual acceptance is claimed.

The pre-theme integrated tree passed the full reviewed engine (3,994 passed,
four existing conditional PostgreSQL skips, zero failures; 555 files) in
344.227 seconds. Its separate guarded compilation completed in 117.572 seconds,
after 11.150 seconds of prebuild guards. Those are historical receipts for tree
`473af0fd9c7479c9e58c043115e285727691ccd7`, not proof for the theme amendment.
John explicitly waived another compile and requested tests only for the amended
source. A fresh source-bound engine run and static checks must establish that
amendment's actual result before publication. No production deployment or merge
of Keith's PR is authorized by this overnight finalization request.

## Cumulative issue and dirty-worktree integration — October 4, 2026

The isolated candidate is `codex/release-integration-159-160-20261004`, based on
`origin/main` at `06fbbce72` plus all audited project-origin branches. The edit
request regression was committed as `b8b9be2ba`; the remaining cumulative
worktree patch from the `reader-groupings` checkout is preserved at
`/tmp/seerrng-reader-groupings-all-dirty.patch` (SHA-256
`7cb33ac20ddf1e33b6b0db09f1cc8f0033acd82b491ebbe1354eb15b05e73421`). The
recoverable ref bundle is
`/tmp/seerrng-release-recovery-20261004/all-refs-post-advances.bundle` (SHA-256
`957485e5da8241409c4a3586d2137cf018df055476cb77217a803a7175e509f8`, recorded in the recovery ledger). Do not treat its original
conflicted apply as an integrated or verified state.

The candidate combines the per-user IMDb/Goodreads list work for #159, the
QuestarrNG search fallback for #160, the edit-request media identity fix, game
library and household sharing, Steam linking/import, Reader Delivery groupings,
request-count refresh, Audiobookshelf scan bounds, support-link update, and
other dirty test/documentation work. The `seerr-api.yml` merge preserves the
candidate's current API contract and adds the new Reader Delivery and Game
Library paths/schemas; settings now include both Steam secret redaction and
ROMarrNG platform mapping fields. Unique auxiliary test diffs and stale
recovery snapshots still require comparison before final validation.

The edit-request regression has a baseline/fixed Playwright reproduction using
separate built trees and seeded SQLite databases on kspls0 loopback ports. The
baseline click left one dialog mounted; the fixed candidate opened a second
`Edit Request` dialog with the pending Movie request. The corresponding captures
are `/tmp/seerrng-release-recovery-20261004/edit-request-before.png` and
`/tmp/seerrng-release-recovery-20261004/edit-request-after.png`. Focused Vitest
and lint passed for that committed fix. This does not establish final candidate
integration, full-gate success, or human visual acceptance.

All further browser, database, and service checks use isolated candidate copies
on kspls0 loopback. Do not target its SeerrNG production service on port 5055,
production databases, configured provider accounts, or household data. Issue
#159/#160 baseline/fixed UI reproductions, issue-specific regression suites,
security review of the imported changes, the complete pinned
`pnpm validate:development` gate, final build, and exact-candidate visual review
remain pending. No current cumulative gate is claimed. The human visual
acceptance gate remains outstanding for the new interface work.

The security review found two unbounded reads in the imported integration:
household sharing materialized every explicitly shared game before paging, and
the scheduled external-list sync loaded every configured list at once. The
shared-game query now reads at most 20,001 entries and returns a documented
service error above the 20,000-entry limit; scheduled list sync now pages by
increasing row ID in batches capped at 100. Focused regressions cover the shared
limit and processing across successive batches. These protections are code
changes, not yet cumulative-gate evidence.

## kspls0 source validation update — October 4, 2026

John directed that application tests, browser checks and builds for this
project run on `kspls0`. The finalization work has followed that target; no test
or build command has run on `kspld0`. The current integration source is based on
candidate merge commit `9e9a816c25c4a0045554e626a645e59d01e54b1e`, with 82 tracked
working-tree paths preserved on top (12,266 insertions and 83 deletions including
this record). `origin/main` is `4665245f97a90d546a94eb25fdcd4c91104bfd7b`; all
project-owned `origin/*`, local feature, and GitLab mirror branch tips are
ancestors of the candidate. The two local pre-rebase recovery refs and the 96
divergent `pr-author/*` and `upstream/*` refs are historical/external source
branches and are not merged into this fork candidate. The intervening origin
commit updates the YunoHost manifest to v3.51.0; both referenced release asset
SHA-256 digests were verified against the published GitHub release. This ref
inventory is documented for maintainer scope review before publication.

The first kspls0 preview used a `node_modules` symlink into an older baseline
tree. Its browser and build results are retained only as diagnostic iterations,
not as final-candidate evidence. A new candidate snapshot was copied from every
tracked working-tree path and installed from its pinned lockfile in isolation.
The focused issue regressions passed there: 76 Node tests across 8 suites for
request-list, software-search and settings contracts (zero failures, skips or
todos), plus 2/2 `RequestBlock` Vitest tests. That Node run covers per-user list
ownership, public URL validation, bounded scheduled sync, Questarr paged-search
fallback and the visible transport-error path.

The isolated kspls0 toolchain is Linux x86_64, Node `v24.21.0`, pnpm `10.24.0`,
with `pnpm-lock.yaml` SHA-256
`40cb5a6475750b19ec14a381df9ad13ec06b02fa37d9782240cb60da6c877830`. The
source-specific read-only `pnpm validate:development --plan --json` on the exact
staged and unstaged source snapshot discovered 579 files: 101 Vitest, 387 native
TypeScript, 58 native JavaScript and 33 Linux tooling files; there are no
platform exclusions in this Linux plan. Plan SHA-256 is
`71229966766ee4551321b70e1bc9250b866a8d0a42e1465ae799f21a1966cae8`. The
snapshot uses the complete candidate history/ref bundle (445 local, remote and
tag refs) plus separate index/worktree patches; its 3,325 tracked-source hashes,
modes, Git index and dirty status were compared byte-for-byte with the
integration worktree. The comprehensive runner has not been executed.

Before final validation, preserve both the source snapshot and exact Git
metadata, review the regenerated plan, expected-case inventory, dependency and
runtime hashes, and invocation details with the maintainer. The earlier issue
screenshots and build are iteration evidence only because their dependency link
did not satisfy the repository's source-isolation preflight. Fresh baseline and
fixed Playwright runs, the final build, complete validation gate, security
review of all integrated changes, exact-candidate visual acceptance and release
checks remain pending. No full-gate or release result is claimed.

## Complete local-branch integration and kspls0 candidate — October 4, 2026

The review candidate now includes the additional local project branch
`codex/reader-groupings-20261004` (tip `bace25a5e2146782a57a4268f0c60f6bcae461c3`)
as its second parent, together with all 82 paths from the preserved dirty source
layer. The integration tree is `c60902bbbbeb996774fb16ea55c6687b3dc9b216` in
validation snapshot commit `f23e8e9936e3d41cf03f81b3fd0e83f536b009c1`; its
other parent is `9e9a816c25c4a0045554e626a645e59d01e54b1e`. This snapshot is a
transfer and review identity, not a published commit. The local worktree and
index have no unresolved merge paths.

The 28 dirty paths that differ from the incoming branch were reconciled against
the current dirty source. They retain the newer Questarr/ROMarr DAT and platform
mapping contract, the explicit Edit Request media-identity props, and the current
security hardening. In particular, scheduled external-list sync is paged in
batches capped at 100; shared-game aggregation reads at most 20,001 rows and
returns a controlled limit error above 20,000; Steam keys remain redacted; and
Reader Delivery settings continue to require administrator permission. Branch
regressions for bounded sync, shared-library limits, settings permission and
edit requests without a media back-reference are retained.

Branch scope: current `origin/main` is `4665245f97a90d546a94eb25fdcd4c91104bfd7b`.
Project-owned `origin/*` tips and the GitLab mirror are already ancestors. The
reader-groupings feature branch is integrated above. The two pre-rebase recovery
refs remain recovery points; 96 `pr-author/*` and `upstream/*` refs belong to
external contributor/upstream histories and are not project feature branches to
merge into this fork.

The complete Git bundle was checked out on kspls0 at
`/tmp/seerrng-validation-final-merged-kspls0-20261004`. Its Git tree is
`c60902bbbbeb996774fb16ea55c6687b3dc9b216`; the lockfile digest is
`40cb5a6475750b19ec14a381df9ad13ec06b02fa37d9782240cb60da6c877830`. The
runtime there is Node `v24.21.0` with pnpm `10.24.0`; the frozen install
completed, with pnpm's existing ignored-build-script warning for `@scarf/scarf`
and `unrs-resolver` preserved. Native Linux tooling, including Docker, SQLite,
Python, Perl, tar, rsync, curl, zip/unzip and 7-Zip, is present on kspls0.

The fresh development-validation plan on that exact source discovers 579
selected files and zero exclusions: 101 Vitest, 387 native TypeScript, 58 native
JavaScript and 33 tooling files across 12 ordered steps. Structured plan SHA-256:
`ae0da149675ca6f7378fea0d0f059a150ea0f1f23e33c4f2b79e1bd7e00fda2a`;
expected-case inventory SHA-256:
`20259a5da1feb44cbc8bf35de0a18b8bc0f26eb940774f2e7a70836235805cfb`. This is
discovery only. Final issue-focused reproductions, the cumulative gate, the
final build and visual acceptance remain pending; no test or build has been run
on kspld0 for this task.
