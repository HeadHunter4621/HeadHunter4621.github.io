---
title: "DeepVocal Voicebank Creation Tutorial - Configuration & Building"
permalink: /resources/deepvocal/vb-tutorial/03/
toc: true
toc_label: "Voicebank Configuration and Building"
toc_icon: "cog"
---

This is where DeepVocal differs from UTAU the most, in my opinion. This is a very involved process, so it will be multiple parts.

## Getting Started with DVTB

Fistly, you have to open DeepVocal ToolBox. Just open the exe or desktop shortcut. It will be a hilariously small window, jsust a bar with some menu items.

To create the voicebank file, select "File" > "New", then "File" > "Save As". Then select your voicebank folder. This will create a `.dvtb` folder, which is where information about the voicebank is stored.

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

For most phonemes, this is very simple, such as `ka,k,a` and `so,s,o`. Sometimes, this varies. For example, I recomend that `ki` is treated as having a `ky` consonant, so its like would be `ki,ky,i`. For phonemes such as `kyo`, the lines look like `kyo,ky,o`. Additionally, you'll need to make lines for vowels. These will just liik like `a,a,a`. Syllabic `N` is always written with a capital N, that way it is differentiated from consonant `n`.

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

### 5: Independent Symbol List

This is pretty much the same as the consonant lists, but for standalone phonemes such as breaths. Call them whatever you want (the most common thing for breaths is `br1`, `br2`, etc). These phonemes are not pitched by the engine.

### 6: Tail Symbol List

These are symbols that can be at the end of phonemes. While I do not know how exactly to use them, I know that this file is formatted the same as the consonant and independent files. This is used for the list of things such as ending breaths and vocal fry.

From what I can tell, DeepVocal has one of these by default, `-`. You don't need to add it here. It is automatically placed at the end of notes that are at the end of a phrase.

Once you're done making the dictionary, make sure to run the check one last time and fix any errors. If it works, it will say "OK! Pass!" which I find very funny.



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
