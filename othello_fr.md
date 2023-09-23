# Cobra Coding Club

![Cobra Coding Club](https://cdn.discordapp.com/attachments/1143578891047420008/1153390581637189683/image.png)
![Epitech Technology](https://cdn.discordapp.com/attachments/1143578891047420008/1153390461013201007/image.png)

# Othello
*Simple rule! Simple code!*

![Othello img1](https://cdn.discordapp.com/attachments/1143578891047420008/1153396791006474340/image.png)
![Othello img2](https://cdn.discordapp.com/attachments/1143578891047420008/1153397616487440424/image.png)

| **Othello**               |
|---------------------------|
| **file name:** othello.py |
| **language:** Python 3    |


# Introduction

L'activité qui va suivre consiste à créer un Othello. [(cliquez ici pour les règles du jeu)](https://www.regledujeu.fr/othello/)
Vous programmerez ce jeu en python avec pygame pour l'affichage graphique.
Si jamais voici des liens vers les documentations de [python](https://docs.python.org/3/) et [pygame](https://www.pygame.org/docs/).

## Préparation

> Si python et pygame sont déjà installé vous pouvez passer cette partie.
> Ce sera généralement le cas si Cobra vous fourni l'ordinateur.

Cette partie expliquera comment tout installer pour Windows et Linux,
cependant je suppose que si vous êtes sur Linux vous savez à peu près faire tout par vous même donc je serai plus vague. (Et aussi parce que ya trop distro)

### Installation de python
Commencez par choisir votre système d'exploitation et suivez les instructions.
#### Windows
Deux options s'offre a vous, Vous pouvez soit l'installer depuis le [microsoft store](https://apps.microsoft.com/store/detail/python-311/9NRWMJP3717K) *(la plus simple)* ou l'installer manuellement.
Aucune des deux option n'est meilleure, c'est à vous de choisir.

Dans le cas ou vous voulez télécharger python manuellement, allez sur ce [lien](https://www.python.org/downloads/) et téléchargez la dernière version.
Ouvrez ensuite le fichier .exe que vous venez de télécharger, **vous devez** cocher l'option "Add python.exe to PATH", vous pouvez ensuite choisir soit **Install Now** ou **Customize installation**.
> Si vous ne savez pas lequel choisir cliquez simplement sur **Install Now**.

Après l'installation, ouvrez l'invite de commande et écrire `python --version`, cela devrait afficher la version de python.

#### Linux
Vous pouvez normalement télécharger python a l'aide du gestionnaire de paquets de votre distribution, si c'est pas le cas, bonne chance. 👍
Une fois installé, Vous avez juste à ouvrir le terminal et écrire `python --version`, cela devrait afficher la version de python.

### Installation de pygame

> Vous aurez sans doute besoin d'une invite de commande avec les droits administrateur.

Premièrement, tapez dans votre invite de commandes `pip --version`, si votre ordinateur ne trouve pas pip, vous avez sans doute raté l'installation de python.

> Note pour les utilisateurs linux: pip peut-être un paquet suplémentaire à télécharger, regardez comment le télécharger pour votre distribution.

Si pip est reconnu, écrivez la commande suivante pour être sur que pip est à jour:
> Note pour les utilisateurs linux: Si pip est installé en tant que paquet suplémentaire vous n'avez pas besoin d'écrire cette commande.
```
pip install --upgrade pip
```
Il y a de grande chance que pip soit déjà à jour, sinon il le sera.

Installons maintenant pygame, c'est assez simple, écrivez juste cette commande:
> Note pour les utilisateurs linux: Dans certain cas, pygame doit être installé à l'aide de votre gestionnaire de paquets.
```
pip install pygame
```
Une fois l'installation terminé, **vous êtes prêt !**




## Consigne

Comme dit précedemment, votre objectif est de reproduire le jeu [Othello](https://www.regledujeu.fr/othello/), **en 2h**,
soyez donc malin et ne vous attardez pas trop sur les détails.

Si vous êtes déjà à l'aise avec python et pygame vous pouvez commencer dès maintenant, 
sinon laissez-moi vous faire une petite introduction à pygame. **(Je part du principe que vous savez coder en python)**

### Pygame

Pygame est une petite bibliothèque graphique qui permet de faire principalement des jeux 2D,
dans cette petite introduction nous verrons toutes les choses que vous avez besoin de savoir pour mener à bien ce projet.

Commencons par une fenêtre vide, vous retrouver ci-dessous le code minimal pour en créer une.
J'ai écrit en commentaire le role de chaque ligne et je vous invite à tout lire pour bien comprendre ce qui se passe à chaque étape.
**<details closed><summary>---Cliquez ici pour voir le code---</summary>**

```python
import pygame # Importe le module


# Initialise le module. Sans ça, rien ne fonctionnera.
pygame.init()

# Vous pouvez retirer cette ligne si vous ne penser pas mettre de texte dans votre jeu.
pygame.font.init()


# Cette ligne est optionnelle, et ne sert qu'a changer le titre de la fenêtre.
pygame.display.set_caption("My Othello")

"""
Cette ligne est celle qui ouvre la fenêtre,
ce qui se trouve dans le tuple est la résolution de la fenêtre,
ellle est ici défini a 1280px en largeur et 720px en hauteur.
"""
window = pygame.display.set_mode((1280, 720))
launched = True

"""
Cette boucle maintien la fenêtre ouverte,
si vous la retirez, la fenêtre se fermera instantannement.
"""
while launched:
    """
    Cette boucle récupère les évènemments,
    ces évènement peuvent provenir de la souris ou le clavier
    ou encore de quand vous appuyer sur le boutton pour fermer de la fenêtre.
    """
    for event in pygame.event.get():
        """
        L'évènemment pygame.QUIT est true
        quand vous appuyer sur le boutton pour fermer de la fenêtre.
        """
        if (event.type == pygame.QUIT):
            launched = False

"""
Ces deux fonctions permettent de stopper proprement pygame.
"""
pygame.display.quit()
pygame.quit()
```
</details>

Fantastique! Si vous exécutez ce code, vous devriez avoir une fenêtre que vous pouvez fermer.
Cependant l'intérieur de celle-ci est au mieux, noir ou complètement buggé, essayons de régler ça.

Laissez moi donc vous présenter deux nouvelles fonctions:

#### Fill

```python
pygame.surface.fill(color, rect=None, special_flags=0)
```
Cette méthode permet de remplir votre fenêtre d'une couleur uni de votre choix.
Pour des questions de simplicité, nous nous interesserons seulement au paramètre *color*.
Le paramètre *color* prend un tuple avec trois entiers *(Red, Green, Blue)* chacuns allant de 0 à 255. 
*(0 voulant dire pas de couleur et 255 couleur au max)
Maintenant interessont nous au `pygame.surface`, pour pouvoir utiliser la méthode **fill()** il nous faut un objet de ce type,
et ça tombe bien puisque la variable `window` créé dans l'exemple de code au dessus l'est.
Cette méthode aura donc pour role de **"nettoyer"** votre écran après avoir dessinée tout vos éléments.

Vous pouvez donc par exemple avoir un arrière plan rouge en ajoutant cette ligne dans le code d'au dessus:

```python
window.fill((255, 0, 0))
```
Et si vous venez d'essayer de lancer votre script avec cette modification vous penserez que je vous ai menti 😉.
Ce à quoi je vous répondrai:

Non.

Lisez la suite.

#### Flip

```python
pygame.display.flip()
```
Cette seconde méthode est très utile mais vous ne vous en servirez sans doute qu'une fois dans tout votre code.
Son but est simple, **rafraichir votre fenêtre**.
Cela veut dire que vous avez effectivement appliqué un fond rouge précedemment,
mais vous n'avez pas demandé à pygame de montrer les modifications.
Vous pouvez donc ajouter la ligne ci-dessus tel quel à la suite de **fill()**
et vous obtiendrez une fenêtre rouge.

**Si cela ne vous parrait pas logique**, laissez moi vous donner un petit exemple,
imaginons que vous voulez dessiner un carré bleu sur un fond rouge, vous utiliseriez:

```python
# Creer un objet qui contient la position et les dimension de notre carré.
rect = pygame.Rect(100, 100, 100, 100) 
# Rempli l'arrière plan de rouge.
window.fill((255, 0, 0))
# Dessine le carré en bleu sur window. (On reviendra sur comment dessiner des rectangles après.)
pygame.draw.rect(window, (0,0,255), rect)
```
Si votre fenêtre se rafraichissait à chaque élément dessinés vous auriez **d'abord un fond rouge** puis **votre carré bleu dessus**.
Or vous voulez **carré bleu sur un fond rouge directement**, voici donc pourquoi `pygame.display.flip()` est aussi utile.
#### Vous dessinez toute votre image, puis vous l'afficher.

Si vous avez compris ces deux concepts,
introduisons à présent les différents éléments qui vont concrètement vous permettre de faire votre jeu.

> Note au sujet des positions en pygame (et en général): La position x=0 y=0 correspond au coin **supérieur gauche** de la fenêtre.
> Si **X** augmente, votre élément ira à droite, et si **Y** augmente, il ira vers le bas.

#### DrawRect

Parlons donc maintenant de la méthode pour dessiner des rectangles:
**<details closed><summary>---Cliquez ici pour voir le code---</summary>**

```python
"""
Les paramètres de cette première méthode définissent votre rectangle.
Dans l'ordre: postion X, position Y, largeur, hauteur.
"""
rect = pygame.Rect(300, 300, 200, 100)
"""
Cette méthode quant à elle permettra de dessiner le rectangle en lui meme.
Le premier paramètre determine dans quoi dessiner le rectangle,
le second de quel couleur doit être dessiné le rectangle
et le dernier quel est la taille/position du rectangle (crée en amont avec pygame.Rect()).
"""
pygame.draw.rect(window, (0,255,0), rect)
```
</details>
A l'instar de la méthode **fill()** vu précèdemment,
après avoir dessiné votre rectangle vous devrez utiliser `pygame.display.flip()`.

Vous retrouverez dans le même esprit un moyen de dessiner d'autre formes à cet endroit de la [documentation](https://www.pygame.org/docs/ref/draw.html).

#### Mouse

Si nous voulons pouvoir interagir avec notre plateau de jeu Othello,
la souris semble être l'intermédiaire de prédilection.
Nous nous interesserons ici à ces deux méthodes:

```python
pygame.mouse.get_pressed()
```
```python
pygame.mouse.get_pos()
```
Leurs nom sont plutôt explicite, intéressons nous directement à ce qu'elle retournent.
`pygame.mouse.get_pressed()` retourne une liste de 3 booléens (`True` quand un boutton est pressé sinon `False`):
- [0] représente le clic gauche
- [1] représente le clic mollette (clic du millieu)
- [2] représente le clic droit

`pygame.mouse.get_pos()` quant à lui retourne un tuple de 2 entiers représentant respectivement la position X et Y de la souris.
- [0] Position X
- [1] Position Y

> Vous pouvez dès à présent essayer de déplacer un rectangle là où vous cliquez
> pour voir si vous comprenez correctement chaque notions présentées jusqu'à maintenant.

#### Image

Il pourrait être chouette d'ajouter des images à votre jeu.
Pour utiliser une image vous aurez besoin dans un premier temps de la charger pour ensuite l'afficher.
```python
myLoadedImg = pygame.image.load("./path/to/your/image.png")
```
Voici donc la méthode pour charger une image,
vous indiquez en paramètre le chemin vers l'image et la méthode vous retournera un `pygame.surface`.
Vous reconnaissez sans doute déjà ce type puisque la variable `window` l'est.
```python
pygame.surface.blit(myLoadedImg, (x, y))
```
Parlons maintenant de la méthode **blit()**, cette méthode dessine un `pygame.surface` sur un autre `pygame.surface`.

les paramètres de **blit()**() sont les suivant:
- L'élément que vous voulez dessiner **sur** l'autre `pygame.surface`.
- La position à laquelle vous voulez dessinez cet élément, sous la forme d'un tuple de 2 de long, la première valeur étant **X** et la seconde **Y**.

Dans notre cas nous dessinerons notre image sur `window` pour la voir s'afficher à l'écran.
Voici comment dessiner une image dans le coin supérieur gauche de la fenêtre:
```python
window.blit(myLoadedImg, (0,0))
```
> N'oubliez pas de mettre `pygame.display.flip()` après.

> Essayez de refaire le petit exercice d'au dessus en remplacant le carré par une image.

#### Font

Voici le dernier element que nous verrons dans cette introduction, **afficher du texte**.
> N'oubliez pas d'inserez `pygame.font.init()` au début de votre code.

Premièrement nous devons charger une font (police d'écriture), deux options se présentent à vous:
- `pygame.font.SysFont(fontName, fontSize)` pour charger une police installé dans le système d'exploitation.
- `pygame.font.Font(fontPath, fontSize)` pour charger une police depuis un dossier.

Ces deux fonctions vous renverrons un objet `Font` que vous pourrez dès lors utiliser pour faire un rendu,
ce rendu ce fait l'aide de la méthode render() de l'objet `Font` petit exemple:
```python
myFont = pygame.font.SysFont("Arial", 20)
renderedText = myFont.render("Hello World!", True, (0, 255, 0))
```
les paramètres de render() sont les suivant:
- Le text que vous voulez afficher
- L'anti-aliasing qui permet d'avoir du texte plus joli (je vous recommande de toujours laisser True)
- La couleur du texte

La méthode vous retournera alors un `pygame.surface`, qui, vous l'aurez deviné, doit être donnée à `window` comme ci-dessous:
```python
myFont = pygame.font.SysFont("Arial", 20)
renderedText = myFont.render("Hello World!", True, (0, 255, 0))
window.blit(renderedText, (100, 100))
```

Avec ces trois lignes vous devriez voir le texte "Hello World!" s'afficher en vert sur votre fenêtre.

#### Pygame Conclusion

Voici donc le tour des fonctionnalités qui vous permettront de coder ce fameux Othello,
la bibliothèque pygame propose bien plus de fonctionnalité et
si vous chercher à faire un quelque chose spécifique allez directement sur la [documentation](https://www.pygame.org/docs/).

Je vous souhaite bon courage pour ce projet, et surtout, amusez-vous!
