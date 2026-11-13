# OSTF Editor for Max for Live

**Version 2.3 — Official Release**  
**Open Song Timeline Format (OSTF) 3.0–4.2 compatibility**

OSTF Editor is a free Max for Live device for **viewing, comparing, editing, merging, organizing, and preserving complete song documents** in the Open Song Timeline Format (OSTF).

It serves as the song-level integration point for OSTF Composer, Song Writer, Producer, Drum Arranger, Bass Arranger, Sequence Arranger, and other compatible tools. Specialized devices focus on writing or shaping individual parts; OSTF Editor focuses on the relationships among song structure, harmony, tracks, MIDI performances, melodies, lyrics, and metadata.

**Version 2.3 restores the internal GM instrument and drum-kit workflow, corrects drum/percussion routing, and improves the distinctness, level, and sustain of built-in cymbal sounds.** The earlier OSTF 4.2, Vocal Export, configurable timeline, OSTF TEXT, two-file comparison, Visual Merge, and MIDI workflows remain available.

**Single-file distribution:** `OSTF_Editor_v2.3.amxd` contains the preview sound engine. No separate drum JavaScript, WAV, or SoundFont files are required.

> **Compatibility note:** Reading or preserving an OSTF field does not imply that every field can be edited or merged visually. Some newer documents or operations use protected handling to avoid data loss. Vocal-format exports are experimental and should be checked in the destination application.

---

## What's New in v2.3

Version 2.3 is a **drum playback and built-in sound-source maintenance release**. It restores the simple sound selection workflow and retains all major OSTF editing capabilities from v2.2.

### Internal Instrument and Drum-Kit Selection

- Restore **128 General MIDI program choices** for pitched instrument preview.
- Restore **four built-in drum-kit presets**: Electronic, Acoustic-style, Tight, and 808-style.
- Remove the experimental selection workflow that attempted to choose instruments from other Ableton Live tracks. The track sound control once again focuses on Editor's **own internal preview sound sources**.
- Route recognized drum and percussion notes to the dedicated drum engine instead of treating them as pitched General MIDI notes.
- Keep sound selection separate from the authored OSTF notes, harmony, and track metadata wherever possible.

### Drum and Cymbal Playback Improvements

- Differentiate kick, snare, tom, hi-hat, crash, ride, bell, splash, and additional percussion preview sounds.
- Improve the differences among the four kits through synthesized attack, tone, and decay settings.
- Add individual audition options for **Closed / Open / Pedal Hi-Hat, Crash, Ride, Ride Bell, Splash**, and other preview hits.
- Adjust cymbal sustain and resonance so that longer sounds are not reduced to a short click as easily.
- Raise the relative level of cymbals and refine the fallback audio path and simultaneous-sound level handling.
- Integrate the preview sound code and its generated buffers into **one AMXD file**. External drum scripts and samples are not needed.

**Sound-quality limitation:** These are **synthesized preview sounds, not recordings of acoustic drums or cymbals**. Cymbal naturalness, kit balance, and real-host playback still have room for improvement. This is not a replacement for a dedicated sampled drum instrument.

### Retained from Earlier Releases

- OSTF 3.0–4.2 document compatibility and protected preservation
- Vocal Export (SVP / USTX / UFDATA) and vocal-expression inspection
- Configurable Global Timeline, lyric and phonetic views, Piano Roll, and MIDI parameters
- OSTF TEXT, two-file Compare / Visual Merge, MIDI export, and Send to Live

The v2.3 release incorporates the drum and cymbal changes developed through the v2.3.1 RC6 candidate. The **v2.3 version number is reused** for this updated public build; keep a backup of any earlier v2.3 device before replacing it.

---

## What v2.2 Introduced

- **OSTF 4.2 support:** schema-aware reading, OSTF TEXT exchange, and preservation of supported vocal-specific data.
- **Vocal Export:** experimental conversion to **Synthesizer V (`.svp`)**, **OpenUtau (`.ustx`)**, and **UtaFormatix (`.ufdata`)**.
- **Lead and chorus parts:** export an explicitly assigned vocal Voice or recognized lead/harmony melody; supported multi-part exports retain separate vocal parts.
- **Melody without lyrics:** export note pitches and timing with temporary placeholder syllables, without changing the original OSTF document.
- **Global Timeline lanes:** choose which song-information lanes are visible without removing their underlying data.
- **Three lyric views:** distinguish phrase text, pronunciation text, and note-aligned syllables. These are *different views of related OSTF information*, not three independent required lyric tracks.
- **Lyric Phrasing:** clearer syllable placement and timing alongside the piano roll; display authored pronunciation/phonetics when present.
- **Vocal Expression viewer:** inspect supported curves and timed events such as dynamics, breathiness, tension, brightness, voicing, pitch, vocal techniques, breaths, and phonemes.
- **Layout improvements:** resizing of Global Timeline rows and clips, including Scale Contexts, and better handling of melody lanes.
- **Loading feedback:** an indicator during supported file-open and drag-and-drop import workflows.
- **Sound selection (v2.2):** the initial preview-source selector, subsequently simplified and restored to internal GM / drum kits in v2.3.
- **Release cleanup:** consolidated v2.2 version labels and metadata.

The v2.2 release incorporates the stability and UI fixes developed through the v2.2.1 RC5 candidate.

---

## Quick Start

1. Download `OSTF_Editor_v2.3.amxd`.
2. Place it in your preferred Max for Live device folder.
3. Open Ableton Live with Max for Live and load the device onto a compatible track. The current Editor workflow uses an audio-effect device on an audio track.
4. Open the Editor window. Use **Open** to load a `.ostf` file, or **OSTF TEXT** to paste a document.
5. Inspect the Global Timeline, Performance Tracks, Piano Roll, and Parameter area.
6. For comparison, load another document into File A or File B, review differences, and merge supported content.
7. Save the result as an OSTF document. Export MIDI or vocal-software formats separately when needed.

**Important:** `Save`/`Save As`, `Export MIDI File`, and `Vocal Export` are different operations. Vocal export does not replace the original OSTF document.

---

## OSTF Version Compatibility

| OSTF version | Scope in Editor v2.3 |
|---|---|
| 3.0–3.3 | Legacy document compatibility; available operations depend on the document |
| 3.4 | Legacy editing and conservative 3.4-to-3.5 migration |
| 3.5 | Note-state, song/track editing, comparison, and compatible merge workflows |
| 4.0 | Recognition and preservation of extended MIDI events and multiple vocal/melody relationships |
| 4.1 | Schema-aware handling and preservation of Track Directions and compatible song data |
| 4.2 | Schema-aware import and protected preservation of phonetics, Voice Profiles, and Vocal Performances; vocal-software export |

The original OSTF version is retained unless an explicit, supported migration is performed. A newer version does **not** automatically make all older documents editable under that newer schema.

Some OSTF 4.x documents may be protected against editing operations that cannot guarantee preservation of references or newer structures. Full visual authoring and merging of every 4.2 field are **not** included.

---

## OSTF TEXT — View, Copy, Import

Select **OSTF TEXT** in the main toolbar to exchange a complete OSTF document as JSON text.

- **View OSTF:** inspect the current selected document, including its song structure, harmony, tracks, notes, MIDI events, and lyrics.
- **COPY OSTF:** copy the document for use in another compatible OSTF device.
- **IMPORT OSTF:** paste text and validate it before replacing the selected document.
- **File A / File B:** choose the destination or source within the two-document workspace.

Invalid JSON or unsupported structures are rejected instead of silently replacing a valid document. Imported text is **not automatically merged** with the other side.

**Example:** Copy from Composer → import into Editor File A → import an Arranger's OSTF into File B → compare → select supported changes → save the combined song.

---

## Visual Song Editor

### Global Timeline and Configurable Lanes

The Global Timeline displays song-level information against a common musical timeline. Its **Lanes** menu provides visibility checkboxes. Hiding a lane affects only the display, **not** the OSTF data.

Available views include:

- Structure
- Tempo
- Time Signature
- Key Map
- Scale Contexts
- Chords
- Chord Tones
- Voicing Data
- Display Lyrics
- Pronunciation Lyrics
- Vocal Lyrics
- Main Melody / applicable melody lanes

**Chord Tones** represent the tones derived from the chord definition. **Voicing Data** is an optional concrete pitch snapshot associated with a chord; it is not an arrangement note sequence or a command to generate accompaniment.

The three lyric lanes intentionally offer separate perspectives on related song data:

- **Display Lyrics:** phrase-level written lyrics.
- **Pronunciation Lyrics:** authored readings or pronunciation text where provided.
- **Vocal Lyrics:** timed lyric units and syllables associated with melodic notes where alignments are available.

These displays are retained for compatibility and inspection. Their presence does **not** mean any corresponding OSTF field has been deprecated. Hidden or empty lanes do not remove data.

The Global Timeline can be resized; row and clip heights are adjusted within the supported layout. The visibility selection helps keep larger songs readable.

### Performance Tracks

Inspect multiple instrument, bass, drum, melodic, and mixed pitched/percussion parts on a shared timeline. Supported documents provide track selection, inspection, and drag-and-drop reordering.

Track operations and editability depend on the document's version and protected status. Reordering a supported editable document updates the saved OSTF track order.

### Piano Roll and Lyric Phrasing

The Piano Roll shows note pitch, position, length, and supported note attributes for the selected part. Lyric Phrasing presents written syllables in relation to their musical timing and can display note-aligned labels near the notes.

- Authored lyrics, pronunciation, and phonetic information are kept distinct.
- Where available, note/lyric alignments are used rather than guessed.
- Unaligned lyric phrases may be shown separately instead of being attached to the wrong notes.
- Melodies without assigned lyrics remain legitimate melodies and can still participate in vocal export.

### Parameters and Note Data

The Parameter area supports the inspection and, where available, editing of note and MIDI performance properties, including velocity, MIDI CC, Pitch Bend, Channel Aftertouch, Poly Aftertouch, and Program Change.

OSTF note-state attributes include `enabled`, `releaseVelocity`, `probability`, `velocityDeviation`, `pitchRole`, and Phrase Instance `noteStateMode`.

**Fixed triggers:** notes marked `pitchRole = fixedTrigger` are protected against ordinary musical transposition. For example, a +12-semitone transpose may move MIDI 64 to 76 while a keyswitch at MIDI 24 remains unchanged.

---

## Vocal Expression Viewer

OSTF 4.2 can carry optional vocal-specific expression data. In the lower Parameter area, select a vocal expression view to inspect authored information where it exists:

- **Continuous values/curves:** Dynamics, Breathiness, Tension, Brightness, Voicing, and Pitch Offset (cents).
- **Timed events:** Vocal Techniques, Breath Events, and Phoneme Events.

Curves are presented on a time axis; timed techniques, breaths, and phonemes can be shown as event lanes. The UI is deliberately **version-neutral** so that the names remain useful as OSTF evolves.

**Read-only in v2.3:** the viewer does not author or synthesize vocal-expression data. If an older OSTF file has no authored expression information, the Editor reports that no data is available instead of inventing a curve. MIDI Velocity is a separate note parameter and should not be mistaken for Vocal Dynamics.

---

## Vocal Export — Synthesizer V, OpenUtau, UtaFormatix

Vocal Export is available in the right-hand panel, near **Export MIDI File**. It converts selected melodic material to a singing-software interchange file.

### Supported Target Formats

| Target | Output |
|---|---|
| Synthesizer V Studio | `.svp` |
| OpenUtau | `.ustx` |
| UtaFormatix and compatible workflows | `.ufdata` |

### Export Steps

1. Load an OSTF song into File A or File B.
2. In **Vocal Export**, select the document and the appropriate Voice or lead/chorus melody.
3. Choose a target format.
4. Review the export report, including any placeholder-lyrics or unsupported-data warnings.
5. Export the file and open it in the target singing application for inspection.

### Melody and Chorus Handling

An explicit OSTF Vocal Voice with a valid track and lyric alignment is preferred. Recognized lead or other appropriate melody material can also be selected without requiring it to be a general-purpose instrumental arrangement track.

When the target supports multiple parts and the source contains several aligned vocal parts, supported lead and chorus parts can be exported as separate target tracks or parts. The Editor should not silently collapse them into a single melody.

A melody **without assigned lyrics** can be exported with **temporary placeholder syllables** (such as `la`) where required by the destination format. These placeholders are used for conversion only; they are **not written into the source OSTF document**.

### Export Limitations

Vocal export is **experimental**. Exact representation of phonemes, vocal techniques, pitch curves, voice identities, and expression parameters depends on the target format and application. Some fields may need approximation or may not transfer. Review warnings and the imported result.

OSTF Editor does **not** include Synthesizer V, OpenUtau, voicebanks, or a singer license. Opening, singing, and rendering in the target application have not been certified by this project's automated browser tests.

---

## Compare Two OSTF Documents

Load two files into **File A** and **File B** to compare supported material, including:

- Song structure and timeline events
- Chords, keys, and scales
- Melodies and lyric relationships
- Performance and arrangement tracks
- Drum and MIDI note data
- Note states and supported metadata

Review differences before applying changes. Two-file comparison is useful when separate Arranger devices have modified different parts of the same song.

## Visual Merge and Track Organization

Supported merge workflows include selected note ranges, entire tracks, melody regions, drum material, chord voicings, Key Map data, and lyric-linked melody material.

For partial melody replacement, available policies can include:

- **Keep Destination Vocal Lyrics:** retain destination words while changing compatible note content.
- **Notes Only:** replace notes and disconnect incompatible lyric links while retaining lyric text.
- **Adopt Source Vocal Lyrics:** adopt source lyrics and their supported note relationships.

Operations are designed to preserve other song data and reject unsafe partial copies where required. Complex OSTF 4.x references may restrict what can be merged.

**Track reordering:** drag Performance Tracks to reorganize them in supported editable documents. The resulting order is stored when saved.

---

## Harmony, Metadata, and Timing

### Chords and Voicing

Chord labels and optional structured harmonic information are maintained independently of played MIDI notes. Voicing is an optional informational pitch snapshot, useful for inspecting harmonic choices and inversions; it is not a substitute for the concrete performance tracks.

### Standard Key and Genre Metadata

OSTF Editor uses standard Core fields such as `song.key`, `timeline.keyChanges`, `song.scale`, `harmony.scales`, `song.genres`, `song.moods`, and `song.languages`. It avoids treating obsolete application-specific metadata as authoritative when standard fields are available.

### Key Map Merge

A supported Key Map merge can copy the song's initial key and timed key changes without replacing unrelated tracks, chords, tempo, time signatures, lyrics, or arrangement data. PPQ conversion must be exact: positions are not silently rounded.

### High-Resolution Timing and Pickup Notes

Timing-sensitive operations use integer OSTF ticks. Unsupported fractional results are rejected rather than rounded without notice. Valid negative clip-local starts are preserved for pickup notes and related musical structures.

### Conservative Migration

Compatible OSTF 3.4 documents may be explicitly migrated to 3.5. Migration does not invent note-state values, and it can be undone before saving. No automatic forced upgrade to 4.x is performed.

---

## Undo / Redo

Document-level Undo and Redo cover supported editing operations, such as note changes, Visual Merge, melody replacement, Key Map replacement, track reordering, and migration. A logical editing operation is generally grouped into a single history step where supported.

---

## MIDI Export and Send to Ableton Live

**Export MIDI File** saves supported musical note and MIDI-performance information to a Standard MIDI File. MIDI export and OSTF saving serve different purposes: not every OSTF field has an SMF equivalent.

**Send to Live** can send supported note selections, time ranges, entire tracks, or stored chord voicings to a destination MIDI track in Live, with Session or Arrangement clip workflows where supported. Compatible attributes may include probability, velocity deviation, release velocity, and enabled/mute state.

Send to Live does not automatically modify the original OSTF document. For complete song-information preservation, keep the `.ostf` file.

### Internal Sound Source Selection (v2.3)

Use the track's sound/program control to choose an **internal preview instrument**:

- **Pitched tracks:** choose from 128 General MIDI program names. These are preview timbres, not a full sampled GM sound library.
- **Drum and percussion tracks:** choose one of the four built-in drum kits (Electronic, Acoustic-style, Tight, or 808-style). Drum notes use dedicated percussion synthesis and note mapping rather than pitched-instrument transposition.
- **Audition:** use the preview controls to compare drum-kit hits and cymbal types. Longer cymbal sounds are intended to retain audible decay.

The preview engine is entirely contained in the `.amxd` file. The sound choice is meant for **listening while editing**, not rewriting musical data or replacing a DAW's external instrument setup.

**There is no in-Editor VST/AU host per OSTF track.** The previous selector for instruments on other Live tracks has been removed. **Send to Live** remains a separate operation for transferring MIDI notes to compatible destination tracks.

### Drum Preview Audio and Limitations

The Editor uses synthesized drum and cymbal sounds, including distinct treatments for kick, snare, tom, hi-hat, crash, ride, bell, splash, and other percussion events. The four kits change preview timbre, attacks and decay; they do **not** load commercial or recorded sample libraries.

Longer cymbal sustain, improved relative cymbal levels, and revised playback routing are included in v2.3. Nevertheless, acoustic realism remains limited, and Live/Max audio quality must be judged in a real host. The internal preview should not be presented as a fully realistic acoustic drum instrument.

---

## Safe Data Preservation

The Editor prioritizes non-destructive handling and conservative interchange:

- Preserve standard and unfamiliar OSTF fields whenever possible.
- Retain MIDI channels, CC, Program Change, Pitch Bend, and Aftertouch data when supported.
- Preserve multiple melodies, lyric units, Voice references, and note alignments.
- Preserve authored phonetics and Vocal Performance data without silently replacing it.
- Preserve original OSTF versions, exact timing, and unrelated song metadata.
- Do not invent missing musical or vocal content during ordinary file editing.
- Refuse unsafe editing/import operations rather than corrupting the document silently.

**Visibility is not deprecation.** The Editor exposes multiple technical views because different OSTF tools may depend on them. A lane being hidden or unused does not mean its underlying Core field is deprecated. No lyric field is declared deprecated by this README.

---

## Current Limitations

- Complete visual authoring and merging of all OSTF 4.1/4.2 structures are not yet available.
- The Vocal Expression viewer is read-only; editing individual vocal-expression curves and events is a future enhancement.
- Vocal exports to SVP/USTX/UFDATA are experimental and need inspection in the destination application.
- Existing Live MIDI clips are not yet directly captured into a new OSTF Performance Track by the Editor.
- Full cross-track chord/scale/harmony validation remains a future capability.
- Whole-song time insertion/deletion across all related tracks, lyrics, and directions is not yet a completed workflow.
- Independent in-device hosting of a VST/AU for each OSTF track is not implemented; v2.3 uses its internal GM/drum preview instead.
- Built-in drum and cymbal sounds are synthesized previews; their realism and kit-to-kit balance may not match sampled instruments.
- File loading and editor-window startup behavior should be checked in your actual Live/Max environment; browser-level tests do not guarantee host behavior.
- No macOS runtime verification is claimed for this release.

OSTF Editor is **not** an automatic melody, chord-progression, drum, bass, or sequence generator. Those tasks remain the responsibility of the specialized OSTF devices.

---

## Typical OSTF Workflow

1. Build the song structure and harmony with OSTF Composer.
2. Generate or edit appropriate parts in Song Writer and the specialized Arrangers.
3. Load the resulting OSTF documents in Editor through files or OSTF TEXT.
4. Compare File A and File B and review differences.
5. Merge supported tracks or ranges, resolve warnings, and arrange track order.
6. Inspect lyrics, note alignments, MIDI properties, and any authored vocal expression.
7. Save the integrated `.ostf` file.
8. Optionally export `.mid`, `.svp`, `.ustx`, or `.ufdata` as needed.

This is one possible workflow, not a mandatory sequence. The Editor acts as the integration and inspection environment for the complete OSTF song.

---

## Requirements

- Ableton Live with Max for Live (developed primarily around Live 12)
- A compatible `.ostf` file for document-based workflows
- `OSTF_Editor_v2.3.amxd`

This release's audio-effect workflow is intended for use on a compatible audio track. MIDI export and Send to Live are separate features; the device should not be confused with a general multitrack VST instrument host.

---

## Open Song Timeline Format

OSTF is an open, text-based interchange format for structured song information, including song structure, harmony, melodies, lyrics, instrument tracks, MIDI performance, and optional vocal-expression data.

### OSTF 4.2 — Vocal Interchange and Expression

OSTF 4.2 builds on OSTF 4.1 while introducing optional data for singing-synthesis workflows:

- Lyric-unit phonetics, including alternate phoneme representations and pronunciations
- Vocal Voice profiles and their associated melody/lyric relationships
- Vocal Performance data: phoneme events, pitch curves, expression curves, vocal techniques, and breath events
- A structured foundation for external conversion to formats such as Synthesizer V (`.svp`), OpenUtau (`.ustx`), and UtaFormatix (`.ufdata`)

OSTF 4.2 does **not** turn every melody track into a vocal track. Ordinary melodic and instrumental tracks remain valid. The Editor supports 4.2-aware document handling and experimental vocal export, but does not yet provide full visual editing of every 4.2 field.

*Repository URL: to be added once the public OSTF 4.2 repository address is confirmed.*

### OSTF 4.1 — Track Directions

OSTF 4.1 extends OSTF 4.0 with Track Directions and instrument playable-pitch capabilities. Its musical direction data can express performance roles, improvisational intent, and pitch-range guidance without replacing concrete MIDI notes.

GitHub: https://github.com/yoh-nak/Open-Song-Timeline-Format-4.1

### OSTF 4.0 — MIDI Performance and Multiple Vocal Voices

OSTF 4.0 standardizes extended MIDI performance information, including Control Change, Program Change, Pitch Bend, Channel/Poly Pressure, MIDI channel/bus data, and multiple melody tracks with voice-specific lyric relationships.

GitHub: https://github.com/yoh-nak/Open-Song-Timeline-Format-4.0

### OSTF 3.5 — Song and Note-State Interchange

OSTF 3.5 provides structured song and harmony information, multi-track arrangements, lyrics, drum mapping, and note states such as probability, release velocity, and fixed-trigger behavior.

GitHub: https://github.com/yoh-nak/Open-Song-Timeline-Format-3.5

OSTF 4.1 and 4.2 build on the earlier Core model; they do not replace the existing chord, melody, track, and note structures. OSTF Editor may preserve newer fields even when their dedicated visual editing controls are not available.

---

## Version History

### v2.3 — Internal GM / Drum Preview Restoration and Cymbal Update

- Restore built-in 128-program GM preview selection for melodic/instrumental tracks
- Restore Electronic, Acoustic-style, Tight, and 808-style drum-kit selection
- Remove the Live-track external-instrument selection workflow
- Correct routing of recognized drum notes to percussion rather than pitched preview voices
- Improve differentiation of kicks, snares, toms, hi-hats, cymbals and additional percussion
- Add or restore audition controls for open/closed/pedal hats, crash, ride, bell and splash
- Improve cymbal level, sustain, decay, resonance and fallback routing
- Package all preview sounds and drum playback code in a single AMXD with no external JS or WAV requirements
- Retain OSTF 4.2 support, experimental Vocal Export, OSTF TEXT, Compare, Visual Merge and MIDI workflows
- Release v2.3 using the RC6 playback improvements; previous v2.3 builds should be backed up before replacement

**Note:** Cymbals are synthesized and may still sound less natural than recorded samples. Real-host compatibility and audio quality are not certified by structural or browser-based tests.

### v2.2 — Vocal Data, Export and Timeline Update

- OSTF 4.2 schema-aware reading and protected preservation
- Vocal Export to SVP, USTX, and UFDATA
- Recognized lead/chorus material and temporary placeholder lyrics for lyric-free melodies
- Improved written lyrics, pronunciation, phonetics, and note-aligned syllable views
- Vocal Expression curves and timed-event visualization (read-only)
- Configurable Global Timeline lanes, row/clip resizing, and Scale Contexts layout fixes
- Loading feedback for Open and drag-and-drop workflows
- Sound-selection interface and startup/UI stability refinements
- Existing OSTF TEXT, compare/merge, MIDI export, and Send to Live retained

### v2.1 — OSTF TEXT Release

- Added view, copy, and import of OSTF JSON text
- Added File A / File B text exchange and safer invalid-import handling
- Added schema-aware text validation for OSTF 4.0 and 4.1
- Retained visual comparison, merge, and MIDI workflows

### v2.0 — OSTF 4.0 and Editor Workflow Update

- Added extended MIDI event and multiple-melody/vocal recognition
- Improved comparison, Visual Merge, and vocal-link-aware melody replacement
- Improved track reordering, Key Map merge, note-state handling, and timing preservation
- Retained conservative migration, Undo/Redo, and Send to Live

### v1.0 — Initial Public Release

- OSTF 3.0–3.5 compatibility
- Visual two-file comparison and merge
- Note, arrangement, drum, and lyrics-aware editing
- Fixed-trigger and high-resolution timing handling
- Key Map merge, migration, Undo/Redo, and Send to Live

---

## GitHub

OSTF Editor: https://github.com/yoh-nak/OSTF-Editor-M4L

Author: **Yohsuke Nakano**  
https://github.com/yoh-nak

## Support the Project

OSTF Editor and the Open Song Timeline Format projects are developed independently and are available free of charge.

**Buy Me a Coffee:** https://buymeacoffee.com/yohsukenak

Support helps with continued specification work, Max for Live development, compatibility testing, documentation, and future updates.

## License

Refer to the license terms included in the repository. Follow the applicable terms when using, modifying, or redistributing the device.
