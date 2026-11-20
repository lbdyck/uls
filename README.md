# ULS - User List Services

ULS is a REXX/ISPF data set list dialog inspired by the ISPF data set list
utility. It uses the ISPF LMDLIST service to obtain catalog entries and a
scrollable dynamic area to display them.

## Install

Copy `ULS.EXEC/ULS` into a data set allocated to SYSEXEC or SYSPROC. Copy the
members in `ULS.PANELS` into a panel library allocated to ISPPLIB. Invoke
`ULS` from ISPF, optionally supplying a data set level:

```
ULS SYS1
ULS YOURID
```

The level field accepts a catalog level (for example `SYS1` or
`YOURID.PROJ`). It does not accept wildcard characters; use `FILTER` to
search the returned names.

## Commands

| Command | Description |
| --- | --- |
| `REFRESH` | Rebuild the catalog list for the current level |
| `FILTER text` | Show data set names containing `text` |
| `FILTER CLEAR` | Remove the name filter |
| `FIND text` / `RFIND` | Find or repeat a search in displayed names |
| `SORT NAME|VOL|SIZE|DEVICE [A|D]` | Sort ascending or descending |
| `UP`, `DOWN`, `TOP`, `BOTTOM` | Scroll the displayed list |
| Enter `B`, `E`, `V`, or `I` in a row's `Act` field | Browse, edit, view, or show catalog details |
| `HELP` | Display command help |
| `TUTORIAL` | Open the ISPF tutorial panels |
| `END` | Exit |

The level field accepts an unquoted data set name up to 44 characters.
The scroll field accepts a number, `PAGE`, or `CSR`. Browse, view, and info
are read-only; EDIT can change data set contents. Allocation, rename,
delete, copy, and move are intentionally not provided.

## Panels

`ULSMAIN` is the dynamic-area list, `ULSINFO` displays scrollable data set
attributes, and `ULSHELP` describes the commands.
`ULSTUT1` through `ULSTUT5` are short tutorial pages covering dialog setup,
dynamic areas, list filtering, navigation, and testing.

The dialog requires ISPF and a TSO environment. It has not been run on a z/OS
system in this workspace; verify panel-library attributes and ISPF service
behavior at the target installation.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
