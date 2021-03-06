﻿---
title: 'Exibir e gerenciar uma regra de atendimento de chamada: Exchange 2013 Help'
TOCTitle: Exibir e gerenciar uma regra de atendimento de chamada
ms:assetid: de6d9fa1-7878-49a9-bddb-e3317d94f4d8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn140251(v=EXCHG.150)
ms:contentKeyID: 54651952
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Exibir e gerenciar uma regra de atendimento de chamada

 

_**Aplica-se a:**Exchange Server 2013, Exchange Server 2016_

_**Tópico modificado em:**2015-04-08_

Você pode usar o Shell para exibir ou configurar uma ou mais regras de atendimentos de chamadas para um usuário. Você também pode usar os cmdlets **Get-UMCallAnsweringRule** ou **Set-UMCallAnsweringRule** em um script do Shell de gerenciamento do Exchange para exibir ou gerenciar regras de atendimento para vários usuários de chamada.

Regras de atendimento de chamada são aplicadas às chamadas recebidas semelhantes à maneira como as regras de caixa de entrada são aplicadas a mensagens de email de entrada. Por padrão, quando um usuário está habilitado para Unificação de mensagens (UM), não há regras de atendimento de chamada são configuradas. Mesmo assim, as chamadas são respondidas pelo sistema de email e os chamadores for solicitados a deixar uma mensagem de voz.


> [!IMPORTANT]
> Usuários que foram habilitados para Unificação de mensagens podem entrar no Outlook Web App para criar, gerenciar e remover regras de atendimento de chamada.



Para tarefas de gerenciamento adicionais relacionadas às regras de atendimento de chamadas, consulte [Encaminhamento de chamadas de procedimentos](forwarding-calls-procedures-exchange-2013-help.md).

## O que você precisa saber antes de começar?

  - Tempo estimado para conclusão: Menos de 1 minuto.

  - Para executar este procedimento ou estes procedimentos, você precisa receber permissões. Para ver de que permissões você precisa, consulte o Entrada "regras de atendimento de chamadas de Unificação de mensagens" no tópico [Permissões de mensagens unificadas](unified-messaging-permissions-exchange-2013-help.md) .

  - Antes de executar esse procedimento, verifique se um plano de discagem de UM foi criado. Para obter etapas detalhadas, consulte [Criar um plano de discagem de UM](create-a-um-dial-plan-exchange-2013-help.md).

  - Antes de executar este procedimento, confirme se uma diretiva de caixa de correio UM foi criada. Para obter etapas detalhadas, consulte [Criar uma política de caixa de correio da UM](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Antes de executar este procedimento, confirme que a caixa de correio do usuário foi habilitado. Para obter etapas detalhadas, consulte [Habilitar um usuário para caixa postal](enable-a-user-for-voice-mail-exchange-2013-help.md).

  - Você só pode usar o Shell para executar esse procedimento. Para saber como abrir o Shell de Gerenciamento do Exchange em sua organização Exchange local, confira [Abra o shell.](https://technet.microsoft.com/pt-br/library/dd638134\(v=exchg.150\)). Para saber como usar o Windows PowerShell para se conectar ao Exchange Online, confira o artigo [Conectar-se ao Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?linkid=396554).

  - Para informações sobre atalhos de teclado que possam se aplicar aos procedimentos neste tópico, consulte [Atalhos de teclado no Centro de administração do Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Está enfrentando problemas? Peça ajuda nos fóruns do Exchange. Visite os fóruns em: <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A>, ou <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Proteção do Exchange Online</A>..



## O que você deseja fazer?

## Use o Shell para exibir uma regra de atendimento de chamada

É possível recuperar as propriedades de uma regra de atendimento de chamada único ou uma lista de regras de atendimento de chamada na caixa de correio de um usuário habilitado.

Este exemplo retorna uma lista formatada de regras de atendimento de chamadas na caixa de correio habilitada para UM de um usuário.

    Get-UMCallAnsweringRule-Mailbox tonysmith | Format-List

Este exemplo exibe as propriedades da regra `MyUMCallAnsweringRule`de atendimento de chamadas.

    Get-UMCallAnsweringRule -Identity MyUMCallAnsweringRule

## Use o Shell para configurar uma regra de atendimento de chamada

Você pode configurar ou alterar uma regra de atendimento de chamada que é armazenada na caixa de correio do usuário. Você pode especificar as seguintes condições:

  - De quem é a chamada de entrada

  - Hora do dia

  - Status de disponibilidade no calendário

  - Se respostas automáticas estão ativadas para email

Também é possível especificar as seguintes ações:

  - Encontrar-me

  - Transferir o chamador para outra pessoa

  - Deixar uma mensagem de voz

Este exemplo define a prioridade para 2 na chamada atendimento regra `MyCallAnsweringRule` que existe na caixa de correio de Tony Smith.

    Set-UMCallAnsweringRule -Mailbox tonysmith -Name MyCallAnsweringRule -Priority 2

Este exemplo executa as seguintes ações na chamada atendimento regra `MyCallAnsweringRule` na caixa de correio de Tony Smith:

  - Define a regra de atendimento de chamada para dois ID de chamadas.

  - Define a prioridade da regra de atendimento de chamada para 2.

  - Define a regra de atendimento de chamada para permitir que chamadores interrompam a saudação.

<!-- end list -->

    Set-UMCallAnsweringRule -Name MyCallAnsweringRule -CallerIds "1,4255550100,,","1,4255550123,," -Priority 2 -CallersCanInterruptGreeting $true -Mailbox tonysmith

Este exemplo altera o status livre/ocupado para ausente na chamada atendimento regra `MyCallAnsweringRule` na caixa de correio de Tony Smith e define a prioridade para 2.

    Set-UMCallAnsweringRule -Name MyCallAnsweringRule -Priority 2 -Mailbox tonysmith@contoso.com -ScheduleStatus 0x8

