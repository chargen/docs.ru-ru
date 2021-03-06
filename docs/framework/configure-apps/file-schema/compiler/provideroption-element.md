---
title: '&lt;providerOption&gt; элемент'
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fa3410cc2c8812c59528676bfad6cd7e887c5f73
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="ltprovideroptiongt-element"></a>&lt;providerOption&gt; элемент
Задает атрибуты версии компилятора для поставщика языка.  
  
 \<Элемент конфигурации >  
\<System.CodeDom-элемент >  
\<компиляторы элемент >  
\<Компилятор > элемент  
\<providerOption > элемент  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`name`|Обязательный атрибут.<br /><br /> Указывает имя параметра; Например, «CompilerVersion».|  
|`value`|Обязательный атрибут.<br /><br /> Указывает значение для параметра; Например «v3.5».|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Корневой элемент в любом файле конфигурации, который используется средой CLR и приложениями .NET Framework.|  
|[\<System.CodeDom > элемент](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Задает параметры конфигурации компилятора для доступных поставщиков языков.|  
|[\<компиляторы > элемент](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Контейнер для элементов конфигурации компилятора; содержит ноль или более `<compiler>` элементов.|  
|[Элемент \<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Задает атрибуты конфигурации компилятора для поставщика языка.|  
  
## <a name="remarks"></a>Примечания  
 В платформе .NET Framework версии 3.5 поставщики кода в объектной модели документов кода (CodeDOM) поддерживают параметры поставщика с использованием `<providerOption>` элемента.  
  
 .NET Framework 3.5 включает обновленные сборки .NET Framework 2.0 и обеспечивает новые сборки версии 3.5, которые содержат новые типы. Поставщики кода Microsoft C# и Visual Basic находятся в сборках .NET Framework 2.0, но были обновлены для поддержки компиляторов версии 3.5. По умолчанию обновленные поставщики кода создать код для компиляторов версии 2.0. Можно использовать `<providerOption>` элемент для изменения целевой версии компилятора 3.5. Чтобы сделать это, укажите «CompilerVersion» для `name` атрибут и «v3.5» для `value` атрибута. Номер версии с прописной буквы «v» должно предшествовать.  
  
 Версии спецификации можно сделать глобальный путем добавления `<providerOption>` элемент для .NET Framework 2.0 Machine.config или корневом файле Web.config. При обновлении версии компилятора по умолчанию 3.5 в файле Machine.config, можно изменить его обратно в 2.0 на основе каждого приложения с помощью `<providerOption>` в файле конфигурации приложения.  
  
 Исполнители поставщик codeDOM кода можно обрабатывать пользовательские параметры, предоставляющий конструктор, который принимает `providerOptions` параметр типа <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Пример  
 Ниже приведен пример, как указать, следует использовать версии 3.5 поставщика кода C#.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>См. также  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Схема файла конфигурации](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<компиляторы > элемент](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [Указание полных имен типов](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [Компилятор элемент для компиляторов для компиляции (схема параметров ASP.NET)](http://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
