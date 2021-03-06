---
title: Отладка обработчика бизнес-логики (программирование репликации)
description: Узнайте, как использовать обработчик бизнес-логики для вызова пользовательской бизнес-логики во время синхронизации подписки на публикацию слиянием.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- merge replication business logic handlers [SQL Server replication]
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: edd0d17a-0e9c-4c28-8395-a7d47e8ce3d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 66e0df2599b8ada5f1c7dc3018e8021e2ee03df7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85654051"
---
# <a name="debug-a-business-logic-handler-replication-programming"></a>выполнить отладку обработчика бизнес-логики (программирование репликации)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Используйте обработчик бизнес-логики для вызова пользовательской бизнес-логики во время синхронизации подписки на публикацию слиянием. Дополнительные сведения см. в статье [Выполнение бизнес-логики при синхронизации слиянием](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md).  
  
 Посредник репликации слиянием (replrec.dll) осуществляет вызов сборки управляемого кода, содержащей бизнес-логику. В большинстве случаев файл replrec.dll и пользовательская бизнес-логика выполняются на компьютере с запущенным агентом слияния (на сервере подписчика для подписки по запросу или на сервере распространителя для принудительной подписки). При веб-синхронизации или для подписчика [!INCLUDE[ssEW](../../includes/ssew-md.md)] посредник и пользовательская бизнес-логика выполняются на веб-сервере.  
  
### <a name="to-debug-a-business-logic-handler-on-a-local-computer"></a>Отладка обработчика бизнес-логики на локальном компьютере  
  
1.  Настройте публикацию и распространение, создайте новую публикацию, а затем подписку на нее. Дополнительные сведения см. в статьях [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md) и [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md).  
  
2.  Создайте и зарегистрируйте обработчик бизнес-логики. Дополнительные сведения см. в статье [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
3.  В среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio создайте проект объектов RMO, который программным путем производит синхронный запуск агента слияния. Дополнительные сведения см. в статье [Synchronize a Pull Subscription](../../relational-databases/replication/synchronize-a-pull-subscription.md).  
  
4.  Установите точку останова в коде обработчика бизнес-логики — в методе, проходящем отладку, или в конструкторе класса. Дополнительные сведения о методах, которые можно реализовать в обработчике бизнес-логики, см. в разделе о методах <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> .  
  
5.  Откройте обработчик бизнес-логики в режиме отладки и произведите развертывание сборки и файла отладки (PDB) в папке, заданной на шаге 1.  
  
    > [!NOTE]  
    >  Чтобы упростить процесс отладки, создайте решение Visual Studio .NET, содержащее проект обработчика бизнес-логики и проект, осуществляющий синхронизацию подписки. В данном случае проект синхронизации должен быть задан как стартовый, а среда разработки должна быть настроена для развертывания сборки бизнес-логики в папку, которая была задана на шаге 1.  
  
6.  Выполните команды вставки, обновления или удаления в базе данных подписки или публикации. Используемая команда и место выполнения зависят от метода, проходящего отладку.  
  
7.  Чтобы синхронизировать подписку, запустите проект в режиме отладки, начиная с шага 3.  
  
8.  Если не заданы другие точки останова и репликацию проходят нужные команды, выполнение будет остановлено по достижении точки останова в обработчике бизнес-логики.  
  
### <a name="to-debug-a-business-logic-handler-on-a-web-server-using-web-synchronization-or-for-a-sql-server-compact-subscriber"></a>Отладка обработчика бизнес-логики на веб-сервере в режиме веб-синхронизации либо при использовании подписчика SQL Server Compact  
  
1.  Настройте публикацию и распространение, создайте публикацию по запросу и подписку на нее. Публикация должна поддерживать веб-синхронизации или подписчиков [!INCLUDE[ssEW](../../includes/ssew-md.md)] .  
  
2.  Создайте и зарегистрируйте обработчик бизнес-логики. Дополнительные сведения см. в статье [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md).  
  
3.  Установите точку останова в коде обработчика бизнес-логики — в методе, проходящем отладку, или в конструкторе класса. Дополнительные сведения о методах, которые можно реализовать в обработчике бизнес-логики, см. в разделе о методах <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> .  
  
4.  Откройте обработчик бизнес-логики в режиме отладки и произведите развертывание сборки и файла отладки (PDB) на сервере, заданном на шаге 1.  
  
    > [!NOTE]  
    >  В том случае, если построение обработчика бизнес-логики завершилось ошибкой по причине того, что сборка занята, необходимо перезагрузить веб-сервер командой `iisreset` из командной строки.  
  
5.  Произведите синхронизацию подписки в режиме веб-синхронизации. В процессе ее выполнения веб-сервер загрузит зарегистрированную сборку.  
  
6.  С помощью отладчика Visual Studio .NET подключитесь к одному из следующих процессов на веб-сервере.  
  
    -   w3wp.exe — Windows Server 2003.  
  
    -   inetinfo.exe — Windows 2000 и Windows XP.  
  
7.  В окне **Выход** проверьте режим отладки выходного столбца и убедитесь, что символы зарегистрированной сборки были загружены правильно. В том случае, если символы не загружены, убедитесь, что PDB-файл на шаге 4 был скопирован правильно, после чего повторите шаг 5.  
  
8.  Выполните команды вставки, обновления или удаления в базе данных подписки или публикации. Используемая команда и место выполнения зависят от метода, проходящего отладку.  
  
9. В среде Visual Studio подключитесь к процессу w3wp.exe.  
  
10. Произведите повторную синхронизацию подписки в режиме веб-синхронизации.  
  
11. Если не заданы другие точки останова и репликацию проходят нужные команды, выполнение будет остановлено по достижении точки останова в обработчике бизнес-логики.  
  
## <a name="see-also"></a>См. также:  
 [Реализация обработчика бизнес-логики для статьи публикации слиянием](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
