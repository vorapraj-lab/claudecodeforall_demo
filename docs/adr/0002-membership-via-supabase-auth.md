# Membership accounts via Supabase Auth, favorites stay per-device

The app was previously backend-free (see AGENTS.md), with all state — including Favorites — in per-device `localStorage` per [ADR-0001](./0001-favorites-in-local-storage.md). Adding member registration requires storing credentials somewhere durable and shared, which `localStorage` cannot do safely, so this is a deliberate, scoped exception: the app now depends on a Supabase project ("Thai Food", ref `zsgwuxdwawgvprkqkgyo`) for authentication only.

We used Supabase Auth (email + password) plus a `public.profiles` table (one row per member, holding `display_name`) rather than hand-rolling a custom members table, because the client only ever holds a publishable/anon key — Supabase Auth handles password hashing and session tokens server-side, which a hand-rolled table queried directly over PostgREST could not do safely. A `handle_new_user` trigger populates `profiles` on signup so the client never needs elevated privileges to write it; Row Level Security restricts every row to its own owner (`auth.uid() = id`).

This introduces email confirmation as a real UX state: a fresh signup may return no session (until the visitor confirms their email), which the UI surfaces explicitly rather than silently failing.

Scope boundary: this is membership only. Favorites remain exactly as ADR-0001 describes — private, per-device, `localStorage` — and are **not** written to Supabase or tied to a member account. Syncing favorites to a signed-in member's account was not requested and is an explicit non-goal for now; revisit ADR-0001 if that changes.
