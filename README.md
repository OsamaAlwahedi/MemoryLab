# MemoryLab

An adaptive flashcard study app that connects active recall with a transparent memory model. Open the deployed site, review the sample cards, or create a deck and add your own.

## Features

- Deck and card creation, review sessions, due dates, and review history
- Review ratings (Again, Hard, Good, Easy), confidence, and answer time adjust the next interval
- Dashboard with due cards, mastered cards, estimated retention, and seven-day review activity
- Responsive layout and local browser storage, with no account required

## Scheduling model

Each card starts with a stability value of one day. A missed card reduces stability and returns after ten minutes. A successful answer multiplies stability according to recall quality, then confidence and answer time modify that gain. The next interval follows the resulting stability, with shorter intervals for hard answers. A card is mastered after at least two reviews and stability of at least seven days. Estimated retention uses `exp(-elapsedDays / stability)` averaged across practiced cards.

This is a heuristic based on spaced repetition principles. It is **not** a model trained on user data, and estimated retention is **not** a measured recall score.

## Run locally

Serve this folder with any static HTTP server, for example `python3 -m http.server 8000`, then open `http://localhost:8000`.

## Data and scope

All data is stored in `localStorage` for this browser and device. Clearing site data removes it. This version does not include accounts, cross-device sync, or a trained machine learning component. Sample decks are included to make the first session immediately usable.
