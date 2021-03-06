---
title: Управление сертификатами (диспетчер конфигурации SQL Server) | Документация Майкрософт
description: Узнайте, как устанавливать сертификаты в различных конфигурациях SQL Server. Примеры включают в себя отдельные экземпляры, отказоустойчивые кластеры и группы доступности Always On.
ms.custom: ''
ms.date: 01/16/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], encrypted
- SSL [SQL Server]
- Secure Sockets Layer (SSL)
- encryption [SQL Server], connections
- cryptography [SQL Server], connections
- certificates [SQL Server], installing
- requesting encrypted connections
- installing certificates
- security [SQL Server], encryption
ms.assetid: e1e55519-97ec-4404-81ef-881da3b42006
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 835d0b1da11ba014b14ede9637117357e84dc208
ms.sourcegitcommit: d498110ec0c7c62782fb694d14436f06681f2c30
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2020
ms.locfileid: "85196051"
---
# <a name="certificate-management-sql-server-configuration-manager"></a>Управление сертификатами (диспетчер конфигурации SQL Server)

В этой статье описывается развертывание сертификатов и управление ими в отказоустойчивом кластере Always On или топологии групп доступности SQL Server.

Сертификаты SSL/TLS широко используются для обеспечения безопасного доступа к SQL Server. В более ранних версиях организациям с масштабными развертываниями SQL Server приходилось тратить значительные усилия на поддержание инфраструктуры сертификатов SQL Server. Для этого часто необходимо было разрабатывать скрипты и выполнять команды вручную. В SQL Server 2019 управление сертификатами интегрировано в диспетчер конфигурации SQL Server, что упрощает выполнение следующих распространенных задач: 

* просмотр и проверка сертификатов, установленных в экземпляре SQL Server; 
* определение сертификатов, срок действия которых может скоро истечь; 
* развертывание сертификатов на компьютерах групп доступности Always On из узла, содержащего первичную реплику; 
* развертывание сертификатов на компьютерах, участвующих в экземпляре отказоустойчивого кластера Always On из активного узла.

> [!NOTE]
> Функции управления сертификатами в диспетчере конфигурации SQL Server можно использовать с более ранними версиями SQL Server, начиная с SQL Server 2008.

##  <a name="to-install-a-certificate-for-a-single-sql-server-instance"></a><a name="provision-single-server-cert"></a> Установка сертификата для одного экземпляра SQL Server  
  
1. В диспетчере конфигурации SQL Server в области консоли разверните раздел **Сетевая конфигурация SQL Server**.  
  
2. Щелкните правой кнопкой мыши элемент **Протоколы для** *&lt;имя экземпляра&gt;* и выберите пункт **Свойства**.  
  
3. Перейдите на вкладку **Сертификат** и выберите команду **Импорт**.  
  
4. Нажмите кнопку **Обзор** и выберите файл сертификата.  
  
5. Нажмите кнопку **Далее**, чтобы проверить сертификат. Если ошибок нет, нажмите кнопку **Далее**, чтобы импортировать сертификат в локальный экземпляр.  
  
 
##  <a name="to-install-a-certificate-in-a-failover-cluster-instance-configuration"></a><a name="provision-failover-cluster-cert"></a> Установка сертификата в конфигурации экземпляра отказоустойчивого кластера  
  
1. В диспетчере конфигурации SQL Server в области консоли разверните раздел **Сетевая конфигурация SQL Server**.
  
2. Щелкните правой кнопкой мыши элемент **Протоколы для** *&lt;имя экземпляра&gt;* и выберите пункт **Свойства**. 

3. Перейдите на вкладку **Сертификат** и выберите команду **Импорт**.

4. Выберите тип сертификата и способ его импорта: только для текущего узла или для каждого узла в кластере.

5. Если сертификат устанавливается для одного узла, нажмите кнопку **Обзор** и выберите файл сертификата. Затем перейдите к шагу 8.

6. Если сертификат устанавливается для каждого узла, нажмите кнопку **Далее**, чтобы открыть список узлов возможных владельцев. Возможные владельцы для текущего экземпляра отказоустойчивого кластера выбираются предварительно.

7. Нажмите кнопку **Далее**, чтобы выбрать импортируемый сертификат.

8. Введите пароль, когда появится запрос. После проверки обратите внимание на предупреждения и ошибки.

9. Нажмите кнопку **Далее**, чтобы импортировать выбранные сертификаты.

> [!NOTE]
> Выполните эти действия в активном узле экземпляра отказоустойчивого кластера Always On. Пользователю необходимо предоставить разрешения администратора на всех узлах кластера.

##  <a name="to-install-a-certificate-in-an-always-on-availability-group-configuration"></a><a name="provision-availability-group-cert"></a>Установка сертификата в конфигурации группы доступности Always On  
  
1. В диспетчере конфигурации SQL Server в области консоли разверните раздел **Сетевая конфигурация SQL Server**.
  
2. Щелкните правой кнопкой мыши элемент **Протоколы для** *&lt;имя экземпляра&gt;* и выберите пункт **Свойства**.  
  
3. Перейдите на вкладку **Сертификат** и выберите команду **Импорт**.  
  
4. Выберите тип сертификата и нажмите кнопку **Далее**, чтобы выбрать группу доступности из списка известных.  

5. Нажмите кнопку **Далее**, чтобы выбрать сертификаты для каждого узла реплики. Имя файла сертификата должно совпадать с NetBIOS-именем узла.

6. Нажмите кнопку **Далее**, чтобы импортировать сертификат в каждом узле.


> [!NOTE]
> Выполните эти действия из узла, содержащего первичную реплику группы доступности. Пользователю необходимо предоставить разрешения администратора на всех узлах кластера.

