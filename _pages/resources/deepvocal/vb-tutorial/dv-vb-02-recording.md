---
title: "DeepVocal Voicebank Creation Tutorial - Recording"
permalink: /resources/deepvocal/vb-tutorial/02/
toc: true
toc_label: "Table of Contents"
toc_icon: cog
toc_sticky: true
classes: none
---

Now is the part of the process where you record the audio files for your voicebank. This process is the same as with UTAU, but often done with other reclists. In fact, you can definitely just use an UTAU voicebank's recordings! This is often done as a test or a port. Just make sure the voicebank is CVVC (or CV, but that sounds worse.)

DeepVocal uses an aliasing system called CVVX (this is what I used when I made [UTAU CVVX](/resources/cvvx-phonemizer/), lol). It is similar to UTAU CVVC, with some slight exceptions (Independent symbols, VC and VV phonemes being treated the same), but UTAU CVVC reclists will work perfectly fine with DeepVocal.

## Choosing a Reclist:
For DeepVocal, you should use either an UTAU CVVC reclist or a DeepVocal reclist. While an UTAU VCV reclist would work, there is no point in wasting time with it, since DV has no support for triphones. I have personally made a [DeepVocal-specific reclist](/resources/ja-cvvx-reclist-dv/), however it is currently still in development. Additionally, DeepVocal does not accept `- C` phonemes (from my testing), so in order to get an acurrate sound you'll need to have `-CV` phonemes (these are treated as normal CV, for some reason). I recommend [Salem Wasteland's JA CVVC 2-Mora reclist](https://utau.felinewasteland.com/jp/cvvc#2) (standard) because it has all phonemes that DeepVocal will use. Also, VV transitions aren't technically necessary, but I recommend them because they make the voicebank sound much smoother and more realistic. 

While CV DeepVocal is possible, I do not recommend it because it sounds unatural and choppy in the same way as UTAU CV does. Additionally, there is no overlap value in the phonemes so it sounds even stranger than UTAU.

## Recording with Recstar

Since I'll assume you're using one of the the above-linked reclists, this will be specific to those. For other reclists, you'll have to do your own research. This section is more spotty than the other sections, since I don't especially want to spend my time describing a process that is often used for UTAU recording as well and is very well documented. If you need help with this section, please look it up online and you will most likely find the answers you need.

### Setup

1. To start, click the `+` button in the lower right to make a new session
2. If this is your first time recording with this reclist, select the kebab menu in the upper right, then select "Import," then select the text file that you downloaded with the reclist.
3. When it promps you and asks if you want to import a comment file, click no (unless you're using a reclist that needs it).

### Recording

1. By default, when you press and hold the space bar, RecStar will start recording. Generally this is fine, (it's the method that I use), but you can experiment with the recording settings if you'd like.
2. When recording, try to hold out each beat for around a second. Don't use vibrato, and leave around a second of silence at the start and end of the audio files. Try to keep the different recordings close to the same pitch as each other.
3. Move to the next audio file (by pressing the down arrow on your keyboard or the right arrow in the UI)
4. Repeat this process until you reach the end of the reclist

## File Preparation

Here is the process I go through to process audio files so that they're ready to use

1. Make a new folder (named the name of your voicebank, ex. `suigin-koora-deepvocal-v1`) somewhere memorable, such as the desktop. This will act as the voicebank folder. I have a folder of all of my voicebanks in my Music folder, but the desktop will work as well. Inside of that, make a folder named "recordings" (this tutorial will only be for monopitch voicebanks. voicebanks with multiple pitches will have subfolders in here), as well as a folder named "logs".
2. ***COPY*** the `.wav` files from the "session" folder (`C:\Users\[User]\RecStar\sessions\[reclist name][date and time]`) to the recordings folder in your voicebank folder. Copy them so that if something messes up with the noise removal you have a backup. please copy them. i beg you.
3. Normalize the volume levels in the files. I use Audacity for this, but I am sure there is a better way to do this (I just don't know of any). Select all of the audio files in the recordings folder and drag them into Audacity. **Audacity will take a long time to load them**, it is fine, be patient. If it says that it stops responding, make Winwos wait for it to finish loading. Once it loads, press `ctrl + a` to select all of the audio, then (in the upper bar) select "Effect" > "Volume and Compression" > "Normalize...". Leave everything at default, but set the peak amplitude to something between -2 and -4 dB. I personally do -2 dB, but it doesn't matter too much. Then click "Apply". Once thats done, go to "File" > "Export Audio". In the window that shows up, set the audio options to be "Mono", "44100 Hz", and "Signed 16-Bit PCM". Set the export range to be "Multiple Files", split files based on tracks, select the file naming option "Using Label/Track Name", and make sure to check "Overwrite existing files". then click export! You can then close Audacity and there's no need to save the project.
4. Optionally, use [UtaUtaUtau's `threaded_noise_remove.exe`](https://github.com/UtaUtaUtau/nnsvslabeling/releases/tag/builds) to remove background noise by dragging the folder with all of the `.wav` folders onto the `.exe`. That should be it, not sure exactly. I always run the Python version, but it's a little bit more complicated (there are more-detailed directions on the GitHub page).
5. You're done!

Next Step: 
[Configuring and Building](/resources/deepvocal/vb-tutorial/03/){: .btn .btn--primary}
