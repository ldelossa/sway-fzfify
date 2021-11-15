# SWAY-FZFIFY

Here are a series of scripts which FZFify your sway desktop. 

These scripts depend on:

  * fzf
  * alacritty (popup terminal)
  * swaymsg (you almost certainly have this if you're using sway)
  * pv (typewritter effect)
  * notify-send (notifications)
  * jq (processing swaymsg output)
  * setsid (dmenu launcher)
  * fd (finding files)

Some of these requirements are opinionated, if you really want to ditch notify-send for dunstify or something like that, feel free to make an argument for it in the issue tracker.

Its **very** likely your package manager has all these depedencies available.

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

Not fzf related, but gives you a prompt to enter a mark for the focused window. 

###  sway-marks-switcher

Open an FZF window containing all the sway marks and focus the marked window 
on selection.

You can also hit the "d" key to delete a mark.

###  sway-new-workspace

Not fzf related, but gives you a prompt to enter a new workspace name and then
focuses this workspace.

### sway-rename

Not fzf related, but gives you a prompt to rename the currently focused workspace.

### sway-tree-switcher

The worst named of the scripts, but for some reason I'm going to keep it like that.
Opens an FZF window containing all windows across all environments. 
Focuses the window (switching workpace if required) on selection.

### sway-window-move

Open an FZF window containing all workspaces and move the currently focused window
to the selected workspace.

By specifying a non-listed workspace the window will be moved to a newly created workspace
of the given name. 

If a name conflict is about to occur suffix the new workspace with ":new" with no space. 

For example, if a workspace named "apps" currently exists and you want to move a window to workspace "apps-1" 
input the string "apps-1:new" to FZF and the scripts will rip off ":new" from the created workspace name.

### sway-workspace-move

Opens an FZF window containing all workspaces.
Selecting a workspace will move it to the currently focused output (screen/monitor/electron gun)

### sway-dmenu

Opens an FZF window with a list of discovered desktop apps.
Selecting an application will launch it in it's own subshell and exit fzf. 

Currently, .desktop field codes such as %F and %U are stripped from the final
command executed.

## Demo

[![FZFIFY Demonstration]()](https://user-images.githubusercontent.com/5642902/140243728-c71cd06e-393f-429a-ab11-6cf9b8508b0e.mp4)
