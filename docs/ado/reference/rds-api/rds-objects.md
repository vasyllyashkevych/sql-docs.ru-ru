---
description: Объекты службы удаленных рабочих столов
title: Объекты RDS | Документация Майкрософт
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
helpviewer_keywords:
- objects [ADO], RDS
- RDS objects [ADO]
ms.assetid: f2ac8b3b-f968-41c4-a504-7aee3538b7c7
author: rothja
ms.author: jroth
ms.openlocfilehash: fa9329b1da84643f75a83ee1487f8c1be47601b1
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91724345"
---
# <a name="rds-objects"></a>Объекты службы удаленных рабочих столов
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](/dotnet/framework/wcf/).  
  
|Объект|Описание|  
|-|-|  
|[Элемент управления (RDS)](./datacontrol-object-rds.md)|Привязывает **набор записей** запроса данных к одному или нескольким элементам управления (например, текстовому полю, элементу управления сетки или полю со списком) для вывода данных **набора записей** на веб-странице.<br /><br /> Объект " **элемент управления** " является надежным для сценариев.|  
|[Факт (RDSServer)](./datafactory-object-rdsserver.md)|Реализует методы, предоставляющие доступ к данным для чтения и записи к указанным источникам данных для клиентских приложений.<br /><br /> Объект **фактов** не является надежным для сценариев.|  
|[Пространство (RDS)](./dataspace-object-rds.md)|Создает прокси на стороне клиента для пользовательских бизнес-объектов, расположенных на среднем уровне.<br /><br /> Объект **Space** является надежным для скриптов.|  
|[Интерфейс IRDSService (служба удаленных рабочих столов)](./irdsservice-interface-rds.md)|Предоставляет метод [инвокесервице (RDS)](./invokeservice-rds.md) , который используется для возвращения указателя на запрошенный интерфейс в более поддерживающей версии объекта.|  
  
## <a name="see-also"></a>См. также  
 [Справочник по API ADO](./rds-api-reference.md)