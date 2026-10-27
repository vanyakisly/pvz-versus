PvZ Versus - online 1v1. Host plays Plants, joiner plays Zombies (room code, peer-to-peer via PeerJS public broker).
Run it with a web server (python serve.py style) or upload to GitHub Pages. Needs internet for PeerJS.
Plants win by surviving 5 minutes; zombies win by reaching the house.
Music: menu theme (lobby), Choose Your Seed (waiting for opponent), lawn theme (match). Mute button top-right.
Seed selection: each player picks up to 5 seeds before the match (host: plants, joiner: zombies); the match starts when both click Ready.
Plants: Sunflower, Peashooter, Wall-nut, Snow Pea, Cherry Bomb, Repeater, Chomper, Squash, Puff-shroom.
Zombies: Zombie, Conehead, Buckethead, Football, Newspaper, Pole Vaulter, Gravestone (the zombies' "sunflower": makes 25 brains every 8s; placed on any free tile; they pop out brains that you click to collect (auto-collected after 6s)).
Help button (on the lobby screen only): Crazy Dave explains the rules in a speech bubble.
Widescreen 16:9 board using the real day-lawn background; own-style HUD and seed chooser screen.
Characters are animated live on a canvas from the game's animation data + sprite parts (assets/anim.js, assets/p/); no GIFs.
Zombies play their death animation (head pops off); Cherry Bomb plays its explosion animation.
UI: own-style wooden seed bar (sun/brain counter, packets with recharge + unaffordable states, shovel for plants), "Choose your seeds" panel with Let's Rock!, tombstone-style main menu, progress bar.
Breaking: cones/buckets/football helmets crack in 3 stages and fall off; Newspaper Zombie goes berserk (fast) when its paper is torn.
Chomper: bite -> chew animation for ~29s -> swallow, cannot eat for 30s total.
Sounds: eating (chompsoft), hat hits/breaks, newspaper rip/rage, ready-set-plant at start, win (prize) / lose (scream + evil laugh) at the end.
Files: sprite parts are packed in assets/atlas.png (57 files total, under GitHub's 100-file browser upload limit). If the music/sounds don't play, a warning icon appears on the sound button: make sure the whole assets folder was uploaded.
