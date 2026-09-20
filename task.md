ส# Task List — ป้ายเมนูไทย (Thai Menu Sign)

Derived from [`CONTEXT.md`](./CONTEXT.md). Each section maps one glossary term to the concrete build task(s) needed to realize it. Status reflects the current published artifact (v4).

## Dish

- [x] Define a `Dish` data shape: name (TH + EN), region, category, spice index — one entry per item in the library
- [x] Give every dish a short, appetizing description (no lorem/placeholder text)

## Dish Library

- [x] Build the full library — 20 dishes, spanning all 4 regions of Thailand (กลาง, อีสาน, เหนือ, ใต้)
- [x] Render every dish from the library on the page — nothing held back from view
- [x] Group dishes into browsable categories (จานเดียว, ซุป, แกง, ยำ/ลาบ, ปิ้งย่าง, น้ำพริก, ของหวาน)
- [x] Make category filter chips functional (click to filter the listing, not just decorative labels)
- [x] Give each category its own illustrated icon (custom SVG, since real food photos can't be hotlinked into an Artifact)

## Signature Dish

- [x] Mark a subset of dishes as signature (Pad Thai, Tom Yum Goong, Som Tam, Khao Soi, Khua Kling)
- [x] Render a distinct badge on signature dishes in the listing
- [x] Document the badge in a short legend near the listing

## Spice Index

- [x] Store a 0–3 spice rating per dish
- [x] Render it as filled vs. unfilled chili marks, with an `aria-label` describing the level in words

## Today's Dish

- [x] Build the random picker: a new pick replaces the current one on every click
- [x] Exclude dishes already surfaced earlier the same local calendar day
- [x] Reset the "already shown" set at local midnight
- [x] Once the whole library has cycled through in a day, allow repeats again (no dead-end button)
- [x] Show a progress caption ("สุ่มไปแล้ว X จาก 20 เมนูวันนี้")
- [x] Auto-pick a dish on first page load so the page opens in a populated state, not an empty prompt

## Favorites

- [x] Add a heart-toggle affordance on every dish card (listing rows, Today's Dish, Favorites list)
- [x] Persist favorites in the visitor's own browser `localStorage` — private per device, per [ADR-0001](./docs/adr/0001-favorites-in-local-storage.md)
- [x] Wrap all `localStorage` reads/writes in `try/catch` so the page still works with storage blocked or unavailable
- [x] Render a dedicated "รายการโปรดของฉัน" section
- [x] Show an empty-state message when nothing is saved yet

## Possible next steps (not yet requested)

- [ ] Add more dishes to the library beyond the current 20
- [ ] Let visitors clear all saved favorites in one action
- [ ] Surface the visitor's spice-level preference (e.g. default-filter to a max spice level)
