# Using the Command-Line Interface (CLI)

The *Command-Line Interface tool* is a standalone program distributed with the server application of this plugin. 
Its main purpose is the management of the server and the database while the
server process is running. The application is called ```spannersctl```.

## Available commands ##

**User commands:**
```
spannersctl user { block <user> | unblock <user> | delete <user> | list | info <user> }
```
* `block <user>` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;          Block the user from submitting any further requests
* `unblock <user>`&nbsp;&nbsp;&nbsp;         Unblock a blocked user
* `delete <user>` &nbsp;&nbsp;&nbsp;&nbsp;         Delete the user and all associated jobs
* `list` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;                  List all users
* `info <user>` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;           Print detailed information about a single user

Users can be identified by their name or ID.  
Example: `spannersctl user info user_x`

**Job commands:**
```
spannersctl job { delete <job> | stop <job> | list | info <job> }
```
* `delete <job>` &nbsp;&nbsp;         Delete the job
* `stop <job>`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;             Stop the job if it is currently running
* `list`  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;                 List all jobs
* `info <job>` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;            Print detailed information about a single job

Jobs can be identified by their ID.  
Example: `spannersctl job delete 123`

**Scheduler commands:**
```
spannersctl scheduler { time-limit | process-limit | resource-limit | sleep } [value]
```
* `time-limit [value]` &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;    Read or modify the time limit for each task on the server in milliseconds
* `process-limit [value]`&nbsp;&nbsp;&nbsp;&nbsp;  Read or modify the limit of concurrent jobs
* `resource-limit [value]`&nbsp;&nbsp; Read or modify the amount of memory a single job can allocate in bytes
* `sleep [value]`&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;          Read or modify the waiting intervall between scheduling jobs in milliseconds

If the optional argument is omitted, the current value of the selected option is fetched.
If the optional argument is given, the argument will be set as the new value.  
Example: `spannersctl scheduler time-limit 123`

### Notes ###

* The CLI tool must be run on the same machine the server application is running
  on.
* The server application must be running while the CLI tool is used because all
  commands will be interpreted by the server.
* Changing the scheduler parameters does **not** modify the configuration file.
  To keep the changes after a restart, the configuration file must be adjusted
  manually.
