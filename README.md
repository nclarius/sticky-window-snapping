# Sticky Window Snapping

This is a fork of Toni Dietze's [Sticky Window Snapping](https://github.com/Flupp/sticky-window-snapping) modified for compatibility with my [Tile Gaps](https://github.com/nclarius/tile-gaps). This version adds an option in the configuration to set the tile gap size between windows, and will properly retain the gap when resizing adjacent windows.

## Installation

1. Clone the repository (top right green button *Code* > *Download ZIP* > unpack, or `git clone https://github.com/nclarius/sticky-window-snapping.git`).
2. Change into the folder, and run `kpackagetool-install.bash` (click on the file > *Execute*, or `./kpackagetool-install.bash`).

## Configuration

*System Settings* > *Window Management* > *KWin Scripts* > settings button for the script.

You may need to disable and re-enable the script (using the checkbox) in order for the changes to take effect.

## 

N.C.

<hr>

KWin script to let snapped window edges stick together when one window is resized.

The script provides an easy to use configuration dialog, which can be reached via `systemsettings`.
(However, note section “Bugs and Workarounds”.)

Additionally, the script registers two global shortcuts: one for enabling/disabling the script permanently, and one for enabling/disabling the script only for the next resize.
The default shortcut keys are Meta+Shift+S and Ctrl+Shift+S, respectively.
You can change them using `systemsettings` (or `kcmshell4 keys`); they are associated with the component “KWin”.
Their names are prefixed by “KWin Script: Sticky Window Snapping”.


## Bugs and Workarounds

* If the configuration dialog is not reachable via `systemsettings`, then try the following command and restart `systemsettings`:

      mkdir --parents ~/.local/share/kservices5/
      ln --relative --symbolic ~/.local/share/kwin/scripts/sticky-window-snapping/metadata.desktop ~/.local/share/kservices5/kwin-script-sticky-window-snapping.desktop

* If the script does not work, increasing the threshold in the configuration dialog might help.


## Known issues

* There is no optical feedback when a shortcut is pressed.
  I do not know how to initiate a KNotify notification from a KWin script.
  There is the function `callDBus`, but I do not know if or how it can be used for that purpose.
  KNotify provides the method `event` via D-Bus, but it expects arguments of types for which I do not know how to produce values with JavaScript.
* Currently, not only snapped window edges are considered as connected, but even edges which are only on the same row/column are considered as connected.
  I have not decided yet if this is a bug or a feature.
