---
title: Métodos generados por el Asistente para consumidores | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OpenAll method
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- methods [C++], OLE DB Consumer Wizard-generated
- CloseDataSource method
- consumer wizard-generated classes and methods
- OpenDataSource method
- CloseAll method
- OpenRowset method
- GetRowsetProperties method
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c0e03d24f61b3eba1ff4c6fa1e4d888a0252a21b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="consumer-wizard-generated-methods"></a>Métodos generados por el Asistente para consumidores
El Asistente para consumidores OLE DB ATL y el Asistente para aplicaciones MFC generan determinadas funciones que deben tener en cuenta. Tenga en cuenta que algunos métodos se implementan de manera diferente en los proyectos con atributos, por lo que hay algunas advertencias; cada caso se trata más adelante. Para obtener información acerca de cómo ver código insertado, vea [Depurar código insertado](/visualstudio/debugger/how-to-debug-injected-code).  
  
-   `OpenAll` se abre el origen de datos, conjuntos de filas y activa los marcadores si están disponibles.  
  
-   `CloseAll` cierra todos los conjuntos de filas y libera todas las ejecuciones de comandos.  
  
-   `OpenRowset` se llama desde OpenAll para abrir conjuntos de filas o un conjunto de filas del consumidor.  
  
-   `GetRowsetProperties` Recupera un puntero a la propiedad del conjunto de filas con qué propiedades se pueden establecer.  
  
-   `OpenDataSource` Abre el origen de datos mediante la cadena de inicialización especificada en el **propiedades de vínculo de datos** cuadro de diálogo.  
  
-   `CloseDataSource` cierra el origen de datos de una manera adecuada.  
  
## <a name="openall-and-closeall"></a>OpenAll y CloseAll  
  
```  
HRESULT OpenAll();   

void CloseAll();  
```  
  
 En el ejemplo siguiente se muestra cómo se puede llamar a `OpenAll` y `CloseAll` cuando se ejecuta el mismo comando varias veces. Compárelo con el ejemplo de código en [CCommand:: Close](../../data/oledb/ccommand-close.md), que muestra una variación que llama a **cerrar** y `ReleaseCommand` en lugar de `CloseAll`.  
  
```  
int main(int argc, char* argv[])  
{  
   HRESULT hr;  
  
   hr = CoInitialize(NULL);  
  
   CCustOrdersDetail rs;      // Your CCommand-derived class  
   rs.m_OrderID = 10248;      // Open order 10248  
   hr = rs.OpenAll();         // (Open also executes the command)  
   hr = rs.MoveFirst();         // Move to the first row and print it  
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );  
  
   // Close the first command execution  
   rs.Close();  
  
   rs.m_OrderID = 10249;      // Open order 10249 (a new order)  
   hr = rs.Open();            // (Open also executes the command)  
   hr = rs.MoveFirst();         // Move to the first row and print it  
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );  
  
   // Close the second command execution;  
   // Instead of rs.CloseAll() you could call  
   // rs.Close() and rs.ReleaseCommand():  
   rs.CloseAll();  
  
   CoUninitialize();  
   return 0;  
}  
```  
  
## <a name="remarks"></a>Comentarios  
 Tenga en cuenta que, si define un `HasBookmark` método, la `OpenAll` código establece la propiedad DBPROP_IRowsetLocate; Asegúrese de que sólo hace esto si su proveedor admite esa propiedad.  
  
## <a name="openrowset"></a>OpenRowset  
  
```  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
 **OpenAll** llama a este método para abrir el conjunto de filas o conjuntos de filas en el consumidor. Por lo general, no es necesario llamar a `OpenRowset` a menos que desee trabajar con varios orígenes de datos/sesiones/conjuntos de filas. `OpenRowset` se declara en el archivo de encabezado de clase de comando o tabla:  
  
```  
// OLE DB Template version:  
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)  
{  
   HRESULT hr = Open(m_session, NULL, pPropSet);  
   #ifdef _DEBUG  
   if(FAILED(hr))  
      AtlTraceErrorRecords(hr);  
   #endif  
   return hr;  
}  
```  
  
 Los atributos implementan este método de manera diferente. Esta versión toma un objeto de sesión y una cadena de comandos cuyo valor predeterminado es la cadena de comando especificada en db_command, aunque puede pasar otra diferente. Tenga en cuenta que, si define un `HasBookmark` método, la `OpenRowset` código establece la propiedad DBPROP_IRowsetLocate; Asegúrese de que sólo hace esto si su proveedor admite esa propiedad.  
  
```  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)  
{  
  
   DBPROPSET *pPropSet = NULL;  
   CDBPropSet propset(DBPROPSET_ROWSET);  
   __if_exists(HasBookmark)  
  
   {  
      propset.AddProperty(DBPROP_IRowsetLocate, true);  
      pPropSet= &propset;  
      }  
...  
}  
```  
  
## <a name="getrowsetproperties"></a>GetRowsetProperties  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet);  
```  
  
 Este método recupera un puntero al conjunto de propiedades del conjunto de filas; Puede utilizar este puntero para establecer propiedades como DBPROP_IRowsetChange. `GetRowsetProperties` se utiliza en la clase de registro de usuario como sigue. Puede modificar este código para establecer las propiedades del conjunto de filas adicionales:  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## <a name="remarks"></a>Comentarios  
 No debe definir un global `GetRowsetProperties` método debido a podría estar en conflicto con la define por el asistente. Tenga en cuenta que se trata de un método generados por el asistente que se obtiene con proyectos en plantillas y atributos; los atributos no insertan este código.  
  
## <a name="opendatasource-and-closedatasource"></a>OpenDataSource y CloseDataSource  
  
```  
HRESULT OpenDataSource();   

void CloseDataSource();  
```  
  
## <a name="remarks"></a>Comentarios  
 El asistente define los métodos `OpenDataSource` y `CloseDataSource`; `OpenDataSource` llamadas [CDataSource:: OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).  
  
## <a name="see-also"></a>Vea también  
 [Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)