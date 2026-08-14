[English](PRIVACY.md) · [Português](PRIVACY.pt-BR.md) · **Español** · [Français](PRIVACY.fr.md)

# Política de Privacidad — MacBat

**Última actualización: 14 de agosto de 2026 · Válida para MacBat 1.0.0 en adelante**

MacBat no recoge, no almacena y no transmite ningún dato de uso. No hay
analíticas, ni telemetría, ni informes de fallos, ni publicidad. MacBat no tiene
sistema de cuentas: nunca creas un perfil ni inicias sesión.

Este documento describe exactamente qué lee MacBat, dónde lo guarda y los dos
únicos momentos en que usa la red.

---

## Qué se queda en tu Mac

MacBat lee datos de batería y energía, y los escribe en tu propia máquina. Nada
de eso sale de tu Mac.

| Dato | Dónde se guarda |
|---|---|
| Historial de batería de tu Mac — carga, salud, ciclos, temperatura, consumo | `~/Library/Application Support/MacBat/` |
| Historial de batería de un iPhone o iPad conectado | `~/Library/Application Support/MacBat/` |
| Nombre y consumo de los procesos que gestiona Centinela | En memoria, y en un registro local en la misma carpeta |
| Tus ajustes y las fechas del periodo de prueba | Preferencias de macOS (`UserDefaults`) de MacBat |
| Tu recibo de licencia — correo, ID de producto, fecha de activación | `~/Library/Application Support/MacBat/license-receipt.json` |

Puedes borrarlo todo cuando quieras. Elimina la carpeta `MacBat` de
`~/Library/Application Support/` y la app vuelve a su estado inicial.

La exportación en CSV se escribe en la ubicación que elijas. MacBat nunca la
sube a ningún sitio.

### iPhone y iPad conectados

MacBat lee el estado de la batería de un dispositivo iOS que conectes por cable.
Habla con el dispositivo a través de `usbmuxd`, el servicio local de macOS que
Finder también usa, mediante un socket Unix en tu Mac. **La conexión nunca sale
de tu máquina.** MacBat no lee tus mensajes, fotos, contactos, copias de
seguridad ni ningún otro contenido del dispositivo — solo el estado de la
batería.

---

## Cuándo usa MacBat la red

MacBat hace conexiones de red en dos situaciones, nada más. **Las dos ocurren
porque tú lo pediste.** MacBat no hace ninguna conexión al abrirse, ni en
segundo plano.

### 1. Cuando buscas actualizaciones

La búsqueda automática está desactivada. MacBat solo accede a la red cuando
eliges **Buscar actualizaciones…** en el menú. Entonces pide un archivo de
versión a GitHub:

```
https://raw.githubusercontent.com/1architect/macbat-releases/refs/heads/main/appcast.xml
```

Como en cualquier petición web, GitHub puede ver tu dirección IP y la versión de
MacBat que pregunta. MacBat no envía perfil del sistema, ni información de
hardware, ni identificador de ningún tipo. El tratamiento que GitHub da a esa
petición está en la
[Declaración de Privacidad de GitHub](https://docs.github.com/site-policy/privacy-policies/github-privacy-statement).

### 2. Cuando activas tu licencia

Cuando escribes tu clave de licencia, MacBat envía una petición a Gumroad, la
tienda que procesa las compras de MacBat:

```
POST https://api.gumroad.com/v2/licenses/verify
```

Esa petición lleva tres campos, y nada más:

- el ID de producto de MacBat
- la clave de licencia que escribiste
- un indicador que cuenta la activación

**El correo que escribes no se envía.** MacBat lo compara en tu propio Mac con
la dirección que Gumroad devuelve para esa clave. Tu correo se queda en tu
máquina.

La compra en sí — nombre, correo, datos de pago — la gestiona Gumroad, no
MacBat. Consulta la [Política de Privacidad de Gumroad](https://gumroad.com/privacy)
para saber qué guardan y durante cuánto tiempo.

---

## Qué no hace MacBat nunca

- Nunca envía tu historial de batería, tu lista de procesos ni los datos de tu dispositivo a ningún sitio.
- Nunca lee archivos fuera de su propia carpeta, salvo los que tú le indiques.
- Nunca ejecuta un servicio en segundo plano ni un daemon auxiliar privilegiado.
- No requiere acceso root para funcionar.

### Sobre la autorización de administrador

Dos funciones piden autorización de administrador la primera vez que las
activas: **Bajo consumo** y **Controlado**. Quien muestra la petición es macOS —
Touch ID o tu contraseña, según lo que use tu Mac — y **MacBat nunca ve la
contraseña**. La autorización instala una regla `sudoers` limitada a los
comandos exactos que la función necesita, una lista corta y fija de argumentos
de `pmset` y `tmutil`, y no se vuelve a pedir. La regla no concede nada más allá
de esos comandos. Puedes eliminar las reglas borrando
`/etc/sudoers.d/macbat-economia` y `/etc/sudoers.d/macbat-lowpowermode`.

---

## Menores

MacBat es una utilidad para macOS y no está dirigida a menores. No recoge
información personal de nadie, de ninguna edad.

## Cambios en esta política

Si el comportamiento de MacBat cambia, este documento cambia con él, y la fecha
de arriba también. El historial de este archivo es público en este repositorio:
puedes ver exactamente qué cambió y cuándo.

## Contacto

Dudas sobre privacidad, o sobre cualquier punto de este documento:

**macbat@giomantovani.com.br**
