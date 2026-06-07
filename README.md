# SSA-Flow-Management-Position-Plugin
VATSSA Flow Management Position Plugin.

## What is SSA-Flow-Management-Position

VATSSA Flow management position is a plugin made for Euroscope across the VATSIM division of VATSSA. Currently, the plugin only serves FACT while testing is being completed.
The initial code is opensource from Jamie. I am planning to create my own version as time permits.

## Features

| Feature | Details |
|---|---|
| **Destination filter** | Only processes aircraft inbound to airports defined in `holds.json` |
| **Route parsing** | Tokenises filed routes, matches waypoints against the hold database |
| **Tag item** | Custom `HLD` / `HLD*` / `FIXNAME` tag column in radar display |
| **Popup menu** | Click the tag to get a dropdown of candidate fixes from the route |
| **Advisory message** | Full structured message sent to pilot on fix assignment |
| **JSON database** | `holds.json` — editable without recompiling the DLL |
| **[FMP] button** | On-screen toggle button (top-left of radar window); click to open/close panel |
| **Status tab** | Shows tracked aircraft count, airports loaded, DB health + [Reload DB] |
| **Airports tab** | Lists every airport in the DB with live demand; click one to view its aircraft |
| **Demand tab** | Per-airport demand level (Low/Medium/High), inbound count, holding count + [Reload DB] |
| **Draggable panel** | Drag the panel title bar to reposition it anywhere on screen |

**Copied from opensource code**

### Status tab
Replaces `.fmp status` and `.fmp airports` — shows total tracked aircraft,
number of airports in the database, database load state, and a compact
airport list. A **[Reload DB]** button hot-reloads `holds.json`.
**Copied from opensource code**

### Airports tab
Replaces `.fmp list <ICAO>` — shows every airport in the DB with live demand
colour-coding (green/amber/red). Click an airport row to drill into a full
aircraft list showing callsign, assigned fix, sequence tag, and ETA.
**Copied from opensource code**

### Demand tab
Replaces `.fmp demand` — shows all **active** airports (at least one tracked
aircraft) with demand level, total inbound count, and holding count.
Includes a **[Reload DB]** button.
**Copied from opensource code**

## Tag States

```
HLD        Grey    No holding fixes found in the filed route
HLD*       Amber   One or more candidate fixes detected — click to assign
CTV        Cyan    Fix assigned; advisory message sent to pilot
```
**Copied from opensource code**

## Installation

1. Copy `FMPPlugin.dll` and `holds.json` to your EuroScope plugin folder
   (same directory as `EuroScope.exe` or any sub-folder you prefer).
2. In EuroScope → **Other SET** → **Plug-ins** → **Load** → select `FMPPlugin.dll`.
3. Add the **Hold Advisor** tag item to your radar label layout:
   **Symbology** → **Label Items** → drag `Hold Advisor` into your label string.
4. Add the **Assign Hold Fix** function to the same tag item as the click action.
5. The **[FMP]** button will appear in the top-left of every open radar window.
**Copied from opensource code**

## Advisory Message Format

```
=== TRAFFIC ADVISORY - FACT ===
TO: BAW234

HIGH TRAFFIC DEMAND — EXPECT HOLDING

HOLDING FIX  : CTV
INBOUND TRACK: 009 DEG
TURN DIR     : LEFT TURNS
MIN ALT      : 3000 FT
LEG LENGTH   : 10 NM

NOTE: THIS INFORMATION MAY CHANGE.
FOLLOW CONTROLLER INSTRUCTIONS AT ALL TIMES.
==========================================
```
**Copied from opensource code**

## To contribute

To contribute to the SSA Flow Management Position plugin, please use the dedicated guide that will be found within this github repository.

## License

Subject to change, as of this moment GNU General Public V3.0.
