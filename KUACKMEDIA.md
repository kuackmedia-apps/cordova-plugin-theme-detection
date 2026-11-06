# Fork de kuackmedia

Fork de [mariusbackes/cordova-plugin-theme-detection](https://github.com/mariusbackes/cordova-plugin-theme-detection) en la versión `1.3.0` publicada en npm (MIT, declarada en `plugin.xml`). Lo usan las apps Cordova de
Kuack Media para el modo oscuro del sistema (`embed/Theme.js` y «usar el tema del sistema» en Configuración).

Base: `4af64da` (upstream no tiene tag de esa versión), idéntico al paquete `cordova-plugin-theme-detection@1.3.0` de npm que las apps instalaban hasta noviembre de 2026.

**Lo publicado es el commit fijado en `_common/configTemplates/config-app*.xml`** del repo de las apps
(`github:kuackmedia-apps/cordova-plugin-theme-detection#<sha>`), no la punta de una branch: un push a este repo no llega a ningún
binario hasta que se mueve ese pin, y mover el pin es un diff que se revisa. La branch `kuack` es la línea de
Kuack; `master` queda como el de upstream.

## Cambios respecto de upstream

**Sin la dependencia `cordova-plugin-add-swift-support`** (iOS). cordova-ios 7 compila Swift con la preferencia `SwiftVersion` del app, que ya está en los `config-app*.xml`; el hook de add-swift-support además tocaba build settings del `project.pbxproj`. El código no cambia.

## Para actualizar desde upstream

`git fetch upstream --tags`, en una branch merge (o rebase) de la versión nueva sobre `kuack`, revisar los
cambios de arriba, probarlo en un app con `config-app-local.xml` (path local del checkout), llevarlo a `kuack` y
mover el pin en los `config-app*.xml`. Nunca cambiar el `id` del plugin ni sus `clobbers`: el bundle remoto lo
comparten los binarios publicados.
