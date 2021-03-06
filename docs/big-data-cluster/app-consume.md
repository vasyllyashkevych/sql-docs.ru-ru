---
title: Использование приложений
titleSuffix: SQL Server Big Data Clusters
description: Использование приложения, развернутого в кластере больших данных SQL Server, с помощью веб-службы на основе REST.
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 06/22/2020
ms.metadata: seo-lt-2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 307d1cf41c319debad4b0fc06b8ba0da516491bd
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257324"
---
# <a name="consume-an-app-deployed-on-big-data-clusters-2019-using-a-restful-web-service"></a>Использование приложения, развернутого в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)], с помощью веб-службы на основе REST

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается использование приложения, развернутого в кластере больших данных SQL Server, с помощью веб-службы на основе REST.

## <a name="prerequisites"></a>предварительные требования

- [Кластер больших данных SQL Server](deployment-guidance.md)
- [[!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)]](../azdata/install/deploy-install-azdata.md)
- Приложение, развернутое с помощью [azdata](app-create.md) или [расширения развертывания приложения](app-deployment-extension.md)

> [!NOTE]
> Если в файле спецификации YAML приложения указано расписание, приложение будет запущено с помощью задания cron. Если кластер больших данных развертывается в OpenShift, запуск задания cron требует дополнительных возможностей. Подробные инструкции см. в [рекомендациях по безопасности для OpenShift](concept-application-deployment.md#app-deploy-security).

## <a name="capabilities"></a>Возможности

После развертывания приложения в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] вы можете обращаться к нему и использовать его с помощью веб-службы на основе REST. Это обеспечивает интеграцию этого приложения с другими приложениями или службами (например, мобильным приложением или веб-сайтом). В следующей таблице описаны команды развертывания приложения, которые можно использовать с **azdata**, чтобы получить сведения о веб-службе на основе REST для приложения.

|Команда |Описание |
|:---|:---|
|`azdata app describe` | Описание приложения. |

Справку по параметру `--help` можно получить, как показано в следующем примере.

```bash
azdata app describe --help
```

В следующих разделах описано, как получить конечную точку для приложения и работать с веб-службой на основе REST для интеграции приложений.

## <a name="retrieve-the-endpoint"></a>Получение конечной точки

Кластеры больших данных предоставляют конечные точки, которые можно использовать для доступа к приложению и его использования с помощью веб-службы RESTful. Основное их назначение заключается в том, чтобы обеспечить взаимодействие с другими веб-приложениями или мобильными приложениями и обеспечить более активный переход на эту архитектуру микрослужб. Команда **azdata app describe** предоставляет подробные сведения о приложении, включая конечную точку в кластере. Обычно она используется разработчиком приложения, чтобы создать приложение с помощью клиента Swagger и использовать веб-службу для взаимодействия с приложением на основе REST.

Опишите приложение, выполнив команду, аналогичную приведенной в следующем примере:

```bash
azdata app describe --name add-app --version v1
```

```json
{
  "input_param_defs": [
    {
      "name": "x",
      "type": "int"
    },
    {
      "name": "y",
      "type": "int"
    }
  ],
  "links": {
    "app": "https://10.1.1.3:30080/app/addpy/v1",
    "swagger": "https://10.1.1.3:30080/app/addpy/v1/swagger.json"
  },
  "name": "add-app",
  "output_param_defs": [
    {
      "name": "result",
      "type": "int"
    }
  ],
  "state": "Ready",
  "version": "v1"
}
```

Запишите IP-адрес (в этом примере — `10.1.1.3`) и номер порта (`30080`) в выходных данных.

Доступен еще один способ получения этой информации: щелкните правой кнопкой мыши элемент "Управление" на сервере в Azure Data Studio, где будут перечислены конечные точки служб.

![Конечная точка ADS](media/big-data-cluster-consume-apps/ads_end_point.png)

## <a name="generate-a-jwt-access-token"></a>Создание маркера доступа JWT

Чтобы обратиться к веб-службе на основе REST для развернутого приложения, сначала нужно создать маркер доступа JWT. URL-адрес маркера доступа зависит от версии кластера больших данных. 

|Версия |URL-адрес|
|------------|------|
|GDR1|  `https://[IP]:[PORT]/docs/swagger.json`|
|C пакетом обновления 1 (CU1) и более поздними версиями| `https://[IP]:[PORT]/api/v1/swagger.json`|

 Учитывая выходные данные предыдущего примера, выпуск CU4 и IP-адрес контроллера (10.1.1.3 в этом примере) и номер порта (30080), URL-адрес будет выглядеть следующим образом: 
 
 ```bash
    https://10.1.1.3 :30080/api/v1/swagger.json
```
 
> Сведения о версиях см. в [журнале выпусков](release-notes-big-data-cluster.md#release-history).

Откройте соответствующий URL-адрес в браузере, объединяя IP-адрес и порт, которые вы получили при выполнении указанной выше команды [`describe`](#retrieve-the-endpoint). Войдите в систему с теми же учетными данными, которые использовались для `azdata login`.

Вставьте содержимое `swagger.json` в [редактор Swagger](https://editor.swagger.io), чтобы понять, какие методы доступны.

![Swagger API](media/big-data-cluster-consume-apps/api_swagger.png)

Обратите внимание, что `app` является методом GET и для получения `token` использует метод POST. Так как проверка подлинности для приложений использует маркеры JWT, вам потребуется получить маркер с помощью привычного вам средства, чтобы выполнить запрос POST к методу `token`. В том же примере URL-адрес для получения маркера JWT будет выглядеть следующим образом:

 ```bash
    https://10.1.1.3 :30080/api/v1/token
```


Ниже приведен пример того, как именно это можно сделать в [Postman](https://www.getpostman.com/).

![Маркер Postman](media/big-data-cluster-consume-apps/postman_token.png)


В выходных данных этого запроса вы получите `access_token` JWT, который потребуется при вызове URL-адреса для запуска приложения.

## <a name="execute-the-app-using-the-restful-web-service"></a>Выполнение приложения с помощью веб-службы на основе REST

Существует несколько способов применить приложение в кластере больших данных. Вы можете использовать команду [azdata app run](app-create.md). В этом разделе показано, как использовать общие средства разработчика, такие как Postman, для выполнения приложения. 

Вы можете открыть URL-адрес для `swagger`, возвращенный при выполнении `azdata app describe --name [appname] --version [version]` в браузере, который должен быть похож на `https://[IP]:[PORT]/app/[appname]/[version]/swagger.json`. 

> [!NOTE]
> Вам потребуется войти в систему с теми же учетными данными, которые использовались для `azdata login`. В том же примере команда будет выглядеть следующим образом:

 ```bash
    azdata app describe --name add-app --version v1
```

Содержимое `swagger.json` можно вставить в [редактор Swagger](https://editor.swagger.io). Вы увидите, что веб-служба предоставляет метод `run`, пройдя через прокси приложения, который является веб-API, проверяющим подлинность пользователей, а затем направляющим запросы в приложения. Обратите внимание на базовый URL-адрес, отображаемый сверху. Вы можете использовать любое средство для вызова метода `run` (`https://[IP]:30778/api/app/[appname]/[version]/run`), передав параметры в текст запроса POST в виде JSON. 


В этом примере мы будем использовать [Postman](https://www.getpostman.com/). Перед вызовом нужно задать для `Authorization` значение `Bearer Token` и вставить полученный ранее маркер. Этим вы зададите заголовок своего запроса. См. снимок экрана ниже.

![Заголовки выполнения Postman](media/big-data-cluster-consume-apps/postman_run_1.png)

Затем в тексте запросов передайте параметры в приложение, которое вы вызываете, и присвойте `content-type` значение `application/json`.

![Текст выполнения Postman](media/big-data-cluster-consume-apps/postman_run_2.png)

При отправке запроса вы получите те же выходные данные, что и при запуске приложения с помощью `azdata app run`.

![Результат выполнения Postman](media/big-data-cluster-consume-apps/postman_result.png)

Вы успешно вызвали приложение через веб-службу. Интегрировать эту веб-службы в свое приложение можно аналогичным образом.


## <a name="next-steps"></a>Дальнейшие действия

Чтобы получить дополнительные сведения, см. статью [Мониторинг приложений в кластерах больших данных](app-monitor.md). Дополнительные примеры можно просмотреть в наборе [примеров развертывания приложений](https://aka.ms/sql-app-deploy).

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md).