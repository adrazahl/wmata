# My Metro

A small phone web app that shows live WMATA Metrorail arrival times for my commute and favorite stations.

## What it does

- **Morning / Evening tabs:** the next trains for one line and direction at a set station. Opens to the right tab automatically based on the time of day.
- **Favorites tab:** arrival boards for any stations I star, in the order I choose.
- **Backup station:** each commute can have a backup station (for example King St-Old Town). A switch at the bottom of the card flips between them.
- **Disruptions:** if trains on your line end early or get rerouted, the commute card shows where they're actually going, other trains from the same platform, and WMATA's alert text.
- **Station alerts:** favorite stations show a collapsible list of current train alerts for their lines.
- **Metro map:** the map button opens WMATA's rail system map (`map.svg`, converted from the official PDF) inside the app, with pinch-to-zoom.
- **Live data:** refreshes every 20 seconds. Trains on the station sign show in dark text with car counts. Trains further out, from WMATA's longer-range feed, show in gray.

## Using it

Open the GitHub Pages link on a phone and add it to the home screen.

It needs a free WMATA API key from [developer.wmata.com](https://developer.wmata.com/) (subscribe to the **Default Tier**, then copy the primary key from your profile). The key is entered in the app and saved only in that browser. It is never stored in this repository.

## How it works

Everything is in one file, `index.html`. No build step, no server. It reads from:

- WMATA Real-Time Rail Predictions API (station-sign arrivals)
- WMATA GTFS-Realtime rail trip updates (longer-range arrivals)
- WMATA Rail Incidents API (delays and alerts by line)
- WMATA station path API (which platform track heads which way)

Settings (favorites, commutes, API key) are kept in the browser's local storage.

Data provided by WMATA under its [Transit Data Terms of Use](https://developer.wmata.com/license).
