# Duel Draw

A private two-player sketch-and-guess game built around shared rooms, alternating turns, optional clues, and a running score.

**Live app:** https://iphiginea.github.io/dueldraw/duel-draw.html

## About

Duel Draw is designed for playing directly with one other person. One player creates a room and shares the code; the other joins, and the pair alternate between drawing and guessing without a public lobby or matchmaking layer in between.

## Features

- Private room codes for two-player games
- Alternating drawing and guessing turns
- Optional clues
- Shared scorekeeping
- Real-time synchronized room state
- Anonymous authentication and room-bound access rules

## Stack

- JavaScript
- Firebase Anonymous Authentication
- Cloud Firestore
- Firebase App Check with reCAPTCHA Enterprise
- GitHub Pages

## Security

Firestore rules bind each room to its host and guest Firebase UIDs. App Check is wired into the web client as an additional anti-abuse layer. See `APP_CHECK_SETUP.md` for deployment and enforcement notes.

## Portfolio

Read the full case study:

https://iphiginea.github.io/kiahharpool/works/duel-draw/
