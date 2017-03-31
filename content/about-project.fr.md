+++
date = "2017-03-16"
title = "À propos du projet"
+++

## Aperçu général

Le projet, distribué à travers plusieurs bibliothèques universitaires, ajoute plus de 1,000 carte à notre base de données numérique collective, incluant des feuilles très connues couvrant l’Ontario à partir de la série de cartes topographiques nationales de 1:63,360 et 1:25,000. Les universités de l’Ontario ont contribué en fournissant et en numérisant des cartes, en effectuant un géoréférencement des images numériques, en créant des métadonnées pour les dossiers et en élaborant une présentation géographique en ligne des cartes pour permettre l’accès au public. 

À ces échelles, les cartes topographiques sont très souvent utilisées par des chercheurs désirant examiner les changements au fil du temps, comme l’expansion urbaine, les tendances en matière de transport, la réduction des lots boisés ou l’érosion des côtes. 

La Communauté Géo du OCUL est un forum permettant d’échanger des informations et des idées en rapport avec des cartes, des données géospatiales et d’autres ressources cartographiques, imprimées et numérisées, avec la plus large communauté du Conseil des bibliothèques universitaires de l’Ontario.

Pour en savoir plus ou pour poser des questions au sujet du projet, veuillez [nous contactez](../contact/).

## Spécifications techniques

Ce qui suit explique les étapes prises pour numériser toutes les cartes topographiques historiques à partir de la série d’échelles 1:25,000 et 1:63,360 pour l’Ontario. Ces spécifications techniques sont présentées comme un ensemble de lignes directrices en termes de géoréférencement et de numérisation pour le projet. Elles peuvent être également utilisées comme références utiles pour d’autres institutions qui désirent mettre en place des projets de numérisation de cartes. 

### Numérisation
Les cartes imprimées ont été numérisées à une résolution de 600 ppi et une profondeur de couleur de 24-bit avec des scanners Colortrac (modèles SmartLF Gx+ T56 et SmartLF SG), en utilisant des couleurs normalisées et des procédés de correction de point. Des méthodes manuelles de contrôle de la qualité ont été appliquées pour chaque feuille numérisée afin de s’assurer que les images ont été correctement redressées et recadrées. Les images ont été manuellement inspectées pour vérifier toute présence de défaut de numérisation pouvant avoir un impact sur la qualité des images ou des feuilles devant être rescannées. 

### Images dérivées
Le logiciel ImageMagick a été utilisé avec un script personnalisé pour générer trois images dérivées de différentes tailles pour chaque feuille numérisée en format JPEG. Un format JPEG « grand » a été créé en élargissant l’image TIFF d’origine de 50 % ; Un format « moyen » JPEG a été créé en élargissant le TIFF d’origine à une image de 2 000 pixels ; et un format « petit » JPEG a été créé en élargissant l’image TIFF d’origine en une image de 200 pixels. 

### Géoréférencement et géorectification
Un total de 8 à 12 points de control au sol ont été créés pour chaque carte numérisé en utilisant le logiciel ArcMap (versions 10.1 à 10.5). Le géoréférencement et la projection pour chaque carte ont été effectués en utilisant les fonctions gdal_translat et gdalwarp de la Geospatial Data Abstraction Library (GDAL). Un script personnalisé a été utilisé pour automatiser la conversion des fichiers ArcMap GCP en format GDAL, ainsi que les procédés de géoréférencement et de transformation. Dans le procédé de transformation, les GeoTIFF ont été projetés au système géodésique NAD83, et dans la zone UTM appropriée. 

### Création de cartes web carrelées
Chaque image géorectifiée a été transformée en une collection de cartes web carrelées en utilisant la bibliothèque gdal2tiles dans un script personnalisé. Le carrelage a été créé dans une projection Web Mercator (EPSG: 3857) pour des niveaux de zoom de 6 à 16. 

Tous les scripts de traitement des données géographiques sont disponibles sur [Github](https://github.com/jasonbrodeur/OCUL_HTDP).

### Site web du projet
Le site web du projet a été créé avec le [générateur de site web Hugo](https://gohugo.io/). Il utilise [JuxtaposeJS](https://juxtapose.knightlab.com/) pour comparer les images, et le [plugin elevateZoom-plus jQuery](https://github.com/igorlino/elevatezoom-plus)  pour zoomer sur des cartes individuelles. Le code source pour le site web est disponible sur [Github](https://github.com/scholarsportal/historical-topos).

## Contributeurs

Pendant la durée du projet, il y a eu de nombreux contributeurs partout dans l’Ontario, y compris des bibliothèques et d’autres organismes, dont certains ont aidé en fournissant des cartes provenant de collections locales, en effectuant un balayage des cartes, et en aidant avec le géoréférencement, l’assurance de la qualité, la création de métadonnées, la transformation de données, la gestion de projet et le développement technique. Ce qui suit est une liste des institutions et organismes qui ont contribué au projet entre 2014 et 2017. 

### Organismes
* Archives de l’Ontario
* Bibliothèque de l’Université Brock
* Bibliothèque de l’Université Carleton 
* Bibliothèque et Archives Canada
* Bibliothèque de l’Université McMaster 
* Ressources naturelles Canada
* Bibliothèque de l’Université Queen
* Bibliothèque de l’Université Ryerson 
* Scholar's Portal (le Portail des chercheurs), OCUL
* Bibliothèque de consultation de Toronto
* Bibliothèque de l’Université Trent 
* Bibliothèque de l’Université de l’Alberta
* Université d’Ottawa
* Bibliothèques de l’Université de Toronto
* Bibliothèque de l’Université Waterloo
* Bibliothèque de l’Université Western 
* Bibliothèque de l’Université Wilfrid Laurier 
* Bibliothèque de l’Université York 


<br>

### Individus
* Colleen Beard (Université Brock)
* Rebecca Bartlett (Bibliothèque de l’Université Carleton)
* Ryder Burt (Bibliothèque de l’Université Carleton)
* Joël Rivard (Bibliothèque de l’Université Carleton)
* Lorraine Dubreuil (Emeritus, Université McGill)
* Jordan Aharoni (Université McMaster)
* Victoria Balkwill Tweedie (Université McMaster)
* Gordon Beck (Université McMaster)
* Jason Brodeur (Université McMaster)
* Katie Maloney (Université McMaster)
* Jenny Ni (Université McMaster)
* Ashleigh Patterson (Université McMaster)
* Margaret Rutten (Université McMaster)
* Bianca Chiarenza (Université Ryerson)
* Noel Damba (Université Ryerson)
* Dan Jakubek (Université Ryerson)
* Jo Ashley (Scholar's Portal, OCUL)
* Jaiwei Chen (Scholar's Portal, OCUL)
* Kara Handren (Scholar's Portal, OCUL)
* Amber Leahey (Scholar's Portal, OCUL)
* Kaitlin Newson (Scholar's Portal, OCUL)
* Kevin Worthington (Scholar's Portal, OCUL)
* Charles Hill (Bibliothèque de l’Université d’Ottawa)
* Raphaël Pelletier (Bibliothèque de l’Université d’Ottawa)
* Sophie Routhier LeBlanc (Bibliothèque de l’Université d’Ottawa)
* Sarah Simpkin (Bibliothèque de l’Université d’Ottawa)
* Cheryl Woods (Bibliothèque de l’Université Western)
* Trudy Bodak (Emeritus, Université York)
* Neil Livingston (Bibliothèque de l’Université York)
* Zarah Malm (Université York)
* Rosa Orlandini (Bibliothèque de l’Université York)
* Veronica Petta (Université York)
* Artemisia Robins (Université York)
* Marisa Thomas-Perrier (Université York)

<br>

Un merci tout particulier au Conseil des bibliothèques universitaires de l’Ontario (OCUL) pour avoir fourni le financement pour ce projet de 3 ans. En 2017, OCUL célèbre son 50ème anniversaire, et ce projet représente une réalisation extraordinaire en prenant en compte la collaboration dans le domaine de la gérance partagée et la préservation du patrimoine du Canada. 
