# crossby-media

Public media hosting for **Crossby** (@crossbyhoodies) social posts. Buffer and Instagram
fetch post images and videos from the permanent links below. Only post-ready media lives here.
Nothing private goes in this repo.

## Layout

```
YYYY-MM/<post-slug>/slide1.jpg ... slideN.jpg   # carousel, in posting order
YYYY-MM/<post-slug>/reel.mp4 (+ cover.jpg)      # reels
```

## Permanent link format

Always pin links to a commit SHA so they never change or break:

```
https://raw.githubusercontent.com/mbadzaghua/crossby-media/<commit-sha>/<path>
```

## Workflow (Claude + GitHub + Buffer)

1. Create or receive the media. Feed posts are 1080x1350 JPG, Reels are 1080x1920 H.264 MP4.
2. Copy them into `YYYY-MM/<post-slug>/`, commit, and push to `main`.
3. Build commit-pinned raw links and check each returns HTTP 200.
4. In Buffer (org "My organization", channel `crossbyhoodies`, id `6addff782f1f5ed648c87361`):
   - Before creating, list scheduled posts and skip anything already there (no duplicates).
   - Create or edit the post with the links as assets, alt text on every image,
     `metadata.instagram.type` = `post` (carousel = several images) or `reel`, `shouldShareToFeed: true`.
   - Schedule with `customScheduled` and a `dueAt` in Asia/Tbilisi (+04:00).
5. Confirm with Buffer that the post reads `scheduled` with the right number of assets.

Free plan limits: Buffer free allows 10 scheduled posts at a time; GitHub files max 100 MB.
