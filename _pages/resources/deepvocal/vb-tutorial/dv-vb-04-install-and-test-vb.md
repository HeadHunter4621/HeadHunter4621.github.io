---
title: "DeepVocal Voicebank Creation Tutorial - Installing and Testing Your Voicebank"
permalink: /resources/deepvocal/vb-tutorial/04/
toc: true
toc_label: "Table of Contents"
toc_icon: cog
toc_sticky: true
classes: none
---

## Installation

This part isn't too complicated! Simply copy the packaged voicebank (the folder that contains `SKC`, `SKI`, and `voice.sksd`) into the editor's `singers` folder. This path will be `C:\Program Files (x86)\DeepVocal\singers`, unless you changed the installation path while you were instaling the DeepVocal editor. Since the `Program Files (x86)` folder is protexted by Windows, you'll need to allow the files to move there (this doesn't take long because there are only a few of them). You're now done installing the voicebank! If the editor is open, make sure to restart it.

## Testing

In order to test your voicebank, you're going to need to make or open a `.dv` sequence file. These act the same as an UTAU `.ust`, OpenUtau `.ustx`, or `.mid` file and contain timing, note, lyric, and track data for a song.

The easiest way to to this would be to find a `.dv` file online, but these are very uncommon. Instead, I've provided this one for you! Before using it, make sure to right-click the track at the top and set the singer to the one you just made.

[kaeru-no-gasshou.dv](https://drive.google.com/file/d/11Nk6i97rPWWlXgYOB2V25UzRMYCNeEQz/view?usp=sharing){: .btn .btn--inverse}

If you're converting from a UST or something, I recommend using [UtaFormatix](https://sdercolin.github.io/utaformatix3/). Drag the sequence file you have, then scroll *nearly* to the bottom of the "Select Output Format" page. Select `Dv`. It will now show you a window where you can convert a bunch of parameters. Since your singer doesn't have a singer dictionary (which is different than the phonetic dictionary, which you can learn about on the next page of the tutorial), make sure that (under "Cleanup and convert lyrics) the target lyrics type is Romaji CV. Make sure that "Convert lurics in Chinere [...]" is off, since this is a Japanese voicebank. Under "Replace Lurics", add anotehr replacement rule. Set the "filter type" to "exact", then the "filter" to "n", "match type"s to "All", and "to" to "N". This will convert the romaji syllabic `n` to `N`, the same way it is in the voicebank. Leave all other settings at default, but turn off :Convert Pitch Parameters". You can experiment with this on your own, but the way DeepVocal handles pitch is quite different from UTAU, so be warned that it may sound weird. Click "NEXT" and then download the sequence.

When you re-open the DeepVocal editor, it will most likely be in chinese again. I don't remember *how* I did it, but on my computer it is in English by default. If I figure out how I did this, I will add it here. To change the language, select the third option from the left (in the top bar) ("首選項"), then the bottom one (in the dropdown) ("語言設定(language)"). Then, select English from the dropdoan menu, then press the left button ("確定") to save your changes. To open a sequence, go to "File" > "Open File", then select the `.dv` file thar you want to open. Before playing, make sure to select then right-click the green track with the notes on it and set the singer to the one that you just made, then press play! You should hear your voicebank's first words!

Thank you for following my tutorial! The rest of this process is optional, so if you're happy with how your singer is you can stop here and make songs!

Next Step (Optional): 
[Creating a Dictioanry File](/resources/deepvocal/vb-tutorial/05/){: .btn .btn--primary}
