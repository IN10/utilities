# Utilities
> A personal, opinionated collection of useful tools for working in development at IN10

## Installation
1. Clone the repository to your homefolder: `git clone git@github.com:IN10/utilities.git ~/utilities`.
1. Add the folder to your path. On a Mac, open `/etc/paths` and add `/Users/<yourusername>/utilities` as the very first entry.

## Assumptions
These utilities, especially the `vagrant_*` commands, make a couple of assumptions on how your system is organised:
1. Your projects are all `~/code/*`. For example, a project named "waterbus" on my PC would be in `/Users/jakobbuis/code/waterbus`.
1. All projects have their web roots in `./code/{name}/public`. Moving the web root will require manual tuning.
1. You have a single Homestead installation for all projects, and it's located in `~/homestead`.
1. You have DNSMasq or similar installed and all your projects are reachable over `http://{name}.test`.

## Available utilities

### Fix coding standard violations
```bash
autofix_app
```
Auto-format the app/ directory to match the coding standard (PSR-1 + PSR-2). Run this in the root-directory of your project. Does not add typehints where necessary, so you'll need to do that manually. You'll need to commit the change yourself.

### Update composer dependencies
```bash
composer_minor_updates
```
Automatically installs semver-compatible upgrades and commits the result with a commit message of "composer minor upgrades". Run in the root-folder of your project.

### Deploy to Production
```bash
deploy_production [server] [username]
```
Login to the production account, update the code, install composer dependencies. *Only use this to deploy projects which do not have deployer setup (legacy projects).* This process will clear caches where appropriate. Use only the server number in the command, e.g. `deploy_production 03 accrpas`.

### Provision a vagrant site
```bash
vagrant_provision [name]
```
Update Laravel Homestead configuration for the project, and open it in your browser.

### Ensure vagrant is running
```bash
vagrant_ensure_up
```
Restarts your vagrant machine to ensure that it is running.

### Open a vagrant connection from anywhere
```bash
vagrant_open
```
Opens a ssh-connection to your default homestead install from any directory. Once logged-in to the vagrant machine, this will immediately run `cd code/{dirname}` where dirname is the name of the current folder you're in.

### Clone a project locally
```bash
setup_locally [git repository] [local name]
```
Clone the project into `~/code/[local name]`, runs some basic setup tasks (composer, artisan, vagrant_provision) and opens the folder in sublime.

### Bring master and develop up to date
```bash
update_local
```
Fetches changes, and brings your develop and master branch up to date.
