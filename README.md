# Inertial Upgrader CLI

## Downloads
**Windows**: [InertialUpdater_15.5.4_x64.exe](https://github.com/LORD-MicroStrain/InertialUpgraderCLI/releases/download/v15.5.4/InertialUpdater_15.5.4_x64.exe)

**Linux** (Ubuntu)
- **amd64**: [18.04](https://github.com/LORD-MicroStrain/InertialUpgraderCLI/releases/download/v15.5.4/InertialUpdater_15.5.4_ubuntu_18.04_amd64.zip) | [20.04](https://github.com/LORD-MicroStrain/InertialUpgraderCLI/releases/download/v15.5.4/InertialUpdater_15.5.4_ubuntu_20.04_amd64.zip) | [22.04](https://github.com/LORD-MicroStrain/InertialUpgraderCLI/releases/download/v15.5.4/InertialUpdater_15.5.4_ubuntu_22.04_amd64.zip)
- **arm64**: [18.04](https://github.com/LORD-MicroStrain/InertialUpgraderCLI/releases/download/v15.5.4/InertialUpdater_15.5.4_ubuntu_18.04_arm64.zip) | [20.04](https://github.com/LORD-MicroStrain/InertialUpgraderCLI/releases/download/v15.5.4/InertialUpdater_15.5.4_ubuntu_20.04_arm64.zip) | [22.04](https://github.com/LORD-MicroStrain/InertialUpgraderCLI/releases/download/v15.5.4/InertialUpdater_15.5.4_ubuntu_22.04_arm64.zip)

## Linux
Builds for versions lower than the operating system version should work fine.

For example, the 22.04 Inertial Upgrader CLI should run on Ubuntu 24.04 without issue.

Within each .zip:
- InertialUpdater - firmware updater executable
- README.txt - brief readme listing some dependencies

## Windows
This file is an executable and can be run directly from the command line.

Device drivers need to be installed before running the command line tool for successful device communication.

Drivers are installed with SensorConnect or can be found on GitHub here: [Drivers](https://github.com/LORD-MicroStrain/Drivers?tab=readme-ov-file#windows)

## Upgrade and Options
To run the updater just unzip the files and run:
|  |  |
| ----------- | ----------- |
| Linux: | `./InertialUpdater <port> <baud> <firmware.zhex> [options]` |
| Windows: | `InertialUpdater_<version>_x64.exe <port> <baud> <firmware.zhex> [options]` |
  
All options are the same between Linux and Windows, the command to run the executable is just a little different based on operating system requirements and how we have packaged/named the files.

Additional information and option details can be found by running:
|  |  |
| ----------- | ----------- |
| Linux: | `./Inertial Updater --help` |
| Windows: | `InertialUpdater_<version>_x64.exe --help` |

#### Important for GQ7 GNSS receiver upgrades
By default, the receivers will be upgraded if the target zhex includes receiver images **even if the version is the same**. Once a unit's receivers are upgraded, receiver upgrades can and probably should be suppressed by running with the **--no-receivers** option:
|  |  |
| ----------- | ----------- |
| Linux: | `./InertialUpdater <port> <baud> <firmware.zhex> [options] --no-receivers` |
| Windows: | `InertialUpdater_<version>_x64.exe <port> <baud> <firmware.zhex> [options] --no-receivers` |

The same warnings regarding receiver upgrades and recovery via SensorConnect apply for this tool as well. Receiver recovery works automatically but there are no warnings or printed information providing duration expectations like SensorConnect has. Unfortunately, the CLI does not make the upgrade go any faster.
Documentation can be found in the [GQ7 manual](https://s3.amazonaws.com/files.microstrain.com/GQ7+User+Manual/user_manual_content/software/Note%20on%20GNSS%20upgrades%20(fw%201.1.02).htm).

## Troubleshooting Upgrade Failures
This tool uses the same code as SensorConnect so it does have all the same device recovery capability - if an upgrade is stopped or fails, the tool should be able to identify and recover the device regardless of its state without the user needing to power cycle, send additional commands, etc.

If an upgrade fails, or fails repeatedly, run the upgrade again with the --debug option. This will print more robust information to the console to help determine how and why the upgrade failed - this information should be copied out of the console and sent to us for [support](https://support.microstrain.com/).
|  |  |
| ----------- | ----------- |
| Linux: | `./InertialUpdater <port> <baud> <firmware.zhex> [options] --debug` |
| Windows: | `InertialUpdater_<version>_x64.exe <port> <baud> <firmware.zhex> [options] --debug` |

If you have any questions or run into any issues, enter a ticket in the [MicroStrain Support Portal](https://support.microstrain.com/) - we're happy to help!
