# Rapport d’audit des traductions françaises

Date : 29 octobre 2026.

## Traduction du verset

V39 demandait `translations=31`. La ressource 31 de l’API Quran.com/Quran Foundation est attribuée à Muhammad Hamidullah et déclarée en français par l’endpoint officiel `resources/translations?language=fr`. Une réponse live vérifiée pour Al-Fātiḥa retourne la référence `1:1`, `resource_id=31` et le nom `French Translation(Muhammad Hamidullah)`. Les pages 1 et 6 d’Al-Baqara ont aussi retourné les clés et ID de traduction conformes à leurs versets.

Dans la copie de développement, la requête explicite l’ID 31 et demande les champs de référence. Avant affichage, chaque verset doit posséder exactement une traduction ID 31 non vide avec la même clé et le même numéro. Le libellé visible nomme Muhammad Hamidullah et crédite Quran Foundation.

L’audit live des 6 236 versets a confirmé la présence d’une traduction ID 31 non vide avec une clé et un numéro conformes à chaque verset. Ce contrôle est structurel : il ne valide pas le sens, la qualité éditoriale ni l’absence d’omission sémantique de la traduction entière. Aucun second traducteur n’a été ajouté; aucune traduction n’a été inventée. La page précise désormais que les bulles lexicales ne sont pas une traduction certifiée mot à mot.

## Attribution et droits

Les [conditions développeur Quran Foundation](https://api-docs.quran.com/legal/developer-terms/) autorisent l’affichage de QF Content dans l’expérience utilisateur d’une application sous réserve de conformité, interdisent de modifier le texte coranique ou de redistribuer les données brutes, et requièrent de créditer Quran Foundation et les traductions par leur source/édition. L’application affiche la traduction dans son expérience utilisateur, pas comme téléchargement brut.

## Contrôles restant à faire

- Relecture humaine de la qualité et de la fidélité sémantique des 6 236 traductions.
- Comparaison sémantique avec d’autres traductions reconnues pour les passages difficiles.
- Vérification d’éventuelles notes/conditions éditoriales propres à Hamidullah avant une distribution en production.
- Audit des gloses mot à mot dans un rapport distinct; elles ne sont pas la traduction officielle du verset.