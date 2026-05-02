---
title: "DeepVocal Voicebank Creation Tutorial - Creating a Singer Dictionary"
permalink: /resources/deepvocal/vb-tutorial/05/
toc: true
toc_label: "Table of Contents"
toc_icon: cog
toc_sticky: true
classes: none
---

This is different from the phonetic dictionary. It lets you convert the symbols you input into a note to multiple (or other) notes with different phonemes. For Japanese, this is typically used to convert kana to romaji, whereas for some languages, they get a lot more complicated.

***Note: These dictionaries are optional! If not used, just type in romaji.***

A lot of the information on this page is taken from the [DeepVocal Wikia](https://deepvocal.fandom.com/wiki/Dictionary).

There are 2 ways to make DeepVocal singer dictionaries. In the wikia, they're referred to as "Format 1" and "Format 2," but I will refer to them as "INI-Style" and "JSON-Style" because of the filetypes that I think they most directly resemble. I recommend INI-Style because it is much simpler to set up.

# INI-Style

## File creation

This is the simpler type of dictionary. To make it, create a UTF-8-formatted text file (if you don't know what UTF-8 is, it should be the default) inside of the voicebank folder alongside `SKC`, `SKI`, and `voice.sksd`. Name it `[something]-dict.txt` (the "something" can be whatever you want, often the singer name (ex. `suigin-koora-dict.txt`)). Open the file in a text editor (I recommend Notepad++, but the Windows text editor works fine as well).

## Phrase entry

I call this file "ini-style" because of how the file is formatted. Each line will contain an equal-sign and text on either side. the left side is a "key" and the right is a "value." When using the DeepVocal editor, if you enter the key into a note, the note is replaced with note/notes that match the text in the value. A simple example line would be `か=ka`, so when you type `か` into a note, it replaces it with romaji `ka` (it shows the romaji alongside the kana). Additionally, if you are converting a note into multiple notes (for example, `naka` turns into notes `na` and `ka`), the value is separated by spaces (ex. `naka=na ka`). 

The values can also reference other keys if they are made before them. For example, if the first line was `な=na` and the second was `か=ka` and the third line was `中=なか`, the DeepVocal Editor would convert `中` into the notes `な` and `か`, which would then be converted into `na` and `ka`. Here's the example in the wikia, which has an English word:

```
per=pe R
person=per so n
```

## Saving

Simply save the text file, and restart the DeepVocal Editor if it's open.

# JSON-Style

This is the more complicated style of dictionary, which I don't recommend. You can look at [this page](https://deepvocal.fandom.com/wiki/Dictionary) on the DeepVocal Wikia to learn how to make it, but I really do not recommend it.

# Free-To-Use Dictionary File

Here is a dictionary that you are free to use for your voicebanks. It is meant to be used with my style (where syllabic ん is written as N), but it can be edited. Follow creations steps for the INI-Style dictionary and paste this text into the text file.

```
あ=a
い=i
う=u
え=e
お=o
か=ka
き=ki
く=ku
け=ke
こ=ko
さ=sa
すぃ=si
す=su
せ=se
そ=so
た=ta
てぃ=ti
とぅ=tu
て=te
と=to
な=na
に=ni
ぬ=nu
ね=ne
の=no
は=ha
ひ=hi
ふ=fu
へ=he
ほ=ho
ま=ma
み=mi
む=mu
め=me
も=mo
や=ya
ゆ=yu
いぇ=ye
よ=yo
ら=ra
り=ri
る=ru
れ=re
ろ=ro
わ=wa
うぃ=wi
うぇ=we
うぉ=wo
を=o
が=ga
ぎ=gi
ぐ=gu
げ=ge
ご=go
ざ=za
ずぃ=zi
ず=zu
ぜ=ze
ぞ=zo
だ=da
でぃ=di
どぅ=du
で=de
ど=do
ば=ba
び=bi
ぶ=bu
べ=be
ぼ=bo
ぱ=pa
ぴ=pi
ぷ=pu
ぺ=pe
ぽ=po
きゃ=kya
きゅ=kyu
きぇ=kye
きょ=kyo
しゃ=sha
し=shi
しゅ=shu
しぇ=she
しょ=sho
ちゃ=cha
ち=chi
ちゅ=chu
ちぇ=che
ちょ=cho
つぁ=tsa
つぃ=tsi
つ=tsu
つぇ=tse
つぉ=tso
にゃ=nya
にゅ=nyu
にぇ=nye
にょ=nyo
ひゃ=hya
ひゅ=hyu
ひぇ=hye
ひょ=hyo
ふぁ=fa
ふぃ=fi
ふぇ=fe
ふぉ=fo
みゃ=mya
みゅ=myu
みぇ=mye
みょ=myo
りゃ=rya
りゅ=ryu
りぇ=rye
りょ=ryo
ぎゃ=gya
ぎゅ=gyu
ぎぇ=gye
ぎょ=gyo
じゃ=ja
じ=ji
じゅ=ju
じぇ=je
じょ=jo
びゃ=bya
びゅ=byu
びぇ=bye
びょ=byo
ぴゃ=pya
ぴゅ=pyu
ぴぇ=pye
ぴょ=pyo
ん=N
ヴぁ=va
ヴぃ=vi
ヴ=vu
ヴぇ=ve
ヴぉ=vo
ラ=la
リ=li
ル=lu
レ=le
ロ=lo
リャ=lya
リュ=lyu
リェ=lye
リョ=lyo
```
