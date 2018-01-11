---
title: Implementar un consumidor sencillo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- clients, creating
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 43ebcd38a3125db7373755b1ebf5366cae8af56b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="implementing-a-simple-consumer"></a>Implementar un consumidor sencillo
Los temas siguientes muestran cómo editar los archivos creados por el Asistente para aplicaciones MFC y el Asistente para consumidores OLE DB ATL para crear un consumidor sencillo. Este ejemplo tiene los siguientes componentes:  
  
-   "Recuperar datos con el consumidor" muestra cómo implementar el código en el consumidor que lee todos los datos, fila por fila, de una tabla de base de datos.  
  
-   "Agregar compatibilidad con marcadores al consumidor", muestra cómo agregar compatibilidad con marcadores al consumidor.  
  
-   "Agregar compatibilidad con XML al consumidor", muestra cómo modificar el código de consumidor para generar los datos del conjunto de filas obtenido como datos XML.  
  
> [!NOTE]
>  Puede usar la aplicación de consumidor que se describe en esta sección para probar los proveedores de ejemplo MyProv y Provider.  
  
> [!NOTE]
>  Para crear una aplicación de consumidor para probar MyProv (el mismo proveedor que se describe en [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)), debe incluir compatibilidad con marcadores como se describe en "Agregar compatibilidad con marcadores al consumidor".  
  
> [!NOTE]
>  Para compilar una aplicación de consumidor para probar el proveedor, deje la compatibilidad con marcadores que se describe en "Agregar marcador admite al consumidor" y vaya a "Agregar compatibilidad con XML al consumidor".  
  
## <a name="retrieving-data-with-the-consumer"></a>Recuperar datos con el consumidor  
  
#### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Para modificar la aplicación de consola para utilizar el consumidor de OLE DB  
  
1.  En MyCons.cpp, cambie el código principal insertando el texto en negrita, como se indica a continuación:  
  
    ```  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
    #include "stdafx.h"  
    #include "Products.h"  
    ...  
    int main(int argc, char* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset   CProducts rs;   hr = rs.OpenAll();   ATLASSERT( SUCCEEDED( hr ) );   hr = rs.MoveFirst();   // Iterate through the rowset   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row      printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",             rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );      hr = rs.MoveNext();   }   rs.Close();   rs.ReleaseCommand();   CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## <a name="adding-bookmark-support-to-the-consumer"></a>Agregar compatibilidad con marcadores al consumidor  
 Un marcador es una columna que identifica de forma única las filas de la tabla. Normalmente es la columna de clave, pero no siempre; es específica del proveedor. En esta sección se muestra cómo agregar compatibilidad con marcadores. Para ello, debe hacer lo siguiente en la clase de registro de usuario:  
  
-   Crear instancias de los marcadores. Se trata de objetos de tipo [CBookmark](../../data/oledb/cbookmark-class.md).  
  
-   Solicitar una columna de marcador del proveedor estableciendo la **DBPROP_IRowsetLocate** propiedad.  
  
-   Agregar una entrada de marcador al mapa de columnas mediante la [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md) macro.  
  
 Los pasos anteriores le ofrecen compatibilidad con marcadores y un objeto de marcador con el que se va a trabajar. Este ejemplo de código muestra un marcador como sigue:  
  
-   Abra un archivo para escribir en él.  
  
-   Datos del conjunto de filas de salida en el archivo fila por fila.  
  
-   Mover el cursor de conjunto de filas al marcador mediante una llamada a [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md).  
  
-   La fila marcada, ésta se agrega al final del archivo de salida.  
  
> [!NOTE]
>  Si utiliza esta aplicación de consumidor para probar la aplicación de proveedor de ejemplo de proveedor, deje la compatibilidad con marcadores que se describe en esta sección.  
  
#### <a name="to-instantiate-the-bookmark"></a>Para crear una instancia del marcador  
  
1.  El descriptor de acceso debe contener un objeto de tipo [CBookmark](../../data/oledb/cbookmark-class.md). El `nSize` parámetro especifica el tamaño del búfer del marcador en bytes (normalmente 4 para plataformas de 32 bits y 8) para plataformas de 64 bits. Agregue la siguiente declaración a los miembros de datos de columna en la clase de registro de usuario:  
  
    ```  
    //////////////////////////////////////////////////////////////////////  
    // Products.h  
    class CProductsAccessor  
    {  
    public:  
       CBookmark<4> m_bookmark;   // Add bookmark declaration  
       LONG m_ProductID;  
       ...  
    ```  
  
#### <a name="to-request-a-bookmark-column-from-the-provider"></a>Para solicitar una columna de marcador del proveedor  
  
1.  Agregue el código siguiente en el `GetRowsetProperties` método en la clase de registro de usuario:  
  
    ```  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Para agregar una entrada de marcador al mapa de columnas  
  
1.  Agregue la siguiente entrada al mapa de columnas en la clase de registro de usuario:  
  
    ```  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### <a name="to-use-a-bookmark-in-your-main-code"></a>Para utilizar un marcador en el código principal  
  
1.  En el archivo MyCons.cpp de la aplicación de consola que creó anteriormente, cambie el código principal para que quede como sigue. Para utilizar marcadores, el código principal necesita crear instancias de su propio objeto de marcador (`myBookmark`); se trata de un marcador diferente de la especificada en el descriptor de acceso (`m_bookmark`).  
  
    ```  
    ///////////////////////////////////////////////////////////////////////  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
  
    #include "stdafx.h"  
    #include "Products.h"   
    #include <iostream>  
    #include <fstream>  
    using namespace std;  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);  
  
       // Instantiate rowset  
       CProducts rs;  
  
       hr = rs.OpenAll();  
       hr = rs.MoveFirst();  
  
       // Cast CURRENCY m_UnitPrice to a long value  
       LONGLONG lPrice = rs.m_UnitPrice.int64;  
  
       // Open file output.txt for writing in overwrite mode  
       ofstream outfile( "C:\\output.txt", ios::out );  
  
       if (!outfile)      // Test for invalid file  
          return -1;  
  
       // Instantiate a bookmark object myBookmark for the main code  
       CBookmark<4> myBookmark;  
       int nCounter = 0;  
  
       // Iterate through the rowset and output column data to output.txt row by row  
       // In the file, mark the beginning of this set of data:  
       outfile << "initial row dump" << endl;  
       while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
       {  
          nCounter++;  
          if( nCounter == 5 )  
             myBookmark = rs.bookmark;  
          // Output the column information for each row:  
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;  
          hr = rs.MoveNext();  
       }  
  
       // Move cursor to bookmark  
       hr = rs.MoveToBookmark(myBookmark);  
  
       // Iterate through the rowset and output column data to output.txt row by row  
       // In the file, mark the beginning of this set of data:  
       outfile << "row dump starting from bookmarked row" << endl;  
       while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
       {  
          // Output the column information for each row  
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;  
          hr = rs.MoveNext();  
       }  
  
       rs.CloseAll();  
       CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
 Para obtener más información acerca de los marcadores, vea [Using Bookmarks](../../data/oledb/using-bookmarks.md). También se muestran varios ejemplos de marcadores en [actualizar conjuntos de filas](../../data/oledb/updating-rowsets.md).  
  
## <a name="adding-xml-support-to-the-consumer"></a>Agregar compatibilidad con XML al consumidor  
 Como se describe en [obtiene acceso a datos XML](../../data/oledb/accessing-xml-data.md), hay dos maneras de recuperar datos XML desde un origen de datos: mediante [CStreamRowset](../../data/oledb/cstreamrowset-class.md) o con [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md). Este ejemplo se utiliza `CStreamRowset`, que es más eficaz, pero requiere tener SQL Server 2000 en ejecución en el equipo en el que se ejecuta esta aplicación de ejemplo.  
  
#### <a name="to-modify-the-command-class-to-inherit-from-cstreamrowset"></a>Para modificar la clase de comando que herede de CStreamRowset  
  
1.  En la aplicación de consumidor que creó anteriormente, cambie la `CCommand` declaración para especificar `CStreamRowset` como el conjunto de filas de la clase como sigue:  
  
    ```  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### <a name="to-modify-the-main-code-to-retrieve-and-output-the-xml-data"></a>Para modificar el código para recuperar y los datos XML de salida principal  
  
1.  En el archivo MyCons.cpp de la aplicación de consola que creó anteriormente, cambie el código principal para que quede como sigue:  
  
    ```  
    ///////////////////////////////////////////////////////////////////////  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
  
    #include "stdafx.h"  
    #include "Products.h"   
    #include <iostream>  
    #include <fstream>  
    using namespace std;  
  
    int _tmain(int argc, _TCHAR* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);  
  
       // Instantiate rowset  
       CProducts rs;  
  
       // Add variable declarations for the Read method to handle sequential stream data  
       CHAR buffer[1001];  // Pointer to buffer into which data stream is read  
       ULONG cbRead;       // Actual number of bytes read from the data stream  
  
       hr = rs.OpenAll();  
  
       // Open file output.txt for writing in overwrite mode  
       ofstream outfile( "C:\\output.txt", ios::out );  
  
       if (!outfile)      // Test for invalid file  
          return -1;  
  
       // The following loop reads 1000 bytes of the data stream at a time   
       // until it reaches the end of the data stream  
       for (;;)  
       {  
          // Read sequential stream data into buffer  
          HRESULT hr = rs.m_spStream->Read(buffer, 1000, &cbRead);  
          if (FAILED (hr))  
             break;  
          // Output buffer to file  
          buffer[cbRead] = 0;  
          outfile << buffer;  
          // Test for end of data stream  
          if (cbRead < 1000)  
             break;  
       }  
  
       rs.CloseAll();  
       CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)