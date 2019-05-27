---
title: Установка PolyBase на компьютере под управлением Linux | Документация Майкрософт
description: В этой статье описывается установка SQL Server Full-Text Search в Linux.
author: aboke
ms.author: aboke
manager: craigg
ms.date: 4/12/2019
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: bb42076f-e823-4cee-9281-cd3f83ae42f5
ms.openlocfilehash: 69c256ef52d9c302d55ef1499059d959ed55b528
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/24/2019
ms.locfileid: "63759071"
---
# <a name="install-polybase-on-linux"></a>Установка PolyBase на компьютере под управлением Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Используйте следующие шаги, чтобы установить [PolyBase](../../relational-databases/search/full-text-search.md) (**mssql-server-polybase**) на платформе Linux. PolyBase позволяет выполнять внешние запросы к удаленным источникам данных. 

>[!NOTE]
> Перед установкой Polybase сначала нужна [Установка SQL Server](../../linux/sql-server-linux-setup.md#platforms). Это позволит настроить ключи и репозитории, которые следует использовать при установке пакета **mssql-server-polybase**.

> Возможность горизонтального масштабирования для PolyBase в Linux сейчас недоступна.


Установите PolyBase для вашей операционной системы:

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)



## <a name="RHEL">Установка в RHEL</a>

Используйте следующую команду для установки **mssql-server-polybase** в Red Hat Enterprise Linux. 

```bash
sudo yum install -y mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>После установки необходимо [включить компонент PolyBase](#enable).

Если вам нужна автономная установка, найдите скачиваемый пакет PolyBase в разделе [Заметки о выпуске](../../linux/sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](../../linux/sql-server-linux-setup.md#offline).

## <a name="ubuntu">Установка в Ubuntu</a>

Используйте следующую команду для установки **mssql-server-polybase** в Ubuntu. 

```bash
sudo apt-get install mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>После установки необходимо [включить компонент PolyBase](#enable).

Если вам нужна автономная установка, найдите скачиваемый пакет PolyBase в разделе [Заметки о выпуске](../../linux/sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](../../linux/sql-server-linux-setup.md#offline).

## <a name="SLES">Установка в SLES</a>

Используйте следующую команду для установки **mssql-server-polybase** в SUSE Linux Enterprise Server. 

```bash
sudo zypper install mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```bash
sudo systemctl restart mssql-server
```

>[!NOTE]
>После установки необходимо [включить компонент PolyBase](#enable).


Если вам нужна автономная установка, найдите скачиваемый пакет PolyBase в разделе [Заметки о выпуске](../../linux/sql-server-linux-release-notes.md). Затем выполните действия по автономной установке, описанные в статье [Установка SQL Server](../../linux/sql-server-linux-setup.md#offline).


## <a name="enable">Включение PolyBase</a> 

Завершив установку, включите компонент PolyBase для доступа к его функциям. Подключитесь к установленному экземпляру SQL Server и используйте следующую команду Transact-SQL для включения.

```sql
exec sp_configure @configname = 'polybase enabled', @configvalue = 1;
RECONFIGURE [WITH OVERRIDE];
```

## <a name="update-polybase"></a>Обновление PolyBase

Если у вас уже есть **mssql-server-polybase**, можно обновить пакет до последней версии, выполнив следующие команды:

### <a name="rhel"></a>RHEL

```bash
sudo yum remove -y mssql-server-polybase
sudo yum check-update
sudo yum install -y mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```
sudo systemctl restart mssql-server
```

### <a name="ubuntu"></a>Ubuntu

```bash
sudo apt-get remove mssql-server-polybase
sudo apt-get update 
sudo apt-get install mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```
sudo systemctl restart mssql-server
```

### <a name="sles"></a>SLES

```bash
sudo zypper remove mssql-server-polybase
sudo zypper refresh
sudo zypper install mssql-server-polybase
```

Вам будет предложено перезапустить экземпляр SQL Server. Используйте для этого следующую команду:

```
sudo systemctl restart mssql-server
```

>[!NOTE]
>После установки необходимо [включить компонент PolyBase](#enable).

## <a name="next-steps"></a>Следующие шаги

### <a name="supported-external-data-sources-on-linux"></a>Поддерживаемые в Linux внешние источники данных

Для PolyBase в Linux доступны следующие источники данных. Следуйте указанным ссылкам, чтобы получить дополнительные сведения о создании внешних таблиц из этих источников в PolyBase. 

- [SQL Server (а также база данных SQL, хранилище данных SQL Azure)](../../relational-databases/polybase/polybase-configure-sql-server.md)
- [Oracle;](../../relational-databases/polybase/polybase-configure-oracle.md)
- [Teradata](../../relational-databases/polybase/polybase-configure-teradata.md)
- [MongoDB (а также Cosmos DB)](../../relational-databases/polybase/polybase-configure-mongodb.md)

Дополнительные сведения об использовании сопоставления см. в справочнике по Transact-SQL для [CREATE EXTERNAL TABLE (Transact-SQL)](../../t-sql/statements/create-external-table-transact-sql.md).