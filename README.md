# Disk Usage Health Check

Nagios compliant health check for Automatron to determine disk usage

## Installation

Simply copy the `diskfree.py` script to the `plugins/checks/` directory.

## Usage

The `diskfree` plugin is used to check the available space on a specified filesystem. If the available disk space is below the specified thresholds this script will exit indicating a `WARNING` or `CRITICAL` status.

### OS Support

  * Linux
    * Debian Base (Debian, Ubuntu, etc.)
    * RedHat Base (RHEL, CentOS)

## Runbook Example

The below is an example of using the `diskfree` health check in a runbook.

```yaml
checks:
  diskfree:
    # Check for the % of disk free create warning with 20% free and critical for 10% free
    execute_from: target
    type: plugin
    plugin: diskfree.py
    args: --warn=20 --critical=10 --filesystem=/var/log
```

### Required Arguments

The `diskfree` check requires 3 arguments.

```yaml
args: --warn=<warning threshold %> --critical=<critical threshold %> --filesystem=<filesystem to check>
```

