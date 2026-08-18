[English](SECURITY.md) · [Português](SECURITY.pt-BR.md) · **Español** · [Français](SECURITY.fr.md)

# Política de Seguridad

MacBat es una utilidad de barra de menús para macOS. Se ejecuta con tu cuenta de
usuario normal, no instala ningún daemon en segundo plano y no recopila datos
sobre ti. Este documento explica exactamente qué toca en tu Mac y cómo informar
un problema.

## Informar una vulnerabilidad

Escribe a **macbat@giomantovani.com.br** con los detalles y los pasos para
reproducirla. No abras una incidencia pública para un informe de seguridad.
Recibes una confirmación en unos días.

## Versiones compatibles

Las correcciones de seguridad solo entran en la última versión. Actualiza siempre
a la versión más reciente desde [Releases](https://github.com/1architect/macbat-releases/releases/latest)
o con `brew upgrade --cask macbat`.

## Qué hace MacBat en tu Mac

### Red

MacBat hace conexiones de red en exactamente dos casos, y solo cuando tú las
inicias. No hace ninguna conexión al abrirse, ni en segundo plano.

1. **Buscar actualizaciones.** Cuando eliges *Buscar actualizaciones…* en el
   menú, MacBat lee un feed de versión alojado con las versiones en GitHub. Si
   aceptas una actualización, descarga la nueva versión desde GitHub Releases. No
   se envía nada sobre ti.
2. **Activar una licencia.** Cuando escribes tu correo y la clave de licencia,
   MacBat los envía a Gumroad (`POST https://api.gumroad.com/v2/licenses/verify`)
   para verificar la clave. Es la única vez que tu correo sale del Mac, y solo
   porque pediste activar.

No hay analíticas, ni telemetría, ni informes de fallos.

### Dónde se guardan tus datos

Todo se queda en tu Mac, en tu cuenta de usuario:

- `~/Library/Application Support/MacBat/` — historial de batería y de
  dispositivos (`battery-history.json`) y el estado de prueba (`trial.json`).
- Preferencias en el dominio `com.giovanimanto.macbat`
  (`~/Library/Preferences/com.giovanimanto.macbat.plist`).

Nada de esto se sube a ningún sitio.

### Cómo actúa Centinela

Centinela es el motor detrás del modo Controlado. Para los procesos en segundo
plano que le dejas gestionar, reduce su uso de CPU sin terminarlos, y el proceso
vuelve a ejecutarse con normalidad en cuanto se libera. También puede mantener un
proceso en los núcleos de eficiencia, y siempre lo deshace cuando el proceso se
libera. Centinela nunca cambia el comportamiento de CPU o GPU de la app que tienes
en primer plano, y nunca toca procesos críticos del sistema.

### Permisos de administrador

Dos funciones piden autorización de administrador la primera vez que las activas
(Touch ID o tu contraseña). La autorización instala una regla `sudoers` limitada
a los comandos exactos que la función necesita, y no se vuelve a pedir:

| Función | Comandos permitidos |
|---|---|
| Bajo consumo | `pmset -a lowpowermode 0` / `1` |
| Controlado | una lista fija de argumentos de `pmset` para reposo de pantalla, Power Nap y activar por red, más `tmutil enable` / `disable` |

De la autorización se encarga macOS, así que MacBat nunca ve tu contraseña, y no
instala ningún daemon en segundo plano. Las reglas están en
`/etc/sudoers.d/macbat-lowpowermode` y `/etc/sudoers.d/macbat-economia`, y puedes
eliminarlas cuando quieras (mira Desinstalar más abajo).

### Firma de código

MacBat está firmado en modo ad-hoc, no con un Apple Developer ID de pago.
Verifica una descarga antes de confiar en ella:

```bash
codesign -dv --verbose=4 /Applications/MacBat.app
```

## Desinstalar por completo

1. Cierra MacBat. Desactiva **Controlado** y **Bajo consumo** antes, para que los
   ajustes del sistema se reviertan.
2. Quita la app:
   ```bash
   brew uninstall --cask macbat
   ```
   o arrastra **MacBat.app** desde Aplicaciones a la Papelera.
3. Quita los datos y las preferencias:
   ```bash
   rm -rf ~/Library/Application\ Support/MacBat
   defaults delete com.giovanimanto.macbat
   ```
4. Quita las reglas de administrador (solo si alguna vez activaste Bajo consumo o
   Controlado):
   ```bash
   sudo rm -f /etc/sudoers.d/macbat-economia /etc/sudoers.d/macbat-lowpowermode
   ```
5. Si MacBat ocultó el icono de batería nativo, actívalo de nuevo en
   **Configuración del Sistema → Centro de Control → Batería**.

Después de esto, no queda ningún archivo de MacBat en tu Mac.
