# Image Compressor

## Description

**Image Compressor** est une application Haskell permettant de compresser des images en réduisant leur nombre de couleurs grâce à l’algorithme k-means. Elle supporte la lecture et l’écriture d’images via **JuicyPixels** et offre une optimisation par parallélisation.

Grâce à l’option `-opt`, il est désormais possible de partir d’une image, d’en compresser les pixels et d’obtenir une nouvelle image compressée en sortie.

## Fonctionnalités

- Lecture des pixels depuis un fichier texte ou directement depuis une image.
- Compression en regroupant les couleurs en `N` clusters via l’algorithme k-means.
- Optimisation des calculs grâce à la parallélisation.
- Sauvegarde de l’image compressée au format d’entrée.
- **Nouveau** : Possibilité de traiter directement une image et d’en générer une version compressée.

## Exemple Avant/Après

Avant compression :

Zoro.png

Après compression :

result.png

## Utilisation

### Commande

```bash
./imageCompressor -n N -l L -f F [-opt O]
```

### Paramètres

- `N` : Nombre de couleurs finales souhaitées.
- `L` : Limite de convergence de l’algorithme.
- `F` : Chemin vers le fichier source (image ou fichier texte).
- `O` : Option d’exécution (`img` ou `txt`), `txt` par défaut.

### Formats supportés en mode image

- PNG, JPEG, Bitmap, GIF, TGA, TIFF, Radiance.

### Formats d’entrée et sortie

#### Mode Texte (`-opt txt` par défaut)

##### Format d’entrée :

Fichier contenant des lignes au format :

```
(x,y) (r,g,b)
```

Exemple :

```
(0,0) (33,18,109)
(1,0) (35,18,109)
```

##### Format de sortie :

Fichier listant les clusters :

```
--
(mean_r, mean_g, mean_b)
-
(x1,y1) (r1,g1,b1)
(x2,y2) (r2,g2,b2)
--
...
```

#### Mode Image (`-opt img`)

L’image compressée est générée et sauvegardée sous le nom `result.png`.

## Développement

Le projet utilise Stack pour la gestion des dépendances et la compilation.

- Version minimale requise : `stack 2.1.3`
- Outil de build : `hpack` avec un fichier `package.yaml`

### Compilation et exécution

```bash
make
./imageCompressor -n <nombre de couleurs> -l <limite> -f <fichier> [-opt img]
```

## Auteurs

Sylvanus BONI

