---
title: Извлечение данных с помощью объекта DataReader
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 0c78db5ce7a6a988e40718daca1d828096a734d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="retrieving-data-using-a-datareader"></a>Извлечение данных с помощью объекта DataReader
Получение данных с помощью **DataReader** включает в себя создание экземпляра **команда** объекта, а затем создать **DataReader** путем вызова  **Command.ExecuteReader** для получения строк из источника данных. В следующем примере демонстрируется использование **DataReader** где `reader` представляет допустимый DataReader и `command` представляет допустимый объект Command.  
  
```  
reader = command.ExecuteReader();  
```  
  
 Вы используете **чтения** метод **DataReader** объект для получения строки из результатов запроса. Доступ к каждого столбца возвращенной строки, передав имя или порядковый номер столбца, **DataReader**. Однако для достижения наилучшей производительности **DataReader** предоставляет ряд методов, которые позволяют получить доступ к значениям столбцов в их собственных типах данных (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**и так далее). Список типизированных методов доступа для конкретных поставщиков данных **объекты DataReader**, в разделе <xref:System.Data.OleDb.OleDbDataReader> и <xref:System.Data.SqlClient.SqlDataReader>. Использование типизированных методов доступа при условии, что известен базовый тип данных, сокращает объем преобразований типов, необходимых при извлечении значения столбца.  
  
> [!NOTE]
>  Выпуск Windows Server 2003 платформы .NET Framework имеется дополнительное свойство для **DataReader**, **HasRows**, что позволяет определить, если **DataReader**вернул никаких результатов перед чтением из него.  
  
 В следующем примере кода выполняется итерация через **DataReader** объекта и возвращает два столбца из каждой строки.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 **DataReader** предоставляет небуферизованный поток данных, позволяющий процедурам последовательно обрабатывать результаты из источника данных. **DataReader** — хороший выбор при извлечении больших объемов данных, поскольку данные не кэшируются в памяти.  
  
## <a name="closing-the-datareader"></a>Закрытие DataReader  
 Следует всегда вызывать **закрыть** метод завершения с помощью **DataReader** объекта.  
  
 Если ваш **команда** содержит выходные данные параметры или возвращаемые значения, они не будут доступны до **DataReader** закрыт.  
  
 Обратите внимание, что, хотя **DataReader** открыт, **подключения** используется исключительно этим объектом **DataReader**. Невозможно выполнить команды для **подключения**, включая создание другого **DataReader**, пока исходный **DataReader** закрыт.  
  
> [!NOTE]
>  Не вызывайте **закрыть** или **Dispose** на **подключения**, **DataReader**, или любого другого управляемого объекта в **Finalize**  метод класса. В методе завершения следует только освобождать неуправляемые ресурсы, которыми ваш класс непосредственно владеет. Если класс не владеет все неуправляемые ресурсы, не включайте **Finalize** метод в определении класса. Дополнительные сведения см. в разделе [мусора](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Извлечение нескольких результирующих наборов при помощи NextResult  
 Если возвращается несколько результирующих наборов, **DataReader** предоставляет **NextResult** задает метод для перебора результат в последовательности. В следующем примере показан объект <xref:System.Data.SqlClient.SqlDataReader>, обрабатывающий результаты двух инструкций SELECT с помощью метода <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>Получение данных схемы от DataReader  
 Хотя **DataReader** является открытым, можно получить данные схемы о текущем результирующем наборе с помощью **GetSchemaTable** метод. **GetSchemaTable** возвращает <xref:System.Data.DataTable> заполненный строк и столбцов, содержащих сведения о схеме для текущего результирующего набора. **DataTable** содержит по одной строке для каждого столбца результирующего набора. Каждый столбец строки таблицы схемы соответствует свойству столбца, возвращенного в результирующем наборе, где **ColumnName** имя свойства и значение столбца является значением свойства. Следующий пример кода записывает сведения о схеме для **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>Работа с разделами OLE DB  
 Иерархические наборы строк или разделы (тип OLE DB **DBTYPE_HCHAPTER**, тип ADO **adChapter**) можно получить с помощью <xref:System.Data.OleDb.OleDbDataReader>. Если запрос, включающий раздел возвращается в виде **DataReader**, раздел возвращается в виде столбца в том, что **DataReader** и доступен как **DataReader** объекта.  
  
 ADO.NET **набора данных** может также использоваться для представления иерархических наборов строк с помощью родительско дочерних отношений между таблицами. Дополнительные сведения см. в разделе [наборы данных, таблицы данных и объекты DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 В следующем примере кода поставщик MSDataShape используется, чтобы сформировать столбец раздела заказов по каждому клиенту из списка клиентов.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Возвращение результатов при помощи Oracle REF CURSOR  
 Поставщик данных .NET Framework для Oracle поддерживает использование параметров Oracle REF CURSOR для возвращения результата запроса. Параметр Oracle REF CURSOR возвращается в виде объекта <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Вы можете получить **OracleDataReader** объекта, который представляет Oracle REF CURSOR с использованием <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> метод и можно также указать <xref:System.Data.OracleClient.OracleCommand> , возвращающий один или несколько REF CURSOR Oracle в виде  **SelectCommand** для <xref:System.Data.OracleClient.OracleDataAdapter> используется для заполнения <xref:System.Data.DataSet>.  
  
 Чтобы получить доступ к параметру REF CURSOR, возвращенному из источника данных Oracle, создайте **OracleCommand** запроса и добавьте выходной параметр, ссылающийся REF CURSOR **параметры** коллекцию вашей  **OracleCommand**. Имя параметра должно соответствовать имени параметра REF CURSOR, используемого в запросе. Задать тип параметра для **OracleType.Cursor**. **ExecuteReader** метод вашей **OracleCommand** вернет **OracleDataReader** для параметра REF CURSOR.  
  
 Если ваш **OracleCommand** возвращает несколько параметров REF CURSOR, добавьте несколько выходных параметров. Доступ к другой типа REF CURSOR путем вызова **OracleCommand.ExecuteReader** метод. Вызов **ExecuteReader** возвращает **OracleDataReader** ссылается первый параметр REF CURSOR. Затем можно вызвать **OracleDataReader.NextResult** метод для доступа к последующих параметров REF CURSOR. Хотя параметры в вашей **OracleCommand.Parameters** REF CURSOR соответствуют выходным параметрам по имени, **OracleDataReader** получает к ним доступ в порядке, в котором они были добавлены  **Параметры** коллекции.  
  
 Например, рассмотрим следующий пакет и текст пакета Oracle.  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
  TYPE T_CURSOR IS REF CURSOR;   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR);   
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS   
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
    DEPTCURSOR OUT T_CURSOR)   
  IS   
  BEGIN   
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;   
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;   
  END OPEN_TWO_CURSORS;   
END CURSPKG;   
```  
  
 В следующем коде создается **OracleCommand** , возвращает параметры REF CURSOR из предыдущего пакета Oracle путем добавления двух параметров типа **OracleType.Cursor** для **параметры** коллекции.  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 В следующем коде возвращаются результаты предыдущей команды при помощи **чтения** и **NextResult** методы **OracleDataReader**. Параметры REF CURSOR возвращаются по порядку.  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 В следующем примере предыдущая команда используется для заполнения **набора данных** с результатами пакета Oracle.  
  
> [!NOTE]
>  Чтобы избежать **OverflowException**, рекомендуется также производить преобразования из типа Oracle NUMBER в допустимый тип .NET Framework перед сохранением значения в **DataRow**. Можно использовать **FillError** событий для определения **OverflowException** произошла. Дополнительные сведения о **FillError** событий, в разделе [обработка событий DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```  
  
## <a name="see-also"></a>См. также  
 [Работа с объекты DataReader](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Объекты DataAdapter и DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Команды и параметры](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Извлечение сведений о схеме базы данных](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](http://go.microsoft.com/fwlink/?LinkId=217917)
