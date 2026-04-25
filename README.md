# MoErgo Go60 Custom Configuration for ZMK

![MoErgo Logo](moergo_logo.png)

This repository contains my custom ZMK configuration for the MoErgo Go60, based on a QMK layout from a BastardKB Dilemma and adapted to the physical geometry of the Go60.

## Current Layout

This keymap currently uses 5 layers:

1. `Base` - QMK base layer ported to Go60
2. `Magic` - original ZMK Go60 magic layer
3. `Programming` - QMK programming symbols layer
4. `Nav` - QMK navigation layer
5. `Numbers` - QMK numbers/F-row layer

## Base Layer

| - | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 0 | - |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TAB | Q | W | E | R | T | Y | U | I | O | P | \ |
| ESC | GUI/A | ALT/S | CTL/D | SFT/F | G | H | SFT/J | CTL/K | ALT/L | GUI/; | ' |
| - | Z | X | C | V | B | N | M | , | . | / | ALT |

Lower block:

| Left extra | Left extra | Left extra | Right extra | Right extra | Right extra |
| --- | --- | --- | --- | --- | --- |
| - | LCLK | DEL | NAV | - | - |

| Left thumb | Left thumb | Left thumb | Right thumb | Right thumb | Right thumb |
| --- | --- | --- | --- | --- | --- |
| BSPC | PROG | NUM | MAGIC | ENTER | SPACE |

## Other Layers

`Magic`
- Bluetooth profile management
- RGB controls
- media controls
- reset / bootloader access

| BTCLR | BRI- | BRI+ | PREV | NEXT | PLAY | MUTE | VOL- | VOL+ | - | - | BTALL |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| BOOT | RGB SPI+ | RGB SAT+ | RGB HUE+ | RGB BRI+ | RGB TOG | - | - | - | - | - | BOOT |
| RESET | RGB SPD+ | RGB SAT- | RGB HUE- | RGB BRI- | RGB EFF | - | - | - | - | - | RESET |
| - | - | BT0 | BT1 | BT2 | BT3 | - | - | - | - | - | BASE |

| Left extra | Left extra | Left extra | Right extra | Right extra | Right extra |
| --- | --- | --- | --- | --- | --- |
| USB | - | - | - | - | - |

| Left thumb | Left thumb | Left thumb | Right thumb | Right thumb | Right thumb |
| --- | --- | --- | --- | --- | --- |
| - | - | - | - | - | - |

`Programming`
- programming symbols like `` ` $ ^ ( ) @ # % & { } = ? * [ ] ! \ ``
- right thumb cluster keeps `Enter`, `<`, `>`

| - | - | - | - | - | - | - | - | - | - | - | - |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| - | - | ` | - | $ | - | ^ | ( | ) | - | - | - |
| - | SFT | @ | # | % | - | & | { | } | = | ' | - |
| - | ` | - | - | ? | - | * | [ | ] | ! | \ | - |

| Left extra | Left extra | Left extra | Right extra | Right extra | Right extra |
| --- | --- | --- | --- | --- | --- |
| TRNS | TRNS | TRNS | - | - | - |

| Left thumb | Left thumb | Left thumb | Right thumb | Right thumb | Right thumb |
| --- | --- | --- | --- | --- | --- |
| TRNS | TRNS | TRNS | ENTER | < | > |

`Nav`
- left-hand modifiers: `GUI ALT CTRL SHIFT`
- right-hand navigation: arrows, `INS`, `HOME`, `PGDN`, `PGUP`, `END`

| - | - | - | - | - | - | - | - | - | - | - | - |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| - | - | - | - | - | - | - | - | - | - | - | - |
| - | GUI | ALT | CTL | SFT | - | LEFT | DOWN | UP | RIGHT | CAPS | - |
| - | - | - | - | - | - | INS | HOME | PGDN | PGUP | END | - |

| Left extra | Left extra | Left extra | Right extra | Right extra | Right extra |
| --- | --- | --- | --- | --- | --- |
| - | - | - | TRNS | - | - |

| Left thumb | Left thumb | Left thumb | Right thumb | Right thumb | Right thumb |
| --- | --- | --- | --- | --- | --- |
| - | - | - | - | ENTER | - |

`Numbers`
- left side: `F1-F9` plus modifiers
- right side: `1-9`, `0`

| TRNS | TRNS | TRNS | TRNS | TRNS | TRNS | TRNS | TRNS | TRNS | TRNS | TRNS | TRNS |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TRNS | TRNS | TRNS | F7 | F8 | F9 | TRNS | 7 | 8 | 9 | TRNS | TRNS |
| TRNS | SFT | ALT | F4 | F5 | F6 | TRNS | 4 | 5 | 6 | 0 | TRNS |
| TRNS | GUI | CTL | F1 | F2 | F3 | TRNS | 1 | 2 | 3 | TRNS | TRNS |

| Left extra | Left extra | Left extra | Right extra | Right extra | Right extra |
| --- | --- | --- | --- | --- | --- |
| TRNS | TRNS | TRNS | TRNS | TRNS | TRNS |

| Left thumb | Left thumb | Left thumb | Right thumb | Right thumb | Right thumb |
| --- | --- | --- | --- | --- | --- |
| TRNS | TRNS | TRNS | TRNS | TRNS | TRNS |

## Reference Files

- `config/go60.keymap` - actual ZMK keymap in use
- `go60-layouts-ascii.txt` - ASCII layout reference
- `go60-layouts.svg` - SVG layout reference
- `config/go60.keymap.backup-pre-port-2026-04-25` - backup of the previous keymap before the QMK-style port

## Notes

- The lower block must follow the Go60 physical order used in `main`:
  - line 5 of each layer = extra row
  - line 6 of each layer = thumbs
- This repository builds a single `go60.uf2`, but the same UF2 must be flashed to both halves.

```text
Line 5 = extra row:  L_C4R5  L_C3R5  L_C2R5  |  R_C2R5  R_C3R5  R_C4R5
Line 6 = thumbs:     L_T1    L_T2    L_T3    |  R_T3    R_T2    R_T1
```

Legend:

- `TRNS` = transparent
- `GUI/A` = `GUI` on hold, `A` on tap
- `LCLK` = left click
- `PROG` = Programming layer
- `NUM` = Numbers layer

## Resources

- The [official MoErgo Go60 Support](https://moergo.com/go60-support) web site. Go60 documentation and other technical resources.
- The [official MoErgo Discord Server](https://moergo.com/discord). Instant conversations with other Go60 users.

- The [official ZMK Documentation](https://zmk.dev/docs) web site. Find the answers to many of your questions about ZMK Firmware.
- The [official ZMK Discord Server](https://discord.gg/8cfMkQksSB). Instant conversations with other ZMK developers and users. Great technical resource!

- The [official MoErgo ZMK Distribution](https://github.com/moergo-sc/zmk). Repository for ZMK firmware customized for Go60 and Glove80.

## Firmware Files
To locate your firmware files and reflash the keyboard:

1. Open the repository on GitHub.
2. Go to `Actions`.
3. Open the desired `Build` workflow run.
4. Download the `go60.uf2` artifact.
5. Flash that same `go60.uf2` to the left half.
6. Flash that same `go60.uf2` to the right half.

After both halves are flashed, power on the left half first and then the right half.
