# hoard

A simple terminal directory session manager. Designed to work with `bash`, `ksh`, and `zsh` on Linux and macOS.

This script allows you to easily save 'sessions' in the form of a pointer to a directory you want to access in the future. It can be a temporary session, or a permanent bookmark. This frees you the need to `cd` everywhere to go to that commonly-used directory you need. Just open a bookmark or attach to a session and you're good to go!


## Prerequisites

Your login shell should be the latest versions of `bash`, `ksh`, or `zsh`.

Note that the installation and uninstallation scripts use `bash`, thus it needs to be present, but need not be your current shell.

## Installation & Updating
Easy, just clone this git repository, then run the install script and source `hoard`. You can update the installation of hoard the same way you would install it.

```
cd hoard
./install
source hoard
```

This will install `hoard` in your `~/bin` directory.

## Updating
You can update the installation of hoard the same way you would install it.

Note that by default: 
- the installation script will automatically attempt to pull updates from this repository unless the debug flag `-d` is present. 
- the script will pause for a moment before updating hoard so as the user can cancel the update with `^C`. This can be overriden with the `-y` flag.

## Configuration
`hoard` should be 'plug and play', and wouldn't need to be configured to function.

The list of sessions are stored in `~/.hoard_sessions`, and list of bookmarks are stored in `~/.hoard_bookmarks`. If you would like to specify a new location to store these, assign and export the environment variables `HOARD_SESSIONS_PATH` and/or `HOARD_BOOKMARKS_PATH`, pointing to your designated paths. Note that as of now, the two cannot be the same file.
```
export HOARD_SESSIONS_PATH=/path/to/sessions_file
export HOARD_BOOKMARKS_PATH=/path/to/bookmarks_file
```

If you want `hoard` to automatically save each exited session, you can copy the following into your `.bashrc` (or equivalent).
```
trap 'hoard s' EXIT
```

## Commands
### Session Control
Sessions are temporary forms of saving a directory. When you save a session and leave the directory you are in, you can re-attach the session (while the saved session will be discarded once re-attached) to go back to the original directory.

Sessions are stored in chronological order, accessibile via numeric indicies with the oldest session starting from `1`.

- **ls** - List all saved hoard sessions
- **a  [NUMBER]** - Attach to hoard session [NUMBER]
- **rm [NUMBER]** - Delete hoard session [NUMBER]
- **s**  - Save current directory as a hoard session

### Bookmark Control
Bookmarks are permanent forms of saving a directory for future use, by using a reference name. This allows you to open a bookmark to jump to a directory at anytime until you delete it.

Bookmark names can be any string you like, but cannot be a number.

- **lb** - List all saved hoard bookmarks
- **o  [NAME]** - Open hoard bookmark [NAME]
- **rm [NAME]** - Delete hoard bookmark [NAME]
- **b  [NAME]** - Bookmark current directory as [NAME]

### Miscellaneous
\* Most commands above are actually interchangable and come in many forms. All supported commands include:

```
ls                       - lists saved sessions
lb                       - lists saved bookmarks
a|attach|o|open          - attaches or opens <?>
d|del|delete|rm|remove|x - deletes <?>
s|save                   - saves a session if no arguments fed, a bookmark if an argument is provided
b|book|bookmark          - saves <bookmark>
```

## Uninstallation
Similar to the installation process, clone this repository (if you have not), then run the uninstall script like so:
```
cd hoard
./uninstall
```

Note that the uninstall script does not remove your sessions and bookmarks data. To delete them, just run:

```
rm "$HOARD_SESSIONS_PATH"
rm "$HOARD_BOOKMARKS_PATH"
```
