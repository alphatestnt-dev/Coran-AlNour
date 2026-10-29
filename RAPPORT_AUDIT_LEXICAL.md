# Rapport lexical et mot à mot

Date : 29 octobre 2026.

L’HTML contient un glossaire français de travail, des notes ciblées, des racines lexicales et des données morphologiques chargées depuis un dépôt GitHub tiers. Ces contenus ne sont pas validés dans leur ensemble. Dans l’audit live de 83 665 enregistrements de mots (dont 6 236 marqueurs de fin de verset), les gloses fournies par l’API étaient signalées en anglais malgré `language=fr`. L’interface le signale maintenant explicitement à l’utilisateur : les bulles sont des gloses de travail, pas une traduction française certifiée mot à mot.

Aucune correction linguistique exhaustive n’a été appliquée. L’alignement des racines du dépôt externe, la couverture de chaque token, les cas inconnus et les sens de contexte doivent être vérifiés occurrence par occurrence avec des sources linguistiques reconnues avant de marquer ce corpus comme validé.

## Correction technique anti-erreur

La copie de développement n’associe plus une racine à un token voisin si le mot à la position attendue ne correspond pas. La racine du corpus n’est utilisée que si l’index et la forme normalisée concordent. Le repli lexical accepte uniquement une clé de mot exacte; son libellé indique qu’il s’agit d’une entrée de travail à vérifier. Un test de non-régression couvre les correspondances de position exacte et le refus d’une correspondance voisine.

L’application conserve la traduction du verset Muhammad Hamidullah séparée des bulles lexicales et des sept éclairages originaux de la Fātiḥa, qui sont identifiés comme éclairages et non comme traductions publiées.
