# FastBoB — canal de actualizaciones

Este repositorio **público** aloja el feed de [Sparkle](https://sparkle-project.org)
para la app **FastBoB** y los binarios de cada versión (como *assets* de GitHub Releases).

- **Appcast (feed):** [`appcast.xml`](appcast.xml)
  → `https://raw.githubusercontent.com/JavierQuerol/FastBoB-updates/main/appcast.xml`
- **Binarios:** cada versión se publica como un *Release* con el `.zip` adjunto.

El código fuente de la app se mantiene aparte (privado/local). Aquí solo vive
lo necesario para distribuir actualizaciones.

## Cómo se publica una versión

Desde el proyecto de la app se ejecuta `release.sh`, que:

1. Compila **Release** firmado con *Developer ID Application* + Hardened Runtime.
2. Genera el `.zip`, lo **notariza** y le hace *staple*.
3. Crea un *Release* en este repo y sube el `.zip`.
4. Regenera `appcast.xml` con `generate_appcast` (firma EdDSA incluida) y lo sube.

La clave pública EdDSA va incrustada en la app (`SUPublicEDKey`); la privada
está en el llavero del desarrollador y nunca se publica.
