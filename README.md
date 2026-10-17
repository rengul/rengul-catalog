# Rengul application catalog

Catalogo privato usato da Rengul Hub. Il launcher legge `catalog.json` tramite
GitHub API e usa la copia inclusa nell'app come fallback.

## Pubblicazione

Una voce appare nel launcher quando `availability` è `published` e `hidden` è
`false` o assente. Impostando `hidden` a `true`, l'app resta nel catalogo ma
viene rimossa dalla UI.

Per pubblicare una nuova app basta aggiungere una voce con `id`, `name`,
`repository`, `bundleName` e `release.teamIdentifier`: non è necessario
ricompilare il launcher.

Il catalogo è la fonte autorevole per la versione pubblicata. Il launcher usa
`repository` e `version` per risolvere il tag GitHub corrispondente (per esempio
`0.1.1` → `v0.1.1`) senza sostituirlo con la release più recente. La release
deve contenere un asset `*-macos.zip` e il relativo `*-macos.zip.sha256`; lo ZIP
deve contenere una sola app macOS al primo livello.

Il token GitHub rimane nel Portachiavi del Mac e non deve mai essere inserito
nel catalogo o nel codice distribuito.
