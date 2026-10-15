# Genius Kids Academy

English-only kids educational hub (ages ~4–8) by **Yousef Joudeh**.

## Sections
Letters (phonics + spelling) · Numbers · Science Explorer · Memory Palace · Logic Lab · Daily Challenge · Avatar shop · Card book · Parent report

## Builds
```bash
python3 build.py                 # Playables → dist/   Web → dist_web/
PACK=en python3 build.py         # default English pack (data_en.js)
# Future Arabic edition (separate game/title/repo):
#   add src/data_ar.js matching PACK shape, then PACK=ar python3 build.py
```

## Ads (disabled in v1)
Single flag **`ADS_ENABLED`** (injected at build time):

| Build | Flag | Behavior |
|-------|------|----------|
| Default (`python3 build.py`) | `false` | **No ads.** Rewarded buttons are not rendered. |
| v2 Playables with ads | `ADS=1 python3 build.py` | Rewarded (`gka_bonus_coins`, `gka_avatar_unlock`) + interstitial between sections (never mid-level, ≥3 min gap). |

When an ad runs: game audio/timer pause (`adBusy`), then resume. Uses YouTube `requestRewardedAd` / `requestInterstitialAd` only inside Playables.

## Playables checklist
- `firstFrameReady` → `loadData` → `gameReady`
- Save via `ytgame.game.saveData` after load
- Pause/resume via `onPause`/`onResume` only (no `visibilitychange`)
- Audio via `isAudioEnabled` / `onAudioEnabledChange`
- Single `index.html`, no external network except YouTube SDK
- Publisher: Yousef Joudeh · No ads in v1

## Form
- **App ID:** `genius-kids-academy`
- **Title:** Genius Kids Academy
- **Description:** Learn ABCs, numbers, science & logic with Leo & friends! Trace letters, spell words, collect cards & daily trophies. Bright, safe fun for ages 4–8.
- **Genres:** Educational, Kids
