# Pebble Discover

An alternative way to browse the [Pebble app store](https://apps.repebble.com), built to make new and popular watchfaces and apps easier to find. It's a single static page (`index.html`) with no build step and no dependencies.

This is an unofficial project and isn't affiliated with Pebble or Rebble.

## Features

- Separate **Watchfaces** and **Apps** tabs
- Sort by **Trending**, **Most liked**, **Newest uploads**, **Recently updated**, or **A to Z**
- **Made for PT2** filter (on by default) that only shows items with a build for the Pebble Time 2
- Category filter for apps, plus search by title or author
- Results appear as they load, and the list scrolls infinitely

## How Trending works

The store only provides each item's total number of likes, so there is no real trend data. Trending is an estimate:

```
score = (likes + 1) / (months since upload + 2) ^ 0.8 * (1 + 30 / (days since last update + 30))
```

Newer items with decent likes rank above older ones with the same likes, and recently updated items get a boost.

## Hosting on GitHub Pages

1. Put `index.html` and this `README.md` in a GitHub repository.
2. Go to **Settings > Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick your main branch and the `/ (root)` folder, then save.
4. After a minute or so the site is live at `https://<your-username>.github.io/<repo-name>/`.

## Notes

- The page fetches data directly from the public Pebble app store API in each visitor's browser, so it needs no server. If the API doesn't allow requests from your Pages domain (a CORS restriction), the page will show an error saying so.
- The catalog is cached in the visitor's browser for 6 hours. The **Refresh** button fetches fresh data.
- Clicking an item opens its page on the official store.
