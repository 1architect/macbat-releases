[English](README.md) · [Português](README.pt-BR.md) · **Español** · [Français](README.fr.md)

# MacBat

**El tiempo restante de batería vuelve a tu barra de menús — y tu Mac se calienta menos.**

MacBat estima cuánto dura de verdad tu batería, muestra los datos de energía que
macOS esconde y calla los procesos en segundo plano que la agotan. Usa menos del
1% de CPU, no necesita acceso root y **no recoge ningún dato sobre ti**.

[**Descargar MacBat**](#instalar) ·
[Comprar una licencia](https://giovaniman8.gumroad.com/l/macbat) ·
[Política de Privacidad](PRIVACY.es.md)

---

## Qué hace

**El tiempo restante, de vuelta a su sitio.** Apple quitó la estimación de la
barra de menús. MacBat la devuelve con su propio algoritmo, y mantiene el número
estable en lugar de saltar de un extremo a otro.

**Modo Controlado.** Tu Mac ya gestiona bien su propia batería. Lo que no
siempre gestiona es un proceso en segundo plano quemando energía sin motivo.
MacBat encuentra esos procesos y reduce su uso de CPU — sin tocar el rendimiento
de CPU ni GPU de la app que estás usando de verdad.

**Centinela.** El motor detrás del modo Controlado, disponible por separado si
prefieres conservar el icono de batería original. Elige qué procesos gestiona, o
fija un proceso en los núcleos de eficiencia.

**Datos avanzados, de tu Mac y de tu iPhone.** Carga, salud, ciclos, temperatura
y consumo, registrados a lo largo del tiempo para que veas qué cambió. Conecta
un iPhone o iPad por cable y MacBat también sigue su batería. Exporta todo a
CSV.

**Información útil, de día y de noche.** MacBat muestra lo que importa sobre
consumo, salud de la batería y procesos gestionados en el propio panel, y se
aparta el resto del tiempo.

**Una interfaz de verdad, no otro menú.** Píldoras en Liquid Glass que ponen los
controles que usas bajo tu puntero. El clic derecho abre el menú avanzado.

**Tu icono, tu elección.** El icono nuevo de macOS 27 o el clásico.

**Cuatro idiomas.** Español, inglés, portugués y francés. MacBat sigue el idioma
de tu sistema.

---

## Instalar

### Homebrew (oficial)

```bash
brew install --cask 1architect/macbat/macbat
```

Homebrew es la forma oficial de instalar MacBat.

### Descarga directa (alternativa)

Usa esta opción solo si no puedes usar Homebrew. Descarga el
`MacBat-x.y.z.zip` más reciente desde
[Releases](https://github.com/1architect/macbat-releases/releases/latest),
descomprímelo y arrastra **MacBat.app** a tu carpeta de Aplicaciones.

MacBat está firmado en modo ad-hoc, no con un Developer ID de pago, así que
macOS bloquea la primera apertura. Para permitirla:

1. Haz doble clic en **MacBat.app**. macOS se niega y dice que no pudo verificar al desarrollador.
2. Abre **Configuración del Sistema → Privacidad y seguridad**, baja hasta **Seguridad** y pulsa **Abrir igualmente** en el mensaje sobre MacBat.
3. Confirma con Touch ID o tu contraseña.

macOS recuerda la elección — es un paso único.

> Las guías antiguas dicen que hagas clic derecho y elijas **Abrir**. Ese atajo
> se eliminó en macOS 15 y no funciona en las versiones que MacBat admite.

### Requisitos

- macOS 26 o posterior
- Apple Silicon o Intel

### Actualizar

MacBat nunca busca actualizaciones por su cuenta. Elige **Buscar
actualizaciones…** en el menú cuando quieras mirar, o ejecuta
`brew upgrade --cask macbat`.

---

## Pruébalo, luego cómpralo

MacBat funciona por completo durante **7 días**. Después, una licencia lo
desbloquea de nuevo. No hay cuenta que crear ni suscripción — lo compras una
vez.

[**Comprar una licencia**](https://giovaniman8.gumroad.com/l/macbat)

Para activar: abre el menú, elige el elemento de licencia e introduce el correo
y la clave que llegaron en el correo de compra.

---

## Privacidad

MacBat no tiene analíticas, ni telemetría, ni informes de fallos. Tu historial de
batería, tu lista de procesos y los datos de tu dispositivo se quedan en tu Mac.

MacBat toca la red exactamente dos veces, y solo cuando tú lo pides: al buscar
actualizaciones y al activar una licencia. No hace ninguna conexión al abrirse,
ni en segundo plano.

El detalle completo — cada archivo que escribe, cada campo que envía — está en la
[Política de Privacidad](PRIVACY.es.md).

---

## Permisos

Dos funciones piden autorización de administrador la primera vez que las
activas — Touch ID o tu contraseña, según lo que use tu Mac. La autorización
instala una regla `sudoers` limitada a los comandos exactos que necesitan, y no
se vuelve a pedir:

| Función | Comandos permitidos |
|---|---|
| Bajo consumo | `pmset -a lowpowermode 0` / `1` |
| Controlado | una lista fija de argumentos de `pmset` para reposo de pantalla, Power Nap y activar por red, más `tmutil enable` / `disable` |

De la autorización se encarga macOS, así que MacBat nunca ve tu contraseña. No
instala ningún daemon en segundo plano. Elimina las reglas cuando quieras
borrando `/etc/sudoers.d/macbat-economia` y
`/etc/sudoers.d/macbat-lowpowermode`.

---

## Soporte

**macbat@giomantovani.com.br**

---

## Licencia

MacBat es software propietario. Copyright © 2026 Gio Mantovani / 1architect.
Todos los derechos reservados. El código fuente no es público.

Este repositorio guarda las versiones públicas, el feed de actualización y los
documentos anteriores.
