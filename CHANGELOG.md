# Changelog

All notable changes to this project will be documented in this file.

## v0.2.0 - 2025-11-12

Highlights
- Per-item Findings notes with Save / Clear and saved/unsaved indicator.
- Firestore per-user persistence for checklist progress (collection: `progress`, doc id: `${userId}_${itemId}`).
- JS masonry layout that preserves left-to-right ordering for cards.
- Smooth expand/collapse animations and inner content fade/slide.
- Login fixes and consolidation to Firebase Web SDK v12; added logout and auth guard.

Details
- index.html
  - Added Firestore helpers to persist per-user note and completion state (`setProgressDoc`, `subscribeToUserProgress`).
  - Implemented Findings UI (textarea + Save / Clear), localStorage fallback, and saved/unsaved visual indicator.
  - Require saved Findings before allowing an item to be unchecked (client-side enforcement).
  - Replaced grid flow gap issues with a JS masonry implementation that preserves reading order.
  - Improved expand/collapse UX using measured max-height animations and inner opacity/translate transitions.
  - Added logout button and wired auth guard to initialize app state after sign-in.

- login.html
  - Rewrote sign-in page to use Firebase Web SDK v12 modular imports and email/password sign-in.
  - Removed Google sign-in control per request.

Notes
- Firestore schema: collection `progress` with documents named `${userId}_${itemId}` and fields: `userId`, `itemId`, `completed` (bool), `note` (string), `updatedAt` (serverTimestamp).
- Add server-side security rules in your Firebase Console to ensure users can only read/write their own `progress` docs.

Commit: a6b0893
