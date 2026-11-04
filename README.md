# OSTF Editor for Max for Live

OSTF Editor is a Max for Live device for viewing, comparing, merging, editing, organizing, and managing song data stored in the **Open Song Timeline Format (OSTF)**.

It is designed for composers, songwriters, arrangers, and music producers who work with OSTF files across multiple devices or workflows and need a central editor for inspecting, correcting, comparing, combining, and managing complete song data.

**Current version: v2.0**

Supports **OSTF 3.0–4.0**.

---

## Main Features

### Visual OSTF Editor

Open OSTF files in a timeline-based editor and inspect complete song information including:

- Song structure
- Tempo
- Time signatures
- Key changes
- Scale contexts
- Chords
- Stored chord voicings
- Multiple melodies
- Lyrics and vocal relationships
- Arrangement tracks
- Performance tracks
- Drum events
- Mixed pitched/drum tracks
- MIDI performance information
- OSTF metadata

Song information is displayed against a shared musical timeline, making it easier to understand how different musical elements relate to each other.

---

## OSTF 4.0 Support

OSTF Editor v2.0 adds support for **OSTF 4.0** while retaining compatibility with OSTF 3.x files.

Supported versions include:

- OSTF 3.0
- OSTF 3.1
- OSTF 3.2
- OSTF 3.3
- OSTF 3.4
- OSTF 3.5
- OSTF 4.0

OSTF 4.0 extends the format beyond note-only musical data and allows richer MIDI performance and multi-part vocal information to be stored directly in the song document.

OSTF Editor recognizes and preserves OSTF 4.0 structures including:

- MIDI channel information
- MIDI bus / routing information
- Control Change events
- Program Change events
- Pitch Bend events
- Channel Pressure
- Polyphonic Pressure
- Multiple melody tracks
- Multiple lyric / vocal voices
- OSTF 4.0 performance-event data

OSTF 4.0 information is kept as standard OSTF data rather than being converted into Editor-specific proprietary extensions.

---

## OSTF 4.0 MIDI Performance Data

OSTF 4.0 can store MIDI-style performance events alongside musical note data.

OSTF Editor can recognize OSTF 4.0 performance information such as:

- **Control Change (CC)**
- **Program Change**
- **Pitch Bend**
- **Channel Pressure**
- **Polyphonic Pressure**
- MIDI channel assignment
- MIDI bus information

These events are preserved when working with OSTF 4.0 documents.

OSTF Editor does not convert OSTF 4.0 performance information into proprietary OSTF 3.x extensions.

This allows OSTF files created by other OSTF 4.0-compatible devices to pass through the Editor without unnecessarily losing performance data.

---

## Multiple Melodies and Vocal Voices

OSTF 4.0 supports songs containing multiple melody parts and multiple vocal / lyric relationships.

OSTF Editor v2.0 can work with OSTF documents containing multiple melody tracks rather than assuming that every song has only one main melody.

This makes it possible to preserve structures such as:

- Main vocal
- Secondary vocal
- Harmony vocal
- Chorus / backing vocal
- Counter melody
- Additional melodic parts

Associated lyric and vocal information can remain linked to the appropriate melody data.

---

## Compare Two OSTF Files

OSTF Editor can open two OSTF files side by side.

This is useful when different OSTF-compatible devices have produced different versions of the same song.

You can compare:

- Song structure
- Chord progressions
- Melodies
- Lyrics
- Arrangement tracks
- Performance tracks
- Key maps
- Note data
- OSTF 3.5 note states
- OSTF 4.0 song structures

Differences can then be reviewed and selectively merged.

---

## Visual Merge

Copy selected material from one OSTF file to another using the visual timeline.

Supported merge workflows include:

- Selected note ranges
- Complete tracks
- Melody regions
- Arrangement parts
- Performance tracks
- Drum material
- Stored chord voicings
- Key Map data
- Lyrics-linked melody material

The editor attempts to preserve existing OSTF relationships instead of flattening the song into plain MIDI data.

Unrelated OSTF data is preserved whenever possible.

---

## Performance Track Reordering

OSTF Editor v2.0 improves Performance Track organization.

Tracks can be reordered directly by dragging them in the Performance Tracks list.

The v2.0 reorder system uses direct row movement with fixed-step drag positioning, making it possible to move tracks accurately across multiple positions without relying on separate insertion-line targets.

This is especially useful in larger OSTF arrangements containing multiple instrument, drum, melody, and performance tracks.

The resulting visual track order is reflected in the OSTF document when saved.

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

## OSTF 3.5 Note-State Support

OSTF Editor continues to support the note-state functionality introduced in OSTF 3.5.

Supported values include:

- `enabled`
- `releaseVelocity`
- `probability`
- `velocityDeviation`
- `pitchRole`
- Phrase Instance `noteStateMode`

These values are preserved during editing, comparison, merge, and save operations.

OSTF 4.0 documents continue to use compatible note information while adding additional performance-event capabilities.

---

## Fixed Trigger Notes

OSTF supports notes whose pitch should remain fixed, such as keyswitches or trigger notes.

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

OSTF Editor uses standard OSTF Core fields as the authoritative source for song information.

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

Legacy or application-specific metadata is not treated as authoritative when equivalent standard OSTF data exists.

Unknown fields and extensions are preserved whenever possible so that opening and saving an OSTF file does not unnecessarily destroy information created by another application.

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
- Performance data

PPQ conversion must be exact.

OSTF Editor does not silently round key-change positions.

---

## OSTF 3.4 to 3.5 Migration

OSTF Editor retains its migration workflow for compatible OSTF 3.4 files.

The migration is intentionally conservative.

It does **not** invent OSTF 3.5 note-state values.

Existing song data is preserved and only the compatible format upgrade is applied.

Migration can be undone before saving.

OSTF 4.0 support does not require older files to be automatically converted to OSTF 4.0.

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
- Track reordering

Operations are grouped so that a single logical edit can usually be undone as one action.

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

OSTF note information is used where supported by Ableton Live, including:

- Probability
- Velocity deviation
- Release velocity
- Enabled / mute state

Sending note material to Live does not automatically modify the original OSTF document.

OSTF 4.0 can contain performance information beyond ordinary note data. Not every OSTF 4.0 performance-event type has a direct equivalent in every Ableton Live clip operation, so OSTF data is preserved independently of the Send to Live workflow.

---

## Backward Compatibility

OSTF Editor v2.0 supports both OSTF 3.x and OSTF 4.0 documents.

Supported versions:

```text
OSTF 3.0
OSTF 3.1
OSTF 3.2
OSTF 3.3
OSTF 3.4
OSTF 3.5
OSTF 4.0
```

Opening an older OSTF file does not automatically convert it to OSTF 4.0.

The original format version is retained unless a migration or conversion is explicitly performed.

This allows OSTF Editor to work with older OSTF projects without unnecessarily rewriting them into a newer format.

---

## Data Preservation

OSTF Editor is designed as a non-destructive editor whenever possible.

Important goals include:

- Preserve unknown OSTF fields
- Preserve unsupported extensions
- Preserve OSTF 4.0 performance data
- Preserve MIDI event information
- Preserve multiple melody relationships
- Preserve lyric and vocal relationships
- Preserve exact timing
- Preserve OSTF version
- Preserve unrelated track information
- Avoid silently inventing metadata
- Avoid silently rounding timing data
- Avoid changing unrelated song data during merge

This is especially important when OSTF Editor is used as the central integration point between multiple OSTF-compatible devices.

Files containing numerical values that cannot be represented safely may be opened in a protected mode rather than being rewritten incorrectly.

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

9. Reorder Performance Tracks if necessary.

10. Review the complete song.

11. Save the updated OSTF file.
```

This makes OSTF Editor particularly useful when combining results from multiple OSTF-compatible Max for Live devices.

---

## Intended Role in the OSTF Workflow

OSTF Editor is designed primarily as a **comparison, correction, merge, organization, and management tool**.

Specialized OSTF devices can create or modify different parts of a song, while OSTF Editor provides a central location for combining and reviewing those results.

For example:

```text
OSTF Composer
        ↓
OSTF Song Writer
        ↓
OSTF Drum Arranger
        ↓
OSTF Bass Arranger
        ↓
OSTF Sequence Arranger
        ↓
Other OSTF-compatible devices
        ↓
OSTF Editor
        ↓
Combined / corrected OSTF song
```

The Editor is not intended to replace every specialized OSTF generation or arrangement device.

Instead, it acts as a central integration and management environment for the complete OSTF song.

---

## OSTF 4.0 Editing Scope

OSTF Editor v2.0 understands significantly more OSTF information than v1.0, including OSTF 4.0 performance and multi-melody structures.

However, recognizing and preserving OSTF data does not necessarily mean that every OSTF field has a dedicated visual authoring interface.

For example, OSTF Editor can preserve OSTF 4.0 MIDI performance events even when a specific event type is not being directly edited in the current workflow.

This distinction is intentional.

OSTF Editor prioritizes safe round-trip preservation over silently discarding standard OSTF data simply because a dedicated editor control is not available.

---

## What v2.0 Does Not Try to Do

OSTF Editor v2.0 does not attempt to become a complete automatic composition or generation engine.

Examples of functions better handled by specialized OSTF devices include:

- Automatic chord progression generation
- Automatic melody generation
- Drum pattern generation
- Bass pattern generation
- Sequence generation
- Automatic phrase regeneration
- Instrument-specific performance generation

OSTF Editor focuses instead on:

- Inspection
- Comparison
- Editing
- Merge
- Track organization
- Correction
- Data preservation
- Song-level OSTF management

---

## Requirements

- Ableton Live
- Max for Live
- A supported OSTF file

The device is distributed as:

```text
OSTF_Editor_v2.0.amxd
```

---

## Installation

1. Download `OSTF_Editor_v2.0.amxd`.
2. Copy it to your preferred Max for Live device folder.
3. Open Ableton Live.
4. Drag OSTF Editor onto a track.
5. Open an OSTF file from the device.

---

## Open Song Timeline Format

OSTF Editor is built around the **Open Song Timeline Format**.

### OSTF 4.0

https://github.com/yoh-nak/Open-Song-Timeline-Format-4.0

### OSTF 3.5

https://github.com/yoh-nak/Open-Song-Timeline-Format-3.5

Earlier OSTF versions are supported for backward compatibility.

---

## Version History

### OSTF Editor v2.0

Major OSTF 4.0 and editor workflow update.

Highlights:

- OSTF 3.0–4.0 support
- Native OSTF 4.0 document handling
- OSTF 4.0 MIDI performance-data preservation
- Control Change support
- Program Change support
- Pitch Bend support
- Channel Pressure support
- Polyphonic Pressure support
- MIDI channel and bus information
- Multiple melody support
- Multiple vocal / lyric relationship support
- Visual two-file comparison
- Visual Merge
- Melody and vocal-link aware replacement
- Arrangement and drum editing
- Performance Track management
- Improved drag-and-drop Performance Track reordering
- Stable multi-position track movement
- OSTF 3.5 note-state support
- Fixed-trigger handling
- High-PPQ timing preservation
- Key Map merge
- OSTF 3.4 → 3.5 migration
- Undo / Redo
- Send to Ableton Live
- Backward-compatible OSTF saving
- Improved editor workflow and UI behavior

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
