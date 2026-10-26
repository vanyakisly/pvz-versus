PvZ Versus - online 1v1. Host plays Plants, joiner plays Zombies (room code, peer-to-peer via PeerJS public broker).
Run it with a web server (python serve.py style) or upload to GitHub Pages. Needs internet for PeerJS.
Plants win by surviving 5 minutes; zombies win by reaching the house.
Music: menu theme (lobby), Choose Your Seed (waiting for opponent), lawn theme (match). Mute button top-right.
Seed selection: each player picks up to 5 seeds before the match (host: plants, joiner: zombies); the match starts when both click Ready.
Plants: Sunflower, Peashooter, Wall-nut, Snow Pea, Cherry Bomb, Repeater, Chomper, Squash, Puff-shroom.
Zombies: Zombie, Conehead, Buckethead, Football, Newspaper, Pole Vaulter, Gravestone (the zombies' "sunflower": makes 25 brains every 8s; placed on any free tile; they pop out brains that you click to collect (auto-collected after 6s)).
Help button (on the lobby screen only): Crazy Dave explains the rules in a speech bubble.
Board uses the real day-lawn background (assets/lawn.jpg) with the 9x5 grid aligned to its tiles.
