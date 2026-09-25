[English](README.md) · **Português** · [Español](README.es.md) · [Français](README.fr.md)

# MacBat

**O tempo restante de bateria voltou para a sua barra de menus — e o seu Mac esquenta menos.**

O MacBat estima quanto tempo a sua bateria realmente dura, mostra os dados de
energia que o macOS esconde e cala os processos em segundo plano que a drenam.
Usa menos de 1% de CPU, não precisa de root e **não coleta nenhum dado sobre
você**.

[**Baixar o MacBat**](#instalar) ·
[Comprar uma licença](https://giovaniman8.gumroad.com/l/macbat) ·
[Política de Privacidade](PRIVACY.pt-BR.md) ·
[Segurança](SECURITY.pt-BR.md)

---

## O que ele faz

**O tempo restante, de volta ao lugar dele.** A Apple tirou a estimativa da
barra de menus. O MacBat traz de volta com algoritmo próprio, e mantém o número
estável em vez de pular de um extremo ao outro.

**Modo Controlado.** Seu Mac já cuida bem da própria bateria. O que ele nem
sempre cuida é de um processo em segundo plano queimando energia à toa. O
MacBat encontra esses processos e reduz o uso de CPU deles — sem mexer no
desempenho de CPU ou GPU do app que você está usando de verdade. Ele mede o
resultado na bateria e mostra quanto o seu Mac gastou a menos.

**Sentinela.** O motor por trás do modo Controlado, disponível sozinho se você
preferir manter o ícone de bateria original. Escolha quais processos ele
gerencia, ou fixe um processo nos núcleos de eficiência. Com a sua autorização,
ele também manda serviços de fundo do macOS para os núcleos de eficiência e
trava processos de outros usuários.

**Dados avançados, do seu Mac e do seu iPhone.** Carga, saúde, ciclos,
temperatura e consumo, registrados ao longo do tempo para você ver o que mudou.
Conecte um iPhone ou iPad por cabo e o MacBat acompanha a bateria dele também.
Exporte tudo em CSV.

**Insights, de dia e de noite.** O MacBat mostra o que importa sobre consumo,
saúde da bateria e processos gerenciados no próprio painel, revezando com a
lista, ao vivo, dos apps que mais gastam energia agora. No resto do tempo, sai
da frente.

**Uma interface de verdade, não mais um menu.** Pílulas em Liquid Glass que
colocam os controles que você usa embaixo do ponteiro. Clique direito abre o
menu avançado.

**Seu ícone, sua escolha.** Mais de 20 estilos de ícone de bateria, do visual
novo do macOS 27 aos clássicos, com a carga na cor do seu modo de energia.
Mostre a porcentagem dentro do ícone ou ao lado.

**Um começo guiado.** A primeira execução apresenta o Sentinela e o modo
Controlado, deixa você escolher o ícone e começa o seu teste grátis.

**Quatro idiomas.** Português, inglês, espanhol e francês. O MacBat acompanha o
idioma do sistema.

---

## Instalar

### Homebrew (oficial)

```bash
brew install --cask 1architect/macbat/macbat
```

O Homebrew é a forma oficial de instalar o MacBat.

### Download direto (alternativa)

Use esta opção só se você não pode usar o Homebrew. Baixe o
`MacBat-x.y.z.zip` mais recente em
[Releases](https://github.com/1architect/macbat-releases/releases/latest),
descompacte e arraste o **MacBat.app** para a pasta Aplicativos.

### Requisitos

- macOS 26 ou mais recente
- Apple Silicon ou Intel

### Atualizar

O MacBat nunca procura atualização sozinho. Escolha **Verificar atualizações…**
no menu quando quiser olhar, ou rode `brew upgrade --cask macbat`.

---

## Teste, depois compre

O MacBat funciona por inteiro durante **7 dias**. Depois disso, uma licença
libera o app de novo. Não há conta para criar nem assinatura — você compra uma
vez.

[**Comprar uma licença**](https://giovaniman8.gumroad.com/l/macbat)

Para ativar: abra o menu, escolha o item de licença e digite o e-mail e a chave
que vieram no e-mail da compra.

---

## Privacidade

O MacBat não tem analytics, telemetria nem relatório de falhas. Seu histórico de
bateria, sua lista de processos e os dados do seu dispositivo ficam no seu Mac.

O MacBat toca a rede exatamente duas vezes, e só quando você pede: ao procurar
atualização (um feed de versão no GitHub) e ao ativar uma licença (Gumroad, para
verificar a chave). Não faz conexão nenhuma ao abrir, nem em segundo plano.

Seus dados ficam no seu Mac, em `~/Library/Application Support/MacBat/`. O
detalhe completo — cada arquivo que ele grava, cada campo que ele envia e como o
Sentinela atua nos processos — está na [Política de Privacidade](PRIVACY.pt-BR.md)
e na [Política de Segurança](SECURITY.pt-BR.md).

---

## Permissões

Até três recursos pedem autorização de administrador na primeira vez que você
os liga — Touch ID ou senha, o que o seu Mac usar. A autorização instala uma
regra `sudoers` limitada aos comandos exatos de que precisam, e não é pedida de
novo:

| Recurso | Comandos liberados |
|---|---|
| Pouca Energia | `pmset -a lowpowermode 0` / `1` |
| Controlado | uma lista fixa de argumentos do `pmset` para sono da tela, Power Nap e acordar por rede, mais `tmutil enable` / `disable` |
| Sentinela, processos do sistema (opcional) | `kill -STOP` / `-CONT` (travar e liberar — nunca encerrar) e `taskpolicy -b` / `-B -p` (núcleos de eficiência, liga e desliga) |

Quem trata a autorização é o macOS, então o MacBat nunca vê sua senha. Ele não
instala daemon nenhum em segundo plano. Remova as regras quando quiser, apagando
`/etc/sudoers.d/macbat-economia`, `/etc/sudoers.d/macbat-lowpowermode` e
`/etc/sudoers.d/macbat-sentinela-sistema`. A regra do Sentinela também pode ser
revogada pelo cadeado da janela do Sentinela.

---

## Desinstalar

O jeito mais rápido: abra o menu, escolha **Sobre o MacBat** e depois
**Desinstalar…**. O MacBat vai para o Lixo e remove as regras de administrador.
Seus dados e a licença ficam guardados, caso você volte.

Para remover tudo à mão:

1. Feche o MacBat. Desligue **Controlado** e **Pouca Energia** antes, para os ajustes de sistema voltarem.
2. Remova o app: `brew uninstall --cask macbat`, ou arraste o **MacBat.app** para o Lixo.
3. Remova os dados e as preferências:
   ```bash
   rm -rf ~/Library/Application\ Support/MacBat
   defaults delete com.giovanimanto.macbat
   ```
4. Remova as regras de administrador, só se você ligou Pouca Energia, Controlado ou o controle de processos do sistema do Sentinela:
   ```bash
   sudo rm -f /etc/sudoers.d/macbat-economia /etc/sudoers.d/macbat-lowpowermode /etc/sudoers.d/macbat-sentinela-sistema
   ```
5. Se o ícone de bateria nativo estiver escondido, reative-o em **Ajustes do Sistema → Central de Controle → Bateria**.

Depois disso, nenhum arquivo do MacBat fica no seu Mac.

---

## Suporte

**macbat@giomantovani.com.br**

---

## Licença

O MacBat é software proprietário. Copyright © 2026 Gio Mantovani / 1architect.
Todos os direitos reservados. O código-fonte não é público.

Este repositório guarda as releases públicas, o feed de atualização e os
documentos acima. Veja a [LICENSE.pt-BR.md](LICENSE.pt-BR.md) para os termos completos.
