---
title: "Crear un proveedor actualizable | Microsoft Docs"
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
  - "notificaciones, compatibilidad en proveedores"
  - "proveedores OLE DB, crear"
  - "proveedores OLE DB, actualizables"
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear un proveedor actualizable
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 6.0 únicamente admitía proveedores de sólo lectura.  Visual C\+\+ .NET admite proveedores actualizables o que puedan actualizar \(escribir en\) el almacén de datos.  En este tema se describe la forma de crear proveedores actualizables mediante plantillas OLE DB.  
  
 Se supone que está empezando a trabajar con un proveedor en funcionamiento.  Hay que realizar dos pasos para crear un proveedor actualizable.  Primero debe decidir el procedimiento que utilizará el proveedor para realizar cambios en el almacén de datos; en concreto, si los cambios se deben efectuar inmediatamente o se deben aplazar hasta que se ejecute un comando.  En la sección "[Convertir proveedores en proveedores actualizables](#vchowmakingprovidersupdatable)" se describen los cambios y la configuración que se debe realizar en el código del proveedor.  
  
 A continuación, debe asegurarse de que el proveedor contiene toda la funcionalidad necesaria para ofrecer compatibilidad con todo lo que pueda solicitar el consumidor.  Si el consumidor desea actualizar el almacén de datos, el proveedor debe contener código que conserve datos en este almacén.  Por ejemplo, puede utilizar la biblioteca en tiempo de ejecución de C o MFC para realizar determinadas operaciones en el origen de datos.  En la sección "[Escribir en el origen de datos](#vchowwritingtothedatasource)", se describe la forma de escribir en el origen de datos, procesar valores **NULL** y los valores predeterminados, así como la forma de establecer marcadores de columna.  
  
> [!NOTE]
>  UpdatePV es un ejemplo de proveedor actualizable.  UpdatePV es igual que MyProv, pero ofrece compatibilidad con la actualización.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Convertir proveedores en proveedores actualizables  
 La clave para convertir un proveedor en actualizable es decidir qué operaciones desea que realice el proveedor en el almacén de datos y cómo debe realizarlas.  Específicamente, la principal cuestión es si las actualizaciones del almacén de datos deben realizarse inmediatamente o deben aplazarse \(procesarse en lotes\) hasta que se ejecute un comando de actualización.  
  
 Primero debe decidir si se debe heredar de `IRowsetChangeImpl` o de `IRowsetUpdateImpl` en la clase del conjunto de filas.  En función de la interfaz que elija implementar, la funcionalidad de los tres métodos, `SetData`, **InsertRows** y `DeleteRows`, se verá afectada.  
  
-   Si se hereda de [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), cuando se llame a estos tres métodos se modificará inmediatamente el almacén de datos.  
  
-   Si se hereda de [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), los métodos aplazan la aplicación de los cambios en el almacén de datos hasta que se llame a **Update**, `GetOriginalData` o **Undo**.  Si la actualización implica varios cambios, se procesarán todos en un lote \(tenga en cuenta que el procesamiento por lotes puede aumentar de forma considerable la sobrecarga de la memoria\).  
  
 Observe que `IRowsetUpdateImpl` deriva de `IRowsetChangeImpl`.  Por tanto, `IRowsetUpdateImpl` ofrece la posibilidad de hacer cambios y la posibilidad de procesar por lotes.  
  
#### Para ofrecer la capacidad de actualizar en el proveedor  
  
1.  En la clase de conjunto de filas, herede de `IRowsetChangeImpl` o `IRowsetUpdateImpl`.  Estas clases proporcionan las interfaces apropiadas para cambiar el almacén de datos:  
  
     **Agregar IRowsetChange**  
  
     Agregue `IRowsetChangeImpl` a la cadena de herencia de la forma siguiente:  
  
    ```  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     Agregue también `COM_INTERFACE_ENTRY(IRowsetChange)` a la sección `BEGIN_COM_MAP` de la clase de conjunto de filas.  
  
     **Agregar IRowsetUpdate**  
  
     Agregue `IRowsetUpdate` a la cadena de herencia de la forma siguiente:  
  
    ```  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Debe quitar la línea de `IRowsetChangeImpl` de la cadena de herencia.  Esta excepción a la directiva mencionada previamente debe incluir el código necesario para `IRowsetChangeImpl`.  
  
2.  Agregue las líneas siguientes al mapa COM \(**BEGIN\_COM\_MAP ... END\_COM\_MAP**\):  
  
    |Si implementa|Agregue al mapa COM|  
    |-------------------|-------------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  En su comando, agregue lo siguiente a su mapa de valores de propiedades \(**BEGIN\_PROPSET\_MAP ... END\_PROPSET\_MAP**\):  
  
    |Si implementa|Agregue al mapa del conjunto de propiedades|  
    |-------------------|-------------------------------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  En el mapa del conjunto de propiedades, también debe incluir los siguientes valores de configuración de la manera que se indica a continuación:  
  
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
  
     Encontrará los valores utilizados en estas llamadas a macros si consulta en Atldb.h los identificadores y los valores de propiedad \(si el contenido del archivo Atldb.h no coincide con la información de la documentación en pantalla, Atldb.h tiene prioridad sobre la documentación\).  
  
    > [!NOTE]
    >  Muchos de los valores de configuración **VARIANT\_FALSE** y `VARIANT_TRUE` son necesarios para las plantillas OLE DB; en la especificación de OLE DB se establece que pueden ser de lectura y escritura, pero las plantillas OLE DB sólo pueden admitir un valor.  
  
     **Si implementa IRowsetChangeImpl**  
  
     Si implementa `IRowsetChangeImpl`, debe establecer las siguientes propiedades en el proveedor.  Estas propiedades se utilizan principalmente para solicitar interfaces a través de **ICommandProperties::SetProperties**.  
  
    -   `DBPROP_IRowsetChange`: si se establece su valor, se establece automáticamente **DBPROP\_IRowsetChange**.  
  
    -   `DBPROP_UPDATABILITY`: máscara de bits que especifica los métodos admitidos en `IRowsetChange`: `SetData`, `DeleteRows` o `InsertRow`.  
  
    -   `DBPROP_CHANGEINSERTEDROWS`: el consumidor puede llamar a **IRowsetChange::DeleteRows** o `SetData` para las filas recién insertadas.  
  
    -   `DBPROP_IMMOBILEROWS`: el conjunto de filas no reordenará las filas insertadas o actualizadas.  
  
     **Si implementa IRowsetUpdateImpl**  
  
     Si implementa `IRowsetUpdateImpl`, debe establecer las siguientes propiedades en el proveedor, además de establecer todas las propiedades de `IRowsetChangeImpl` mostradas previamente:  
  
    -   `DBPROP_IRowsetUpdate`.  
  
    -   `DBPROP_OWNINSERT`: debe ser READ\_ONLY y VARIANT\_TRUE.  
  
    -   `DBPROP_OWNUPDATEDELETE`: debe ser READ\_ONLY y VARIANT\_TRUE.  
  
    -   `DBPROP_OTHERINSERT`: debe ser READ\_ONLY y VARIANT\_TRUE.  
  
    -   `DBPROP_OTHERUPDATEDELETE`: debe ser READ\_ONLY y VARIANT\_TRUE.  
  
    -   `DBPROP_REMOVEDELETED`: debe ser READ\_ONLY y VARIANT\_TRUE.  
  
    -   `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Si admite notificaciones, también podría tener algunas propiedades más; consulte la sección en `IRowsetNotifyCP` para obtener esta lista.  
  
     Si desea consultar un ejemplo sobre cómo se establecen estas propiedades, vea el mapa del conjunto de propiedades en **CUpdateCommand** \(incluido en Rowset.h\) de [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f).  
  
##  <a name="vchowwritingtothedatasource"></a> Escribir en el origen de datos  
 Para leer desde el origen de datos, llame a la función **Execute**.  Para escribir en el origen de datos, llame a la función `FlushData`. \(En un sentido general, "flush" significa guardar en disco las modificaciones realizadas en una tabla o un índice.\)  
  
```  
FlushData(HROW, HACCESSOR);  
```  
  
 Los argumentos del identificador de fila \(*HROW*\) y el identificador del descriptor de acceso \(*HACCESSOR*\) permiten especificar la región en la que hay que escribir.  Normalmente, se escribe en un solo campo de datos cada vez.  
  
 El método `FlushData` escribe datos en el formato con el que se almacenaron originalmente.  Si no reemplaza esta función, el proveedor funcionará correctamente, pero los cambios no se guardarán en el almacén de datos.  
  
### Cuándo se deben volcar datos  
 Las plantillas de proveedor llaman a `FlushData` siempre que haya que escribir datos en el almacén de datos; esto suele suceder \(aunque no sucede siempre\) como resultado de llamadas a las siguientes funciones:  
  
-   **IRowsetChange::DeleteRows**  
  
-   **IRowsetChange::SetData**  
  
-   **IRowsetChange::InsertRows** \(si hay datos nuevos para insertar en la fila\)  
  
-   **IRowsetUpdate::Update**  
  
### Cómo funciona  
 El consumidor realiza una llamada que requiere guardar \(como **Update**\) y esta llamada se pasa al proveedor, que siempre hace lo siguiente:  
  
-   Llama a `SetDBStatus` siempre que exista un valor de estado enlazado \(vea el capítulo 6 de la *Referencia del programador de OLE DB*, *Partes de los datos: Estado*\).  
  
-   Comprueba los marcadores de columna.  
  
-   Llama a `IsUpdateAllowed`.  
  
 Estos tres pasos proporcionan seguridad.  Después el proveedor llama a `FlushData`.  
  
### Cómo se implementa FlushData  
 Para implementar `FlushData`, debe tener en cuenta varias cuestiones:  
  
-   Asegúrese de que el almacén de datos puede controlar los cambios.  
  
-   Debe controlar los valores **NULL**.  
  
-   Debe controlar los valores predeterminados.  
  
 Para implementar su propio método `FlushData`, debe hacer lo siguiente:  
  
-   Vaya a la clase de conjunto de filas.  
  
-   Coloque en la clase de conjunto de filas la declaración de:  
  
```  
HRESULT FlushData(HROW, HACCESSOR)  
{  
    // Insert your implementation here and return an HRESULT.  
}  
```  
  
-   Proporcione una implementación de `FlushData`.  
  
 Una buena implementación de `FlushData` sólo almacenará las filas y las columnas que se hayan actualizado.  Puede utilizar los parámetros *HROW* y *HACCESSOR* para determinar la fila y la columna actuales que se van a almacenar para la optimización.  
  
 Normalmente, el mayor desafío será trabajar con su propio almacén de datos nativos.  Si es posible, intente:  
  
-   Escribir en el almacén de datos de la forma más sencilla posible.  
  
-   Controle los valores **NULL** \(esto es opcional, pero aconsejable\).  
  
-   Controle los valores predeterminados \(esto es opcional, pero aconsejable\).  
  
 Para ello, lo mejor es tener los valores reales especificados en el almacén de datos para valores **NULL** y valores predeterminados.  Es mejor si puede extrapolar estos datos.  Si no, se recomienda no permitir valores **NULL** y predeterminados.  
  
 A continuación se muestra un ejemplo de cómo se implementa `FlushData` en la clase `RUpdateRowset` del ejemplo [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f) \(vea el contenido de Rowset.h en el código de ejemplo\):  
  
```  
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
  
### Controlar los cambios  
 Para que el proveedor pueda controlar los cambios, primero se debe asegurar de que el almacén de datos \(por ejemplo, un archivo de texto, un archivo de vídeo, etc.\) tiene las características que permiten realizar cambios en él.  Si no las ofrece, debe crear este código por separado del proyecto del proveedor.  
  
### Controlar datos NULL  
 Existe la posibilidad de que un usuario final envíe datos de tipo **NULL**.  Cuando escriba valores de tipo **NULL** en campos del origen de datos, pueden producirse algunos problemas.  Suponga que tiene una aplicación de recepción de pedidos que acepta valores de ciudad y código postal; podría aceptar uno de los dos valores, o ambos, pero hay que escribir al menos uno de los dos, puesto que, de no ser así, la entrega no sería posible.  Por tanto, tendrá que restringir determinadas combinaciones de valores **NULL** en los campos que tienen sentido para la aplicación.  
  
 El programador del proveedor debe considerar la forma de almacenar estos datos, de leer estos datos desde el almacén de datos y de especificarlo al usuario.  Específicamente, debe considerar la forma de cambiar el estado de los datos del conjunto de filas en el origen de datos \(por ejemplo, DataStatus \= **NULL**\).  Debe decidir qué valor hay que devolver cuando un consumidor tiene acceso a un campo que contiene un valor de tipo **NULL**.  
  
 Examine el código del ejemplo [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f), que ilustra cómo controla un proveedor los datos de tipo **NULL**.  En UpdatePV, el proveedor almacena datos de tipo **NULL** escribiendo la cadena "NULL" en el almacén de datos.  Cuando lee datos de tipo **NULL** del almacén de datos, ve esa cadena y después vacía el búfer, creando una cadena de tipo **NULL**.  También tiene un reemplazo de `IRowsetImpl::GetDBStatus` en el que devuelve **DBSTATUS\_S\_ISNULL** si ese valor de datos está vacío.  
  
### Marcar columnas que aceptan valores NULL  
 Si también implementa conjuntos de filas de esquema \(vea `IDBSchemaRowsetImpl`\), la implementación debe especificar en el conjunto de filas **DBSCHEMA\_COLUMNS** \(normalmente marcado en el proveedor como **C***xxx***SchemaColSchemaRowset**\) que la columna acepta valores de tipo NULL.  
  
 También debe especificar que las columnas que aceptan valores NULL contienen el valor **DBCOLUMNFLAGS\_ISNULLABLE** en la versión de `GetColumnInfo`.  
  
 En la implementación de las plantillas OLE DB, si no puede marcar columnas como columnas que aceptan valores NULL, el proveedor supondrá que deben contener un valor y no permitirá al consumidor que le envíe valores de tipo NULL.  
  
 En el siguiente ejemplo, se muestra cómo se implementa la función **CommonGetColInfo** en **CUpdateCommand** \(vea UpProvRS.cpp\) en UpdatePV.  Tenga en cuenta que las columnas tienen este valor **DBCOLUMNFLAGS\_ISNULLABLE** para las columnas que aceptan valores NULL.  
  
```  
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
  
### Valores predeterminados  
 Como en el caso de los datos **NULL**, el programador debe encargarse de los cambios de valores predeterminados.  
  
 La acción predeterminada de `FlushData` y **Execute** es devolver `S_OK`.  Por tanto, si no reemplaza esta función, parecerá que los cambios se aplican correctamente \(se devuelve `S_OK`\), pero no se transmitirán al almacén de datos.  
  
 En el ejemplo [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f) \(en el archivo Rowset.h\), el método `SetDBStatus` controla valores predeterminados de la manera siguiente:  
  
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
  
### Marcadores de columna  
 Si admite valores predeterminados en las columnas, debe establecerse mediante metadatos en la clase de**\>SchemaRowset***de la clase de proveedor*de **\<**.  Establezca *m\_bColumnHasDefault* \= `VARIANT_TRUE`.  
  
 También debe encargarse de establecer los marcadores de columna, que se especifican con el tipo enumerado **DBCOLUMNFLAGS**.  Los marcadores de columna describen las características de cada columna.  
  
 Por ejemplo, en la clase `CUpdateSessionColSchemaRowset` de [UpdatePV](http://msdn.microsoft.com/es-es/c8bed873-223c-4a7d-af55-f90138c6f38f) \(en el archivo Session.h\), la primera columna se configura de la manera siguiente:  
  
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
  
 Estas líneas de código especifican, entre otras cosas, que la columna admite 0 como valor predeterminado, que es grabable y que todos los datos de la columna tienen la misma longitud.  Si desea que los datos de la columna sean de longitud variable, no debe establecer este marcador.  
  
## Vea también  
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)