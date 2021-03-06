---
title: Azure Logic Apps — бессерверные приложения
description: С помощью службы Azure Logic Apps можно создавать автоматические масштабируемые рабочие процессы для интеграции приложений и данных в различные облачные службы и локальные системы.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7ece3d30209713d42ee44ef9c1be1cf0fe82464a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577457"
---
# <a name="azure-logic-apps"></a>Azure Logic Apps

[Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps) предоставляет бессерверный модуль, позволяющий создавать автоматизированные рабочие процессы для интеграции приложений и данных в различные облачные службы и локальные системы. Рабочие процессы можно создать с помощью визуального конструктора. Вы можете активировать рабочие процессы на основе событий или таймеров, а также использовать соединители для интеграции приложений и обеспечения связи "бизнес — бизнес" (B2B). Служба Logic Apps легко интегрируется с Функциями Azure.

![Логотип Azure Logic Apps](./media/logic-apps-logo.png)

Logic Apps может не только подключать облачные службы (например, функции) к облачным ресурсам (например, к очередям и базам данных). Вы также можете управлять локальными рабочими процессами с помощью локального шлюза. Например, Logic Apps можно использовать для активации локальной хранимой процедуры SQL в ответ на облачное событие или условную логику в рабочем процессе. [Дополнительные сведения о подключении к локальным источникам данных с помощью локального шлюза данных](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway).

![Архитектура Logic Apps](./media/logic-apps-architecture.png)

Как и в случае с Функциями Azure, вы запускаете рабочие процессы Logic Apps с помощью триггера. Вы можете выбрать один из множества триггеров. На приведенном ниже снимке экрана показаны лишь несколько популярных триггеров из сотен доступных.

![Триггеры Logic Apps](./media/logic-app-triggers.png)

После запуска приложения можно использовать визуальный конструктор для шагов, циклов, условий и действий. Все данные, полученные на предыдущем шаге, доступны для использования на последующих шагах. Следующий рабочий процесс загружает URL-адреса из базы данных CosmosDB. Он находит URL-адреса с узлом `t.co`, а затем ищет их в Twitter. Если он находит соответствующие твиты, он обновляет документы, добавляя связанные твиты путем вызова функции.

![Рабочий процесс Logic Apps](./media/logic-app-workflow.png)

На панели мониторинга Logic Apps отображается журнал выполнения рабочих процессов и результатов их выполнения (успешное или нет). Можно перейти к любому заданному выполнению и проверить данные, используемые на каждом шаге, для устранения неполадок. Logic Apps также предоставляет существующие шаблоны, которые можно изменять и которые хорошо подходят для сложных рабочих процессов предприятия.

Дополнительные сведения см. в разделе [Документация по Azure Logic Apps](https://docs.microsoft.com/azure/logic-apps).

>[!div class="step-by-step"]
>[Назад](application-insights.md)
>[Вперед](event-grid.md)
