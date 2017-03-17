---
title: Clase CDataRecoveryHandler | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CDataRecoveryHandler class
ms.assetid: 7794802c-e583-4eba-90b9-2fed1a161f9c
caps.latest.revision: 18
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: c2a99e32a88b8cb3f12d0961451025596886abb0
ms.lasthandoff: 02/24/2017

---
# <a name="cdatarecoveryhandler-class"></a>Clase CDataRecoveryHandler
El `CDataRecoveryHandler` guarda los documentos y los restaura si una aplicación se cierra inesperadamente.  
  
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
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Devuelve el intervalo entre intentos de Autoguardar.|  
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Devuelve la ruta de acceso de los archivos guardados automáticamente.|  
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Recupera el nombre del documento de un `CDocument` objeto.|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Recupera el título normal para el documento especificado.|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Crea y devuelve el título para el documento recuperado.|  
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Recupera el identificador único de reinicio de la aplicación.|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Indica si la `CDataRecoveryHandler` realiza una acción de Autoguardar en el bucle inactivo actual.|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Indica si el Administrador de reinicio provocó el cierre de la aplicación.|  
|[CDataRecoveryHandler::Initialize](#initialize)|Inicializa el `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Muestra un cuadro de diálogo al usuario para cada documento que el `CDataRecoveryHandler` Autoguardado. El cuadro de diálogo determina si el usuario desea restaurar los documentos guardados automáticamente.|  
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Carga la lista de documento abierto desde el registro.|  
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Quita el documento proporcionado de la lista de documentos abiertos.|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Abre los documentos abiertos previamente.|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Restaura los documentos guardados automáticamente basados en la entrada del usuario.|  
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Guarda la lista actual de documentos abiertos en el registro de Windows.|  
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Establece el tiempo entre ciclos de autoguardado en milisegundos.|  
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Establece el directorio donde se almacenan los archivos guardados automáticamente.|  
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Establece el identificador único de reinicio para esta instancia de la `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Establece si el `CDataRecoveryHandler` guarda la información de documento abierto en el registro de Windows durante el período de inactividad actual.|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Establece si la salida anterior de la aplicación se debe a que el Administrador de reinicio.|  
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Actualiza la información de un documento porque el usuario guardó.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|m_bRestoringPreviousOpenDocs|Indica si el controlador de recuperación de datos se vuelve a abrir documentos abiertos previamente.|  
|m_bSaveDocumentInfoOnIdle|Indica si la guarda de controlador de recuperación de datos se documenta en el siguiente bucle de inactividad.|  
|m_bShutdownByRestartManager|Indica si el Administrador de reinicio hace que la aplicación se cierre.|  
|m_dwRestartManagerSupportFlags|Proporciona indicadores que indican lo que admite el Administrador de reinicio de la aplicación.|  
|m_lstAutosavesToDelete|Una lista de los archivos guardados automáticamente que no se eliminan cuando se cierran los documentos originales. Cuando se cierra la aplicación, los reintentos de administrador de reinicio al eliminar los archivos.|  
|m_mapDocNameToAutosaveName|Un mapa de los nombres de documento a los nombres de archivo de autoguardado.|  
|m_mapDocNameToDocumentPtr|Un mapa de los nombres de documento para el [CDocument](../../mfc/reference/cdocument-class.md) punteros.|  
|m_mapDocNameToRestoreBool|Un mapa de los nombres de documento a un parámetro Boolean que indica si se deben restaurar los documentos guardados automáticamente.|  
|m_mapDocumentPtrToDocName|Un mapa de la `CDocument` punteros a los nombres del documento.|  
|m_mapDocumentPtrToDocTitle|Un mapa de la `CDocument` punteros a los títulos del documento. Estos títulos se utilizan para guardar archivos.|  
|m_nAutosaveInterval|Tiempo en milisegundos entre guarda.|  
|m_nTimerID|El identificador para el temporizador de Autoguardar.|  
|m_strAutosavePath|La ubicación donde se almacenan los documentos guardados automáticamente.|  
|m_strRestartIdentifier|La representación de cadena de un GUID para el Administrador de reinicio.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de reinicio se utiliza la `CDataRecoveryHandler` clase para mantener un seguimiento de todos los documentos abiertos y Autoguardado ellos según sea necesario. Para habilitar el guardado automático, use la [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) método. Este método indica la `CDataRecoveryHandler` para realizar una acción de Autoguardar en el siguiente bucle de inactividad. Las llamadas del Administrador de reinicio `SetSaveDocumentInfoOnIdle` cuando el `CDataRecoveryHandler` debe llevar a cabo una acción de Autoguardar.  
  
 Todos los métodos de la `CDataRecoveryHandler` clase son virtuales. Reemplace los métodos de esta clase para crear su propio controlador de recuperación de datos personalizados. A menos que cree su propio controlador de recuperación de datos o administrador de reinicio, no cree instancias de un CDataRecoveryHandler. El [clase CWinApp](../../mfc/reference/cwinapp-class.md) crea un `CDataRecoveryHandler` objeto tal y como resulta necesario.  
  
 Para poder usar un `CDataRecoveryHandler` de objeto, se debe llamar a [CDataRecoveryHandler::Initialize](#initialize).  
  
 Dado que la `CDataRecoveryHandler` clase estrechamente está conectada al administrador de reinicio, `CDataRecoveryHandler` depende del parámetro global `m_dwRestartManagerSupportFlags`. Este parámetro determina qué permisos tiene el Administrador de reinicio y cómo interactúa con la aplicación. Para incorporar el Administrador de reinicio a una aplicación existente, tiene que asignar `m_dwRestartManagerSupportFlags` el valor apropiado en el constructor de la aplicación principal. Para obtener más información acerca de cómo usar el Administrador de reinicio, consulte [Cómo: Add Restart Manager Support](../../mfc/how-to-add-restart-manager-support.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdatarecovery.h  
  
##  <a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo  
 Guarda cada archivo registrado con el `CDataRecoveryHandler` clase.  
  
```  
virtual BOOL AutosaveAllDocumentInfo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el `CDataRecoveryHandler` guarda todos los documentos; `FALSE` si no se ha guardado un documento.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve `TRUE` si no hay ningún documento que se debe guardar. También devuelve `TRUE` sin guardar los documentos si recuperando el `CWinApp` o `CDocManager` para la aplicación genera un error.  
  
 Para utilizar este método, ya sea `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` o `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL` debe establecerse `m_dwRestartManagerSupportFlags`. Consulte [m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags) para obtener más información.  
  
##  <a name="autosavedocumentinfo"></a>CDataRecoveryHandler::AutosaveDocumentInfo  
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
|[in] `pDocument`|Un puntero a la `CDocument` para guardar.|  
|[in] `bResetModifiedFlag`|`TRUE`indica que el `CDataRecoveryHandler` considera `pDocument` modificarse; `FALSE` indica que el marco de trabajo considera `pDocument` como sin modificar. Vea la sección Comentarios para obtener más información acerca del efecto de esta marca.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se establecen las marcas apropiadas y `pDocument` es válido `CDocument` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Cada `CDocument` objeto tiene una marca que indica si ha cambiado desde la última. Utilice [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) para determinar el estado de este indicador. Si un `CDocument` no ha cambiado desde la última, `AutosaveDocumentInfo` elimina los archivos guardados automáticamente para ese documento. Si un documento ha cambiado desde la última vez que guardó, cerrarla pide al usuario que guarde el documento antes de cerrarse.  
  
> [!NOTE]
>  Usar `bResetModifiedFlag` para cambiar el estado del documento a unmodified puede hacer el usuario se pierdan los datos. Si el marco de trabajo se considera que un documento sin modificaciones, cerrarla no pide al usuario que guarde.  
  
 Este método produce una excepción con el [ASSERT](http://msdn.microsoft.com/library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) macro si `pDocument` no es válido `CDocument` objeto.  
  
 Para utilizar este método, ya sea `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` o `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` debe establecerse `m_dwRestartManagerSupportFlags`.   
  
##  <a name="cdatarecoveryhandler"></a>CDataRecoveryHandler::CDataRecoveryHandler  
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
|[in] `dwRestartManagerSupportFlags`|Indica que se admiten las opciones del Administrador de reinicio.|  
|[in] `nAutosaveInterval`|El tiempo entre guarda. Este parámetro está en milisegundos.|  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo MFC crea automáticamente un `CDataRecoveryHandler` objeto de la aplicación cuando se utiliza la **nuevo proyecto** asistente. A menos que se va a personalizar el comportamiento de recuperación de datos o el Administrador de reinicio, no debería crear un `CDataRecoveryHandler` objeto.  
  
  
##  <a name="createdocumentinfo"></a>CDataRecoveryHandler::CreateDocumentInfo  
 Agrega un documento a la lista de documentos abiertos.  
  
```  
virtual BOOL CreateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pDocument`|Un puntero a un `CDocument`. Este método crea la información del documento para este `CDocument`.|  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada devuelve `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método comprueba si `pDocument` ya está en la lista de documentos antes de añadir el documento. Si `pDocument` ya está en la lista, este método elimina el archivo de autoguardado asociado `pDocument`.  
  
 Para utilizar este método, ya sea `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` o `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` debe establecerse `m_dwRestartManagerSupportFlags`. 
  
##  <a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles  
 Elimina todos los archivos de autoguardado actual.  
  
```  
virtual BOOL DeleteAllAutosavedFiles();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada siempre devuelve `TRUE`.  
  
##  <a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile  
 Elimina el archivo de autoguardado especificado.  
  
```  
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `strAutosavedFile`|Cadena que contiene el nombre de archivo de autoguardado.|  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada siempre devuelven `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Si este método no puede eliminar el archivo de autoguardado, guarda el nombre del archivo en una lista. El destructor para la `CDataRecoveryHandler` intenta eliminar cada archivo de autoguardado especificado en la lista.  
  
##  <a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName  
 Genera el nombre de un archivo de autoguardado asociado con el nombre de archivo de documento proporcionado.  
  
```  
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strDocumentName`  
 Cadena que contiene el nombre del documento. `GenerateAutosaveFileName`usa este nombre de documento para generar un nombre de archivo de autoguardado correspondiente.  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre de archivo de autoguardado generado a partir de `strDocumentName`.  
  
### <a name="remarks"></a>Comentarios  
 Cada nombre de documento tiene una asignación uno a uno con un nombre de archivo de guardado automático.  
  
##  <a name="getautosaveinterval"></a>CDataRecoveryHandler::GetAutosaveInterval  
 Devuelve el intervalo entre intentos de Autoguardar.  
  
```  
virtual int GetAutosaveInterval() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de milisegundos entre Autoguardado intenta.  
  
##  <a name="getautosavepath"></a>CDataRecoveryHandler::GetAutosavePath  
 Devuelve la ruta de acceso de los archivos guardados automáticamente.  
  
```  
virtual CString GetAutosavePath() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La ubicación donde se almacenan los documentos guardados automáticamente.  
  
##  <a name="getdocumentlistname"></a>CDataRecoveryHandler::GetDocumentListName  
 Recupera el nombre del documento de un `CDocument` objeto.  
  
```  
virtual CString GetDocumentListName(CDocument* pDocument) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pDocument`|Un puntero a un `CDocument`. `GetDocumentListName`Recupera el nombre del documento de este `CDocument`.|  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre del documento de `pDocument`.  
  
### <a name="remarks"></a>Comentarios  
 El `CDataRecoveryHandler` utiliza el nombre del documento como la clave de `m_mapDocNameToAutosaveName`, `m_mapDocNameToDocumentPtr`, y `m_mapDocNameToRestoreBool`. Estos parámetros permiten la `CDataRecoveryHandler` para supervisar `CDocument` objetos, el nombre de archivo de autoguardado y la configuración de autoguardado.  
  
##  <a name="getnormaldocumenttitle"></a>CDataRecoveryHandler::GetNormalDocumentTitle  
 Recupera el título normal para el documento especificado.  
  
```  
virtual CString GetNormalDocumentTitle(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pDocument`|Un puntero a un `CDocument`.|  
  
### <a name="return-value"></a>Valor devuelto  
 El título normal para el documento especificado.  
  
### <a name="remarks"></a>Comentarios  
 El título de un documento normal suele ser el nombre de archivo del documento sin la ruta de acceso. Este es el título en el **nombre de archivo** campo de la **Guardar como** cuadro de diálogo.  
  
##  <a name="getrecovereddocumenttitle"></a>CDataRecoveryHandler::GetRecoveredDocumentTitle  
 Crea y devuelve el título para el documento recuperado.  
  
```  
virtual CString GetRecoveredDocumentTitle(const CString& strDocumentTitle) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strDocumentTitle`  
 El título normal para el documento.  
  
### <a name="return-value"></a>Valor devuelto  
 El título del documento recuperado.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el título recuperado de un documento es el título normal con **[recuperado]** anexado a él. El título recuperado se muestra al usuario cuando el `CDataRecoveryHandler` pregunta al usuario para restaurar los documentos guardados automáticamente.  
  
##  <a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier  
 Recupera el identificador único de reinicio de la aplicación.  
  
```  
virtual CString GetRestartIdentifier() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador único de reinicio.  
  
### <a name="remarks"></a>Comentarios  
 El identificador de reinicio es único para cada ejecución de la aplicación.  
  
 El `CDataRecoveryHandler` almacena información en el registro acerca de los documentos abiertos actualmente. Cuando el Administrador de reinicio sale de una aplicación y lo reinicia, proporciona el identificador de reinicio a la `CDataRecoveryHandler`. El `CDataRecoveryHandler` utiliza el identificador de reinicio para recuperar la lista de documentos abiertos previamente. Esto permite la `CDataRecoveryHandler` para intentar buscar y restaurar los archivos guardados automáticamente.  
  
##  <a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle  
 Indica si la `CDataRecoveryHandler` realiza una acción de Autoguardar en el bucle inactivo actual.  
  
```  
virtual BOOL GetSaveDocumentInfoOnIdle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica el `CDataRecoveryHandler` guarda en el bucle inactivo actual; `FALSE` indica lo contrario.  
  
##  <a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager  
 Indica si el Administrador de reinicio provocó el cierre de la aplicación.  
  
```  
virtual BOOL GetShutdownByRestartManager() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica que el Administrador de reinicio ha provocado que la aplicación se cierre; `FALSE` indica que no lo hizo.  
  
##  <a name="initialize"></a>CDataRecoveryHandler::Initialize  
 Inicializa el `CDataRecoveryHandler`.  
  
```  
virtual BOOL Initialize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la inicialización se realiza correctamente; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El proceso de inicialización carga la ruta de acceso para almacenar archivos de Autoguardar desde el registro. Si el `Initialize` método no puede encontrar este directorio o si la ruta de acceso es `NULL`, `Initialize` devuelve `FALSE`.  
  
 Utilice [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) para cambiar la ruta de acceso de guardado automático después de que la aplicación la `CDataRecoveryHandler`.  
  
 El `Initialize` método también inicia un temporizador para supervisar cuándo se produce el siguiente Autoguardar. Utilice [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) para cambiar el intervalo de autoguardado después de la aplicación inicializa la `CDataRecoveryHandler`.  
  
##  <a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments  
 Muestra un cuadro de diálogo al usuario para cada documento que el `CDataRecoveryHandler` Autoguardado. El cuadro de diálogo determina si el usuario desea restaurar los documentos guardados automáticamente.  
  
```  
virtual void QueryRestoreAutosavedDocuments();
```  
  
### <a name="remarks"></a>Comentarios  
 Si su aplicación es Unicode, este método muestra una [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) al usuario. De lo contrario, se utiliza el marco de trabajo [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) para solicitar al usuario.  
  
 Después de `QueryRestoreAutosavedDocuments` recopila todas las respuestas del usuario, almacena la información en la variable miembro `m_mapDocNameToRestoreBool`. Este método no restaura los documentos guardados automáticamente.  
  
##  <a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList  
 Carga la lista de documento abierto desde el registro.  
  
```  
virtual BOOL ReadOpenDocumentList();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica que `ReadOpenDocumentList` cargado la información de al menos un documento de registro; `FALSE` indica que se ha cargado ninguna información del documento.  
  
### <a name="remarks"></a>Comentarios  
 Esta función carga la información de documento abierto desde el registro y se almacena en la variable miembro `m_mapDocNameToAutosaveName`.  
  
 Después de `ReadOpenDocumentList` carga todos los datos, elimina del registro la información del documento.  
  
##  <a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo  
 Quita el documento proporcionado de la lista de documentos abiertos.  
  
```  
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pDocument`|Un puntero al documento que se va a quitar.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si `pDocument` se ha quitado de la lista. `FALSE` si se produjo un error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario cierra un documento, el marco de trabajo usa este método para quitar de la lista de documentos abiertos.  
  
 Si `RemoveDocumentInfo` no se puede encontrar `pDocument` en la lista de documentos abiertos, no hace nada y se devuelve `TRUE`.  
  
 Para utilizar este método, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` debe establecerse `m_dwRestartManagerSupportFlags`.   
  
##  <a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments  
 Abre los documentos abiertos previamente.  
  
```  
virtual BOOL ReopenPreviousDocuments();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se ha abierto al menos un documento; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método abre el almacenamiento más reciente de los documentos abiertos previamente. Si no se ha guardado un documento o Autoguardado, `ReopenPreviousDocuments` abre un documento en blanco basado en la plantilla para ese tipo de archivo.  
  
 Para utilizar este método, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` debe establecerse `m_dwRestartManagerSupportFlags`. Si no se establece este parámetro, `ReopenPreviousDocuments` no hace nada y devuelve `FALSE`.  
  
 Si no hay ningún documento almacenado en la lista de documentos abiertos previamente `ReopenPreviousDocuments` no hace nada y devuelve `FALSE`.  
  
##  <a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments  
 Restaura los documentos guardados automáticamente basados en la entrada del usuario.  
  
```  
virtual BOOL RestoreAutosavedDocuments();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método restaura correctamente los documentos.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) determinar los documentos que el usuario desea restaurar. Si un usuario decide no restaurar un documento de autoguardado `RestoreAutosavedDocuments` elimina el archivo de guardado automático. De lo contrario, `RestoreAutosavedDocuments` reemplaza el documento abierto con la versión de autoguardado.  
  
 Para utilizar este método, ya sea `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` o `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES` debe establecerse `m_dwRestartManagerSupportFlags`.   
  
##  <a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList  
 Guarda la lista actual de documentos abiertos en el registro de Windows.  
  
```  
virtual BOOL SaveOpenDocumentList();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si no hay ningún documento abierto para guardar o si se han guardado correctamente. `FALSE`Si hay documentos para guardar en el registro, pero no se han guardado porque se produjo un error.  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas del Administrador de reinicio `SaveOpenDocumentList` cuando la aplicación se cierra inesperadamente o cuando sale de una actualización. Cuando se reinicia la aplicación, utiliza [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) para recuperar la lista de documentos abiertos.  
  
 Este método guarda sólo la lista de documentos abiertos. El método [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) es responsable de guardar los documentos en Sí.  
  
##  <a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval  
 Establece el tiempo entre ciclos de autoguardado en milisegundos.  
  
```  
Virtual void SetAutosaveInterval(int nAutosaveInterval);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `nAutosaveInterval`  
 El nuevo intervalo de autoguardado en milisegundos.  
  
##  <a name="setautosavepath"></a>CDataRecoveryHandler::SetAutosavePath  
 Establece el directorio donde se almacenan los archivos guardados automáticamente.  
  
```  
virtual void SetAutosavePath(const CString& strAutosavePath);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `strAutosavePath`|La ruta de acceso donde se almacenan los archivos de Autoguardar.|  
  
### <a name="remarks"></a>Comentarios  
 Cambie el directorio de autoguardado no mueve actualmente guarda automáticamente los archivos.  
  
##  <a name="setrestartidentifier"></a>CDataRecoveryHandler::SetRestartIdentifier  
 Establece el identificador único de reinicio para esta instancia de la `CDataRecoveryHandler`.  
  
```  
virtual void SetRestartIdentifier(const CString& strRestartIdentifier);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `strRestartIdentifier`|El identificador único para el Administrador de reinicio.|  
  
### <a name="remarks"></a>Comentarios  
 El Administrador de reinicio registra información acerca de los documentos abiertos en el registro. Esta información se almacena con el identificador único de reinicio como la clave. Dado que el identificador de reinicio es único para cada instancia de una aplicación, varias instancias de una aplicación pueden cerrarse inesperadamente y el Administrador de reinicio puede recuperar cada uno de ellos.  
  
##  <a name="setsavedocumentinfoonidle"></a>CDataRecoveryHandler::SetSaveDocumentInfoOnIdle  
 Establece si el `CDataRecoveryHandler` guarda la información de documento abierto en el registro de Windows durante el período de inactividad actual.  
  
```  
virtual void SetSaveDocumentInfoOnIdle(BOOL bSaveOnIdle);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `bSaveOnIdle`|`TRUE`Para guardar la información del documento durante el período de inactividad actual; `FALSE to not perform a save`.|  
  
##  <a name="setshutdownbyrestartmanager"></a>CDataRecoveryHandler::SetShutdownByRestartManager  
 Establece si la salida anterior de la aplicación se debe a que el Administrador de reinicio.  
  
```  
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `bShutdownByRestartManager`|`TRUE`para indicar que el Administrador de reinicio ha provocado la aplicación se cierre; `FALSE` para indicar que la aplicación haya finalizado por algún otro motivo.|  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo se comporta de manera diferente basándose en la salida anterior no se esperaba o si se inició desde el Administrador de reinicio.  
  
##  <a name="updatedocumentinfo"></a>CDataRecoveryHandler::UpdateDocumentInfo  
 Actualiza la información de un documento porque el usuario guardó.  
  
```  
virtual BOOL UpdateDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pDocument`|Un puntero al documento guardado.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método elimina el documento de autoguardado y actualiza la información del documento; `FALSE` si se produjo un error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando un usuario guarda un documento, la aplicación quita el archivo de autoguardado porque ya no es necesario. `UpdateDocumentInfo`Elimina el archivo de autoguardado llamando a [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo`a continuación, agrega la información de `pDocument` a la lista de actualmente documentos abiertos porque `RemoveDocumentInfo` elimina esa información, pero el guardado documento aún está abierto.  
  
 Para utilizar este método, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` debe establecerse `m_dwRestartManagerSupportFlags`.   
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Cómo: agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md)


