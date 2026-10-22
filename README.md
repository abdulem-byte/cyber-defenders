# Cyber Defenders

An Among Us-style party game for Cybersecurity Month. Four Defenders fix systems around the ship; one of them is secretly the Hacker.

**Play:** https://abdulem-byte.github.io/cyber-defenders/

No accounts, no app and no same-Wi-Fi needed.

## Start a game

1. On the laptop connected to the lounge TV, open the link above and press **Host a game on this screen**. Press F11 for full screen.
2. The TV shows a 6-letter game code and a QR code.
3. Players scan the QR code with their phone camera, or open the link and type the code, then enter their name.
4. When at least 4 players have joined, press **Start game** on the TV. Practice bots can fill empty seats.

Keep the TV page open while you play. Reloading it carries on with the same game.

## Before the event

Test once on the real lounge laptop and network: host a game, then join from one phone on office Wi-Fi and one on mobile data.
- **Check the TV lobby:** it should say "Game network: connected". If it says "Not connected", the office network blocks the game relays. Use a phone hotspot for the TV laptop, and mobile data for the players.
- **Don't update during the event:** GitHub Pages can take up to 10 minutes to serve a new version everywhere.

## How it works

`index.html` is the whole game. The TV's browser runs the game, and the TV and phones exchange messages through free public MQTT relays (EMQX, Eclipse, HiveMQ, Mosquitto) over secure WebSockets.

- **What the relays see:** only encrypted traffic. The game code sets the hidden channel and the shared key.
- **Private keys:** each phone also agrees a key of its own with the TV, so a player's role and moves can only be read by the TV and that phone.
- **Signed TV messages:** the TV signs what it sends, so nobody else can speak for it.

Bundled libraries: [MQTT.js](https://github.com/mqttjs/MQTT.js) 5.10.1 (MIT) and [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) by Kazuhiko Arase (MIT).
