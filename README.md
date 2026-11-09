# OSTF Editor for Max for Live

**Version 2.1 — Official Release**

OSTF Editor is a free Max for Live device for viewing, comparing, merging, editing, organizing, and managing song data stored in the **Open Song Timeline Format (OSTF)**.

It is designed for composers, songwriters, arrangers, and music producers who work with OSTF files across multiple devices and need a central environment for inspecting, correcting, comparing, combining, and managing complete song data.

Unlike specialized OSTF Arranger devices, which focus on generating and editing specific musical parts, OSTF Editor focuses on the complete song document and the relationships between its musical components.

**Current version: v2.1**

**Supported OSTF document versions: 3.0–4.1**

Support levels vary by format version. OSTF 4.1 includes schema-aware text import and protected data handling; full visual editing of every OSTF 4.1 structure is not yet available.

---

## What's New in v2.1

Version 2.1 introduces **OSTF TEXT**, allowing users to exchange OSTF song documents between compatible devices through text rather than relying exclusively on files.

### Highlights

- New OSTF TEXT interface
- View OSTF documents as formatted JSON text
- Copy OSTF documents to the clipboard
- Import OSTF documents from pasted text
- Support text operations for File A and File B
- Improve interoperability with OSTF Composer and Arranger devices
- Add schema-aware validation for OSTF 4.0 and 4.1 text imports
- Protect existing documents against invalid imports
- Improve preservation of newer OSTF structures
- Retain the existing visual editor, comparison, merge, and MIDI workflows
- Update release metadata and version labels to v2.1

OSTF TEXT provides an additional method of exchanging song data. Existing file-based OSTF workflows remain available.

---

## OSTF TEXT

OSTF TEXT allows an OSTF document to be displayed, copied, and imported as structured text.

This is particularly useful when exchanging song data between several OSTF-compatible Max for Live devices.

### View OSTF Text

Use the **OSTF TEXT** button in the Editor toolbar.

The text interface displays the selected OSTF document as JSON.

This allows users to inspect the underlying song data, including:

- Song metadata
- Song structure
- Tempo and time signatures
- Keys and scale contexts
- Chord progressions
- Arrangement information
- Performance tracks
- MIDI notes
- MIDI performance events
- Melody and lyric relationships
- Other supported OSTF data

The text interface provides access to the document representation without requiring a separate external text editor.

### Copy OSTF

Use **COPY OSTF** to copy the selected document to the clipboard.

The copied data can be pasted into another OSTF-compatible device supporting OSTF TEXT import.

Typical uses include:

- Transferring song data from Composer to Editor
- Exchanging data between Arranger devices
- Inspecting generated OSTF data
- Sharing an OSTF document without saving an intermediate file
- Preparing data for external inspection or backup

### Import OSTF

Use **IMPORT OSTF** to paste a complete OSTF text document into the Editor.

The import process parses and validates the supplied data before it replaces the target document.

Invalid JSON or unsupported document structures are rejected rather than silently treated as valid OSTF data.

The existing document is protected against unsuccessful imports.

### File A and File B

OSTF TEXT operations support the Editor's two-document workflow.

Users can work with the documents assigned to File A and File B, allowing text-based document exchange to participate in the existing comparison workflow.

Importing a document does not automatically merge it with another document.

Comparison and merge remain separate operations.

### Example Workflow

1. Create a song in OSTF Composer.
2. Open OSTF TEXT in Composer.
3. Copy the OSTF document.
4. Open OSTF Editor.
5. Open OSTF TEXT.
6. Import the copied document into File A.
7. Import another OSTF document into File B.
8. Compare the documents.
9. Review differences and merge supported material.
10. Save the resulting OSTF document.

This workflow allows multiple OSTF devices to exchange their song data without requiring an intermediate file for every transfer.

---

## OSTF Version Compatibility

OSTF Editor supports documents from several generations of the Open Song Timeline Format.

| OSTF Version | Support |
|---|---|
| 3.0 | Legacy compatibility |
| 3.1 | Legacy compatibility |
| 3.2 | Legacy compatibility |
| 3.3 | Legacy compatibility |
| 3.4 | Editing and migration compatibility |
| 3.5 | Note-state and editing compatibility |
| 4.0 | Extended MIDI and vocal-data recognition and preservation |
| 4.1 | Schema-aware import, viewing, copying, and protected preservation |

**Important:** Recognition, validation, and preservation do not necessarily mean that every field can be edited through the visual interface.

Some newer document structures may be opened in a protected mode when the Editor cannot guarantee that an editing operation will preserve their relationships.

Opening an older OSTF file does not automatically upgrade it to OSTF 4.0 or 4.1.

The original document version is retained unless an explicit migration or conversion is performed.

---

## OSTF 4.0 and 4.1 Support

OSTF 4.0 expands the format beyond traditional note-oriented musical data.

OSTF Editor recognizes standard OSTF performance and vocal structures, including:

- MIDI channel information
- MIDI bus and routing information
- Control Change events
- Program Change events
- Pitch Bend events
- Channel Pressure
- Polyphonic Pressure
- Multiple melody tracks
- Multiple lyric and vocal relationships
- Extended performance-event information

These structures are kept as standard OSTF data rather than converted into proprietary Editor-specific extensions.

### OSTF 4.1

Version 2.1 adds schema-aware OSTF 4.1 text handling.

OSTF 4.1 introduces additional musical direction information, including Track Directions and performance-related constraints.

The Editor can import, inspect, copy, and preserve supported OSTF 4.1 documents.

However, complete visual authoring of OSTF 4.1 Track Directions and other new structures is not yet implemented.

Operations that could damage unsupported data or relationships may be restricted.

### Data Preservation

OSTF Editor prioritizes safe round-trip preservation.

Important principles include:

- Preserve supported standard fields
- Preserve unfamiliar fields whenever possible
- Avoid deleting unrelated data
- Avoid silently converting unsupported structures
- Retain MIDI performance information
- Retain vocal and melody relationships
- Preserve exact timing where possible
- Avoid automatic format upgrades
- Protect documents that cannot be safely edited

The Editor is intended to complement other OSTF devices rather than force their data into a simplified representation.

---

## Main Features

### Visual OSTF Editor

Open OSTF files in a timeline-based editor.

Supported song information includes:

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

Song information is displayed against a shared musical timeline.

This makes it easier to understand how different musical parts relate to each other.

### Global Timeline

The Global Timeline provides a song-level overview.

It includes information such as:

- Structure
- Tempo
- Time Signature
- Key Map
- Scale Contexts
- Chords
- Chord Tones
- Display Lyrics

These elements can be inspected together rather than separately in specialized Arranger devices.

Editing availability depends on the OSTF document version and the supported operation.

### Performance Tracks

The Performance Tracks area provides an overview of the instrument and performance content stored in the OSTF document.

It supports workflows involving:

- Melodic instruments
- Chord voicings
- Bass parts
- Drum and percussion tracks
- Mixed performance material
- Multiple melody parts

Tracks can be selected and inspected within the same song timeline.

Supported documents also provide track-management operations, including reordering.

### Piano Roll

The Piano Roll displays MIDI note information associated with the selected track.

This provides a visual representation of:

- Note positions
- Note lengths
- Pitch
- Timing
- Musical relationships
- Supported note attributes

The Piano Roll works alongside the timeline and track-management interfaces.

### Parameter Editing

The parameter area provides access to supported note attributes and processing operations.

OSTF 3.5 note-state information includes:

- `enabled`
- `releaseVelocity`
- `probability`
- `velocityDeviation`
- `pitchRole`
- Phrase Instance `noteStateMode`

These fields can be preserved through supported editing, comparison, merge, and save workflows.

---

## Compare Two OSTF Files

OSTF Editor supports a two-document comparison workflow.

Load one OSTF document into File A and another into File B.

The two documents can be compared to identify differences in musical content and song organization.

Comparison areas include:

- Song structure
- Chord progressions
- Melodies
- Lyrics
- Arrangement tracks
- Performance tracks
- Key maps
- Note data
- OSTF note states
- Supported metadata and song structures

This is useful when different OSTF devices have independently modified or generated material for the same song.

The comparison interface helps identify what has changed before material is merged.

---

## Visual Merge

OSTF Editor provides a visual workflow for transferring selected material between OSTF documents.

Supported workflows include:

- Selected note ranges
- Complete tracks
- Melody regions
- Arrangement parts
- Performance tracks
- Drum material
- Stored chord voicings
- Key Map data
- Lyrics-linked melody material

The Editor attempts to preserve OSTF relationships rather than flattening all information into ordinary MIDI notes.

Existing unrelated song data is preserved whenever possible.

### Selective Integration

A typical use case is combining the results of several specialized Arranger devices.

For example:

- OSTF Composer produces the harmony
- OSTF Song Writer produces a melody
- OSTF Drum Arranger produces drum patterns
- OSTF Bass Arranger produces bass material
- OSTF Sequence Arranger produces MIDI sequences

OSTF Editor can be used to inspect and combine supported parts of these documents into a single OSTF song.

Merge operations should be reviewed before application, especially when source and destination documents contain different structures or references.

---

## Performance Track Reordering

Performance Tracks can be reordered through drag-and-drop in supported editable documents.

The track-reordering system supports direct row movement.

It allows tracks to be repositioned across multiple locations without relying on separate insertion-line targets.

This is useful in arrangements containing many instrument, drum, melody, and performance tracks.

The resulting order is reflected in the OSTF document when saved.

---

## Melody and Vocal-Lyrics Handling

OSTF Editor supports workflows involving multiple melodies and vocal relationships.

Examples include:

- Main vocal
- Secondary vocal
- Harmony vocal
- Backing vocal
- Counter melody
- Additional melodic parts

Partial melody replacement requires special care because lyric units may reference specific notes.

### Keep Destination Vocal Lyrics

Replace supported musical information while retaining the existing destination lyrics.

When note timing remains compatible, existing lyric relationships can be reconnected to replacement notes.

### Notes Only

Replace note material without automatically adopting source lyric relationships.

This can be useful when note rhythm or note count changes.

Affected lyric-note relationships may be disconnected while the lyric content remains in the document.

### Adopt Source Vocal Lyrics

Copy supported melody material together with its corresponding vocal relationships.

Unsafe partial copies may be rejected when a vocal unit references notes outside the selected range.

These safeguards help prevent unrelated lyrics from becoming attached to incorrect notes.

---

## MIDI Performance Data

OSTF can store performance events alongside ordinary MIDI note data.

Supported recognized event categories include:

| Event | Description |
|---|---|
| Control Change | MIDI controller messages |
| Program Change | Instrument or program selection |
| Pitch Bend | Pitch modulation |
| Channel Pressure | Channel-wide aftertouch |
| Polyphonic Pressure | Per-note-key pressure |
| MIDI Channel | Channel assignment |
| MIDI Bus | Routing-related information |

OSTF Editor preserves supported performance-event data independently of the standard note editor.

**Preserving MIDI performance information does not mean that every MIDI event type has a dedicated visual editing control.**

Likewise, Send to Live and MIDI file export may expose different subsets of the stored OSTF data.

---

## Fixed Trigger Notes

OSTF supports notes whose pitches should remain fixed during musical transposition.

These notes use:

```text
pitchRole = fixedTrigger
```

They may represent keyswitches or other instrument-specific trigger notes.

For example, when transposing by +12 semitones:

```text
Musical note: MIDI 64 → 76
Fixed trigger: MIDI 24 → 24
```

Fixed Trigger notes are protected from normal musical transposition.

They are also excluded from ordinary melody-range and lyric-pitch processing where appropriate.

---

## Key and Genre Metadata

OSTF Editor uses standard OSTF Core fields as the authoritative source of song information.

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

Legacy or application-specific metadata is not treated as authoritative when equivalent standard OSTF fields exist.

Unknown metadata is retained whenever possible.

### Key Map Merge

The Key Map can be transferred independently from another OSTF document.

This includes:

- Initial song key
- Timeline key changes

The operation is designed to avoid replacing unrelated information, such as:

- Performance tracks
- Chord progressions
- Tempo
- Time signatures
- Scale contexts
- Lyrics
- Arrangement material

PPQ conversion must be exact.

Key-change positions are not silently rounded.

---

## High-Resolution Timing

OSTF supports high PPQ values.

OSTF Editor uses integer OSTF ticks for timing-sensitive editing operations rather than relying exclusively on rounded quarter-note values.

This helps preserve the timing accuracy of high-resolution song data.

When a timing conversion cannot be represented exactly, an operation may be rejected instead of silently rounding the result.

### Pickup Notes

OSTF supports certain notes whose local start position is negative.

These may represent pickup notes or related musical structures.

Valid negative clip-local note starts are preserved during supported editing and merge operations.

---

## OSTF 3.4 to 3.5 Migration

OSTF Editor retains its conservative migration workflow for compatible OSTF 3.4 files.

Migration does not invent OSTF 3.5 note-state values.

Existing musical data is preserved, and only the supported format upgrade is applied.

Migration operations can be undone before saving.

Older documents are not automatically converted into OSTF 4.0 or 4.1.

---

## Undo and Redo

OSTF Editor provides document-level Undo and Redo for supported editing operations.

Examples include:

- Note editing
- Visual Merge
- Melody replacement
- Key Map replacement
- OSTF migration
- Track adoption
- Track reordering

Operations are grouped so that a logical edit can usually be undone as a single action.

---

## Send to Ableton Live

OSTF Editor can send selected OSTF note material to an existing Ableton Live MIDI track.

Supported source scopes include:

- Selected notes
- Selected time range
- Entire track
- Stored chord voicing

Depending on the operation, MIDI clips can be created in:

- Session View
- Arrangement View

Supported note attributes may include:

- Probability
- Velocity deviation
- Release velocity
- Enabled/mute state

Sending material to Ableton Live does not automatically modify the original OSTF document.

### MIDI Export

OSTF Editor also provides MIDI file export.

MIDI export is separate from OSTF document saving.

Some OSTF structures do not have direct equivalents in Standard MIDI Files.

For long-term preservation of complete song data, save the OSTF document in addition to exporting MIDI.

---

## Data Preservation and Protected Editing

Preserving the original OSTF data is a primary design goal.

The Editor aims to protect:

- Unknown or unsupported fields
- Standard performance-event information
- Multiple melody relationships
- Vocal and lyric references
- Exact timing
- Original OSTF version
- Unrelated track data
- Song metadata
- Arrangement relationships

This is especially important when OSTF Editor is used as a central integration point between multiple devices.

### Protected Documents

Some documents may be opened in protected mode.

Protection may be applied when:

- The document contains structures beyond the supported editing scope
- An operation cannot safely preserve existing references
- Numerical values cannot be represented safely
- A format conversion would require unsupported transformations

Protected documents can still be inspected and used in supported non-destructive workflows.

Not every visual editing command is available for every OSTF version.

---

## Current Limitations

OSTF Editor v2.1 focuses on text exchange, document inspection, comparison, editing, merge, and safe data handling.

Some features remain outside the current release.

### OSTF 4.1 Editing

OSTF 4.1 documents support schema-aware text handling and preservation.

Full editing of all OSTF 4.1 structures, including advanced Track Directions, is not yet implemented.

### Live MIDI Import

Directly capturing existing Ableton Live MIDI clips into a new OSTF Performance Track is not included in v2.1.

The existing Send to Live functionality is a separate workflow.

### Advanced Harmony Validation

Comprehensive cross-track musical validation against chord tones, scales, and playing ranges is not yet available as a complete editing system.

### Whole-Song Time Editing

Automatic insertion or deletion of time across every song track, including all dependent OSTF structures, is not included as a complete workflow in v2.1.

### Automatic Music Generation

OSTF Editor is not intended to replace specialized composition and arrangement devices.

The following functions remain better suited to dedicated tools:

- Automatic chord progression generation
- Automatic melody generation
- Drum pattern generation
- Bass pattern generation
- Sequence generation
- Automatic phrase regeneration
- Instrument-specific performance generation

---

## Typical Workflow

A common OSTF Editor workflow is:

1. Open the main OSTF song in File B.
2. Open another OSTF document in File A.
3. Alternatively, import either document through OSTF TEXT.
4. Compare the two song timelines.
5. Select a track or musical range.
6. Review the differences.
7. Choose supported material to merge.
8. Resolve dependency or lyric warnings if necessary.
9. Apply the merge.
10. Reorder Performance Tracks if required.
11. Inspect the combined song.
12. Save the updated OSTF document.

This makes OSTF Editor useful when integrating material created by multiple OSTF-compatible devices.

---

## Role in the OSTF Ecosystem

OSTF Editor is designed primarily as a **song-level comparison, correction, merge, organization, and management environment**.

Specialized OSTF devices focus on musical generation and instrument-specific editing.

OSTF Editor provides a central location to inspect and integrate those results.

Example ecosystem:

```text
                 OSTF Composer
                       |
              OSTF Song Structure
                       |
          +------------+------------+
          |            |            |
      Song Writer  Drum Arranger  Bass Arranger
          |            |            |
          +------------+------------+
                       |
                Sequence Arranger
                       |
                 Other OSTF Tools
                       |
                       v
                  OSTF Editor
                       |
        Compare / Inspect / Merge / Edit
                       |
                       v
              Combined OSTF Song
```

This diagram represents a conceptual workflow rather than a mandatory processing order.

OSTF documents can be exchanged in different sequences depending on the project.

The Editor is not intended to replace specialized Arranger devices.

Instead, it serves as a central environment for managing the complete song document.

---

## Requirements

- Ableton Live
- Max for Live
- A compatible OSTF file for document-based workflows

The device is distributed as:

```text
OSTF_Editor_v2.1.amxd
```

OSTF Editor is a Max for Live MIDI device.

---

## Installation

1. Download `OSTF_Editor_v2.1.amxd`.
2. Copy the file to your preferred Max for Live device folder.
3. Open Ableton Live.
4. Drag OSTF Editor onto a MIDI track.
5. Open the Editor window.
6. Open an OSTF file or use OSTF TEXT to import a document.

No conversion to MIDI is required to open an OSTF document in the Editor.

---

## Open Song Timeline Format

OSTF Editor is built around the **Open Song Timeline Format**, an open text-based format for structured musical information.

OSTF can represent song structure, harmony, melodies, lyrics, instrument parts, and supported MIDI performance information.

### OSTF 4.0

https://github.com/yoh-nak/Open-Song-Timeline-Format-4.0

### OSTF 3.5

https://github.com/yoh-nak/Open-Song-Timeline-Format-3.5

Earlier OSTF versions remain relevant for backward compatibility.

OSTF 4.1 compatibility in Editor v2.1 focuses on schema-aware text exchange and protected handling of newer document structures.

---

## Version History

### v2.1 — Official Release

**OSTF TEXT and document interoperability update**

Highlights:

- Introduced OSTF TEXT
- Added formatted OSTF text display
- Added COPY OSTF
- Added IMPORT OSTF
- Added File A and File B text workflows
- Improved exchange with other OSTF-compatible devices
- Added OSTF 4.0 and 4.1 schema-aware text validation
- Improved invalid-import handling
- Improved protection of existing song data
- Preserved existing comparison and merge workflows
- Retained MIDI output and export functionality
- Updated official release version and metadata

### v2.0

**OSTF 4.0 and editor workflow update**

Highlights:

- OSTF 3.0–4.0 compatibility
- OSTF 4.0 document recognition and preservation
- MIDI performance-event support
- Control Change data preservation
- Program Change data preservation
- Pitch Bend data preservation
- Channel Pressure data preservation
- Polyphonic Pressure data preservation
- MIDI channel and bus information
- Multiple melody support
- Multiple vocal and lyric relationship support
- Visual two-file comparison
- Visual Merge
- Melody and vocal-link aware replacement
- Arrangement and drum editing
- Performance Track management
- Improved drag-and-drop track reordering
- OSTF 3.5 note-state handling
- Fixed Trigger note support
- High-PPQ timing preservation
- Key Map Merge
- OSTF 3.4 to 3.5 migration
- Undo and Redo
- Send to Ableton Live
- Backward-compatible OSTF saving

### v1.0

**Initial public release**

Highlights:

- OSTF 3.0–3.5 compatibility
- Visual two-file comparison
- Visual Merge
- Melody and lyric-aware replacement
- Arrangement and drum editing
- OSTF 3.5 note-state support
- Fixed Trigger handling
- High-resolution timing preservation
- Key Map Merge
- OSTF 3.4 to 3.5 migration
- Undo and Redo
- Send to Ableton Live
- Backward-compatible OSTF saving

---

## Support the Project

OSTF Editor and the Open Song Timeline Format projects are developed independently and are available free of charge.

If you find this project useful and would like to support continued development:

**Buy Me a Coffee**

https://buymeacoffee.com/yohsukenak

Your support helps with:

- OSTF specification development
- Max for Live device development
- Testing and compatibility improvements
- Documentation
- Future updates

Thank you for supporting the project.

---

## Author

**Yohsuke Nakano**

GitHub:

https://github.com/yoh-nak

---

## License

Please refer to the license information included with the project and repository.

When redistributing or modifying OSTF Editor, follow the terms of the applicable license.
