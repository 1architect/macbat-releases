[English](PRIVACY.md) · **Português** · [Español](PRIVACY.es.md) · [Français](PRIVACY.fr.md)

# Política de Privacidade — MacBat

**Última atualização: 14 de agosto de 2026 · Vale para o MacBat 1.0.0 em diante**

O MacBat não coleta, não armazena e não transmite nenhum dado de uso. Não há
analytics, telemetria, relatório de falhas nem publicidade. O MacBat não tem
sistema de contas: você nunca cria um perfil nem faz login.

Este documento descreve exatamente o que o MacBat lê, onde ele guarda, e os
dois únicos momentos em que ele usa a rede.

---

## O que fica no seu Mac

O MacBat lê dados de bateria e energia e grava na sua própria máquina. Nada
disso sai do seu Mac.

| Dado | Onde fica guardado |
|---|---|
| Histórico de bateria do seu Mac — carga, saúde, ciclos, temperatura, consumo | `~/Library/Application Support/MacBat/` |
| Histórico de bateria de um iPhone ou iPad conectado | `~/Library/Application Support/MacBat/` |
| Nome e consumo dos processos que o Sentinela gerencia | Em memória, e num registro local na mesma pasta |
| Seus ajustes e as datas do período de teste | Preferências do macOS (`UserDefaults`) do MacBat |
| Seu recibo de licença — e-mail, ID do produto, data de ativação | `~/Library/Application Support/MacBat/license-receipt.json` |

Você pode apagar tudo quando quiser. Remova a pasta `MacBat` de
`~/Library/Application Support/` e o app volta ao estado inicial.

A exportação em CSV grava no local que você escolher. O MacBat nunca envia esse
arquivo para lugar nenhum.

### iPhone e iPad conectados

O MacBat lê o estado da bateria de um dispositivo iOS que você conecta por
cabo. Ele conversa com o dispositivo pelo `usbmuxd`, o serviço local do macOS
que o Finder também usa, através de um socket Unix no seu Mac. **A conexão
nunca sai da sua máquina.** O MacBat não lê suas mensagens, fotos, contatos,
backups nem qualquer outro conteúdo do dispositivo — só o estado da bateria.

---

## Quando o MacBat usa a rede

O MacBat faz conexão de rede em duas situações, só. **As duas acontecem porque
você pediu.** O MacBat não faz conexão nenhuma ao abrir, nem em segundo plano.

### 1. Quando você procura atualizações

A verificação automática está desligada. O MacBat só acessa a rede quando você
escolhe **Verificar atualizações…** no menu. Aí ele pede um arquivo de versão
ao GitHub:

```
https://raw.githubusercontent.com/1architect/macbat-releases/refs/heads/main/appcast.xml
```

Como em qualquer requisição web, o GitHub enxerga o seu endereço IP e a versão
do MacBat que está perguntando. O MacBat não envia perfil de sistema, nem
informação de hardware, nem identificador de espécie alguma. O tratamento que o
GitHub dá a essa requisição está na
[Declaração de Privacidade do GitHub](https://docs.github.com/site-policy/privacy-policies/github-privacy-statement).

### 2. Quando você ativa sua licença

Quando você digita a chave de licença, o MacBat envia uma requisição à Gumroad,
a loja que processa as compras do MacBat:

```
POST https://api.gumroad.com/v2/licenses/verify
```

Essa requisição leva três campos, e mais nada:

- o ID do produto MacBat
- a chave de licença que você digitou
- um sinalizador que conta a ativação

**O e-mail que você digita não é enviado.** O MacBat compara o endereço no seu
próprio Mac com o que a Gumroad devolve para aquela chave. Seu e-mail fica na
sua máquina.

A compra em si — nome, e-mail, dados de pagamento — é tratada pela Gumroad, não
pelo MacBat. Consulte a [Política de Privacidade da Gumroad](https://gumroad.com/privacy)
para saber o que eles guardam e por quanto tempo.

---

## O que o MacBat nunca faz

- Nunca envia seu histórico de bateria, sua lista de processos ou os dados do seu dispositivo para lugar nenhum.
- Nunca lê arquivos fora da própria pasta, salvo o que você apontar.
- Nunca roda um serviço em segundo plano nem um daemon auxiliar privilegiado.
- Não exige acesso root para funcionar.

### Sobre a autorização de administrador

Dois recursos pedem autorização de administrador na primeira vez que você os
liga: **Pouca Energia** e **Controlado**. Quem mostra o pedido é o macOS — Touch
ID ou senha, o que o seu Mac usar — e **o MacBat nunca vê a senha**. A
autorização instala uma regra `sudoers` limitada aos comandos exatos de que o
recurso precisa, uma lista curta e fixa de argumentos do `pmset` e do `tmutil`,
e não é pedida de novo. A regra não libera nada além desses comandos. Você pode remover as regras apagando
`/etc/sudoers.d/macbat-economia` e `/etc/sudoers.d/macbat-lowpowermode`.

---

## Crianças

O MacBat é um utilitário para macOS e não se destina a crianças. Ele não coleta
informação pessoal de ninguém, de nenhuma idade.

## Mudanças nesta política

Se o comportamento do MacBat mudar, este documento muda junto, e a data no topo
muda também. O histórico deste arquivo é público neste repositório: dá para ver
exatamente o que mudou e quando.

## Contato

Dúvidas sobre privacidade, ou sobre qualquer ponto deste documento:

**macbat@giomantovani.com.br**
