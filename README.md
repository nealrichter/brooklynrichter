# Brooklyn Richter — Personal Athletic Profile Site

A single-page static website for Brooklyn Richter, #35, Murray High School Girls Basketball.

## What It Does

- Three-tab layout: **Posts**, **Videos**, **Stats**
- Posts feed pulled from Google Sheets and Tumblr RSS, merged and sorted newest-first
- Videos tab embeds Cloudflare Stream and Instagram content from a `public_videos` Google Sheet tab
- Stats tab shows EYBL, high school basketball career stats, and swim championship results
- Instagram posts auto-embed when detected in post links
- Responsive design: desktop sidebar collapses to a mobile header on small screens
- Sticky tab navigation
- Hash-based routing (`#posts`, `#videos`, `#stats`) for shareable links
- AI-discoverable via `llms.txt`, `robots.txt`, and `sitemap.xml`
- Murray High School color scheme (`#F05423` orange, `#231F20` dark)

## Tech Stack

- Single HTML file with inline CSS and JS (no build step, no dependencies)
- GitHub Pages hosting with custom domain
- Cloudflare DNS
- Cloudflare Stream for video hosting
- Google Sheets as a headless CMS (posts + videos)
- Tumblr RSS via rss2json for media posts
- Favicon generated from headshot via sips/Python

## Structure

```
index.html              # Single-page app (all HTML, CSS, JS inline)
BrooklynFace.png        # Headshot (avatar)
murray_spartans_logo.png
murray_high_logo.png
favicon.ico
llms.txt                # AI-readable player profile
robots.txt
sitemap.xml
BingSiteAuth.xml        # Bing verification
CNAME                   # Custom domain for GitHub Pages
README.md
```

## Data Sources

| Source | How to update |
|--------|--------------|
| Posts | Edit the [Google Sheet](https://docs.google.com/spreadsheets/d/1BpfE6ehYIZ3eE3-PwEDmitMd9iTGN8IqHsWlU2gJA8g) (Sheet1) |
| Videos | Edit the `public_videos` tab in the same Google Sheet |
| Media posts | Post to [Tumblr](https://www.tumblr.com/brooklynrbasketball) |

### Google Sheet Columns (Posts - Sheet1)

| Column | Description |
|--------|-------------|
| `datetime` | Display date (e.g. `12/17/2025`) |
| `post_title` | Bold title shown above body text |
| `post_text` | Body of the post (supports markdown bold/italic/links) |
| `link_text` | Label for the optional link button |
| `post_link` | URL for the link button (Instagram URLs auto-embed) |
| `video_link` | YouTube or Hudl URL |

### Google Sheet Columns (Videos - public_videos)

| Column | Description |
|--------|-------------|
| `datetime` | Display date |
| `video_type` | `SHORT` or `LONG` (controls icon: 🎬 or 🎦) |
| `post_text` | Description shown above the embed |
| `video_link` | Cloudflare Stream `/watch` URL or Instagram reel URL |

## Running Locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploying

Push to GitHub and enable **GitHub Pages** (Settings → Pages → Deploy from `main` branch).

## Repository

[https://github.com/nealrichter/brooklynrichter](https://github.com/nealrichter/brooklynrichter)

## Live Site

- [brooklynrichter.com](https://brooklynrichter.com)
- [llms.txt](https://brooklynrichter.com/llms.txt)
- [robots.txt](https://brooklynrichter.com/robots.txt)

## Extracting YouTube Clips

```bash
yt-dlp --download-sections "*START-END" --merge-output-format mp4 -o "clip_name.mp4" "URL"
```

## Merging MP4 Files

```bash
printf "file 'clip1.mp4'\nfile 'clip2.mp4'\nfile 'clip3.mp4'\n" > list.txt
ffmpeg -f concat -safe 0 -i list.txt -c copy merged.mp4
rm list.txt
```
