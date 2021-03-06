---
description: Свойство NumericScale (ADO)
title: Свойство NumericScale (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
author: rothja
ms.author: jroth
ms.openlocfilehash: 120d88e82f77af622de962ac306442625487ff08
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88990415"
---
# <a name="numericscale-property-ado"></a>Свойство NumericScale (ADO)
Указывает масштаб числовых значений в объекте [параметра](./parameter-object.md) или [поля](./field-object.md) .  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Задает или возвращает значение **типа Byte** , указывающее количество десятичных разрядов, к которым будут разрешены числовые значения.  
  
## <a name="remarks"></a>Remarks  
 Используйте свойство **NumericScale** , чтобы определить, сколько цифр справа от десятичной запятой будет использоваться для представления значений числового **параметра** или объекта **поля** .  
  
 Для объектов **параметров** свойство **NumericScale** доступно для чтения и записи.  
  
 Для объекта **field** **NumericScale** обычно доступен только для чтения. Однако для новых объектов **field** , добавленных к коллекции [Fields](./fields-collection-ado.md) [записи](./record-object-ado.md), **NumericScale** доступен только для чтения и записи только после того, как было указано свойство [value](./value-property-ado.md) для **поля** и поставщик данных успешно добавил новое **поле** , вызвав метод [Update](./update-method.md) коллекции [Fields](./fields-collection-ado.md) .  
  
## <a name="applies-to"></a>Применение  

:::row:::
    :::column:::
        [Объект Field](./field-object.md)  
    :::column-end:::
    :::column:::
        [Объект Parameter](./parameter-object.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>См. также  
 [Пример свойств NumericScale и Precision (Visual Basic)](./numericscale-and-precision-properties-example-vb.md)   
 [Пример свойств NumericScale и Precision (Visual c++)](./numericscale-and-precision-properties-example-vc.md)   
 [Свойство Precision (ADO)](./precision-property-ado.md)