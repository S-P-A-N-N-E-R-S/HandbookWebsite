# Backend Configuration
The backend provides various configuration options that can be used to adapt the system to different environments. 
These configuration parameters can be set through command-line options, environment variables and a configuration file.
The mentioned order indicates the prioritization if the same option is set in multiple places. 
Thus, command-line options are always dominant. But the preferred way to configure the backend is the configuration file, as it stores the configuration persistently.

## Config File
By default, the configuration file is located under `~.config/spanners/server.cfg` and is created when the server is started 
for the first time or no file exists. If the [`$XDG_CONFIG_HOME`](https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html) 
environment variable is set, the file is saved in `spanners/server.cfg` relative to the directory specified in the 
`$XDG_CONFIG_HOME` environment variable. The initial created configuration file contains some options with default values.
If an option is not set, the corresponding default value will be used. The configurations are defined as key-value 
pairs, e.g. `server-port=4712` to set the server port to 4712.

The following options are available:

| Option                     | Default Value           | Description                                                                                     |
|-------------------------------------|-----------------------|------------------------------------------------------------------------------------------|
| `server-port`              | `4711`                  | server port                                                                                     |
| `db-host`                  | `localhost`             | database host                                                                                   |
| `db-port`                  | `5432`                  | database port                                                                                   |
| `db-user`                  | `spanner_user`          | database user                                                                                   |
| `db-name`                  | `spanner_db`            | database name                                                                                   |
| `db-password`              | `pwd`                   | database password                                                                               |
| `db-timeout`               | `10`                    | database timeout in seconds                                                                     |
| `scheduler-exec-path`      | `./src/handler_process` | absolute path to the handler_process executable                                                 |
| `scheduler-process-limit`  | `4`                     | maximum number of processes to schedule parallel                          |
| `scheduler-time-limit`     | `0`                     | scheduler time limit for each job in milliseconds <br /> (if zero or negative, no time limits are enforced)         |
| `scheduler-resource-limit` | `0`                     | scheduler memory resource limit for each job in bytes <br /> (if zero or negative, no resource limits are enforced) |
| `scheduler-sleep`          | `1000`                  | scheduler sleep time between two scheduling jobs <br /> in milliseconds                                |
| `tls-cert-path`            |                         | path to signed TLS certificate (required if TLS is enabled)                                     |
| `tls-key-path`             |                         | path to key file (required if TLS is enabled)                                                   |

## Command-Line Options
The command-line options offer the same configuration options as the configuration file and can be passed to the server at startup, e.g. `./apps/server --db-user test_user` to set the database user to test_user. Two additional options 
`help` and `config-file` are available. The command  
`./apps/server --help` shows a help message with all 
supported options. The option`config-file` can be used to specify an absolute path to a configuration file 
that is preferred to the configuration file located in the above-mentioned path.

## Environment Variables
The backend supports environment variables corresponding to the options above. For example, if you run 
`export SPANNERS_SERVER_PORT=4712` in the terminal, the `SPANNERS_SERVER_PORT` environment variable is set to 4712, 
which configures the server port to 4712. The environment variable can be removed with `unset SPANNERS_SERVER_PORT`.

The following environment variables can be set:

| Environment Variable                | Corresponding Option       |
|-------------------------------------|----------------------------|
| `SPANNERS_SERVER_PORT`              | `server-port`              |
| `SPANNERS_DB_HOST`                  | `db-host`                  |
| `SPANNERS_DB_PORT`                  | `db-port`                  |
| `SPANNERS_DB_USER`                  | `db-user`                  |
| `SPANNERS_DB_NAME`                  | `db-name`                  |
| `SPANNERS_DB_PASSWORD`              | `db-password`              |
| `SPANNERS_DB_TIMEOUT`               | `db-timeout`               |
| `SPANNERS_SCHEDULER_EXEC_PATH`      | `scheduler-exec-path`      |
| `SPANNERS_SCHEDULER_PROCESS_LIMIT`  | `scheduler-process-limit`  |
| `SPANNERS_SCHEDULER_TIME_LIMIT`     | `scheduler-time-limit`     |
| `SPANNERS_SCHEDULER_RESOURCE_LIMIT` | `scheduler-resource-limit` |
| `SPANNERS_SCHEDULER_SLEEP`          | `scheduler-sleep`          |
| `SPANNERS_TLS_CERT_PATH`            | `tls-cert-path`            |
| `SPANNERS_TLS_KEY_PATH`             | `tls-key-path`             |