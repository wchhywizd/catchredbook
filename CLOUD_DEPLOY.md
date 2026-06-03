# Cloud Deploy

This app is deployment-ready for a Python web service.

## Render

1. Push this folder to a Git repository.
2. In Render, create a new Web Service from that repository.
3. Use:
   - Build command: `python3 -m py_compile server.py`
   - Start command: `HOST=0.0.0.0 python3 server.py`
4. Open `/小红书舆情监管.html` on the deployed domain.

## Notes

- `opinion-data/` is local JSON storage. On most free cloud hosts, filesystem data may reset across deploys or restarts.
- For production monitoring, replace local JSON files with a managed database or object storage.
- Real Xiaohongshu logged-in scraping still depends on a logged-in browser/session and platform limits; the cloud service itself cannot reuse your local browser login state.
- The first monitoring run is configured to backfill the previous 7 days by default. Later daily runs focus on the latest 1 day.
- If the report imports fewer than the configured crawl limit, the usual cause is that the logged-in Xiaohongshu search page has only loaded that many cards. Scroll the search results page to load more cards before importing.
