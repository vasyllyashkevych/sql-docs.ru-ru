---
title: Анализ запросов с помощью результатов инструкции SHOWPLAN
titleSuffix: SQL Server Profiler
description: Сведения о том, как извлечь события Showplan из трассировки, чтобы SQL Server Profiler выводил сведения о плане запроса. Просмотр таблицы событий трассировки Showplan.
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: profiler
ms.topic: conceptual
ms.assetid: 6a2f7727-141c-4f59-8613-2e452bc78467
author: markingmyname
ms.author: maghan
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.openlocfilehash: b833f87e092260d38649c464fd4b09c6e43899d0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85774951"
---
# <a name="analyze-queries-with-showplan-results-in-sql-server-profiler"></a>Анализ запросов с помощью результатов инструкции SHOWPLAN в приложении SQL Server Profiler

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  В определение трассировки можно могут быть добавлены классы событий инструкции Showplan, после чего приложение [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] соберет и отобразит в трассировке сведения о плане запроса. Кроме того, события Showplan можно извлечь из других событий, собранных в трассировке, и сохранить в отдельном XML-файле.  
  
 События инструкции Showplan можно извлечь из трассировки следующими способами.  
  
-   При настройке трассировки на вкладке **Настройки извлечения событий** . Обратите внимание на то, что эта вкладка не отображается до тех пор, пока не будет выбрано одно из событий инструкции Showplan на вкладке **Выбор событий** .  
  
-   С помощью параметра **Извлечь события SQL Server** в меню **Файл** .  
  
-   Отдельные события можно извлечь и сохранить, щелкнув их правой кнопкой мыши и выбрав команду **Извлечь данные события**.  
  
## <a name="showplan-events"></a>События инструкции Showplan  
 События трассировки инструкции Showplan перечислены и описаны в следующей таблице.  
  
|Имя события|Описание|  
|----------------|-----------------|  
|**Performance statistics**|Отображает сведения о первом кэшировании скомпилированной инструкции Showplan, данные о ее повторной компиляции и удалении из кэша планов. Столбец **TextData** содержит инструкцию Showplan в формате XML. Дополнительные сведения см. в статье [Класс событий Performance Statistics](../../relational-databases/event-classes/performance-statistics-event-class.md).|  
|**Showplan All**|Выводит план запроса со всеми подробностями процесса компиляции для выполненной инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Например, здесь можно отобразить оценку затрат и списки столбцов. Дополнительные сведения см. в статье [Showplan All Event Class](../../relational-databases/event-classes/showplan-all-event-class.md).|  
|**Showplan All For Query Compile**|Происходит при компиляции или перекомпиляции запроса на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это происходящий во время компиляции аналог события **Showplan All** . **Showplan All** происходит при выполнении запроса. **Showplan All For Query Compile** происходит при компиляции запроса. Дополнительные сведения см. в статье [Showplan All for Query Compile Event Class](../../relational-databases/event-classes/showplan-all-for-query-compile-event-class.md).|  
|**Showplan Statistics Profile**|Отображает план запроса со всеми подробностями времени выполнения инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] , включая фактическое число строк, участвующих в каждой операции. Дополнительные сведения см. в статье [Showplan Statistics Profile Event Class](../../relational-databases/event-classes/showplan-statistics-profile-event-class.md).|  
|**Showplan Text**|Отображает дерево плана запроса выполняемой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в виде двоичных данных. Дополнительные сведения см. в статье [Showplan Text Event Class](../../relational-databases/event-classes/showplan-text-event-class.md).|  
|**Showplan Text (Unencoded)**|Отображает дерево плана запроса выполняемой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] в виде текста. Этот класс событий отображает те же сведения, что и предыдущий, но только в текстовом, а не в двоичном виде. Дополнительные сведения см. в статье [Класс событий Showplan Text (Unencoded)](../../relational-databases/event-classes/showplan-text-unencoded-event-class.md).|  
|**Showplan XML**|Отображает план запроса со всеми данными, собранными во время его оптимизации. Данное событие формируется, только если план запроса оптимизирован. Дополнительные сведения см. в статье [Showplan XML Event Class](../../relational-databases/event-classes/showplan-xml-event-class.md).|  
|**Showplan XML For Query Compile**|Отображает план запроса во время компиляции. Дополнительные сведения см. в статье [Showplan XML for Query Compile Event Class](../../relational-databases/event-classes/showplan-xml-for-query-compile-event-class.md).|  
|**Showplan XML Statistics Profile**|Отображает план запроса в формате XML с подробными сведениями по его выполнению. Например, этот класс событий регистрирует количество строк, участвующих в каждом операторе выполняемой инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] . Дополнительные сведения см. в статье [Showplan XML Statistics Profile Event Class](../../relational-databases/event-classes/showplan-xml-statistics-profile-event-class.md).|  
  
## <a name="see-also"></a>См. также:  
 [Категория событий Performance](../../relational-databases/event-classes/performance-event-category.md)  
  
  
