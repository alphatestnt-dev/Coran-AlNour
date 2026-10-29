# Comparaison du texte arabe — Quran Foundation et édition dérivée de Tanzil

Date : 29 octobre 2026.

## Portée et méthode

Le flux Uthmani de Quran Foundation a fourni 6 236 versets. Ils ont été comparés, lorsque le point d’accès indépendant était disponible, à l’édition indiquée par QuranBench comme « Tanzil Uthmani 1.1 ». Les comparaisons distinguent égalité Unicode exacte, égalité après NFC et égalité du squelette consonantique (marques vocaliques et tatwīl retirés). Ces normalisations servent uniquement au diagnostic; le texte coranique de l’application n’a pas été altéré.

## Résultats constatés

- Métadonnées Quran Foundation : 114 sourates et 6 236 versets; clés, ordre, unicité des identifiants et présence de texte valide contrôlés sur le flux complet.
- Al-Fātiḥa : 7 versets comparés. 3/7 sont identiques en Unicode exact et après NFC; les 7/7 squelettes consonantiques correspondent. Les écarts observés dans les autres versets relèvent de signes/formatage, selon le test de normalisation.
- Al-Baqara : l’endpoint indépendant de sourate complète n’a pas pu être récupéré. Trois versets échantillonnés : 2:143 et 2:286 ont un squelette consonantique identique, avec des différences de signes/formatage; 2:1 présente aussi un écart au niveau du squelette consonantique. Cette différence doit être examinée avec une édition de référence avant toute décision.
- Le contrôle indépendant intégral des 6 236 textes n’est donc pas terminé. Il serait inexact de conclure que toutes les sourates sont textuellement identiques à Tanzil.

## Décision conservatoire

Aucune différence de texte arabe n’a été corrigée automatiquement et aucun texte n’a été choisi arbitrairement entre les sources. L’interface conserve le flux Quran Foundation et les rapports signalent les limites de comparaison. Avant publication, faire vérifier les différences d’édition et de signes par une source coranique qualifiée, notamment l’écart de 2:1.

## Sources

- [Quran Foundation — versets par sourate](https://api-docs.quran.com/docs/content_apis_versioned/4.0.0/verses-by-chapter-number/)
- [Tanzil — documentation et conditions](https://tanzil.net/docs/)
- [QuranBench — API et édition textuelle annoncée](https://quranbench.com/api)
