---
title: Форматы метаданных
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a3c6b1f551d1bff8c68a91f33e62df289d2078cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="metadata-formats"></a>Форматы метаданных
Форматы метаданных, поддерживаемые Windows Communication Foundation (WCF) в таблице ниже.  
  
## <a name="metadata-specifications-and-usage"></a>Спецификации и использование метаданных  
  
|Протокол|Спецификация и использование|  
|--------------|-----------------------------|  
|WSDL 1.1|[Язык описания веб-служб (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF использует язык описания веб-служб (WSDL) для описания служб.|  
|схема XML|[Схема XML, часть 2: Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861) и [XML Schema Part 1: Structures Second Edition](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> WCF использует схему XML для описания типов данных, используемые в сообщениях.|  
|WS Policy|[Политика веб служб 1.2 — платформа (WS-Policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Политика веб служб 1.5 — платформа](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF использует спецификации WS-Policy 1.2 или 1.5 с доменными утверждениями для описания требований и возможностей служб.|  
|Вложения WS Policy|[Политика веб служб 1.2 — вложение (WS-PolicyAttachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> WCF реализует вложениями WS-Policy для прикрепления выражений политики в различных областях на языке WSDL.|  
|WS Metadata Exchange|[Обмен метаданными веб служб (WS-MetadataExchange) версии 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF реализует спецификацию WS-MetadataExchange для извлечения схемы XML, WSDL и спецификации WS-Policy.|  
|Привязка WS Addressing для WSDL|[Web Services Addressing 1.0 - привязка WSDL](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> WCF реализует привязки WS-Addressing для WSDL для вложения сведений об адресации в WSDL.|  
  
## <a name="see-also"></a>См. также  
 [Протоколы веб-служб, поддерживаемые предоставляемыми системой привязками](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL и политика](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
