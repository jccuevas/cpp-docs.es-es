---
title: Crear un proveedor actualizable | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 317ccd043b3a69489f9cbd2737ad7741389863c5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098646"
---
# <a name="creating-an-updatable-provider"></a>Crear un proveedor actualizable
Visual C++ admite proveedores actualizables o que pueden actualizar (escribir en) el almacén de datos. En este tema se describe cómo crear proveedores actualizables mediante plantillas OLE DB.  
  
 En este tema se da por supuesto que comienza con un proveedor en funcionamiento. Hay dos pasos para crear un proveedor actualizable. En primer lugar debe decidir cómo el proveedor hará que los cambios al almacén de datos; en concreto, si cambios se deben realizar inmediatamente o se aplaza hasta que se emite un comando de actualización. La sección "[convertir proveedores actualizables](#vchowmakingprovidersupdatable)" se describen los cambios y configuraciones que se debe hacer en el código del proveedor.  
  
 A continuación, debe asegurarse de que su proveedor contiene toda la funcionalidad para administrar que el consumidor puede solicitar del mismo. Si el consumidor desea actualizar el almacén de datos, el proveedor debe contener código que conserva los datos al almacén de datos. Por ejemplo, podría utilizar la biblioteca en tiempo de ejecución de C o MFC para realizar estas operaciones en el origen de datos. La sección "[escribir en el origen de datos](#vchowwritingtothedatasource)" se describe cómo escribir en el origen de datos, ocuparse de **NULL** valores predeterminados y establecer marcadores de columna.  
  
> [!NOTE]
>  UpdatePV es un ejemplo de un proveedor actualizable. UpdatePV es igual que MyProv pero compatibilidad con la actualización.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Hacer que los proveedores actualizables  
 La clave para que un proveedor actualizable es decidir qué operaciones desea que su proveedor para llevar a cabo en el almacén de datos y cómo desea que el proveedor para llevar a cabo esas operaciones. En concreto, el principal problema indica si las actualizaciones del almacén de datos deben realizarse inmediatamente o diferido (por lotes) hasta que se emite un comando de actualización.  
  
 En primer lugar debe decidir si se debe heredar de `IRowsetChangeImpl` o `IRowsetUpdateImpl` en la clase de conjunto de filas. Dependiendo de cuál de las siguientes decide implementar, la funcionalidad de los tres métodos que se verán afectada: `SetData`, **InsertRows**, y `DeleteRows`.  
  
-   Si se hereda de [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), inmediatamente al llamar a estos tres métodos modificará el almacén de datos.  
  
-   Si se hereda de [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), los métodos aplazan los cambios al almacén de datos hasta que se llama **actualización**, `GetOriginalData`, o **deshacer**. Si la actualización implica varios cambios, se realizan en modo por lotes (tenga en cuenta que el procesamiento por lotes de cambios puede agregar una sobrecarga considerable de memoria).  
  
 Tenga en cuenta que `IRowsetUpdateImpl` deriva de `IRowsetChangeImpl`. Por lo tanto, `IRowsetUpdateImpl` ofrece hacer cambios funcionalidad y capacidad de proceso por lotes.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Para admitir la actualización en un proveedor  
  
1.  En la clase de conjunto de filas, se heredan de `IRowsetChangeImpl` o `IRowsetUpdateImpl`. Estas clases proporcionan las interfaces apropiadas para cambiar el almacén de datos:  
  
     **Agregar IRowsetChange**  
  
     Agregar `IRowsetChangeImpl` a la cadena de herencia de esta forma:  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Agregar `COM_INTERFACE_ENTRY(IRowsetChange)` a la `BEGIN_COM_MAP` sección de la clase de conjunto de filas.  
  
     **Agregar IRowsetUpdate**  
  
     Agregar `IRowsetUpdate` a la cadena de herencia de esta forma:  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Debe quitar la `IRowsetChangeImpl` línea de la cadena de herencia. Esta excepción a la Directiva mencionada previamente debe incluir el código de `IRowsetChangeImpl`.  
  
2.  Agregue lo siguiente al mapa COM (**BEGIN_COM_MAP... END_COM_MAP**):  
  
    |Si implementa|Agregue al mapa COM|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  En el comando, agregue lo siguiente a la asignación de conjunto de propiedades (**BEGIN_PROPSET_MAP... END_PROPSET_MAP**):  
  
    |Si implementa|Agregar al mapa del conjunto de propiedades|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  En la asignación de conjunto de propiedades, también debe incluir todos los valores siguientes que aparecen a continuación:  
  
    ```  
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
  
     Puede encontrar los valores utilizados en estas llamadas a macros si consulta en Atldb.h para los identificadores de propiedad y valores (si Atldb.h difiere de la documentación en línea, Atldb.h tiene prioridad sobre la documentación).  
  
    > [!NOTE]
    >  Muchos de los **VARIANT_FALSE** y `VARIANT_TRUE` configuración es necesarios para las plantillas OLE DB; la especificación OLE DB indica que pueden ser lectura/escritura, pero las plantillas OLE DB sólo pueden admitir un valor.  
  
     **Si implementa IRowsetChangeImpl**  
  
     Si implementa `IRowsetChangeImpl`, debe establecer las siguientes propiedades en el proveedor. Estas propiedades se utilizan principalmente para solicitar interfaces a través de **ICommandProperties:: SetProperties**.  
  
    -   `DBPROP_IRowsetChange`: Esta acción automáticamente establecer establece **DBPROP_IRowsetChange**.  
  
    -   `DBPROP_UPDATABILITY`: Una máscara de bits que especifica los métodos admitidos en `IRowsetChange`: `SetData`, `DeleteRows`, o `InsertRow`.  
  
    -   `DBPROP_CHANGEINSERTEDROWS`: El consumidor puede llamar a **IRowsetChange:: DeleteRows** o `SetData` para las filas recién insertadas.  
  
    -   `DBPROP_IMMOBILEROWS`: El conjunto de filas no reordenará las filas insertadas o actualizadas.  
  
     **Si implementa IRowsetUpdateImpl**  
  
     Si implementa `IRowsetUpdateImpl`, debe establecer las siguientes propiedades en el proveedor, además a establecer todas las propiedades de `IRowsetChangeImpl` enumerados anteriormente:  
  
    -   `DBPROP_IRowsetUpdate`.  
  
    -   `DBPROP_OWNINSERT`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    -   `DBPROP_OWNUPDATEDELETE`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    -   `DBPROP_OTHERINSERT`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    -   `DBPROP_OTHERUPDATEDELETE`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    -   `DBPROP_REMOVEDELETED`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    -   `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Si se admiten las notificaciones, también podría tener algunas otras propiedades también; vea la sección sobre `IRowsetNotifyCP` para esta lista.  
  
     Por ejemplo de cómo se establecen las propiedades, vea la propiedad mapa del conjunto **CUpdateCommand** (en el archivo Rowset.h) en [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f).  
  
##  <a name="vchowwritingtothedatasource"></a> Escribir en el origen de datos  
 Para leer desde el origen de datos, llame a la **Execute** función. Para escribir en el origen de datos, llame a la `FlushData` (función). (En sentido general, "flush" significa guardar las modificaciones que realice en una tabla o índice en el disco.)  
  
```  
FlushData(HROW, HACCESSOR);  
```  
  
 El identificador de fila (*HROW*) e identificador del descriptor de acceso (*HACCESSOR*) argumentos le permiten especificar la región para escribir. Normalmente, se escribe un único campo de datos a la vez.  
  
 El `FlushData` método escribe datos en el formato en el que se almacenó originalmente. Si no reemplaza esta función, el proveedor funcionará correctamente pero no se vaciará cambios al almacén de datos.  
  
### <a name="when-to-flush"></a>Cuándo se debe vaciar  
 La llamada de plantillas de proveedor `FlushData` cada vez que los datos deben escribirse en el almacén de datos; Esto normalmente (aunque no siempre) se produce como resultado de las llamadas a las funciones siguientes:  
  
-   **IRowsetChange:: DeleteRows**  
  
-   **IRowsetChange:: SetData**  
  
-   **IRowsetChange:: InsertRows** (si hay datos nuevos para insertar en la fila)  
  
-   **IRowsetUpdate:: Update**  
  
### <a name="how-it-works"></a>Cómo funciona  
 El consumidor realiza una llamada que requiere una operación de vaciado (como **actualización**) y esta llamada se pasa al proveedor, que siempre hace lo siguiente:  
  
-   Llamadas `SetDBStatus` siempre que tenga un valor de estado enlazado (vea *referencia del programador de OLE DB*, capítulo 6, *partes de datos: estado*).  
  
-   Comprueba los marcadores de columna.  
  
-   Llama a `IsUpdateAllowed`.  
  
 Estos tres pasos ayudan a proporcionar seguridad. A continuación, el proveedor llama `FlushData`.  
  
### <a name="how-to-implement-flushdata"></a>Cómo se implementa FlushData  
 Para implementar `FlushData`, debe tener en cuenta varios problemas:  
  
-   Asegurarse de que el almacén de datos puede controlar los cambios.  
  
-   Control de **NULL** valores.  
  
-   Controlar los valores predeterminados.  
  
 Para implementar su propia `FlushData` método, debe:  
  
-   Vaya a la clase de conjunto de filas.  
  
-   En el conjunto de filas de la clase coloque la declaración de:  
  
```  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    // Insert your implementation here and return an HRESULT.  
}  
```  
  
-   Proporcionar una implementación de `FlushData`.  
  
 Una buena implementación de `FlushData` almacena solo las filas y columnas que realmente se actualizan. Puede usar el *HROW* y *HACCESSOR* parámetros para determinar la fila actual y la columna que se va a almacenar para la optimización.  
  
 Normalmente, el mayor desafío es trabajar con su propio almacén de datos nativos. Si es posible, intente:  
  
-   Mantener el método de escritura en el almacén de datos tan simple como sea posible.  
  
-   Controlar **NULL** valores (opcionales, pero aconsejable).  
  
-   Controlar los valores predeterminados (opcionales, pero aconsejable).  
  
 Lo mejor es tener los valores reales especificados en el almacén de datos para **NULL** y los valores predeterminados. Es mejor si puede extrapolar estos datos. Si no es así, se recomienda no permitir **NULL** y los valores predeterminados.  
  
 El siguiente ejemplo se muestra cómo `FlushData` se implementa en el `RUpdateRowset` clase en el [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ejemplo (consulte Rowset.h en el código de ejemplo):  
  
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
 Para que el proveedor controlar los cambios, primero debe asegurarse de que el almacén de datos (por ejemplo, un archivo de texto o un archivo de vídeo) tiene las características que permiten realizar cambios en él. Si no es así, debe crear ese código desde el proyecto de proveedor.  
  
### <a name="handling-null-data"></a>Controlar datos NULL  
 Es posible que un usuario final enviará **NULL** datos. Al escribir **NULL** valores a los campos del origen de datos, puede haber problemas potenciales. Imagine una aplicación de recepción de pedidos que acepta valores de ciudad y código postal; podría aceptar uno o ambos valores, pero no es ninguno, porque en ese caso sería imposible entrega. Por tanto, debe restringir determinadas combinaciones de **NULL** valores en los campos que tengan sentido para la aplicación.  
  
 Como el programador del proveedor, debe tener en cuenta cómo se almacenarán los datos, cómo debe leer datos desde el almacén de datos y cómo especificar que el usuario. En concreto, debe tener en cuenta cómo cambiar el estado de datos del conjunto de filas del origen de datos (por ejemplo, DataStatus = **NULL**). Debe decidir qué valor para devolver cuando un consumidor tiene acceso a un campo que contiene un **NULL** valor.  
  
 Examine el código en el [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) ejemplo; ilustra cómo puede controlar un proveedor **NULL** datos. En UpdatePV, el proveedor almacena **NULL** datos al escribir la cadena "NULL" en el almacén de datos. Cuando lee **NULL** almacenan los datos de los datos, ve esa cadena y, a continuación, vacía el búfer, creando una **NULL** cadena. También tiene un reemplazo del `IRowsetImpl::GetDBStatus` en que devuelve **DBSTATUS_S_ISNULL** si ese valor de datos está vacío.  
  
### <a name="marking-nullable-columns"></a>Marcar columnas que aceptan valores null  
 Si también implementa conjuntos de filas de esquema (vea `IDBSchemaRowsetImpl`), la implementación debe especificar en el **DBSCHEMA_COLUMNS** conjunto de filas (normalmente marcado en el proveedor, **C***xxx*** SchemaColSchemaRowset**) que la columna es que aceptan valores NULL.  
  
 También debe especificar que todas las columnas que aceptan valores NULL contienen el **DBCOLUMNFLAGS_ISNULLABLE** valor de la versión de la `GetColumnInfo`.  
  
 En la implementación de plantillas OLE DB, si no puede marcar columnas que aceptan valores NULL, el proveedor se da por supuesto que debe contener un valor y no permitirá al consumidor que le envíe valores null.  
  
 El siguiente ejemplo se muestra cómo el **CommonGetColInfo** función se implementa en **CUpdateCommand** (vea UpProvRS.cpp) en UpdatePV. Tenga en cuenta que las columnas tienen este **DBCOLUMNFLAGS_ISNULLABLE** para las columnas que aceptan valores NULL.  
  
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
 Al igual que con **NULL** datos, tiene la responsabilidad de tratar con el cambio de valores predeterminados.  
  
 El valor predeterminado de `FlushData` y **Execute** debe devolver `S_OK`. Por lo tanto, si no reemplaza esta función, los cambios que todo parezca correcto (`S_OK` se devolverá), pero no se transmitirá al almacén de datos.  
  
 En el [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) (en el archivo Rowset.h), el `SetDBStatus` método controla valores predeterminados de la manera siguiente:  
  
```  
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
  
### <a name="column-flags"></a>Marcadores de columna  
 Si decide admitir valores predeterminados en las columnas, deberá establecerlo mediante metadatos en la  **\< ***clase de proveedor***> SchemaRowset** clase. Establecer *m_bColumnHasDefault* = `VARIANT_TRUE`.  
  
 También tiene la responsabilidad de establecer los marcadores de columna, que se especifican utilizando el **DBCOLUMNFLAGS** tipo enumerado. Los marcadores de columna describen las características de la columna.  
  
 Por ejemplo, en la `CUpdateSessionColSchemaRowset` clase [UpdatePV](http://msdn.microsoft.com/en-us/c8bed873-223c-4a7d-af55-f90138c6f38f) (en el archivo Session.h), la primera columna se configura de esta forma:  
  
```  
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
  
 Este código especifica, entre otras cosas, que la columna es compatible con un valor predeterminado de 0, que permite escritura, y que todos los datos de la columna tienen la misma longitud. Si desea que los datos de una columna a tienen longitud variable, no debe establecer este indicador.  
  
## <a name="see-also"></a>Vea también  
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)