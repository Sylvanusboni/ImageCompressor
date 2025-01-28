# Image Compressor

## Description
**Image Compressor** est une application développée en Haskell qui permet de compresser des images en réduisant leur nombre de couleurs. Ce projet utilise l’algorithme k-means pour regrouper les couleurs et produit des images compressées. Il supporte désormais la lecture et l’écriture directe d’images grâce à **JuicyPixels**.

## Fonctionnalités
- Lecture des pixels depuis un fichier ou directement depuis une image.
- Compression d’images en regroupant leurs couleurs en `N` clusters via l’algorithme k-means.
- Optimisation des calculs par parallélisation.
- Sauvegarde de l’image compressée dans un format pris en charge.

## Utilisation
### Commande
```bash
./imageCompressor -n N -l L -f F

N : Nombre de couleurs finales souhaitées.
L : Limite de convergence de l’algorithme.
F : Chemin vers un fichier contenant les pixels ou une image (PNG, JPEG, etc.).

Format d’entrée

    Fichier texte :
    Contient des lignes au format :

(x,y) (r,g,b)

Exemple :

    (0,0) (33,18,109)
    (1,0) (35,18,109)

    Image :
    Format d’image pris en charge par JuicyPixels (e.g., PNG, JPEG). Les pixels sont extraits automatiquement.

Format de sortie

    Clusters :
    Fichier listant les clusters, par exemple :

    --
    (mean_r, mean_g, mean_b)
    -
    (x1,y1) (r1,g1,b1)
    (x2,y2) (r2,g2,b2)
    --
    ...

    Image compressée :
    Image générée avec les couleurs compressées, sauvegardée dans le même format que l’image d’entrée.

Bonus

    Lecture/écriture d’images : Lecture des pixels directement depuis une image et écriture de l’image compressée via JuicyPixels.
    Optimisation par parallélisation : Utilisation de threads pour accélérer le traitement.

Développement

Le projet utilise Stack pour la gestion des dépendances et la compilation :

    Version minimale : stack 2.1.3
    Build tool : hpack avec un fichier package.yaml.

Commandes de build et d’exécution

Pour compiler et exécuter le projet :

make
./imageCompressor -n <nombre de couleurs> -l <limite> -f <fichier ou image>

Auteurs