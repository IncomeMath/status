# WorkdayTracker status

The live status and 90-day history of WorkdayTracker:
[status.workdaytracker.com](https://status.workdaytracker.com).

`index.html` is the whole page, served by GitHub Pages from this branch. It holds no data:
the browser reads `status/status.json` from the public bucket `incomemath.com`
(https://storage.googleapis.com/incomemath.com/status/status.json), which the product's
status job (`services/jobs/status-checks`) replaces every five minutes. Because neither the
page nor the file is served by WorkdayTracker's own servers, the page stays up when
production is down, and when the file stops changing the page says the checks stopped.

To work on the page locally, write a file with the job's `--json-to` and serve this folder:

```bash
python3 -m http.server 8000   # then open http://localhost:8000/?src=status.json
```
