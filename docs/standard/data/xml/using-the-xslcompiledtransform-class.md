---
title: Использование класса XslCompiledTransform
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 6fc29b523e59590138cb7ca4db1b0da1bfee99c8
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937933"
---
# <a name="using-the-xslcompiledtransform-class"></a>Использование класса XslCompiledTransform
Класс <xref:System.Xml.Xsl.XslCompiledTransform> является обработчиком XSLT в платформе Microsoft .NET Framework. Этот класс используется для компиляции таблиц стилей и выполнения преобразований XSLT.  
  
> [!NOTE]
> Хотя класс <xref:System.Xml.Xsl.XslCompiledTransform> имеет более высокий общий уровень производительности, чем класс <xref:System.Xml.Xsl.XslTransform>, метод <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> класса <xref:System.Xml.Xsl.XslCompiledTransform> может выполняться медленнее, чем метод <xref:System.Xml.Xsl.XslTransform.Load%2A> класса <xref:System.Xml.Xsl.XslTransform> при первом вызове преобразования. Причина этого заключается в необходимости компиляции XSLT-файла перед его загрузкой. См. дополнительные сведения о [сравнении XslCompiledTransform и XslTransform](https://docs.microsoft.com/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)  
  
## <a name="in-this-section"></a>В этом разделе  
 [Входные данные для класса XslCompiledTransform](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Описываются доступные входные параметры XSLT.  
  
 [Параметры вывода в классе XslCompiledTransform](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Описываются доступные выходные параметры XSLT.  
  
 [Разрешение внешних ресурсов в ходе обработки XSLT](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Обсуждается использование класса <xref:System.Xml.XmlResolver> для разрешения внешних ресурсов.  
  
 [Расширение таблиц стилей XSLT](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 Обсуждается поддержка расширений XSLT.  
  
|||  
|-|-|  
|[Устранимые ошибки XSLT](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|Содержит список поведений по выбору, допустимых в соответствии с рекомендациями консорциума W3C по XSLT 1.0, и описывает, каким образом эти поведения обрабатываются классом <xref:System.Xml.Xsl.XslCompiledTransform>.|  
|[Как преобразовать фрагмент узла](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Описывает процесс преобразования фрагмента узла.|  
  
## <a name="related-sections"></a>Связанные разделы  
 [Миграция с класса XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Обсуждается перенос кода из класса <xref:System.Xml.Xsl.XslTransform>.  
  
## <a name="see-also"></a>См. также:

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
