# hoard

A simple terminal session manager.

## Installation
Just drop `hoard` into a folder in your path.

Or you can fire up a terminal and execute the following:
```
git clone https://gitlab.com/l-yc/hoard.git
cd hoard
ln hoard ~/bin
```

## Configuration
If you want `hoard` to automatically save each exited session, you can copy the following into your` .bashrc`.
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
