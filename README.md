# Osoy
Lightweight package manager currently written in POSIX shell. Inspired by vim-plug, yarn and pacman. It supports multiple git hosting services and asynchronous updating.

<p style='text-align:center'><em><b>a demo gif</b></em></p>

## Compatibility
It has currently been tested on Linux with dash but most likely will work with bash, zsh and possibly even on Windows with Git Bash. Osoy aims to be easily readable and compliant with variety of platforms.

## Dependencies
    sed; grep; find; ls; sort; cut; tr; curl; git

## File structure

    ~/.osoy/
    ├── bin/
    │   ├── <symlink>  ->  <executable>
    │   :   ...
    │
    └── packages/
        ├── <domain>/
        │   :   ...
        │
        ├── <domain>/
        :   ├── <author>/
            │   :   ...
            │
            ├── <author>/
            :   ├── <package>/
                │   :   ...
                │
                ├── <package>/
                :   ├── <modules>/
                    ├── <module>
                    ├── <executable>
                    :   ...

## Usage
    osoy [operator] [flags]

**Operators**:

    c|clone    <query*>   clone packages from GitHub, GitLab or Bitbucket
    r|remove   <query*>   remove packages
    s|symlink  [query*]   make packages' executables available in PATH
    u|update   [query*]   update (all) packages
    l|list     [query*]   list (all) packages
    dir        <query>    print package's directory path
    read       <query>    view package's README file
    license    <query>    view package's LICENSE file
    uninstall  -          uninstall osoy and all packages

**Query syntax**:

    <[[domain/]author/]package>

**Flags**:

    -d         <domain>   enforce a specific domain to clone from
    -a         <author>   specify packages' author
    -p         <protocol> specify a protocol other than HTTPS
    -b         <branch>   specify a single branch as the HEAD
    -B         -          clone all branches
    -y         -          proceed with defaults
    -f         -          force overwriting and/or removing
    -v         -          show version
    -h         -          show help menu
    -c         -          enable ansi colors
    -C         -          disable ansi colors

## Contributions
I currently don't yet know if anybody other than me would even use something like this. Though if you have interest constructive critisism and contributions are ofcourse more than welcome.
