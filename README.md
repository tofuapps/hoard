# hoard

A simple terminal directory session manager. Designed to work on most POSIX compliant shells across Linux and macOS, such as `bash`, `zsh`, `dash`, `ksh`, etc.

This script allows you to easily save 'sessions' in the form of a pointer to a directory you want to access in the future. It can be a temporary session, or a permanent bookmark. This frees you the need to `cd` everywhere to go to that commonly-used directory you need. Just open a bookmark or attach to a session and you're good to go!


## Prerequisites

Your login shell should be a modern POSIX compliant shell, ideally with the ability to run scripts on startup. Examples include `bash`, `ksh`, `dash`, `zsh`, etc.

## Installation

Easy, just clone this git repository. Then, run the install script and source `hoard`.

This will install `hoard` in your `~/bin` directory.

```
cd hoard
./install
. ~/bin/hoard
```

(This automatic installation procedure works for `bash`, `ksh`, and `zsh`. If you prefer an alternative installation directory, or do not use `bash`, `ksh`, `zsh`, refer to manual installation instructions.)

Note: `hoard` shorthands might conflict with other commands or aliases you may have. Check the [Shorthands](#shorthands) section for details.

## Manual Installation
Simply make sure to copy the script somewhere and source the script in your shell startup profile.

For instance, copy the script to a location `\path\to\hoard`, then source it by running `. \path\to\hoard` in your shell startup profile.

## Updating
You can update the installation of hoard the same way you would install it.

Note that by default:
- the installation script can pull updates from this repository if the upstream flag `-u` is present.
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

### Shorthands
Shorthands are available for faster hoard usage. Arguments like bookmark names can be provided.
- `h`: equivalent to `hoard`. However, automatically lists all sessions and bookmarks if no arguments are provided.
- `a`: equivalent to `hoard attach`.
- `o`: equivalent to `hoard open`.

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
