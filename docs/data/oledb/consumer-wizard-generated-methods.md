---
title: "M&#233;todos generados por el Asistente para consumidores | Microsoft Docs"
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
  - "clases y métodos con atributos"
  - "CloseAll (método)"
  - "CloseDataSource (método)"
  - "clases y métodos generados por el asistente para consumidores"
  - "GetRowsetProperties (método)"
  - "métodos [C++], generados por el asistente para consumidores OLE DB"
  - "consumidores OLE DB, clases y métodos generados por el asistente"
  - "OpenAll (método)"
  - "OpenDataSource (método)"
  - "OpenRowset (método)"
  - "clases y métodos generados por el asistente"
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# M&#233;todos generados por el Asistente para consumidores
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El Asistente para consumidores OLE DB ATL y el Asistente para aplicaciones MFC generan determinadas funciones que es necesario conocer.  Observe que algunos métodos se implementan de forma diferente en los proyectos con atributos, por lo que hay ciertas cuestiones que deberá tener en cuenta; cada una se explica más adelante.  Para obtener más información sobre cómo ver el código insertado, vea [Depurar código insertado](../Topic/How%20to:%20Debug%20Injected%20Code.md).  
  
-   `OpenAll` abre el origen de datos y los conjuntos de filas, y activa los marcadores si están disponibles.  
  
-   `CloseAll` cierra todos los conjuntos de filas abiertos y libera todas las ejecuciones de comandos.  
  
-   `OpenRowset` se llama desde OpenAll para abrir el conjunto o los conjuntos de filas del consumidor.  
  
-   `GetRowsetProperties` recupera un puntero al conjunto de propiedades del conjunto de filas que permite establecer las propiedades.  
  
-   `OpenDataSource` abre el origen de datos mediante la cadena de inicialización especificada en el cuadro de diálogo **Propiedades de vínculo de datos**.  
  
-   `CloseDataSource` cierra el origen de datos de forma apropiada.  
  
## OpenAll y CloseAll  
  
```  
HRESULT OpenAll();   
void CloseAll();  
```  
  
 En el ejemplo siguiente se muestra cómo se puede llamar a `OpenAll` y `CloseAll` cuando se ejecuta el mismo comando de forma repetida.  Compárelo con el ejemplo de código de [CCommand::Close](../../data/oledb/ccommand-close.md), en el que se muestra una variación que llama a **Close** y `ReleaseCommand`, en lugar de a `CloseAll`.  
  
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
  
## Comentarios  
 Observe que si se define un método `HasBookmark`, el código `OpenAll`  establece la propiedad DBPROP\_IRowsetLocate; asegúrese de que sólo define ese método si el proveedor admite dicha propiedad.  
  
## OpenRowset  
  
```  
// OLE DB Template version:   
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)  
// Attribute-injected version:  
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);  
```  
  
 **OpenAll** llama a este método para abrir el conjunto o los conjuntos de filas en el consumidor.  Normalmente, no es necesario llamar a `OpenRowset` si no desea trabajar con varios orígenes de datos\/sesiones\/conjuntos de filas.  `OpenRowset` se declara en el archivo de encabezado de la clase de comando o tabla:  
  
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
  
 Los atributos implementan este método de forma distinta.  Esta versión toma un objeto de sesión y una cadena de comando como predeterminados para la cadena de comando especificada en db\_command, aunque puede pasar otra distinta.  Observe que si se define un método `HasBookmark`, el código `OpenRowset` establece la propiedad DBPROP\_IRowsetLocate; asegúrese de que solo define ese método si el proveedor admite dicha propiedad.  
  
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
  
## GetRowsetProperties  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet);  
```  
  
 Este método recupera un puntero al conjunto de propiedades del conjunto de filas; este puntero se puede usar para establecer propiedades como DBPROP\_IRowsetChange.  `GetRowsetProperties` se utiliza en la clase de registro de usuario del siguiente modo.  Este código se puede modificar para establecer propiedades adicionales del conjunto de filas:  
  
```  
void GetRowsetProperties(CDBPropSet* pPropSet)  
{  
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);  
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
}  
```  
  
## Comentarios  
 No se debe definir un método global `GetRowsetProperties`, ya que podría causar conflictos con el definido por el administrador.  Observe que éste es un método generado por el asistente que se recibe con los proyectos con plantillas y atributos; los atributos no insertan este código.  
  
## OpenDataSource y CloseDataSource  
  
```  
HRESULT OpenDataSource();   
void CloseDataSource();  
```  
  
## Comentarios  
 El asistente define los métodos `OpenDataSource` y `CloseDataSource` ; el método `OpenDataSource` llama a [CDataSource::OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).  
  
## Vea también  
 [Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)