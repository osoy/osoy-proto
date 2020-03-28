# Osoy

Lightweight package manager currently written in POSIX shell.
Inspired by
<a href='https://github.com/junegunn/vim-plug' />vim-plug</a>,
<a href='https://github.com/yarnpkg/yarn' />yarn</a> and
<a href='https://wiki.archlinux.org/index.php/Pacman' />pacman</a>.
It supports multiple git hosting services and asynchronous updating.

<img alt='demo' src='./demo.gif' width='100%' />

## Table of contents
* [Compatibility](#Compatibility)
* [Dependencies](#Dependencies)
* [Usage](#Usage)
    * [Operators](#Operators)
    * [Query syntax](#Query-syntax)
    * [Flags](#Flags)
* [Installation](#File-structure)
* [Configuration](#File-structure)
* [Contributions](#File-structure)

## Compatibility

It has currently been tested on Linux with dash but most likely will work on BSD and macOS with bash, zsh and possibly even on Windows with Git Bash.
Osoy aims to be easily readable and compatible with variety of platforms.

## Dependencies

    sed; grep; find; ls; sort; cut; tr; curl; git

On a \*nix system, chances are you already have these installed.
You may have to install <code>curl</code> and <code>git</code>.

## Usage

    osoy [operator] [flags]

#### Operators

    c|clone    <query*>   clone packages from GitHub, GitLab or Bitbucket
    r|remove   <query*>   remove packages
    s|symlink  [query*]   make packages' executables available in PATH
    u|update   [query*]   update (all) packages
    l|list     [query*]   list (all) packages
    dir        <query>    print package's directory path
    read       <query>    view package's README file
    license    <query>    view package's LICENSE file
    uninstall  -          uninstall osoy and all packages

#### Query syntax

    <[[domain/]author/]package>

#### Flags

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

## Installation

Curl contents of the osoy file and execute with POSIX-compliant shell.

>     curl https://raw.githubusercontent.com/osoy/osoy/master/osoy | sh

Add osoy bin directory ~/.osoy/bin to your system path.

>     PATH="$PATH:$HOME/.osoy/bin"

To make it permanent add the previous line to your shell profile — ~/.bash_profile, ~/.zprofile, ~/.profile, etc.
More at
<a href='https://www.computerhope.com/issues/ch001647.htm'>computerhope.com</a>,
<a href='https://askubuntu.com/questions/60218/how-to-add-a-directory-to-the-path'>askubuntu.com</a> or
<a href='https://www.google.com/?q=add+directory+to+path'>google.com</a>.

## Configuration

You can configure osoy by making an alias.
For example, next line will enable colors by default

>     alias osoy='osoy -c'

Following line will make it easier to navigate to package's directory

>     oycd() { cd "$(osoy dir $*)"; }

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

## Contributions

I currently don't yet know if anybody other than me would even use something like this.
Of course, if you have interest, constructive criticism and contributions are more than welcome.
