---
description: Свойство CursorLocation (ADO)
title: Свойство CursorLocation (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::CursorLocation
- Recordset15::CursorLocation
helpviewer_keywords:
- CursorLocation property [ADO]
ms.assetid: 39c8d86e-7ee9-4182-be5e-aad5ce952f84
author: rothja
ms.author: jroth
ms.openlocfilehash: 121aeef137946152a82808c8a439f2e5d03a2c94
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88974465"
---
# <a name="cursorlocation-property-ado"></a>Свойство CursorLocation (ADO)
Указывает расположение службы курсора.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Long** , которое можно задать для одного из значений [курсорлокатионенум](./cursorlocationenum.md) .  
  
## <a name="remarks"></a>Remarks  
 Это свойство позволяет выбрать между различными библиотеками курсоров, доступными для поставщика. Обычно можно выбрать одну из них, используя библиотеку курсоров на стороне клиента или ту, которая находится на сервере.  
  
 Этот параметр свойства влияет на соединения, установленные только после установки свойства. Изменение свойства **CursorLocation** не влияет на существующие соединения.  
  
 Курсоры, возвращаемые методом [EXECUTE](./execute-method-ado-connection.md) , наследуют этот параметр. Объекты **набора записей** будут автоматически наследовать этот параметр от связанных соединений.  
  
 Это свойство доступно для чтения и записи в [соединении](./connection-object-ado.md) или закрытом [наборе записей](./recordset-object-ado.md)и доступно только для чтения в открытом **наборе записей**.  
  
> [!NOTE]
>  **Использование удаленной службы данных** При использовании **набора записей** или объекта **соединения** на стороне клиента свойство **CursorLocation** может иметь только значение **адусеклиент**.  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Connection (ADO)](./connection-object-ado.md)  
    :::column-end:::
    :::column:::
        [Объект Recordset (ADO)](./recordset-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Приложение А. Поставщики](../../guide/appendixes/appendix-a-providers.md)