Small BASH script that (re)starts Harvest timers on today's timesheet.

## Dependencies

- [jq](https://stedolan.github.io/jq/)
- [curl](https://curl.se/)

## Installation

Clone this repo and `cd` into it:

```sh
git clone https://github.com/seb-jones/harvest-script.git && cd harvest-script
```

Ensure the script files have execute permissions:

```sh
chmod u+x ./hv*
```

`export` the following variables from your `.bashrc` (or the relevant configuration file if using another shell) so that they can be accessed by the script.

```sh
export HARVEST_ACCOUNT_ID='...'
export HARVEST_API_TOKEN='...'
export HARVEST_USER_ID='...'
```

`HARVEST_ACCOUNT_ID` and `HARVEST_API_TOKEN` are obtained by going to the [Harvest Developers](https://id.getharvest.com/developers) page and creating a personal access token.

Your `HARVEST_USER_ID` can be found by going to 'My profile' in Harvest and looking at the URL in the address bar. For instance if the URL was `/people/123456/edit` then your User ID is `123456`.

You will probably also want to add the directory to your `PATH` so that you can run the script from anywhere.

## Usage

```sh
hv project_id task_id [notes]
```

Starts a timer on the current day for the given `project_id` and `task_id`, optionally with `notes`. If a timesheet entry already exists on the current day with identical `project_id`, `task_id` and `notes`, then the timer for that entry is resumed instead.

The recommended usage of this command is to set up aliases for tasks you do repeatedly, for example:

```sh
alias coffee="hv 'internal_project_id' 'unproductive_task_id' 'Making Coffee'"
```

To get the `project_id` and `task_id`, you can use the following command that is also included in this repo:

```sh
hvls
```

This outputs all Harvest Tasks that you have permission to access, along with their Client and Project, as a stream of rows with tab-separated columns. The first column is the Client name, the second column is the Project name and ID, and the third column is the Task name ID. One row is printed per task. I recommend piping the output of this into `sort` and `grep` or `less` to filter the project or task you are looking for, for instance:

```sh
hvls | sort | grep -i unproductive
```

## Licence

> This code is Copyrighted in U.K., under The Unlicense, for a period of 28 years, and anybody caught usin' it without our permission, will be mighty good friends of ourn, cause we don't give a dern. Edit it. Use it. Hack it. Redistribute it. Yodel it. We wrote it, that's all we wanted to do.
