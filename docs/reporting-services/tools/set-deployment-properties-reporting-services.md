---
title: Задание свойства развертывания (службы Reporting Services) | Документация Майкрософт
description: Узнайте, как задавать свойства развертывания, используемые SQL Server Data Tools (SSDT) или Visual Studio для создания, предварительного просмотра и развертывания отчетов.
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: tools
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], deploying
- publishing reports [Reporting Services]
- properties [Reporting Services], deployment
- deploying reports [Reporting Services]
ms.assetid: 18201ca0-bf4a-484f-b3a2-95d1046a6a9b
author: maggiesMSFT
ms.author: maggies
ms.date: 05/15/2019
ms.openlocfilehash: 97a0f7d9bf63bf6ad74b522a42900fc36cfcd429
ms.sourcegitcommit: 783b35f6478006d654491cb52f6edf108acf2482
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91891654"
---
# <a name="set-deployment-properties-reporting-services"></a>Задание свойства развертывания (службы Reporting Services)

  В [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или Visual Studio необходимо указать сервер отчетов. Можно также указать папки для отчетов и общие источники данных, чтобы публиковать элементы в соответствующем проекте на сервере отчетов. Свойства и значения, используемые в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] или Visual Studio для создания, предварительного просмотра и развертывания отчетов, хранятся в конфигурациях проектов в проекте сервера отчетов. Можно создать несколько именованных наборов для этих свойств проекта, чтобы можно было просто переключаться с одного набора свойств на другой. Каждый набор свойств представляет собой конфигурацию. Например, может существовать одна конфигурация для публикации отчетов на тестовом сервере и другая конфигурация для публикации отчетов на рабочем сервере.  
  
 Создание наборов свойств проекта в конфигурациях проектов и управление ими производится с помощью диспетчера конфигурации. Диспетчер конфигурации представляет собой компонент, поддерживаемый средой [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], на котором основана среда [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] .  
  
> [!NOTE]  
> Не следует путать этот компонент с диспетчером конфигурации сервера отчетов, который применяется для настройки служб Reporting Services после установки. Дополнительные сведения см. в разделе [Настройка и администрирование сервера отчетов &#40;службы Reporting Services в собственном режиме&#41;](../../reporting-services/report-server/configure-and-administer-a-report-server-ssrs-native-mode.md).  
>
> [!NOTE]  
> В среде [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]действие публикации отчетов из проекта сервера отчетов или решения принято называть *развертыванием отчетов*.  
  
## <a name="to-set-deployment-properties"></a>Установка свойств развертывания
  
1. Щелкните правой кнопкой мыши проект отчета и выберите пункт **Свойства**.  
  
2. В диалоговом окне **Свойства страницы** проекта выберите изменяемую конфигурацию в списке **Конфигурация** . Распространенные конфигурации — **DebugLocal**, **Debug**и **Release**.  
  
    > [!NOTE]  
    > Можно использовать несколько конфигураций для быстрого переключения между различными серверами или настройками.  
  
3. В текстовом поле **OutputPath**  введите или вставьте путь в локальной файловой системе, чтобы сохранить определение отчета, используемое при проверке сборки, развертывании и предварительном просмотре отчетов. Путь должен отличаться от пути, используемого для проекта, и относительного пути, который является дочерней папкой в каталоге проекта.  
  
4. В текстовом поле **ErrorLevel**  введите серьезность проблем сборки, которые выводятся как ошибки. Проблемы при построении отчетов, источников данных или других ресурсов проекта, степень серьезности которых будет меньше значения **ErrorLevel**  или равна ему, выводятся как ошибки. Все остальные проблемы выводятся как предупреждения. Любая ошибка вызовет завершение задачи построения. Допустимы степени серьезности от 0 до 4 включительно. Значение по умолчанию — 2.  
  
     **Уровень ошибки** может использоваться для повышения или понижения чувствительности сборки. Например, если создается отчет с картой при развертывании на сервере отчетов [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] , то по умолчанию отображается ошибка и построение отчета завершается ошибкой. Если понизить **Уровень ошибки** , то карта будет удалена из отчета, выдано предупреждение и построение отчета продолжится.  
  
5. В списке **StartItem**  выберите отчет, который будет отображаться в окне предварительного просмотра или в окне браузера, когда запустится проект отчета.  
  
6. В списке **OverwriteDataSources** выберите **True** , чтобы общий источник данных перезаписывался на сервере при каждой публикации общих источников данных, либо **False** , чтобы сохранить источник данных на сервере.  
  
7. В списке **TargetServerVersion** выберите версию SQL Server 2016 для [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] или пункт **Обнаружить версию** , чтобы автоматически определять установленную версию на сервере, который указан в свойстве **TargetServer URL** . Значение по умолчанию — **SQL Server 2016 или более поздней версии**.  
  
     Параметр **TargetServerVersion** позволяет настроить отчеты о сборке, размещенные в каталоге, указанном в поле "Выходной путь", для версии сервера отчетов, обозначенной в **TargetServer URL**.  
  
8. В текстовом поле **TargetDataSourceFolder** укажите папку, в которую сервер отчетов должен помещать опубликованные общие источники данных. Значением по умолчанию свойства **TargetDataSourceFolder** является "Data Sources". Если оставить это значение пустым, источники данных будут опубликованы в местоположении, указываемом свойством **TargetReportFolder**.  
  
9. В текстовое поле **TargetReportFolder** введите имя папки на сервере отчетов, в которой будут храниться опубликованные отчеты. По умолчанию в текстовом поле **TargetReportFolder**  используется имя проекта отчета.  
  
    > [!NOTE]  
    > На сервере отчетов, работающем в собственном режиме, необходимо иметь разрешение **Публикация** для целевой папки, чтобы публиковать в ней отчеты. Разрешения на публикацию предоставляются через назначение ролей, которая сопоставляет текущую учетную запись с ролью, которая включает операции публикации. Дополнительные сведения см. в разделе [Создание назначений ролей и управление ими](../../reporting-services/security/create-and-manage-role-assignments.md). На сервере отчетов, работающем в режиме интеграции с SharePoint, необходимо иметь разрешение **Член** или **Владелец** на сайте SharePoint. Дополнительные сведения см. в разделе [Справочная таблица по разрешениям на сайты SharePoint и списки для элементов сервера отчетов](../../reporting-services/security/sharepoint-site-and-list-permission-reference-for-report-server-items.md).  
  
10. В текстовое поле **TargetServerURL** введите URL-адрес целевого сервера отчетов. Перед публикацией отчета необходимо задать в этом свойстве правильный URL-адрес сервера отчетов. При публикации на сервере отчетов, работающем в собственном режиме, используйте URL-адрес виртуального каталога сервера отчетов (например, http:*//сервер/сервер_отчетов* или http:*//сервер/сервер_отчетов)*. Это виртуальный каталог сервера отчетов, а не веб-портала.  
  
     При публикации на сервере отчетов, работающем в режиме интеграции с SharePoint, указывайте URL-адрес сайта SharePoint верхнего уровня или соответствующего подсайта. Если сайт не указан, используется сайт верхнего уровня по умолчанию (например, `https://*servername*`, `https://*servername*/*site*`или `https://*servername*/*site*/*subsite*`).  
  
## <a name="to-set-configuration-manager-properties"></a>Установка свойств диспетчера конфигурации  
  
1. Щелкните правой кнопкой мыши проект отчета и выберите пункт **Свойства**.  
  
2. В диалоговом окне **Страницы свойств** проекта выберите **Диспетчер конфигурации**.  
  
3. В диалоговом окне **Диспетчер конфигурации** выберите изменяемую конфигурацию. Конфигурация, активная в настоящее время, отображается как **Active(***\<configuration>***)** .  
  
4. В разделе **Контексты проекта**для каждого проекта в решении установите либо снимите флажки **Создать** или **Развернуть**.  
  
    > [!NOTE]  
    > Если установлен флажок **Создать** , конструктор отчетов создает проект отчета и осуществляет его проверку перед предварительным просмотром или публикацией на сервере отчетов. Если установлен флажок **Развернуть** , конструктор отчетов публикует отчет на сервере отчетов согласно свойствам развертывания. Если флажок **Развернуть** не установлен, конструктор отчетов отображает отчет, указанный в свойстве **StartItem** в локальном окне предварительного просмотра.  
  
## <a name="see-also"></a>См. также раздел  

- [Публикация источников данных и отчетов](../../reporting-services/reports/publishing-data-sources-and-reports.md)
- [Предварительный просмотр отчетов](../../reporting-services/reports/previewing-reports.md)
- [Справка F1 по использованию конструктора отчетов](../../reporting-services/tools/report-designer-f1-help.md)
- [Примеры URL-адресов для элементов опубликованного отчета на сервере отчетов в режиме SharePoint (службы SSRS)](../../reporting-services/tools/url-examples-for-items-on-a-report-server-sharepoint-mode.md)
- [Диалоговое окно страниц свойств проекта](../../reporting-services/tools/project-property-pages-dialog-box.md)
- [Публикация отчетов на сервере отчетов](../../reporting-services/reports/publishing-reports-to-a-report-server.md)
