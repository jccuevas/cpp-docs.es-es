---
title: "Implementar un consumidor sencillo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clientes, crear"
  - "consumidores OLE DB, implementar"
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Implementar un consumidor sencillo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En los siguientes temas se muestra cómo modificar los archivos que crea el Asistente para aplicaciones MFC y el Asistente para consumidores OLE DB ATL para crear un consumidor sencillo.  Este ejemplo se divide en las siguientes partes:  
  
-   En "Recuperar datos con el consumidor" se muestra cómo implementar en el consumidor código que lee todos los datos, fila por fila, de una tabla de base de datos.  
  
-   En "Agregar compatibilidad con marcadores al consumidor" se muestra cómo agregar compatibilidad con marcadores al consumidor.  
  
-   En "Agregar compatibilidad con XML al consumidor" se muestra cómo modificar el código del consumidor para producir como resultado los datos del conjunto de filas recuperadas como datos XML.  
  
> [!NOTE]
>  Puede utilizar la aplicación de consumidor que se describe en esta sección para probar los proveedores de ejemplo MyProv y Provider.  
  
> [!NOTE]
>  Si desea crear una aplicación de consumidor para probar MyProv \(el proveedor que se describe en [Mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)\), debe incluir la compatibilidad con marcadores como se describe en "Agregar compatibilidad con marcadores al consumidor".  
  
> [!NOTE]
>  Si desea crear una aplicación de consumidor para probar Provider, omita la parte relativa a la compatibilidad con marcadores que se describe en "Agregar compatibilidad con marcadores al consumidor" y pase a "Agregar compatibilidad con XML al consumidor".  
  
## Recuperar datos con el consumidor  
  
#### Para modificar la aplicación de consola de forma que utilice el consumidor OLE DB  
  
1.  En MyCons.cpp, cambie el código principal mediante la inserción del texto que aparece en negrita a continuación:  
  
    ```  
    // MyCons.cpp : Defines the entry point for the console application.  
    //  
    #include "stdafx.h"  
    #include "Products.h"  
    ...  
    int main(int argc, char* argv[])  
    {  
       HRESULT hr = CoInitialize(NULL);        // Instantiate rowset    CProducts rs;        hr = rs.OpenAll();    ATLASSERT( SUCCEEDED( hr ) );    hr = rs.MoveFirst();        // Iterate through the rowset    while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )    {       // Print out the column information for each row       printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",              rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );       hr = rs.MoveNext();    }        rs.Close();    rs.ReleaseCommand();        CoUninitialize();  
  
       return 0;  
    }  
    ```  
  
## Agregar compatibilidad con marcadores al consumidor  
 Un marcador es una columna que identifica de manera única filas de la tabla.  Normalmente es la columna clave, pero no siempre: es específico de cada proveedor.  En esta sección se muestra cómo agregar compatibilidad con marcadores.  Para ello, debe llevar a cabo los pasos siguientes en la clase de registro de usuario:  
  
-   Cree instancias de los marcadores.  Éstos son objetos de tipo [CBookmark](../../data/oledb/cbookmark-class.md).  
  
-   Solicite una columna de marcador del proveedor estableciendo la propiedad **DBPROP\_IRowsetLocate**.  
  
-   Agregue una entrada de marcador al mapa de columnas mediante la macro [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md).  
  
 Con los pasos anteriores se genera compatibilidad con marcadores y un objeto de marcador con el que trabajar.  Con este código de ejemplo, el marcador se muestra de la siguiente manera:  
  
-   Se abre un archivo para escritura.  
  
-   Se envían los datos del conjunto de filas al archivo, fila por fila.  
  
-   Se llama a [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md) para mover el cursor del conjunto de filas al marcador.  
  
-   Se envía la fila marcada, anexándola al final del archivo.  
  
> [!NOTE]
>  Si utiliza esta aplicación de consumidor para probar la aplicación de proveedor de ejemplo Provider, omita la parte relativa a la compatibilidad con marcadores que se describe en esta sección.  
  
#### Para crear una instancia del marcador  
  
1.  El descriptor de acceso tiene que contener un objeto de tipo [CBookmark](../../data/oledb/cbookmark-class.md).  Con el parámetro `nSize` se especifica el tamaño del búfer del marcador en bytes \(normalmente 4 en las plataformas de 32 bits y 8 en las de 64 bits\).  Agregue la siguiente declaración a los miembros de datos de columna de la clase de registro de usuario:  
  
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
  
#### Para solicitar una columna de marcador al proveedor  
  
1.  Agregue el siguiente código al método `GetRowsetProperties` de la clase de registro de usuario:  
  
    ```  
    // Set the DBPROP_IRowsetLocate property.  
    void GetRowsetProperties(CDBPropSet* pPropSet)  
    {  
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
       // Add DBPROP_IRowsetLocate property to support bookmarks    pPropSet->AddProperty(DBPROP_IRowsetLocate, true);  
    }  
    ```  
  
#### Para agregar una entrada de marcador al mapa de columnas  
  
1.  Agregue la siguiente entrada al mapa de columnas de la clase de registro de usuario:  
  
    ```  
    // Set a bookmark entry in the column map.  
    BEGIN_COLUMN_MAP(CProductsAccessor)  
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry  
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)  
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)  
    ...  
    END_COLUMN_MAP()  
    ```  
  
#### Para utilizar un marcador en el código principal  
  
1.  En el archivo MyCons.cpp de la aplicación de consola que creó anteriormente, cambie el código principal para que se lea como sigue:  Para utilizar marcadores, el código principal tiene que crear instancias de su propio objeto de marcador \(`myBookmark`\); se trata de un marcador distinto al del descriptor de acceso \(`m_bookmark`\).  
  
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
  
 Para obtener más información acerca de los marcadores, vea [Utilizar marcadores](../../data/oledb/using-bookmarks.md).  Además, en [Actualizar conjuntos de filas](../../data/oledb/updating-rowsets.md) se muestran varios ejemplos de marcadores.  
  
## Agregar compatibilidad con XML al consumidor  
 Como se describe en [Obtener acceso a datos XML](../../data/oledb/accessing-xml-data.md), existen dos maneras de recuperar datos XML en un origen de datos: mediante [CStreamRowset](../../data/oledb/cstreamrowset-class.md) o mediante [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).  En este ejemplo se utiliza `CStreamRowset`, que es más eficaz, pero requiere que SQL Server 2000 se ejecute en el equipo en el que se ejecuta esta aplicación de ejemplo.  
  
#### Para modificar la clase de comando de forma que herede de CStreamRowset  
  
1.  En la aplicación de consumidor que se creó anteriormente, cambie la declaración `CCommand` de la forma siguiente para especificar `CStreamRowset` como clase de conjunto de filas:  
  
    ```  
    class CProducts : public CCommand<CAccessor<CProductsAccessor>, CStreamRowset >  
    ```  
  
#### Para modificar el código principal de forma que recupere y produzca como resultado los datos XML  
  
1.  En el archivo MyCons.cpp de la aplicación de consola que creó anteriormente, cambie el código principal para que se lea como sigue:  
  
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
  
## Vea también  
 [Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)