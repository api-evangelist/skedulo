---
name: Run a schedule optimization
description: Start a Skedulo optimization run, poll for results, and save the optimized schedule.
api: openapi/skedulo-optimization-openapi.yml
operations: ["Schedule Run", "Get Schedule Run By Id", "Get Schedule Run Results", "Schedule Run Save"]
---

# Run a schedule optimization

Use the Optimization Manager API to auto-schedule jobs to resources, then review and persist
the result.

## Auth
Bearer JWT API token. Base URL: `https://api.skedulo.com/optimization`.

## Steps
1. **Start a run** — `POST /schedule` (operationId `Schedule Run`) to kick off a one-off
   optimization run over a scope of jobs and resources.
2. **Poll the run** — `GET /schedule/run/{runId}` (`Get Schedule Run By Id`) until the run
   completes.
3. **Read the results** — `GET /schedule/run/{runId}/results` (`Get Schedule Run Results`) to
   inspect the proposed allocations and routes.
4. **Save (or reject)** — `POST /schedule/run/{runId}/save` (`Schedule Run Save`) to commit the
   optimized schedule. Use the reject/defer variants to discard or postpone auto-save.

## Notes
- For lighter-weight recommendations use the **Suggest** endpoint (`POST /suggest`).
- Check tenant limits with `GET /limits` before large runs.
