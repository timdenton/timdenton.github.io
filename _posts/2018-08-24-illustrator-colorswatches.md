---
layout: post
title: Illustrator Color Swatches for Data Science
author: Tim
---

I enjoy annotating my plots and putting them together to a big figure in Adobe Illustrator. However, Illustrator lacks some key color palettes often needed in data science. Luckily, we can built our own color swatches, how palettes are called in Illustrator. I'll show you how to prepare your own color swatch by example of the Otabe & Ito colorblind palette (see [http://jfly.iam.u-tokyo.ac.jp/color/](http://jfly.iam.u-tokyo.ac.jp/color/)).

![otabeitopalette]({{ "assets/img/otabeito.png" | absolute_url }})



## Build your own color swatches

Our goal is, to save the color palette as an .ase file:

1.  Delete the default colors in the Illustrator swatches panel (don't worry, they'll be back when you open a new file). Simply select the colors and hit the 'Delete Swatches' button.
2. Let's also create a new color group.
3. For this example we first need to look up the RGB values of the colors we want to add to the colorblind pallet:

> Blue: 0,114,178
>
> Vermillion: 213,94,0
>
> Bluish Green: 0,158,115
>
> Reddish Purple: 204,121,167
>
> Orange: 230,159,0
>
> Yellow: 240,288,66
>
> Black: 0,0,0

4. Open the Color Picker by double-clicking on the current fill color.
5. Enter the RGB values of the first color.
6. Drag-and-drop the new fill color into the new color group we just created in the swatches panel and repeat this for all colors.
7. Open the options menu of the panel and select 'Save swatches library as ASE...'.

You may want to save an additional copy in folder other that the default one, in case you want easy access to the file. If saved in the default folder, the new palette will be available in the swatches library > user defined.



## Download Brewer and Coloblind palettes

If you don't want to build your own palettes, you can also download .ase files and copy them into the Illustrator Swatches folder (/Applications/Adobe Illustrator CC 2018/Presets/en_US/Swatches).

You can download the Okabe & Ito colorblind palette here: [Okabe-Ito-Colorblind.ase]({{ "assets/download/Otabe-Ito-Colorblind.ase" | absolute_url}})

You should also get the collection of Brewer palettes, as they are commonly used in data science. You'll find .ase and .ai files on Martin Skrywinski's website: [http://mkweb.bcgsc.ca/brewer/]( http://mkweb.bcgsc.ca/brewer/)

![brewerswatches]({{ "assets/img/brewer-swatches-subset.png" | absolute_url }}) 

*A screenshot of Martin Skrywinski's article on Brewer palettes  ([http://mkweb.bcgsc.ca/brewer/](http://mkweb.bcgsc.ca/brewer/)) that shows a subset of Brewer swatches.*