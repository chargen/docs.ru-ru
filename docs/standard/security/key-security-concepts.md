---
title: "Key Security Concepts | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "unauthorized access"
  - "permissions [.NET Framework]"
  - "security [.NET Framework], about security"
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: 22
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 20
---
# Key Security Concepts
Microsoft .NET Framework предлагает прозрачность безопасности, управление доступом для кода и безопасность на основе ролей для решения проблем безопасности, связанных с мобильным кодом, и предоставления поддержки, которая позволяет компонентам определять, какие пользователи авторизованы для выполнения действий.  Эти механизмы безопасности используют простую согласованную модель, чтобы разработчики, знакомые с управлением доступом для кода, могли легко использовать безопасность на основе ролей и наоборот.  Как управление доступом для когда, так и безопасность на основе ролей реализованы при помощи общей инфраструктуры, предоставленной средой CLR.  
  
> [!NOTE]
>  Начиная с [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], прозрачность безопасности является механизмом применения по умолчанию.  Прозрачность безопасности отделяет код, выполняемый в рамках приложения, от кода, выполняемого в рамках инфраструктуры.  Дополнительные сведения см. в разделе [Security\-Transparent Code](../../../docs/framework/misc/security-transparent-code.md).  
  
 Так как они используют одну и ту же модель и инфраструктуру, управление доступом для кода и безопасность на основе ролей совместно используют некоторые базовые понятия, которые описываются в этом разделе.  Убедитесь, что вы знакомы с этими понятиями, прежде чем приступить к чтению документации по управлению доступом для кода и безопасности на основе ролей в .NET Framework.  
  
## Разрешения безопасности  
 Среда CLR позволяет коду выполнять только те операции, на которые у него есть разрешение.  Среда выполнения использует объекты, называемые разрешениями, для обеспечения выполнения ограничений в управляемом коде.  Эта среда выполнения предоставляет встроенные классы разрешений в нескольких пространствах имен, а также поддерживает проектирование и реализацию настраиваемых классов разрешений.  
  
 Существует два типа разрешений, каждый из которых имеет свое определенное назначение.  
  
-   Разрешения для доступа к коду контролируют доступ к защищенному ресурсу или возможность выполнения защищенной операции.  
  
-   Права доступа на основе ролей предоставляют механизм для определения, имеет ли пользователь \(или агент, действующий от имени пользователя\) конкретное удостоверение или является ли он членом указанной роли.  <xref:System.Security.Permissions.PrincipalPermission> — это единственное разрешение безопасности на основе ролей.  
  
 Разрешения безопасности могут определяться в форме класса разрешений \(принудительной безопасности\) или атрибута, представляющего класс разрешений \(декларативной безопасности\).  Базовый класс для разрешений безопасности — <xref:System.Security.CodeAccessPermission?displayProperty=fullName>; базовый класс для атрибутов разрешений безопасности — <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName>.  
  
 Приложению в виде сборки предоставляется набор разрешений во время его загрузки в домен приложения.  Предоставление прав обычно выполняется с помощью заранее заданных наборов разрешений, определяемых методом <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=fullName>.  Набор прав определяет разрешения, которыми обладает код.  Среда выполнения предоставляет разрешения на основе исходного расположения кода \(например, на локальном компьютере, в местной интрасети или в Интернете\).  Коду также могут быть предоставлены специальные разрешения, если он загружается в песочницу.  Дополнительные сведения о выполнении кода в песочнице см. в разделе [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md).  
  
 Далее приведены основные способы использования разрешений.  
  
-   Код библиотеки может требовать, чтобы вызывающие его объекты имели определенные разрешения.  Если вы помещаете <xref:System.Security.CodeAccessPermission.Demand%2A> для разрешения в своем коде, любой код, использующий ваш код, должен иметь это разрешение для запуска.  Требования можно использовать для определения наличия у вызывающих объектов доступа к определенным ресурсам или для обнаружения удостоверения вызывающего объекта.  
  
-   Код может использовать разрешения для запрета доступа к ресурсам, которые необходимо защитить.  Вы можете использовать <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> для указания ограниченного набора разрешений, неявно запрещая все остальные разрешения.  Тем не менее, мы не рекомендуем использовать <xref:System.Security.Permissions.SecurityAction> для запрета доступа с целью защиты от умышленного злоупотребления.  Вызванные сборки, имеющие неявно отклоненные разрешения в своем наборе разрешений, могут переопределять отклоненные разрешения, выполнив <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> для всех разрешений, которые они хотят использовать.  Например, если предоставлено только разрешение <xref:System.Security.Permissions.UIPermission>, и вызывается сборка, изначально имеющая разрешение <xref:System.Security.Permissions.FileIOPermission>, эта сборка может просто выполнить <xref:System.Security.Permissions.SecurityAction> для <xref:System.Security.Permissions.FileIOPermission>, а затем выполнить операции с файлами.  Единственный способ надежно защитить ресурсы от ненадежного кода в связанных сборках заключается в выполнении этого кода с набором прав, который не включает эти разрешения.  
  
### Разрешения для доступа к коду  
 Разрешения для доступа к коду — это объекты разрешений, которые используются для защиты ресурсов и операций от несанкционированного использования.  Они являются основной частью механизма среды CLR для применения ограничений безопасности в управляемом коде.  
  
 Каждое разрешение для доступа к коду представляет одно из следующих прав.  
  
-   Право на доступ к защищенному ресурсу, такому как файлы или переменные среды.  
  
-   Право выполнять защищенную операцию, такую как доступ к неуправляемому коду.  
  
 Все разрешения для доступа к коду могут быть запрошены или затребованы кодом, а среда выполнения определяет, какие разрешения, если таковые имеются, следует предоставить коду.  
  
 Каждое разрешение для доступа к коду является производным от класса <xref:System.Security.CodeAccessPermission>, что означает, что все разрешения для доступа к коду имеют методы, такие как **Demand**, **Assert**, **Deny**, **PermitOnly**, **IsSubsetOf**, **Intersect** и **Union**.  
  
> [!IMPORTANT]
>  В [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] удалена поддержка среды выполнения для принудительного применения запросов разрешений <xref:System.Security.Permissions.SecurityAction>, <xref:System.Security.Permissions.SecurityAction>, <xref:System.Security.Permissions.SecurityAction> и <xref:System.Security.Permissions.SecurityAction>.  Эти запросы не должны использоваться в коде, основанном на [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] или более поздней версии.  Дополнительные сведения об этом и других изменениях см. в разделе [Изменения системы безопасности](../../../docs/framework/security/security-changes.md).  
  
### Разрешения безопасности на основе ролей  
 <xref:System.Security.Permissions.PrincipalPermission> — это разрешение безопасности на основе ролей, которое может использоваться для определения, имеет ли пользователь указанное удостоверение, или является ли он членом указанной роли.  **PrincipalPermission** — это единственное разрешение безопасности на основе ролей, предоставляемые библиотекой классов .NET Framework.  
  
## Безопасность типа и безопасность  
 Код с безопасностью типа имеет доступ только к областям памяти, авторизованным для доступа.  \(В данном разделе безопасность типа относится исключительно к безопасности типа памяти, и ее не следует путать с безопасностью типа в широком смысле.\) Например, код с безопасностью типа не может читать значения из закрытых полей другого объекта.  Он обращается к типам только строго определенными, допустимыми способами.  
  
 Во время JIT\-компиляции дополнительный процесс проверки проверяет метаданные и MSIL метода для JIT\-компиляции в машинный код, чтобы убедиться, что они являются типобезопасными.  Этот процесс не выполняется, если код имеет разрешение на пропуск проверки.  Дополнительные сведения о проверке см. в разделе [Процесс управляемого выполнения](../../../docs/standard/managed-execution-process.md).  
  
 Хотя проверка безопасности типа не обязательна для запуска управляемого кода, безопасность типа играет ключевую роль в изоляции сборок и обеспечении безопасности.  Если код является типобезопасным, среда CLR может полностью изолировать сборки друг от друга.  Эта изоляция помогает обеспечить отсутствие отрицательного влияния сборок друг на друга и повышает надежность приложений.  Компоненты с безопасностью типа могут безопасно выполняться в одном процессе, даже если они имеют доверие на разных уровнях.  Если код не является типобезопасным, могут возникать нежелательные побочные эффекты.  Например, среда выполнения не может препятствовать вызову машинного \(неуправляемого\) кода со стороны управляемого кода и выполнению управляемым кодом нежелательных операций.  Если код является типобезопасным, механизм обеспечения безопасности среды выполнения гарантирует, что он не будет иметь доступ к машинному коду при отсутствии соответствующего разрешения.  Чтобы код без безопасности типа мог запускаться, ему необходимо предоставить разрешение <xref:System.Security.Permissions.SecurityPermission> с переданным элементом перечисления <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>.  
  
 Дополнительные сведения см. в разделе [NIB: Writing Verifiably Type\-Safe Code](http://msdn.microsoft.com/ru-ru/d18f10ef-3b48-4f47-8726-96714021547b).  
  
## Участник  
 Участник представляет удостоверение и роль пользователя и действует от имени пользователя.  Безопасность на основе ролей в .NET Framework поддерживает три вида участников.  
  
-   Универсальные участники представляют пользователей и роли, которые существуют независимо от пользователей и ролей Windows.  
  
-   Участники Windows представляют пользователей Windows и их роли \(или их группы Windows\).  Участник Windows может олицетворять другого пользователя, что означает, что этому участнику разрешен доступ к ресурсу от имени пользователя при предоставлении удостоверения, которое принадлежит этому пользователю.  
  
-   Настраиваемые участники могут определяться приложением любым способом, который необходим для данного конкретного приложения.  При этом можно расширять базовое определение удостоверения и ролей участника.  
  
 Дополнительные сведения см. в разделе [Principal and Identity Objects](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## Аутентификация  
 Проверка подлинности \(аутентификация\) — это процесс обнаружения и проверки удостоверения участника путем проверки учетных данных пользователя и проверки этих учетных данных в отношении некоторого центра сертификации.  Сведения, полученные во время проверки подлинности, можно напрямую использовать в коде.  Для проверки подлинности текущего пользователя и определения, следует ли предоставить этому участнику доступ к коду, можно также использовать безопасность на основе ролей в .NET Framework.  Примеры проверки подлинности участника для конкретных ролей см. в описании перегрузок метода <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=fullName>.  Например, можно использовать перегрузку <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=fullName>, чтобы определить, является ли текущий пользователь членом группы «Администраторы».  
  
 В настоящее время используется ряд механизмов проверки подлинности, многие из которых могут быть использованы вместе с безопасностью на основе ролей в .NET Framework.  Некоторые из наиболее часто используемых механизмов — это обычная проверка подлинности, дайджест\-проверка подлинности, проверка подлинности по паспорту, проверка подлинности операционной системы \(например, NTLM или Kerberos\) или механизмы, определяемые приложением.  
  
### Пример  
 Следующий пример требует, чтобы активный участник был администратором.  Параметр `name` имеет значение `null`, что позволяет любому пользователю с правами администратора проходить требование.  
  
> [!NOTE]
>  В Windows Vista привилегии пользователя определяются контролем учетных записей \(UAC\).  Члену встроенной группы "Администраторы" присваивается два маркера доступа на время выполнения: маркер доступа обычного пользователя и маркер доступа администратора.  По умолчанию назначена роль обычного пользователя.  Чтобы выполнить код, требующий прав администратора, необходимо сначала повысить права от прав стандартного пользователя до прав администратора.  Это можно сделать при запуске приложения, , щелкнув значок приложения правой кнопкой мыши и указав, что приложение должно запускаться от имени администратора.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 Следующий пример демонстрирует, как определить удостоверение участника и доступные для него роли.  Приложение в этом примере должно проверять, что текущий пользователь имеет роль, которая позволяет использовать приложение.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## Авторизация  
 Авторизация — это процесс определения, разрешено ли участнику выполнять запрошенное действие.  Авторизация происходит после проверки подлинности и использует сведения об удостоверении и ролях участника, чтобы определить, к каким ресурсам имеет доступ этот участник.  Для реализации авторизации можно использовать безопасность на основе ролей в .NET Framework.  
  
## Вопросы безопасности, связанные с использованием ключевых слов internal virtual  
 Никогда не следует строить безопасность приложения на основе члена, помеченного с помощью модификатора [internal](../Topic/internal%20\(C%23%20Reference\).md) [virtual](../Topic/virtual%20\(C%23%20Reference\).md) в C\# \(модификатора [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md) [Friend](../Topic/Friend%20\(Visual%20Basic\).md) в Visual Basic\).  Хотя члены, помеченные этими модификаторами, могут быть переопределены только другими членами в текущей сборке, данное правило применяется только в языках C\# и Visual Basic.  Среда выполнения не обеспечивает применение этого правила.  Таким образом, можно переопределить элементы, отмеченные как **internal virtual** в C\# и **Overloads Overridable Friend** в Visual Basic, с помощью MSIL или любого другого языка, который не обеспечивает применение этого правила.  
  
## См. также  
 [Key Security Concepts](../../../docs/standard/security/key-security-concepts.md)