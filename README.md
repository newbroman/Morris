# Nine Men's Morris

A single-file web version of the ancient board game Nine Men's Morris, playable against the computer, on one device, or online between two phones.

**Live app:** https://newbroman.github.io/Morris/

## Features

- Full rules: placing phase (nine pieces each), moving phase along the lines, mills that let you remove an opposing piece (pieces in a mill are protected unless all of the opponent's pieces are in mills), flying when reduced to three pieces, and a win by reducing the opponent to two pieces or leaving them with no legal move.
- Three ways to play:
  - Play online (two phones): one player creates a game and shares a short room code, the other joins with it. The host plays Ivory and moves first; the joiner plays Ebony.
  - Play against the computer (the menu calls it "Claude"): choose your side (Ivory first or Ebony second) and a difficulty of Easy, Medium or Hard. The opponent is a minimax search with alpha-beta pruning (depth 1, 3 and 4 for the three levels, with some randomness on Easy), not a language model.
  - Two players on one device (pass and play).
- Board drawn in SVG with highlighting of legal selections and destinations, drawn mill lines, and a status line showing pieces left to place, pieces on board and when a side is flying.
- Built-in "How to play" rules page.
- Dark wood and brass styling using Cormorant Garamond and EB Garamond fonts, laid out for phone screens.

## Using it

Open the live app in a modern browser; no installation or account is needed. It is designed for phones but works on desktop.

Online play needs both players to be connected to the internet. Moves are sent directly between the two browsers using WebRTC through PeerJS, which uses PeerJS's public broker to make the initial connection. The page loads PeerJS from unpkg and the fonts from Google Fonts, so it does not work offline. There is no manifest or service worker.

## Project structure

| File | Purpose |
|------|---------|
| `index.html` | The whole app: styles, game rules, AI, PeerJS networking, rendering and menus in one file |

## Development

There is no build step. Serve the folder with a static server and open the page:

```
python3 -m http.server
```

then open http://localhost:8000.

Testing online play on one machine needs two browser windows (or devices) and an internet connection for PeerJS.

## Notes

- The page footer reads "Made for Martin · v2".
- Peer IDs are prefixed `morris-v1-` plus the room code. Room codes are four letters; if the ID is already taken the host retries with a five-letter code, and the join box accepts four or five letters.

Built by Martin Hollingham.
