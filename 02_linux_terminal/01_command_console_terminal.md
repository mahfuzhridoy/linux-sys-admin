# Shell, Console, Terminal & Kernel

## Terminal
A terminal emulator is crucial part of any linux distro because it basically allows a user to access a system through a shell. It is an interface that allows a user to interact with a shell by typing commands.


It is usually a window/application inside a graphical desktop such as:

- GNOME Terminal
- Konsole
- xterm
- kitty

To open a terminal click ```ctrl + alt + T``` or search on application or right click for a menu where open terminal here is listed.

When a user open one, it usually starts a shell such as most popular ```bash``` or most recent ```zsh```

## Console
A console is a text-based interface that allows a user to interact directly with a computer system. In Linux, the term console can refer to a physical or virtual text-based interface used for system administration and interaction with the operating system. Linux provides multiple virtual consoles, also known as virtual terminals (VTs) or TTYs. These allow multiple text-based login sessions to run on the same computer without requiring multiple physical monitors or keyboards.

On many Linux distributions, you can switch to a virtual console using keyboard shortcuts such as:

> **Ctrl + Alt + F1** through **Ctrl + Alt + F6**. One of the virtual terminal have GUI others are text only interface.

### When consoles are useful
Virtual consoles are especially useful for:

* Troubleshooting system problems
* Recovering from graphical desktop failures
* Managing servers without a GUI
* System administration
* Working directly in a text-based environment

For example, if the graphical desktop freezes or fails to start, a system administrator may switch to a virtual console, log in, and investigate or repair the system.


## Shell
A shell is a command interpreter that allows users to interact with the Linux operating system by entering commands. The shell reads the commands entered by the user, interprets them, and performs the requested actions. It can execute built-in commands or start other programs and processes.

If a command is written it will send the command to kernel to get executed. For example:

**User → Terminal/Console → Shell → Operating System → Kernel**


> One of the most powerful feature of a shell is a user can save the commands into a file and execute it. This is called **shell scripting**. Shell scripting is commonly used to automate repetitive tasks and system administration tasks e.g. Running multiple commands automatically, Managing files etc.

### Common linux shells
Some common linux shells includes:

* bash — Bourne Again Shell
* zsh — Z Shell
* sh — Bourne Shell
* fish — Friendly Interactive Shell

Bash is the most commonly used shell in linux systems.

## Kernel
A kernel is the core part of an operating system. It acts as a bridge between hardware and software running on the system. It runs at privileged system level. the kernel manages the computers important resources like:

1. CPU management
2. Memory management
3. Process management
4. Hardware management

## Interaction Flow
**Using terminal emulator**

> User → Terminal Emulator → Shell → Kernel → Hardware

**Using virtual console(TTY)**

> User → Virtual Console (TTY) → Shell → Kernel → Hardware

#

### Final overview

* `Terminal Emulator` → Provides a graphical interface where users can type commands.

* `Console (TTY)` → Provides a text-based interface for accessing and interacting with the system.

* `Shell` → Reads and interprets user commands and executes them.

* `Kerne`l` → Manages system resources and communicates with the hardware.