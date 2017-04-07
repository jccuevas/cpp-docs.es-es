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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 26e36977a2e18dcaa4a76b201f9543e200f2d276
ms.lasthandoff: 03/31/2017

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
|[CDataRecoveryHandler::DeleteAutosavedFile](#deleteautosavedfile)|Elimina el archivo Autoguardado especificado.|  
|[CDataRecoveryHandler::GenerateAutosaveFileName](#generateautosavefilename)|Genera el nombre de un archivo de autoguardado asociado con el nombre de archivo de documento proporcionado.|  
|[CDataRecoveryHandler::GetAutosaveInterval](#getautosaveinterval)|Devuelve el intervalo entre intentos de Autoguardar.|  
|[CDataRecoveryHandler::GetAutosavePath](#getautosavepath)|Devuelve la ruta de acceso de los archivos guardados automáticamente.|  
|[CDataRecoveryHandler::GetDocumentListName](#getdocumentlistname)|Recupera el nombre del documento de un `CDocument` objeto.|  
|[CDataRecoveryHandler::GetNormalDocumentTitle](#getnormaldocumenttitle)|Recupera el título normal para el documento especificado.|  
|[CDataRecoveryHandler::GetRecoveredDocumentTitle](#getrecovereddocumenttitle)|Crea y devuelve el título para el documento recuperado.|  
|[CDataRecoveryHandler::GetRestartIdentifier](#getrestartidentifier)|Recupera el identificador único de reinicio para la aplicación.|  
|[CDataRecoveryHandler::GetSaveDocumentInfoOnIdle](#getsavedocumentinfoonidle)|Indica si la `CDataRecoveryHandler` realiza una acción de Autoguardar en el bucle inactivo actual.|  
|[CDataRecoveryHandler::GetShutdownByRestartManager](#getshutdownbyrestartmanager)|Indica si el Administrador de reinicio provocó el cierre de la aplicación.|  
|[CDataRecoveryHandler::Initialize](#initialize)|Inicializa el `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments)|Muestra un cuadro de diálogo al usuario para cada documento que la `CDataRecoveryHandler` Autoguardado. El cuadro de diálogo determina si el usuario desea restaurar los documentos guardados automáticamente.|  
|[CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist)|Carga la lista de documento abierto desde el registro.|  
|[CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo)|Quita el documento proporcionado de la lista de documentos abiertos.|  
|[CDataRecoveryHandler::ReopenPreviousDocuments](#reopenpreviousdocuments)|Abre los documentos abiertos previamente.|  
|[CDataRecoveryHandler::RestoreAutosavedDocuments](#restoreautosaveddocuments)|Restaura los documentos de autoguardado basados en proporcionados por el usuario.|  
|[CDataRecoveryHandler::SaveOpenDocumentList](#saveopendocumentlist)|Guarda la lista actual de los documentos abiertos en el registro de Windows.|  
|[CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval)|Establece el tiempo entre los ciclos de autoguardado en milisegundos.|  
|[CDataRecoveryHandler::SetAutosavePath](#setautosavepath)|Establece el directorio donde se almacenan los archivos guardados automáticamente.|  
|[CDataRecoveryHandler::SetRestartIdentifier](#setrestartidentifier)|Establece el identificador único de reinicio para esta instancia de la `CDataRecoveryHandler`.|  
|[CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle)|Establece si el `CDataRecoveryHandler` guarda la información de documento abierto en el registro de Windows durante el período de inactividad actual.|  
|[CDataRecoveryHandler::SetShutdownByRestartManager](#setshutdownbyrestartmanager)|Establece si la salida anterior de la aplicación fue provocada por el Administrador de reinicio.|  
|[CDataRecoveryHandler::UpdateDocumentInfo](#updatedocumentinfo)|Actualiza la información de un documento porque el usuario guardó.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|m_bRestoringPreviousOpenDocs|Indica si el controlador de recuperación de datos se vuelve a abrir documentos abiertos previamente.|  
|m_bSaveDocumentInfoOnIdle|Indica si la guarda de controlador de recuperación de datos se documenta en el siguiente bucle inactivo.|  
|m_bShutdownByRestartManager|Indica si el Administrador de reinicio hace que la aplicación se cierre.|  
|m_dwRestartManagerSupportFlags|Proporciona marcas que indican lo que admite el Administrador de reinicio de la aplicación.|  
|m_lstAutosavesToDelete|Una lista de archivos de autoguardado que no se elimina cuando se cierran los documentos originales. Cuando se cierra la aplicación, los reintentos del Administrador de reinicio eliminar los archivos.|  
|m_mapDocNameToAutosaveName|Un mapa de los nombres de documento para los nombres de archivo de autoguardado.|  
|m_mapDocNameToDocumentPtr|Un mapa de los nombres de documento para el [CDocument](../../mfc/reference/cdocument-class.md) punteros.|  
|m_mapDocNameToRestoreBool|Un mapa de los nombres de documento para un parámetro booleano que indica si es necesario restaurar los documentos guardados automáticamente.|  
|m_mapDocumentPtrToDocName|Un mapa de la `CDocument` punteros a los nombres de documento.|  
|m_mapDocumentPtrToDocTitle|Un mapa de la `CDocument` punteros a los títulos del documento. Estos títulos se utilizan para guardar archivos.|  
|m_nAutosaveInterval|Tiempo en milisegundos entre guarda.|  
|m_nTimerID|El identificador del temporizador Autoguardado.|  
|m_strAutosavePath|La ubicación donde se almacenan los documentos guardados automáticamente.|  
|m_strRestartIdentifier|La representación de cadena de un GUID para el Administrador de reinicio.|  
  
## <a name="remarks"></a>Comentarios  
 El Administrador de reinicio se utiliza la `CDataRecoveryHandler` clase para mantener un seguimiento de todos los documentos abiertos y Autoguardado ellos según sea necesario. Para habilitar Autoguardado, use la [CDataRecoveryHandler::SetSaveDocumentInfoOnIdle](#setsavedocumentinfoonidle) método. Este método indica la `CDataRecoveryHandler` para realizar una acción de Autoguardar en el siguiente bucle inactivo. Las llamadas del Administrador de reinicio `SetSaveDocumentInfoOnIdle` cuando el `CDataRecoveryHandler` debe llevar a cabo una acción de Autoguardar.  
  
 Todos los métodos de la `CDataRecoveryHandler` clase son virtuales. Invalide los métodos de esta clase para crear su propio controlador de recuperación de datos personalizados. A menos que cree su propio controlador de recuperación de datos o reinicie el administrador, no cree instancias de un CDataRecoveryHandler. El [CWinApp (clase)](../../mfc/reference/cwinapp-class.md) crea un `CDataRecoveryHandler` objeto a medida que sea necesario.  
  
 Para poder usar un `CDataRecoveryHandler` objeto, debe llamar a [CDataRecoveryHandler::Initialize](#initialize).  
  
 Dado que la `CDataRecoveryHandler` clase estrechamente está conectada en el Administrador de reinicio, `CDataRecoveryHandler` depende de los parámetros globales `m_dwRestartManagerSupportFlags`. Este parámetro determina qué permisos tiene el Administrador de reinicio y cómo interactúa con la aplicación. Para incorporar el Administrador de reinicio en una aplicación existente, deberá asignar `m_dwRestartManagerSupportFlags` el valor adecuado en el constructor de la aplicación principal. Para obtener más información sobre cómo usar el Administrador de reinicio, vea [Cómo: agregar Restart Manager Support](../../mfc/how-to-add-restart-manager-support.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdatarecovery.h  
  
##  <a name="autosavealldocumentinfo"></a>CDataRecoveryHandler::AutosaveAllDocumentInfo  
 Guarda cada archivo registrado con el `CDataRecoveryHandler` clase.  
  
```  
virtual BOOL AutosaveAllDocumentInfo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el `CDataRecoveryHandler` guarda todos los documentos; `FALSE` si no se ha guardado cualquier documento.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve `TRUE` si no hay ningún documento que deban guardarse. También devuelve `TRUE` sin guardar todos los documentos si recupera la `CWinApp` o `CDocManager` para la aplicación genera un error.  
  
 Para utilizar este método, ya sea `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` o `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL` debe establecerse `m_dwRestartManagerSupportFlags`. Vea [m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags) para obtener más información.  
  
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
|[in] `bResetModifiedFlag`|`TRUE`indica que la `CDataRecoveryHandler` considera `pDocument` modificarse; `FALSE` indica que el marco de trabajo considera `pDocument` como sin modificar. Vea la sección Comentarios para obtener más información sobre el efecto de esta marca.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se establecen las marcas adecuadas y `pDocument` es válido `CDocument` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Cada `CDocument` objeto tiene una marca que indica si ha cambiado desde la última vez que guardó. Use [CDocument::IsModified](../../mfc/reference/cdocument-class.md#ismodified) para determinar el estado de esta marca. Si un `CDocument` no ha cambiado desde la última vez que guardó, `AutosaveDocumentInfo` elimina los archivos de autoguardado para ese documento. Si un documento ha cambiado desde la última vez que guardó, al cerrarla pide al usuario para guardar el documento antes de cerrarse.  
  
> [!NOTE]
>  Usar `bResetModifiedFlag` cambiar el estado del documento a sin modificar puede hacer que el usuario se pierdan los datos. Si el marco de trabajo se considera que un documento sin modificar, cerrarla no solicita al usuario guardar.  
  
 Este método produce una excepción con el [ASSERT](diagnostic-services.md#assert) macro si `pDocument` no es válido `CDocument` objeto.  
  
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
 El marco de trabajo MFC crea automáticamente un `CDataRecoveryHandler` objeto de la aplicación cuando se usa el **nuevo proyecto** asistente. A menos que se va a personalizar el comportamiento de la recuperación de datos o el Administrador de reinicio, no debería crear un `CDataRecoveryHandler` objeto.  
  
  
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
 Este método comprueba si `pDocument` ya está en la lista de documentos antes de añadir el documento. Si `pDocument` ya está en la lista, este método elimina el archivo Autoguardado asociado `pDocument`.  
  
 Para utilizar este método, ya sea `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART` o `AFX_RESTARTMANAGER_AUTOSAVE_AT_INTERVAL` debe establecerse `m_dwRestartManagerSupportFlags`. 
  
##  <a name="deleteallautosavedfiles"></a>CDataRecoveryHandler::DeleteAllAutosavedFiles  
 Elimina todos los archivos de autoguardado actual.  
  
```  
virtual BOOL DeleteAllAutosavedFiles();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada siempre devuelve `TRUE`.  
  
##  <a name="deleteautosavedfile"></a>CDataRecoveryHandler::DeleteAutosavedFile  
 Elimina el archivo Autoguardado especificado.  
  
```  
virtual BOOL DeleteAutosavedFile(const CString& strAutosavedFile);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `strAutosavedFile`|Una cadena que contiene el nombre de archivo de autoguardado.|  
  
### <a name="return-value"></a>Valor devuelto  
 La implementación predeterminada siempre devuelven `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Si este método no puede eliminar el archivo de autoguardado, guarda el nombre del archivo en una lista. El destructor para la `CDataRecoveryHandler` intenta eliminar cada archivo de autoguardado especificado en esa lista.  
  
##  <a name="generateautosavefilename"></a>CDataRecoveryHandler::GenerateAutosaveFileName  
 Genera el nombre de un archivo de autoguardado asociado con el nombre de archivo de documento proporcionado.  
  
```  
virtual CString GenerateAutosaveFileName(const CString& strDocumentName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `strDocumentName`  
 Una cadena que contiene el nombre del documento. `GenerateAutosaveFileName`usa este nombre de documento para generar un nombre de archivo de autoguardado correspondiente.  
  
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
|[in] `pDocument`|Un puntero a un `CDocument`. `GetDocumentListName`Recupera el nombre del documento desde esta `CDocument`.|  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre del documento de `pDocument`.  
  
### <a name="remarks"></a>Comentarios  
 El `CDataRecoveryHandler` utiliza el nombre del documento como la clave de `m_mapDocNameToAutosaveName`, `m_mapDocNameToDocumentPtr`, y `m_mapDocNameToRestoreBool`. Estos parámetros permiten la `CDataRecoveryHandler` para supervisar `CDocument` objetos, el nombre de archivo de guardado automático y la configuración de autoguardado.  
  
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
 De forma predeterminada, el título recuperado de un documento es el título normal con **[recuperado]** anexada al mismo. El título recuperado se muestra al usuario cuando el `CDataRecoveryHandler` pregunta al usuario para restaurar los documentos guardados automáticamente.  
  
##  <a name="getrestartidentifier"></a>CDataRecoveryHandler::GetRestartIdentifier  
 Recupera el identificador único de reinicio para la aplicación.  
  
```  
virtual CString GetRestartIdentifier() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador único de reinicio.  
  
### <a name="remarks"></a>Comentarios  
 El identificador de reinicio es único para cada ejecución de la aplicación.  
  
 El `CDataRecoveryHandler` almacena información en el registro acerca de los documentos abiertos actualmente. Cuando el Administrador de reinicio sale de una aplicación y lo reinicia, proporciona el identificador de reinicio para la `CDataRecoveryHandler`. El `CDataRecoveryHandler` utiliza el identificador de reinicio para recuperar la lista de documentos abiertos previamente. Esto permite la `CDataRecoveryHandler` para intentar encontrar y restaurar los archivos guardados automáticamente.  
  
##  <a name="getsavedocumentinfoonidle"></a>CDataRecoveryHandler::GetSaveDocumentInfoOnIdle  
 Indica si la `CDataRecoveryHandler` realiza una acción de Autoguardar en el bucle inactivo actual.  
  
```  
virtual BOOL GetSaveDocumentInfoOnIdle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica el `CDataRecoveryHandler` guarda en el bucle inactivo actual; `FALSE` indica no lo hace.  
  
##  <a name="getshutdownbyrestartmanager"></a>CDataRecoveryHandler::GetShutdownByRestartManager  
 Indica si el Administrador de reinicio provocó el cierre de la aplicación.  
  
```  
virtual BOOL GetShutdownByRestartManager() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica que el Administrador de reinicio provocó que la aplicación salir; `FALSE` indica no lo hicieron.  
  
##  <a name="initialize"></a>CDataRecoveryHandler::Initialize  
 Inicializa el `CDataRecoveryHandler`.  
  
```  
virtual BOOL Initialize();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si la inicialización se realiza correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 El proceso de inicialización carga la ruta de acceso para almacenar archivos de Autoguardar desde el registro. Si el `Initialize` método no puede encontrar este directorio o si la ruta de acceso es `NULL`, `Initialize` se produce un error y devuelve `FALSE`.  
  
 Use [CDataRecoveryHandler::SetAutosavePath](#setautosavepath) para cambiar la ruta de acceso de guardado automático después de la aplicación inicializa la `CDataRecoveryHandler`.  
  
 El `Initialize` método también inicia un temporizador para supervisar cuándo se produce el siguiente Autoguardado. Use [CDataRecoveryHandler::SetAutosaveInterval](#setautosaveinterval) para cambiar el intervalo de autoguardado después de la aplicación inicializa la `CDataRecoveryHandler`.  
  
##  <a name="queryrestoreautosaveddocuments"></a>CDataRecoveryHandler::QueryRestoreAutosavedDocuments  
 Muestra un cuadro de diálogo al usuario para cada documento que la `CDataRecoveryHandler` Autoguardado. El cuadro de diálogo determina si el usuario desea restaurar los documentos guardados automáticamente.  
  
```  
virtual void QueryRestoreAutosavedDocuments();
```  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación es Unicode, este método muestra un [CTaskDialog](../../mfc/reference/ctaskdialog-class.md) al usuario. En caso contrario, se utiliza el marco de trabajo [AfxMessageBox](../../mfc/reference/cstring-formatting-and-message-box-display.md#afxmessagebox) para preguntar al usuario.  
  
 Después de `QueryRestoreAutosavedDocuments` recopila todas las respuestas del usuario, almacena la información en la variable miembro `m_mapDocNameToRestoreBool`. Este método no restaura los documentos guardados automáticamente.  
  
##  <a name="readopendocumentlist"></a>CDataRecoveryHandler::ReadOpenDocumentList  
 Carga la lista de documento abierto desde el registro.  
  
```  
virtual BOOL ReadOpenDocumentList();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica que `ReadOpenDocumentList` cargado la información de al menos un documento desde el registro; `FALSE` indica ninguna información del documento se ha cargado.  
  
### <a name="remarks"></a>Comentarios  
 Esta función carga la información de documento abierto desde el registro y lo almacena en la variable miembro `m_mapDocNameToAutosaveName`.  
  
 Después de `ReadOpenDocumentList` carga todos los datos, elimina la información del documento desde el registro.  
  
##  <a name="removedocumentinfo"></a>CDataRecoveryHandler::RemoveDocumentInfo  
 Quita el documento proporcionado de la lista de documentos abiertos.  
  
```  
virtual BOOL RemoveDocumentInfo(CDocument* pDocument);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `pDocument`|Un puntero para el documento que se va a quitar.|  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si `pDocument` se ha quitado de la lista; `FALSE` si se produjo un error.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario cierra un documento, el marco de trabajo utiliza este método para quitar de la lista de documentos abiertos.  
  
 Si `RemoveDocumentInfo` no se puede encontrar `pDocument` en la lista de documentos abiertos, no hace nada y se devuelve `TRUE`.  
  
 Para utilizar este método, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` debe establecerse `m_dwRestartManagerSupportFlags`.   
  
##  <a name="reopenpreviousdocuments"></a>CDataRecoveryHandler::ReopenPreviousDocuments  
 Abre los documentos abiertos previamente.  
  
```  
virtual BOOL ReopenPreviousDocuments();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se abrió al menos un documento; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método abre el guardar más reciente de los documentos abiertos previamente. Si no se guarda un documento o Autoguardado, `ReopenPreviousDocuments` abre un documento en blanco basado en la plantilla para ese tipo de archivo.  
  
 Para utilizar este método, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` debe establecerse `m_dwRestartManagerSupportFlags`. Si no se establece este parámetro, `ReopenPreviousDocuments` no hace nada y devuelve `FALSE`.  
  
 Si no hay ningún documento almacenado en la lista de documentos abiertos anteriormente `ReopenPreviousDocuments` no hace nada y devuelve `FALSE`.  
  
##  <a name="restoreautosaveddocuments"></a>CDataRecoveryHandler::RestoreAutosavedDocuments  
 Restaura los documentos de autoguardado basados en proporcionados por el usuario.  
  
```  
virtual BOOL RestoreAutosavedDocuments();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método restaura correctamente los documentos.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [CDataRecoveryHandler::QueryRestoreAutosavedDocuments](#queryrestoreautosaveddocuments) determinar que documenta el usuario desea restaurar. Si un usuario decide no restaurar un documento Autoguardado, `RestoreAutosavedDocuments` elimina el archivo de Autoguardar. En caso contrario, `RestoreAutosavedDocuments` reemplaza el documento abierto con la versión de autoguardado.  
  
 Para utilizar este método, ya sea `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` o `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES` debe establecerse `m_dwRestartManagerSupportFlags`.   
  
##  <a name="saveopendocumentlist"></a>CDataRecoveryHandler::SaveOpenDocumentList  
 Guarda la lista actual de los documentos abiertos en el registro de Windows.  
  
```  
virtual BOOL SaveOpenDocumentList();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si no hay ningún documento abierto para guardar o se guardaron correctamente. `FALSE`Si hay documentos para guardar en el registro, pero no se guardaron porque se produjo un error.  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas del Administrador de reinicio `SaveOpenDocumentList` cuando la aplicación se cierra inesperadamente o cuando sale de una actualización. Cuando se reinicia la aplicación, usa [CDataRecoveryHandler::ReadOpenDocumentList](#readopendocumentlist) para recuperar la lista de documentos abiertos.  
  
 Este método guarda sólo la lista de documentos abiertos. El método [CDataRecoveryHandler::AutosaveDocumentInfo](#autosavedocumentinfo) es responsable de guardar los documentos en Sí.  
  
##  <a name="setautosaveinterval"></a>CDataRecoveryHandler::SetAutosaveInterval  
 Establece el tiempo entre los ciclos de autoguardado en milisegundos.  
  
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
 Cambiar el directorio de autoguardado no mueve actualmente Autoguardado archivos.  
  
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
 El Administrador de reinicio registra información acerca de los documentos abiertos en el registro. Esta información se almacena con el identificador único de reinicio como clave. Dado que el identificador de reinicio es único para cada instancia de una aplicación, varias instancias de una aplicación se cierre inesperadamente y el Administrador de reinicio puede recuperar cada uno de ellos.  
  
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
 Establece si la salida anterior de la aplicación fue provocada por el Administrador de reinicio.  
  
```  
virtual void SetShutdownByRestartManager(BOOL bShutdownByRestartManager);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `bShutdownByRestartManager`|`TRUE`para indicar que el Administrador de reinicio provocó que la aplicación salir; `FALSE` para indicar que la aplicación se cerró por algún otro motivo.|  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo se comporta de forma distinta según si se esperaba la salida anterior o si se inició desde el Administrador de reinicio.  
  
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
 Cuando un usuario guarda un documento, la aplicación quita el archivo Autoguardado porque ya no es necesario. `UpdateDocumentInfo`Elimina el archivo Autoguardado mediante una llamada a [CDataRecoveryHandler::RemoveDocumentInfo](#removedocumentinfo). `UpdateDocumentInfo`a continuación, agrega la información de `pDocument` a la lista de actualmente documentos abiertos porque `RemoveDocumentInfo` elimina esa información, pero el guardado documento aún está abierto.  
  
 Para utilizar este método, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES` debe establecerse `m_dwRestartManagerSupportFlags`.   
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CObject (clase)](../../mfc/reference/cobject-class.md)   
 [Procedimiento para agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md)


