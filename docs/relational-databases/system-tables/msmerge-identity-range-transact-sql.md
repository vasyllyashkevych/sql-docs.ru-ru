---
description: MSmerge_identity_range (Transact-SQL)
title: MSmerge_identity_range (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 0c473f481bc2a997d222558654ae960d4359667b
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89547122"
---
# <a name="msmerge_identity_range-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSmerge_identity_range** используется для контроля числовых диапазонов, назначенных столбцам идентификаторов для подписок на публикации, для которых репликация автоматически управляет этими назначениями диапазонов. Эта таблица хранится в базах данных публикации и подписки.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|Уникальный идентификатор данной подписки.|  
|**artid**|**uniqueidentifier**|Уникальный идентификационный номер данной статьи.|  
|**range_begin**|**numeric (38)**|Значение идентификатора в начале текущего диапазона.|  
|**range_end**|**numeric (38)**|Значение идентификатора в конце текущего диапазона.|  
|**next_range_begin**|**numeric (38)**|Значение идентификатора в начале следующего назначенного диапазона.|  
|**next_range_end**|**numeric (38)**|Значение идентификатора в конце следующего назначенного диапазона.|  
|**is_pub_range**|**bit**|Значение **1** , если диапазон идентификаторов назначен публикации.|  
|**max_used**|**numeric (38)**|Максимальное значение идентификатора, которое может быть назначено.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
