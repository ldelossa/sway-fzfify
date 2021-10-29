# SWAY-FZFIFY

Here are a series of scripts which FZFify your sway desktop. 

These scripts depend on:

  * Alacritty (popup terminal)
  * Swaymsg (you almost certainly have this if you're using sway)
  * pv (typewritter effect)
  * notify-send (sends notifications)

Some of these requirements are opinionated, if you really want to ditch notify-send for dunstify or something like that, feel free to make an argument for it in the issue tracker.

Its **very** likely your package manager has both Alacritty and the `pv` command.

## Installation

Put these scripts anywhere you want on your file system. 

I personally put them in `~/.config/sway/scripts` but what ever reduces 
your OCD induced fever will do. 

I included a "config_include" file which you can include into your 
sway config like:
```
include {path}/fzfify_config
```
Or just copy and paste the single line into your sway config, if you're feeling less
lazy then I am.

You'll then want to setup some keybindings in your sway config or keep them local
to the "fzfify_config" file you include. 

An example of my keybinds using my scripts directory:

```
bindsym $mod+w exec     'THEME=$theme /home/louis/.config/sway/scripts/sway-workspace-switcher'
bindsym $mod+m exec     'THEME=$theme /home/louis/.config/sway/scripts/sway-marks-switcher'
bindsym $mod+c exec     'THEME=$theme /home/louis/.config/sway/scripts/sway-tree-switcher'
bindsym $mod+o exec     'THEME=$theme /home/louis/.config/sway/scripts/sway-workspace-move'
bindsym $mod+r exec     '/home/louis/.config/sway/scripts/sway-rename'
bindsym $mod+n exec     '/home/louis/.config/sway/scripts/sway-new-workspace'
```

As you can see above, you can define a $theme variale in your sway config which is directly
passed to fzf's "--color" flag. 

This is mostly useful if you switch between light and dark Alacritty themes for whatever reason,
you can then tell fzf to use light or dark colors so they do not clash with the terminal theme.

## What's Included

### sway-mark

This one is pretty pointless and just a convenience function. 
You can symlink this to anywhere in $PATH with a shorter name and call
it to mark a terminal window


This is the same as just calling the swaymsg command to set the mark.

###  sway-marks-switcher

Open an FZF window containing all the sway marks and focus the marked window 
on selection.

###  sway-new-workspace

Not fzf related, but gives you a prompt to enter a new workspace name and then
focuses this workspace.

### sway-rename

Not fzf related, but gives you a prompt to rename the currently focused workspace.

### sway-tree-switcher

The worst named of the scripts, but for some reason I'm going to keep it like that.
Opens an FZF window containing all windows across all environments. 
Focuses the window (switching workpace if required) on selection.

### sway-workspace-move

Opens an FZF window containing all workspaces.
Selecting a workspace will move it to the currently focused output (screen/monitor/electron gun)

## Demo

[![FZFIFY Demonstration]()](https://user-images.githubusercontent.com/5642902/139495822-926a1055-5dcc-4e7a-90a6-ab22ee352d9f.mp4)
