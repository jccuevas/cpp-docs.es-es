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
ms.openlocfilehash: bdfcbea6c345235358384691388afcdbbd2d0a42
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321931"
---
# <a name="cdatarecoveryhandler-class"></a>CDataRecoveryHandler (clase)

El `CDataRecoveryHandler` auto guarda documentos y los restaura si una aplicación se cierra inesperadamente.

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
|[CDataRecoveryHandler::AutosaveAllDocumentInfo](#autosavealldocumentinfo)|Guarda automáticamente cada archivo `CDataRecoveryHandler` registrado con la clase.|
|[CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo)|Guarda automáticamente el documento especificado.|
|[CDataRecoveryHandler::CreateDocumentInfo](#createdocumentinfo)|Agrega un documento a la lista de documentos abiertos.|
|[CDataRecoveryHandler::DeleteAllAutosavedFiles](#deleteallautosavedfiles)|Elimina todos los archivos guardados automáticamente actuales.|
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Elimina el archivo guardado automáticamente especificado.|
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Genera el nombre de un archivo de guardado automático asociado con el nombre de archivo de documento proporcionado.|
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Devuelve el intervalo entre los intentos de guardado automático.|
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Devuelve la ruta de acceso de los archivos guardados automáticamente.|
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Recupera el nombre del `CDocument` documento de un objeto.|
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Recupera el título normal del documento especificado.|
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Crea y devuelve el título del documento recuperado.|
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Recupera el identificador de reinicio único para la aplicación.|
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Indica si `CDataRecoveryHandler` realiza un guardado automático en el bucle inactivo actual.|
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Indica si el administrador de reinicio hizo que la aplicación se cierre.|
|[CDataRecoveryHandler::Initialize](#initialize)|Inicializa el `CDataRecoveryHandler`.|
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Muestra un cuadro de diálogo al `CDataRecoveryHandler` usuario para cada documento que el guardado automáticamente. El cuadro de diálogo determina si el usuario desea restaurar el documento guardado automáticamente.|
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Carga la lista de documentos abiertos desde el registro.|
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Quita el documento suministrado de la lista de documentos abiertos.|
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Abre los documentos abiertos anteriormente.|
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Restaura los documentos guardados automáticamente en función de la entrada del usuario.|
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Guarda la lista actual de documentos abiertos en el registro de Windows.|
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Establece el tiempo entre ciclos de guardado automático en milisegundos.|
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Establece el directorio donde se almacenan los archivos guardados automáticamente.|
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Establece el identificador de reinicio `CDataRecoveryHandler`único para esta instancia del archivo .|
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Establece si `CDataRecoveryHandler` guarda la información del documento abierto en el registro de Windows durante el ciclo de inactividad actual.|
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Establece si la salida anterior de la aplicación fue causada por el administrador de reinicio.|
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Actualiza la información de un documento porque el usuario la guardó.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|m_bRestoringPreviousOpenDocs|Indica si el controlador de recuperación de datos vuelve a abrir documentos abiertos anteriormente.|
|m_bSaveDocumentInfoOnIdle|Indica si el controlador de recuperación de datos guarda automáticamente los documentos en el siguiente bucle de inactividad.|
|m_bShutdownByRestartManager|Indica si el administrador de reinicio hace que la aplicación salga.|
|m_dwRestartManagerSupportFlags|Indicadores que indican qué compatibilidad proporciona el Administrador de reinicio para la aplicación.|
|m_lstAutosavesToDelete|Una lista de archivos guardados automáticamente que no se eliminaron cuando se cerraron los documentos originales. Cuando se cierra la aplicación, el gestor de reinicio vuelve a intentar eliminar los archivos.|
|m_mapDocNameToAutosaveName|Un mapa de los nombres de documento a los nombres de archivo guardados automáticamente.|
|m_mapDocNameToDocumentPtr|Un mapa de los nombres de documento a los punteros [CDocument.](../../mfc/reference/cdocument-class.md)|
|m_mapDocNameToRestoreBool|Un mapa de los nombres de documento a un parámetro booleano que indica si se va a restaurar el documento guardado automáticamente.|
|m_mapDocumentPtrToDocName|Mapa de `CDocument` los punteros a los nombres de documento.|
|m_mapDocumentPtrToDocTitle|Un mapa `CDocument` de los punteros a los títulos del documento. Estos títulos se utilizan para guardar archivos.|
|m_nAutosaveInterval|Tiempo en milisegundos entre guardados automáticos.|
|m_nTimerID|Identificador del temporizador de guardado automático.|
|m_strAutosavePath|La ubicación donde se almacenan los documentos guardados automáticamente.|
|m_strRestartIdentifier|Representación de cadena de un GUID para el Administrador de reinicio.|

## <a name="remarks"></a>Observaciones

El gestor de `CDataRecoveryHandler` reinicio utiliza la clase para realizar un seguimiento de todos los documentos abiertos y para guardarlos automáticamente según sea necesario. Para habilitar el guardado automático, utilice el [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) método. Este método indica `CDataRecoveryHandler` que se realice un guardado automático en el siguiente bucle inactivo. El administrador `SetSaveDocumentInfoOnIdle` de `CDataRecoveryHandler` reinicio llama cuando debe realizar un guardado automático.

Todos los métodos `CDataRecoveryHandler` de la clase son virtuales. Invalide los métodos de esta clase para crear su propio controlador de recuperación de datos personalizado. A menos que cree su propio controlador de recuperación de datos o administrador de reinicio, no cree una instancia de un CDataRecoveryHandler. La [clase CWinApp](../../mfc/reference/cwinapp-class.md) crea un `CDataRecoveryHandler` objeto tal como es necesario.

Para poder utilizar `CDataRecoveryHandler` un objeto, debe llamar a [CDataRecoveryHandler::Initialize](#initialize).

Dado `CDataRecoveryHandler` que la clase está estrechamente `CDataRecoveryHandler` conectada al `m_dwRestartManagerSupportFlags`gestor de reinicio, depende del parámetro global. Este parámetro determina qué permisos tiene el Administrador de reinicio y cómo interactúa con la aplicación. Para incorporar el gestor de reinicio en `m_dwRestartManagerSupportFlags` una aplicación existente, debe asignar el valor adecuado en el constructor de la aplicación principal. Para obtener más información acerca de cómo utilizar el Administrador de reinicio, consulte [Cómo: Agregar compatibilidad con Restart Manager](../../mfc/how-to-add-restart-manager-support.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdatarecovery.h

## <a name="cdatarecoveryhandlerautosavealldocumentinfo"></a><a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo

Guarda automáticamente cada archivo `CDataRecoveryHandler` registrado con la clase.

```
virtual BOOL AutosaveAllDocumentInfo();
```

### <a name="return-value"></a>Valor devuelto

TRUESi `CDataRecoveryHandler` el guardado todos los documentos; FALSE si no se ha guardado ningún documento.

### <a name="remarks"></a>Observaciones

Este método devuelve TRUE si no hay documentos que se deben guardar. También devuelve TRUE sin guardar ningún `CWinApp` `CDocManager` documento si recuperar o para la aplicación genera un error.

Para utilizar este método, debe establecerse `m_dwRestartManagerSupportFlags`AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART o AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL en . Para obtener más información, consulte [Cómo: Agregar compatibilidad con Restart Manager](../../mfc/how-to-add-restart-manager-support.md).

## <a name="cdatarecoveryhandlerautosavedocumentinfo"></a><a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo

Guarda automáticamente el documento especificado.

```
virtual BOOL AutosaveDocumentInfo(
    CDocument* pDocument,
    BOOL bResetModifiedFlag = TRUE);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[en] Un puntero `CDocument` a la para guardar.|
|*bResetModifiedFlag*|[en] TRUE indica que `CDataRecoveryHandler` la considera *pDocument* que se va a modificar; FALSE indica que el marco de trabajo considera *pDocument* para ser sin modificar. Consulte la sección Comentarios para obtener más información sobre el efecto de esta marca.|

### <a name="return-value"></a>Valor devuelto

TRUESi se establecen los indicadores `CDocument` adecuados y *pDocument* es un objeto válido.

### <a name="remarks"></a>Observaciones

Cada `CDocument` objeto tiene una marca que indica si ha cambiado desde el último guardado. Utilice [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) para determinar el estado de esta marca. Si `CDocument` a no ha cambiado `AutosaveDocumentInfo` desde el último guardado, elimina los archivos guardados automáticamente para ese documento. Si un documento ha cambiado desde el último guardado, al cerrarlo se le pedirá al usuario que guarde el documento antes de cerrarlo.

> [!NOTE]
> El uso de *bResetModifiedFlag* para cambiar el estado del documento a no modificado puede hacer que el usuario pierda datos no guardados. Si el marco de trabajo considera un documento sin modificar, cerrarlo no solicita al usuario que guarde.

Este método produce una excepción con la macro `CDocument` [ASSERT](diagnostic-services.md#assert) si *pDocument* no es un objeto válido.

Para utilizar este método, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART o AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL debe establecerse en *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlercdatarecoveryhandler"></a><a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler

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
|*dwRestartManagerSupportFlags*|[en] Indica qué opciones del administrador de reinicio son compatibles.|
|*nAutosaveInterval*|[en] El tiempo entre autoguardados. Este parámetro está en milisegundos.|

### <a name="remarks"></a>Observaciones

El marco de `CDataRecoveryHandler` trabajo MFC crea automáticamente un objeto para la aplicación cuando se usa el Asistente para **nuevo proyecto.** A menos que esté personalizando el comportamiento de recuperación de datos o el Administrador de reinicio, no debe crear un `CDataRecoveryHandler` objeto.

## <a name="cdatarecoveryhandlercreatedocumentinfo"></a><a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo

Agrega un documento a la lista de documentos abiertos.

```
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[en] Un puntero `CDocument`a un archivo . Este método crea la `CDocument`información del documento para esto .|

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada devuelve TRUE.

### <a name="remarks"></a>Observaciones

Este método comprueba si *pDocument* ya está en la lista de documentos antes de agregar el documento. Si *pDocument* ya está en la lista, este método elimina el archivo guardado automáticamente asociado a *pDocument*.

Para utilizar este método, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART o AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL debe establecerse en *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerdeleteallautosavedfiles"></a><a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles

Elimina todos los archivos guardados automáticamente actuales.

```
virtual BOOL DeleteAllAutosavedFiles();
```

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada siempre devuelve TRUE.

## <a name="cdatarecoveryhandlerdeleteautosavedfile"></a><a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile

Elimina el archivo guardado automáticamente especificado.

```
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*strAutosavedFile*|[en] Cadena que contiene el nombre de archivo guardado automáticamente.|

### <a name="return-value"></a>Valor devuelto

La implementación predeterminada siempre devuelve TRUE.

### <a name="remarks"></a>Observaciones

Si este método no puede eliminar el archivo guardado automáticamente, guarda el nombre del archivo en una lista. El destructor `CDataRecoveryHandler` de los intentos de eliminar cada archivo guardado automáticamente especificado en esa lista.

## <a name="cdatarecoveryhandlergenerateautosavefilename"></a><a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName

Genera el nombre de un archivo de guardado automático asociado con el nombre de archivo de documento proporcionado.

```
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;
```

### <a name="parameters"></a>Parámetros

*strDocumentName*<br/>
[en] Cadena que contiene el nombre del documento. `GenerateAutosaveFileName`utiliza este nombre de documento para generar un nombre de archivo de guardado automático correspondiente.

### <a name="return-value"></a>Valor devuelto

El nombre de archivo de guardado automático generado a partir de *strDocumentName*.

### <a name="remarks"></a>Observaciones

Cada nombre de documento tiene una asignación uno a uno con un nombre de archivo de guardado automático.

## <a name="cdatarecoveryhandlergetautosaveinterval"></a><a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval

Devuelve el intervalo entre los intentos de guardado automático.

```
virtual int GetAutosaveInterval() const;
```

### <a name="return-value"></a>Valor devuelto

El número de milisegundos entre los intentos de guardado automático.

## <a name="cdatarecoveryhandlergetautosavepath"></a><a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath

Devuelve la ruta de acceso de los archivos guardados automáticamente.

```
virtual CString GetAutosavePath() const;
```

### <a name="return-value"></a>Valor devuelto

La ubicación donde se almacenan los documentos guardados automáticamente.

## <a name="cdatarecoveryhandlergetdocumentlistname"></a><a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName

Recupera el nombre del `CDocument` documento de un objeto.

```
virtual CString GetDocumentListName(CDocument* pDocument) const;
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[en] Un puntero `CDocument`a un archivo . `GetDocumentListName`recupera el nombre del `CDocument`documento de este archivo .|

### <a name="return-value"></a>Valor devuelto

El nombre del documento de *pDocument*.

### <a name="remarks"></a>Observaciones

Utiliza `CDataRecoveryHandler` el nombre del documento como clave en *m_mapDocNameToAutosaveName*, *m_mapDocNameToDocumentPtr*y *m_mapDocNameToRestoreBool*. Estos parámetros `CDataRecoveryHandler` permiten `CDocument` supervisar los objetos, el nombre del archivo de guardado automático y la configuración de guardado automático.

## <a name="cdatarecoveryhandlergetnormaldocumenttitle"></a><a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle

Recupera el título normal del documento especificado.

```
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[en] Un puntero `CDocument`a un archivo .|

### <a name="return-value"></a>Valor devuelto

El título normal del documento especificado.

### <a name="remarks"></a>Observaciones

El título normal de un documento suele ser el nombre de archivo del documento sin la ruta de acceso. Este es el título del campo **Nombre** de archivo del cuadro de diálogo **Guardar como.**

## <a name="cdatarecoveryhandlergetrecovereddocumenttitle"></a><a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle

Crea y devuelve el título del documento recuperado.

```
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;
```

### <a name="parameters"></a>Parámetros

*strDocumentTitle*<br/>
[en] El título normal del documento.

### <a name="return-value"></a>Valor devuelto

El título del documento recuperado.

### <a name="remarks"></a>Observaciones

De forma predeterminada, el título recuperado de un documento es el título normal con **[recuperado]** anexado a él. El título recuperado se muestra al `CDataRecoveryHandler` usuario cuando el usuario consulta al usuario para restaurar documentos guardados automáticamente.

## <a name="cdatarecoveryhandlergetrestartidentifier"></a><a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier

Recupera el identificador de reinicio único para la aplicación.

```
virtual CString GetRestartIdentifier() const;
```

### <a name="return-value"></a>Valor devuelto

El identificador de reinicio único.

### <a name="remarks"></a>Observaciones

El identificador de reinicio es único para cada ejecución de la aplicación.

La `CDataRecoveryHandler` almacena información en el registro sobre los documentos abiertos actualmente. Cuando el Administrador de reinicio sale de una aplicación y la `CDataRecoveryHandler`reinicia, proporciona el identificador de reinicio al archivo . Utiliza `CDataRecoveryHandler` el identificador de reinicio para recuperar la lista de documentos abiertos anteriormente. Esto permite `CDataRecoveryHandler` que el tratar de encontrar y restaurar archivos guardados automáticamente.

## <a name="cdatarecoveryhandlergetsavedocumentinfoonidle"></a><a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle

Indica si `CDataRecoveryHandler` realiza un guardado automático en el bucle inactivo actual.

```
virtual BOOL GetSaveDocumentInfoOnIdle() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica `CDataRecoveryHandler` los guardados automáticos en el bucle inactivo actual; FALSE indica que no lo hace.

## <a name="cdatarecoveryhandlergetshutdownbyrestartmanager"></a><a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager

Indica si el administrador de reinicio hizo que la aplicación se cierre.

```
virtual BOOL GetShutdownByRestartManager() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el administrador de reinicio hizo que la aplicación se cierre; FALSE indica que no lo hizo.

## <a name="cdatarecoveryhandlerinitialize"></a><a name="initialize"></a>CDataRecoveryHandler::Initialize

Inicializa el `CDataRecoveryHandler`.

```
virtual BOOL Initialize();
```

### <a name="return-value"></a>Valor devuelto

TRUESi la inicialización se realiza correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El proceso de inicialización carga la ruta de acceso para almacenar archivos de guardado automático desde el registro. Si `Initialize` el método no puede encontrar este `Initialize` directorio o `FALSE`si la ruta de acceso es NULL, se produce un error y devuelve .

Utilice [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) para cambiar la ruta de `CDataRecoveryHandler`acceso de guardado automático después de que la aplicación inicialice el archivo .

El `Initialize` método también inicia un temporizador para supervisar cuándo se produce el siguiente guardado automático. Utilice [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) para cambiar el intervalo de `CDataRecoveryHandler`guardado automático después de que la aplicación inicialice el archivo .

## <a name="cdatarecoveryhandlerqueryrestoreautosaveddocuments"></a><a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments

Muestra un cuadro de diálogo al `CDataRecoveryHandler` usuario para cada documento que el guardado automáticamente. El cuadro de diálogo determina si el usuario desea restaurar el documento guardado automáticamente.

```
virtual void QueryRestoreAutosavedDocuments();
```

### <a name="remarks"></a>Observaciones

Si la aplicación es Unicode, este método muestra un [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) al usuario. De lo contrario, el marco de trabajo usa [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) para consultar al usuario.

Después `QueryRestoreAutosavedDocuments` de recopilar todas las respuestas del usuario, almacena la información en la variable miembro *m_mapDocNameToRestoreBool*. Este método no restaura los documentos guardados automáticamente.

## <a name="cdatarecoveryhandlerreadopendocumentlist"></a><a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList

Carga la lista de documentos abiertos desde el registro.

```
virtual BOOL ReadOpenDocumentList();
```

### <a name="return-value"></a>Valor devuelto

TRUE indica `ReadOpenDocumentList` que cargó la información de al menos un documento del registro; FALSE indica que no se ha cargado ninguna información del documento.

### <a name="remarks"></a>Observaciones

Esta función carga la información del documento abierto desde el registro y la almacena en la variable miembro *m_mapDocNameToAutosaveName*.

Después `ReadOpenDocumentList` de cargar todos los datos, elimina la información del documento del registro.

## <a name="cdatarecoveryhandlerremovedocumentinfo"></a><a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo

Quita el documento suministrado de la lista de documentos abiertos.

```
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[en] Un puntero al documento que se va a quitar.|

### <a name="return-value"></a>Valor devuelto

TRUESi *pDocument* se ha quitado de la lista; FALSE si se ha producido un error.

### <a name="remarks"></a>Observaciones

Cuando el usuario cierra un documento, el marco de trabajo utiliza este método para quitarlo de la lista de documentos abiertos.

Si `RemoveDocumentInfo` no puede encontrar *pDocument* en la lista de documentos abiertos, no hace nada y devuelve TRUE.

Para utilizar este método, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES debe establecerse en *m_dwRestartManagerSupportFlags*.

## <a name="cdatarecoveryhandlerreopenpreviousdocuments"></a><a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments

Abre los documentos abiertos anteriormente.

```
virtual BOOL ReopenPreviousDocuments();
```

### <a name="return-value"></a>Valor devuelto

TRUESi se ha abierto al menos un documento; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método abre el guardado más reciente de los documentos abiertos anteriormente. Si un documento no se `ReopenPreviousDocuments` guardó o guardó automáticamente, abre un documento en blanco basado en la plantilla para ese tipo de archivo.

Para utilizar este método, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES debe establecerse en *m_dwRestartManagerSupportFlags*. Si no se establece `ReopenPreviousDocuments` este parámetro, no hace nada y devuelve FALSE.

Si no hay documentos almacenados en `ReopenPreviousDocuments` la lista de documentos abiertos anteriormente, no hace nada y devuelve FALSE.

## <a name="cdatarecoveryhandlerrestoreautosaveddocuments"></a><a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments

Restaura los documentos guardados automáticamente en función de la entrada del usuario.

```
virtual BOOL RestoreAutosavedDocuments();
```

### <a name="return-value"></a>Valor devuelto

TRUESi este método restaura correctamente los documentos.

### <a name="remarks"></a>Observaciones

Este método llama a [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) para determinar qué documentos desea restaurar el usuario. Si un usuario decide no restaurar un `RestoreAutosavedDocuments` documento guardado automáticamente, elimina el archivo de guardado automático. De `RestoreAutosavedDocuments` lo contrario, reemplaza el documento abierto por la versión guardada automáticamente.

Para utilizar este método, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES o `m_dwRestartManagerSupportFlags`AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES debe establecerse en .

## <a name="cdatarecoveryhandlersaveopendocumentlist"></a><a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList

Guarda la lista actual de documentos abiertos en el registro de Windows.

```
virtual BOOL SaveOpenDocumentList();
```

### <a name="return-value"></a>Valor devuelto

TRUESi no hay documentos abiertos que guardar o si se guardaron correctamente. FALSE si hay documentos para guardar en el registro, pero no se guardaron porque se produjo un error.

### <a name="remarks"></a>Observaciones

El administrador `SaveOpenDocumentList` de reinicio llama cuando la aplicación se cierra inesperadamente o cuando se cierra para una actualización. Cuando se reinicia la aplicación, usa [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) para recuperar la lista de documentos abiertos.

Este método guarda solo la lista de documentos abiertos. El método [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) es responsable de guardar los propios documentos.

## <a name="cdatarecoveryhandlersetautosaveinterval"></a><a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval

Establece el tiempo entre ciclos de guardado automático en milisegundos.

```
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```

### <a name="parameters"></a>Parámetros

*nAutosaveInterval*<br/>
[en] El nuevo intervalo de guardado automático en milisegundos.

## <a name="cdatarecoveryhandlersetautosavepath"></a><a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath

Establece el directorio donde se almacenan los archivos guardados automáticamente.

```
virtual void SetAutosavePath(const CString& strAutosavePath);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*strAutosavePath*|[en] La ruta de acceso donde se almacenan los archivos de guardado automático.|

### <a name="remarks"></a>Observaciones

Cambiar el directorio de guardado automático no mueve los archivos guardados automáticamente actualmente.

## <a name="cdatarecoveryhandlersetrestartidentifier"></a><a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier

Establece el identificador de reinicio `CDataRecoveryHandler`único para esta instancia del archivo .

```
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*strRestartIdentifier*|[en] Identificador único para el administrador de reinicio.|

### <a name="remarks"></a>Observaciones

El gestor de reinicio registra información sobre los documentos abiertos en el registro. Esta información se almacena con el identificador de reinicio único como clave. Dado que el identificador de reinicio es único para cada instancia de una aplicación, varias instancias de una aplicación pueden salir inesperadamente y el administrador de reinicio puede recuperar cada una de ellas.

## <a name="cdatarecoveryhandlersetsavedocumentinfoonidle"></a><a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoOnIdle

Establece si `CDataRecoveryHandler` guarda la información del documento abierto en el registro de Windows durante el ciclo de inactividad actual.

```
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*bSaveOnIdle*|[en] TRUE para guardar la información del documento durante el ciclo de inactividad actual; FALSE para no realizar un guardado.|

## <a name="cdatarecoveryhandlersetshutdownbyrestartmanager"></a><a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager

Establece si la salida anterior de la aplicación fue causada por el administrador de reinicio.

```
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*bShutdownByRestartManager*|[en] TRUE para indicar que el administrador de reinicio hizo que la aplicación se cierre; FALSE para indicar que la aplicación se ha salido por otro motivo.|

### <a name="remarks"></a>Observaciones

El marco de trabajo se comporta de forma diferente en función de si la salida anterior fue inesperada o si la inició el administrador de reinicio.

## <a name="cdatarecoveryhandlerupdatedocumentinfo"></a><a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo

Actualiza la información de un documento porque el usuario la guardó.

```
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```

### <a name="parameters"></a>Parámetros

|||
|-|-|
|Parámetro|Descripción|
|*pDocument*|[en] Un puntero al documento guardado.|

### <a name="return-value"></a>Valor devuelto

TRUESi este método eliminó el documento guardado automáticamente y actualizó la información del documento; FALSE si se ha producido un error.

### <a name="remarks"></a>Observaciones

Cuando un usuario guarda un documento, la aplicación quita el archivo guardado automáticamente porque ya no es necesario. `UpdateDocumentInfo`elimina el archivo guardado automáticamente llamando a [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo`A continuación, agrega la información de *pDocument* `RemoveDocumentInfo` a la lista de documentos abiertos actualmente porque elimina esa información, pero el documento guardado sigue abierto.

Para utilizar este método, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES debe establecerse en *m_dwRestartManagerSupportFlags*.

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CObject](../../mfc/reference/cobject-class.md)<br/>
[Procedimiento para agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md)
