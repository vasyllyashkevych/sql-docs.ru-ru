---
description: Назначение больших двоичных объектов Azure
title: Назначение больших двоичных объектов Azure | Документы Майкрософт
ms.custom: ''
ms.date: 07/25/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpblobdest.f1
- sql14.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2f7db713ef6aa1c18c3506a842624bfd514c4807
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88457522"
---
# <a name="azure-blob-destination"></a>Назначение больших двоичных объектов Azure

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


 Компонент **Назначение больших двоичных объектов Azure** позволяет пакету SSIS записывать данные в BLOB-объект Azure. Поддерживаются следующие форматы файлов: CSV и AVRO. 
   
 Перетащите компонент **Назначение больших двоичных объектов Azure** в конструктор потока данных и дважды щелкните его, чтобы открыть редактор.  
  
 Компонент **Назначение больших двоичных объектов Azure** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).  
  
1.  В поле **Диспетчер подключений службы хранилища Azure** укажите существующий диспетчер подключений службы хранилища Azure или создайте новый, который ссылается на учетную запись хранения Azure.  
  
2.  В поле **Имя контейнера больших двоичных объектов** укажите имя контейнера больших двоичных объектов, который содержит исходные файлы.  
  
3.  В поле **Имя большого двоичного объекта** укажите путь к большому двоичному объекту.  
  
4.  В поле **Формат файла большого двоичного объекта** укажите формат большого двоичного объекта, который следует использовать.  
  
5.  Если формат файла — CSV, необходимо указать значение **знака-разделителя столбцов** . Также выберите **Имена столбцов в первой строке данных** , если первая строка файла содержит имена столбцов.  
  
6.  После указания сведений о соединении переключитесь на страницу **Столбцы** , чтобы сопоставить столбцы источника со столбцами назначения для потока данных служб SSIS.  
  
  
