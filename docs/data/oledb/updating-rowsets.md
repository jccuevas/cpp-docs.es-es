---
title: "Actualizar conjuntos de filas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conjuntos de filas, actualizar datos"
  - "actualizar datos, conjuntos de filas"
  - "actualizar conjuntos de filas"
  - "conjuntos de filas"
ms.assetid: 39588758-5c72-4254-a10d-cc2b1f473357
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Actualizar conjuntos de filas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una operación de base de datos muy básica es actualizar el almacén de datos, o escribir datos en este. En OLE DB, el mecanismo de actualización es sencillo: la aplicación de consumidor establece los valores de los miembros de datos enlazados y, después, escribe esos valores en el conjunto de filas; luego, el consumidor solicita que el proveedor actualice el almacén de datos.  
  
 Los consumidores pueden realizar los siguientes tipos de actualizaciones en los datos del conjunto de filas: establecer los valores de columna dentro de una fila, insertar una fila y eliminar una fila. Para realizar estas operaciones, la clase de plantilla OLE DB [CRowset](../../data/oledb/crowset-class.md) implementa la interfaz [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) e invalida los métodos de interfaz siguientes:  
  
-   [SetData](../../data/oledb/crowset-setdata.md) cambia los valores de columna de una fila de un conjunto de filas; es equivalente al comando UPDATE de SQL.  
  
-   [Insertar](../../data/oledb/crowset-insert.md) inserta una fila en un conjunto de filas; es equivalente al comando INSERT de SQL.  
  
-   [Delete](../../data/oledb/crowset-delete.md) elimina una fila de un conjunto de filas; es equivalente al comando DELETE de SQL.  
  
## Admitir operaciones de actualización  
 Al crear un consumidor con el Asistente para consumidores OLE DB ATL, puede activar una o más de las tres casillas **Cambiar**, **Insertar** y **Eliminar** para que se admitan las operaciones de actualización. Si las activa, el asistente modifica el código correctamente para admitir el tipo de cambios elegido. Sin embargo, si no usa el asistente, debe establecer las siguientes propiedades del conjunto de filas en `VARIANT_TRUE` para admitir las actualizaciones:  
  
-   **DBPROPVAL\_UP\_CHANGE** le permite cambiar los valores de datos en una fila.  
  
-   **DBPROPVAL\_UP\_INSERT** permite insertar una fila.  
  
-   **DBPROPVAL\_UP\_DELETE** permite eliminar una fila.  
  
 Establezca las propiedades de la siguiente manera:  
  
```  
CDBPropSet ps(DBPROPSET_ROWSET); ps.AddProperty(DBPROP_IRowsetChange, true) ps.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
```  
  
 Las operaciones de cambio, inserción o eliminación pueden fallar si no se puede escribir en una o más columnas. Modifique la asignación del cursor para corregirlo.  
  
## Establecer datos en filas  
 [CRowset::SetData](../../data/oledb/crowset-setdata.md) establece los valores de datos en una o más columnas de la fila actual. El código siguiente establece los valores de los miembros de datos enlazados a las columnas "Name" y "Units in Stock" de la tabla Products y, después, llama a `SetData` para escribir dichos valores en la fila número 100 del conjunto de filas:  
  
```  
// Instantiate a rowset based on the user record class CTable<CAccessor<CProductAccessor> > product; CSession session; // Open the rowset and move to the 100th row product.Open(session, "Product", &ps, 1);  // ps is the property set product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row // Change the values of columns "Name" and "Units in Stock" in the current row of the Product table _tcscpy_s( product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) ); product.m_UnitsInStock = 10000; // Set the data HRESULT hr = product.SetData( );  
```  
  
## Insertar filas en conjuntos de filas  
 [CRowset::Insert](../../data/oledb/crowset-insert.md) crea e inicializa una nueva fila con datos del descriptor de acceso.**Insert** crea una fila totalmente nueva después de la fila actual; debe especificar si se debe incrementar la fila actual a la siguiente fila o dejarla sin modificar. Para ello, establezca el parámetro *bGetRow*:  
  
```  
HRESULT Insert(int nAccessor = 0, bool bGetRow = false)  
```  
  
-   **false** \(valor predeterminado\) especifica que la fila actual se incremente a la siguiente fila \(en cuyo caso apunta a la fila insertada\).  
  
-   **true** especifica que la fila actual debe permanecer donde está.  
  
 El código siguiente establece los valores de los miembros de datos enlazados a las columnas de la tabla Products y, después, llama a **Insert** para insertar una nueva fila con dichos valores en la fila número 100 del conjunto de filas: Se recomienda establecer todos los valores de columna para evitar datos no definidos en la nueva fila:  
  
```  
// Instantiate a rowset based on the user record class CTable<CAccessor<CProductAccessor> > product; CSession session; // Open the rowset and move to the 100th row product.Open(session, "Product", &ps, 1);  // ps is the property set product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row // Set the column values for a row of the Product table, then insert the row product.m_ProductID = 101; _tcscpy_s( product.m_ProductName, product.m_sizeOfProductName, _T( "Candle" ) ); product.m_SupplierID = 27857; product.m_CategoryID = 372; _tcscpy_s( product.m_QuantityPerUnit, product.m_sizeOfQuantityPerUnit, _T( "Pack of 10" ) ); product.m_UnitPrice = 20; product.m_UnitsInStock = 10000; product.m_UnitsOnOrder = 5201; product.m_ReorderLevel = 5000; product.m_Discontinued = false; // You must also initialize the status and length fields before setting/inserting data // Set the column status values m_dwProductIDStatus = DBSTATUS_S_OK; m_dwProductNameStatus = DBSTATUS_S_OK; m_dwSupplierIDStatus = DBSTATUS_S_OK; m_dwCategoryIDStatus = DBSTATUS_S_OK; m_dwQuantityPerUnitStatus = DBSTATUS_S_OK; m_dwUnitPriceStatus = DBSTATUS_S_OK; m_dwUnitsInStockStatus = DBSTATUS_S_OK; m_dwUnitsOnOrderStatus = DBSTATUS_S_OK; m_dwReorderLevelStatus = DBSTATUS_S_OK; m_dwDiscontinuedStatus = DBSTATUS_S_OK; // Set the column length value for column data members that are not fixed-length types. // The value should be the length of the string that you are setting. m_dwProductNameLength = 6;             // "Candle" has 6 characters m_dwQuantityPerUnitLength = 10;        // "Pack of 10" has 10 characters // Insert the data HRESULT hr = product.Insert( );  
```  
  
 Para obtener un ejemplo más detallado, vea [CRowset::Insert](../../data/oledb/crowset-insert.md).  
  
 Para obtener información sobre cómo establecer los miembros de datos de estado y longitud, consulte [Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
## Eliminar filas de conjuntos de filas  
 [CRowset::Delete](../../data/oledb/crowset-delete.md) elimina la fila actual del conjunto de filas. El código siguiente llama a **Eliminar** para quitar la fila número 100 del conjunto de filas:  
  
```  
// Instantiate a rowset based on the user record class CTable<CAccessor<CProductAccessor> > product; CSession session; // Open the rowset and move to the 100th row product.Open(session, "Product", &ps, 1);  // ps is the property set product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row // Delete the row HRESULT hr = product.Delete( );  
```  
  
## Actualizaciones inmediatas y diferidas  
 A menos que se especifique lo contrario, las llamadas a los métodos `SetData`, **Insert** y **Delete** actualizan el almacén de datos inmediatamente. Sin embargo, puede diferir las actualizaciones para que el consumidor almacene todos los cambios en una memoria caché local y, luego, los transfiera al almacén de datos cuando se llame a uno de los siguientes métodos de actualización:  
  
-   [CRowset::Update](../../data/oledb/crowset-update.md) transfiere los cambios pendientes realizados en la fila actual desde la última recuperación de cambios o llamada a **Update** en esta.  
  
-   [CRowset::UpdateAll](../../data/oledb/crowset-updateall.md) transfiere todos los cambios pendientes realizados en todas las filas desde la última recuperación de cambios o llamada a **Update** en estas.  
  
 Tenga en cuenta que la actualización, tal y como la usan los métodos de actualización, tiene el significado específico de realizar cambios en el comando y no debe confundirse con el comando UPDATE de SQL \(`SetData` es equivalente al comando UPDATE de SQL\).  
  
 Las actualizaciones diferidas son útiles, por ejemplo, en situaciones como una serie de transacciones bancarias; si se cancela una transacción, puede deshacer el cambio, ya que la serie de cambios no se envía hasta que se confirma el último. Además, el proveedor puede agrupar los cambios en una llamada de red, que es más eficaz.  
  
 Para admitir actualizaciones diferidas, se debe establecer la propiedad **DBPROP\_IRowsetChange** además de las propiedades que se describen en "Admitir operaciones de actualización":  
  
```  
pPropSet->AddProperty(DBPROP_IRowsetUpdate, true);  
```  
  
 Cuando se llama a **Update** o a `UpdateAll`, los métodos transfieren los cambios de la memoria caché local al almacén de datos y, después, borran la memoria caché local. Dado que la actualización transfiere los cambios solo de la fila actual, es importante que la aplicación realice un seguimiento de qué fila debe actualizar y cuándo actualizarla. En el ejemplo siguiente se muestra cómo actualizar dos filas consecutivas:  
  
```  
// Instantiate a rowset based on the user record class CTable<CAccessor<CProductAccessor> > product; CSession session; // Open the rowset and move to the 100th row product.Open(session, "Product", &ps, 1);  // ps is the property set product.MoveToBookmark(&bookmark, 0);      // Assume that bookmark is set to 100th row // Change the values of columns "Name" and "Units in Stock" in the 100th row of the Product table _tcscpy_s( product.m_ProductName, product.m_sizeOfProductName, _T( "Wick" ) ); product.m_UnitsInStock = 10000; HRESULT hr = product.SetData( );  // No changes made to row 100 yet product.Update();                 // Update row 100 now // Change the values of columns "Name" and "Units in Stock" in the 101st row of the Product table product.MoveNext( ); _tcscpy_s( product.m_ProductName, product.m_sizeOfProductName _T( "Wax" ) ); product.m_UnitsInStock = 500; HRESULT hr = product.SetData( );  // No changes made to row 101 yet product.Update();                 // Update row 101 now  
```  
  
 Para asegurarse de que se transfieren los cambios pendientes, debe llamar a **Update** antes de pasar a otra fila. Sin embargo, si esta acción resulta tediosa o poco eficaz, por ejemplo, cuando la aplicación necesite actualizar cientos de filas, puede usar `UpdateAll` para actualizar todas las filas a la vez.  
  
 Por ejemplo, si la primera llamada a **Update** no estaba presente en el código anterior, la fila 100 se mantendría sin cambios, pero se cambiaría la fila 101. Después de ese punto, la aplicación tendría que llamar a `UpdateAll` o regresar a la fila 100 y llamar a **Update** para actualizar esa fila.  
  
 Por último, una de las principales razones para diferir los cambios es que se pueden deshacer. La llamada a [CRowset::Undo](../../data/oledb/crowset-undo.md) revierte el estado de la memoria caché de cambios local al estado del almacén de datos antes de aplicar los cambios pendientes. Es importante tener en cuenta que **Deshacer** no revierte el estado de la memoria caché local en un paso \(el estado anterior al último cambio\), sino que borra la memoria caché local de esa fila. Además, **Deshacer** afecta solo a la fila actual.  
  
## Vea también  
 [Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)   
 [CRowset \(Clase\)](../../data/oledb/crowset-class.md)   
 [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)