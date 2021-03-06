---
title: Подключение контекста
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: e237bb53c699fd4bf051876a378c31b73a038502
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451815"
---
# <a name="the-context-connection"></a>Подключение контекста
Проблема внутреннего доступа к данным встречается довольно часто. Речь идет о тех ситуациях, когда необходимо получить доступ к тому же серверу, на котором выполняется конкретная хранимая процедура или функция среды CLR. Один из вариантов состоит в том, чтобы создать соединение с использованием <xref:System.Data.SqlClient.SqlConnection>, задать строку соединения, в которой указан локальный сервер, и открыть соединение. В этом случае требуется указать учетные данные для входа в систему. Кроме того, соединение устанавливается в другом сеансе базы данных, отличном от сеанса хранимой процедуры или функции, поэтому оно может иметь другие параметры `SET`, находится в отдельной транзакции, не позволяет обращаться к используемым временным таблицам и т. д. Если управляемая хранимая процедура или функция выполняется в процессе SQL Server, причина этого состоит в том, что кто-то соединился с этим сервером и выполнил инструкцию SQL для вызова соответствующего процедуры или функции. В этой ситуации наверняка следует обеспечить выполнение хранимой процедуры или функции в контексте данного соединения вместе с осуществляемыми в нем транзакцией, параметрами `SET` и т. д. В этом состоит так называемое контекстное соединение.  
  
 Контекстное соединение позволяет выполнять инструкции Transact-SQL в том же контексте, в каком первоначально был вызван конкретный код. Более подробные сведения см. в электронной документации по SQL Server для используемой версии SQL Server.  
  
 **Документация по SQL Server**  
  
1. [Подключение контекста](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a>См. также раздел

- [Общие сведения об ADO.NET](../ado-net-overview.md)
