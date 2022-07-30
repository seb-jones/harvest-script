Small BASH script that (re)starts Harvest timers on today's timesheet.

## Dependencies

- [jq](https://stedolan.github.io/jq/)
- [curl](https://curl.se/)

## Usage

```
hv project_id task_id [notes]
```

Starts a timer on the current day for the given `project_id` and `task_id`, optionally with `notes`. If a timesheet entry already exists on the current day with identical `project_id`, `task_id` and `notes`, then the timer for that entry is resumed instead.
