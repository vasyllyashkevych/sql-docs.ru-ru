---
description: sp_repltrans (Transact-SQL)
title: sp_repltrans (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_repltrans_TSQL
- sp_repltrans
helpviewer_keywords:
- sp_repltrans
ms.assetid: 738e2322-335b-44fa-820e-f31c02743978
author: markingmyname
ms.author: maghan
ms.openlocfilehash: f8808b5955e18e56d9c49f8ce315a5f201c7837e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534909"
---
# <a name="sp_repltrans-transact-sql"></a>sp_repltrans (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Возвращает результирующий набор всех транзакций из журнала транзакций базы данных публикации, которые помечены для репликации, но не были помечены как распространенные. Эта хранимая процедура выполняется в базе данных публикаций на сервере издателя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_repltrans  
```  
  
## <a name="result-sets"></a>Результирующие наборы  
 **sp_repltrans** возвращает сведения о базе данных публикации, из которой она выполняется, позволяя просматривать нераспределенные транзакции (транзакции, оставшиеся в журнале транзакций, которые не были отправлены распространителю). Результирующий набор отображает регистрационный номер транзакций в журнале для первой и последней записи по каждой транзакции. **sp_repltrans** похож на [sp_replcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replcmds-transact-sql.md) , но не возвращает команды для транзакций.  
  
## <a name="remarks"></a>Примечания  
 **sp_repltrans** используется в репликации транзакций.  
  
 **sp_repltrans** не поддерживается для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей, отличных от.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_repltrans**.  
  
## <a name="see-also"></a>См. также  
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
