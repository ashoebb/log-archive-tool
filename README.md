# log-archive-tool

A Bash tool that compresses a log directory into a timestamped `tar.gz` and records each archive in a log file. Built as a roadmap.sh DevOps project.

## Usage

    ./log-archive <log-directory> [archive-directory]

- The archive is named `logs_archive_YYYYMMDD_HHMMSS.tar.gz`.
- The default archive directory is `~/log-archives`.
- Each run appends the date, time, source, archive path and size to `archive.log` in the archive directory.
- Use `sudo` for `/var/log`, because some files there are readable only by root.

Example:

    sudo ./log-archive /var/log ~/log-archives

## Behavior

- Fails with a usage message if no directory is given, and with an error if the directory does not exist.
- Exits non-zero and keeps no partial archive if `tar` fails.
- Warns, but keeps the archive, if files changed while being archived.

## Development

    shellcheck log-archive
