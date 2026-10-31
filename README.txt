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
Network: uses STUN + TURN relay servers (see the ICE list near the bottom of index.html) so players on different/strict networks can connect.
If joining ever still fails, put your own TURN servers in that list (free account at metered.ca gives you an iceServers list).
Join/Host now show clear errors (wrong code, server unreachable, blocked network) and time out instead of staying on "Connecting".
Squash: spots zombies on either side, looks, jumps in an arc and lands on them (animated), then disappears.
Snow Pea: slowed zombies turn blue, and animate/walk/bite at half speed.
Robustness: data files are cache-busted (anim.js?v=..., atlas.png?v=...); a drawing/logic error no longer freezes the game and shows a red error line at the bottom-left instead.
The lobby shows the version (bottom-left). If something looks broken after updating, press Ctrl+F5 once to load fresh files and check the version matches.
New units (from the supplied GIFs, converted to frame animations in assets/atlas2.webp - no GIFs are used at runtime):
 Garlic: a zombie takes one bite then swerves one lane up or down (top-lane zombies can only go down, bottom-lane only up).
 Spikeweed: zombies walk over it and take damage; only a Gargantuar smashes it.
 Tall-nut: very tough; Pole Vaulters cannot jump over it.
 Gargantuar (zombie, 350 brains): slow giant, smashes any plant in one hit (club lands ~1.7s into the swing); Chompers cannot eat it, Cherry Bomb/Squash only wound it.
Sounds: gargantuar_thump.mp3, gargantuar_death.mp3 (converted from the supplied .ogg files).
Mobile: works in landscape on phones/tablets (portrait shows a "rotate" prompt). Everything (menus, seed chooser, help, HUD) scales with the game stage.
 - Tap a seed packet, then tap a tile. Tap sun/brain pickups (larger tap area on touch screens). Shovel works by tap too.
 - Sound: the first tap unlocks audio (required by iOS/Android). Sound effects use WebAudio so they play reliably on phones.
 - Fullscreen button (top-right) on Android/iPad; on iPhone use Share > Add to Home Screen for a full-screen app (manifest + icons included).
 - The screen stays awake during a match where the browser allows it.
Connection: players now connect through an instant relay (public MQTT brokers over WebSocket, assets/mqtt.min.js) and the game upgrades to a direct WebRTC link (assets/peerjs.min.js) if one succeeds. Both libraries are bundled (no CDN needed).
Balance: longer seed cooldowns (see the table in the chat message); heavy seeds (cooldown >= 9-14s) start half-charged.
Added (from new_zombies_and_plants.zip; frames extracted into assets/atlas2.webp, no GIFs at runtime):
 Grave Digger (plant, 75 sun, 16s): only on a gravestone; digs it up in 5s then disappears; zombies can eat it meanwhile; removed if its gravestone is destroyed.
 Hypno-shroom (plant, 100 sun, 24s): a zombie that bites it turns purple, faces right and fights enemy zombies in the same lane (Gargantuar is immune and just smashes it); plant weapons ignore hypnotized zombies.
 Imp (zombie, 25 brains, 3s): small, 10 hp, speed 0.3 (normal 0.2).
Modes (lobby): 
 - Versus (online): host plays Plants, joiner plays Zombies.
 - Co-op (online): pick "Co-op" above Host Game; both players plant together (shared sun and seed cooldowns) against computer zombies.
 - Single Player: play Plants (computer sends zombies) or Zombies (computer plants). Works offline.
Settings: round length only (1-15 minutes, saved in the browser). Online, the host's round length is used.
The computer players follow the same costs, cooldowns and rules as a human.
