---
description: sys.service_contract_usages (Transact-SQL)
title: sys. service_contract_usages (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- service_contract_usages
- sys.service_contract_usages
- sys.service_contract_usages_TSQL
- service_contract_usages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.service_contract_usages catalog view
ms.assetid: 20af425e-1152-4a46-b1ac-94cff5fc9f02
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 1b44ee215023a33cb27c73e16933bfafd9839703
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89539555"
---
# <a name="sysservice_contract_usages-transact-sql"></a>sys.service_contract_usages (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Это представление каталога содержит строку для пары (служба, контракт).  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**service_id**|**int**|Идентификатор службы, использующей контракт. Не допускает значения NULL.|  
|**service_contract_id**|**int**|Идентификатор контракта, используемого службой. Не допускает значения NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
