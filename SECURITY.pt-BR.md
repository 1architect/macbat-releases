[English](SECURITY.md) · **Português** · [Español](SECURITY.es.md) · [Français](SECURITY.fr.md)

# Política de Segurança

O MacBat é um utilitário de barra de menus para macOS. Ele roda na sua conta de
usuário normal, não instala daemon em segundo plano e não coleta dados sobre
você. Este documento explica exatamente o que ele toca no seu Mac e como relatar
um problema.

## Relatar uma vulnerabilidade

Envie um e-mail para **macbat@giomantovani.com.br** com os detalhes e os passos
para reproduzir. Não abra uma issue pública para um relato de segurança. Você
recebe uma confirmação em poucos dias.

## Versões suportadas

As correções de segurança entram só na versão mais recente. Atualize sempre para
a versão mais nova em [Releases](https://github.com/1architect/macbat-releases/releases/latest)
ou com `brew upgrade --cask macbat`.

## O que o MacBat faz no seu Mac

### Rede

O MacBat faz conexões de rede em exatamente dois casos, e só quando você as
inicia. Ele não faz conexão ao abrir, nem em segundo plano.

1. **Procurar atualizações.** Ao escolher *Procurar atualizações…* no menu, o
   MacBat lê um feed de versão hospedado com as releases no GitHub. Se você
   aceitar uma atualização, ele baixa a nova versão do GitHub Releases. Nada
   sobre você é enviado.
2. **Ativar uma licença.** Ao digitar seu e-mail e a chave de licença, o MacBat
   os envia para o Gumroad (`POST https://api.gumroad.com/v2/licenses/verify`)
   para verificar a chave. É a única vez em que seu e-mail sai do Mac, e só
   porque você pediu para ativar.

Não há analytics, telemetria nem relatório de falhas.

### Onde seus dados ficam

Tudo fica no seu Mac, na sua conta de usuário:

- `~/Library/Application Support/MacBat/` — histórico de bateria e de
  dispositivos (`battery-history.json`) e o estado do teste (`trial.json`).
- Preferências no domínio `com.giovanimanto.macbat`
  (`~/Library/Preferences/com.giovanimanto.macbat.plist`).

Nada disso é enviado para lugar nenhum.

### Como o Sentinela atua

O Sentinela é o motor por trás do modo Controlado. Para os processos em segundo
plano que você deixa ele gerenciar, ele reduz o uso de CPU deles sem encerrá-los,
e o processo volta a rodar normalmente assim que é liberado. Ele também pode
manter um processo nos núcleos de eficiência, e sempre desfaz isso quando o
processo é liberado. O Sentinela nunca muda o comportamento de CPU ou GPU do app
que você tem em primeiro plano, e nunca toca em processos críticos do sistema.

### Permissões de administrador

Dois recursos pedem autorização de administrador na primeira vez que você os
liga (Touch ID ou sua senha). A autorização instala uma regra `sudoers` limitada
aos comandos exatos de que o recurso precisa, e não é pedida de novo:

| Recurso | Comandos liberados |
|---|---|
| Pouca Energia | `pmset -a lowpowermode 0` / `1` |
| Controlado | uma lista fixa de argumentos do `pmset` para sono da tela, Power Nap e acordar por rede, mais `tmutil enable` / `disable` |

Quem trata a autorização é o macOS, então o MacBat nunca vê sua senha, e ele não
instala daemon nenhum em segundo plano. As regras ficam em
`/etc/sudoers.d/macbat-lowpowermode` e `/etc/sudoers.d/macbat-economia`, e você
pode removê-las quando quiser (veja Desinstalar abaixo).

### Assinatura de código

O MacBat é assinado em modo ad-hoc, não com um Apple Developer ID pago. Verifique
um download antes de confiar nele:

```bash
codesign -dv --verbose=4 /Applications/MacBat.app
```

## Desinstalar por completo

1. Feche o MacBat. Desligue **Controlado** e **Pouca Energia** antes, para os
   ajustes de sistema voltarem.
2. Remova o app:
   ```bash
   brew uninstall --cask macbat
   ```
   ou arraste o **MacBat.app** de Aplicativos para o Lixo.
3. Remova os dados e as preferências:
   ```bash
   rm -rf ~/Library/Application\ Support/MacBat
   defaults delete com.giovanimanto.macbat
   ```
4. Remova as regras de administrador (só se você já ligou Pouca Energia ou
   Controlado):
   ```bash
   sudo rm -f /etc/sudoers.d/macbat-economia /etc/sudoers.d/macbat-lowpowermode
   ```
5. Se o MacBat escondeu o ícone de bateria nativo, reative-o em **Ajustes do
   Sistema → Central de Controle → Bateria**.

Depois disso, nenhum arquivo do MacBat fica no seu Mac.
