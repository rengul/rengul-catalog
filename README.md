# Rengul application catalog

Catalogo privato per il launcher Rengul. Il launcher scarica questo file dopo
che l'utente ha eseguito il login con il proprio account; un token GitHub non
deve mai essere inserito dentro un'app distribuita.

## Stato iniziale

`Disk Map` è presente come `pending-signed-release`: il launcher lo mostra ma
non offre alcun download fino a quando la release non è firmata Developer ID,
notarizzata e dotata di checksum SHA-256.

Quando sarà pronta la release, sostituire `release: null` con:

```json
{
  "url": "https://github.com/rengul/diskmap/releases/download/v0.1/DiskMap-0.1-macos.zip",
  "sha256": "<hash SHA-256 dell'asset>",
  "signature": {
    "required": true,
    "teamIdentifier": "<Apple Team ID>"
  }
}
```

e impostare `availability` a `available`.
