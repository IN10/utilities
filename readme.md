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

## Available utilities

### Deploy to Production
```bash
deploy_production [options] [username]
```
Login to the production account, update the code, composer and migrations. This commands accepts two options: -v for deploying over the VPN, and -s 02 for deploying on a specific server. Valid servers are 01, 02 and 03, default is 01.

### Deliver code to branch
```bash
deliver source target
```
Fetch, checkout the source branch, and rebase origin/{source} locally unto source. Checkout target and rebase origin/{target} onto it. Merge (not rebase!) source into target and push both branches.

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
