# hoard

A simple terminal directory session manager. Designed to work in `bash` on Linux and macOS.

This script allows you to easily save 'sessions' in the form of a pointer to a directory you want to access in the future. It can be a temporary session, or a permanent bookmark. This frees you the need to `cd` everywhere to go to that commonly-used directory you need. Just open a bookmark or attach to a session and you're good to go!


## Prerequisites

Linux:
- The directory ~/bin/ needs to be available and used for storing binaries. This is usually already present on most systems.

macOS:
- The directory /usr/local/bin/ needs to be available and used for storing binaries. This is usually present if you already installed `homebrew`.


## Installation
Easy, just clone this git repository, then run the install script like so:
```
cd hoard
./install
```

## Configuration
`hoard` should be 'plug and play', and wouldn't need to be configured to function.

The list of sessions are stored in `~/.hoard_sessions`, and list of bookmarks are stored in `~/.hoard_bookmarks`. If you would like to specify a new location to store these, assign and export the enviromental variables `HOARD_SESSIONS_PATH` and/or `HOARD_BOOKMARKS_PATH`, pointing to your designated paths. Note that as of now, the two cannot be the same file.

If you want `hoard` to automatically save each exited session, you can copy the following into your `.bashrc` (or equivalent).

```
trap 'hoard s' EXIT
```

## Commands
### Session Control
Sessions are temporary forms of saving a directory. When you save a session and leave the directory you are in, you can re-attach the session (while the saved session will be discarded once re-attached) to go back to the original directory.

Sessions are stored in chronological order, accessibile via numeric indicies with the oldest session starting from `1`.

- **ls** - List all saved hoard sessions
- **a [NUMBER]** - Attach to hoard session [NUMBER]
- **d [NUMBER]** - Delete hoard session [NUMBER]
- **s** - Save current directory as a hoard session

### Bookmark Control
Bookmarks are permanent forms of saving a directory for future use, by using a reference name. This allows you to open a bookmark to jump to a directory at anytime until you delete it.

Bookmark names can be any string you like, but cannot start with a number.

- **lb** - List all saved hoard bookmarks
- **o [NAME]** - Open hoard bookmark [NAME]
- **x [NAME]** - Delete hoard bookmark [NAME]
- **b [NAME]** - Bookmark current directory as [NAME]

\*\* If you mix up bookmarks and sessions by executing the wrong `hoard` command listed above, `hoard` can automatically perform corrections or request more info about the command you were trying to execute.

## Uninstallation
Similar to the installation process, clone this repository (if you have not), then run the uninstall script like so:
```
cd hoard
./uninstall
```
