# Procedimiento de publicación — MIDIPlayerMac Big Sur

**Base aprobada:** 1.0.37 (96), `com.redcrea24.MIDIPlayerMac.dev.bigsur`.

**Estado:** infraestructura en preparación. No publicar `appcast.xml` hasta disponer de un paquete real, firmado y verificado.

1. Preparar una versión incremental partiendo del código y las modificaciones exactas de la base aprobada; no asumir que Git HEAD reproduce el binario.
2. Configurar en la aplicación el feed HTTPS exclusivo y la clave pública Ed25519 de Sparkle 2.9.6; nunca incorporar la clave privada.
3. Validar firma de código, helpers, sandbox, identidad, macOS mínimo 11, arquitectura y conservación de bookmarks/recursos en el Mac Big Sur.
4. Crear el ZIP final, obtener su SHA-256 y firmarlo con las herramientas oficiales de Sparkle; comprobar la firma antes de publicar.
5. Subir el ZIP verificado a una GitHub Release del repositorio de distribución, con nombre y versión inequívocos.
6. Crear o actualizar `appcast.xml` con `enclosure` HTTPS real, versión creciente, longitud exacta y firma Ed25519 verificada. No usar URLs hipotéticas.
7. Publicar únicamente después de aprobación; comprobar HTTPS y que el menú «Buscar actualizaciones» descarga y verifica la versión superior.
8. Conservar la base aprobada y las copias protegidas. No ejecutar scripts antiguos de recuperación.

**Transición:** la build 96 no incluye `SUFeedURL`; requiere una instalación manual y supervisada de la primera build con feed (propuesta: 1.0.38 build 97). La siguiente build (98 o superior) podrá validar la actualización integrada.

**Seguridad:** no almacenar secretos, contraseñas, llaveros, firmas privadas, repertorios, SoundFonts ni código fuente privado en este repositorio. Mantener desactivadas consultas/descargas automáticas hasta que el usuario apruebe expresamente el comportamiento.
