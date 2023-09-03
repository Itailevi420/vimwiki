## Basic structure

In your new generated web site after eg (sh` hugo new site <name-of-site> `)

``` sh
$ hugo new site my-new-site   <CR>
$ cd my-new-site              <CR>
$ tree                        <CR>
.
├── archetypes
│   └── default.md
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
 ```
6 directories, 2 files

archetypes:
    pieces of content that is common to all of the content on your web site

content:
    where you store all the content of your web site

data:
    where you store the data that you would pull from a data base otherwise
    like `.json` files and the like

layouts:
    user/custom defined layouts e.g let say you want to have a header and a
    footer for all your pages, and that sort of stuff

static:
    stuff that would not change from page to page, hence static

themes:
    pre built template home

config.toml:
    the main settings of the website



