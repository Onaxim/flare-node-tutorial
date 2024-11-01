# Go-Flare Helper Script

The _Go-Flare Helper Script_ is designed to assist in installing a Flare node and upgrade it with a single command. It will install all required dependencies including Go, build-essentials and JQ. It clones the latest node repository, switches to the desired tag, builds and creates systemd service to start the node and enabling start on server reboot. It also enables upgrades done by accessing the go-flare directory, pulling any updates and building. During systemd configuration, a node runner script is created as the executable for the service file in order to dynamically fetch the latest bootstrap node ID and IP on node launch.

Note: This script is not fully developed - some features might not work as expected.

## Example Usage

This script is designed and tested on Ubuntu 20.04 and assumes an install will be made to a user directory ($HOME).

To install a specific version, http-host & db-dir in silent mode run:
`Example Usage: ./flare.sh --version v1.7.1805 --http-host 0.0.0.0 --db-dir $HOME/mydb --install`

Run `./flare.sh --help` for more information:

```
Usage: /.flare.sh [ --help | --version <tag> | --http-host <ip> | --db-dir <path> | --archival ] [ --list | --install | --upgrade  | --remove | --status ]
Options:
   --help            			Shows this message
   --version <tag>                      Installs <tag> version, default is the latest
   --http-host <ip>  			The accepted interface for RPC requests on port 9650
   --db-dir <path>                      Full path to the database directory, defaults to $HOME/<.avalanchego | .flare>/db"
   --archival                           If provided, will disable state pruning, defaults to pruning enabled

   --list            			Lists latest versions available to install
   --install         			Installs node with provided version (see --version && --list)
   --upgrade         			Upgrades go-flare to latest tag version available
   --remove         			Removes goflare/gosongbird and service files
   --status         			Gives current health state, peers and version of locally running node

Example Usage: ./flare.sh --version v1.7.1806 --http-host 0.0.0.0 --db-dir $HOME/mydb --network flare --install
```
