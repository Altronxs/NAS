# # TrueNAS Scale Build Documentation

![TrueNAS SCALE](https://img.shields.io/badge/TrueNAS-SCALE%2024.10.2.4-0095D5?logo=truenas&logoColor=white)
![ZFS](https://img.shields.io/badge/Filesystem-ZFS-orange)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

A home NAS built to give my family a reliable, central place to store our photos — and an excuse to slowly learn ZFS, storage planning, and self-hosting along the way.

## Table of Contents

- [Overview](#overview)
- [Current Specs](#current-specs)
- [Why TrueNAS SCALE?](#why-truenas-scale)
- [History / Timeline](#history--timeline)
- [Storage Layout](#storage-layout)
- [Services & Apps](#services--apps)
- [Notes / Future Plans](#notes--future-plans)

## Overview

This server started life as a family desktop PC and has been repurposed, upgraded, and re-platformed over the years into a dedicated NAS running TrueNAS SCALE. The whole project is driven by one simple need: my family takes a lot of photos, and we needed somewhere safe and central to keep them.

## Current Specs

| Component | Spec |
|---|---|
| OS | TrueNAS SCALE Electric Eel 24.10.2.4 |
| CPU | AMD Ryzen 5 3600X |
| RAM | 32 GB |
| Boot Drive | 500 GB NVMe SSD |
| Storage Pool 1 | 3x 2TB HDD — ZFS, single parity |
| Storage Pool 2 | 4x 2TB HDD — ZFS, single parity |

## Why TrueNAS SCALE?

The server originally ran plain Ubuntu with a manually configured ZFS pool. That worked fine, but managing everything from the command line got tedious over time. In 2023, I migrated to TrueNAS SCALE specifically for the web UI — easier pool management, monitoring, and general day-to-day administration without sacrificing ZFS underneath.

## History / Timeline

- **2017** — The hardware started life as a prebuilt desktop (AMD FX 6300, 8GB RAM), my first ever computer.
- **~2020** — The prebuilt was retired from daily use as a desktop and sat unused for a couple of years.
- **2021** — Repurposed the machine into a home server running Ubuntu, with a 3x2TB HDD ZFS pool, kicking off the project as a family photo NAS.
- **2023** — Migrated from Ubuntu to TrueNAS SCALE for a proper server UI. Upgraded the hardware at the same time: AMD Ryzen 5 3600X, 32GB DDR4 RAM, and a new NVMe SSD boot drive.
- **2025** — As the original 3x2TB pool started filling up, began planning and acquiring a second set of drives.
- **2025–2026** — Added a second ZFS pool: 4x2TB HDDs, single parity, to expand storage capacity.
- **2024** — Set up Docker on TrueNAS SCALE and deployed Jellyfin for media streaming and a Minecraft Java server for family/friends (later decommissioned).
- **2026** — Deployed Nextcloud via Docker to enable automatic photo uploads from phones while on the home network.

## Storage Layout

- **Pool 1 (2021–2026):** 3x 2TB HDD, ZFS single parity (RAIDZ1) — original storage pool, still in service.
- **Pool 2 (2025–2026):** 4x 2TB HDD, ZFS single parity (RAIDZ1) — added to expand capacity as Pool 1 approached full.

Both pools use single-parity ZFS (RAIDZ1), allowing one drive per pool to fail without data loss.

## Services & Apps

All services below run as Docker containers on TrueNAS SCALE.

| Service | Purpose | Added | Status |
|---|---|---|---|
| [Jellyfin](https://jellyfin.org/) | Media streaming for family/users | 2024 | Active |
| [Nextcloud](https://nextcloud.com/) | Auto-upload of photos from phones when on home network | 2026 | Active |
| Minecraft Java Server | Family/friends game server | 2024 | Decommissioned — no longer running |

## Notes / Future Plans

- Monitor drive health (SMART) on both pools, especially the original drives that have been in service since 2021.
- Consider a backup/replication strategy off-box for critical photo data (3-2-1 backup principle).
- Evaluate whether Pool 2 needs further expansion as photo library grows.

## About This Repo

This is personal documentation for my home NAS build — not a software project. It's here mainly as a build log / reference for myself, and for anyone else curious about setting up a similar family photo server.
