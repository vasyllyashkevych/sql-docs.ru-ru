---
description: Состояние только для чтения (драйвер для Excel)
title: Состояние только для чтения (драйвер для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- read-only status for Excel driver [ODBC]
- Excel driver [ODBC], read-only status
ms.assetid: ef5d773b-4f8f-4005-b985-84b53d8e9f9b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 04a0c5d0cb2c9932d30c0edb900169d8c5e5f82b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340390"
---
# <a name="read-only-status-excel-driver"></a>Состояние только для чтения (драйвер для Excel)
При использовании драйвера Microsoft Excel таблицы источников данных по умолчанию открываются как доступные только для чтения и могут быть открыты только одним пользователем за раз. Хотя таблицы имеют состояние только для чтения, однако приложения могут выполнять вставки и обновления для таблиц Microsoft Excel.  
  
 Когда приложение выполняет команду Сохранить как для данных Microsoft Excel через драйвер Microsoft Excel, приложение должно создать новую таблицу и вставить данные, которые будут сохранены в новой таблице. Операции вставки приводят к добавлению в таблицу. Никакие другие операции с таблицей не могут быть выполнены до ее закрытия и повторного открытия. После закрытия таблицы дальнейшая вставка не может быть выполнена, так как таблица затем является таблицей, предназначенной только для чтения.  
  
 Можно обновлять значения при использовании драйвера Microsoft Excel, но нельзя удалить строку из таблицы, основанной на электронной таблице Microsoft Excel, поэтому обновления не считаются официально поддерживаемыми драйвером Microsoft Excel.
