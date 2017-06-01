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
deploy_production username [server]
```
Login to the production account, update the code, composer and migrations. Server is optional, defaults to 01.

### Deliver code to branch
```bash
deliver source target
```
Checkout the source branch, merge its origin; checkout target branch, merge its origin. Rebase source unto target and push everything.

### Provision a vagrant site
```bash
vagrant_provision [name]
```
Update Laravel Homestead configuration for the project, and open it in your browser.

### Ensure vagrant is running
```bash
vagrant_ensure_up
```
Restarts your vagrant machine to ensure that it is running. It is advisable to run this on login by adding this command to `~/.profile`.

### Open a vagrant connection from anywhere
```bash
vagrant_open
```
Opens a ssh-connection to your default homestead install from any directory. Once logged-in to the vagrant machine, this will immediately run `cd code/{dirname}` where dirname is the name of the current folder you're in.
