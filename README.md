# Tasqr CLI

[Tasqr](http://www.tasqr.io) is an IT automation product that helps you automate any sort of server configuration without needing to write and maintain code or special automation infrastructure. It is design to be simple to learn and use, yet be powerful and flexible enough for the most complicated of deployments,

### Record and Replay

At its heart, any sort of system configuration is composed of two elements:

- Commands
- Files

Tasqr tries to eliminate as much arcane and complex notation as possible to help you have tight control over these two elements of your configuration. The way this is accomplished is through enabling *recording* of your commands and files, and *replaying* these commands and files onto the systems you want to automate.

Recording via the Tasqr command line utility is simple and painless: you precede a shell command you would normally run with the `tasqr` command. If the command can be executed successfully, the tool will prompt for any additional information that is needed to record your command and log its execution result. All this information is automatically saved in the Tasqr service (valid credentials are required).

Below is an example of what it looks like to record a command that prints "hello world":

```
> tasqr echo hello world
(cwd: /home/ereyes/work/) Running: echo hello world ...
=====stdout=====
hello world
=====stderr=====
return value = 0
Execution Time: 935.317µs
Server Name [myhostname]: laptop 
Select Recording: demo
Command Name [demo-0]: 
```

Here is what happened in the invocation above:

- The current working directory is saved.
- The command `echo hello world` is executed.
- The stdout/stderr output, return value, and time taken to execute is shown.
- Since the Tasqr service has never seen this server before, you are prompted for a name
  - The default name is your system's hostname. Instead, we chose to name this system "laptop"
- You are asked which recording this command should be a part of.
  - The default is the last recording you've edited from this server.
  - Since this is our first time recording from this server, there is no default.
- You are asked to name this command.
  - The default is the name of the recording, followed by the sequence number of this command in the recording.

The recording called "demo" can later be replayed on the "laptop" server, or on any other server.
