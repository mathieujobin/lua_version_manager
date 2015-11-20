Lua Version Manager
-------------------

This aim at solving running multiple lua in one environment

I am new to Lua, and I am having problems understanding the support of Lua 5.3 with various tools. and how runtimes can not be mixed.

I am using ArchLinux as my favorite distro, which comes with Lua 5.3 by default.

I install openresty, luarocks and then lapis and encountered some 5.1 versus 5.2 versus 5.3 incompatiblity...

Searching the web for similar problems, I found my 2-3 years old post asking for Lua 5.2 support. And also people wishing for an easy version switcher. And I could not find recent answers on that matter.

So I thought building a very simple one.

This if my first draft, feel free to open a pull request to make it better.

For now, it allow me to switch lua easily.

I am taking care of setting aliases for lua and luac
And updating a symlink to the ~/.luarocks/bin

I also wrote a quick wrapper around luarocks so that the version specific bin folder exist.
and the proper luarocks is being used.

Install
--------

* Install ArchLinux
* Install openresty and lua packages
```bash
yaourt -S openresty lua lua5.1 lua5.2 luarocks luarocks5.1 luarocks5.2 tup lua-sec
```
* Download this repo somewhere and modify your .bashrc like this
```patch
diff --git a/.bashrc b/.bashrc
index a355b0c..0ac6b6d 100644
--- a/.bashrc
+++ b/.bashrc
@@ -7,3 +7,6 @@

 alias ls='ls --color=auto'
 PS1='[\u@\h \W]\$ '
+export VISUAL="vim"
+
+source ~/projects/opensource/lua_version_manager/lua_vm.bash

```
