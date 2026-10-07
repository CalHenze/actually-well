# Actually Well — Feed Repository

Central feed for the [Actually Well](https://www.youtube.com/@Actually-Well) YouTube channel banner displayed across the Henze & Associates network of sites.

## How it works

`feed.json` is the single source of truth. All site banners load it on page render.

## feed.json fields

| Field | Purpose |
|-------|---------|
| `live` | `true` = banner visible. `false` = banner hidden on all sites. |
| `launchDate` | ISO date string. Banner also shows automatically on/after this date even if `live` is false. |
| `featured` | **Manual override.** Set this to a YouTube video ID to pin a specific episode. Clears the automatic selection. Set to `null` to resume automatic mode. |
| `latest` | Auto-maintained by GitHub Action. The most recent video ID from the YouTube RSS feed. Never edit manually. |
| `latestTitle` | Auto-maintained. Title of the latest video. |
| `channelId` | YouTube channel ID — do not change. |
| `channelUrl` | YouTube channel URL — do not change. |

## Workflow: Launch

1. Set `"live": true` and `"launchDate"` to today's date in `feed.json`
2. Set `"featured"` to the video ID you want to highlight from the launch batch
3. Commit and push — all banners go live immediately

## Workflow: Featuring a specific episode

Edit `feed.json`, set `"featured": "VIDEO_ID_HERE"`, commit and push.

## Workflow: Return to automatic (latest video always shown)

Edit `feed.json`, set `"featured": null`, commit and push.

## Finding a YouTube video ID

The video ID is the `v=` parameter in a YouTube URL:
`https://www.youtube.com/watch?v=`**`dQw4w9WgXcQ`**
