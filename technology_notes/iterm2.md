# iTerm2 Notes

iTerm2 is a replacement for Terminal and the successor to iTerm. A terminal emulator for macOS.

## Basic commands

   * '\<CMD\> + d' creates a new pane splitting vertically
   * '\<CMD\> + \<SHIFT\> + d' creates a new pane splitting horizontally
   * '\<CMD\> + \<ENTER\> ' Full screen mode. I think it's a toggle to exit
   * '\<CMD\> + ]' Cycle round panes clockwise
   * '\<CMD\> + [' Cycle round panes anti-clockwise




Having integrated shell utilities you can now do things like
   * 'imgcat \<some-image-file\>' to display in the terminal the image
   * 'imgls \<some-dir\>' to display files and those that are images have a nice little thumbnail
   * 'it2attention' requests attention, some commands are:
   * 'it2attention start' Begin bouncing the dock icon if another app is active
   * 'it2attention stop' stop bouncing the dock icon if another app is active
   * 'it2attention fireworks' Show an explosion animation at the cursor
   * 'it2check && echo "This is iTerm2" || "This is not iTerm2"' - checks if terminal is iTerm2
   * 'it2copy' copy to clipboard, e.g., 'it2copy \<filename\>' or 'cat \<filename\> | it2copy'



### References 

See documentation [here](https://iterm2.com/#/section/documentation/)
Also a workflow description from a developer [here](https://thelinuxcode.com/supercharge-your-workflow-with-iterm2-profiles-and-arrangements/)

