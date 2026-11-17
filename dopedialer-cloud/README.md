# DopeDialer — Cloud-ready prototype

Open `index.html` locally to use browser-only mode. For cloud synchronization, host it over HTTPS (for example, Netlify or Vercel), create a Supabase project, and run `schema.sql` in the SQL editor. In Supabase Auth, enable email/password sign-in and configure email confirmation as desired. In the app's Cloud Sync panel, paste the project URL and **publishable/anon** key (never a service-role or secret key). Sign up and sign in.

The app saves lead changes to the authenticated user's row-level-secured database and retrieves them on sign-in. A browser-only backup remains available with CSV export. The configuration is stored in the current browser. The prototype does not yet include nationwide lead discovery, background refresh, or automatic Google Voice call logging. Google Voice launch remains a manual handoff. Use only compliant lead sources and honor do-not-call requests.

## Limitations
- Initial migration merges browser leads into the account after sign-in; if records share IDs, the current browser copy wins. Export CSV before migration.
- Sync uses one request per saved batch; wait for the status indicator after edits. For production, use a server-side API, conflict resolution, incremental sync, audit logs, and structured contacts/activity tables.
- No API secret should be embedded in this static site. Supabase publishable/anon keys are designed for clients with RLS; the user JWT governs access.

## New: nationwide discovery staging

See `discovery/README.md` for a market-filtered Google Places API importer, dry-run support, and CRM-compatible CSV output. This is a **manual staging workflow**, not yet scheduled or connected directly to the Supabase database. API access and billing must be configured by the owner.
