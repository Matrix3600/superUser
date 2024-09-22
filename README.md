# About
_superUser_ is a simple and lightweight utility to start any process as the System user with Trusted Installer privileges.

# How It Works
The program acquires the Trusted Installer's process' access token and creates a new (user-specified) process as the System user with Trusted Installer privileges using this token.

# Usage
There are two ways to run the program:

## From the File Explorer
Double-click the executable, grant administrator privileges and wait for a command prompt to appear.

## From the Command Prompt
Simply run _superUser_ from the command prompt (preferably one with administrator privileges) using the following arguments:

#### ```superUser [options] [command_to_run]```

| Option |                           Meaning                           |
|:------:|-------------------------------------------------------------|
|   /h   | Display the help message.                                   |
|   /r   | Return the exit code of the child process. Requires /w.     |
|   /s   | The child process shares the parent's console. Requires /w. |
|   /v   | Display verbose messages with progress information.         |
|   /w   | Wait for the child process to finish. Used for scripts.     |

Notes:
- You can also use a dash (-) in place of a slash (/) in front of an option.
- Multiple options can be grouped together (e.g., `/wrs`).
- `command_to_run` is the filename of an executable (.exe) or script (.cmd),
followed by parameters. If not specified, `cmd.exe` is started.


## Exit Codes

| Exit Code |                        Meaning                         |
|:---------:|--------------------------------------------------------|
|     1     | Invalid argument.                                      |
|     2     | Failed to acquire SeDebugPrivilege.                    |
|     3     | Failed to open/start TrustedInstaller process/service. |
|     4     | Process creation failed (prints error code).           |
|     5     | Another fatal error occurred.                          |

If the `/r` option is specified, the exit code of the child process is returned.
If _superUser_ fails, it returns a code from -1000001 to -1000005 (e.g., -1000002 instead of 2).
