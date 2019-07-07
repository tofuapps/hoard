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
Sessions are temporary forms of saving a directory as a session, so that if you left the directory, you can re-attach it (and discard the saved session once re-attached) when you're back.

- **ls** - List all saved hoard sessions
- **a [NUMBER]** - Attach to hoard session [NUMBER]
- **d [NUMBER]** - Delete hoard session [NUMBER]
- **s** - Save current directory as a hoard session

### Bookmark Control
Bookmarks are permanent forms of saving a directory for future use, by using a reference name. This allows you to open a bookmark to jump to a directory at anytime.

- **lb** - List all saved hoard bookmarks
- **o [NAME]** - Open hoard bookmark [NAME]
- **x [NAME]** - Delete hoard bookmark [NAME]
- **b [NAME]** - Bookmark current directory as [NAME]

## Uninstallation
```
cd hoard
./uninstall
```
