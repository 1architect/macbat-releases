[English](TERMS.md) · [Português](TERMS.pt-BR.md) · **Español** · [Français](TERMS.fr.md)

# Términos de Servicio — MacBat

**Última actualización: 30 de septiembre de 2026 · Válido para MacBat 1.0.0 y posteriores**

Estos términos regulan el uso de MacBat, la app de barra de menús para macOS
publicada por Gio Mantovani / 1architect ("nosotros"), de su sitio web y de su
repositorio público de versiones. Al instalar o usar MacBat, aceptas estos
términos. Si no estás de acuerdo, no instales ni uses MacBat.

---

## 1. La licencia

MacBat es software propietario. Tu derecho de uso está definido en la
[Licencia Propietaria de MacBat](LICENSE.es.md): un derecho personal, limitado,
revocable, no exclusivo e intransferible para instalar y usar MacBat. Estos
términos complementan la licencia; si entran en conflicto, la licencia prevalece
en propiedad intelectual y estos términos prevalecen en todo lo demás.

## 2. Funciones gratuitas, prueba y licencia de pago

- **Prueba.** Toda instalación nueva incluye 7 días de prueba gratuita con todas
  las funciones desbloqueadas.
- **Después de la prueba,** el icono de la barra de menús, el porcentaje y el
  tiempo restante siguen siendo gratuitos. Centinela, el modo Controlado, los
  Datos de la batería y los iconos extra requieren una licencia.
- **Licencia.** La licencia es una compra única, no una suscripción. Se activa
  con la clave que recibes de Gumroad y vale para hasta **3 activaciones**. No
  compartas, revendas ni publiques tu clave.
- **Compras y reembolsos.** Las compras las procesa Gumroad, que es el vendedor
  responsable del pago. El pago, los impuestos y los reembolsos se rigen por los
  términos de Gumroad y por los derechos del consumidor del lugar donde vives.
  Dudas sobre una compra: macbat@giomantovani.com.br.
- Podemos cambiar los precios y qué funciones son gratuitas o de pago en
  versiones futuras. Un cambio nunca retira de una licencia ya comprada una
  función de la versión con la que se compró.

## 3. Qué hace MacBat en tu Mac

MacBat es una utilidad que lee datos de energía y, cuando activas la función,
cambia el comportamiento de tu Mac. Conviene que sepas exactamente qué implica:

- **Centinela** pausa y reanuda procesos, o los mueve a los núcleos de
  eficiencia, para reducir su uso de CPU. Un proceso pausado de forma demasiado
  agresiva puede volverse lento, dejar de responder o perder trabajo sin
  guardar. Tú eliges qué procesos gestiona y puedes desactivarlo en cualquier
  momento.
- **El modo Controlado y el modo Bajo consumo** cambian ajustes de energía del
  sistema (`pmset`), y Controlado los restaura al desactivarlo.
- **El control de procesos del sistema** (opcional) permite que Centinela actúe
  sobre procesos de otros usuarios y sobre servicios en segundo plano de macOS.
  Úsalo solo si entiendes los procesos que afectas.
- **Autorización de administrador.** Estas funciones piden una vez Touch ID o tu
  contraseña a través del propio macOS. MacBat nunca ve la contraseña. Instala
  reglas de `sudoers` limitadas a los comandos exactos de cada función, que
  puedes eliminar en cualquier momento, como se describe en la
  [Política de Privacidad](PRIVACY.es.md).
- **Los datos de batería y de dispositivos** provienen de interfaces de macOS,
  algunas no documentadas por Apple y que pueden cambiar con cualquier
  actualización. El tiempo restante, la salud y otras lecturas son
  **estimaciones** y pueden ser erróneas. No dependas de MacBat para nada
  crítico para la seguridad.
- La lectura de un iPhone o iPad conectado usa el servicio local `usbmuxd` y
  solo lee el estado de la batería.

## 4. Uso aceptable

Aceptas no: copiar, modificar, redistribuir, alquilar ni revender MacBat;
intentar la ingeniería inversa, salvo donde la ley lo permita; eludir, alterar o
compartir el mecanismo de prueba o de licencia; ni usar MacBat para interferir
en equipos o datos que no son tuyos o que no estás autorizado a gestionar.

## 5. Actualizaciones

MacBat no busca actualizaciones por sí solo. Tú decides cuándo usar **Buscar
actualizaciones…** o `brew upgrade --cask macbat`. No prometemos un calendario de
versiones, y las correcciones de seguridad van solo a la versión más reciente
(consulta [Seguridad](SECURITY.es.md)). Te corresponde mantener MacBat
compatible con tu versión de macOS; MacBat requiere macOS 26 o posterior.

## 6. Privacidad

MacBat no recopila datos sobre ti. Cómo funciona, qué se queda en tu Mac y los
dos únicos momentos en que usa la red se describen en la
[Política de Privacidad](PRIVACY.es.md), que forma parte de estos términos.

## 7. Sin garantía

MacBat se ofrece **"tal cual" y "según disponibilidad"**, sin garantía de ningún
tipo, expresa o implícita, incluida la idoneidad para un fin concreto, la
exactitud de las estimaciones o el funcionamiento ininterrumpido y sin errores.
No garantizamos que MacBat ahorre una cantidad concreta de batería.

## 8. Limitación de responsabilidad

En la máxima medida permitida por la ley, no respondemos por daños indirectos,
incidentales o consecuentes, pérdida de datos, lucro cesante ni daños a tu Mac o
a otros dispositivos derivados del uso o de la imposibilidad de uso de MacBat.
Nuestra responsabilidad total por cualquier reclamación se limita al importe que
pagaste por tu licencia de MacBat. Nada en estos términos limita la
responsabilidad que la ley no permite limitar, ni los derechos imperativos del
consumidor.

## 9. Terminación

Puedes dejar de usar MacBat en cualquier momento eliminándolo y, si quieres,
borrando sus datos y las reglas de `sudoers`. Podemos revocar una licencia usada
en incumplimiento de estos términos, por ejemplo una compartida o revendida, u
obtenida mediante un contracargo o un pago fraudulento. Al terminar, debes dejar
de usar MacBat y borrar tus copias.

## 10. Cambios en estos términos

Si cambiamos estos términos, este documento cambia con ellos y la fecha de
arriba también. El historial de este archivo es público en este repositorio.
Seguir usando MacBat después de un cambio significa que aceptas los nuevos
términos.

## 11. Ley aplicable

Estos términos se rigen por las leyes de Brasil, sin tener en cuenta sus normas
de conflicto de leyes. Las normas imperativas de protección del consumidor del
país donde vives siguen aplicándose. Cualquier controversia podrá someterse a
los tribunales del lugar donde puedas demandar conforme a esas normas y, en su
defecto, a los tribunales de Brasil.

## 12. Contacto

Preguntas sobre estos términos o solicitudes de autorización:

**macbat@giomantovani.com.br**

El texto en inglés es la versión de referencia en caso de discrepancia entre
las traducciones.
