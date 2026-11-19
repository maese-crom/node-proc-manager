# node-proc-manager

A pure-Bash TUI (no dependencies) to find and kill `node`, `npm`, `npx`, `yarn` or `pnpm` processes that get stuck on your system. It only uses tools that already ship with macOS: `bash`, `ps`, `lsof`, `awk`, `sed`, `tput`.

## Why

When you work on several Node projects at once (Expo, MCP servers launched with `npx`, bundlers, etc.), it is easy to end up with orphaned `node`/`npm`/`npx` processes running in the background. This tool lists them all, shows where each one comes from (full command, working directory, listening ports) and lets you close them without running `ps aux | grep` + `kill` by hand.

## Requirements

No external dependencies: it uses `bash`, `ps`, `lsof`, `awk`, `sed` and `tput`, which are available on any macOS. Designed and tested on macOS (Apple's bash 3.2); it should work the same on Linux if those tools are installed.

The interface text is in Spanish.

## Usage

```
./nproc
```

To run it from anywhere, copy or symlink it into a directory on your `$PATH`, for example:

```
ln -s ~/tools/node-proc-manager/nproc /usr/local/bin/nproc
```

## Controls

**Main list**
- `↑`/`↓` (or `k`/`j`, vim style): move
- `Enter` / `→`: show details of the selected process
- `r`: refresh
- `q`: quit

**Detail view** (PID, PPID, user, elapsed time, listening ports, working directory, full command)
- `k`: kill the process (SIGTERM), asks for confirmation
- `K` (`Shift+K`): force kill (SIGKILL), asks for confirmation
- `←` / `Backspace` / `b`: back to the list
- `r`: refresh the details

## License

MIT, see [LICENSE](LICENSE).
