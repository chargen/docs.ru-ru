---
title: Сопоставление неявных отношений между вложенными элементами схемы
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 1bce0c2815ac94787055794942807777232df295
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>Сопоставление неявных отношений между вложенными элементами схемы
Схема на языке XSD может иметь сложные типы, вложенные друг в друга. В этом случае процесс сопоставления применяет сопоставление по умолчанию и создает в объекте <xref:System.Data.DataSet>:  
  
-   одну таблицу для каждого сложного типа (родительского и дочернего);  
  
-   Если не существует ограничения уникальности в родительском, один дополнительный столбец первичного ключа в определение таблицы с именем *TableName*_Id где *TableName* имя родительской таблицы.  
  
-   Ограничение первичного ключа в родительской таблице, определяющее дополнительный столбец в качестве первичного ключа (установив **IsPrimaryKey** свойства **True**). Ограничению назначается имя Constraint*#* где *#* — 1, 2, 3 и т. д. Например, имя первого ограничения по умолчанию - Constraint1;  
  
-   ограничение внешнего ключа для дочерней таблицы, определяющее дополнительный столбец как внешний ключ, ссылающийся на первичный ключ родительской таблицы. Ограничению назначается имя *ParentTable_ChildTable* где *ParentTable* имя родительской таблицы и *ChildTable* имя дочерней таблицы.  
  
-   связи данных между родительскими и дочерними таблицами.  
  
 В следующем примере показано, схема которой **OrderDetail** является дочерним элементом элемента **порядок**.  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
   <xs:complexType>  
     <xs:choice maxOccurs="unbounded">  
       <xs:element name="Order">  
         <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 Процесс сопоставления схем XML создает в **набора данных**:  
  
-   **Порядок** и **OrderDetail** таблицы.  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   Ограничение уникальности на **порядок** таблицы. Обратите внимание, что **IsPrimaryKey** свойству **True**.  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   Ограничение внешнего ключа для **OrderDetail** таблицы.  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   Связь между **порядок** и **OrderDetail** таблиц. **Nested** для этого отношения свойству **True** из-за **порядок** и **OrderDetail** элементы являются вложенными в схеме .  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>См. также  
 [Создание отношений DataSet из схемы XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [Сопоставление ограничений схемы XML (XSD) с ограничениями DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [Центр разработчиков наборов данных и управляемых поставщиков ADO.NET](http://go.microsoft.com/fwlink/?LinkId=217917)
