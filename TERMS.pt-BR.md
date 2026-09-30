[English](TERMS.md) · **Português** · [Español](TERMS.es.md) · [Français](TERMS.fr.md)

# Termos de Serviço — MacBat

**Última atualização: 30 de setembro de 2026 · Vale para o MacBat 1.0.0 em diante**

Estes termos regem o uso do MacBat, o app de barra de menus para macOS
publicado por Gio Mantovani / 1architect ("nós"), de seu site e de seu
repositório público de versões. Ao instalar ou usar o MacBat, você concorda com
eles. Se não concordar, não instale nem use o MacBat.

---

## 1. A licença

O MacBat é software proprietário. Seu direito de uso está na
[Licença Proprietária do MacBat](LICENSE.pt-BR.md): um direito pessoal,
limitado, revogável, não exclusivo e intransferível de instalar e usar o
MacBat. Estes termos complementam a licença; em caso de conflito, a licença
prevalece sobre propriedade intelectual e estes termos prevalecem sobre todo o
resto.

## 2. Recursos gratuitos, teste e licença paga

- **Teste.** Toda instalação nova inclui 7 dias de teste grátis com todos os
  recursos liberados.
- **Depois do teste,** o ícone na barra de menus, a porcentagem e o tempo
  restante continuam grátis. O Sentinela, o modo Controlado, os Dados da
  Bateria e os ícones extras exigem licença.
- **Licença.** A licença é uma compra única, não uma assinatura. Ela é ativada
  com a chave que você recebe do Gumroad e vale para até **3 ativações**. Não
  compartilhe, revenda nem publique sua chave.
- **Compras e reembolsos.** As compras são processadas pelo Gumroad, que é o
  vendedor responsável pelo pagamento. Pagamento, impostos e reembolsos seguem
  os termos do Gumroad e os direitos do consumidor do lugar onde você mora.
  Dúvidas sobre uma compra: macbat@giomantovani.com.br.
- Podemos mudar preços e quais recursos são gratuitos ou pagos em versões
  futuras. Uma mudança nunca retira de uma licença já comprada um recurso da
  versão com a qual ela foi comprada.

## 3. O que o MacBat faz no seu Mac

O MacBat é um utilitário que lê dados de energia e, quando você liga o recurso,
muda o comportamento do seu Mac. Você precisa saber exatamente o que isso
significa:

- **O Sentinela** pausa e retoma processos, ou os move para os núcleos de
  eficiência, para reduzir o uso de CPU. Um processo pausado de forma agressiva
  demais pode ficar lento, parar de responder ou perder trabalho não salvo. Você
  escolhe quais processos ele controla e pode desligá-lo a qualquer momento.
- **O modo Controlado e o modo Pouca Energia** alteram ajustes de energia do
  sistema (`pmset`), e o Controlado os restaura quando você o desliga.
- **O controle de processos do sistema** (opcional) permite que o Sentinela aja
  em processos de outros usuários e em serviços de segundo plano do macOS. Use
  só se entender os processos que está afetando.
- **Autorização de administrador.** Esses recursos pedem uma vez o Touch ID ou
  a senha, pelo próprio macOS. O MacBat nunca vê a senha. Ele instala regras de
  `sudoers` limitadas aos comandos exatos de cada recurso, que você pode
  remover a qualquer momento, como descrito na
  [Política de Privacidade](PRIVACY.pt-BR.md).
- **Os dados de bateria e de dispositivos** vêm de interfaces do macOS, algumas
  não documentadas pela Apple e que podem mudar a cada atualização. O tempo
  restante, a saúde e outras leituras são **estimativas** e podem estar erradas.
  Não dependa do MacBat para nada crítico para a segurança.
- A leitura de um iPhone ou iPad conectado usa o serviço local `usbmuxd` e lê
  somente o estado da bateria.

## 4. Uso aceitável

Você concorda em não: copiar, modificar, redistribuir, alugar ou revender o
MacBat; tentar fazer engenharia reversa, salvo onde a lei permitir; burlar,
adulterar ou compartilhar o mecanismo de teste ou de licença; ou usar o MacBat
para interferir em computadores ou dados que não sejam seus ou que você não
tenha autorização para gerenciar.

## 5. Atualizações

O MacBat não procura atualizações sozinho. Você decide quando usar **Verificar
Atualizações…** ou `brew upgrade --cask macbat`. Não prometemos um calendário de
versões, e as correções de segurança entram só na versão mais recente (veja
[Segurança](SECURITY.pt-BR.md)). Cabe a você manter o MacBat compatível com a
sua versão do macOS; o MacBat exige o macOS 26 ou posterior.

## 6. Privacidade

O MacBat não coleta dados sobre você. Como ele funciona, o que fica no seu Mac e
os dois únicos momentos em que usa a rede estão na
[Política de Privacidade](PRIVACY.pt-BR.md), que faz parte destes termos.

## 7. Sem garantia

O MacBat é fornecido **"no estado em que se encontra" e "conforme
disponível"**, sem garantia de qualquer tipo, expressa ou implícita, inclusive
de adequação a uma finalidade específica, de exatidão das estimativas ou de
funcionamento ininterrupto e sem erros. Não garantimos que o MacBat vá
economizar uma quantidade específica de bateria.

## 8. Limitação de responsabilidade

Na máxima extensão permitida por lei, não respondemos por danos indiretos,
incidentais ou consequenciais, perda de dados, lucros cessantes ou danos ao seu
Mac ou a outros dispositivos decorrentes do uso ou da impossibilidade de uso do
MacBat. Nossa responsabilidade total por qualquer reclamação se limita ao valor
que você pagou pela licença do MacBat. Nada nestes termos limita a
responsabilidade que a lei não permite limitar, nem os direitos do consumidor
que são obrigatórios.

## 9. Encerramento

Você pode deixar de usar o MacBat a qualquer momento, apagando-o e, se quiser,
removendo seus dados e as regras de `sudoers`. Podemos revogar uma licença usada
em violação a estes termos, por exemplo uma compartilhada ou revendida, ou
obtida por estorno ou pagamento fraudulento. No encerramento, você deve parar de
usar o MacBat e apagar suas cópias.

## 10. Mudanças nestes termos

Se mudarmos estes termos, este documento muda junto e a data no topo também. O
histórico deste arquivo é público neste repositório. Continuar a usar o MacBat
depois de uma mudança significa que você aceita os novos termos.

## 11. Lei aplicável

Estes termos são regidos pelas leis do Brasil, sem considerar suas regras de
conflito de leis. As regras obrigatórias de proteção ao consumidor do país onde
você mora continuam valendo para você. Qualquer disputa pode ser levada ao foro
em que você puder demandar segundo essas regras e, fora isso, aos tribunais do
Brasil.

## 12. Contato

Dúvidas sobre estes termos ou pedidos de autorização:

**macbat@giomantovani.com.br**

O texto em inglês é a versão de referência em caso de divergência entre as
traduções.
