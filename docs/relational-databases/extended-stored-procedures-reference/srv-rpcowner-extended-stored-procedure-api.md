---
title: srv_rpcowner (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
description: Узнайте, как srv_rpcowner в API расширенных хранимых процедур Возвращает компонент-владелец для текущей удаленной хранимой процедуры.
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_rpcowner
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_rpcowner
ms.assetid: e81a60e6-14ea-47bc-a11c-3d7635344447
author: rothja
ms.author: jroth
ms.openlocfilehash: 64e9fa0970367ccac5d4fca5bf6b9815ad0e0e17
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87248273"
---
# <a name="srv_rpcowner-extended-stored-procedure-api"></a>srv_rpcowner (API-интерфейс расширенных хранимых процедур)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Используйте вместо этого интеграцию со средой CLR.  
  
 Возвращает компонент владельца для текущей удаленной хранимой процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DBCHAR * srv_rpcowner (  
SRV_PROC *  
srvproc  
,  
int *  
len   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, получивший удаленную хранимую процедуру). Структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *len*  
 Указатель на целочисленную переменную, получающую значение длины имени владельца. Параметр *len* может быть пустым; в этом случае длина компонента владельца не возвращается.  
  
## <a name="returns"></a>Результаты  
 Указатель DBCHAR на оканчивающийся нулевым байтом компонент владельца для текущей удаленной хранимой процедуры. Если текущей удаленной хранимой процедуры нет, возвращается значение NULL, а переменная *len* принимает значение –1.  
  
## <a name="remarks"></a>Remarks  
 Эта функция возвращает только компонент владельца удаленной хранимой процедуры. В него не входят необязательные описатели для имени, имени удаленной хранимой процедуры и номера удаленной хранимой процедуры.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).  
  
  
