---
title: "DeepVocal Editor Tutorial - Installing the Editor"
permalink: /resources/deepvocal/dv-tutorial/01/
toc: true
toc_label: "Table of Contents"
toc_icon: cog
toc_sticky: true
classes: none
---

Installing the DeepVocal editor is pretty easy, but I'm documenting it anyway in case anyone needs help! The installer for DeepVocal can be found on [DeepVocal's homepage](https://www.deep-vocal.com/#/) (make sure to download the editor and not the toolbox).

## DeepVocal Installation

1. Select "Download" from the website's homepage, then click the download button under "DeepVocal Editor"
2. Extract `Setup_DeepVocal_beta_2.1.0.zip` and run `Setup_DeepVocal_beta_2.1.0.exe`
3. Follow the installer's directions. This tutorial assumes that it is installed in the default location (`C:\Program Files (x86)\DeepVocal`), but if needed you can change it. I would recommend keeping it here since it keeps things organized.
4. If the DeepVocal editor opened on its own, close it. To change the default language from Chinese to English, go to `C:\Program Files (x86)\DeepVocal\config` in the file explorer and open `app.cfg` in a text editor (I use Notepad++, but Windows Notepad will work fine). This is basically the application's persistent settings page. Edit the line that starts with `"langFilePath"` to say `"langFilePath" : "C:\\Program Files (x86)\\DeepVocal\\language\\English.txt"` (or change the path to the correct path, if you installed somewhere else). Make sure to save the file, then you can open DeepVocal and verify that the language is set correctly. This can also be done by running `DeepVocal.exe` as administrator and changing it through the GUI (`首选项` (`Preferences`) -> `语言设定(language)...` (`Language)` -> `English` -> `确定` (`Confirm`)), then restart the program (doesn't need to be run as administrator)
` (or change the path to the correct path, if you installed somewhere else). Make sure to save the file, then you can open DeepVocal and verify that the language is set correctly.
5. Done! You can now close the DeepVocal editor.

Next Step: 
[Installing DeepVocal Voicebanks](/resources/deepvocal/dv-tutorial/02/){: .btn .btn--primary}
