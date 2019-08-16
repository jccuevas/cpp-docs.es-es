---
title: CDataRecoveryHandler (clase)
ms.date: 03/27/2019
f1_keywords:
- CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::CDataRecoveryHandler
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveAllDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::AutosaveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::CreateDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAllAutosavedFiles
- AFXDATARECOVERY/CDataRecoveryHandler::DeleteAutosavedFile
- AFXDATARECOVERY/CDataRecoveryHandler::GenerateAutosaveFileName
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::GetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::GetDocumentListName
- AFXDATARECOVERY/CDataRecoveryHandler::GetNormalDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRecoveredDocumentTitle
- AFXDATARECOVERY/CDataRecoveryHandler::GetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::GetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::GetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::Initialize
- AFXDATARECOVERY/CDataRecoveryHandler::QueryRestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::ReadOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::RemoveDocumentInfo
- AFXDATARECOVERY/CDataRecoveryHandler::ReopenPreviousDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::RestoreAutosavedDocuments
- AFXDATARECOVERY/CDataRecoveryHandler::SaveOpenDocumentList
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosaveInterval
- AFXDATARECOVERY/CDataRecoveryHandler::SetAutosavePath
- AFXDATARECOVERY/CDataRecoveryHandler::SetRestartIdentifier
- AFXDATARECOVERY/CDataRecoveryHandler::SetSaveDocumentInfoOnIdle
- AFXDATARECOVERY/CDataRecoveryHandler::SetShutdownByRestartManager
- AFXDATARECOVERY/CDataRecoveryHandler::UpdateDocumentInfo
helpviewer_keywords:
- CDataRecoveryHandler [MFC], CDataRecoveryHandler
- CDataRecoveryHandler [MFC], AutosaveAllDocumentInfo
- CDataRecoveryHandler [MFC], AutosaveDocumentInfo
- CDataRecoveryHandler [MFC], CreateDocumentInfo
- CDataRecoveryHandler [MFC], DeleteAllAutosavedFiles
- CDataRecoveryHandler [MFC], DeleteAutosavedFile
- CDataRecoveryHandler [MFC], GenerateAutosaveFileName
- CDataRecoveryHandler [MFC], GetAutosaveInterval
- CDataRecoveryHandler [MFC], GetAutosavePath
- CDataRecoveryHandler [MFC], GetDocumentListName
- CDataRecoveryHandler [MFC], GetNormalDocumentTitle
- CDataRecoveryHandler [MFC], GetRecoveredDocumentTitle
- CDataRecoveryHandler [MFC], GetRestartIdentifier
- CDataRecoveryHandler [MFC], GetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], GetShutdownByRestartManager
- CDataRecoveryHandler [MFC], Initialize
- CDataRecoveryHandler [MFC], QueryRestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], ReadOpenDocumentList
- CDataRecoveryHandler [MFC], RemoveDocumentInfo
- CDataRecoveryHandler [MFC], ReopenPreviousDocuments
- CDataRecoveryHandler [MFC], RestoreAutosavedDocuments
- CDataRecoveryHandler [MFC], SaveOpenDocumentList
- CDataRecoveryHandler [MFC], SetAutosaveInterval
- CDataRecoveryHandler [MFC], SetAutosavePath
- CDataRecoveryHandler [MFC], SetRestartIdentifier
- CDataRecoveryHandler [MFC], SetSaveDocumentInfoOnIdle
- CDataRecoveryHandler [MFC], SetShutdownByRestartManager
- CDataRecoveryHandler [MFC], UpdateDocumentInfo
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
ms.openlocfilehash: 5c5836a11dbf9e05db5b56e0bc5c062dd1617b2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253587"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler (clase)

El `CDataRecoveryHandler` guarda documentos automáticamente y restaura si una aplicación se cierra inesperadamente.

## <a name="syntax"></a>Sintaxis

```
class CDataRecoveryHandler : public CObject
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|||
|-|-|
|[CDataRecoveryHandler::CDataRecoveryHandler](#cdatarecoveryhandler)|Construye un objeto `CDataRecoveryHandler`.|

### <a name="methods"></a>Métodos

|||
|-|-|
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Guarda cada archivo registrado con el `CDataRecoveryHandler` clase.|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Guarda el documento especificado.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Agrega un documento a la lista de documentos abiertos.|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Elimina todos los archivos de autoguardado actual.|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Elimina el archivo de autoguardado especificado.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Genera el nombre de un archivo de autoguardado asociado con el nombre de archivo de documento proporcionado.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Devuelve el intervalo entre intentos de guardado automático.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Devuelve la ruta de acceso de los archivos guardados automáticamente.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Recupera el nombre del documento desde una `CDocument` objeto.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Recupera el título normal para el documento especificado.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Crea y devuelve el título para el documento recuperado.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Recupera el identificador único de reinicio para la aplicación.|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Indica si el `CDataRecoveryHandler` realiza una acción de Autoguardar en bucle inactivo actual.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Indica si el Administrador de reinicio provocó el cierre de la aplicación.|
|[CDataRecoveryHandler::Initialize](#initialize)|Inicializa el `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Muestra un cuadro de diálogo al usuario por cada documento que el `CDataRecoveryHandler` Autoguardado. El cuadro de diálogo determina si el usuario desea restaurar el autoguardado del documento.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Carga la lista de documentos abiertos en el registro.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Quita el documento proporcionado de la lista de documentos abiertos.|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Abre los documentos abiertos previamente.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Restaura los documentos guardados automáticamente basados en la entrada del usuario.|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Guarda la lista actual de documentos abiertos en el registro de Windows.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Establece el tiempo entre ciclos de autoguardado en milisegundos.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Establece el directorio donde se almacenan los archivos guardados automáticamente.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Establece el identificador único de reinicio para esta instancia de la `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Establece si el `CDataRecoveryHandler` guarda la información del documento abierto en el registro de Windows durante el ciclo actual de inactividad.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Establece si la salida anterior de la aplicación fue causada por el Administrador de reinicio.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Actualiza la información de un documento porque el usuario lo guardó.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|m_bRestoringPreviousOpenDocs|Indica si el controlador de recuperación de datos vuelve a abrir documentos abiertos previamente.|
|m_bSaveDocumentInfoOnIdle|Indica si se documenta en el siguiente bucle inactivo guarde automáticamente el controlador de recuperación de datos.|
|m_bShutdownByRestartManager|Indica si el Administrador de reinicio hace que la aplicación salir.|
|m_dwRestartManagerSupportFlags|Proporciona marcas que indican lo que admite el Administrador de reinicio de la aplicación.|
|m_lstAutosavesToDelete|Una lista de archivos de autoguardado que no se elimina cuando se cierran los documentos originales. Cuando se cierra la aplicación, los reintentos del Administrador de reinicio eliminando los archivos.|
|m_mapDocNameToAutosaveName|Un mapa de los nombres de documento para los nombres de archivo de autoguardado.|
|m_mapDocNameToDocumentPtr|Un mapa de los nombres de documento para el [CDocument](../../mfc/reference/cdocument-class.md) punteros.|
|m_mapDocNameToRestoreBool|Un mapa de los nombres de documento a un parámetro booleano que indica si se debe restaurar el autoguardado del documento.|
|m_mapDocumentPtrToDocName|Un mapa de la `CDocument` punteros a los nombres de documento.|
|m_mapDocumentPtrToDocTitle|Un mapa de la `CDocument` punteros a los títulos de documento. Los siguientes ejemplares se utilizan para guardar archivos.|
|m_nAutosaveInterval|Tiempo en milisegundos entre guarde automáticamente.|
|m_nTimerID|El identificador del temporizador de guardado automático.|
|m_strAutosavePath|La ubicación donde se almacenan los documentos guardados automáticamente.|
|m_strRestartIdentifier|La representación de cadena de un GUID para el Administrador de reinicio.|

## <a name="remarks"></a>Comentarios

El Administrador de reinicio se usa el `CDataRecoveryHandler` clase para mantener un seguimiento de todos los documentos abiertos y para Autoguardar ellos según sea necesario. Para habilitar el guardado automático, use el [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) método. Este método se dirige el `CDataRecoveryHandler` para realizar una acción de Autoguardar en el siguiente bucle inactivo. Las llamadas del Administrador de reinicio `SetSaveDocumentInfoOnIdle` cuando el `CDataRecoveryHandler` debe llevar a cabo una acción de Autoguardar.

Todos los métodos de la `CDataRecoveryHandler` clase son virtuales. Invalide los métodos en esta clase para crear su propio controlador de recuperación de datos personalizados. A menos que cree su propio controlador de recuperación de datos o administrador de reinicio, no cree instancias de un CDataRecoveryHandler. El [CWinApp (clase)](../../mfc/reference/cwinapp-class.md) crea un `CDataRecoveryHandler` objeto puesto que es necesaria.

Para poder usar un `CDataRecoveryHandler` objeto, debe llamar a [CDataRecoveryHandler::Initialize](#initialize).

Dado que el `CDataRecoveryHandler` clase estrechamente está conectada al administrador de reinicio, `CDataRecoveryHandler` depende del parámetro global `m_dwRestartManagerSupportFlags`. Este parámetro determina qué permisos tiene el Administrador de reinicio y cómo interactúa con la aplicación. Para incorporar el Administrador de reinicio en una aplicación existente, tendrá que asignar `m_dwRestartManagerSupportFlags` el valor adecuado en el constructor de la aplicación principal. Para obtener más información sobre cómo usar el Administrador de reinicio, vea [Cómo: Agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdatarecovery.h

##  <a name="autosavealldocumentinfo"></a>  CDataRecoveryHandler::AutosaveAllDocumentInfo

Guarda cada archivo registrado con el `CDataRecoveryHandler` clase.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el `CDataRecoveryHandler` guarda todos los documentos; FALSE si no se guardó ningún documento.

### <a name="remarks"></a>Comentarios

Este método devuelve TRUE si no hay ningún documento que se debe guardar. También devuelve TRUE sin guardar los documentos si recupera la `CWinApp` o `CDocManager` para la aplicación genera un error.

Para usar este método, se debe establecer AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART o AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL `m_dwRestartManagerSupportFlags`. Para obtener más información, vea [Cómo: Agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md).

##  <a name="autosavedocumentinfo"></a>  CDataRecoveryHandler::AutosaveDocumentInfo

Guarda el documento especificado.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[in] Un puntero a la `CDocument` para guardar.|
|*bResetModifiedFlag*|[in] TRUE indica que el `CDataRecoveryHandler` considera *pDocument* modificarse; FALSE indica que se considera que el marco de trabajo *pDocument* sea sin modificar. Vea la sección Comentarios para obtener más información sobre el efecto de esta marca.|

### <a name="return-value"></a>Valor devuelto

TRUE si se establecen las marcas apropiadas y *pDocument* es válido `CDocument` objeto.

### <a name="remarks"></a>Comentarios

Cada `CDocument` objeto tiene una marca que indica si ha cambiado desde la última operación de guardado. Use [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) para determinar el estado de esta marca. Si un `CDocument` no ha cambiado desde la última operación de guardado, `AutosaveDocumentInfo` elimina cualquier archivo de autoguardado para ese documento. Si un documento ha cambiado desde la última vez que guardó, cerrarla pide al usuario que guarde el documento antes de cerrarse.

> [!NOTE]
>  Uso de *bResetModifiedFlag* cambiar el estado del documento a no modificado puede provocar el usuario que se pierdan los datos. Si el marco de trabajo se considera que un documento sin modificar, no solicita al usuario guardar cerrarla.

Este método produce una excepción con el [ASSERT](diagnostic-services.md#assert) macro si *pDocument* no es válido `CDocument` objeto.

Para usar este método, se debe establecer AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART o AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL *m_dwRestartManagerSupportFlags*.

##  <a name="cdatarecoveryhandler"></a>  CDataRecoveryHandler::CDataRecoveryHandler

Construye un objeto `CDataRecoveryHandler`.

```
CDataRecoveryHandler(
    DWORD dwRestartManagerSupportFlags,
    int nAutosaveInterval);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*dwRestartManagerSupportFlags*|[in] Indica qué opciones del Administrador de reinicio se admiten.|
|*nAutosaveInterval*|[in] El tiempo entre guarde automáticamente. Este parámetro está en milisegundos.|

### <a name="remarks"></a>Comentarios

El marco de trabajo MFC crea automáticamente un `CDataRecoveryHandler` objeto para la aplicación cuando se usa el **nuevo proyecto** asistente. A menos que se va a personalizar el comportamiento de la recuperación de datos o el Administrador de reinicio, no debería crear un `CDataRecoveryHandler` objeto.

##  <a name="createdocumentinfo"></a>  CDataRecoveryHandler::CreateDocumentInfo

Agrega un documento a la lista de documentos abiertos.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[in] Un puntero a un `CDocument`. Este método crea la información del documento para este `CDocument`.|

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve TRUE.

### <a name="remarks"></a>Comentarios

Este método comprueba si *pDocument* ya está en la lista de documentos antes de agregar el documento. Si *pDocument* ya está en la lista, este método elimina el archivo de autoguardado asociado *pDocument*.

Para usar este método, se debe establecer AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART o AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL *m_dwRestartManagerSupportFlags*.

##  <a name="deleteallautosavedfiles"></a>  CDataRecoveryHandler::DeleteAllAutosavedFiles

Elimina todos los archivos de autoguardado actual.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada siempre devuelve TRUE.

##  <a name="deleteautosavedfile"></a>  CDataRecoveryHandler::DeleteAutosavedFile

Elimina el archivo de autoguardado especificado.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*strAutosavedFile*|[in] Una cadena que contiene el nombre de archivo de autoguardado.|

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Comentarios

Si este método no puede eliminar el archivo de autoguardado, guarda el nombre del archivo en una lista. El destructor para la `CDataRecoveryHandler` intenta eliminar cada archivo de autoguardado especificado en esa lista.

##  <a name="generateautosavefilename"></a>  CDataRecoveryHandler::GenerateAutosaveFileName

Genera el nombre de un archivo de autoguardado asociado con el nombre de archivo de documento proporcionado.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Parámetros

*strDocumentName*<br/>
[in] Una cadena que contiene el nombre del documento. `GenerateAutosaveFileName` usa este nombre de documento para generar un nombre de archivo de autoguardado correspondiente.

### <a name="return-value"></a>Valor devuelto

El nombre de archivo de autoguardado generado a partir de *strDocumentName*.

### <a name="remarks"></a>Comentarios

Cada nombre de documento tiene una asignación uno a uno con un nombre de archivo de autoguardado.

##  <a name="getautosaveinterval"></a>  CDataRecoveryHandler::GetAutosaveInterval

Devuelve el intervalo entre intentos de guardado automático.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Valor devuelto

El número de milisegundos entre Autoguardado intenta.

##  <a name="getautosavepath"></a>  CDataRecoveryHandler::GetAutosavePath

Devuelve la ruta de acceso de los archivos guardados automáticamente.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Valor devuelto

La ubicación donde se almacenan los documentos guardados automáticamente.

##  <a name="getdocumentlistname"></a>  CDataRecoveryHandler::GetDocumentListName

Recupera el nombre del documento desde una `CDocument` objeto.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[in] Un puntero a un `CDocument`. `GetDocumentListName` Recupera el nombre del documento desde esta `CDocument`.|

### <a name="return-value"></a>Valor devuelto

El nombre del documento de *pDocument*.

### <a name="remarks"></a>Comentarios

El `CDataRecoveryHandler` utiliza el nombre del documento como la clave en *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*, y *m_mapDocNameToRestoreBool*. Estos parámetros permiten la `CDataRecoveryHandler` para supervisar `CDocument` objetos, el nombre de archivo de autoguardado y la configuración de autoguardado.

##  <a name="getnormaldocumenttitle"></a>  CDataRecoveryHandler::GetNormalDocumentTitle

Recupera el título normal para el documento especificado.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[in] Un puntero a un `CDocument`.|

### <a name="return-value"></a>Valor devuelto

El título normal para el documento especificado.

### <a name="remarks"></a>Comentarios

El título normal de un documento suele ser el nombre de archivo del documento sin la ruta de acceso. Este es el título en el **nombre de archivo** campo de la **Guardar como** cuadro de diálogo.

##  <a name="getrecovereddocumenttitle"></a>  CDataRecoveryHandler::GetRecoveredDocumentTitle

Crea y devuelve el título para el documento recuperado.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Parámetros

*strDocumentTitle*<br/>
[in] El título normal para el documento.

### <a name="return-value"></a>Valor devuelto

El título del documento recuperado.

### <a name="remarks"></a>Comentarios

De forma predeterminada, el título recuperado de un documento es el título normal con **[recuperado]** anexado a él. El título recuperado se muestra al usuario cuando el `CDataRecoveryHandler` pregunta al usuario para restaurar los documentos guardados automáticamente.

##  <a name="getrestartidentifier"></a>  CDataRecoveryHandler::GetRestartIdentifier

Recupera el identificador único de reinicio para la aplicación.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador único de reinicio.

### <a name="remarks"></a>Comentarios

El identificador de reinicio es único para cada ejecución de la aplicación.

El `CDataRecoveryHandler` almacena información en el registro acerca de los documentos abiertos actualmente. Cuando el Administrador de reinicio cierra una aplicación y lo reinicia, proporciona el identificador de reinicio para la `CDataRecoveryHandler`. El `CDataRecoveryHandler` utiliza el identificador de reinicio para recuperar la lista de documentos abiertos previamente. Esto permite la `CDataRecoveryHandler` para intentar buscar y restaurar los archivos guardados automáticamente.

##  <a name="getsavedocumentinfoonidle"></a>  CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

Indica si el `CDataRecoveryHandler` realiza una acción de Autoguardar en bucle inactivo actual.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el `CDataRecoveryHandler` guarda en el bucle inactivo actual; FALSE indica que no lo hace.

##  <a name="getshutdownbyrestartmanager"></a>  CDataRecoveryHandler::GetShutdownByRestartManager

Indica si el Administrador de reinicio provocó el cierre de la aplicación.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el Administrador de reinicio produjo la aplicación salir; FALSE indica que no lo hizo.

##  <a name="initialize"></a>  CDataRecoveryHandler::Initialize

Inicializa el `CDataRecoveryHandler`.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Valor devuelto

TRUE si la inicialización es correcta; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El proceso de inicialización carga la ruta de acceso para almacenar los archivos de autoguardado del registro. Si el `Initialize` método no puede encontrar este directorio o si la ruta de acceso es NULL, `Initialize` devuelve `FALSE`.

Use [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) para cambiar la ruta de acceso de guardado automático después de la aplicación inicializa la `CDataRecoveryHandler`.

El `Initialize` método también inicia un temporizador para supervisar cuándo se produce el autoguardado del siguiente. Use [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) para cambiar el intervalo de guardado automático después de la aplicación inicializa la `CDataRecoveryHandler`.

##  <a name="queryrestoreautosaveddocuments"></a>  CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Muestra un cuadro de diálogo al usuario por cada documento que el `CDataRecoveryHandler` Autoguardado. El cuadro de diálogo determina si el usuario desea restaurar el autoguardado del documento.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Comentarios

Si la aplicación es Unicode, este método muestra un [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) al usuario. En caso contrario, el marco usa [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) para solicitar al usuario.

Después de `QueryRestoreAutosavedDocuments` reúne todas las respuestas del usuario, almacena la información en la variable miembro *m_mapDocNameToRestoreBool*. Este método no restaura los documentos guardados automáticamente.

##  <a name="readopendocumentlist"></a>  CDataRecoveryHandler::ReadOpenDocumentList

Carga la lista de documentos abiertos en el registro.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que `ReadOpenDocumentList` carga la información de al menos un documento desde el registro; FALSE indica que se ha cargado ninguna información del documento.

### <a name="remarks"></a>Comentarios

Esta función se carga la información del documento abierto desde el registro y lo almacena en la variable miembro *m_mapDocNameToAutosaveName*.

Después de `ReadOpenDocumentList` carga todos los datos, elimina la información del documento del registro.

##  <a name="removedocumentinfo"></a>  CDataRecoveryHandler::RemoveDocumentInfo

Quita el documento proporcionado de la lista de documentos abiertos.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[in] Un puntero al documento que se va a quitar.|

### <a name="return-value"></a>Valor devuelto

TRUE si *pDocument* se ha quitado de la lista. FALSE si se produjo un error.

### <a name="remarks"></a>Comentarios

Cuando el usuario cierra un documento, el marco de trabajo usa este método para quitarlo de la lista de documentos abiertos.

Si `RemoveDocumentInfo` no se puede encontrar *pDocument* en la lista de documentos abiertos, no hace nada y devuelve TRUE.

Para usar este método, se debe establecer AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*.

##  <a name="reopenpreviousdocuments"></a>  CDataRecoveryHandler::ReopenPreviousDocuments

Abre los documentos abiertos previamente.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Valor devuelto

TRUE si al menos un documento se abrió; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método abre al guardar más reciente de los documentos abiertos previamente. Si no se ha guardado un documento o Autoguardado, `ReopenPreviousDocuments` abre un documento en blanco basado en la plantilla para ese tipo de archivo.

Para usar este método, se debe establecer AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*. Si no se establece este parámetro, `ReopenPreviousDocuments` no hace nada y devuelve FALSE.

Si no hay ningún documento almacenado en la lista de documentos abiertos previamente, `ReopenPreviousDocuments` no hace nada y devuelve FALSE.

##  <a name="restoreautosaveddocuments"></a>  CDataRecoveryHandler::RestoreAutosavedDocuments

Restaura los documentos guardados automáticamente basados en la entrada del usuario.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Valor devuelto

TRUE si este método restaura correctamente los documentos.

### <a name="remarks"></a>Comentarios

Este método llama a [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) determinar donde documentan el usuario quiere restaurar. Si un usuario decide no restaurar un documento de autoguardado `RestoreAutosavedDocuments` elimina el archivo de autoguardado. En caso contrario, `RestoreAutosavedDocuments` reemplaza el documento abierto con la versión de autoguardado.

Para usar este método, se debe establecer AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES o AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES `m_dwRestartManagerSupportFlags`.

##  <a name="saveopendocumentlist"></a>  CDataRecoveryHandler::SaveOpenDocumentList

Guarda la lista actual de documentos abiertos en el registro de Windows.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Valor devuelto

TRUE si no hay ningún documento abierto para guardar o si se han guardado correctamente. FALSE si hay documentos para guardar en el registro, pero no se guardaron porque se produjo un error.

### <a name="remarks"></a>Comentarios

Las llamadas del Administrador de reinicio `SaveOpenDocumentList` cuando la aplicación se cierra inesperadamente o cuando se cierra para realizar una actualización. Cuando se reinicia la aplicación, utiliza [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) para recuperar la lista de documentos abiertos.

Este método guarda sólo la lista de documentos abiertos. El método [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) es responsable de guardar los documentos en Sí.

##  <a name="setautosaveinterval"></a>  CDataRecoveryHandler::SetAutosaveInterval

Establece el tiempo entre ciclos de autoguardado en milisegundos.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Parámetros

*nAutosaveInterval*<br/>
[in] El nuevo intervalo de guardado automático en milisegundos.

##  <a name="setautosavepath"></a>  CDataRecoveryHandler::SetAutosavePath

Establece el directorio donde se almacenan los archivos guardados automáticamente.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*strAutosavePath*|[in] La ruta de acceso donde se almacenan los archivos de guardado automático.|

### <a name="remarks"></a>Comentarios

Si cambia el directorio Autoguardar no mueve actualmente Autoguardado archivos.

##  <a name="setrestartidentifier"></a>  CDataRecoveryHandler::SetRestartIdentifier

Establece el identificador único de reinicio para esta instancia de la `CDataRecoveryHandler`.

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*strRestartIdentifier*|[in] El identificador único para el Administrador de reinicio.|

### <a name="remarks"></a>Comentarios

El Administrador de reinicio registra información acerca de los documentos abiertos en el registro. Esta información se almacena con el identificador único de reinicio como clave. Dado que el identificador de reinicio es único para cada instancia de una aplicación, varias instancias de una aplicación pueden cerrarse inesperadamente y el Administrador de reinicio puede recuperar cada uno de ellos.

##  <a name="setsavedocumentinfoonidle"></a>  CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

Establece si el `CDataRecoveryHandler` guarda la información del documento abierto en el registro de Windows durante el ciclo actual de inactividad.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*bSaveOnIdle*|[in] TRUE para guardar la información del documento durante el ciclo actual de inactividad; FALSE para no realizar una operación de guardar.|

##  <a name="setshutdownbyrestartmanager"></a>  CDataRecoveryHandler::SetShutdownByRestartManager

Establece si la salida anterior de la aplicación fue causada por el Administrador de reinicio.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*bShutdownByRestartManager*|[in] TRUE para indicar que el Administrador de reinicio ha provocado la aplicación salir; FALSE para indicar que la aplicación se cerró por otro motivo.|

### <a name="remarks"></a>Comentarios

El marco de trabajo se comporta de forma diferente basándose en la salida anterior no se esperaba o si se ha iniciado el Administrador de reinicio.

##  <a name="updatedocumentinfo"></a>  CDataRecoveryHandler::UpdateDocumentInfo

Actualiza la información de un documento porque el usuario lo guardó.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[in] Un puntero al documento guardado.|

### <a name="return-value"></a>Valor devuelto

TRUE si este método elimina el documento de autoguardado y actualiza la información del documento; FALSE si se produjo un error.

### <a name="remarks"></a>Comentarios

Cuando un usuario guarda un documento, la aplicación quita el archivo de autoguardado porque ya no se necesita. `UpdateDocumentInfo` Elimina el archivo de autoguardado mediante una llamada a [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo` a continuación, agrega la información de *pDocument* a la lista de actualmente abierto documenta porque `RemoveDocumentInfo` elimina esa información, pero el guardado documento todavía está abierto.

Para usar este método, se debe establecer AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES *m_dwRestartManagerSupportFlags*.

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CObject (clase)](../../mfc/reference/cobject-class.md)<br/>
[Cómo: Agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md)
