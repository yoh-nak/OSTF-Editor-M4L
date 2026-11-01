# OSTF Editor for Max for Live

OSTF Editor is a Max for Live device for viewing, comparing, merging, editing, and managing song data stored in the **Open Song Timeline Format (OSTF)**.

It is designed for composers, songwriters, arrangers, and music producers who work with OSTF files across multiple devices or workflows and need a central editor for inspecting, correcting, comparing, and combining song data.

**Current version: v1.0**

Supports **OSTF 3.0–3.5**.

---

## Main Features

### Visual OSTF Editor

Open OSTF files in a timeline-based editor and inspect:

- Song structure
- Tempo
- Time signatures
- Key changes
- Scale contexts
- Chords
- Stored chord voicings
- Melodies
- Lyrics
- Arrangement tracks
- Drum events
- Mixed pitched/drum tracks
- OSTF metadata

Song information is displayed against a shared musical timeline, making it easier to understand how different parts of the song relate to each other.

---

## Compare Two OSTF Files

OSTF Editor can open two OSTF files side by side.

This is useful when different OSTF-compatible devices have produced different versions of the same song.

You can compare:

- Song structure
- Chord progressions
- Melody
- Lyrics
- Arrangement tracks
- Key maps
- Note data
- OSTF 3.5 note states

Differences can then be reviewed and selectively merged.

---

## Visual Merge

Copy selected material from one OSTF file to another using the visual timeline.

Supported merge workflows include:

- Selected note ranges
- Complete tracks
- Melody regions
- Arrangement parts
- Drum material
- Stored chord voicings
- Key Map data
- Lyrics-linked melody material

The editor attempts to preserve existing OSTF relationships instead of flattening the song into plain MIDI data.

---

## Melody and Vocal-Lyrics Handling

Melody editing is aware of OSTF vocal-note relationships.

For partial melody replacement, you can choose how lyrics should be handled.

### Keep Destination Vocal Lyrics

Use this when you want to replace pitch or velocity while keeping the existing destination lyrics.

When note timing remains compatible, OSTF Editor reconnects the existing lyric alignment to the replacement notes.

### Notes Only

Use this when the rhythm or number of notes changes.

The lyric text remains in the OSTF file, while affected note links can be safely disconnected.

### Adopt Source Vocal Lyrics

Use this when you want to copy both the melody and the corresponding vocal relationships from the source file.

OSTF Editor prevents unsafe partial copies when a vocal unit also references notes outside the selected range.

---

## OSTF 3.5 Support

OSTF Editor v1.0 supports the standard OSTF 3.5 note-state features, including:

- `enabled`
- `releaseVelocity`
- `probability`
- `velocityDeviation`
- `pitchRole`
- Phrase Instance `noteStateMode`

These values are preserved during editing, comparison, merge, and save operations.

---

## Fixed Trigger Notes

OSTF 3.5 supports notes whose pitch should remain fixed, such as keyswitches or trigger notes.

Notes using:

```text
pitchRole = fixedTrigger
```

are protected from normal musical transposition.

For example, if a song is transposed by +12 semitones:

```text
Musical note: MIDI 64 → 76
Fixed trigger: MIDI 24 → 24
```

Fixed triggers are also excluded from normal melody-range and lyric-pitch processing.

---

## Key and Genre Metadata

OSTF Editor uses the standard OSTF Core fields.

Examples include:

```text
song.key
timeline.keyChanges
song.scale
harmony.scales
song.genres
song.moods
song.languages
```

Legacy or application-specific metadata is not used as the authoritative source for these values.

Unknown extensions are preserved whenever possible so that opening and saving an OSTF file does not unnecessarily destroy data created by another application.

---

## Key Map Merge

A Key Map can be copied independently from another OSTF file.

This transfers:

- Initial song key
- Timeline key changes

without replacing:

- Tracks
- Chords
- Tempo
- Time signatures
- Scale contexts
- Lyrics
- Arrangement data

PPQ conversion must be exact. OSTF Editor does not silently round key-change positions.

---

## OSTF 3.4 to 3.5 Migration

OSTF Editor includes a migration workflow for compatible OSTF 3.4 files.

The migration is intentionally conservative.

It does **not** invent OSTF 3.5 note-state values.

Existing song data is preserved and only the compatible format upgrade is applied.

Migration can be undone before saving.

---

## High-Resolution Timing

OSTF can use very high PPQ values.

OSTF Editor performs timing edits using integer OSTF ticks rather than relying only on rounded quarter-note decimal values.

This helps preserve exact timing even in high-resolution OSTF files.

When PPQ conversion cannot produce an exact integer tick, the operation is stopped rather than silently rounded.

---

## Pickup and Negative Clip-Local Notes

OSTF allows certain notes to begin before the nominal start of their containing clip.

OSTF Editor preserves valid negative clip-local note starts during merge and editing.

This makes pickup notes and similar musical structures safe to transfer between OSTF files.

---

## Undo and Redo

Editing operations use document-level Undo and Redo.

Examples include:

- Note editing
- Visual Merge
- Melody replacement
- Key Map replacement
- OSTF migration
- Track adoption

Operations are grouped so that a single logical merge can usually be undone as one action.

---

## Send to Ableton Live

Selected OSTF note material can be sent to an existing Ableton Live MIDI track.

Supported source scopes include:

- Selected notes
- Selected time range
- Entire track
- Stored chord voicing

The editor can create a new MIDI clip in:

- Session View
- Arrangement View

OSTF 3.5 note information is used where supported by Live, including probability, velocity deviation, release velocity, and enabled/mute state.

The original OSTF document is not modified simply by sending notes to Live.

---

## Backward Compatibility

OSTF Editor supports:

- OSTF 3.0
- OSTF 3.1
- OSTF 3.2
- OSTF 3.3
- OSTF 3.4
- OSTF 3.5

Opening an older OSTF file does not automatically convert it to the latest version.

The original format version is retained unless a migration is explicitly requested.

---

## Data Preservation

OSTF Editor is designed as a non-destructive editor whenever possible.

Important goals include:

- Preserve unknown OSTF fields
- Preserve unsupported extensions
- Preserve lyric relationships
- Preserve exact timing
- Preserve OSTF version
- Avoid silently inventing metadata
- Avoid silently rounding timing data
- Avoid changing unrelated song data during merge

Files containing numerical values that cannot be represented safely may be opened in a protected mode instead of being rewritten incorrectly.

---

## Typical Workflow

A common OSTF Editor workflow is:

```text
1. Open the main OSTF song in File B.

2. Open another OSTF file in File A.

3. Compare the two timelines.

4. Select a track or musical range in File A.

5. Copy / drag it to File B.

6. Review the proposed changes.

7. Resolve lyric or dependency warnings if necessary.

8. Apply the changes.

9. Review the complete song.

10. Save the updated OSTF file.
```

This makes OSTF Editor particularly useful when combining results from multiple OSTF-compatible Max for Live devices.

---

## Intended Role in the OSTF Workflow

OSTF Editor is designed primarily as a **comparison, correction, merge, and management tool**.

Specialized OSTF devices can create their own musical material, while OSTF Editor can be used to combine and refine those outputs into a single song file.

Examples may include:

```text
OSTF Chord Arranger
        ↓
OSTF Song Writer
        ↓
OSTF Drum Arranger
        ↓
Other OSTF-compatible devices
        ↓
OSTF Editor
        ↓
Combined / corrected OSTF song
```

---

## What v1.0 Does Not Try to Do

Some OSTF data can be loaded and preserved even when OSTF Editor does not yet provide a dedicated authoring interface for it.

v1.0 does not attempt to become a full generation engine.

Examples of functionality intentionally left for future development include:

- Running OSTF generation engines
- Regenerating relative phrases automatically
- Applying template changes to every phrase instance
- Full localization authoring
- Full presentation-style authoring
- Replacing or appending notes inside an existing Live MIDI clip
- OSTF 4 event editing

OSTF Editor prefers to preserve unsupported standard data rather than replace it with proprietary alternatives.

---

## OSTF 4 and MIDI-Style Events

Control Change, Program Change, Pitch Bend, Aftertouch, and MPE-style event data are outside the scope of OSTF 3.5.

OSTF Editor v1.0 therefore does not introduce proprietary extensions to simulate these features.

Support can be added when the corresponding OSTF standard defines them.

---

## Requirements

- Ableton Live
- Max for Live
- A supported OSTF file

The device is distributed as:

```text
OSTF_Editor_v1.0.amxd
```

---

## Installation

1. Download `OSTF_Editor_v1.0.amxd`.
2. Copy it to your preferred Max for Live device folder.
3. Open Ableton Live.
4. Drag OSTF Editor onto a track.
5. Open an OSTF file from the device.

---

## Open Song Timeline Format

OSTF Editor is built around the Open Song Timeline Format.

OSTF repositories:

- OSTF 3.5  
  https://github.com/yoh-nak/Open-Song-Timeline-Format-3.5

Earlier OSTF versions are also supported for compatibility.

---

## Version

### OSTF Editor v1.0

Initial public release.

Highlights:

- OSTF 3.0–3.5 support
- Visual two-file comparison
- Visual Merge
- Melody and vocal-link aware replacement
- Arrangement and drum editing
- OSTF 3.5 note-state support
- Fixed-trigger handling
- High-PPQ timing preservation
- Key Map merge
- OSTF 3.4 → 3.5 migration
- Undo / Redo
- Send to Ableton Live
- Backward-compatible OSTF saving

---

## Support the Project

OSTF Editor and the Open Song Timeline Format projects are developed independently.

If you find the project useful and would like to support continued development:

**Buy Me a Coffee**

https://buymeacoffee.com/yohsukenak

Your support helps with continued OSTF specification work, Max for Live device development, testing, documentation, and future updates.

---

## Author

**Yohsuke Nakano**

GitHub:

https://github.com/yoh-nak

---

## License

Please refer to the license information included with the project and repository.

When redistributing or modifying OSTF Editor, follow the terms of the applicable license.
