# PixelSkies for Tidbyt

PixelSkies is a custom 64×32 pixel-art weather app designed for Greg's Tidbyt
Gen 2. It alternates between live current conditions and a real three-day
forecast.

Mount Vernon, Washington remains the default location. Temperatures are shown
in Fahrenheit, observed wind is shown in knots with direction, and primary
weather data comes from Open-Meteo. NWS watches and warnings can add an alert
screen.

The handcrafted current-condition and forecast artwork is embedded inside
`pixel_skies.star`, so the live installation requires only the app file.

## Repository files

- `pixel_skies.star` — app source and embedded artwork
- `manifest.yaml` — app identity and settings metadata
- `.github/workflows/update-pixelskies.yml` — automatic five-minute render and push
- `update-pixelskies.yml` — reference copy; GitHub does not run this root copy
- `pixel_skies.gif` — visual reference retained from the previous project

## Local preview

```sh
pixlet render pixel_skies.star
pixlet serve pixel_skies.star
```

## Existing Tidbyt installation

The workflow intentionally keeps the installation ID `mountvernonweather`.
This lets PixelSkies replace the app currently running on the Tidbyt instead of
creating a second installation.

## Automatic GitHub updates

The workflow renders fresh weather and updates the existing Tidbyt installation
every five minutes. These repository secrets must remain configured:

- `TIDBYT_DEVICE_ID`
- `TIDBYT_API_TOKEN`

Renaming the GitHub repository does not remove its Actions secrets.
