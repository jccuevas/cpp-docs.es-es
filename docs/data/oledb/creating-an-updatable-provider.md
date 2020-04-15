---
title: Crear un proveedor actualizable
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 720ceba397d17642402de4d44cbb4481852fa153
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365559"
---
# <a name="creating-an-updatable-provider"></a>Crear un proveedor actualizable

Visual C++ admite proveedores o proveedores actualizables que pueden actualizar (escribir en) el almacén de datos. En este tema se describe cómo crear proveedores actualizables mediante plantillas OLE DB.

En este tema se supone que está empezando con un proveedor viable. Hay dos pasos para crear un proveedor actualizable. Primero debe decidir cómo el proveedor realizará cambios en el almacén de datos; específicamente, si los cambios deben realizarse inmediatamente o aplazarse hasta que se emita un comando update. La sección["Hacer proveedores actualizables"](#vchowmakingprovidersupdatable)describe los cambios y la configuración que debe hacer en el código del proveedor.

A continuación, debe asegurarse de que su proveedor contiene toda la funcionalidad para admitir cualquier cosa que el consumidor pueda solicitar de él. Si el consumidor desea actualizar el almacén de datos, el proveedor debe contener código que conserve los datos en el almacén de datos. Por ejemplo, puede usar la biblioteca en tiempo de ejecución de C o MFC para realizar estas operaciones en el origen de datos. La sección "[Escritura en el origen](#vchowwritingtothedatasource)de datos " describe cómo escribir en el origen de datos, tratar con VALORES NULL y valores predeterminados y establecer marcas de columna.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) es un ejemplo de un proveedor actualizable. UpdatePV es el mismo que MyProv pero con soporte actualizable.

## <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>Hacer que los proveedores sean actualizables

La clave para hacer que un proveedor sea actualizable es comprender qué operaciones desea que realice su proveedor en el almacén de datos y cómo desea que el proveedor lleve a cabo esas operaciones. En concreto, el problema principal es si las actualizaciones en el almacén de datos deben realizarse inmediatamente o diferirse (por lotes) hasta que se emita un comando de actualización.

Primero debe decidir si `IRowsetChangeImpl` desea `IRowsetUpdateImpl` heredar de o en la clase de conjunto de filas. Dependiendo de cuál de estos elija implementar, la funcionalidad de `SetData` `InsertRows`tres `DeleteRows`métodos se verá afectada: , , y .

- Si hereda de [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), llamar a estos tres métodos cambia inmediatamente el almacén de datos.

- Si hereda de [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), los métodos aplazan `GetOriginalData`los `Undo`cambios en el almacén de datos hasta que se llama a `Update`, , o . Si la actualización implica varios cambios, se realizan en modo por lotes (tenga en cuenta que los cambios de procesamiento por lotes pueden agregar una sobrecarga de memoria considerable).

Tenga `IRowsetUpdateImpl` en cuenta `IRowsetChangeImpl`que se deriva de . Por `IRowsetUpdateImpl` lo tanto, le proporciona capacidad de cambio más capacidad por lotes.

### <a name="to-support-updatability-in-your-provider"></a>Para apoyar la capacidad de actualización en su proveedor

1. En la clase de `IRowsetChangeImpl` `IRowsetUpdateImpl`conjunto de filas, herede de o . Estas clases proporcionan interfaces adecuadas para cambiar el almacén de datos:

   **Adición de IRowsetChange**

   Agregue `IRowsetChangeImpl` a su cadena de herencia utilizando este formulario:

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   Agregue `COM_INTERFACE_ENTRY(IRowsetChange)` también `BEGIN_COM_MAP` a la sección de la clase de conjunto de filas.

   **Adición de IRowsetUpdate**

   Agregue `IRowsetUpdate` a su cadena de herencia utilizando este formulario:

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > Debe quitar `IRowsetChangeImpl` la línea de la cadena de herencia. Esta excepción a la directiva mencionada `IRowsetChangeImpl`anteriormente debe incluir el código para .

1. Agregue lo siguiente al`BEGIN_COM_MAP ... END_COM_MAP`mapa COM ( ):

   |  Si implementa   |           Añadir al mapa COM             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Si implementa | Agregar al mapa del conjunto de propiedades |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. En el comando, agregue lo siguiente`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`al mapa del conjunto de propiedades ( ):

   |  Si implementa   |                                             Agregar al mapa del conjunto de propiedades                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. En el mapa del conjunto de propiedades, también debe incluir todos los siguientes valores tal y como aparecen a continuación:

    ```cpp
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)

    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)
    ```

   Puede encontrar los valores utilizados en estas llamadas de macro buscando en Atldb.h los identificadores de propiedad y los valores (si Atldb.h difiere de la documentación en línea, Atldb.h reemplaza la documentación).

   > [!NOTE]
   > Muchas de `VARIANT_FALSE` `VARIANT_TRUE` las plantillas OLE DB requieren muchas de las opciones de configuración; la especificación OLE DB dice que pueden ser de lectura y escritura, pero las plantillas OLE DB solo pueden admitir un valor.

   **Si implementa IRowsetChangeImpl**

   Si implementa `IRowsetChangeImpl`, debe establecer las siguientes propiedades en el proveedor. Estas propiedades se utilizan principalmente `ICommandProperties::SetProperties`para solicitar interfaces a través de .

   - `DBPROP_IRowsetChange`: Si se `DBPROP_IRowsetChange`establece automáticamente.

   - `DBPROP_UPDATABILITY`: Una máscara de bits `IRowsetChange`que `SetData` `DeleteRows`especifica `InsertRow`los métodos admitidos en : , , o .

   - `DBPROP_CHANGEINSERTEDROWS`: el `IRowsetChange::DeleteRows` consumidor `SetData` puede llamar o para las filas recién insertadas.

   - `DBPROP_IMMOBILEROWS`: El conjunto de filas no reordenará las filas insertadas o actualizadas.

   **Si implementa IRowsetUpdateImpl**

   Si implementa `IRowsetUpdateImpl`, debe establecer las siguientes propiedades en el proveedor, `IRowsetChangeImpl` además de establecer todas las propiedades para la lista anterior:

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: Debe ser READ_ONLY Y VARIANT_TRUE.

   - `DBPROP_OWNUPDATEDELETE`: Debe ser READ_ONLY Y VARIANT_TRUE.

   - `DBPROP_OTHERINSERT`: Debe ser READ_ONLY Y VARIANT_TRUE.

   - `DBPROP_OTHERUPDATEDELETE`: Debe ser READ_ONLY Y VARIANT_TRUE.

   - `DBPROP_REMOVEDELETED`: Debe ser READ_ONLY Y VARIANT_TRUE.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > Si admite notificaciones, también puede tener otras propiedades; ver la `IRowsetNotifyCP` sección de esta lista.

## <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>Escritura en el origen de datos

Para leer desde el origen `Execute` de datos, llame a la función. Para escribir en el origen `FlushData` de datos, llame a la función. (En un sentido general, el vaciado significa guardar las modificaciones que realice en una tabla o índice en el disco.)

```cpp
FlushData(HROW, HACCESSOR);
```

Los argumentos de identificador de fila (HROW) y identificador de descriptor de acceso (HACCESSOR) permiten especificar la región que se va a escribir. Normalmente, se escribe un único campo de datos a la vez.

El `FlushData` método escribe datos en el formato en el que se almacenaron originalmente. Si no invalida esta función, el proveedor funcionará correctamente, pero los cambios no se vaciarán en el almacén de datos.

### <a name="when-to-flush"></a>Cuándo vaciar

Las plantillas de proveedor llaman a FlushData siempre que es necesario escribir datos en el almacén de datos; esto suele ocurrir (pero no siempre) como resultado de llamadas a las siguientes funciones:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows`(si hay nuevos datos para insertar en la fila)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Cómo funciona

El consumidor realiza una llamada que requiere un vaciado (como Update) y esta llamada se pasa al proveedor, que siempre hace lo siguiente:

- Llamadas `SetDBStatus` siempre que tenga un valor de estado enlazado.

- Comprueba los indicadores de columna.

- Llama a `IsUpdateAllowed`.

Estos tres pasos ayudan a proporcionar seguridad. A continuación, `FlushData`el proveedor llama a .

### <a name="how-to-implement-flushdata"></a>Cómo implementar FlushData

Para `FlushData`implementar, debe tener en cuenta varios problemas:

Asegurarse de que el almacén de datos puede controlar los cambios.

Controlar valores NULL.

### <a name="handling-default-values"></a>Manejo de valores predeterminados.

Para implementar `FlushData` su propio método, debe:

- Vaya a la clase de conjunto de filas.

- En la clase rowset, coloque la declaración de:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Proporcione una `FlushData`implementación de .

Una buena `FlushData` implementación de almacena solo las filas y columnas que se actualizan realmente. Puede utilizar los parámetros HROW y HACCESSOR para determinar la fila y la columna actuales que se almacenan para la optimización.

Normalmente, el mayor desafío es trabajar con su propio almacén de datos nativo. Si es posible, intente:

- Mantenga el método de escritura en su almacén de datos lo más sencillo posible.

- Controlar valores NULL (opcional pero recomendable).

- Controlar los valores predeterminados (opcional pero aconsejado).

Lo mejor es tener valores especificados reales en el almacén de datos para NULL y valores predeterminados. Es mejor si puede extrapolar estos datos. Si no es así, se recomienda no permitir valores NULL y predeterminados.

En el ejemplo `FlushData` siguiente se `RUpdateRowset` muestra cómo `UpdatePV` se implementa en la clase del ejemplo (consulte Rowset.h en el código de ejemplo):

```cpp
///////////////////////////////////////////////////////////////////////////
// class RUpdateRowset (in rowset.h)
...
HRESULT FlushData(HROW, HACCESSOR)
{
    ATLTRACE2(atlTraceDBProvider, 0, "RUpdateRowset::FlushData\n");

    USES_CONVERSION;
    enum {
        sizeOfString = 256,
        sizeOfFileName = MAX_PATH
    };
    FILE*    pFile = NULL;
    TCHAR    szString[sizeOfString];
    TCHAR    szFile[sizeOfFileName];
    errcode  err = 0;

    ObjectLock lock(this);

    // From a filename, passed in as a command text,
    // scan the file placing data in the data array.
    if (m_strCommandText == (BSTR)NULL)
    {
        ATLTRACE( "RRowsetUpdate::FlushData -- "
                  "No filename specified\n");
        return E_FAIL;
    }

    // Open the file
    _tcscpy_s(szFile, sizeOfFileName, OLE2T(m_strCommandText));
    if ((szFile[0] == _T('\0')) ||
        ((err = _tfopen_s(&pFile, &szFile[0], _T("w"))) != 0))
    {
        ATLTRACE("RUpdateRowset::FlushData -- Could not open file\n");
        return DB_E_NOTABLE;
    }

    // Iterate through the row data and store it.
    for (long l=0; l<m_rgRowData.GetSize(); l++)
    {
        CAgentMan am = m_rgRowData[l];

        _putw((int)am.dwFixed, pFile);

        if (_tcscmp(&am.szCommand[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szCommand2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szCommand2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);

        if (_tcscmp(&am.szText2[0], _T("")) != 0)
            _stprintf_s(&szString[0], _T("%s\n"), am.szText2);
        else
            _stprintf_s(&szString[0], _T("%s\n"), _T("NULL"));
        _fputts(szString, pFile);
    }

    if (fflush(pFile) == EOF || fclose(pFile) == EOF)
    {
        ATLTRACE("RRowsetUpdate::FlushData -- "
                 "Couldn't flush or close file\n");
    }

    return S_OK;
}
```

### <a name="handling-changes"></a>Manejo de cambios

Para que su proveedor controle los cambios, primero debe asegurarse de que el almacén de datos (como un archivo de texto o un archivo de vídeo) tiene instalaciones que le permiten realizar cambios en él. Si no es así, debe crear ese código por separado del proyecto de proveedor.

### <a name="handling-null-data"></a>Manejo de datos NULL

Es posible que un usuario final envíe datos NULL. Al escribir valores NULL en campos del origen de datos, puede haber problemas potenciales. Imagine una aplicación de toma de pedidos que acepte valores para la ciudad y el código postal; podría aceptar uno o ambos valores, pero no ninguno, porque en ese caso la entrega sería imposible. Por lo tanto, debe restringir ciertas combinaciones de valores NULL en campos que tienen sentido para la aplicación.

Como desarrollador del proveedor, debe tener en cuenta cómo almacenará esos datos, cómo leerá esos datos del almacén de datos y cómo los especificará al usuario. En concreto, debe tener en cuenta cómo cambiar el estado de los datos del conjunto de filas en el origen de datos (por ejemplo, StatusStatus - NULL). Decide qué valor devolver cuando un consumidor tiene acceso a un campo que contiene un valor NULL.

Observe el código en el ejemplo UpdatePV; ilustra cómo un proveedor puede controlar los datos NULL. En UpdatePV, el proveedor almacena datos NULL escribiendo la cadena "NULL" en el almacén de datos. Cuando lee datos NULL del almacén de datos, ve esa cadena y, a continuación, vacía el búfer, creando una cadena NULL. También tiene una `IRowsetImpl::GetDBStatus` invalidación en la que devuelve DBSTATUS_S_ISNULL si ese valor de datos está vacío.

### <a name="marking-nullable-columns"></a>Marcar columnas que aceptan valores NULL

Si también implementa conjuntos `IDBSchemaRowsetImpl`de filas de esquema (consulte ), la implementación debe especificar en el conjunto de filas de DBSCHEMA_COLUMNS (normalmente marcado en el proveedor por CxxxSchemaColSchemaRowset) que la columna acepta valores NULL.

También debe especificar que todas las columnas que aceptan valores `GetColumnInfo`NULL contienen el valor DBCOLUMNFLAGS_ISNULLABLE en la versión de la versión .

En la implementación de plantillas OLE DB, si no puede marcar columnas como que aceptan valores NULL, el proveedor supone que deben contener un valor y no permitirá que el consumidor le envíe valores nulos.

En el ejemplo `CommonGetColInfo` siguiente se muestra cómo se implementa la función en CUpdateCommand (consulte UpProvRS.cpp) en UpdatePV. Observe cómo las columnas tienen este DBCOLUMNFLAGS_ISNULLABLE para las columnas que aceptan valores NULL.

```cpp
/////////////////////////////////////////////////////////////////////////////
// CUpdateCommand (in UpProvRS.cpp)

ATLCOLUMNINFO* CommonGetColInfo(IUnknown* pPropsUnk, ULONG* pcCols, bool bBookmark)
{
    static ATLCOLUMNINFO _rgColumns[6];
    ULONG ulCols = 0;

    if (bBookmark)
    {
        ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Bookmark"), 0,
                            sizeof(DWORD), DBTYPE_BYTES,
                            0, 0, GUID_NULL, CAgentMan, dwBookmark,
                            DBCOLUMNFLAGS_ISBOOKMARK)
        ulCols++;
    }

    // Next set the other columns up.
    // Add a fixed length entry for OLE DB conformance testing purposes
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Fixed"), 1, 4, DBTYPE_UI4,
                        10, 255, GUID_NULL, CAgentMan, dwFixed,
                        DBCOLUMNFLAGS_WRITE |
                        DBCOLUMNFLAGS_ISFIXEDLENGTH)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command"), 2, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text"), 3, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Command2"), 4, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szCommand2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;
    ADD_COLUMN_ENTRY_EX(ulCols, OLESTR("Text2"), 5, 16, DBTYPE_STR,
                        255, 255, GUID_NULL, CAgentMan, szText2,
                        DBCOLUMNFLAGS_WRITE | DBCOLUMNFLAGS_ISNULLABLE)
    ulCols++;

    if (pcCols != NULL)
    {
        *pcCols = ulCols;
    }

    return _rgColumns;
}
```

### <a name="default-values"></a>Valores predeterminados

Al igual que con los datos NULL, tiene la responsabilidad de tratar con el cambio de valores predeterminados.

El valor `FlushData` `Execute` predeterminado de y es devolver S_OK. Por lo tanto, si no invalida esta función, los cambios parecen realizarse correctamente (S_OK se devolverán), pero no se transmitirán al almacén de datos.

En `UpdatePV` el ejemplo (en Rowset.h), el método controla los `SetDBStatus` valores predeterminados de la siguiente manera:

```cpp
virtual HRESULT SetDBStatus(DBSTATUS* pdbStatus, CSimpleRow* pRow,
                            ATLCOLUMNINFO* pColInfo)
{
    ATLASSERT(pRow != NULL && pColInfo != NULL && pdbStatus != NULL);

    void* pData = NULL;
    char* pDefaultData = NULL;
    DWORD* pFixedData = NULL;

    switch (*pdbStatus)
    {
        case DBSTATUS_S_DEFAULT:
            pData = (void*)&m_rgRowData[pRow->m_iRowset];
            if (pColInfo->wType == DBTYPE_STR)
            {
                pDefaultData = (char*)pData + pColInfo->cbOffset;
                strcpy_s(pDefaultData, "Default");
            }
            else
            {
                pFixedData = (DWORD*)((BYTE*)pData +
                                          pColInfo->cbOffset);
                *pFixedData = 0;
                return S_OK;
            }
            break;
        case DBSTATUS_S_ISNULL:
        default:
            break;
    }
    return S_OK;
}
```

### <a name="column-flags"></a>Banderas de columna

Si admite valores predeterminados en las columnas, debe \<establecerlo\>mediante metadatos en la clase de proveedor SchemaRowset clase. Establezca `m_bColumnHasDefault = VARIANT_TRUE`.

También tiene la responsabilidad de establecer los indicadores de columna, que se especifican mediante el tipo enumerado DBCOLUMNFLAGS. Los indicadores de columna describen las características de columna.

Por ejemplo, `CUpdateSessionColSchemaRowset` en `UpdatePV` la clase de (en Session.h), la primera columna se configura de esta manera:

```cpp
// Set up column 1
trData[0].m_ulOrdinalPosition = 1;
trData[0].m_bIsNullable = VARIANT_FALSE;
trData[0].m_bColumnHasDefault = VARIANT_TRUE;
trData[0].m_nDataType = DBTYPE_UI4;
trData[0].m_nNumericPrecision = 10;
trData[0].m_ulColumnFlags = DBCOLUMNFLAGS_WRITE |
                            DBCOLUMNFLAGS_ISFIXEDLENGTH;
lstrcpyW(trData[0].m_szColumnDefault, OLESTR("0"));
m_rgRowData.Add(trData[0]);
```

Este código especifica, entre otras cosas, que la columna admite un valor predeterminado de 0, que se puede escribir y que todos los datos de la columna tienen la misma longitud. Si desea que los datos de una columna tengan una longitud variable, no establecería esta marca.

## <a name="see-also"></a>Consulte también

[Creación de un proveedor OLE DB](creating-an-ole-db-provider.md)
