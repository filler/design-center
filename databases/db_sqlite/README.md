
<pre>Copyright (C) CFEngine AS
 
This program is free software; you can redistribute it and/or modify it
under the terms of the GNU Lesser General Public License LGPL as published by the
Free Software Foundation; version 3.
   
This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

To the extent this program is licensed as part of the Enterprise
versions of CFEngine, the applicable Commerical Open Source License
(COSL) may apply to this file if you as a licensee so wish it. See
included file COSL.txt.</pre>

<h2>SQLite</h2>

<h4>AUTHOR:</h4>
 Nakarin Phooripoom <<nakarin.phooripoom@cfengine.com>>

<h4>CATEGORY:</h4>
 Databases

<h4>LICENSE:</h4>
 COPBL

<h4>PLATFORMS:</h4>
 LINUX (Redhat, CentOS, Debian, Ubuntu, SUSE)

<h4>DESCRIPTION:</h4>
 This sketch contains a bundle to install SQLite packages

<h4>REQUIREMENTS:</h4>
 * CFEngine version 3.x.x
 * Public/Private software repository
 * CFEngine standard library (`cfengine_stdlib.cf`)

<h4>INSTALLATION:</h4>
 Save `db_sqlite.cf` as `/var/cfengine/masterfiles/design-center/databases/db_sqlite.cf` in the policy hub.

<h4>SAMPLE USAGE:</h4>
> <pre>body common control
> {
>  bundlesequence => {
>                     db_sqlite("$(state)"),
>                    };
>          inputs => {
>                     "cfengine_stdlib.cf",
>                     "design-center/databases/db_sqlite.cf", 
>                    };
> }</pre>

 or call the bundle up by `methods:` promise

> <pre>body common control
> {
>  bundlesequence => { "main" };
>          inputs => {
>                     "cfengine_stdlib.cf",
>                     "design-center/databases/db_sqlite.cf", 
>                    };
> }</pre>
>
> <pre>bundle agent main
> {
>  methods:
>   any::
>    "SQLite" usebundle => db_sqlite("$(state)");
> }</pre>

 This bundle accepts only 2 values of `$(state)` parameter.

 `$(state) = "on"`
>>To install SQLite database

 `$(state) = "purge"`
>>To uninstall SQLite database

<h4>CHANGES:</h4>
 * exclude redhat not to purge SQLite packages as rpm/yum depend on libsqlite3.so.0
