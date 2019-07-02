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
- **ls** - List all saved hoard sessions
- **a [NUMBER]** - Attach to hoard session [NUMBER]
- **d [NUMBER]** - Delete hoard session [NUMBER]
- **s** - Save current directory as a hoard session

## Uninstallation
```
cd hoard
./uninstall
```
