# Debug Protocol



The game has a debug protocol which can be instantiated by running the game with the "-net" commandline parameter. This lets you interact with the game with other programs.

The address of this socket is [http://localhost:37010/](http://localhost:37010/). It even has an unfinished https debug page but since it isn't finished it can't really be used for anything:

![Debug page](http://i.imgur.com/mUZPufZ.png)

The debug protocol has some various features some of which is utilized in script studio:

* Reload
  * This will recompile and reload all scripts. `self.w3net.send(Request().utf8("scripts").utf8("reload").end())`
* Modlist
  * This returns the list of installed mods. `self.w3net.send(Request().pkglist().end())`
* Rootpath
  * This returns the rooth path of the game. `self.w3net.send(Request().sc_root_path().end())`
* Execute(command)
  * This will execute "command" as if you would input it into the console. `self.w3net.send(Request().remote(cmd).end())`
* Opcode(self, funcname, classname=None)
  * This will return the opcodes for "funcname". `self.w3net.send(Request().opcode(funcname, classname).end())`
* Varlist(self, section="", name="")
  * Searches for config variables. `self.w3net.send(Request().varlist(section, name).end())`
* UnfilteredLocals(self, value)
  * Enables/disables the filtering of the list of locals received from the game `self.w3net.send(Request().sd_unfiltered_locals(value).end())`
