# Shell - Processes and Signals

This repository contains Bash scripts that demonstrate various concepts related to processes and signals in Unix-like systems.

## Learning Objectives

By the end of this project, you should be able to explain:

- What is a PID (Process ID)
- What is a process
- How to find a process' PID
- How to kill a process
- What is a signal
- What are the 2 signals that cannot be ignored

## Requirements

- All files are interpreted on Ubuntu 20.04 LTS
- All files end with a new line
- All Bash script files are executable
- Scripts pass Shellcheck (version 0.7.0) without any error
- The first line of all Bash scripts is exactly `#!/usr/bin/env bash`
- The second line of all Bash scripts is a comment explaining what the script does

## Files Description

### 0-what-is-my-pid
Bash script that displays its own PID.

**Usage:** `./0-what-is-my-pid`

### 1-list_your_processes
Bash script that displays a list of currently running processes.

**Requirements:**
- Must show all processes, for all users, including those which might not have a TTY
- Display in a user-oriented format
- Show process hierarchy

**Usage:** `./1-list_your_processes`

### 2-show_your_bash_pid
Bash script that displays lines containing the bash word, allowing you to easily get the PID of your Bash process.

**Requirements:**
- You cannot use `pgrep`
- The third line must be `# shellcheck disable=SC2009`

**Usage:** `./2-show_your_bash_pid`

### 3-show_your_bash_pid_made_easy
Bash script that displays the PID, along with the process name, of processes whose name contains the word bash.

**Requirements:**
- You cannot use `ps`

**Usage:** `./3-show_your_bash_pid_made_easy`

### 4-to_infinity_and_beyond
Bash script that displays "To infinity and beyond" indefinitely.

**Requirements:**
- In between each iteration of the loop, add a `sleep 2`

**Usage:** `./4-to_infinity_and_beyond`

### 5-dont_stop_me_now
Bash script that stops the `4-to_infinity_and_beyond` process.

**Requirements:**
- You must use `kill`

**Usage:** `./5-dont_stop_me_now`

### 6-stop_me_if_you_can
Bash script that stops the `4-to_infinity_and_beyond` process.

**Requirements:**
- You cannot use `kill` or `killall`

**Usage:** `./6-stop_me_if_you_can`

### 7-highlander
Bash script that displays:
- "To infinity and beyond" indefinitely
- With a `sleep 2` in between each iteration
- "I am invincible!!!" when receiving a SIGTERM signal

**Usage:** `./7-highlander`

### 67-stop_me_if_you_can
Copy of `6-stop_me_if_you_can` script that kills the `7-highlander` process instead of the `4-to_infinity_and_beyond` one.

**Usage:** `./67-stop_me_if_you_can`

### 8-beheaded_process
Bash script that kills the process `7-highlander`.

**Usage:** `./8-beheaded_process`

### 10-process_and_pid_file
Bash script that:
- Creates the file `/var/run/myscript.pid` containing its PID
- Displays "To infinity and beyond" indefinitely
- Displays "I hate the kill command" when receiving a SIGTERM signal
- Displays "Y U no love me?!" when receiving a SIGINT signal
- Deletes the file `/var/run/myscript.pid` and terminates itself when receiving a SIGQUIT or SIGTERM signal

**Usage:** `sudo ./10-process_and_pid_file`

### manage_my_process
Bash script that:
- Indefinitely writes "I am alive!" to the file `/tmp/my_process`
- In between every "I am alive!" message, the program should pause for 2 seconds

**Usage:** `./manage_my_process &`

### 11-manage_my_process
Bash (init) script that manages `manage_my_process`.

**Requirements:**
- When passing the argument `start`: Starts `manage_my_process`, creates a file containing its PID in `/var/run/my_process.pid`, displays "manage_my_process started"
- When passing the argument `stop`: Stops `manage_my_process`, deletes the file `/var/run/my_process.pid`, displays "manage_my_process stopped"
- When passing the argument `restart`: Stops `manage_my_process`, deletes the file `/var/run/my_process.pid`, starts `manage_my_process`, creates a file containing its PID in `/var/run/my_process.pid`, displays "manage_my_process restarted"
- Displays "Usage: manage_my_process {start|stop|restart}" if any other argument or no argument is passed

**Usage:** 
- `sudo ./11-manage_my_process start`
- `sudo ./11-manage_my_process stop`
- `sudo ./11-manage_my_process restart`

## Signals

Common signals used in these exercises:

- **SIGTERM (15)**: Termination signal - requests graceful shutdown
- **SIGINT (2)**: Interrupt signal - typically sent by Ctrl+C
- **SIGQUIT (3)**: Quit signal - typically sent by Ctrl+\
- **SIGKILL (9)**: Kill signal - cannot be caught or ignored

## Commands Used

- `ps`: Display running processes
- `pgrep`: Search for processes by name
- `pkill`: Kill processes by name
- `kill`: Send signals to processes
- `trap`: Handle signals in shell scripts
- `$$`: Current shell's PID
- `$!`: PID of last background process

## Author

This project is part of the Holberton School curriculum.

## Repository

- **GitHub repository:** holbertonschool-shell
- **Directory:** processes_and_signals
