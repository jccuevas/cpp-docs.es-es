---
title: Implementar un consumidor sencillo
ms.date: 08/19/2019
helpviewer_keywords:
- OLE DB consumers, implementing
ms.assetid: 13828167-23a4-4e94-8b6c-878262fda464
ms.openlocfilehash: 2f290f2a17c51682c75fbc09118757e5fd12c4f7
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "79544709"
---
# <a name="implementing-a-simple-consumer"></a>Implementar un consumidor sencillo

::: moniker range="vs-2019"

El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores. Puede seguir agregando la funcionalidad manualmente. Para obtener más información, consulte [Crear un consumidor sin utilizar un asistente](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="<=vs-2017"

Los temas siguientes muestran cómo editar los archivos creados por el **Asistente para aplicaciones MFC** y **Asistente para consumidores OLE DB ATL** para crear un consumidor sencillo. En este ejemplo tiene las siguientes partes:

- [Recuperación de datos con el consumidor](#retrieve) muestra cómo implementar el código en el consumidor que lee todos los datos, fila por fila, de una tabla de base de datos.

- [Agregar compatibilidad con marcadores al consumidor](#bookmark) muestra cómo agregar compatibilidad con marcadores al consumidor.

> [!NOTE]
> Puede usar la aplicación de consumidor que se describe en esta sección para probar los proveedores de ejemplo `MyProv` y `Provider`.

> [!NOTE]
> Para crear una aplicación de consumidor con el fin de probar `MyProv` (se describe el mismo proveedor en [Mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md)), debe incluir compatibilidad con marcadores como se describe en [Agregar compatibilidad con marcadores al consumidor](#bookmark).

## <a name="retrieving-data-with-the-consumer"></a><a name="retrieve" ></a> Recuperación de datos con el consumidor

### <a name="to-modify-the-console-application-to-use-the-ole-db-consumer"></a>Modificar la aplicación de consola para usar el consumidor OLE DB

1. En `MyCons.cpp`, cambie el código principal mediante la inserción del texto en negrita como sigue:

    ```cpp
    // MyCons.cpp : Defines the entry point for the console application.
    //
    #include "pch.h" // "stdafx.h" in Visual Studio 2017 and earlier
    #include "Products.h"
    ...
    int main(int argc, char* argv[])
    {
       HRESULT hr = CoInitialize(NULL);   // Instantiate rowset
       CProducts rs;
       hr = rs.OpenAll();
       ATLASSERT(SUCCEEDED(hr ) );
       hr = rs.MoveFirst();   // Iterate through the rowset
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )   {      // Print out the column information for each row
         printf("Product ID: %d, Name: %s, Unit Price: %d, Quantity per Unit: %d, Units in Stock %d, Reorder Level %d\n",
           rs.m_ProductID, rs.m_ProductName, rs.m_UnitPrice, rs.m_QuantityPerUnit, rs.m_UnitsInStock, rs.m_ReorderLevel );
         hr = rs.MoveNext();   }
       rs.Close();
       rs.ReleaseCommand();
       CoUninitialize();

       return 0;
    }
    ```

## <a name="adding-bookmark-support-to-the-consumer"></a><a name="bookmark" ></a> Agregar compatibilidad con marcadores al consumido

Un marcador es una columna que identifica de forma única las filas de la tabla. Normalmente es la columna de clave, pero no siempre; es específico del proveedor. En esta sección se muestra cómo agregar compatibilidad con marcadores. Para ello, deberá realizar los pasos siguientes en la clase de registro de usuario:

- Cree una instancia de los marcadores. Estos son los objetos de tipo [CBookmark](../../data/oledb/cbookmark-class.md).

- Solicite una columna de marcador del proveedor estableciendo la propiedad `DBPROP_IRowsetLocate`.

- Agregue una entrada de marcador al mapa de columnas mediante la macro [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

Los pasos anteriores proporcionan compatibilidad con marcadores y un objeto de marcador con el que se va a trabajar. Este ejemplo de código muestra un marcador como sigue:

- Abra un archivo para escritura.

- Genera los datos del conjunto de filas en el archivo fila por fila.

- Mueva el cursor del conjunto de filas al marcador mediante una llamada a [MoveToBookmark](../../data/oledb/crowset-movetobookmark.md).

- Genere la fila marcada anexándola al final del archivo.

> [!NOTE]
> Si usa esta aplicación de consumidor para probar la aplicación de proveedor de ejemplo `Provider`, omita la compatibilidad con marcadores que se describe en esta sección.

### <a name="to-instantiate-the-bookmark"></a>Crear una instancia del marcador

1. El descriptor de acceso debe contener un objeto de tipo [CBookmark](../../data/oledb/cbookmark-class.md). El parámetro *nSize* especifica el tamaño del búfer del marcador en bytes (normalmente 4 para las plataformas de 32 bits y 8 para las de 64 bits). Agregue la declaración siguiente a los miembros de datos de columna en la clase de registro de usuario:

    ```cpp
    //////////////////////////////////////////////////////////////////////
    // Products.h
    class CProductsAccessor
    {
    public:
       CBookmark<4> m_bookmark;   // Add bookmark declaration
       LONG m_ProductID;
       ...
    ```

### <a name="to-request-a-bookmark-column-from-the-provider"></a>Solicitar una columna de marcador del proveedor

1. Agregue el código siguiente en el método `GetRowsetProperties` de clase de registro de usuario:

    ```cpp
    // Set the DBPROP_IRowsetLocate property.
    void GetRowsetProperties(CDBPropSet* pPropSet)
    {
       pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
       // Add DBPROP_IRowsetLocate property to support bookmarks   pPropSet->AddProperty(DBPROP_IRowsetLocate, true);
    }
    ```

### <a name="to-add-a-bookmark-entry-to-the-column-map"></a>Agregar una entrada de marcador al mapa de columnas

1. Agregue la siguiente entrada al mapa de columnas en la clase de registro de usuario:

    ```cpp
    // Set a bookmark entry in the column map.
    BEGIN_COLUMN_MAP(CProductsAccessor)
       BOOKMARK_ENTRY(m_bookmark)   // Add bookmark entry
       COLUMN_ENTRY_LENGTH_STATUS(1, m_ProductID, m_dwProductIDLength, m_dwProductIDStatus)
       COLUMN_ENTRY_LENGTH_STATUS(2, m_ProductName, m_dwProductNameLength, m_dwProductNameStatus)
    ...
    END_COLUMN_MAP()
    ```

### <a name="to-use-a-bookmark-in-your-main-code"></a>Utilizar un marcador en el código principal

1. En el archivo `MyCons.cpp` de la aplicación de consola que creó anteriormente, cambie el código principal para que quede como sigue. Para utilizar marcadores, el código principal debe crear una instancia de su propio objeto de marcador (`myBookmark`); se trata de un marcador diferente de la especificada en el descriptor de acceso (`m_bookmark`).

    ```cpp
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
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
       {
          nCounter++;
          if(nCounter == 5 )
             myBookmark = rs.m_bookmark;
          // Output the column information for each row:
          outfile << rs.m_ProductID << rs.m_ProductName << lPrice << rs.m_QuantityPerUnit << rs.m_UnitsInStock << rs.m_ReorderLevel << endl;
          hr = rs.MoveNext();
       }

       // Move cursor to bookmark
       hr = rs.MoveToBookmark(myBookmark);

       // Iterate through the rowset and output column data to output.txt row by row
       // In the file, mark the beginning of this set of data:
       outfile << "row dump starting from bookmarked row" << endl;
       while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
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

Para obtener más información sobre los marcadores, vea [Utilizar marcadores](../../data/oledb/using-bookmarks.md). También se muestran ejemplos de marcadores en [Actualizar conjuntos de filas](../../data/oledb/updating-rowsets.md).

::: moniker-end

## <a name="see-also"></a>Consulte también

[Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
