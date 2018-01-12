---
title: Clases generadas por el Asistente para consumidores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- command classes in OLE DB consumer
- classes [C++], OLE DB Consumer Wizard-generated
- consumer wizard-generated classes and methods
- user record classes in OLE DB consumer
ms.assetid: dba0538f-2afe-4354-8cbb-f202ea8ade5a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8ebd53b8b39fb94e4275f5052a74f77bf71bd790
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="consumer-wizard-generated-classes"></a>Clases generadas por el Asistente para consumidores
Cuando utiliza el Asistente para consumidores OLE DB ATL para generar un consumidor, tiene la opción de utilizar plantillas OLE DB o atributos OLE DB. En ambos casos, el asistente genera una clase de comando y una clase de registro de usuario. La clase de comando contiene código para abrir el origen de datos y el conjunto de filas especificado en el asistente. La clase de registro de usuario contiene un mapa de columnas para la tabla de base de datos seleccionada. Sin embargo, el código generado es distinto en cada caso:  
  
-   Si selecciona un consumidor con plantilla, el asistente genera una clase de comando y una clase de registro de usuario. La clase de comando tendrá el nombre que escriba en el cuadro Clase del asistente (por ejemplo, `CProducts`) y la clase de registro de usuario tendrá un nombre con el formato "*ClassName*Accessor" (por ejemplo, `CProductsAccessor`). Ambas clases se colocan en el archivo de encabezado del consumidor.  
  
-   Si selecciona un consumidor con atributos, la clase de registro de usuario tendrá un nombre con el formato "_*ClassName*Accessor" y se insertará. Por tanto, solo podrá ver la clase de comando en el editor de texto; la clase de registro de usuario solo se puede ver como código insertado. Para obtener información acerca de cómo ver código insertado, vea [Depurar código insertado](/visualstudio/debugger/how-to-debug-injected-code).  
  
 Los ejemplos siguientes usan una clase de comando creada en la tabla Products de la base de datos Northwind para mostrar el código de consumidor generado por el asistente para la clase de comando y la clase de registro de usuario.  
  
## <a name="templated-user-record-classes"></a>Clases de registro de usuario con plantilla  
 Si crea un consumidor OLE DB mediante las plantillas OLE DB (en lugar de los atributos OLE DB), el asistente genera código como se describe en esta sección.  
  
### <a name="column-data-members"></a>Miembros de datos de columna  
 La primera parte de la clase de registro de usuario incluye las declaraciones de los miembros de datos y los miembros de datos de estado y longitud de cada columna enlazada a datos. Para obtener información acerca de estos miembros de datos, consulte [Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
> [!NOTE]
>  Si modifica la clase de registro de usuario o escribe su propio consumidor, las variables de datos deben preceder a las variables de estado y longitud.  
  
> [!NOTE]
>  El Asistente para consumidores OLE DB ATL usa el tipo **DB_NUMERIC** para enlazar tipos de datos numéricos. Anteriormente, usaba **DBTYPE_VARNUMERIC** (cuyo formato se describe en el tipo **DB_VARNUMERIC** ; vea Oledb.h). Si no usa el asistente para crear consumidores, se recomienda que use **DB_NUMERIC**.  
  
```  
// Products.H : Declaration of the CProducts class  
  
class CProductsAccessor  
{  
public:  
   // Column data members:  
   LONG m_ProductID;  
   TCHAR m_ProductName[41];  
   LONG m_SupplierID;  
   LONG m_CategoryID;  
   TCHAR m_QuantityPerUnit[21];  
   CURRENCY m_UnitPrice;  
   SHORT m_UnitsInStock;  
   SHORT m_UnitsOnOrder;  
   SHORT m_ReorderLevel;  
   VARIANT_BOOL m_Discontinued;  
  
   // Column status data members:  
   DBSTATUS m_dwProductIDStatus;  
   DBSTATUS m_dwProductNameStatus;  
   DBSTATUS m_dwSupplierIDStatus;  
   DBSTATUS m_dwCategoryIDStatus;  
   DBSTATUS m_dwQuantityPerUnitStatus;  
   DBSTATUS m_dwUnitPriceStatus;  
   DBSTATUS m_dwUnitsInStockStatus;  
   DBSTATUS m_dwUnitsOnOrderStatus;  
   DBSTATUS m_dwReorderLevelStatus;  
   DBSTATUS m_dwDiscontinuedStatus;  
  
   // Column length data members:  
   DBLENGTH m_dwProductIDLength;  
   DBLENGTH m_dwProductNameLength;  
   DBLENGTH m_dwSupplierIDLength;  
   DBLENGTH m_dwCategoryIDLength;  
   DBLENGTH m_dwQuantityPerUnitLength;  
   DBLENGTH m_dwUnitPriceLength;  
   DBLENGTH m_dwUnitsInStockLength;  
   DBLENGTH m_dwUnitsOnOrderLength;  
   DBLENGTH m_dwReorderLevelLength;  
   DBLENGTH m_dwDiscontinuedLength;  
```  
  
### <a name="rowset-properties"></a>Propiedades del conjunto de filas  
 A continuación, el asistente establece las propiedades del conjunto de filas. Si seleccionó **Cambiar**, **Insertar**o **Eliminar** en el Asistente para consumidores OLE DB ATL, las propiedades adecuadas se establecen aquí (siempre se establece DBPROP_IRowsetChange y, después, una o varias de las propiedades DBPROPVAL_UP_CHANGE, DBPROPVAL_UP_INSERT y DBPROPVAL_UP_DELETE, respectivamente).  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
### <a name="command-or-table-class"></a>Clase de comando o de tabla  
 Si se especifica una clase de comando, el asistente declara la clase de comando; para código con plantilla, el comando tiene el siguiente aspecto:  
  
```  
DEFINE_COMMAND_EX(CProductsAccessor, L" \  
SELECT \  
   ProductID, \  
   ProductName, \  
   SupplierID, \  
   CategoryID, \  
   QuantityPerUnit, \  
   UnitPrice, \  
   UnitsInStock, \  
   UnitsOnOrder, \  
   ReorderLevel, \  
   Discontinued \  
   FROM dbo.Products")  
```  
  
### <a name="column-map"></a>Mapa de columnas  
 El asistente genera los enlaces de columna o el mapa de columnas. Para solucionar varios problemas con algunos proveedores, el código siguiente podría enlazar columnas en un orden diferente del que indica el proveedor.  
  
```  
   BEGIN_COLUMN_MAP(CProductsAccessor)  
      COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(3, m_SupplierID, m_dwSupplierIDLength, m_dwSupplierIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(4, m_CategoryID, m_dwCategoryIDLength, m_dwCategoryIDStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(5, m_QuantityPerUnit, m_dwQuantityPerUnitLength, m_dwQuantityPerUnitStatus)  
      _COLUMN_ENTRY_CODE(6, DBTYPE_CY, _SIZE_TYPE(m_UnitPrice), 0, 0, offsetbuf(m_UnitPrice), offsetbuf(m_dwUnitPriceLength), offsetbuf(m_dwUnitPriceStatus))  
      COLUMN_ENTRY_LENGTH_STATUS(7, m_UnitsInStock, m_dwUnitsInStockLength, m_dwUnitsInStockStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(8, m_UnitsOnOrder, m_dwUnitsOnOrderLength, m_dwUnitsOnOrderStatus)  
      COLUMN_ENTRY_LENGTH_STATUS(9, m_ReorderLevel, m_dwReorderLevelLength, m_dwReorderLevelStatus)  
      _COLUMN_ENTRY_CODE(10, DBTYPE_BOOL, _SIZE_TYPE(m_Discontinued), 0, 0, offsetbuf(m_Discontinued), offsetbuf(m_dwDiscontinuedLength), offsetbuf(m_dwDiscontinuedStatus))  
   END_COLUMN_MAP()  
};  
```  
  
### <a name="class-declaration"></a>Declaración de clase  
 Por último, el asistente genera una declaración de clase de comando como la siguiente:  
  
```  
class CProducts : public CCommand<CAccessor<CProductsAccessor> >  
```  
  
## <a name="attribute-injected-user-record-classes"></a>Clases de registro de usuario con atributos  
 Si crea un consumidor OLE DB mediante los atributos de base de datos ([db_command](../../windows/db-command.md) o [db_table](../../windows/db-table.md)), los atributos insertan una clase de registro de usuario cuyo nombre tiene el formato "_*ClassName*Accessor". Por ejemplo, si la clase de comando se llama `COrders`, la clase de registro de usuario será `_COrdersAccessor`. Aunque la clase de registro de usuario aparezca en la vista de clases, al hacer doble clic en esta se desplaza a la clase de comando o de tabla en el archivo de encabezado en su lugar. En estos casos, solo se puede ver la declaración real de la clase de registro de usuario mediante la visualización del código con atributos.  
  
 Podría haber complicaciones si se agregan o anulan métodos en consumidores con atributos. Por ejemplo, podría agregar un constructor `_COrdersAccessor` a la declaración `COrders` , pero tenga en cuenta que en realidad se agrega un constructor a la clase `COrdersAccessor` insertada. Dicho constructor puede inicializar las columnas o los parámetros, pero no se puede crear a un constructor de copias de este modo, ya que no se puede crear instancias directamente del objeto `COrdersAccessor` . Si necesita un constructor (u otro método) directamente en la clase `COrders` , se recomienda definir una clase nueva derivada de `COrders` y agregarle los métodos necesarios.  
  
 En el ejemplo siguiente, el asistente genera una declaración para la clase `COrders`, pero la clase de registro de usuario `COrdersAccessor` no aparece porque los atributos la insertan.  
  
```  
#define _ATL_ATTRIBUTES  
#include <atlbase.h>  
#include <atldbcli.h>  
[  
   db_source(L"your connection string"),  
   db_command(L"Select ShipName from Orders;")  
]  
class COrders  
{  
public:  
  
   // COrders()            // incorrect constructor name  
   _COrdersAccessor()      // correct constructor name  
   {  
   }  
      [db_column(1) ] TCHAR m_ShipName[41];  
   };  
```  
  
 La declaración de clase de comando insertada presenta el siguiente aspecto:  
  
```  
class CProducts : public CCommand<CAccessor<_CProductsAccessor> >  
```  
  
 La mayoría del código insertado es igual o similar a la versión de la plantilla. Las diferencias principales están en los métodos insertados, que se describen en [Métodos generados por el Asistente para consumidores](../../data/oledb/consumer-wizard-generated-methods.md).  
  
 Para obtener información acerca de cómo ver código insertado, vea [Depurar código insertado](/visualstudio/debugger/how-to-debug-injected-code).  
  
## <a name="see-also"></a>Vea también  
 [Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)