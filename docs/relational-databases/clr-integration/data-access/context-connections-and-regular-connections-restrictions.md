---
title: Ограничения для обычных и контекстных подключений | Документация Майкрософт
description: В этой статье описываются ограничения, связанные с кодом, выполняемым в Microsoft SQL Server процессом через контекст и обычные соединения.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- context connections [CLR integration]
- regular connections [CLR integration]
ms.assetid: 0c6fe4cb-d846-40b5-8884-35a9c770f5e8
author: rothja
ms.author: jroth
ms.openlocfilehash: 17f95da5b152dd73939dcdf8552f72c20f199f20
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85882188"
---
# <a name="context-connections-and-regular-connections---restrictions"></a>Контекстные соединения и обычные соединения — ограничения
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  В этом разделе обсуждаются ограничения, связанные с кодом, который выполняется в [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] процессе через контекст и обычные соединения.  
  
## <a name="restrictions-on-context-connections"></a>Ограничения контекстных соединений  
 При проектировании приложения учитывайте следующие ограничения, которые применяются к контекстным соединениям.  
  
-   В определенное время для заданного соединения может существовать только одно открытое контекстное соединение. Если имеется несколько инструкций, параллельно выполняемых в отдельных соединениях, каждая из них может иметь собственное контекстное соединение. Ограничение не влияет на параллельные запросы из различных соединений, оно влияет только на конкретный запрос в отдельном соединении.  
  
-   Режим MARS не поддерживается в контекстных соединениях.  
  
-   Класс **SqlBulkCopy** не работает в контекстных соединениях.  
  
-   Пакетное обновление не поддерживается в контекстных соединениях.  
  
-   **SqlNotificationRequest** нельзя использовать с командами, применяемыми в контекстном соединении.  
  
-   Отмена команд, применяемых в контекстном соединении, не поддерживается. Метод **SqlCommand.Cancel** не учитывает запрос, не сообщая об этом.  
  
-   Никакие другие ключевые слова строки соединения не могут использоваться при использовании «context connection=true».  
  
-   Класс **SqlConnectionравна «context connection=true».DataSource** возвращает вместо имени экземпляра **SqlConnection** значение NULL, если строка соединения для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]равна «context connection=true».  
  
-   Установка свойства **SqlCommand.CommandTimeout** не имеет значения, если команда выполняется в контекстном соединении.  
  
## <a name="restrictions-on-regular-connections"></a>Ограничения обычных соединений  
 При проектировании приложения учитывайте следующие ограничения, которые применяются к обычным соединениям.  
  
-   Асинхронное применение команд к внутренним серверам не поддерживается. Если в строке соединения содержится «async=true», по при последующем выполнении команды возникает исключение **System.NotSupportedException** . Отображается сообщение: «Асинхронная обработка не поддерживается при выполнении в процессе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ».  
  
-   Объект**SqlDependency** не поддерживается.  
  
## <a name="see-also"></a>См. также  
 [Контекстное соединение](../../../relational-databases/clr-integration/data-access/context-connection.md)  
  
  
