---
layout: post
title:  "Documentation sous Xcode"
date:   2014-06-12 22:59:35
categories: Développement
---

Les développeurs utilisant Xcode et Cocoa connaissent le raccourci `alt+clic` qui permet de voir rapidement la documentation d'une méthode ou d'une classe des frameworks fournis par Apple. Si ce n’est pas le cas, vous manquez un outil bien utile !

<a href="http://farm8.staticflickr.com/7313/12364419514_d32c9cfd3d.jpg" rel="lightbox">
![Alt+clic sur runModal d'un NSSavePanel](http://farm8.staticflickr.com/7313/12364419514_d32c9cfd3d.jpg)
</a>

A partir d'Xcode 5, Apple offre la possibilité d’utiliser cette feature pour documenter son code Cocoa et ainsi avoir les définitions de nos méthodes et classes rapidement sans retourner voir les sources. Utile pour les projets de groupe !



## Utiliser la syntaxe de documentation appropriée

Chaque langage ou IDE posséde sa propre manière d’être documenté, elles se ressemblent toutes, mais ont aussi chacune leur particularité. L’outil d’Apple ne déroge pas à la règle. Même si des outils, comme [Doxygen](www.doxygen.org), permettent de centraliser la question, certains développeurs préféreront utiliser les méthodes les plus adéquates pour leur langage ou leur IDE,pour exploiter les possibilités de l’IDE au maximum par exemple.

#### Exemple

- votre documentation :    
 
<a href="http://farm3.staticflickr.com/2853/12443847493_fac0325c51.jpg" rel="lightbox">
![Exemple de docuement](http://farm3.staticflickr.com/2853/12443847493_fac0325c51.jpg)
</a>    

- Le resultat : 

<a href="http://farm3.staticflickr.com/2819/12443709685_17d7e55a35.jpg" rel="lightbox">
![resultat de la documenation précédente](http://farm3.staticflickr.com/2819/12443709685_17d7e55a35.jpg)
</a>    


Plutôt que d'expliquer en details les normes de la documentation, vous pouvez consulter ce  [petit projet](https://github.com/leolelego/OSX-Bricks-Codes/tree/master/XcodeDocumentation) avec quelques exemples (qui vont évoluer avec mes découvertes). Mais sachez qu'il existe un plugin d'Xcode pour vous mâcher le travail !
 
 
    
## Un Plugin pour le faire pour vous ?
    
Comme me disait un prof durant mes études,  *ça ne sert à rien de réinventer la roue*, j'ai cherché ce que les autres ont fait de bien, et voici ce que j'ai trouvé (et que j'utilise tous les jours depuis 6 mois), **VVDocument**, un plugin pour Xcode qui permet de générer votre documentation directement dans vos fichiers ressources.  Rapidement, vous entrez trois slashs `///` et **VVDocument** se débrouille pour trouver le format de documentation le plus adéquat, avec des `<#variable#>` pour éditer la doc' facilement. La preuve en image :

<a href="https://raw.github.com/onevcat/VVDocumenter-Xcode/master/ScreenShot.gif" rel="lightbox">
![GIF montrant le fonctionnement de VVDocumenter](https://raw.github.com/onevcat/VVDocumenter-Xcode/master/ScreenShot.gif)
</a>    
Pour utiliser ce magnifique plugin, [télécharger la dernière version](https://github.com/onevcat/VVDocumenter-Xcode/archive/master.zip), et je vous recommande de visiter la page [Github des développeurs](https://github.com/onevcat/VVDocumenter-Xcode) !

> Petit rappel, nul besoin d'ouvrir le projet une fois téléchargé, taper juste :
 `xcodebuild -project path/to/VVDocumenter-Xcode.xcodeproj --alltarguets`