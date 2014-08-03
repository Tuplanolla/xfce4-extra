# Extra Features for Xfce Version 4

Xfce is a lightweight desktop environment for
 operating systems of the Unix variety.
This small project extends its basic functionality.

## Installation

Installation involves copying the scripts into a suitable location.

	[user@computer:~]$ sudo cp -i xfce4-* /usr/local/bin

## Configuration

The shell scripts can be edited, should such a thing be necessary.

## Running

There are several shell scripts, each of which has a single responsibility.
When invoked without arguments, they print a usage summary and terminate.
Otherwise they send the appropriate messages to Xfce.
They are intended to be used with shortcut keys, so
 they use `zenity` (a graphical dialog) for communicating with the user, but
 fall back to `echo` (command line messages) if it's not available.
They might also have other dependencies.

### Focusing a Window

The script `xfce4-focus` focuses task list windows based on their indices.
It requires `xfce4-panel` with at least one task list that
 uses window title ordering.
It also depends on `xfconf-query`, `wmctrl` and `xprop`.

Assume there are four windows open in the currently active workspace.
It's easy to bring the second window on the task bar to the top

	[user@computer:~]$ xfce4-focus 2

 or stack all of the windows, putting the first one on the top.

	[user@computer:~]$ xfce4-focus 3 2 4 1

### Moving a Window

The script `xfce4-move` moves the currently active window to
 a precise position on the screen.
The position can be specified by
 using a combination of `center`, `up`, `down`, `left` and `right`.
It depends on `xwininfo` `xprop` and `wmctrl`.

Centering a window

	[user@computer:~]$ xfce4-move center

 or moving it to the bottom right corner of the screen is trivial

	[user@computer:~]$ xfce4-move down right

 and works even if there's a task bar or another panel in the way.

## Integration

Shortcut keys can be set in the Keyboard menu or by
 editing `~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml`.

### Focusing a Window

The following configuration allows using the Super key with
 a number to focus a window.

	<?xml version="1.0" encoding="UTF-8"?>
	<channel name="xfce4-keyboard-shortcuts" version="1.0">
		<property name="commands" type="empty">
			<property name="default" type="empty">
				<property name="&lt;Super&gt;1" type="string" value="xfce4-focus 1" />
				<property name="&lt;Super&gt;2" type="string" value="xfce4-focus 2" />
				<property name="&lt;Super&gt;3" type="string" value="xfce4-focus 3" />
				<property name="&lt;Super&gt;4" type="string" value="xfce4-focus 4" />
				<property name="&lt;Super&gt;5" type="string" value="xfce4-focus 5" />
				<property name="&lt;Super&gt;6" type="string" value="xfce4-focus 6" />
				<property name="&lt;Super&gt;7" type="string" value="xfce4-focus 7" />
				<property name="&lt;Super&gt;8" type="string" value="xfce4-focus 8" />
				<property name="&lt;Super&gt;9" type="string" value="xfce4-focus 9" />
			</property>
		</property>
	</channel>

### Moving a Window

The following configuration allows using the Super key with
 a letter, arranged in a matrix, to move a window.

	<?xml version="1.0" encoding="UTF-8"?>
	<channel name="xfce4-keyboard-shortcuts" version="1.0">
		<property name="commands" type="empty">
			<property name="default" type="empty">
				<property name="&lt;Super&gt;q" type="string" value="xfce4-move up left />
				<property name="&lt;Super&gt;w" type="string" value="xfce4-move center up />
				<property name="&lt;Super&gt;e" type="string" value="xfce4-move up right />
				<property name="&lt;Super&gt;a" type="string" value="xfce4-move center left />
				<property name="&lt;Super&gt;s" type="string" value="xfce4-move center />
				<property name="&lt;Super&gt;d" type="string" value="xfce4-move center right />
				<property name="&lt;Super&gt;z" type="string" value="xfce4-move down left />
				<property name="&lt;Super&gt;x" type="string" value="xfce4-move center down />
				<property name="&lt;Super&gt;c" type="string" value="xfce4-move down right />
			</property>
		</property>
	</channel>

## Development

This project is in usable condition, but may develop further over time.

### Contributing

Contributions are welcome.
