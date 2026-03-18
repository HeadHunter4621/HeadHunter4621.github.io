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

This part isn't too complicated! Simply drag the packaged voicebank (the folder that ocntains `SKC`, `SKI`, and `voice.sksd`) into the editor's `singers` folder. If you didn';'t change the installation path of the DeepVocal Editor, that will be `C:\Program Files (x86)\DeepVocal\singers`. You're done installing the voicebank!

## Testing

In order to test your voicebank, you're going to need to make or open a `.dv` sequence file. These act the same as an UTAU `.ust`, OpenUtau `.ustx`, or `.mid` file and contain timing, note, lyric, and track data for a song.

The easiest way to to this would be to find a `.dv` file online, but these are very uncommon. Instead, I've provided this one for you!

[kaeru-no-gasshou.dv](https://drive.google.com/file/d/11Nk6i97rPWWlXgYOB2V25UzRMYCNeEQz/view?usp=sharing){: .btn .btn--inverse}

If you're converting from a UST or something, I recommend using [UtaFormatix](https://sdercolin.github.io/utaformatix3/). Drag the sequence file you have, then scroll *nearly* to the bottom of the "Select Output Format" page. Select `Dv`. It will now show you a window where you can convert a bunch of parameters. Since your singer doesn't have a singer dictionary (which is different than the phonetic dictionary, which you can learn about on the next page of the tutorial), make sure that (under "Cleanup and convert lyrics) the target lyrics type is Romaji CV. Make sure that "Convert lurics in Chinere [...]" is off, since this is a Japanese voicebank. Under "Replace Lurics", add anotehr replacement rule. Set the "filter type" to "exact", then the "filter" to "n", "match type"s to "All", and "to" to "N". This will convert the romaji syllabic `n` to `N`, the same way it is in the voicebank. Leave all other settings at default, but turn off :Convert Pitch Parameters". You can experiment with this on your own, but the way DeepVocal handles pitch is quite different from UTAU, so be warned that it may sound weird. Click "NEXT" and then download the sequence.

[making your own test]

[provide my own test (kaeru no gasshou)]

[Opening sequence (talk about language setting again)]

[Play!]



Next Step (Optional): 
[Creating a Dictioanru File](/resources/deepvocal/vb-tutorial/04/){: .btn .btn--primary}
