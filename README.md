# 📡 Radio Spectrum Explorer

An interactive visual guide to the radio spectrum — from 3 Hz to 300 GHz.

**Live demo:** https://radio.az.jen.re

## Features

- **Interactive frequency slider** (logarithmic scale) — everything updates in real time
- **Animated sine wave** — wavelength and speed change visually as you scroll
- **Usage icons** per band (submarines, aircraft, GPS, WiFi, satellites...)
- **Propagation animations** — waveguide (VLF), ionospheric bounce (HF), line-of-sight (VHF+)
- **Diffraction canvas** — see how waves pass through or are blocked by walls
- **Bandwidth & throughput panel** — from 10 bit/s (VLF) to 20+ Gbit/s (mmWave)
- **Material attenuation** — air / wood / concrete / metal in dB
- **Full spectrum bar** — clickable, with markers for FM, GPS, ADS-B, WiFi, 5G...
- **Accordion** — all 8 bands detailed (VLF, LF, MF, HF, VHF, UHF, SHF, EHF)

## Bands covered

| Band | Range | Examples |
|------|-------|---------|
| VLF | 3 Hz – 30 kHz | Submarine comms, OMEGA nav |
| LF | 30 – 300 kHz | AM longwave, DCF77, LORAN |
| MF | 300 kHz – 3 MHz | AM radio, 500 kHz distress |
| HF | 3 – 30 MHz | Shortwave, ham radio, STANAG |
| VHF | 30 – 300 MHz | FM radio, aviation, marine |
| UHF | 300 MHz – 3 GHz | 4G/5G, WiFi, GPS, ADS-B |
| SHF | 3 – 30 GHz | WiFi 5/6 GHz, radar, Ku/Ka sat |
| EHF | 30 – 300 GHz | 5G mmWave, airport scanners |

## Stack

Pure HTML/CSS/JS — zero dependencies, zero frameworks.  
Single `index.html` file. Self-hosted with nginx + Docker + Traefik.

## Self-host

```bash
docker compose up -d
```

Then point your reverse proxy to port 80.
