# Petites victoires — Hall des trophées

[Ouvrir l’application](https://egalland.github.io/petites-victoires/) · [Calendrier Inktober 2026](https://egalland.github.io/)

Refonte en TypeScript : compteurs personnalisés, jusqu’à huit paliers par parcours, médailles SVG métalliques, inspection, jauge animée, particules Canvas et célébrations. Jusqu’à 40 parcours et 20 000 actions dans l’historique conservé (les 120 dernières sont affichées).

## Fonctionnement
Créer un parcours (ou utiliser le préréglage Jira), saisir la valeur, puis progresser avec +1/+10/+20 ou un ajout personnalisé. Une médaille se débloque la première fois que le total atteint son palier. Elle reste acquise après une correction à la baisse. Retirer un palier dans la personnalisation retire cette médaille de la collection ; sa trace reste dans l’historique. Supprimer un parcours supprime aussi son historique, après confirmation.

La démo (480 tickets fictifs) est isolée en mémoire ; +20 permet de voir le déblocage 500. Les aperçus et relectures d’effets ne modifient pas les données. Réglages et export concernent toujours les données réelles.

## Données
localStorage sur l’origine du Site, sans synchronisation entre appareils ni intégration Jira. Import/export JSON avec validation, confirmation avant remplacement et vérification d’écriture avant toute réussite. L’ancien journal V1 reste dans sa clé distincte et n’est pas effacé par cette refonte.

## Accessibilité et effets
Boutons natifs, labels, navigation clavier, dialogues natifs, alertes et états vides. Les préférences système et le réglage local réduisent les animations. Les déblocages restent identifiés textuellement. Particules limitées à 220 et rendu arrêté hors activité ou si le document est masqué.

## Compilation et vérifications
`tsc -p tsconfig.json`, publication du dossier `dist`. TypeScript strict. Parcours métier vérifié avec stockage simulé : création, seuils, persistance après redémarrage, correction, isolation démo, import invalide, échec d’écriture et suppression confirmée. Pas de vérification visuelle automatisée de navigateur dans l’environnement de création.

## Personnalisation des médailles
Cliquez sur une médaille (acquise ou verrouillée) ou le trophée central. Choisissez parmi six formes : blason, sceau rond, étoile, cristal, couronne et hexagone. Cinq emblèmes sont disponibles pour chaque palier. L’aperçu est temporaire jusqu’au bouton « Garder cette apparence ». Le choix est conservé pour ce palier, y compris dans les exports et après modification du parcours. Les sauvegardes sans choix de style restent compatibles. Les tests couvrent la persistance, la conservation des déblocages et l’échec d’enregistrement.
