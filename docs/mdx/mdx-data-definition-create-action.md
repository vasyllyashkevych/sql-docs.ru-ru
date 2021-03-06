---
description: Определение данных многомерных выражений — CREATE ACTION
title: Инструкция CREATE ACTION (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7132c28e93dbc11eee1c5a4e4d53126f280fa74a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494907"
---
# <a name="mdx-data-definition---create-action"></a>Определение данных многомерных выражений — CREATE ACTION


  Создает действие, которое можно связать с кубом, измерением, иерархией или подчиненным объектом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE ACTION CURRENTCUBE | Cube_Name  
   .Action_Name <action body>  
<action body> ::=   
FOR   
        CUBE   
    | Hierarchy_Name [MEMBERS]   
    | Level_Name [MEMBERS]   
    | CELLS   
    | SET }   
      AS 'MDX_Expression'   
        [, TYPE = '  
              { URL   
            | HTML   
            | STATEMENT   
               | DATASET   
            | ROWSET   
            | COMMANDLINE   
               | PROPRIETARY }   
         ']  
   [ , INVOCATION = 'INTERACTIVE | ON_OPEN | BATCH ' ]  
   [ , APPLICATION = String_Expression ]  
   [ , DESCRIPTION = String_Expression ]  
   [ , CAPTION = 'MDX_Expression' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимая строка, представляющая имя куба.  
  
 *Имя Action_*  
 Допустимая строка, представляющая имя создаваемого действия.  
  
 *Имя Hierarchy_*  
 Допустимая строка, представляющая имя иерархии.  
  
 *Имя Level_*  
 Допустимая строка, представляющая имя уровня.  
  
 *Имя Member_*  
 Допустимая строка, представляющая имя или ключ элемента.  
  
 *MDX_Expression*  
 Допустимое многомерное выражение.  
  
 *String_Expression*  
 Допустимое строковое выражение.  
  
## <a name="remarks"></a>Комментарии  
 Возможна ситуация, когда клиентские приложения создают и запускают небезопасные действия или используют ненадежные функции. Чтобы избежать этих ситуаций, используйте свойство " **Параметры безопасности** ". Дополнительные сведения см. в разделе «Свойство параметров безопасности».  
  
> [!NOTE]  
>  Данная инструкция включена для обеспечения обратной совместимости. Действия [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , не поддерживаемые, например детализация или действия с отчетами, не поддерживаются.  
  
## <a name="action-types"></a>Типы действий  
 В следующей таблице описаны различные типы действий, доступные в [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] .  
  
|Тип действия|Описание|  
|-----------------|-----------------|  
|**URL-адрес**|Возвращаемая строка действия представляет собой URL-адрес, который можно открыть с помощью интернет-обозревателя.<br /><br /> Примечание. Если это действие не начинается с `https://` или `https://` , действие будет недоступно для браузера, если для **сафетйоптионс** не задано значение **DBPROPVAL_MSMD_SAFETY_OPTIONS_ALLOW_ALL**.|  
|**HTML**|Возвращаемая строка действия является скриптом HTML. Строку следует сохранить в файле, который надо просматривать с помощью интернет-обозревателя. Тогда весь скрипт можно запускать как часть созданного кода HTML.|  
|**БАЛАНС**|Возвращаемая строка действия — это инструкция, которая должна быть выполнена путем установки метода **ICommand:: SetText** объекта Command в строку и вызова метода **ICommand:: Execute**. Если команда завершится неудачно, будет возвращено сообщение об ошибке.|  
|**ОБЪЕКТЕ**|Возвращаемая строка действия — это инструкция многомерных выражений, которую необходимо выполнить, установив метод **ICommand:: SetText** объекта Command в строку и вызвав метод **ICommand:: Execute** . Запрошенный идентификатор интерфейса (IID) должен быть **идатасет**. Команда успешно выполнится, если набор данных уже был создан. Клиентское приложение должно обеспечить пользователю просмотр созданного набора данных.|  
|**НАБОРА строк**|Аналогично **набору данных**, но вместо запроса IID **идатасет**клиентское приложение должно запросить идентификатор IID программы **IRowset**. Команда успешно выполнится, если набор строк уже был создан. Клиентское приложение должно обеспечить пользователю просмотр созданного набора строк.|  
|**КОМАНД**|Клиентское приложение должно выполнить строку действия. Эта строка является командной.|  
|**СОБСТВЕННЫХ**|Клиентское приложение не будет показывать или выполнять это действие, если только данное приложение не обладает заданными пользователем (а не общими) знаниями об этом конкретном действии. Закрытые действия не возвращаются клиентскому приложению, если только клиентское приложение явно не запрашивает их, установив соответствующее ограничение на **APPLICATION_NAME**.|  
  
## <a name="invocation-types"></a>Типы инициации  
 В следующей таблице представлены различные типы инициации, имеющиеся в службах [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Тип инициации применяется только клиентским приложением, чтобы помочь определить, когда инициировать действие. Тип инициации в реальности не определяет поведение инициации действия.  
  
|Тип инициации|Описание|  
|---------------------|-----------------|  
|**Интерактивный**|Действие должно быть инициировано клиентским приложением через взаимодействие с пользователем.|  
|**ON_OPEN**|Действие должно быть инициировано клиентским приложением при открывании целевого объекта. Тип инициации еще не реализован.|  
|**РАЗДЕЛАХ**|Действие должно быть инициировано клиентским приложением, когда целевой объект используется в пакетной операции, определенной клиентским приложением.  Тип инициации еще не реализован.|  
  
### <a name="scope"></a>Область  
 Каждое действие определяется для заданного куба, оно имеет в этом кубе уникальное имя. Каждое действие может обладать одной из областей действия, приведенных в таблице (см. ниже).  
  
 Область — куб  
 Для действий, не зависящих от определенных измерений, элементов или ячеек; Например: "запуск эмуляции терминала для рабочей системы AS/400".  
  
 Область — измерение  
 Действие применимо к заданному измерению. Эти действия не зависят от конкретного выбора уровней и элементов.  
  
 Область — уровень  
 Действие применимо к заданному уровню измерения. Эти действия не зависят от выбора конкретного элемента в этом измерении.  
  
 Область — элемент  
 Это действие применимо к конкретным элементам уровня.  
  
 Область — ячейка  
 Это действие применимо только к конкретным ячейкам.  
  
 Область — набор  
 Действие применимо только к заданному набору. Имя **актионпараметерсет**зарезервировано для использования приложением внутри выражения действия.  
  
## <a name="see-also"></a>См. также  
 [Инструкции определения данных многомерных выражений &#40;&#41;многомерных выражений ](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
