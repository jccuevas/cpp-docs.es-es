---
title: Crear un proveedor actualizable
ms.date: 08/16/2018
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
ms.openlocfilehash: d3f8314e7cd57617e35e50a67a4562d4055cb93a
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024745"
---
# <a name="creating-an-updatable-provider"></a>Crear un proveedor actualizable

Visual C++ admite proveedores actualizables o que se puede actualizar (escribir en) el almacén de datos. En este tema se describe cómo crear proveedores actualizables mediante plantillas OLE DB.

En este tema se da por supuesto que empieza con un proveedor viable. Hay dos pasos para crear un proveedor actualizable. Primero debe decidir cómo el proveedor realizará cambios en el almacén de datos; en concreto, si los cambios deben realizarse inmediatamente o aplaza hasta que se emite un comando de actualización. La sección "[convertir proveedores actualizables](#vchowmakingprovidersupdatable)" se describen los cambios y configuración que necesita hacer en el código del proveedor.

A continuación, debe asegurarse de que su proveedor contiene toda la funcionalidad para admitir cualquier cosa que el consumidor puede solicitar del mismo. Si el consumidor desea actualizar el almacén de datos, el proveedor debe contener código que conserva los datos en el almacén de datos. Por ejemplo, podría usar la biblioteca de tiempo de ejecución de C o MFC para realizar esas operaciones en el origen de datos. La sección "[escribir en el origen de datos](#vchowwritingtothedatasource)" se describe cómo escribir en el origen de datos, tratar los valores NULL y el valor predeterminado y establecer marcadores de columna.

> [!NOTE]
> [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) es un ejemplo de un proveedor actualizable. UpdatePV es el mismo como MyProv pero compatibilidad con la actualización.

##  <a name="vchowmakingprovidersupdatable"></a> Hacer que los proveedores actualizables

La clave para crear un proveedor actualizable es comprender las operaciones que desea que el proveedor para realizar en el almacén de datos y cómo desea que el proveedor para llevar a cabo esas operaciones. En concreto, el problema principal es que si están las actualizaciones del almacén de datos que deben realizarse inmediatamente o se aplaza (por lotes) hasta que se emite un comando de actualización.

Primero debe decidir si va a heredar `IRowsetChangeImpl` o `IRowsetUpdateImpl` en la clase de conjunto de filas. Dependiendo de cuál de estos elija implementar, afectará la funcionalidad de los tres métodos: `SetData`, `InsertRows`, y `DeleteRows`.

- Si se hereda de [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), llamar a estos tres métodos inmediatamente los cambios del almacén de datos.

- Si se hereda de [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), los métodos aplazan los cambios realizados en el almacén de datos hasta que llame a `Update`, `GetOriginalData`, o `Undo`. Si la actualización implica varios cambios, que se realizan en modo por lotes (tenga en cuenta que el procesamiento por lotes de cambios puede agregar una sobrecarga de memoria considerable).

Tenga en cuenta que `IRowsetUpdateImpl` deriva `IRowsetChangeImpl`. Por lo tanto, `IRowsetUpdateImpl` ofrece hacer cambios funcionalidad y capacidad de proceso por lotes.

### <a name="to-support-updatability-in-your-provider"></a>Para admitir la posibilidad de actualización en un proveedor

1. En la clase de conjunto de filas, se heredan de `IRowsetChangeImpl` o `IRowsetUpdateImpl`. Estas clases proporcionan interfaces adecuadas para cambiar el almacén de datos:

   **Agregar IRowsetChange**

   Agregar `IRowsetChangeImpl` a la cadena de herencia de esta forma:

    ```cpp
    IRowsetChangeImpl< rowset-name, storage-name >
    ```

   También agregar `COM_INTERFACE_ENTRY(IRowsetChange)` a la `BEGIN_COM_MAP` sección en la clase de conjunto de filas.

   **Agregar IRowsetUpdate**

   Agregar `IRowsetUpdate` a la cadena de herencia de esta forma:

    ```cpp
    IRowsetUpdateImpl< rowset-name, storage>
    ```

   > [!NOTE]
   > Debe quitar la `IRowsetChangeImpl` línea desde la cadena de herencia. Esta excepción a la Directiva mencionada anteriormente debe incluir el código para `IRowsetChangeImpl`.

1. Agregue lo siguiente al mapa COM (`BEGIN_COM_MAP ... END_COM_MAP`):

   |  Si implementa   |           Agregar al mapa COM             |
   |---------------------|--------------------------------------|
   | `IRowsetChangeImpl` | `COM_INTERFACE_ENTRY(IRowsetChange)` |
   | `IRowsetUpdateImpl` | `COM_INTERFACE_ENTRY(IRowsetUpdate)` |

   | Si implementa | Agregar al mapa del conjunto de propiedades |
   |----------------------|-----------------------------|
   | `IRowsetChangeImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)` |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. En el comando, agregue lo siguiente a la asignación de conjunto de propiedades (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):

   |  Si implementa   |                                             Agregar al mapa del conjunto de propiedades                                              |
   |---------------------|------------------------------------------------------------------------------------------------------------------|
   | `IRowsetChangeImpl` |                            `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`                             |
   | `IRowsetUpdateImpl` | `PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)` |

1. En la asignación de conjunto de propiedades, también debe incluir todos los valores siguientes que aparecen a continuación:

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

   Puede encontrar los valores utilizados en estas llamadas a macros mediante una búsqueda en Atldb.h para los identificadores de propiedad y valores (si Atldb.h difiere de la documentación en línea, Atldb.h tiene prioridad sobre la documentación).

   > [!NOTE]
   > Muchos de los `VARIANT_FALSE` y `VARIANT_TRUE` ; indica que la especificación OLE DB pueden ser lectura/escritura, pero las plantillas OLE DB pueden admitir solo un valor de configuración es necesarios para las plantillas OLE DB.

   **Si implementa IRowsetChangeImpl**

   Si implementa `IRowsetChangeImpl`, debe establecer las siguientes propiedades en el proveedor. Estas propiedades se utilizan principalmente para solicitar interfaces a través de `ICommandProperties::SetProperties`.

   - `DBPROP_IRowsetChange`: Establece automáticamente este establece `DBPROP_IRowsetChange`.

   - `DBPROP_UPDATABILITY`: Una máscara de bits que especifica los métodos admitidos en `IRowsetChange`: `SetData`, `DeleteRows`, o `InsertRow`.

   - `DBPROP_CHANGEINSERTEDROWS`: Consumidor puede llamar a `IRowsetChange::DeleteRows` o `SetData` para las filas recién insertadas.

   - `DBPROP_IMMOBILEROWS`: Conjunto de filas no reordenará las filas insertadas o actualizadas.

   **Si implementa IRowsetUpdateImpl**

   Si implementa `IRowsetUpdateImpl`, debe establecer las siguientes propiedades en el proveedor, además a establecer todas las propiedades de `IRowsetChangeImpl` enumeradas anteriormente:

   - `DBPROP_IRowsetUpdate`.

   - `DBPROP_OWNINSERT`: Debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_OWNUPDATEDELETE`: Debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_OTHERINSERT`: Debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_OTHERUPDATEDELETE`: Debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_REMOVEDELETED`: Debe ser READ_ONLY y VARIANT_TRUE.

   - `DBPROP_MAXPENDINGROWS`.

   > [!NOTE]
   > Si se admiten las notificaciones, es posible que también tiene algunas otras propiedades; Consulte la sección sobre `IRowsetNotifyCP` para esta lista.

##  <a name="vchowwritingtothedatasource"></a> Escribir en el origen de datos

Para leer desde el origen de datos, llame a la `Execute` función. Para escribir en el origen de datos, llame a la `FlushData` función. (En sentido general, vaciar significa guardar las modificaciones que realice en una tabla o índice en el disco).

```cpp
FlushData(HROW, HACCESSOR);
```

El identificador de fila (HROW) y los argumentos de identificador (HACCESSOR) del descriptor de acceso le permiten especificar la región de escritura. Normalmente, un único campo de datos se escribe en un momento.

El `FlushData` método escribe datos en el formato en el que se almacenó originalmente. Si no reemplaza esta función, el proveedor funcionará correctamente pero no se descargan los cambios al almacén de datos.

### <a name="when-to-flush"></a>Cuándo se debe vaciar

Las plantillas de proveedor llaman a FlushData siempre que haya datos se escriban en el almacén de datos; Esto normalmente (pero no siempre) se produce como resultado de las llamadas a las funciones siguientes:

- `IRowsetChange::DeleteRows`

- `IRowsetChange::SetData`

- `IRowsetChange::InsertRows` (si hay nuevos datos que se va a insertar en la fila)

- `IRowsetUpdate::Update`

### <a name="how-it-works"></a>Cómo funciona

El consumidor realiza una llamada que requiere una operación de vaciado (como Update) y esta llamada se pasa al proveedor, que siempre hace lo siguiente:

- Las llamadas `SetDBStatus` siempre que tenga un valor de estado enlazado.

- Comprueba los marcadores de columna.

- Llama a `IsUpdateAllowed`.

Estos tres pasos ayudan a proporcionar seguridad. A continuación, el proveedor llame a `FlushData`.

### <a name="how-to-implement-flushdata"></a>Cómo implementar FlushData

Para implementar `FlushData`, deberá tener en cuenta varios problemas:

Asegurarse de que el almacén de datos puede controlar los cambios.

Administrar valores NULL.

### <a name="handling-default-values"></a>Controlar los valores predeterminados.

Para implementar su propia `FlushData` método, deberá:

- Vaya a la clase de conjunto de filas.

- En el conjunto de filas de la clase poner la declaración de:

   ```cpp
   HRESULT FlushData(HROW, HACCESSOR)
   {
      // Insert your implementation here and return an HRESULT.
   }
   ```

- Proporcionar una implementación de `FlushData`.

Una buena implementación de `FlushData` almacena solo las filas y columnas que se actualicen. Puede usar los parámetros HROW y HACCESSOR para determinar la fila actual y la columna que se va a almacenar para la optimización.

Normalmente, el mayor desafío es trabajar con su propio almacén de datos nativos. Si es posible, intente:

- Mantenga el método de escritura en el almacén de datos tan simple como sea posible.

- Controlar valores NULL (opcionales, pero aconsejable).

- Controlar los valores predeterminados (opcionales, pero aconsejable).

Lo mejor es que los valores reales especificados en el almacén de datos para los valores NULL y el valor predeterminado. Es mejor si puede extrapolar estos datos. De lo contrario, se recomienda no permitir valores NULL y el valor predeterminado.

El ejemplo siguiente se muestra cómo `FlushData` se implementa en el `RUpdateRowset` clase en el `UpdatePV` ejemplo (consulte Rowset.h en el código de ejemplo):

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

Para que el proveedor controlar los cambios, primero deberá asegurarse de que el almacén de datos (por ejemplo, un archivo de texto o vídeo) tiene las características que permiten realizar cambios en ella. Si no es así, debe crear ese código del proyecto del proveedor.

### <a name="handling-null-data"></a>Controlar datos NULL

Es posible que un usuario final envíe datos de tipo NULL. Al escribir valores NULL a los campos del origen de datos, puede haber problemas potenciales. Imagine una aplicación de recepción de pedidos que acepta valores de ciudad y código postal; podría aceptar uno o ambos valores, pero no es ninguno, porque en ese caso sería imposible entrega. Por lo tanto, tiene que restringir determinadas combinaciones de valores NULL en campos que tengan sentido para su aplicación.

Como el programador del proveedor, debe tener en cuenta cómo se almacenarán los datos, cómo debe leer los datos del almacén de datos y cómo especificar el usuario. En concreto, debe tener en cuenta cómo cambiar el estado de datos del conjunto de filas del origen de datos (por ejemplo, DataStatus = NULL). Debe decidir qué valor que se devuelve cuando un consumidor tiene acceso a un campo que contiene un valor NULL.

Examine el código en el ejemplo UpdatePV; ilustra cómo un proveedor puede controlar datos NULL. En UpdatePV, el proveedor almacena datos NULL mediante la escritura de la cadena "NULL" en el almacén de datos. Cuando lee datos de tipo NULL del almacén de datos, ve esa cadena y, a continuación, vacía el búfer, creando una cadena NULL. También tiene un reemplazo de `IRowsetImpl::GetDBStatus` donde se devuelve DBSTATUS_S_ISNULL si ese valor de datos está vacío.

### <a name="marking-nullable-columns"></a>Marcar columnas que aceptan valores null

Si también implementa conjuntos de filas de esquema (consulte `IDBSchemaRowsetImpl`), la implementación debe especificar en el conjunto de filas DBSCHEMA_COLUMNS (normalmente marcado en el proveedor por CxxxSchemaColSchemaRowset) que la columna es que acepta valores NULL.

También deberá especificar que todas las columnas que aceptan valores null que contienen el valor DBCOLUMNFLAGS_ISNULLABLE en su versión de la `GetColumnInfo`.

En la implementación de plantillas OLE DB, si no puede marcar las columnas que aceptan valores NULL, el proveedor se supone que debe contener un valor y no permitirá al consumidor que le envíe valores null.

El ejemplo siguiente se muestra cómo el `CommonGetColInfo` función se implementa en CUpdateCommand (vea UpProvRS.cpp) en UpdatePV. Tenga en cuenta que las columnas tienen este valor DBCOLUMNFLAGS_ISNULLABLE para las columnas que aceptan valores NULL.

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

Al igual que con datos nulos, tiene la responsabilidad de tratar con el cambio de los valores predeterminados.

El valor predeterminado de `FlushData` y `Execute` es devolver S_OK. Por lo tanto, si no reemplaza esta función, los cambios que todo parezca correcto (se devuelve S_OK), pero no se transmitirán al almacén de datos.

En el `UpdatePV` ejemplo (en Rowset.h), el `SetDBStatus` método controla los valores predeterminados de la manera siguiente:

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

### <a name="column-flags"></a>Indicadores de columna

Si decide admitir valores predeterminados en las columnas, deberá establecerlo mediante metadatos en el \<clase de proveedor\>SchemaRowset clase. Establezca `m_bColumnHasDefault = VARIANT_TRUE`.

También tiene la responsabilidad para establecer los marcadores de columna, que se especifican con el enumerado DBCOLUMNFLAGS tipo. Los indicadores de columna describen las características de la columna.

Por ejemplo, en el `CUpdateSessionColSchemaRowset` clase `UpdatePV` (en Session.h), la primera columna se configura de esta manera:

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

Este código especifica, entre otras cosas, que la columna admite un valor predeterminado de 0, que permite escritura, y que todos los datos de la columna tienen la misma longitud. Si desea que los datos de una columna para tener una longitud variable, no establecería esta marca.

## <a name="see-also"></a>Vea también

[Crear un proveedor OLE DB](creating-an-ole-db-provider.md)