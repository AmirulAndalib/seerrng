# Grimmory and BookOrbit reader delivery integration journal

## Recovery identity

- Starting repository revision: `a96fafa07c77a2d6d95badeb9f60c32a6b4a47c9`.
- The initial reader implementation was kept in the recovery snapshot/stash
  recorded in the game-library integration journal. It is now integrated into
  `/tmp/seerrng-reader-groupings` on top of current `origin/main`.
- The initial user work included external request-list sync settings, software
  routes, entity, and migrations; subsequent external-list files remain
  separately attributable in the combined candidate.

## Scope and decisions

- Keep Bookshelf as the acquisition and availability source.
- Integrate Grimmory and BookOrbit through their documented OPDS catalogs and
  Grimmory's documented Komga API. Do not copy either application's code or
  depend on server APIs that lack a stable published contract.
- Keep Grimmory as the default preferred app. When its address is empty, use a
  configured BookOrbit address for the book-page handoff without changing the
  saved preference.
- Media pages open the configured reader service's web library. E-reader
  clients get the generated OPDS address in Settings > Services > Reader Apps;
  comic clients get Grimmory's separate Komga address there. Grimmory's
  audiobook link opens its built-in library player.
- Book, comic, and magazine pages offer protected direct downloads for files
  attached to the signed-in user's available requests. Book downloads preserve
  the ebook/audiobook distinction, including combined requests; comic and
  magazine downloads list available issues. Request Status is filtered by the
  exact internal media ID and signed-in user, and download routes recheck
  requester and request-view permissions before each file stream. Downloads
  save through the browser on the current device; they do not push files to an
  e-reader or sync progress.
- Partial provider failures preserve any copies already resolved and report
  that lookup was incomplete instead of presenting the result as an empty
  library.
- The initial URL/handoff implementation stored only HTTP or HTTPS app
  addresses. The later managed-shelf phase below adds a separate SeerrNG
  administrator account for shelf operations and redacts its passwords from
  API responses. OPDS reader credentials, scan results, device state, reading
  progress, and annotations remain in the companion app.

## File record

- server/lib/settings/index.ts: added the reader-delivery type, empty URL
  defaults, Grimmory preference, settings field, and getter. This file also
  contains pre-existing external-request-list changes; those are user-owned.
- server/routes/settings/readerDelivery.ts: added admin-only settings
  retrieval and persistence, redacted account credentials, URL validation,
  normalization of pasted OPDS addresses, connection checks, rule previews,
  live shelf create/update/delete, and durable SeerrNG mapping state.
- server/routes/settings/readerDelivery.test.ts and
  server/api/readerDelivery.test.ts: cover secret redaction, access controls,
  provider-specific filters and payloads, preview/count states, empty-rule
  consent, upserts, BookOrbit visibility constraints, and managed deletion.
- server/entity/ReaderDeliveryGrouping.ts and the SQLite/Postgres
  `1791030000000-CreateReaderDeliveryGroupings` migrations: persist only the
  target-to-provider shelf mapping and operation status; reader files and
  catalog contents stay in the reader service.
- src/components/Common/ReaderGroupingAction.tsx and
  src/components/Settings/ReaderDeliverySettings.tsx: expose shelf preview,
  save, visibility/Kobo options, status/count, and removal to administrators.
- AuthorDetails, BookSeriesDetails, and ComicDetails: add the shelf action to
  relevant author and series pages.
- seerr-api.yml: documents the admin reader settings, connection test, managed
  shelf listing, preview, save, and delete contracts.
- server/routes/settings/index.ts: mounted the reader-delivery settings API.
- server/routes/service.ts: added the authenticated handoff summary, selecting
  the preferred configured app or falling back to the other app without
  changing preference.
- server/routes/request.ts and server/lib/requestStatus.ts: added exact
  media-ID filtering to Request Status for the book-page lookup.
- server/interfaces/api/requestInterfaces.ts: added the shared Request Status
  media-ID query and typed download asset response, including book-file format.
- seerr-api.yml: documented the Request Status mediaId query parameter, typed
  book-file format and partial download-lookup status, and the reader-service
  handoff endpoint. This file also has a separate user-owned
  external-request-list change.
- src/components/Settings/ReaderDeliverySettings.tsx: added Grimmory and
  BookOrbit address fields, generated OPDS addresses, copy fallback, preference
  selection, setup links, save and discard states, and shared-library guidance.
- src/components/Settings/SettingsServices.tsx: placed reader configuration
  after Bookshelf services.
- src/components/BookDetails/index.tsx, ComicDetails/index.tsx,
  MagazineDetails/index.tsx: connect page actions to the matching reader
  library and protected per-request download workflow.
- src/components/Common/ReaderDeliveryLink.tsx: opens the reader web library,
  and explains where to copy OPDS or Komga addresses for reader apps. Grimmory
  remains the default and audiobook player target; BookOrbit remains the
  configured fallback and its archive/PDF capability is described separately.
- src/components/Common/RequestDownloadAction.tsx: scopes Request Status to the
  current user, exact media ID and media type; supports one or many assets,
  partial lookup errors and a useful Request Status fallback. Combined book
  requests show only the selected ebook or audiobook format.
- server/lib/requestDownloadAssets.ts and seerr-api.yml: preserve file format
  metadata, retain successful assets when one combined-request Bookshelf lookup
  fails, and return an explicit partial-error indicator without provider paths
  or credentials.
- docs/using-seerr/reader-delivery.md and docs/README.md: added operator setup
  and troubleshooting guidance, device download steps, and indexed the guide.
- src/i18n/locale/en.json: extracted the new book-page and reader-settings
  messages. The extractor also captured labels from the separate external-list
  component already present in the working tree; that user-owned source was not
  changed here.
- release-notes/2026-10-04-reader-service-delivery.md: documented the OPDS and
  direct-download workflows in the user-facing release fragment.

No stylesheet changes were needed. Focused regression cases were added for
exact-media Request Status filtering, malformed media IDs, the Request Status
OpenAPI contract, and safe download-file resolution.

## Unrelated work preserved

The following existing or concurrent external-request-list changes were not
modified as part of reader delivery (the single mediaId parameter addition in
the shared OpenAPI file is reader delivery work):

- server/routes/software.ts and server/routes/software.test.ts
- server/lib/settings/index.ts external-request-list job type and schedule
- server/job/schedule.ts
- server/routes/index.ts
- seerr-api.yml
- server/entity/ExternalRequestList.ts
- server/lib/externalRequestLists.ts
- server/lib/externalRequestLists.test.ts
- server/lib/settings/migrations/0021_add_external_request_list_sync_job.ts
- server/lib/settings/migrations/0021_add_external_request_list_sync_job.test.ts
- server/migration/postgres/1791010000000-CreateExternalRequestLists.ts
- server/migration/sqlite/1791010000000-CreateExternalRequestLists.ts
- server/migration/sqlite/1791010000000-CreateExternalRequestLists.test.ts
- server/routes/externalRequestLists.ts
- server/routes/externalRequestLists.test.ts
- src/components/UserProfile/UserSettings/UserGeneralSettings/index.tsx
- src/components/UserProfile/UserSettings/UserGeneralSettings/ExternalRequestLists.tsx
- the external-list message additions in src/i18n/locale/en.json were emitted
  by the shared catalogue extractor for that existing user-owned component.

The reader-grouping capability is now mounted and exposed in the admin UI. It
manages rule-based shelves only; it does not create reader-library entries or
copy, move, or delete reader files. Provider operations use bounded previews,
explicit opt-in for empty rules, a durable local mapping, and redacted service
credentials.

### Earlier grouping checkpoint — superseded

At an earlier integration checkpoint, `server/api/readerDelivery.ts`,
`ReaderDeliveryGrouping`, and the `1791030000000-CreateReaderDeliveryGroupings`
migrations existed but were not mounted by the reader-delivery routes. That
checkpoint correctly described them as internal groundwork at the time. The
live routes, settings controls, detail-page action, API contract, and focused
regression coverage described above supersede that implementation status.

## Verification and acceptance

- Source review: inspected the changed reader-delivery paths and their existing
  settings and Bookshelf owners, including the existing request-level download
  authorization and file resolution path.
- Runtime: Node.js 24.15.0 from the official Node archive with its published
  SHA-256 verified; pnpm 10.24.0 from the repository toolchain.
- Focused automated checks: Request Status exact-media/current-owner case
  passed (1/1); malformed media ID validation passed (1/1); reader settings and
  preferred-app fallback tests passed (3/3); Request Status OpenAPI tests passed
  (7/7); mapped-download asset tests passed (3/3), including the ebook/audiobook
  split for a combined request.
- TypeScript: server and client type checks passed. Targeted ESLint and Prettier
  checks passed for the changed application and route files.
- UI batch: current-batch contract passed (557 files); shared-style reference
  audit inspected 386/386 components; its behavior checks passed (68/68).
- Translation catalogue: `i18n:check` passed after extracting the English
  messages from the current source tree.
- Whitespace: `git diff --check` passed.
- A first Vitest invocation included an unnecessary `--` separator and was
  interrupted after it failed to select the requested file. The correctly
  scoped Vitest command then completed successfully; the interrupted run is not
  counted as evidence.
- An intermediate OpenAPI run caught indentation that placed the new optional
  book-file format outside the download asset schema. The schema was corrected,
  and the final OpenAPI suite then passed (7/7).
- Full development validation, production build, full-repository lint, and
  release-note preview: not run.
- Rendered preview and human visual review: pending; no safe disposable preview
  instance was available. The source/style checks above do not prove that the
  rendered page works or looks correct.
- Grimmory, BookOrbit, and e-reader OPDS round trips: pending; no live reader
  service was configured or contacted.
- No change is staged, published, or deployed.

## Combined candidate update — October 4, 2026

- Forward-integrated upstream Audiobookshelf/ChaptarrNG and v3.50.0 release
  preparation. Reader settings and download actions were preserved across the
  shared Settings Services, Book Details, Request Status, request API, and
  OpenAPI files.
- Shared English catalog extraction also includes the independently preserved
  game-library and external-request-list strings.
- The cumulative development gate, production build, isolated rendered preview,
  and human visual acceptance are pending on the combined final candidate.
- The first integrated validation attempt stopped at formatting before test
  execution. Twenty-two candidate files were formatted; no test results were
  counted from that attempt.
- Grimmory, BookOrbit, OPDS, and live Bookshelf delivery round trips remain
  unverified; the implementation uses mocked/unit/provider-boundary evidence.

## Audiobook, comic, and magazine extension — October 4, 2026

This extension expands the existing ebook reader workflow. Grimmory supports
ebooks through OPDS, M4B/M4A/MP3 audiobooks through its player, and comics
through the Komga API. BookOrbit provides OPDS for ebooks, supported CBZ/CBR
comic archives, and PDFs. Magazine PDFs must be imported into either reader
library as ordinary PDF files. Neither service is documented here as a
magazine-specific catalog or as BookOrbit audiobook playback.

Book, comic, and magazine details now include format-aware protected download
actions when the signed-in user has an available request with a resolvable file.
These use existing service path mappings and Mylar's issue stream. Provider
errors are reported separately from no-copy results, and combined book requests
continue checking the second format when the first provider fails.

Current extension verification after the last source edits:

- Focused Vitest: 3 files, 16 tests passed (download actions, reader links,
  resolved path downloads and partial combined-request errors).
- Focused Node API tests: 3 files, 8 tests passed (reader settings validation
  and fallback, download response OpenAPI contract, and reader handoff route).
- Focused Request Status integration tests: 2 tests passed (exact media ID and
  requester filtering; malformed media ID rejection).
- Server and client TypeScript checks passed; focused ESLint passed; Prettier,
  translation catalogue and whitespace checks passed.
- Shared UI batch check passed: current-batch contract covers 561 files, shared
  style references inspect 390 components, button geometry 68/68 passed.
- The local validation plan was inspected: 95 Vitest, 376 native TypeScript,
  56 native JavaScript and 32 tooling files selected, with no declared platform
  exclusions. The complete cumulative gate has not run on an isolated reader
  candidate; the checkpoint records earlier unrelated cumulative failures and
  unavailable tool inputs that must be reconciled before a release claim.
- Rendered preview and John's visual acceptance remain pending. The in-app
  browser and isolated workspace browser tools were not exposed in this
  session. No live Grimmory, BookOrbit, OPDS app, or e-reader round trip ran.
- User-owned external request-list and software catalog changes remain outside
  the reader-delivery candidate and must not enter its commit.
