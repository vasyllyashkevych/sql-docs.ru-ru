---
description: sp_reinitsubscription (Transact-SQL)
title: sp_reinitsubscription (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_reinitsubscription
- sp_reinitsubscription_TSQL
helpviewer_keywords:
- sp_reinitsubscription
ms.assetid: d56ae218-6128-4ff9-b06c-749914505c7b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 68761baaf874d4900a7914753a37e1f465ff757e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89538690"
---
# <a name="sp_reinitsubscription-transact-sql"></a>sp_reinitsubscription (Transact-SQL)
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

  Помечает подписку для повторной инициализации. Эта хранимая процедура выполняется на стороне издателя для принудительной подписки.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_reinitsubscription [ [ @publication = ] 'publication' ]  
    [ , [ @article = ] 'article' ]  
        , [ @subscriber = ] 'subscriber'  
    [ , [ @destination_db = ] 'destination_db']  
    [ , [ @for_schema_change = ] 'for_schema_change']  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @ignore_distributor_failure = ] ignore_distributor_failure ]   
    [ , [ @invalidate_snapshot = ] invalidate_snapshot ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` Имя публикации. Аргумент *publication* имеет тип **sysname**и значение по умолчанию ALL.  
  
`[ @article = ] 'article'` Имя статьи. Аргумент *article* имеет тип **sysname**и значение по умолчанию ALL. Для немедленно обновляемой публикации *статья* должна быть **все**. в противном случае хранимая процедура пропускает публикацию и сообщает об ошибке.  
  
`[ @subscriber = ] 'subscriber'` Имя подписчика. Аргумент *Subscriber* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @destination_db = ] 'destination_db'` Имя целевой базы данных. Аргумент *destination_db* имеет тип **sysname**и значение по умолчанию ALL.  
  
`[ @for_schema_change = ] 'for_schema_change'` Указывает, происходит ли повторная инициализация в результате изменения схемы в базе данных публикации. *for_schema_change* имеет **бит**и значение по умолчанию 0. Если значение **равно 0**, активные подписки для публикаций, которые разрешают немедленное обновление, повторно активируются, пока вся публикация, а не только часть ее статьи, повторно инициализируется. Это означает, что повторная инициализация инициируется в результате изменения схемы. Если значение равно **1**, активные подписки не будут повторно активированы до тех пор, пока не будет запущен агент моментальных снимков.  
  
`[ @publisher = ] 'publisher'` Указывает издателя, отличного от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Аргумент *Publisher* имеет тип **sysname**и значение по умолчанию NULL.  
  
> [!NOTE]  
>  *Издатель* не должен использоваться для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
`[ @ignore_distributor_failure = ] ignore_distributor_failure` Разрешает повторную инициализацию, даже если распространитель не существует или находится вне сети. *ignore_distributor_failure* имеет **бит**и значение по умолчанию 0. Если значение **равно 0**, повторная инициализация завершается неудачей, если распространитель не существует или находится в автономном режиме.  
  
`[ @invalidate_snapshot = ] invalidate_snapshot` Делает недействительным существующий моментальный снимок публикации. *invalidate_snapshot* имеет **бит**и значение по умолчанию 0. Если значение равно **1**, для публикации создается новый моментальный снимок.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_reinitsubscription** используется в репликации транзакций.  
  
 **sp_reinitsubscription** не поддерживается для одноранговой репликации транзакций.  
  
 Для подписок, для которых исходный моментальный снимок применяется автоматически и публикации не допускают обновляемых подписок, агент моментальных снимков должен быть запущен после выполнения этой хранимой процедуры так, чтобы схема и программные файлы массового копирования были подготовлены, и агент распространителя был готов к повторной синхронизации подписок.  
  
 Для подписок, у которых исходный моментальный снимок применяется автоматически и публикация допускает обновляемые подписки, агент распространителя повторно синхронизирует подписку, используя последнюю схему и программные файлы массового копирования, предварительно созданные агентом моментальных снимков. Агент распространения повторно синхронизирует подписку сразу после выполнения пользователем **sp_reinitsubscription**, если агент распространения не занята; в противном случае синхронизация может произойти после интервала сообщений (задается агент распространения параметром командной строки: **MessageInterval**).  
  
 **sp_reinitsubscription** не влияет на подписки, в которых исходный моментальный снимок применяется вручную.  
  
 Для повторной синхронизации анонимных подписок на публикацию передайте значения **ALL** или NULL в качестве *подписчика*.  
  
 Репликация транзакций поддерживает повторную инициализацию подписок на уровне статей. Моментальный снимок статьи повторно применяется на стороне подписчика во время следующей инициализации, после того как статья была помечена для повторной инициализации или синхронизации. Однако если существуют зависимые статьи, на которые подписан тот же подписчик, повторное применение к статье моментального снимка может завершиться неудачно, если только зависимые статьи в публикации также автоматически не инициализируются повторно при возникновении определенных обстоятельств:  
  
-   если командой перед созданием статьи является DROP, то статьи для привязанных к схеме представлений и хранимых процедур на основном объекте статьи также помечаются для повторной инициализации;  
  
-   если параметр схемы статьи включает создание сценария объявленной ссылочной целостности для первичных ключей, статьи, у которых есть основные таблицы с внешними ключами к основным таблицам повторно инициализируемой статьи, также помечаются для повторной инициализации.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_reinittranpushsub](../../relational-databases/replication/codesnippet/tsql/sp-reinitsubscription-tr_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , члены предопределенной роли базы данных **db_owner** или создатель подписки могут выполнять **sp_reinitsubscription**.  
  
## <a name="see-also"></a>См. также  
 [Повторная инициализация подписки](../../relational-databases/replication/reinitialize-a-subscription.md)   
 [Повторная инициализация подписок](../../relational-databases/replication/reinitialize-subscriptions.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
