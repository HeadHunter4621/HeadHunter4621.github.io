---
title: "DeepVocal Voicebank Creation Tutorial - Configuration & Building"
permalink: /resources/deepvocal/vb-tutorial/03/
toc: true
toc_label: "Table of Contents"
toc_icon: cog
toc_sticky: true
classes: none
---

This is where DeepVocal differs from UTAU the most, in my opinion. This is a very involved process, so it will be multiple parts.

## Getting Started with DVTB

Fistly, you have to open DeepVocal ToolBox. Just open the exe or desktop shortcut. It will be a hilariously small window, jsust a bar with some menu items.

To create the voicebank file, select "File" > "New", then "File" > "Save As". Then select your voicebank folder. This will create a `.dvtb` file, which is where information about the voicebank is stored.

## Phonetic Dictionary

This part of DeepVocal is maybe my favorite. Basically, DV uses a weird CVVC-based phonemizer thing which reads from a voicebank's phonetic dictionary to determine what VX phonemes match to which CV phonemes. The process of making them is very time-consuming, so I will explain all of the pages. (You may need to use the arrows in the upper right to be able to see all of the pages)

To show the phonetic dictionary window, select "Function" > "Phonetic Dictionary"

*My custom Japanese phonetic dictionary has all of these sections prepared already. To use it, copy the text from the applicable section of the file and paste it into the correct text boxes. It will also be at the bottom of this page*

### 1: Symbol List

This is the part that takes the longest. It is where you need to enter every CV pair (or vowel) in a voicebank.

Text is entered into the text box like this:

```
[Phoneme 1],[(Starting) Consonant],[(Ending) vowel]
[Phoneme 2],[(Starting) Consonant],[(Ending) vowel]
[...]
```

For most phonemes, this is very simple, such as `ka,k,a` and `so,s,o`. Sometimes, this varies. For example, I recomend that `ki` is treated as having a `ky` consonant, so its like would be `ki,ky,i`. For phonemes such as `kyo`, the lines look like `kyo,ky,o`. Additionally, you'll need to make lines for vowels. These will just look like `a,a,a`. Syllabic `N` is always written with a capital N, that way it is differentiated from consonant `n`.

You have to do every phoneme. It is very annoying, I know.

If you use my custom dictionary, scroll to the last section (labeled "Symbol List") and copy the lines and paste them into the box.

### 2: Vowel list

This is the list of phonemes that DeepVocal's editor knows that it can stretch along a note. This includes all 5 Japanese vowels, as well as syllabic `N`. The file is formatted like this:

```
[Vowel 1],[Vowel 1]
[Vowel 2],[Vowel 2]
[...]
```

For Japanese, it should always look like this (unless you have some weird stuff going on):

```
a,a
i,i
u,u
e,e
o,o
N,N
```

I don't know why there needs to be the comma and second vowel. My best guess is that it has to do with diphthongs, but that doesn't apply in Japanese

### 3: Voiced Consonant List

The title of this section is misleading. It is not for every voiced consonant, just the ones that hold a pitch while being spoken (remember, in Japanese this includes `cy` consonants). In Japanese, these are the phonemes in this list:
`z`, `j`, `n`, `ny`, `m`, `my`, `y`, `w`, and `v`.
depending on pronunciation, some of these (most often `r` and `ry`) may need to be removed. To do this, just remove their lines from this and add them to "4 Unvoiced Consonant List". In the engine, the consonants in this list have pitch-shifting applied in the same way as vowels.

This file is structured like this (very simple):

```
[Consonant 1]
[Consonant 2]
[...]
```

### 4: Unvoiced Consonant List

This file is the same as the voiced consonants list, except it's every consonant not in the voiced consonants list. These consonants are interpreted the same as voiced consonants in the engine, but no pitch shifting is applied to them. It's formatted the same as well:

```
[Consonant 1]
[Consonant 2]
[...]
```

Once you're done assembling lists 1 through 4, press the "Check Dictionary" button to see if it finds any errors. If it does, correct them.

### 5: Independent Symbol List (Optional)

This is pretty much the same as the consonant lists, but for standalone phonemes such as breaths. Call them whatever you want (the most common thing for breaths is `br1`, `br2`, etc). These phonemes are not pitched by the engine and are not needed, but cna be heplful.

### 6: Tail Symbol List (Optional)

These are symbols that can be at the end of phonemes. While I do not know how exactly to use them, I know that this file is formatted the same as the consonant and independent files. This is used for the list of things such as ending breaths and vocal fry.

From what I can tell, DeepVocal has one of these by default, `-`. You don't need to add it here. It is automatically placed at the end of notes that are at the end of a phrase. As with theindependent symbol list, you don't actually need to add anything here unless your reclist has phonemes for it.

Once you're done making the dictionary, make sure to run the check one last time and fix any errors. If it works, it will say "OK! Pass!" which I find very funny. You can now close the phonetic dictionary window, and make sure to save the voicebank!

## Configuration

To open the voicebank configuration menu in DVTB, go to "Function" > "Build Voice Config". This will open another window which is where DVTB will show you all of the "markers" (for UTAU, these are OTO lines) and information about them. I also recommend having a file explorer window open so that you can view the voicebank's audio files, which will come in handy soon (this isn't part of DVTB, it's just helpfil).

### Config Setup

The first thing to do is select "Wav Location" and select the "recordings" folder that we made earlier. This tells DVTB what directory to look in. Doing this also makes a `voice.dvcfg` file, which is pretty much what `oto.ini` is in UTAU. 

Once you have the directory set correctly, it's time to actually start configuring. In the file explorer window, sort the files by name, then take the first name of the first one and type it into the "Wav File Name" box of DVTB. Technically you don't need to do these in any fixed order, I just recommend going alphabetically because it makes it the easiest to pick up where you left off. In the "Pitch" box, enter the pitch of the recording. Ideally, you recorded at exactly this pitch throughout all of every sample, but that isn't humanely possible. As long as it's relatively accurate, you're fine. To my knowledge, this only really effects multi-pitch voicebanks. 

Here's how I like to have my windows arranged:
![image-right](/assets/images/resources/deepvocal/dvtb-organization.png){: .align-center}

### Markers!

Once you've selected the right file and entered the pitch correctly, it's time to start making the markers! These are analogous to lines in an `oto.ini` file, but a bit different to interact with. The first thing you need to do is determine the type of marker that's at the start of the audio file. Technically the order doesn't matter, but doing it in order makes it a bit simpler in my opinion.

Below is a list of the types of phonemes in DeepVocal, as well as what they do and how to configure them.

* CV - Same as UTAU, these are V and CV phonemes as well as -V and -CV (V/CV phonemes that start with silence) (ex. `-a`, `-se`, etc.), which are automatically replaced (from the non-silence versions) by DeepVocal and technically optional. These are configured the same as in UTAU, with some slight differences. To configure them, make sure that the type is set to "CV" and the text in the box is the CV phoneme. Select "New markers" to start placing the markers!

* VX - In CVVC UTAU, these are VC, VV, and V- phonemes. They are also the tail symbols we added to the dictionary earlier, which start with vowels. While they're configured very similarly to UTAU ones, DeepVocal is actually made for this type of phoneme (whereas UTAU is technically just made for CV), so it won't try to stretch them at all! To configure them, make sure that the type is set to "VX" and the text in the "V" box is the starting vowel and the text in the "X" box is whatever comes next. Select "New markers" to start placing the markers!

* Independent (sometimes shortened to "Indie") - This has the same interface as the VX phonemes, but aren't connected to any other phonemes. To configure them, make sure that the type is set to "Independent" and the text in the box is the name of the independent phoneme as listed in the phonetic dictionary. Select "New markers" to start placing the markers!

By default, the marker editor is very small. I recommend making it wider, but you do you. To zoom in on a sample, you can use the yellow things on th sides of the top bar of the editor to change what section of the sample can be viewed.

To move markers, you can either drag them (which can *only* be done by the little labels) or click on where you want them to go (to place the playhead there) and then pres the corresponding number on your keyboard (either 1-2 or 1-4). I prefer the second option because it's faster. After you move the markers to the correct places (I have explanations below of how they're supposed to be arranged, as well as examples), press the red checkmark button to save the sample. If there is an error (for example, the markers are in the wrong order), it will show you the error and you'll have to correct it. Once you save a phoneme, don't close the window; instead, scoll (by moving the upper yelow rectangle thing) to generally contain the place where the next phoneme will be, then enter the parameters for the next phoneme and make the markers. DVTB will keep the window in place and place the markers within it. Of course, the markers will need to move still, but it's incredibly helpfl to start with them in roughly the right place, *especially* for voicebanks with longer samples. 

You'll need to place each phoneme in the voicebank individually. Ideally, every voicebank provider will make some sort of description of which phonemes each recording contains, but that often isn't the case. Later in the process (when building), it'll tell you if any are missing which is handy (though sometimes it's a bit strange; I'll get into that later as well)

As you can see, DVTB makes an **astonishing** amount of noises. When you drag the markers, it loops a *very small* section of the audio to show you what phoneme is playing, which is very handy in case you lose your place in a sample and need to know what vowel it is. You can also move the playhead and then press the space bar to play the audio file. Also, when making and saving markers it plays noises too. How fun!

#### Marker Types

There are 6 types of markers in DeepVocal: CP, PP, VSP, VEP, SP, and EP. CV phonemes have the first 4 and VX phonemes have the last 2. 

For CV phonemes, the phonemes align to an OTO's parameters like this (not quite the same, but very similar). 

* `CP` (Offset): This stands for "Consonant Point." You place this at the very start of the consonant for stops all consonants. If it is a `-CV` phoneme, this goes right when any the sound starts.

* `PP` (Preutterance): This stands for "Preutterance Point." It goes right at the start of the vowel sound. For phonemes like `kya`, it goes **before** the `y` sound.

* `VSP` (Fixed): This stands for "Vowel Start Point." It goes at the point where the vowel is stable, marking the start of the part of the phoneme that is stretched.

* `VEP` (Cutoff): This stands for "Vowel End Point." It's the end of the part that's stretched and the end of the sample.

For VX and Independent phonemes, there are only 2 types of marker, and in my opinion they're so much simpler

* `SP`: This stands for "Start Point." It marks the start of the VX/Independent phoneme. For VX phonemes, this is placed at the point of the vowel where it is no longer stable. For independent phonemes, this is at the start of the sound.

* `EP`: This stands for "End Point." It marks the end of the VX/Independent phoneme and goes at the very start of the next phoneme. For stop consonants such as `k`, this is as soon as the silence starts. For fricatives/voiced phonemes, this is immediately at the point where the consonant sound is stable (generally right when the vowel ends). For VV phonemes, this is imediately when the sound becomes the next vowel, though I may be doing this wrong (the timing for my VV phonemes is always a bit messed up).

### Configuration Examples

#### CV

`-a`:
![image-center](/assets/images/resources/deepvocal/example_-a.png){: .align-center}

`a`:
![image-center](/assets/images/resources/deepvocal/example_a.png){: .align-center}

`-se`:
![image-center](/assets/images/resources/deepvocal/example_-se.png){: .align-center}

`-pyu`:
![image-center](/assets/images/resources/deepvocal/example_-pyu.png){: .align-center}

`to`:
![image-center](/assets/images/resources/deepvocal/example_to.png){: .align-center}

`ka`:
![image-center](/assets/images/resources/deepvocal/example_ka.png){: .align-center}

`nu`:
![image-center](/assets/images/resources/deepvocal/example_nu.png){: .align-center}

#### VX

`a_i`:
![image-center](/assets/images/resources/deepvocal/example_a_i.png){: .align-center}

`u_k`:
![image-center](/assets/images/resources/deepvocal/example_u_k.png){: .align-center}

`e_m`:
![image-center](/assets/images/resources/deepvocal/example_e_m.png){: .align-center}

`N_k`:
![image-center](/assets/images/resources/deepvocal/example_n_k.png){: .align-center}

`N_sh`:
![image-center](/assets/images/resources/deepvocal/example_n_sh.png){: .align-center}

`a_Fr` (Tail):
![image-center](/assets/images/resources/deepvocal/example_a_fr.png){: .align-center}

`o_-` (Tail): note to self: add this screenshot
![image-center](/assets/images/resources/deepvocal/example_o_-.png){: .align-center}

#### Other

`Ex` (Independent, Exhale) (breaths are very quiet):
![image-center](/assets/images/resources/deepvocal/example_ex.png){: .align-center}


## ***BETA*** Japanese Phonetic Dictionary for my [DeepVocal JA CVVX reclist](/resources/ja-cvvx-reclist-dv/)

(This is at the bottom of the page because it's very long)

Since this is in beta, it may not function properly. Please reach out to me for help if needed.

(Last updated: `3-16-2026`)

### 1: Symbol List

```
a,a,a
i,i,i
u,u,u
e,e,e
o,o,o
N,N,N
'a,',a
'i,',i
'u,',u
'e,',e
'o,',o
'N,',N
ka,k,a
ki,ky,i
ku,k,u
ke,k,e
ko,k,o
kya,ky,a
kyu,ky,u
kye,ky,e
kyo,kyo
ga,g,a
gi,gy,i
gu,g,u
ge,g,e
go,g,o
gya,gy,a
gyu,gy,u
gye,gy,e
gyo,gy,o
sa,s,a
si,s,i
su,s,u
se,s,e
so,s,o
sha,sh,a
shi,sh,i
shu,sh,u
she,sh,e
sho,sh,o
za,z,a
zi,z,i
zu,z,u
ze,z,e
zo,z,o
ja,j,a
ji,j,i
ju,j,u
je,j,e
jo,j,o
ta,t,a
ti,t,i
tu,t,u
te,t,e
to,t,o
tsa,ts,a
tsi,ts,i
tsu,ts,u
tse,ts,e
tso,ts,o
cha,ch,a
chi,ch,i
chu,ch,u
che,ch,e
cho,ch,o
da,d,a
di,d,i
du,d,u
de,d,e
do,d,o
dza,dz,a
dzi,dz,i
dzu,dz,u
dze,dz,e
dzo,dz,o
dja,dj,a
dji,dj,i
dju,dj,u
dje,dj,e
djo,dj,o
na,n,a
ni,ny,i
nu,n,u
ne,n,e
no,n,o
nya,ny,a
nyu,ny,u
nye,ny,e
ha,h,a
hi,hy,i
hu,h,u
he,h,e
ho,h,o
hya,hy,a
hyu,hy,u
hye,hy,e
hyo,hy,o
ba,b,a
bi,by,i
bu,b,u
be,b,e
bo,b,o
bya,by,a
byu,by,u
bye,by,e
byo,by,o
pa,p,a
pi,py,i
pu,p,u
pe,p,e
po,p,o
pya,py,a
pyu,py,u
pye,py,e
pyo,py,o
fu,f,u
ma,m,a
mi,my,i
mu,m,u
me,m,e
mo,m,o
mya,my,a
myu,my,u
mye,my,e
myo,my,o
ya,y,a
yu,y,u
ye,y,e
yo,y,o
ra,r,a
ri,ry,i
ru,r,u
re,r,e
ro,r,o
rya,ry,a
ryu,ry,u
rye,ry,e
ryo,ry,o
wa,w,a
wi,w,i
we,w,e
wo,w,o
va,v,a
vi,v,i
vu,v,u
ve,v,e
vo,v,o
```

### 2: Vowel List

```
a,a
i,i
u,u
e,e
o,o
N,N
```

### 3: Voiced Consonant List

```
z
j
n
m
y
v
w
```

### 4: Unvoiced Consonant List

```
k
ky
g
gy
s
sh
t
ch
ts
h
hy
f
b
by
p
py
r
ry
```

### 5: Independent Symbol List

```
In
Ex
```

### 6: Tail Symbol List

```
Fr
```
