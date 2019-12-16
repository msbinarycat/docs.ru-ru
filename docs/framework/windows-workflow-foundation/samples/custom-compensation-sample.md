---
title: "Образец настраиваемой компенсации | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 385920da-9284-44bf-9fe9-0d87c7478ec5
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Образец настраиваемой компенсации
В этом образце показано, как использовать действие <xref:System.Activities.Statements.CompensableActivity> и его обработчик компенсации для определения пользовательской логики компенсации.В этом образце моделируется «Агентство по аренде грузовиков».  
  
## Подробные сведения об образце  
 Выполняется моделирование следующих шагов.  
  
1.  Пользователь запрашивает тарифы на аренду грузовика на заданную дату.  
  
2.  Агентство связывается с тремя компаниями, предоставляющими грузовики, и предлагает три тарифа.  
  
3.  Пользователь выбирает один из тарифов на аренду грузовика и переходит к оформлению заказа и оплате с помощью кредитной карты.  
  
4.  Приложение отменяет два других заказа.  
  
5.  Приложение взимает оплату за обслуживание, которая не возмещается для учетных записей, не относящихся к классу PREMIUM, если отмена происходит за 10 дней или менее до дня бронирования.  
  
6.  Приложение взимает стоимость аренды грузовика.  
  
7.  Приложение ждет наступления даты бронирования или отмены бронирования заказчиком, в зависимости от того, какое из событий наступит первым.  
  
8.  Если заказчик отменяет бронирование, выполняется пользовательская логика компенсации <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>, которая построена следующим образом.  
  
    1.  Если у заказчика нет учетной записи PREMIUM\-класса, и до дня бронирования остается 10 дней или меньше, то с него взимается стоимость обслуживания, в противном случае приложение возмещает стоимость обслуживания.  
  
    2.  Оставшиеся компенсируемые действия \(заказ грузовика \+ оплата заказа\) выполняются в соответствии с логикой компенсации по умолчанию, которая заключается в компенсации в порядке, обратном порядку выполнения.  
  
#### Настройка, построение и выполнение образца  
  
1.  Откройте решение CustomCompensation.sln в среде [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].Файл с решением находится в папке \\WF\\Basic\\Compensation\\CustomCompensation.  
  
2.  Чтобы построить решение, нажмите CTRL\+SHIFT\+B.  
  
3.  Нажмите CTRL \+ F5, чтобы запустить приложение.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере.Перед продолжением проверьте следующий каталог \(по умолчанию\).  
>   
>  `<диск_установки>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Образцы Windows Communication Foundation \(WCF\) и Windows Workflow Foundation \(WF\) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780), чтобы загрузить все образцы [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Этот образец расположен в следующем каталоге.  
>   
>  `<диск_установки>:\WF_WCF_Samples\WF\Basic\Compensation\CustomCompensation`  
  
## См. также