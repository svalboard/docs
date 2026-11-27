---
title: App Layers
description: Let your Svalboard change layers by itself while a program or website is in front, such as a CAD layer while Onshape is open.
---

App Layers changes your Svalboard's layers while a given program or website is in front. Bring your CAD app to the front and your CAD layer is on. Switch away and your layers go back.

:::note[Which release you need]
App Layers needs firmware x4.6.9 or later and Keybard Overlay x4.6.9 or later. Use the two from the same release.
:::

## How it works

- **The rules live on the keyboard.** You make them in Keybard, and the keyboard keeps them, like your keymap.
- **Keybard Overlay tells the keyboard which app is in front.** Without Keybard Overlay running, no rule applies. Keybard itself doesn't need to be open.
- **Nothing a rule does is saved.** When the app leaves the front, your own layers come back.

## Set it up

### 1. Run Keybard Overlay

Install Keybard Overlay and start it, as in [Desktop overlay](/keybard/#desktop-overlay). It runs in the system tray. It follows every Svalboard connected to your computer, so there is nothing else to switch on.

To pick apps from a list instead of typing their names, also connect Keybard to it: in Keybard, choose **Overlay**, then **Connect**.

### 2. Open App Layers

In Keybard, connect your keyboard. In the left navigation, choose **More**, then **App Layers**.

**App Layers** is listed only when your keyboard's firmware has it. If it's missing, [update your firmware](/keybard/update-firmware/).

<!-- TODO screenshot: More open on the left rail, with the Overrides, Alt-Repeat and App Layers cards. -->

### 3. Add a rule

1. Choose **Add rule**.
2. Choose **Program** or **Website**.
3. Name the program or the website. See [Name the app](#name-the-app) below.
4. Choose what the rule does while that app is in front. See [What a rule can do](#what-a-rule-can-do).
5. Switch to that app and check that the layer changes. Switch back and check that your layers return.

Edits reach the keyboard the same way as every other edit. In **Live Updating** they are written as you make them. In **Manual Updates**, apply your changes first.

<!-- TODO screenshot: the App Layers panel with one Program rule and one Website rule, showing the grip and number, the Program/Website choice, the on/off switch, Default layer, Turn on layer and the layer pills. -->

## Name the app

### A program

Type the program's name, as your system names it:

| System | Name | Example |
|---|---|---|
| Windows | the program's file name, with `.exe` | `notepad.exe` |
| macOS | the app's bundle ID | `com.apple.Safari` |
| Linux | the Wayland app ID, or the X11 window class | `firefox` |

Capital letters don't matter.

When Keybard is connected to Keybard Overlay, a **Running…** list next to the name lists the apps open on your computer. Pick one to fill in its name. The refresh button next to **Add rule** reads the list again, for an app you opened after.

To find a name by hand on macOS, run `osascript -e 'id of app "Safari"'` in Terminal, with the app's name in place of Safari. On Linux with X11, run `xprop WM_CLASS` and click the app's window: the name is the second word it prints.

### A website

Choose **Website** and type the site, such as `onshape.com`. Use a website rule for an app that runs in your browser, so it doesn't apply to every tab.

- A site matches its own address and every address under it. `onshape.com` matches `cad.onshape.com` and `www.onshape.com`.
- It never matches a different site that ends the same way: `onshape.com` doesn't match `notonshape.com`.
- A longer site matches only itself and the addresses under it: `practice.svalboard.com` doesn't match `docs.svalboard.com`.
- You can paste a whole address. Keybard keeps only the site: `https://www.onshape.com/documents` becomes `onshape.com`.
- When two website rules match a tab, the longer site wins.

Every other tab, a new tab, and the browser's own pages count as the browser program. So a rule for the browser program, such as `chrome.exe`, applies to them.

Website rules work on Windows and macOS. See [On each system](#on-each-system).

## What a rule can do

A rule can do any of these, alone or together. Each one lasts only while the app is in front.

- **Default layer**: the base layer while the app is in front. Your own default layer comes back when you leave the app. If you change the default layer yourself while a rule holds it, your choice stands until a different app comes to the front.
- **Turn on layer**: one layer that is on while the app is in front, just above the default layer. Layers you turn on yourself, by holding or toggling, stay on top of it. Transparent keys on it fall through to the default layer.
- **Other layers while the app is in front**: a pill for each layer. Click a pill to change it:
  - **Unchanged**: left as you set it. This is where every pill starts.
  - **Turned on** (shown with **+**): on while the app is in front.
  - **Turned off** (struck through): kept off while the app is in front, even if you hold its layer key. Off wins over on, and over **Turn on layer**.

Leave a choice at **None**, or a pill unchanged, and the rule leaves it alone.

The mouse layer has no pill. It belongs to Auto Mouse, so mouse keys keep working as usual.

Keys you're already holding when the app changes keep their layer until you let go. Layer lights show the highest layer that is on, the same as for layers you turn on yourself.

## Examples

### A CAD layer for Onshape

You keep CAD shortcuts on layer 3, and use Onshape in your browser.

1. **Add rule**, then choose **Website**.
2. Type `onshape.com`.
3. Set **Turn on layer** to layer 3.

While an Onshape tab is in front, layer 3 is on. Other tabs keep your usual layers.

### A different base layer for a game

1. **Add rule**, then keep **Program**.
2. Type the game's program name, or pick it from **Running…**.
3. Set **Default layer** to your game layer.

### Keep a layer off in one app

If one app should never get your symbols layer by accident, add a rule for it and click that layer's pill twice, so it shows struck through.

## Turn rules on and off

- **The App Layers switch**, at the top of the panel, turns every rule on or off at once. While it's off, no rule applies and your own layers return at once. The rules stay on the keyboard.
- **Each rule's switch** turns that rule on or off. A rule that is off is skipped.
- **The trash button** deletes a rule.

## Rule order

The number next to each rule is its place in the list. To move a rule, drag it by its grip, the dotted handle next to its number. With the keyboard, focus the grip, press Space, move it with the arrow keys, and press Space again. Escape cancels.

When more than one rule that is on names the same app, the first one in the list applies. A rule for another app never gets in the way, whatever its place.

## On each system

### Windows

- **Programs**: named by their `.exe` file.
- **Websites**: in Chrome, Edge, Brave, Vivaldi and Firefox. Keybard Overlay reads the site in the browser's address bar, without a browser extension. It reads it when you switch to the browser, when you change tabs, and every few seconds.

### macOS

- **Programs**: named by their bundle ID.
- **Websites**: in Safari, Chrome, Edge, Brave, Arc and Vivaldi. Firefox tabs count as the Firefox program.
- The first time a website rule could apply in a browser, macOS asks whether the overlay app may control that browser. Allow it to use website rules there. If you choose **Don't Allow**, that browser counts as its program. To change your answer later, open **System Settings** → **Privacy & Security** → **Automation**, then quit and restart Keybard Overlay.
- The overlay asks a browser for its tab only while your keyboard has a website rule.

<!-- VERIFY: the x4.6.9 Keybard Overlay release workflow packages Windows and Linux only. How do macOS customers get the overlay app for this release? The macOS paths are unit-tested but untested on a Mac. Confirm the exact name in the macOS Automation prompt. -->

### Linux

- **Programs**: named by their Wayland app ID or X11 window class. App Layers works on:
  - any desktop on X11 (Xorg)
  - sway and Hyprland on Wayland
  - KDE Plasma on Wayland, with [kdotool](https://github.com/jinliu/kdotool) installed and on your `PATH` before you start Keybard Overlay
- GNOME on Wayland doesn't tell other apps which window is in front, so no rule applies there. If your login screen offers **GNOME on Xorg**, use that session.
- **Websites**: not on Linux yet. A browser counts as its program, and Keybard says **Websites work on Windows and Mac for now.** under a website rule.

## Limits

- **Up to 64 rules.**
- **Names up to 64 bytes.** Most letters take one byte. Accented letters and emoji take more.
- **Rules and names share 1,792 bytes on the keyboard.** Each rule takes 12 bytes plus its name. That fits 64 rules with names of about 15 letters, or 23 rules with 64-byte names. The line under the switch shows the count, such as **3 of 64 rules · 72 of 1792 bytes used**.
- If an edit doesn't fit, Keybard keeps the rule as it was and says **Not enough room left on the board.** or **Names can be at most 64 bytes.**
- **Your rules are part of your layout.** A `.svil` export holds them, an import puts them back, and Keybard restores them after a firmware update with **Restore my layout**.

## Privacy

Keybard Overlay sends the keyboard only a short code made from the app's name, or from the website rule's site. It never keeps or sends addresses or page titles, and reads a browser's address only while your keyboard has a website rule. It never changes the rules: only Keybard does.

## Troubleshooting

### Nothing changes when I switch apps

- Check that Keybard Overlay is running: its icon is in the system tray or menu bar.
- In the overlay's **⋯** menu or the tray icon, check that **Board** isn't set to **Disconnect**.
- Check that the **App Layers** switch and the rule's own switch are on.
- Check the name. On Windows it ends in `.exe`. Pick it from **Running…** to be sure.
- On Linux, check that your desktop is one listed in [Linux](#linux).

### The layers stay changed after I quit Keybard Overlay

When Keybard Overlay quits, your layers go back at once. If it stops some other way, such as a crash, they go back within 15 seconds.

### A website rule doesn't apply

- Website rules work on Windows and macOS only, in the browsers listed in [On each system](#on-each-system).
- Check the site. `cad.onshape.com` matches only that site and the addresses under it. Use `onshape.com` to match all of Onshape.
- On macOS, check **System Settings** → **Privacy & Security** → **Automation**, allow the overlay app to control your browser, then restart Keybard Overlay.

### A different rule applies than I expected

When two rules that are on name the same app, the first one in the list wins. Drag the one you want above the other, or turn the other off.

### App Layers isn't in More

Your keyboard's firmware doesn't have App Layers. [Update your firmware](/keybard/update-firmware/) to x4.6.9 or later.
