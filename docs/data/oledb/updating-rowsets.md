---
title: Actualizar conjuntos de filas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- rowsets, updating data
- updating data, rowsets
- updating rowsets
- rowsets
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: be82fb1c1f77ae3204bed54257062f362d286844
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083832"
---
# <a name="updating-rowsets"></a>actualizar conjuntos de filas

Una operación de base de datos muy básica es actualizar el almacén de datos, o escribir datos en este. En OLE DB, el mecanismo de actualización es sencillo: la aplicación de consumidor establece los valores de los miembros de datos enlazados y, después, escribe esos valores en el conjunto de filas; luego, el consumidor solicita que el proveedor actualice el almacén de datos.  
  
Los consumidores pueden realizar los siguientes tipos de actualizaciones en los datos del conjunto de filas: establecer los valores de columna dentro de una fila, insertar una fila y eliminar una fila. Para realizar estas operaciones, la clase de plantilla OLE DB [CRowset](../../data/oledb/crowset-class.md) implementa la interfaz [IRowsetChange](/previous-versions/windows/desktop/ms715790) e invalida los métodos de interfaz siguientes:  
  
- [SetData](../../data/oledb/crowset-setdata.md) cambia los valores de columna de una fila de un conjunto de filas; es equivalente al comando UPDATE de SQL.  
  
- [Insertar](../../data/oledb/crowset-insert.md) inserta una fila en un conjunto de filas; es equivalente al comando INSERT de SQL.  
  
- [Delete](../../data/oledb/crowset-delete.md) elimina una fila de un conjunto de filas; es equivalente al comando DELETE de SQL.  
  
## <a name="supporting-update-operations"></a>Admitir operaciones de actualización  

Al crear un consumidor con el Asistente para consumidores OLE DB ATL, puede activar una o más de las tres casillas **Cambiar**, **Insertar**y **Eliminar**para que se admitan las operaciones de actualización. Si las activa, el asistente modifica el código correctamente para admitir el tipo de cambios elegido. Sin embargo, si no usa el asistente, debe establecer las siguientes propiedades del conjunto de filas en `VARIANT_TRUE` para admitir las actualizaciones:  
  
- `DBPROPVAL_UP_CHANGE` permite cambiar los valores de datos en una fila.  
  
- `DBPROPVAL_UP_INSERT` permite insertar una fila.  
  
- `DBPROPVAL_UP_DELETE` permite eliminar una fila.  
  
Establezca las propiedades de la siguiente manera:  
  
```cpp  
CDBPropSet ps(DBPROPSET_ROWSET);  

ps.AddProperty(DBPROP_IRowsetChange, true)  
ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
```  
  
Las operaciones de cambio, inserción o eliminación pueden fallar si no se puede escribir en una o más columnas. Modifique la asignación del cursor para corregirlo.  
  
## <a name="setting-data-in-rows"></a>Establecer datos en filas  

[CRowset::SetData](../../data/oledb/crowset-setdata.md) establece los valores de datos en una o más columnas de la fila actual. El código siguiente establece los valores de los miembros de datos enlazados a las columnas "Name" y "Units in Stock" de la tabla Products y, después, llama a `SetData` para escribir dichos valores en la fila número 100 del conjunto de filas:  
  
```cpp  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the current row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

product.m_UnitsInStock = 10000;  
  
// Set the data  
HRESULT hr = product.SetData();  
```  
  
## <a name="inserting-rows-into-rowsets"></a>Insertar filas en conjuntos de filas  

[CRowset::Insert](../../data/oledb/crowset-insert.md) crea e inicializa una nueva fila con datos del descriptor de acceso. `Insert` crea una fila totalmente nueva después de la fila actual; debe especificar si se debe incrementar la fila actual a la siguiente fila o dejarla sin modificar. Para ello, establezca el parámetro *bGetRow* :  
  
```cpp  
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)  
```  
  
- **false** (valor predeterminado) especifica que la fila actual se incremente a la siguiente fila (en cuyo caso apunta a la fila insertada).  
  
- **true** especifica que la fila actual debe permanecer donde está.  
  
El código siguiente establece los valores de los miembros de datos enlazados a las columnas de la tabla Products y, a continuación, llama a `Insert` para insertar una nueva fila con dichos valores después de la fila número 100 del conjunto de filas. Se recomienda establecer todos los valores de columna para evitar datos no definidos en la nueva fila:  
  
```cpp  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Set the column values for a row of the Product table, then insert the row  
product.m_ProductID = 101;  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Candle" ) );  

product.m_SupplierID = 27857;  
product.m_CategoryID = 372;  
_tcscpy_s(product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit,  
           _T( "Pack of 10" ) );  

product.m_UnitPrice = 20;  
product.m_UnitsInStock = 10000;  
product.m_UnitsOnOrder = 5201;  
product.m_ReorderLevel = 5000;  
product.m_Discontinued = false;  
  
// You must also initialize the status and length fields before setting/inserting data  
// Set the column status values  
m_dwProductIDStatus = DBSTATUS_S_OK;  
m_dwProductNameStatus = DBSTATUS_S_OK;  
m_dwSupplierIDStatus = DBSTATUS_S_OK;  
m_dwCategoryIDStatus = DBSTATUS_S_OK;  
m_dwQuantityPerUnitStatus = DBSTATUS_S_OK;  
m_dwUnitPriceStatus = DBSTATUS_S_OK;  
m_dwUnitsInStockStatus = DBSTATUS_S_OK;  
m_dwUnitsOnOrderStatus = DBSTATUS_S_OK;  
m_dwReorderLevelStatus = DBSTATUS_S_OK;  
m_dwDiscontinuedStatus = DBSTATUS_S_OK;  
  
// Set the column length value for column data members that are not fixed-length types.  
// The value should be the length of the string that you are setting.  
m_dwProductNameLength = 6;             // "Candle" has 6 characters  
m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters  
  
// Insert the data  
HRESULT hr = product.Insert();  
```  
  
Para obtener un ejemplo más detallado, vea [CRowset::Insert](../../data/oledb/crowset-insert.md).  
  
Para obtener información sobre cómo establecer los miembros de datos de estado y longitud, consulte [Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
## <a name="deleting-rows-from-rowsets"></a>Eliminar filas de conjuntos de filas  

[CRowset::Delete](../../data/oledb/crowset-delete.md) elimina la fila actual del conjunto de filas. El código siguiente llama `Delete` para quitar la fila número 100 del conjunto de filas:  
  
```cpp  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Delete the row  
HRESULT hr = product.Delete();  
```  
  
## <a name="immediate-and-deferred-updates"></a>Actualizaciones inmediatas y diferidas  

A menos que se especifique lo contrario, las llamadas a la `SetData`, `Insert`, y `Delete` métodos actualizan el almacén de datos inmediatamente. Sin embargo, puede diferir las actualizaciones para que el consumidor almacene todos los cambios en una memoria caché local y, luego, los transfiera al almacén de datos cuando se llame a uno de los siguientes métodos de actualización:  
  
- [CRowset:: Update](../../data/oledb/crowset-update.md) los cambios realizados en la fila actual desde la última recuperación de cambios pendientes transfiere o `Update` llamar en ella.  
  
- [CRowset:: UpdateAll](../../data/oledb/crowset-updateall.md) los cambios realizados en todas las filas desde la última recuperación de cambios pendientes transfiere o `Update` llamar en ella.  
  
Tenga en cuenta que la actualización, tal y como la usan los métodos de actualización, tiene el significado específico de realizar cambios en el comando y no debe confundirse con el comando UPDATE de SQL (`SetData` es equivalente al comando UPDATE de SQL).  
  
Las actualizaciones diferidas son útiles, por ejemplo, en situaciones como una serie de transacciones bancarias; si se cancela una transacción, puede deshacer el cambio, ya que la serie de cambios no se envía hasta que se confirma el último. Además, el proveedor puede agrupar los cambios en una llamada de red, que es más eficaz.  
  
Para admitir actualizaciones diferidas, se debe establecer el `DBPROP_IRowsetChange` propiedad además de las propiedades descritas en "Admitir operaciones de actualización":  
  
```cpp  
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);  
```  
  
Cuando se llama a `Update` o `UpdateAll`, los métodos transfieren los cambios de la memoria caché local al almacén de datos y, después, borran la memoria caché local. Dado que la actualización transfiere los cambios solo de la fila actual, es importante que la aplicación realice un seguimiento de qué fila debe actualizar y cuándo actualizarla. En el ejemplo siguiente se muestra cómo actualizar dos filas consecutivas:  
  
```cpp  
// Instantiate a rowset based on the user record class  
CTable<CAccessor<CProductAccessor>> product;  
CSession session;  
  
// Open the rowset and move to the 100th row  
product.Open(session, "Product", &ps, 1);  // ps is the property set  
product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row  
  
// Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table  
_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName,  
           _T( "Wick" ) );  

product.m_UnitsInStock = 10000;  

HRESULT hr = product.SetData();  // No changes made to row 100 yet  
product.Update();                 // Update row 100 now  
  
// Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table  
product.MoveNext();  

_tcscpy_s(product.m_ProductName, product.m_sizeOfProductName  
           _T( "Wax" ) );  

product.m_UnitsInStock = 500;  

HRESULT hr = product.SetData();  // No changes made to row 101 yet  
product.Update();                 // Update row 101 now  
```  
  
Para asegurarse de que se transfieren los cambios pendientes, debe llamar a `Update` antes de pasar a otra fila. Sin embargo, si esta acción resulta tediosa o poco eficaz, por ejemplo, cuando la aplicación necesite actualizar cientos de filas, puede usar `UpdateAll` para actualizar todas las filas a la vez.  
  
Por ejemplo, si la primera `Update` llamada estaba presente en el código anterior, la fila 100 se mantendría sin cambios, pero se cambiaría la fila 101. Después de ese punto, la aplicación tendría que llamar a `UpdateAll` o regresar a la fila 100 y llamar a `Update` para actualizar esa fila.  
  
Por último, una de las principales razones para diferir los cambios es que se pueden deshacer. La llamada a [CRowset::Undo](../../data/oledb/crowset-undo.md) revierte el estado de la memoria caché de cambios local al estado del almacén de datos antes de aplicar los cambios pendientes. Es importante tener en cuenta que `Undo` no revierte hacer una copia del estado de la memoria caché local en un paso (el estado anterior al cambio más reciente); en su lugar, borra la memoria caché local para esa fila. Además, `Undo` afecta únicamente la fila actual.  
  
## <a name="see-also"></a>Vea también  

[Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)<br/>
[CRowset (Clase)](../../data/oledb/crowset-class.md)<br/>
[IRowsetChange](/previous-versions/windows/desktop/ms715790)