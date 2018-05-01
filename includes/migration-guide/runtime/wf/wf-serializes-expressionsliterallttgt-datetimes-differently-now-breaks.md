### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="96a1d-101">Теперь WF сериализует Expressions.Literal&lt;T&gt; DateTimes по-другому (нарушает работу пользовательских средств синтаксического анализа XAML)</span><span class="sxs-lookup"><span data-stu-id="96a1d-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

|   |   |
|---|---|
|<span data-ttu-id="96a1d-102">Подробные сведения</span><span class="sxs-lookup"><span data-stu-id="96a1d-102">Details</span></span>|<span data-ttu-id="96a1d-103">Связанный объект <xref:System.Windows.Markup.ValueSerializer> преобразует объект <xref:System.DateTime?displayProperty=name> или <xref:System.DateTimeOffset?displayProperty=name>, компоненты Second и <xref:System.DateTime.Millisecond?displayProperty=name> которого не равны нулю и (для значения <xref:System.DateTime?displayProperty=name>) свойство <xref:System.DateTime.Kind> которого не равно Unspecified, в синтаксис элемента свойства вместо строки.</span><span class="sxs-lookup"><span data-stu-id="96a1d-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=name> or <xref:System.DateTimeOffset?displayProperty=name> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=name> components are non-zero and (for a <xref:System.DateTime?displayProperty=name> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="96a1d-104">Это изменение позволяет передавать значения <xref:System.DateTime?displayProperty=name> и <xref:System.DateTimeOffset?displayProperty=name> в оба конца.</span><span class="sxs-lookup"><span data-stu-id="96a1d-104">This change allows <xref:System.DateTime?displayProperty=name> and <xref:System.DateTimeOffset?displayProperty=name> values to be round-tripped.</span></span> <span data-ttu-id="96a1d-105">Пользовательские средства синтаксического анализа XAML, в которых предполагается, что входные данные XAML имеют синтаксис атрибутов, не будут работать правильно.</span><span class="sxs-lookup"><span data-stu-id="96a1d-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>|
|<span data-ttu-id="96a1d-106">Предложение</span><span class="sxs-lookup"><span data-stu-id="96a1d-106">Suggestion</span></span>|<span data-ttu-id="96a1d-107">Это изменение позволяет передавать значения <xref:System.DateTime?displayProperty=name> и <xref:System.DateTimeOffset?displayProperty=name> в оба конца.</span><span class="sxs-lookup"><span data-stu-id="96a1d-107">This change allows <xref:System.DateTime?displayProperty=name> and <xref:System.DateTimeOffset?displayProperty=name> values to be round-tripped.</span></span> <span data-ttu-id="96a1d-108">Пользовательские средства синтаксического анализа XAML, в которых предполагается, что входные данные XAML имеют синтаксис атрибутов, не будут работать правильно.</span><span class="sxs-lookup"><span data-stu-id="96a1d-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>|
|<span data-ttu-id="96a1d-109">Область</span><span class="sxs-lookup"><span data-stu-id="96a1d-109">Scope</span></span>|<span data-ttu-id="96a1d-110">Пограничный случай</span><span class="sxs-lookup"><span data-stu-id="96a1d-110">Edge</span></span>|
|<span data-ttu-id="96a1d-111">Версия</span><span class="sxs-lookup"><span data-stu-id="96a1d-111">Version</span></span>|<span data-ttu-id="96a1d-112">4.5</span><span class="sxs-lookup"><span data-stu-id="96a1d-112">4.5</span></span>|
|<span data-ttu-id="96a1d-113">Тип</span><span class="sxs-lookup"><span data-stu-id="96a1d-113">Type</span></span>|<span data-ttu-id="96a1d-114">Среда выполнения</span><span class="sxs-lookup"><span data-stu-id="96a1d-114">Runtime</span></span>|
