# Extra Features for Xfce

Xfce is a lightweight desktop environment for operating systems of the Unix variety.
These shell scripts slightly extend its basic functionality.

## Installation

Copy the scripts into a suitable location.

	[user@arch ~]$ sudo cp xfce4-* /usr/local/bin

## Running

### Configuration

No configuration is needed.

### Integration

Shortcut keys can be set in the Keyboard and Window Manager menus.

### Example

Let's focus the second and the third windows on the task list

	[user@arch ~]$ xfce4-focus 2 3

and move the third window to the lower right corner.

	[user@arch ~]$ xfce4-move down right
