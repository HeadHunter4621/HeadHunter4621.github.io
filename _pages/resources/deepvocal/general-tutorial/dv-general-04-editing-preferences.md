---
title: "DeepVocal Editor Tutorial - Editing Preferences"
permalink: /resources/deepvocal/dv-tutorial/04/
toc: false
toc_icon: cog
toc_sticky: true
classes: wide
---

Since my website needs me to disable the table of contents to have a wide page, I've separated this page from the usage page.

Here's a table of the settings that can be edited through the GUI.

| Setting | File to Edit | Key(s) | Explanation | Possible Values | Recommendation |
| :-- | :-- | :-- | :-- | :-- | :-- |
| **Default** Vibrato | `app.cfg` | `"vibPercent"`, `"vibPreins"` | Default vibrato values | Unknown | Leave at Default |
| **Custom** Vibrato | `vib.cfg` | Unknown | Custom vibrato values. For these I recommend running as admin and using the GUI. | I recommend running as admin and using the GUI for these | Leave at Default |
| **Default** Portamento | `app.cfg` | `"expBendDep"`, `"expBendLen"`, `"expHeadChg"`, `"expTailChg"` | Edges of notes, default | Each can be an integer | `0`, `5`, `16`, `16` |
| **Custom** Portamento | `exp.cfg` | Unknown | Edges of notes | I recommend running as admin and using the GUI for these | Set `"expBendDep"` to `0` and leave the rest at default |
| Default Symbol | `app.cfg` | `"defaultSymbol"` | The default lyric when placing notes | Any string (with quotes aroud it), no spaces or special characters | `"ta"` |
| Auto Backup | `app.cfg` | `"useAutoBackup"` | Toggle for automatic backup | `true` or `false` | `true` |
| Gridline | `app.cfg` | `"showGridLine"` | Whether or not to show grid lines in the editor | `true` or `false` | `true` |
| Playhead Return | `app.cfg` | `"backToStartAfterPlay"` | Whether or not to return to the playhead to where you started playing once you stop. | `true` or `false` | `false` |
| Language | `app.cfg` | `"langFilePath"` | Language in editor | Path to the text files in `[install directory]\DeepVocal\language` | `"C:\\Program Files (x86)\\DeepVocal\\language\\English.txt"` |
	
There are also some settings that aren't editable in the GUI:

| Setting | File to Edit | Key(s) | Explanation | Possible Values | Recommendation |
| :-- | :-- | :-- | :---- | :-- | :-- |
| Auto-Backup Interval | `app.cfg` | `"autoBackupMinute"` | Interval for saving backup file in minutes | Any integer | `1` |
| Auto-Apply Vibrato | `app.cfg` | `"isAutoVib"` | Automatically apply vibrato to notes | `true`, `false` | `false` |
| Default Singer | `app.cfg` | `"singerName"` | Default voicebank for new tracks | Name of an installed singer | N/A |

I recommend using Notepad++ to edit these files and (if you like) setting the language to `JSON` so that there is color theming and logic.
