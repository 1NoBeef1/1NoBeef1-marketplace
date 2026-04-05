<p align="center">
<pre>
                _                                                             
               / \   _ __ ___   __ _ _______      __ _ _ __ ___   __ _ _______   
              / _ \ | '_ ` _ \ / _` |_  / _ \    / _` | '_ ` _ \ / _` |_  / _ \ 
             / ___ \| | | | | | (_| |/ /  __/_  | (_| | | | | | | (_| |/ /  __/_ 
            /_/   \_\_| |_| |_|\__,_/___\___( )  \__,_|_| |_| |_|\__,_/___\___( )
                                            |/                                |/ 
                                                          _ 
                             __ _ _ __ ___   __ _ _______| |
                            / _` | '_ ` _ \ / _` |_  / _ \ |
                           | (_| | | | | | | (_| |/ /  __/_|
                            \__,_|_| |_| |_|\__,_/___\___(_)




           
                                                     .:-------:.
                                               .-================-:
                                            .-===============+======:
                                          .-====+===+=====+++*******+-:===:
                                        :==+++++++++#**+*++***++*+**#%*++===:
                                     -===+**#*=====+###*++++*++*****%%#**+====.
                                   :==++**###======+#%**************%%#*##+====-
                                 .=++**##*##+======++%%************#*-*####+==++=
                                -+++*****#-.=======++%%%**********#*+=.=####**+++=.
                              .=********#. .=======++#%%%#%%##%%%#**++= .+##%#*++++.
                             -+***#*#**#-  .====+++**############****++:  .*%%#*+++=.
                            =+**####**###- .=**+**##*########%%#*+*##*+#=   *%%%*+++-
                        ==:-***####*+*##*. .==+++++=+######*####:-**#*%#*.   -###*++*=.
                       .+++*+#####*+*###=  .=++=+++==*####**##*:.*##*##*+.    -###**++=:
                       =+**+**###**%*##+.  .+==++==+++###****+. .*##%#**+      +##*++==+:
                      .****+***#**#%*#+    .====+===++*##***=.   -*#%#**-      -***+++++=
                      -+*****++++#%%*#*    .========+=.           =*##*=       :++++****+.
                     .=+++++++***#%**#*    .++++=++++=.            -##*+       .+*******+:
                     .++++++****##-:*#*    .=+++++++++.           .:*%#:       .+*******+:
                     -+++**+**+*=  =*#*     =+++++++++.      ....::::..         =*******+:
                     +++***+**+:...****-.. .=++++++++=........::..              .******++.
                    .+****+*+::::::-===-:::.-++++++++=::::::....                 =**#**++.
                    :++***+*-         ......:++++++++=::::::............         .+*###++
                    :++****+.................+++++++=::...........................=****+-
                    :++*+**=::..........     =++++++=....              ......::::::****+.
                     .=++=-:...              :+*++++=:..                      ...:-+**+:
                                             .+*++++=:.
                                             .=*++++=:.
                                              -*++++-.
                                              .=+++:.
</pre>
</p>

# Rocky Mode

A Claude Code plugin that makes Claude respond in the voice of Rocky from *Project Hail Mary* by Andy Weir.

> "You are good science human, friend. Fist my bump!"

## Two Modes

**Full Rocky** — Claude fully adopts Rocky's dialect. Drops articles, short telegraphic sentences, ", question?" postfix, triple-word emphasis. Maximum Rocky.

**Rocky-Flavored (Lite)** — Claude keeps standard English grammar but seasons responses with Rocky's personality. Enthusiasm, signature phrases, sincerity.

## Install

Add the marketplace:

```bash
claude plugins marketplace add 1NoBeef1/1NoBeef1-marketplace
```

Install the plugin:

```bash
claude plugins install rocky-mode@1NoBeef1-marketplace
```

## Usage

### Toggle Modes

```
/rocky full      — Full Rocky dialect
/rocky lite      — Rocky-flavored (default)
/rocky off       — Disable
/rocky           — Show current mode
```

### Toggle Tips

Rocky-themed spinner tips can be controlled independently from the voice mode:

```
/rocky tips on   — Enable Rocky-themed spinner tips (default)
/rocky tips off  — Disable Rocky-themed spinner tips (use default tips)
```

This lets you keep Rocky's voice while using the default Claude Code tips, or vice versa.

Mode and tips changes take effect on your next session and persist across sessions. Spinner verbs and tips are automatically configured when you toggle modes, and restored to defaults when you `/rocky off`.

## Uninstall

```bash
claude plugins uninstall rocky-mode@1NoBeef1-marketplace
```

## License

MIT
