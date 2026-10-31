# 🌋 The Floor Is Lava: La Palma 2021

Watching the 2021 La Palma eruption from space, using Sentinel-2 satellite imagery and Python.

![La Palma eruption gallery](la_palma_gallery.png)

## What this shows

On 19 September 2021, a new volcano (now named Tajogaite) erupted on La Palma in the Canary Islands. It erupted for 85 days, until 13 December 2021, sending lava west across the island and into the sea.

This project tracks the eruption in **shortwave infrared (SWIR)**. Hot lava glows strongly at SWIR wavelengths, so active flows show up bright orange-red, even through thin smoke. The gallery runs from **15 September 2021** (four days before the eruption: no glow) to **December 2021** (after it ended: a cooled black scar).

## How it works

1. **Search:** query a satellite catalogue (STAC) for Sentinel-2 images over the volcano between two dates
2. **Get the cards:** each result is a catalogue entry with the date, cloud cover and links to the image files
3. **Load the pixels:** download only the three bands needed, and only for a small box around the volcano
4. **Make the pictures:** combine the bands into a false-colour image for each date

**Band combination:** B12 (SWIR) → red, B11 (SWIR) → green, B8A (near infrared) → blue.
Hot lava appears red to yellow, and vegetation appears blue, because plants are very bright in near infrared.

## Data

- **Satellite:** Sentinel-2, Level-2A (Collection 1)
- **Source:** [Element 84 Earth Search](https://earth-search.aws.element84.com/v1), free, no account needed
- **Area:** around the eruption site (bbox: -17.98, 28.58, -17.84, 28.66)
- **Dates:** 15 Sept 2021 to 8 Jan 2022, giving 22 image dates
- **Resolution:** 20 m pixels

- ## Limitations

- **Clouds and ash** hide the lava on many days. Some frames show mostly cloud.
- **Only active lava glows.** Lava that has cooled stops showing in SWIR, so the glow shows where lava is *flowing*, not the full area covered.
- **Brightness varies between images**, because each one is contrast-stretched on its own.
- 
## Tools

Python · pystac-client · odc-stac · xarray · numpy · matplotlib · Google Colab
