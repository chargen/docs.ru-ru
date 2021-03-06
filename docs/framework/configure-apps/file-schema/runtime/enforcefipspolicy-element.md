---
title: '&lt;enforceFIPSPolicy&gt; элемент'
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9040bf2548964cf6df5f4fd87ee9f6d979c7df1e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;enforceFIPSPolicy&gt; элемент
Указывает, нужно ли принудительно обеспечивать соблюдение требования конфигурации компьютера о том, что криптографические алгоритмы должны соответствовать стандартам FIPS.  
  
 \<Конфигурация > элемент  
\<Среда выполнения > элемент  
\<enforceFIPSPolicy > элемент  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|enabled|Обязательный атрибут.<br /><br /> Указывает, следует ли включить применение требования конфигурации компьютера, алгоритмов шифрования должна быть совместима с FIPS.|  
  
## <a name="enabled-attribute"></a>Атрибут enabled  
  
|Значение|Описание|  
|-----------|-----------------|  
|`true`|Если компьютер настроен требовать быть FIPS-совместимые алгоритмы шифрования, это требование применяется. Если класс реализует алгоритм, который не соответствует стандарту FIPS, конструкторы или `Create` методы для этого класса вызывать исключения, когда они запускаются на этом компьютере. Это значение по умолчанию.|  
|`false`|Алгоритмы шифрования, которые используются в приложении не требуются для соответствия FIPS, вне зависимости от конфигурации компьютера.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|`configuration`|Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.|  
|`runtime`|Содержит сведения о привязке сборок и сборке мусора.|  
  
## <a name="remarks"></a>Примечания  
 Начиная с .NET Framework 2.0, создания классов, реализующих алгоритмы шифрования управляется конфигурации компьютера. Если компьютер настроен требовать соответствие стандарту FIPS алгоритмы и класса, реализующего алгоритм, который не соответствует стандарту FIPS, любая попытка создать экземпляр этого класса создает исключение. Конструкторы вызывать <xref:System.InvalidOperationException> исключение, и `Create` методы создают исключение <xref:System.Reflection.TargetInvocationException> исключение внутренний <xref:System.InvalidOperationException> исключение.  
  
 Если приложение выполняется на компьютерах, на которых конфигурации требуют соответствия стандарту FIPS, и приложение использует алгоритм, который не соответствует стандарту FIPS, можно использовать этот элемент в файле конфигурации для предотвращения выполнения (CLR) из обеспечение соответствия FIPS. Этот элемент был введен в [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)].  
  
## <a name="example"></a>Пример  
 Приведенный ниже показано, как предотвратить обеспечение соответствия FIPS в среде CLR.  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также  
 [Схема параметров среды выполнения](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Схема файла конфигурации](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Модель криптографии](../../../../../docs/standard/security/cryptography-model.md)
