﻿---
title: 'Globais atualizações necessárias: Exchange 2013 Help'
TOCTitle: Globais atualizações necessárias
ms:assetid: 0530f3c6-6fa6-456b-a33a-f3d2f7eaa2ef
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/ms.exch.setupreadiness.globalupdaterequired(v=EXCHG.150)
ms:contentKeyID: 50484898
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Globais atualizações necessárias

 

_**Aplica-se a:**Exchange Server_

_**Tópico modificado em:**2014-12-02_

Microsoft Exchange Server 2013 a instalação não pode continuar porque o usuário conectado não tem as permissões de conta necessárias para atualizá-las globais do Active Directory.

A Instalação exige que o usuário conectado durante a instalação do Exchange 2013 tenha permissão para criar e modificar objetos no Active Directory. Se você estiver executando pela primeira vez a Instalação do Exchange 2013 em sua organização, a conta que você usa deve ser membro dos grupos Administradores de Esquema e Administradores Empresariais. Essas permissões são necessárias porque o Active Directory é preparado para o Exchange 2013 na primeira vez que a Instalação é executada. Após a preparação do Active Directory, a conta que você usar para instalar servidores adicionais do Exchange 2013 devem ser membros do grupo de função de gerenciamento chamada Gerenciamento de Organização.

Para resolver esse problema, conceda ao usuário conectado as permissões apropriadas ou faça logon com uma conta que tenha essas permissões e execute a Instalação do Exchange 2013 novamente.


> [!IMPORTANT]
> A instalação entre florestas do Exchange 2013 não tem suporte. Use uma conta que não seja membro da floresta do Active Directory em que você está instalando o Exchange 2013.



Está enfrentando problemas? Peça ajuda nos fóruns do Exchange. Visite os fóruns em: [Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=60612), [Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=267542), ou [Proteção do Exchange Online](https://go.microsoft.com/fwlink/p/?linkid=285351).

Você encontrou o que você está procurando? Por favor, separe um minuto do seu tempo para [enviar seus comentários para nós](mailto:exsetuphelpfeedback@microsoft.com?subject=exchange%202013%20setup%20help%20feedback) sobre as informações que você estava esperando encontrar.

