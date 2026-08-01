---
name: Create a recurring schedule
description: Create and manage recurring job schedules and their resource allocations in Skedulo.
api: openapi/skedulo-recurring-openapi.yml
operations: [listRecurringSchedules, preview, createRecurringSchedule, upsertJobAllocations]
---

# Create a recurring schedule

Generate repeating jobs from a recurrence pattern and allocate resources to them.

## Auth
Bearer JWT API token. Base URL: `https://api.skedulo.com/recurring`.

## Steps
1. **Preview** — `POST /schedules/jobs/preview` (`preview`) to see the jobs a recurrence pattern
   would generate before committing.
2. **Create the recurring schedule** — `POST /schedules/jobs` (`createRecurringSchedule`) with
   the base job and recurrence pattern.
3. **Allocate resources** — `POST /schedules/job_allocations` (`upsertJobAllocations`) to
   create/update resource allocations across the generated jobs.
4. **Review** — `GET /schedules` (`listRecurringSchedules`) to list recurring schedules and
   confirm the result.

## Notes
- Use availability (see check-resource-availability skill) to pick eligible resources first.
- Delete allocations with `POST /schedules/job_allocations/delete`.
