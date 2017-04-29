---
title: "Ресурсы XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "повторное использование ресурсов"
  - "ресурсы, повторное использование"
  - "повторное использование часто определяемых объектов"
  - "XAML, повторное использование ресурсов"
ms.assetid: 91580b89-a0a8-4889-aecb-fddf8e63175f
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# Ресурсы XAML
Ресурс — это объект, который можно повторно использовать в разных местах приложения. Примерами ресурсов являются кисти и стили. В этом обзоре описывается использование ресурсов в [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Можно также создать и доступ к ресурсам с помощью кода или попеременно кодом и [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Дополнительные сведения см. в разделе [ресурсы и код](../../../../docs/framework/wpf/advanced/resources-and-code.md).  
  
> [!NOTE]
>  Файлы ресурсов, описанных в этом разделе отличаются от файлы ресурсов, описанные в [ресурса приложения WPF, содержимое и файлы данных](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md) и отличаются от внедренных или связанных ресурсов, приведенных в [управление ресурсами приложения (.NET)](../Topic/Managing%20Application%20Resources%20\(.NET\).md).  
  
   
  
<a name="usingresources"></a>   
## <a name="using-resources-in-xaml"></a>Использование ресурсов в XAML  
 В следующем примере определяется <xref:System.Windows.Media.SolidColorBrush> как ресурс в корневом элементе страницы. В примере затем ссылается на ресурс и использует его для задания свойства нескольких дочерних элементов, включая <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Controls.TextBlock>и <xref:System.Windows.Controls.Button>.  
  
 [!code-xml[FEResourceSH_snip#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xaml)]  
  
 Каждый элемент уровня инфраструктуры ( <xref:System.Windows.FrameworkElement> или <xref:System.Windows.FrameworkContentElement>) имеет <xref:System.Windows.FrameworkElement.Resources%2A> свойство, которое является свойство, которое содержит ресурсы (как <xref:System.Windows.ResourceDictionary>), определяющий ресурс. Можно определить ресурсы в любом элементе. Однако ресурсы, наиболее часто определяются в корневом элементе, который является <xref:System.Windows.Controls.Page> в примере.  
  
 Каждый ресурс в словаре ресурсов должен иметь уникальный ключ. При определении ресурсов в разметке, уникальный ключ через назначается [директива x: Key](../../../../docs/framework/xaml-services/x-key-directive.md). Как правило ключ является строкой; Тем не менее можно также задать его значение другие типы объектов с помощью соответствующих расширений разметки. Нестроковые ключи для ресурсов используются определенными функциональными областями [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], важнее всего это для стилей, компонентных ресурсов и стилей данных.  
  
 После определения ресурса можно ссылаться на ресурс, который используется для значения свойства с помощью синтаксиса расширения разметки ресурсов, который указывает имя ключа, например:  
  
 [!code-xml[FEResourceSH_snip#KeyNameUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#keynameusage)]  
  
 В предыдущем примере при [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] загрузчика обрабатывает значение `{StaticResource MyBrush}` для <xref:System.Windows.Controls.Control.Background%2A> свойство <xref:System.Windows.Controls.Button>, логика поиска ресурсов сначала проверяет наличие в словаре ресурсов <xref:System.Windows.Controls.Button> элемент. Если <xref:System.Windows.Controls.Button> нет определения ключа ресурса `MyBrush` (нет, его коллекция ресурсов пуста), затем подстановка проверяет родительский элемент <xref:System.Windows.Controls.Button>, который является <xref:System.Windows.Controls.Page>. Таким образом, при определении ресурса в <xref:System.Windows.Controls.Page> корневого элемента, все элементы в логическом дереве <xref:System.Windows.Controls.Page> доступ к нему и повторно использовать тот же ресурс для задания значения любого свойства, принимает <xref:System.Type> , представляющий ресурс. В предыдущем примере, также `MyBrush` ресурсов задает два различных свойства: <xref:System.Windows.Controls.Control.Background%2A> из <xref:System.Windows.Controls.Button>и <xref:System.Windows.Shapes.Shape.Fill%2A> из <xref:System.Windows.Shapes.Rectangle>.  
  
<a name="staticdynamic"></a>   
## <a name="static-and-dynamic-resources"></a>Статические и динамические ресурсы  
 Ресурс можно ссылаться как на статический или динамический ресурс. Это делается с помощью [расширение разметки StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) или [расширение разметки DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Расширения разметки — это функция [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] помощью которой можно задать ссылку на объект с расширением разметки обработки строки атрибута и возвращает объект [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] загрузчика. Дополнительные сведения о поведении расширения разметки см. в разделе [расширения разметки и WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 При использовании расширения разметки обычно предоставляют один или несколько параметров в виде строки, обрабатываются, определенное расширение разметки, а не проверяется в контексте задаваемое свойство. [Расширение разметки StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) обрабатывает ключ путем поиска значения для этого ключа во всех доступных словарях ресурсов. Это происходит во время загрузки, которая является моментом времени, когда процессу загрузки необходимо присвоить значение свойству, которое принимает ссылку на статический ресурс. [Расширение разметки DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) вместо процессы ключ путем создания выражения и выражения остается необработанным, пока приложение фактически не будет запущено, в этот момент выражение вычисляется и получается значение.  
  
 При ссылке на ресурсы следующие соображения могут повлиять на выбор использовать ссылку на статический ресурс или ссылка на динамический ресурс:  
  
-   Общая схема способ создания ресурсов для приложения (постранично, в приложении, в свободном [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], в сборке только ресурсов).  
  
-   Функциональные возможности приложения: является ли обновление ресурсов в режиме реального времени частью требований приложения?  
  
-   Соответствующее поведение подстановки этого ссылочного типа ресурса.  
  
-   Определенное свойство или тип ресурса и собственное поведение этих типов.  
  
### <a name="static-resources"></a>Статические ресурсы  
 Ссылки на статические ресурсы работы наилучшим образом в следующих случаях:  
  
-   Структура приложения концентрирует большую часть всех его ресурсов в страницу или ресурса уровня приложения словарей. Ссылки на статические ресурсы не будут повторно обработаны в зависимости от поведения среды выполнения, например, перезагрузки страницы и поэтому может быть производительность требовательных к отсутствию большого количества ссылок на динамический ресурс, когда они не нужны в структуре ресурсов и приложения.  
  
-   Значение свойства, не <xref:System.Windows.DependencyObject> или <xref:System.Windows.Freezable>.  
  
-   Вы создаете словаря ресурсов, который будет скомпилирован в DLL и упакованы как часть приложения или совместно использоваться приложениями.  
  
-   Создании темы для пользовательского элемента управления и определении ресурсов, используемых в темах. В этом случае обычно требуется поведение подстановки динамического ресурса ссылки, вместо этого требуется поведение ссылку статический ресурс так, что подстановка является прогнозируемой и самодостаточной для темы. На динамический ресурс ссылку, даже ссылка в теме остается необработанной до времени выполнения, и существует вероятность того, что при применении темы некоторые локальные элементы переопределят ключ, на который тема пытается сослаться и локальный элемент потерпит неудачу перед самой темой в уточняющем запросе. В этом случае тема будет вести себя ожидаемым образом.  
  
-   Использовании ресурсов для задания большого количества свойств зависимости. Свойства зависимостей есть эффективное кэширование значений, как задано системой свойств, поэтому если предоставить значение для свойства зависимостей, которое может быть вычислено во время загрузки, свойство зависимости не потребуется проверка пересчета выражений и оно сможет вернуть последнее эффективное значение. Этот метод может оказаться выигрыш в производительности.  
  
-   Необходимо изменить основной ресурс для всех объектов-получателей, или требуется поддерживать отдельные записываемые экземпляры для каждого объекта-получателя с помощью [x: Shared Attribute](../../../../docs/framework/xaml-services/x-shared-attribute.md).  
  
#### <a name="static-resource-lookup-behavior"></a>Поведение подстановки статического ресурса  
  
1.  Процесс подстановки ищет запрошенный ключ в словаре ресурсов, определяется элемент, который задает для свойства.  
  
2.  Затем процесс подстановки обходит логическое дерево снизу вверх, родительский элемент и его словарь ресурсов. Это продолжается, пока не будет достигнут корневой элемент.  
  
3.  Далее проверяются ресурсы приложения. Ресурсы приложения — это ресурсы в словаре ресурсов, который определяется <xref:System.Windows.Application> объекта для вашего [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] приложения.  
  
 Ссылки на статический ресурс из словаря ресурсов должны ссылаться ресурс, который уже определен лексически до ссылки на ресурс. Прямых ссылок не удается разрешить ссылку на статический ресурс. По этой причине при использовании ссылки на статический ресурс, необходимо разработать структуру словаря ресурсов таким образом, что ресурсы, предназначенные для использования ресурсами определены на уровне или в начале каждого соответствующего словаря ресурсов.  
  
 Подстановку статических ресурсов можно расширить в темы или в системные ресурсы, но это поддерживается только потому, что [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] загрузчик задерживает запрос. Задержка необходима, чтобы тема среды выполнения в момент загрузки страницы правильно применялась приложения. Тем не менее ссылок на статические ресурсы для ключей, которые существуют только в теме или как системные ресурсы не рекомендуются. Это потому, что такие ссылки не будут повторно обработаны при изменении темы пользователем в режиме реального времени. Ссылка на динамический ресурс обеспечивает повышенную надежность, при запросе темы или системных ресурсов. Это исключение, когда элемент темы сам запрашивает другой ресурс. Эти ссылки должны быть статическими по причинам, упомянутым ранее.  
  
 Зависит от поведения исключения, если статическая ссылка на ресурс не найден. Если ресурс был задержан, исключение возникает во время выполнения. Если ресурс не был задержан, исключение возникает во время загрузки.  
  
### <a name="dynamic-resources"></a>Динамические ресурсы  
 Динамические ресурсы лучше всего подходят для следующих случаев:  
  
-   Значение ресурса зависит от условий, которые неизвестны до времени выполнения. Сюда входят системные ресурсы или ресурсы, которые в противном случае устанавливаются пользователем. Например, можно создать значения установщика, которые ссылаются на системные свойства, как представлено <xref:System.Windows.SystemColors>, <xref:System.Windows.SystemFonts>, или <xref:System.Windows.SystemParameters>. Эти значения являются действительно динамическими, так как они в конечном счете берутся из среды выполнения пользователя и операционной системы. Может также потребоваться темы уровня приложения, которые можно изменить, где доступ к ресурсу уровня страницы также должен отследить изменения.  
  
-   При создании или ссылке на стили темы для пользовательского элемента управления.  
  
-   Когда планируется настроить содержимое <xref:System.Windows.ResourceDictionary> во время существования приложения.  
  
-   Имеется сложная структура ресурсов с взаимозависимости, где могут потребоваться прямая ссылка. Ссылки на статические ресурсы не поддерживают дальнейшие ссылки, но ссылки на динамические ресурсы поддерживают их, так как ресурс не нужно пересчитывать до времени выполнения и прямых ссылок, следовательно, не релевантны.  
  
-   При ссылке на особенно большой с точки зрения компиляции или рабочего множества и ресурс не может быть использована немедленно при загрузке страницы. Ссылки на статические ресурсы всегда загружаются из [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] при загрузке страницы; однако ссылка на динамический ресурс не загружается до фактического использования.  
  
-   Вы создаете стиль, где значения установщика могут браться из других значений, которые влияют темы или другие параметры пользователя.  
  
-   Ресурсы применяются к элементам, которые может быть изменен порядок наследования в логическом дереве во время существования приложения. Изменение родителя также потенциально изменяет область поиска ресурса, поэтому ресурса для элемента с измененным порядком наследования пересчета на основе новой области, всегда используйте ссылку на динамический ресурс.  
  
#### <a name="dynamic-resource-lookup-behavior"></a>Поведение подстановки динамического ресурса  
 Поведение подстановки ресурса для ссылки на динамический ресурс аналогично поведению подстановки в коде при вызове <xref:System.Windows.FrameworkElement.FindResource%2A> или <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  
  
1.  Процесс подстановки ищет запрошенный ключ в словаре ресурсов, определяется элемент, который задает для свойства.  
  
    -   Если элемент определяет <xref:System.Windows.FrameworkElement.Style%2A> свойства <xref:System.Windows.Style.Resources%2A> dictionary внутри <xref:System.Windows.Style> проверяется.  
  
    -   Если элемент определяет <xref:System.Windows.Controls.Control.Template%2A> свойства <xref:System.Windows.FrameworkTemplate.Resources%2A> dictionary внутри <xref:System.Windows.FrameworkTemplate> установлен.  
  
2.  Затем процесс подстановки обходит логическое дерево снизу вверх, родительский элемент и его словарь ресурсов. Это продолжается, пока не будет достигнут корневой элемент.  
  
3.  Далее проверяются ресурсы приложения. Ресурсы приложения — это ресурсы в словаре ресурсов, который определяется <xref:System.Windows.Application> объекта для вашего [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] приложения.  
  
4.  Для текущей активной темы проверяется словарь ресурсов темы. Если тема изменяется во время выполнения, это выражение заново вычисляется значение.  
  
5.  Проверяются системные ресурсы.  
  
 Поведение исключения (если имеется) варьируется:  
  
-   Если ресурс был запрошен пользователем <xref:System.Windows.FrameworkElement.FindResource%2A> вызова и не найден, возникает исключение.  
  
-   Если ресурс был запрошен пользователем <xref:System.Windows.FrameworkElement.TryFindResource%2A> вызова и не найден, исключение не создается, но возвращаемое значение является `null`. Если задаваемое свойство не принимает `null`, по-прежнему возможно, возникнет исключение глубже (это зависит от задания отдельного свойства).  
  
-   Если ресурс запрошен по ссылке на динамический ресурс в [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], не найден, то поведение зависит от общей системы свойств, но общее поведение таково, как если бы не свойство произошло операции задания на уровне, где существует ресурс. Например при попытке задать фон на отдельном элементе кнопки с помощью ресурса, который не может быть вычислено, то не происходит задания значения, но эффективное значение по-прежнему могут поступать из других участников приоритет системы и значение свойства. Например значение фона по-прежнему могут быть из локально определенного стиля кнопки, или из стиля темы. Для свойств, не определенных стилями темы после неудачи обработки ресурса эффективное значение источником может быть значение по умолчанию в метаданных свойства.  
  
#### <a name="restrictions"></a>Ограничения  
 Ссылки на динамический ресурс есть некоторые важные ограничения. Должно быть значение true, по крайней мере одно из следующих:  
  
-   Задаваемое свойство должно быть свойством <xref:System.Windows.FrameworkElement> или <xref:System.Windows.FrameworkContentElement>. Свойство должна опираться на <xref:System.Windows.DependencyProperty>.  
  
-   Ссылка указывает на значение в <xref:System.Windows.Style><xref:System.Windows.Setter>.  
  
-   Задаваемое свойство должно быть свойством <xref:System.Windows.Freezable> , предоставляется как значение либо <xref:System.Windows.FrameworkElement> или <xref:System.Windows.FrameworkContentElement> свойства, или <xref:System.Windows.Setter> значение.  
  
 Поскольку задаваемое свойство должно быть <xref:System.Windows.DependencyProperty> или <xref:System.Windows.Freezable> свойства, большинство изменений свойств может распространяться на пользовательский Интерфейс, поскольку изменение свойства (измененное значение динамического ресурса) подтверждается системой свойств. Большинство элементов управления включает логику, которая принудительно создаст новый макет элемента управления, если <xref:System.Windows.DependencyProperty> изменений и свойство может повлиять на макет. Однако не все свойства, имеющие [расширение разметки DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) со своим значением, гарантированно предоставляют значение таким образом, что они обновляются в режиме реального времени в пользовательском Интерфейсе. Эти функциональные возможности по-прежнему могут различаться в зависимости от свойства, а также в зависимости от типа, которому принадлежит свойство, или даже от логической структуры приложения.  
  
<a name="stylesimplicitkeys"></a>   
## <a name="styles-datatemplates-and-implicit-keys"></a>Стили, DataTemplates и неявные ключи  
 Ранее было отмечено, что у всех элементов в <xref:System.Windows.ResourceDictionary> должен иметь ключ. Однако, не означает, что все ресурсы должны иметь явные `x:Key`. Некоторые типы объектов поддерживают неявный ключ, если он определен как ресурс, где значение ключа связано значение другого свойства. Это называется неявным ключом, в то время как `x:Key` атрибута является явным ключом. Можно перезаписать любой неявный ключ, указав явный ключ.  
  
 Одним очень важным скриптом для ресурсов является определение <xref:System.Windows.Style>. На самом деле <xref:System.Windows.Style> почти всегда определяется как запись в словаре ресурсов, поскольку стили по своей природе предназначены для повторного использования. Дополнительные сведения о стилях см. в разделе [Стилизация и использование шаблонов](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
 Стили для элементов управления можно создать с помощью и ссылаться с помощью неявного ключа. Стили темы, определяющие внешний вид элемента управления по умолчанию полагаются на этот неявный ключ. Неявный ключ с точки зрения запроса представляет <xref:System.Type> самого элемента управления. Неявный ключ с точки зрения определения ресурса представляет <xref:System.Windows.Style.TargetType%2A> стиля. Таким образом, если создается тема для пользовательских элементов управления, стили, которые взаимодействуют с существующими стилями темы, необходимо указать [директива x: Key](../../../../docs/framework/xaml-services/x-key-directive.md) для этого <xref:System.Windows.Style>. И если вы хотите использовать стили для тем, не нужно задавать стиль вообще. Например, следующее определение стиля работает, даже если <xref:System.Windows.Style> ресурс не имеет ключа:  
  
 [!code-xml[FEResourceSH_snip#ImplicitStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page2.xaml#implicitstyle)]  
  
 Что действительно стилем ключ: неявный ключ `typeof(` <xref:System.Windows.Controls.Button>`)`. В разметке, можно указать <xref:System.Windows.Style.TargetType%2A> в качестве типа имени (или при необходимости можно использовать [{x: Type...}](../../../../docs/framework/xaml-services/x-type-markup-extension.md) Чтобы вернуть <xref:System.Type>.  
  
 Через механизмы стиля темы по умолчанию, используемые [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], что стиль будет применен как стиль среды выполнения для <xref:System.Windows.Controls.Button> на странице хотя <xref:System.Windows.Controls.Button> сама не пытается задать его <xref:System.Windows.FrameworkElement.Style%2A> свойство или конкретную ссылку на ресурс стиля. Стиль, определенный на странице, находится в последовательности подстановки раньше, чем стиль словаря темы, с помощью того же ключа стиля словаря темы. Можно просто задать `<Button>Hello</Button>` в любом месте страницы и стиль, определенный с <xref:System.Windows.Style.TargetType%2A> из `Button` будет применен к этой кнопке. Если требуется, можно по-прежнему явно задать ключ стиля с тем же значением типа, как <xref:System.Windows.Style.TargetType%2A>для ясности в разметке, но это необязательно.  
  
 Неявные ключи для стилей не применяются для элемента управления, если <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> — `true` (также Обратите внимание, что <xref:System.Windows.FrameworkElement.OverridesDefaultStyle%2A> может быть задан как часть собственного поведения для класса элементов управления, а не явным образом в экземпляре элемента управления). Кроме того, чтобы поддерживать неявные ключи для производных скриптов класса, элемент управления должен переопределить <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> (все существующие элементы управления, поставляемые как часть [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] этого). Дополнительные сведения о стилях, темах и разработке элементов управления см. в разделе [рекомендации по разработке элементов](../../../../docs/framework/wpf/controls/guidelines-for-designing-stylable-controls.md).  
  
 <xref:System.Windows.DataTemplate> также имеет неявный ключ. Неявный ключ для <xref:System.Windows.DataTemplate> — <xref:System.Windows.DataTemplate.DataType%2A> значение свойства.                  <xref:System.Windows.DataTemplate.DataType%2A> также могут быть указаны как имя типа, а не явным образом с помощью [{x: Type...} ](../../../../docs/framework/xaml-services/x-type-markup-extension.md). Дополнительные сведения см. в разделе [сведения о шаблонах данных](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.ResourceDictionary>   
 [Ресурсы приложения](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Ресурсы и код](../../../../docs/framework/wpf/advanced/resources-and-code.md)   
 [Определение и ссылки на ресурс](../../../../docs/framework/wpf/advanced/how-to-define-and-reference-a-resource.md)   
 [Общие сведения об управлении приложением](../../../../docs/framework/wpf/app-development/application-management-overview.md)   
 [Расширение разметки x: Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md)   
 [Расширение разметки StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)   
 [Расширение разметки DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)