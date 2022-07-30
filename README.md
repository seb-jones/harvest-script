Small BASH script that (re)starts Harvest timers on today's timesheet.

## Dependencies

- [jq](https://stedolan.github.io/jq/)
- [curl](https://curl.se/)

## Installation

Clone this repo and `cd` into it:

```sh
git clone https://github.com/seb-jones/harvest-script.git && cd harvest-script
```

Ensure the script file has execute permissions:

```sh
chmod u+x ./hv
```

`export` the following variables from your `.bashrc` (or the relevant configuration file if using another shell) so that they can be accessed by the script.

```sh
HARVEST_ACCOUNT_ID='xxx'
HARVEST_API_TOKEN='xxx'
HARVEST_USER_ID='xxx'
```

`HARVEST_ACCOUNT_ID` and `HARVEST_API_TOKEN` are obtained by going to the [Harvest Developers](https://id.getharvest.com/developers) page and creating a personal access token.

Your `HARVEST_USER_ID` can be found by going to 'My profile' in Harvest and looking at the URL in the address bar. For instance if the URL was `/people/123456/edit` then your User ID is `123456`.

You will probably also want to add the directory to your `PATH` so that you can run the script from anywhere.

## Usage

```
hv project_id task_id [notes]
```

Starts a timer on the current day for the given `project_id` and `task_id`, optionally with `notes`. If a timesheet entry already exists on the current day with identical `project_id`, `task_id` and `notes`, then the timer for that entry is resumed instead.
