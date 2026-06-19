# Projet-Image

Ce projet implémente un flux de travail complet pour détecter et segmenter des objets spécifiques au sein d'une image en combinant deux architectures de Deep Learning complémentaires.

## Comment faire fonctionner le projet

Pour exécuter ce pipeline dans Google Colab, suivez ces étapes dans l'ordre :

1.  **Installation & Imports** : Exécutez la première cellule pour importer les bibliothèques (`transformers`, `torch`, etc.). Si les bibliothèques manquent, décommentez et lancez la commande `pip install`.
2.  **Chargement de l'image** : La cellule 1 télécharge une image depuis MS COCO. Vous pouvez modifier la variable `url` pour tester une autre image.
3.  **Détection** : Lancez la cellule 2 pour que le modèle **YOLOS** identifie les objets. Les résultats s'affichent sous forme de texte (nombre d'objets).
4.  **Segmentation localisée** : Exécutez la cellule 3. Pour chaque objet, vous verrez apparaître le "crop" (l'image découpée) et son masque de segmentation correspondant.
5.  **Rendu final** : La dernière cellule de code affiche l'image originale avec tous les masques superposés en couleur.

## Architecture du Pipeline

### 1. Acquisition de Données
Utilisation d'images provenant du dataset **MS COCO**.

### 2. Détection d'Objets (YOLOS)
- **Rôle** : Identifier les boîtes englobantes et les classes.
- **Modèle** : `hustvl/yolos-small`.

### 3. Segmentation par Instance Localisée (MaskFormer)
- **Crop & Segment** : Chaque objet détecté est extrait. Le modèle `MaskFormer` génère un masque binaire pour l'objet principal dans ce recadrage.
- **Affichage Intermédiaire** : Le code affiche désormais côte à côte l'objet extrait et son masque de segmentation.
- **Reprojection** : Les masques sont ensuite fusionnés sur un canevas global.

### 4. Synthèse Finale
Superposition du masque global sur l'image source pour une vue d'ensemble des segmentations.

## Bibliothèques
`Transformers`, `PyTorch`, `Pillow`, `Matplotlib`, `NumPy`.
