# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file Pomodoro timer web application (`pomodoro.html`). No build system, no dependencies — open directly in a browser.

## Architecture

All code (HTML, CSS, JavaScript) lives in one file. The app structure:

- **Modes**: Pomodoro (专注), Short Break (短休), Long Break (长休) — toggled via mode buttons
- **Timer state**: Managed by a `state` object with `mode`, `running`, `paused`, `timeLeft`, `total`, `sessions`, `timer` (interval ID)
- **Ring progress**: SVG circle with `stroke-dashoffset` animated via CSS transition
- **Sound**: Web Audio API generates three ascending beeps at session end
- **Notifications**: Browser Notification API with permission request
- **Keyboard shortcut**: Space bar toggles start/pause
- **Auto-switch**: After a pomodoro session completes, automatically switches to short break (or long break every 4th session); after a break, switches back to pomodoro

## Key Behavior

- Changing modes while timer is running/paused shows a confirm dialog
- Adjusting time settings takes effect on next reset (or immediately if timer is idle)
- `setInterval` with 1-second tick — the single timing mechanism
- Session count persists in memory (resets on page reload)

## Common Tasks

- **Run the app**: Open `pomodoro.html` in any browser
- **Modify styles**: CSS is in the `<style>` block — uses glassmorphism design, gradient background, no CSS framework
- **Add a mode**: Add a button in `.modes`, define its time in the settings form, add its label to the switch/case objects in JS
