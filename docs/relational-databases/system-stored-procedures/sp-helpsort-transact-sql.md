---
description: sp_helpsort (Transact-SQL)
title: sp_helpsort (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpsort_TSQL
- sp_helpsort
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpsort
ms.assetid: 2a88d079-3755-43cb-8a54-97d0114149e6
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a55c2206d8a065f0e34c68ae06f0a1bd6baee462
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538750"
---
# <a name="sp_helpsort-transact-sql"></a>sp_helpsort (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Показывает порядок сортировки и кодировку для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpsort  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Возвращает параметры сортировки по умолчанию для сервера.  
  
## <a name="remarks"></a>Примечания  
 Если экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установлен с параметрами сортировки, совместимыми с более ранней установкой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , **sp_helpsort** возвращает пустые результаты. При возникновении этого поведения можно определить параметры сортировки, запросив объект SERVERPROPERTY, например: `SELECT SERVERPROPERTY ('Collation');` .  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="examples"></a>Примеры  
 Следующий пример отображает имя порядка сортировки по умолчанию сервера, его кодировку и основные значения сортировки.  
  
```  
sp_helpsort;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Server default collation`  
  
 `------------------------`  
  
 `Latin1-General, case-sensitive, accent-sensitive, kanatype-insensitive, width-insensitive for Unicode Data, SQL Server Sort Order 51 on Code Page 1252 for non-Unicode Data.`  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [COLLATE (Transact-SQL)](~/t-sql/statements/collations.md)   
 [sys.fn_helpcollations (Transact-SQL)](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)   
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  
