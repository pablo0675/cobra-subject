# Cobra - Where is Xavier

###### Ce jeu de piste aura pour objectif de vous faire découvrir les différentes façons de dissimuler une information. Dans cette variante d’un CTF (Capture The Flag), vous trouverez des balises qui prendront la forme suivante: `EPI{Th1s_iS_4_Fl4g}`. Vous devez les trouver pour valider les challenges. 

Voici le site ou vous pourrez avoir les indices de xavier:  [https://ctfd.crooser.xyz/](https://ctfd.crooser.xyz/login?next=%2Fchallenges%3F)

## Xavier, curieux personnage

Xavier est un honnête homme, bien aimé de ses proches et plein de bon sentiments.  \
Il dédie son temps libre à créer des énigmes et des jeux de piste, c'est sa passion.

## Mais où est-il passé ?

Un jour Xavier disparaît du jour au lendemain, sans rien laisser derrière lui. \
En tant que détective privé employé par C.O.B.R.A (COmmandement-Brigade de Recherche et d'Acquisition) vous devez retrouver Xavier à tout prix, mort ou vif. \
Si vous parvenez à le retrouver il faudra vous addresser aux autorités compétentes de votre lieu de travail (C.O.B.R.A), qui informerons ses proches sur le déroulé de l'enquête.

## Les quelques informations dont nous disposons

On l'aurait filmé sur la nationale 10 en direction du sud de la France. \
Certains de ses collègues de travail auraient essayé de le contacter par mail mais tomberaient sur un répondeur automatique: [son addresse mail](mailto:xavier.cobra.epitech@gmail.com) \
Et c'est tout, Xavier à l'air d'un homme vraiment discret.

## Vos ressources

Vous disposez de quelques ressources, des outils qui vous serviront à déchiffrer les indices et qui vous permettront ainsi de remonter la piste de Xavier:

- [DCode](https://dcode.fr/): L'outil français de cryptographie le plus connu, déchiffrement et mathématiques !
- [CyberChef](https://cyberchef.org/): Déchiffrer des messages avec des centaines de type d'encodage et de chiffrement.
- `hexedit`: Cet éditeur de fichier au format héxadécimal vous permet d'ouvrir n'importe quel fichier et de lire son contenu. `hexedit --help` pour plus d'informations. \
  (Sur Windows ce logiciel est dans le dossier `tools\HexEdit` sur le bureau sous le nom de `HexEdit.exe`)
- `steghide`: StegHide permet de cacher et d'extraire des fichier depuis des images. `steghide --help`  pour plus d'informations \
  (Sur Windows ce logiciel est dans le dossier `tools\steghide` sur le bureau sous le nom de `steghide.exe`)
- `hashcat`: HashCat est un logiciel de crackage de [hash](https://fr.wikipedia.org/wiki/Fonction_de_hachage), à partir d'un type, d'un [dictionnaire de mot](https://fr.wikipedia.org/wiki/Attaque_par_dictionnaire) et d'un hash à cracker \
             on peut en retrouver le mot d'origine, différents algorithmes de hachage existent: [https://assiste.com/Algorithme_de_hachage.html#p02](https://assiste.com/Algorithme_de_hachage.html#p02) \
             `hashcat --help` pour plus d'informations ou [sur le site du projet (en anglais)](https://hashcat.net/hashcat/) \
             (Sur Windows ce logiciel est dans le dossier `tools\hashcat` sur le bureau sous le nom de `hashcat.exe`, le dictionnaire de mot est au même endroit et s'appelle `wordlist.txt`)
- [CrackStation](https://crackstation.net/): Crackstation est une base de donnée de centaine de millions d'associations de hashes et des mot d'origines qui permet de retrouver un mot d'origine directement à partir d'un hash.
- `audacity`: Audacity est un éditeur/lecteur de bande sonore de tout type, sur Windows un raccourci est présent dans `tools\Audacity`, sur Linux on peut le trouver en tapant `audacity` dans la barre de recherche de programme ou dans le terminal.

Vous pouvez cependant utiliser n'importe quel autre outil avec approbation des C.O.B.R.A

