---
name: Check resource availability
description: Find when field resources are available and which resources can take a job, using the Skedulo Availability API.
api: openapi/skedulo-availability-openapi.yml
operations: [getAvailability, postAvailability, postAvailableResources]
---

# Check resource availability

Use the Skedulo Availability service to determine resource availability windows and to
find resources that can perform a job in a time range.

## Auth
All requests use a Bearer JWT API token:
`Authorization: Bearer <token>`. Base URL: `https://api.skedulo.com` (or the regional host
`api.au|uk|ca.skedulo.com`). See `conventions/skedulo-conventions.yml`.

## Steps
1. **Fetch availability for known resources** — `GET /availability` (`getAvailability`) with a
   time range to read availability/unavailability windows. For large filters use
   `POST /availability` (`postAvailability`) to pass the filter in the body.
2. **Find available resources for a job** — `POST /availability/resources`
   (`postAvailableResources`) with the required time window and constraints to get the set of
   resources that are free.
3. Feed the resulting resource ids into scheduling (see the optimize-schedule and
   create-recurring-schedule skills) or dispatch.

## Notes
- Errors are JSON; check 400/401/403/404 per `errors/skedulo-problem-types.yml`.
- Date/time formats follow the Skedulo valid date-time formats guide.
