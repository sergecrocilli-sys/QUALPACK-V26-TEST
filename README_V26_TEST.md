# QUALPACK V26 TEST

Version de test créée à partir de QUALPACK V25.2.

## Ajouts V26 TEST

- Écran de validation `site_id + clé` au lancement.
- Envoi automatique des headers Supabase :
  - `x-qualpack-site-id`
  - `x-qualpack-site-key`
- Site par défaut pour les essais : `codex_test`.
- Cache service worker renommé pour éviter les conflits avec V25.2.
- V25.2 doit rester en service pour Moulin des Moines et Traiteur de la Thur.

## URL de test conseillée

https://sergecrocilli-sys.github.io/QUALPACK-V26-TEST/?site_id=codex_test

## Clé de test

QP-CODEX-TEST

## Important

Tant que les policies temporaires `temp_v25_*` existent dans Supabase, V25.2 continue de fonctionner.
Quand V26 TEST sera validée, il faudra supprimer ces policies temporaires pour activer la sécurité stricte.
