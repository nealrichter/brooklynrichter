# Brooklyn Richter — Personal Athletic Profile Site

A single-page static website for Brooklyn Richter, #35, Murray High School Girls Basketball.

## What It Does

- Displays a Twitter/X-style post feed pulled from two sources:
  - **Google Sheets** — manually curated posts (game stats, news, achievements)
  - **Tumblr** ([brooklynrbasketball](https://www.tumblr.com/brooklynrbasketball)) — via RSS feed through rss2json
- Posts from both sources are merged and sorted newest-first
- Sidebar shows bio info: school, EYBL team, GPA, ACT, season stats, and links
- Murray High School color scheme (`#F05423` orange, `#231F20` dark)

## Structure

```
index.html              # Single-page app (all HTML, CSS, JS inline)
murray_spartans_logo.png
murray_high_logo.png
README.md
```

## Data Sources

| Source | How to update |
|--------|--------------|
| Posts | Edit the [Google Sheet](https://docs.google.com/spreadsheets/d/1BpfE6ehYIZ3eE3-PwEDmitMd9iTGN8IqHsWlU2gJA8g) |
| Media posts | Post to [Tumblr](https://www.tumblr.com/brooklynrbasketball) |

### Google Sheet Columns

| Column | Description |
|--------|-------------|
| `datetime` | Display date (e.g. `12/17/2025`) |
| `post_title` | Bold title shown above body text |
| `post_text` | Body of the post |
| `link_text` | Label for the optional link button |
| `post_link` | URL for the link button |
| `video_link` | YouTube or Hudl URL — auto-labeled as "YouTube Game Video" or "Hudl Game Video" |

## Running Locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Deploying

Push to GitHub and enable **GitHub Pages** (Settings → Pages → Deploy from `main` branch).

## Repository

[https://github.com/nealrichter/brooklynrichter](https://github.com/nealrichter/brooklynrichter)
