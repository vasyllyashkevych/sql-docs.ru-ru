---
title: Настройки сведений об устройстве PDF | Документы Майкрософт
description: Узнайте о настройках сведений об устройстве, доступных для подготовки отчетов к просмотру в формате PDF.
ms.date: 03/16/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- device information settings [Reporting Services], PDF rendering
- PDF [Reporting Services]
ms.assetid: 9a4aabe5-dbdc-4884-b999-1200983fee47
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 126740ad794007e06d7565ddeea8a977fe07798b
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245283"
---
# <a name="pdf-device-information-settings"></a>Настройки сведений об устройстве PDF
  В следующей таблице перечислены настройки сведений об устройстве, предназначенные для подготовки отчетов к просмотру в формате PDF.  
  
|Параметр|Значение|  
|-------------|-----------|  
| **AccessiblePDF** | Указывает, следует ли отрисовывать доступный и помеченный тегами PDF-файл, имеющий больший размер, но проще воспринимаемый программами чтения с экрана и другими вспомогательными технологиями. Значение по умолчанию — **false**. [Доступно на сервере отчетов Power BI (март 2018) и в более поздних версиях] |
|**Столбцы**|Задаваемое число столбцов в отчете. Это значение переопределяет исходные параметры отчета.|  
|**ColumnSpacing**|Интервал между столбцами, который должен быть задан для отчета. Это значение переопределяет исходные параметры отчета.|  
|**DpiX**|Разрешение устройства вывода по оси x.|  
|**DpiY**|Разрешение устройства вывода по оси y.|  
|**EndPage**|Последняя подготавливаемая к просмотру страница отчета. Значением по умолчанию является значение для **StartPage**.|  
|**HumanReadablePDF**|Указывает, следует ли отрисовывать несжатый PDF-файл, имеющий больший размер, но более удобный для чтения в текстовом редакторе. Значение по умолчанию — **false.**|  
|**MarginBottom**|Задаваемая ширина нижнего поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 1in). Это значение переопределяет исходные параметры отчета.|  
|**MarginLeft**|Задаваемая ширина левого поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 1in). Это значение переопределяет исходные параметры отчета.|  
|**MarginRight**|Задаваемая ширина правого поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 1in). Это значение переопределяет исходные параметры отчета.|  
|**MarginTop**|Задаваемая ширина верхнего поля отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 1in). Это значение переопределяет исходные параметры отчета.|  
|**PageHeight**|Задаваемая высота страницы отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка "in" (например, 11in). Это значение переопределяет исходные параметры отчета.|  
|**PageWidth**|Задаваемая ширина страницы отчета, в дюймах. Необходимо включить целочисленное или десятичное значение, за которым следует строка «in» (например, 8,5in). Это значение переопределяет исходные параметры отчета.|  
|**StartPage**|Первая подготавливаемая к просмотру страница отчета. Значение **0** указывает, что к просмотру подготовлены все страницы. Значение по умолчанию — **1**.|  
  
## <a name="see-also"></a>См. также:  
 [Передача настроек сведений об устройстве модулям подготовки отчетов к просмотру](../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)   
 [Настройка параметров модулей подготовки отчетов в RSReportServer.Config](../reporting-services/customize-rendering-extension-parameters-in-rsreportserver-config.md)   
 [Технический справочник (службы SSRS)](../reporting-services/technical-reference-ssrs.md)  
  
  
