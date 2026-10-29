# Rapport d’audit technique — Coran Al Nour, copie de développement

Mise à jour : 29 octobre 2026. Périmètre : comparaison de V39, de la correction pagination précédente et de `Coran_AlNour_Development.html`.

## Inventaire et sauvegardes

- V39 d’origine (Bureau) : conservée intacte; SHA-256 `146BD97A979E79843325C607EC7544C85989A79B55F9D33A3B3420940468ABB4`.
- Sauvegarde locale intacte : `Coran_AlNour_V39_Preparation_Lancement_Web.backup.html`, même SHA-256.
- Copie corrigée précédente : `Coran_AlNour_V39_Pagination_Corrected.html`.
- Copie de développement active : `Coran_AlNour_Development.html`.
- Copies de retour arrière avant modifications : `Coran_AlNour_Development_PreChange.backup.html` et `Coran_AlNour_Development_PreTranslation.backup.html`.
- Dépôt local `coran` : aucun commit ni remote configuré. Aucun fichier de Chiffr’Eco Pro n’a été modifié.

## Problèmes confirmés

1. V39 demandait `per_page=300` et ne récupérait qu’une page sans contrôler les clés, les identifiants ou le nombre de versets.
2. La correction pagination antérieure demandait 50 versets, mais calculait son nombre de pages à partir du catalogue au lieu de suivre `next_page`; elle ne validait pas les identifiants ni la traduction de chaque verset et acceptait des racines récupérées par proximité de mots.
3. La version antérieure contenait les caractères littéraux `\\n` entre des règles CSS, qui pouvaient invalider le sélecteur Tajwīd suivant. Ils ont été remplacés dans la copie de développement.
4. La traduction de l’API était affichée sans nom d’auteur ni crédit du fournisseur des données.

## Corrections intégrées dans la copie de développement

- Pagination plafonnée à 50, suivie selon les métadonnées `next_page`, `current_page`, `total_pages` et `total_records`.
- Refus d’afficher une sourate si le compte attendu, l’ordre, la clé `sourate:verset`, les identifiants uniques, les mots ou la traduction demandée sont incomplets ou incohérents.
- Délai de 20 secondes par page et bouton de nouvelle tentative en cas d’échec; aucune donnée partielle n’est rendue.
- Traduction française ID 31 sélectionnée explicitement et validée par clé/numéro de verset.
- Attribution visible : Muhammad Hamidullah et Quran Foundation.
- Racines morphologiques retenues uniquement lorsque le mot normalisé correspond à la position exacte; aucun rapprochement avec des tokens voisins ou retrait automatique de suffixe. Les entrées exactes du lexique de travail portent un libellé qui les indique comme candidates à vérifier.
- Les séquences littérales `\\n` corrigées dans le CSS et le JavaScript de la copie de développement.

## Vérifications effectuées

- Catalogue local : 114 entrées, total déclaré 6 236 versets.
- Comparaison live de `chapters?language=fr` : 114 IDs et nombres de versets correspondent au catalogue local. Source officielle API; ce contrôle ne constitue pas une comparaison indépendante du texte arabe.
- Audit live complet : 190 pages pour 114 sourates; 6 236 versets ordonnés, IDs uniques, clés conformes, texte arabe présent et 6 236 références de traduction ID 31 vérifiées. Audit des enregistrements de mots : 83 665 entrées, dont 77 429 mots arabes hors marqueurs de fin; gloses de l’API signalées en anglais.
- Édition indépendante Tanzil/QuranBench : comparaison intégrale indisponible; Fātiḥa 7/7 squelettes consonantiques concordants et échantillons 2:143/2:286 concordants; un écart de squelette observé en 2:1 reste à arbitrer. Voir RAPPORT_COMPARAISON_TEXTE.md.
- Ressource 31 retournée par l’API : auteur Muhammad Hamidullah, langue française.
- Tests automatisés simulés : `node --test tests/pagination.test.cjs` — 14 réussis, 0 échec.
- Syntaxe du script JS embarqué : analyse syntaxique réussie.
- Tajwīd décoché par défaut. Aucun `rel="manifest"` ni service worker présent. Aucune clé ou aucun secret détecté dans le code client lors du contrôle statique.

## Améliorations recommandées

- Ajouter une source et une politique de mise à jour pour une vérification coranique indépendante et reproductible.
- Créer une attribution/source accessible dans une page « À propos » et vérifier les droits et mentions propres à chaque contenu.
- Auditer séparément les gloses mot à mot; la réponse live observée peut donner une glose anglaise aux mots, même avec `language=fr`, puis le code applique son glossaire français de travail.
- Ajouter une recherche si elle est souhaitée; l’interface actuelle propose navigation par sourate et par verset.
- Évaluer PWA/cache seulement avec la stratégie et la synchronisation autorisées par les conditions Quran Foundation.

## Éléments restant à vérifier

- La comparaison indépendante intégrale des 6 236 textes coraniques n’est pas achevée; une divergence de squelette en 2:1 doit être examinée. Pas de validation religieuse complète.
- Les références structurales des 6 236 traductions Hamidullah sont vérifiées; leur fidélité sémantique n’a pas été relue verset par verset.
- Les racines, gloses, formes grammaticales et bulles lexicales des 114 sourates restent à auditer.
- Tests visuels mobile/ordinateur, console navigateur, Android réel, liens de sadaqa, navigation complète et publication non effectués. Aucune vérification visuelle de navigateur/Android réel n’a été effectuée dans cette étape.
- Aucune application Android, configuration de package, AAB, manifeste PWA, URL de production ou procédure de retour arrière n’est fournie dans ce dossier.

Ne pas interpréter ces vérifications comme une validation complète du Coran ou comme une autorisation de publication.