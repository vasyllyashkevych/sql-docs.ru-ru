---
description: MSSQLSERVER_17084
title: MSSQLSERVER_17084 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17084 (Database Engine error)
ms.assetid: e579d104-3307-4edd-8587-b14ecbc02ed9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bf44aa95cca35e56f836306f7870bd2c2de9be7a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471116"
---
# <a name="mssqlserver_17084"></a>MSSQLSERVER_17084
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|17084|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|P3_ATOMIC_WITH_MISSING_OPTION|  
|Текст сообщения|Предложение WITH инструкции BEGIN ATOMIC должно задавать значение для параметра «%ls».|  
  
## <a name="explanation"></a>Объяснение  
Предложение WITH инструкции BEGIN ATOMIC не задает значение для параметра.  
  
## <a name="user-action"></a>Действие пользователя  
Блоки **ATOMIC** требуют значений для параметров **WITH** **TRANSACTION ISOLATION LEVEL** и **LANGUAGE**. Вот несколько примеров.  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
