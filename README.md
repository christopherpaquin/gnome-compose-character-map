Custom Compose Key Configuration (GNOME / Linux)
================================================

This document explains how to configure and use a **custom Compose key** on GNOME-based Linux systems to type common Unicode symbols (check marks, arrows, typography, math symbols, etc.) directly from the keyboard.

The configuration works system-wide, including:

-   Gmail (email body)

-   LibreOffice

-   Google Docs

-   VS Code

-   Markdown editors

-   Most terminals with UTF-8 support

* * * * *

What Is the Compose Key?
------------------------

The **Compose key** allows you to type Unicode characters by pressing a short sequence of keys instead of memorizing numeric codes.

Example:

-   `Compose g c` → ✅

-   `Compose r x` → ❌

* * * * *

Prerequisites
-------------

-   GNOME desktop (Wayland or X11)

-   UTF-8 locale (default on modern Linux)

-   Standard XKB keyboard layout (US layout assumed)

* * * * *

Step 1 --- Assign a Compose Key
-----------------------------

### Recommended: Right Alt

`gsettings set org.gnome.desktop.input-sources xkb-options "['compose:ralt']"`

Log out and log back in.

### Alternatives

If Right Alt is needed for AltGr, choose one of the following:

`gsettings set org.gnome.desktop.input-sources xkb-options "['compose:menu']"`

`gsettings set org.gnome.desktop.input-sources xkb-options "['compose:caps']"`

* * * * *

Step 2 --- Create `~/.XCompose`
-----------------------------

Create or edit the file:

`nano ~/.XCompose`

Paste the following content:

`include "%L"

# =====================================================
# Status / Review Markers
# =====================================================
<Multi_key> <g> <c>        : "✅"
<Multi_key> <r> <x>        : "❌"
<Multi_key> <c> <h>        : "✔"
<Multi_key> <x> <o>        : "✘"
<Multi_key> <b> <c>        : "☑"
<Multi_key> <b> <x>        : "☒"

# =====================================================
# Arrows
# =====================================================
<Multi_key> <-> <->        : "→"
<Multi_key> <<> <->        : "←"
<Multi_key> <=> <->        : "⇒"
<Multi_key> <-> <=>        : "⇐"
<Multi_key> <-> <v>        : "↓"
<Multi_key> <-> <^>        : "↑"

# =====================================================
# Comparison / Logic
# =====================================================
<Multi_key> <=> <=>        : "≡"
<Multi_key> <!> <=>        : "≠"
<Multi_key> <<> <=>        : "≤"
<Multi_key> <>> <=>        : "≥"
<Multi_key> <a> <n>        : "∧"
<Multi_key> <o> <r>        : "∨"
<Multi_key> <n> <o>        : "¬"

# =====================================================
# Typography
# =====================================================
<Multi_key> <-> <.>        : "--"
<Multi_key> <-> <-> <.>    : "---"
<Multi_key> <'> <'>        : "'"
<Multi_key> <'> <">        : """
<Multi_key> <"> <'>        : """
<Multi_key> <.> <.> <.>    : "..."

# =====================================================
# Math / Technical
# =====================================================
<Multi_key> <p> <i>        : "π"
<Multi_key> <d> <e>        : "°"
<Multi_key> <m> <u>        : "µ"
<Multi_key> <i> <n>        : "∞"
<Multi_key> <s> <q>        : "√"

# =====================================================
# Currency
# =====================================================
<Multi_key> <e> <u>        : "€"
<Multi_key> <g> <b>        : "£"
<Multi_key> <y> <e>        : "¥"

# =====================================================
# Bullets / UI
# =====================================================
<Multi_key> <o> <o>        : "-"
<Multi_key> <s> <s>        : "§"`

Save the file and **log out and log back in**.

* * * * *

Step 3 --- Using the Compose Key
------------------------------

Press the **Compose key**, then the key sequence.

### Common examples

| Keys | Output |
| --- | --- |
| Compose g c | ✅ |
| Compose r x | ❌ |
| Compose - - | → |
| Compose < = | ≤ |
| Compose . . . | ... |
| Compose p i | π |
| Compose m u | µ |

* * * * *

Fallback: Unicode Input (Always Works)
--------------------------------------

If Compose is unavailable:

-   Press `Ctrl + Shift + U`

-   Type the Unicode value

-   Press `Enter`

Examples:

-   `2705` → ✅

-   `274C` → ❌

-   `2714` → ✔

-   `2718` → ✘

* * * * *

Verification
------------

Check the active keyboard options:

`gsettings get org.gnome.desktop.input-sources xkb-options`

Expected output (example):

`['compose:ralt']`

Test in a GTK app:

`gnome-text-editor`

If it works there, it will work in browsers and document editors.

If it works there, it will work in browsers and document editors.
