# hoard

A simple terminal directory session manager. Works on Linux and macOS.

## Installation
Easy, just clone this git repository, then run the install script like so:
```
cd hoard
./install
```

## Configuration
`hoard` should be 'plug and play', and wouldn't need configurations.

However, if you want `hoard` to automatically save each exited session, you can copy the following into your `.bashrc` (on relevant systems).

```
finish() {
    hoard s
}

trap finish EXIT
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

\*\*`hoard` now has smart error handling capabilities, so that even if you mess up by executing the wrong `hoard` command listed above, `hoard` can automatically apply corrections or request more info about the command you were trying to execute.

## Uninstallation
Similar to the installation process, clone this repository (if you have not), then run the uninstall script like so:
```
cd hoard
./uninstall
```
