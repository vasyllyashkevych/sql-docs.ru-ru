---
description: sp_delete_jobserver (Transact-SQL)
title: sp_delete_jobserver (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_jobserver
- sp_delete_jobserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_jobserver
ms.assetid: 6d63ed32-68cf-4d8f-aa40-05a3826e05b8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 4db36a6fbcf09ca6758fd3838ab489bc6aa23cb2
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546155"
---
# <a name="sp_delete_jobserver-transact-sql"></a>sp_delete_jobserver (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет указанный целевой сервер.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_delete_jobserver { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ,   
     [ @server_name = ] 'server'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @job_id = ] job_id` Идентификационный номер задания, из которого будет удален указанный целевой сервер. *job_id* имеет тип **uniqueidentifier**и значение по умолчанию NULL.  
  
`[ @job_name = ] 'job_name'` Имя задания, из которого будет удален указанный целевой сервер. Аргумент *job_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  Необходимо указать либо *job_id* , либо *job_name* . нельзя указывать оба значения.  
  
`[ @server_name = ] 'server'` Имя целевого сервера, который необходимо удалить из указанного задания. *Server* имеет тип **nvarchar (30)** и не имеет значения по умолчанию. *сервер* может быть **(локальным)** или именем удаленного целевого сервера.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой хранимой процедуры пользователи должны быть членами предопределенной роли сервера **sysadmin** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере сервер удаляется `SEATTLE2` из обработки `Weekly Sales Backups` задания.  
  
> [!NOTE]  
>  В этом примере предполагается, что ранее было создано задание `Weekly Sales Backups`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_delete_jobserver  
    @job_name = N'Weekly Sales Backups',  
    @server_name = N'SEATTLE2' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_add_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql.md)   
 [sp_help_jobserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-jobserver-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
