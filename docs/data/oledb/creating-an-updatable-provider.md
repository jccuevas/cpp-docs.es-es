---
title: Crear un proveedor actualizable
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: 2811cd56bdc87282b9d4395a9a79ba9b333dadee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211398"
---
# <a name="creating-an-updatable-provider"></a>Crear un proveedor actualizable

Visual C++ admite proveedores o proveedores actualizables que pueden actualizar (escribir en) el almacén de datos. En este tema se describe cómo crear proveedores actualizables mediante plantillas OLE DB.

En este tema se supone que está empezando con un proveedor viable. Hay dos pasos para crear un proveedor actualizable. En primer lugar, debe decidir cómo realizará el proveedor los cambios en el almacén de datos. concretamente, si los cambios se realizan inmediatamente o se aplazan hasta que se emite un comando de actualización. En la sección "hacer que los[proveedores se actualicen](#vchowmakingprovidersupdatable)" se describen los cambios y la configuración que debe realizar en el código del proveedor.

A continuación, debe asegurarse de que el proveedor contiene toda la funcionalidad para admitir cualquier elemento que el consumidor pueda solicitar. Si el consumidor quiere actualizar el almacén de datos, el proveedor debe contener código que conserve los datos en el almacén de datos. Por ejemplo, puede usar la biblioteca en tiempo de ejecución de C o MFC para realizar estas operaciones en el origen de datos. En la sección "[escribir en el origen de datos](#vchowwritingtothedatasource)" se describe cómo escribir en el origen de datos, tratar con valores NULL y predeterminados y establecer marcas de columna.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) es un ejemplo de un proveedor actualizable. UpdatePV es igual que MyProv pero con compatibilidad actualizable.

##  <a name="making-providers-updatable"></a><a name="vchowmakingprovidersupdatable"></a>Convertir proveedores en actualizables

La clave para hacer que un proveedor actualizable es comprender qué operaciones desea que realice el proveedor en el almacén de datos y cómo desea que el proveedor lleve a cabo esas operaciones. En concreto, el problema principal es si las actualizaciones en el almacén de datos se realizarán inmediatamente o se aplazarán (por lotes) hasta que se emita un comando de actualización.

En primer lugar, debe decidir si heredar de `IRowsetChangeImpl` o `IRowsetUpdateImpl` en la clase de conjunto de filas. Dependiendo de cuál de ellos decida implementar, se verá afectada la funcionalidad de tres métodos: `SetData`, `InsertRows`y `DeleteRows`.

- Si hereda de [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), al llamar a estos tres métodos, se cambia inmediatamente el almacén de datos.

- Si hereda de [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), los métodos aplazan los cambios en el almacén de datos hasta que se llama a `Update`, `GetOriginalData`o `Undo`. Si la actualización implica varios cambios, se realizan en el modo por lotes (tenga en cuenta que el procesamiento por lotes de los cambios puede Agregar una gran sobrecarga de memoria).

Tenga en cuenta que `IRowsetUpdateImpl` deriva de `IRowsetChangeImpl`. Por lo tanto, `IRowsetUpdateImpl` ofrece funcionalidad de cambio más la capacidad de batch.

### <a name="to-support-updatability-in-your-provider"></a>Para admitir la actualización en el proveedor

1. En la clase de conjunto de filas, herede de `IRowsetChangeImpl` o `IRowsetUpdateImpl`. Estas clases proporcionan las interfaces adecuadas para cambiar el almacén de datos:

   **Agregar IRowsetChange**

   Agregue `IRowsetChangeImpl` a la cadena de herencia con este formato:

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   Agregue también `COM_INTERFACE_ENTRY(IRowsetChange)` a la sección `BEGIN_COM_MAP` de la clase de conjunto de filas.

   **Agregar IRowsetUpdate**

   Agregue `IRowsetUpdate` a la cadena de herencia con este formato:

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > Debe quitar la línea de `IRowsetChangeImpl` de la cadena de herencia. Esta excepción a la directiva mencionada previamente debe incluir el código de `IRowsetChangeImpl`.

1. Agregue lo siguiente al mapa COM (`BEGIN_COM_MAP ... END_COM_MAP`):

   |  Si implementa   |           Agregar a asignación COM             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Si implementa | Agregar a asignación de conjunto de propiedades |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. En el comando, agregue lo siguiente a la asignación del conjunto de propiedades (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):

   |  Si implementa   |                                             Agregar a asignación de conjunto de propiedades                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. En el mapa del conjunto de propiedades, también debe incluir todas las opciones siguientes, tal y como aparecen a continuación:

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

   Puede buscar los valores utilizados en estas llamadas de macro; para ello, busque atldb. h para los identificadores y valores de propiedad (si atldb. h difiere de la documentación en línea, atldb. h reemplaza la documentación).

   > [!NOTE]
   > Muchas de las opciones de `VARIANT_FALSE` y `VARIANT_TRUE` son necesarias para las plantillas de OLE DB; la especificación OLE DB indica que pueden ser de lectura/escritura, pero las plantillas de OLE DB solo pueden admitir un valor.

   **Si implementa IRowsetChangeImpl**

   Si implementa `IRowsetChangeImpl`, debe establecer las siguientes propiedades en el proveedor. Estas propiedades se utilizan principalmente para solicitar interfaces a través de `ICommandProperties::SetProperties`.

   - `DBPROP_IRowsetChange`: establecer esto establece automáticamente `DBPROP_IRowsetChange`.

   - `DBPROP_UPDATABILITY`: una máscara de. que especifica los métodos admitidos en `IRowsetChange`: `SetData`, `DeleteRows`o `InsertRow`.

   - `DBPROP_CHANGEINSERTEDROWS`: el consumidor puede llamar a `IRowsetChange::DeleteRows` o `SetData` para las filas recién insertadas.

   - `DBPROP_IMMOBILEROWS`: el conjunto de filas no volverá a ordenar las filas insertadas o actualizadas.

   **Si implementa IRowsetUpdateImpl**

   Si implementa `IRowsetUpdateImpl`, debe establecer las siguientes propiedades en el proveedor, además de establecer todas las propiedades de `IRowsetChangeImpl` enumeradas anteriormente:

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_OWNUPDATEDELETE`: debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_OTHERINSERT`: debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_OTHERUPDATEDELETE`: debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_REMOVEDELETED`: debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > Si admite notificaciones, también puede tener otras propiedades. Vea la sección sobre `IRowsetNotifyCP` de esta lista.

##  <a name="writing-to-the-data-source"></a><a name="vchowwritingtothedatasource"></a>Escribir en el origen de datos

Para leer desde el origen de datos, llame a la función `Execute`. Para escribir en el origen de datos, llame a la función `FlushData`. (En general, vaciar significa guardar las modificaciones que realice en una tabla o un índice en el disco).

```cpp
FlushData(HROW, HACCESSOR);
```

Los argumentos de identificador de fila (HROW) y identificador de descriptor de acceso (HACCESSOR) permiten especificar la región que se va a escribir. Normalmente, se escribe un único campo de datos a la vez.

El método `FlushData` escribe datos en el formato en el que se almacenó originalmente. Si no invalida esta función, el proveedor funcionará correctamente, pero los cambios no se vaciarán en el almacén de datos.

### <a name="when-to-flush"></a>Cuándo se debe vaciar

Las plantillas de proveedor llaman a FlushData siempre que los datos se deben escribir en el almacén de datos. normalmente (pero no siempre) se produce como resultado de las llamadas a las siguientes funciones:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` (si hay nuevos datos que se van a insertar en la fila)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Cómo funciona

El consumidor realiza una llamada que requiere un vaciado (como Update) y esta llamada se pasa al proveedor, que siempre hace lo siguiente:

- Llama a `SetDBStatus` cada vez que tiene un valor de estado enlazado.

- Comprueba las marcas de columna.

- Llama a `IsUpdateAllowed`.

Estos tres pasos ayudan a proporcionar seguridad. A continuación, el proveedor llama a `FlushData`.

### <a name="how-to-implement-flushdata"></a>Cómo implementar FlushData

Para implementar `FlushData`, debe tener en cuenta varios problemas:

Asegurarse de que el almacén de datos puede controlar los cambios.

Controlar valores NULL.

### <a name="handling-default-values"></a>Control de los valores predeterminados.

Para implementar su propio método de `FlushData`, debe:

- Vaya a la clase de conjunto de filas.

- En la clase de conjunto de filas, coloque la declaración de:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Proporcione una implementación de `FlushData`.

Una buena implementación de `FlushData` solo almacena las filas y las columnas que se actualizan realmente. Puede usar los parámetros HROW y HACCESSOR para determinar la fila y la columna actuales que se almacenan para su optimización.

Normalmente, el mayor desafío es trabajar con su propio almacén de datos nativo. Si es posible, intente:

- Mantenga el método de escritura en el almacén de datos lo más sencillo posible.

- Controlar valores NULL (opcional pero aconsejable).

- Controlar los valores predeterminados (opcional pero aconsejable).

Lo mejor es tener valores reales especificados en el almacén de datos para valores NULL y valores predeterminados. Es mejor si puede extrapolar estos datos. Si no es así, se recomienda no permitir valores NULL y predeterminados.

En el ejemplo siguiente se muestra cómo se implementa `FlushData` en la clase `RUpdateRowset` en el ejemplo `UpdatePV` (vea RowSet. h en el código de ejemplo):

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

### <a name="handling-changes"></a>Control de cambios

Para que el proveedor controle los cambios, primero debe asegurarse de que el almacén de datos (por ejemplo, un archivo de texto o un archivo de vídeo) tiene instalaciones que le permiten realizar cambios en él. Si no es así, debe crear ese código independientemente del proyecto de proveedor.

### <a name="handling-null-data"></a>Administrar datos NULL

Es posible que un usuario final envíe datos NULOs. Cuando se escriben valores NULL en los campos del origen de datos, pueden producirse problemas. Imagine una aplicación de pedido que acepta valores para la ciudad y el código postal. podría aceptar uno o ambos valores, pero no ninguno, porque en ese caso no sería posible la entrega. Por lo tanto, tiene que restringir ciertas combinaciones de valores NULL en los campos que tienen sentido para su aplicación.

Como programador del proveedor, tiene que tener en cuenta cómo almacenará los datos, cómo leerá esos datos del almacén de datos y cómo se especifica para el usuario. En concreto, debe tener en cuenta cómo cambiar el estado de los datos de los conjuntos de filas en el origen de datos (por ejemplo, de estado = NULL). Decida qué valor devolver cuando un consumidor tenga acceso a un campo que contenga un valor NULL.

Examine el código del ejemplo UpdatePV; muestra cómo un proveedor puede controlar datos NULL. En UpdatePV, el proveedor almacena los datos NULL escribiendo la cadena "NULL" en el almacén de datos. Cuando lee datos NULOs del almacén de datos, ve esa cadena y, a continuación, vacía el búfer y crea una cadena nula. También tiene una invalidación de `IRowsetImpl::GetDBStatus` en la que devuelve DBSTATUS_S_ISNULL si ese valor de datos está vacío.

### <a name="marking-nullable-columns"></a>Marcar columnas que aceptan valores NULL

Si también implementa conjuntos de filas de esquema (vea `IDBSchemaRowsetImpl`), la implementación debe especificar en el conjunto de filas DBSCHEMA_COLUMNS (normalmente marcado en el proveedor por CxxxSchemaColSchemaRowset) que la columna admite valores NULL.

También debe especificar que todas las columnas que aceptan valores NULL contengan el valor DBCOLUMNFLAGS_ISNULLABLE de la versión de la `GetColumnInfo`.

En la implementación de las plantillas de OLE DB, si no puede marcar las columnas como que aceptan valores NULL, el proveedor supone que deben contener un valor y no permitirá que el consumidor le envíe valores NULL.

En el ejemplo siguiente se muestra cómo se implementa la función `CommonGetColInfo` en CUpdateCommand (vea UpProvRS. cpp) en UpdatePV. Observe cómo las columnas tienen esta DBCOLUMNFLAGS_ISNULLABLE para las columnas que aceptan valores NULL.

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

Al igual que con los datos NULL, tiene la responsabilidad de tratar de cambiar los valores predeterminados.

El valor predeterminado de `FlushData` y `Execute` es devolver S_OK. Por lo tanto, si no invalida esta función, los cambios se verán como correctos (se devolverá S_OK), pero no se transmitirán al almacén de datos.

En el ejemplo `UpdatePV` (en RowSet. h), el método `SetDBStatus` controla los valores predeterminados de la manera siguiente:

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

### <a name="column-flags"></a>Marcas de columna

Si admite valores predeterminados en las columnas, debe establecerlos mediante metadatos en la clase de proveedor \<\>clase Conjuntodefilasdeesquema. Establezca `m_bColumnHasDefault = VARIANT_TRUE`.

También tiene la responsabilidad de establecer las marcas de columna, que se especifican mediante el tipo enumerado DBCOLUMNFLAGS. Las marcas de columna describen las características de las columnas.

Por ejemplo, en la clase `CUpdateSessionColSchemaRowset` en `UpdatePV` (en session. h), la primera columna se configura de esta manera:

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

Este código especifica, entre otras cosas, que la columna admite un valor predeterminado de 0, que se puede escribir y que todos los datos de la columna tienen la misma longitud. Si desea que los datos de una columna tengan una longitud variable, no debe establecer esta marca.

## <a name="see-also"></a>Consulte también

[Crear un proveedor OLE DB](creating-an-ole-db-provider.md)
