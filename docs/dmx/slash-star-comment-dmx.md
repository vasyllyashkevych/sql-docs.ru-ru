---
description: Косая черта (комментарий) (расширения интеллектуального анализа данных)
title: Косая черта (комментарий) (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 011d72bfcb0b72d1b73579e81dc6f82e4d50da69
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500876"
---
# <a name="slash-star-comment-dmx"></a>Косая черта (комментарий) (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Указывает строку текста, которая не должна выполняться службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Сервер не вычисляет текст между символами комментария/* и \* /. Комментарии внутри инструкции языка расширений интеллектуального анализа данных могут быть вложенными, их можно включать в конце строки кода или вставлять отдельной строкой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
/* Comment_Text */  
```  
  
#### <a name="parameters"></a>Параметры  
 *Comment_Text*  
 Строка, содержащая текст комментария.  
  
## <a name="remarks"></a>Комментарии  
 Многострочные комментарии необходимо отмечать сочетаниями символов /* и \*/.  
  
 Длина комментариев не ограничена.  
  
 Дополнительные сведения об использовании различных типов комментариев в расширениях интеллектуального анализа данных см. в разделе [комментарии &#40;dmx&#41;](../dmx/comments-dmx.md).  
  
## <a name="see-also"></a>См. также  
 [Двойная косая черта &#40;комментарий&#41; &#40;DMX&#41;](../dmx/double-slash-comment-dmx.md)   
 [--&#40;комментарий&#41; &#40;&#41; сводные данные расширений интеллектуального анализа данных](../dmx/comment-dmx-summary.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных ](../dmx/operators-dmx.md)  
  
  
