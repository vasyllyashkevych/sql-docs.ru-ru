---
description: Escape-последовательности для значений даты, времени и отметок времени
title: Escape-последовательности даты, времени и метки времени | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC]
- escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC], about escape sequences
- ODBC escape sequences [ODBC]
ms.assetid: 67b7dee0-e5b1-4469-a626-0c7767852b80
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bd70c005d2fa7ae4972605c45793f2a0836f849
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88483307"
---
# <a name="date-time-and-timestamp-escape-sequences"></a>Escape-последовательности для значений даты, времени и отметок времени
ODBC определяет escape-последовательности для литералов даты, времени и меток времени. Синтаксис этих escape-последовательностей выглядит следующим образом:  
  
```  
  
{d 'value'}  
{t 'value'}  
{ts 'value'}  
```  
  
 В нотации BNF синтаксис выглядит следующим образом:  
  
```bnf 
ODBC-date-time-escape ::=  
     ODBC-date-escape  
     | ODBC-time-escape  
     | ODBC-timestamp-escape

ODBC-date-escape ::=  
     ODBC-esc-initiator d 'date-value' ODBC-esc-terminator

ODBC-time-escape ::=  
     ODBC-esc-initiator t 'time-value' ODBC-esc-terminator

ODBC-timestamp-escape ::=  
     ODBC-esc-initiator ts 'timestamp-value' ODBC-esc-terminator

ODBC-esc-initiator ::= {  

ODBC-esc-terminator ::= }  

date-value ::=   
     years-value date-separator months-value date-separator days-value

time-value ::=   
     hours-value time-separator minutes-value time-separator seconds-value

timestamp-value ::= date-value timestamp-separator time-value

date-separator ::= -  

time-separator ::= :  

timestamp-separator ::=  
     (The blank character)

years-value ::= digit digit digit digit

months-value ::= digit digit

days-value ::= digit digit

hours-value ::= digit digit

minutes-value ::= digit digit

seconds-value ::= digit digit[.digit...]  
```  
  
## <a name="remarks"></a>Remarks  
 Escape-последовательности литералов даты, времени и отметок времени поддерживаются, если источник данных поддерживает типы данных даты, времени и отметки времени. Приложение должно вызывать **SQLGetTypeInfo** , чтобы определить, поддерживаются ли эти типы данных.
