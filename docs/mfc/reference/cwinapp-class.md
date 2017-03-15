---
title: CWinApp (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinApp
- hInstance
dev_langs:
- C++
helpviewer_keywords:
- CWinApp class
- application objects [C++]
- HINSTANCE
- main object
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
caps.latest.revision: 27
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
ms.openlocfilehash: 292816c8f753a7b47b563a3fcd0fa336e08acd6a
ms.lasthandoff: 02/24/2017

---
# <a name="cwinapp-class"></a>CWinApp (clase)
La clase base de la que se deriva un objeto de aplicación Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CWinApp : public CWinThread  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinApp::CWinApp](#cwinapp)|Construye un objeto `CWinApp`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinApp:: AddDocTemplate](#adddoctemplate)|Agrega una plantilla de documento a la lista de la aplicación de plantillas de documento disponibles.|  
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|Agrega un nombre de archivo a la lista de archivos usa más recientemente (MRU).|  
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|Llamado por el marco de trabajo cuando la aplicación se cierra inesperadamente.|  
|[CWinApp::CloseAllDocuments](#closealldocuments)|Cierra todos los documentos abiertos.|  
|[CWinApp::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora.|  
|[CWinApp::DelRegTree](#delregtree)|Elimina una clave especificada y todas sus subclaves.|  
|[CWinApp::DoMessageBox](#domessagebox)|Implementa [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) para la aplicación.|  
|[CWinApp::DoWaitCursor](#dowaitcursor)|Activa el cursor de espera y desactiva.|  
|[CWinApp::EnableD2DSupport](#enabled2dsupport)|Permite la aplicación `D2D` admite. Llame a este método antes de que se inicialice la ventana principal.|  
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|HTMLHelp implementa la aplicación, en lugar de WinHelp.|  
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|Permite la interacción de la barra de tareas.|  
|[CWinApp:: ExitInstance](#exitinstance)|Invalidación para limpiar cuando la aplicación termina.|  
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|Recupera el parámetro de entrada para el método de recuperación de la aplicación.|  
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|Devuelve la longitud de tiempo que espera el Administrador de reinicio para que la función de devolución de llamada de recuperación devolver.|  
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|Devuelve las marcas para el Administrador de reinicio.|  
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|Devuelve la clave HKEY_CURRENT_USER\\\RegistryKey\ProfileName "Software".|  
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|Obtiene el controlador de recuperación de datos para esta instancia de la aplicación.|  
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Recupera la posición de la primera plantilla de documento.|  
|[CWinApp::GetHelpMode](#gethelpmode)|Recupera el tipo de ayuda utilizado por la aplicación.|  
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|Recupera la posición de una plantilla de documento. Se puede utilizar de forma recursiva.|  
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|Recupera los valores predeterminados de dispositivo de impresora.|  
|[CWinApp::GetProfileBinary](#getprofilebinary)|Recupera datos binarios de una entrada en la aplicación. Archivo INI.|  
|[CWinApp::GetProfileInt](#getprofileint)|Recupera un entero de una entrada en la aplicación. Archivo INI.|  
|[CWinApp::GetProfileString](#getprofilestring)|Recupera una cadena de una entrada en la aplicación. Archivo INI.|  
|[CWinApp::GetSectionKey](#getsectionkey)|Devuelve la clave HKEY_CURRENT_USER\\\RegistryKey\AppName\lpszSection "Software".|  
|[CWinApp::HideApplication](#hideapplication)|Oculta la aplicación antes de cerrar todos los documentos.|  
|[CWinApp::HtmlHelp](#htmlhelp)|Llamadas del `HTMLHelp` función de Windows.|  
|[InitInstance](#initinstance)|Invalidación para realizar la inicialización de la instancia de Windows, como la creación de los objetos de ventana.|  
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|Indica si está habilitada la interacción de la barra de tareas de Windows 7.|  
|[CWinApp::LoadCursor](#loadcursor)|Carga un recurso de cursor.|  
|[CWinApp::LoadIcon](#loadicon)|Carga un recurso de icono.|  
|[CWinApp::LoadOEMCursor](#loadoemcursor)|Cargas de OEM de Windows predefinidos de cursor que la **OCR_** especifican constantes en WINDOWS. H.|  
|[CWinApp::LoadOEMIcon](#loadoemicon)|Carga un icono predefinido de OEM de Windows que el **OIC_** especifican constantes en WINDOWS. H.|  
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|Carga un Windows predefinidos de cursor que la **IDC_** especifican constantes en WINDOWS. H.|  
|[CWinApp::LoadStandardIcon](#loadstandardicon)|Carga un icono predefinido de Windows que el **IDI_** especifican constantes en WINDOWS. H.|  
|[CWinApp::OnDDECommand](#onddecommand)|Llamado por el marco de trabajo en respuesta a los datos dinámicos DDE (intercambio) ejecute el comando.|  
|[CWinApp:: OnIdle](#onidle)|Invalidación para realizar el procesamiento de tiempo de inactividad específicos de la aplicación.|  
|[CWinApp:: OpenDocumentFile](#opendocumentfile)|Llamado por el marco para abrir un documento desde un archivo.|  
|[CWinApp::ParseCommandLine](#parsecommandline)|Analiza los parámetros individuales y marcadores en la línea de comandos.|  
|[CWinApp:: PreTranslateMessage](#pretranslatemessage)|Filtra los mensajes antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|Intercepta determinados mensajes antes de que lleguen a la aplicación.|  
|[CWinApp::ProcessShellCommand](#processshellcommand)|Controla las marcas y los argumentos de línea de comandos.|  
|[CWinApp::ProcessWndProcException](#processwndprocexception)|Intercepta todas las excepciones no controladas producidas por mensajes de la aplicación y controladores de comandos.|  
|[CWinApp::Register](#register)|Realiza el registro personalizado.|  
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|Registra la aplicación con el Administrador de reinicio.|  
|[CWinApp::ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|Determina si el Administrador de reinicio se vuelve a abrir los archivos que estaban abiertos cuando la aplicación terminó inesperadamente.|  
|[CWinApp::RestartInstance](#restartinstance)|Controla el reinicio de una aplicación iniciado por el Administrador de reinicio.|  
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|Determina si el Administrador de reinicio restaura los archivos guardados automáticamente cuando se reinicia la aplicación.|  
|[CWinApp:: Run](#run)|Se ejecuta el bucle de mensajes predeterminado. Invalidar para personalizar el bucle de mensajes.|  
|[CWinApp::RunAutomated](#runautomated)|Pruebas de línea de comandos de la aplicación para la **/automatización** opción. Obsoleto. En su lugar, utilice el valor de [CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) después de llamar a [ParseCommandLine](#parsecommandline).|  
|[CWinApp:: RunEmbedded](#runembedded)|Pruebas de línea de comandos de la aplicación para la **/incrustación** opción. Obsoleto. En su lugar, utilice el valor de [CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) después de llamar a [ParseCommandLine](#parsecommandline).|  
|[CWinApp::SaveAllModified](#saveallmodified)|Pide al usuario que guarde los documentos de todas las modificaciones.|  
|[CWinApp::SelectPrinter](#selectprinter)|Selecciona una impresora que se indicaba anteriormente un usuario mediante un cuadro de diálogo Imprimir.|  
|[CWinApp::SetHelpMode](#sethelpmode)|Establece e inicializa el tipo de ayuda utilizado por la aplicación.|  
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|Determina si el Administrador de reinicio recupera una aplicación que se cerraron de forma inesperada.|  
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|Determina si el Administrador de reinicio guarde automáticamente documentos abiertos a intervalos regulares.|  
|[CWinApp::SupportsAutosaveAtRestart](#supportsautosaveatrestart)|Determina si el Administrador de reinicio guarde automáticamente cualquier abrir documentos cuando se reinicia la aplicación.|  
|[CWinApp::SupportsRestartManager](#supportsrestartmanager)|Determina si la aplicación admite el Administrador de reinicio.|  
|[CWinApp::Unregister](#unregister)|Anula el registro de todo lo que sabe que registre el `CWinApp` objeto.|  
|[CWinApp:: WinHelp](#winhelp)|Llamadas del `WinHelp` función de Windows.|  
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|Escribe datos binarios en una entrada de la aplicación. Archivo INI.|  
|[CWinApp:: Writeprofileint](#writeprofileint)|Escribe un entero a una entrada de la aplicación. Archivo INI.|  
|[CWinApp::WriteProfileString](#writeprofilestring)|Escribe una cadena a una entrada de la aplicación. Archivo INI.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinApp::EnableShellOpen](#enableshellopen)|Permite al usuario abrir archivos de datos del Administrador de archivos de Windows.|  
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|Estándar de carga. Característica lista de archivos de configuración del archivo INI y habilita la MRU.|  
|[CWinApp::OnContextHelp](#oncontexthelp)|Controla la ayuda MAYÚS+F1 dentro de la aplicación.|  
|[CWinApp::OnFileNew](#onfilenew)|Implementa el `ID_FILE_NEW` comando.|  
|[CWinApp::OnFileOpen](#onfileopen)|Implementa el `ID_FILE_OPEN` comando.|  
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|Implementa el `ID_FILE_PRINT_SETUP` comando.|  
|[CWinApp::OnHelp](#onhelp)|Controla la Ayuda de F1 de la aplicación (usando el contexto actual).|  
|[CWinApp::OnHelpFinder](#onhelpfinder)|Controla los comandos `ID_HELP_FINDER` e `ID_DEFAULT_HELP`.|  
|[CWinApp::OnHelpIndex](#onhelpindex)|Controla el comando `ID_HELP_INDEX` y proporciona un tema de Ayuda predeterminado.|  
|[CWinApp::OnHelpUsing](#onhelpusing)|Controla el comando `ID_HELP_USING`.|  
|[CWinApp:: RegisterShellFileTypes](#registershellfiletypes)|Tipos de documentos de toda la aplicación se registra con el Administrador de archivos de Windows.|  
|[CWinApp::SetAppID](#setappid)|Establece explícitamente el identificador de modelo de usuario de aplicación para la aplicación. Este método debe llamarse antes de cualquier interfaz de usuario se presenta al usuario (el mejor lugar es el constructor de la aplicación).|  
|[CWinApp::SetRegistryKey](#setregistrykey)|Provoca que se almacenan en el registro en lugar de los valores de aplicación. Archivos INI.|  
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|Anula el registro de tipos de documentos de toda la aplicación con el Administrador de archivos de Windows.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinApp::m_bHelpMode](#m_bhelpmode)|Indica si el usuario está en modo de contexto de ayuda (normalmente se invoca con MAYÚS+F1).|  
|[CWinApp::m_eHelpType](#m_ehelptype)|Especifica el tipo de ayuda utilizado por la aplicación.|  
|[CWinApp::m_hInstance](#m_hinstance)|Identifica la instancia actual de la aplicación.|  
|[CWinApp:: M_lpcmdline](#m_lpcmdline)|Apunta a una cadena terminada en null que especifica la línea de comandos para la aplicación.|  
|[CWinApp::m_nCmdShow](#m_ncmdshow)|Especifica cómo se muestra inicialmente la ventana.|  
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|Puntero a la ventana principal de la aplicación cuando un servidor OLE está activo en contexto.|  
|[CWinApp::m_pszAppID](#m_pszappid)|Id. de modelo de usuario de aplicación.|  
|[CWinApp::m_pszAppName](#m_pszappname)|Especifica el nombre de la aplicación.|  
|[CWinApp::m_pszExeName](#m_pszexename)|El nombre del módulo de la aplicación.|  
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|La ruta de acceso al archivo de Ayuda de la aplicación.|  
|[CWinApp::m_pszProfileName](#m_pszprofilename)|La aplicación. Nombre de archivo INI.|  
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|Se utiliza para determinar la clave de registro completo para almacenar la configuración de perfil de aplicación.|  
  
### <a name="protected-data-members"></a>Miembros de datos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Marcadores que determinan cómo se comporta el Administrador de reinicio.|  
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|La longitud de tiempo en milisegundos entre guarda.|  
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Puntero al controlador de recuperación de datos para la aplicación.|  
  
## <a name="remarks"></a>Comentarios  
 Un objeto de aplicación proporciona funciones miembro para inicializar la aplicación (y cada instancia de él) y para ejecutar la aplicación.  
  
 Cada aplicación que utiliza Microsoft Foundation classes sólo puede contener un objeto derivado de `CWinApp`. Este objeto se crea cuando se crean otros objetos globales de C++ y ya está disponible cuando se llama a Windows la `WinMain` función, que es proporcionado por la biblioteca Microsoft Foundation Class. Declarar la derivada `CWinApp` objeto en el nivel global.  
  
 Al derivar una clase de aplicación de `CWinApp`, reemplace la [InitInstance](#initinstance) función de miembro para crear el objeto de la ventana principal de la aplicación.  
  
 Además el `CWinApp` funciones miembro, la biblioteca Microsoft Foundation Class proporciona las siguientes funciones globales para tener acceso a su `CWinApp` objeto y otra información global:  
  
- [AfxGetApp](application-information-and-management.md#afxgetapp) Obtiene un puntero a la `CWinApp` objeto.  
  
- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle) Obtiene un identificador de la instancia actual de la aplicación.  
  
- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle) Obtiene un identificador de recursos de la aplicación.  
  
- [AfxGetAppName](application-information-and-management.md#afxgetappname) Obtiene un puntero a una cadena que contiene el nombre de la aplicación. Como alternativa, si tiene un puntero a la `CWinApp` objeto, utilice `m_pszExeName` para obtener el nombre de la aplicación.  
  
 Consulte [CWinApp: la clase de aplicación](../../mfc/cwinapp-the-application-class.md) para obtener más información sobre la `CWinApp` (clase), incluida una descripción general de las acciones siguientes:  
  
- `CWinApp`-derivada código escrito por el Asistente para aplicaciones.  
  
- `CWinApp`del rol en la secuencia de ejecución de la aplicación.  
  
- `CWinApp`'s implementaciones de funciones miembro de forma predeterminada.  
  
- `CWinApp`de clave se pueden sobrecargar.  
  
 El **m_hPrevInstance** miembro de datos ya no existe. Para obtener información sobre la detección de una instancia anterior de `CWinApp`, consulte el artículo de Knowledge Base "Cómo identificar un anterior instancia de una aplicación" (KB106385) en [http://support.microsoft.com/default.aspxscid=kb;en-us;106385](http://support.microsoft.com/default.aspxscid=kb;en-us;106385).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 `CWinApp`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-nameadddoctemplatea--cwinappadddoctemplate"></a><a name="adddoctemplate"></a>CWinApp:: AddDocTemplate  
 Llame a esta función miembro para agregar una plantilla de documento a la lista de plantillas de documento disponibles que mantiene la aplicación.  
  
```  
void AddDocTemplate(CDocTemplate* pTemplate);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTemplate`  
 Un puntero a la `CDocTemplate` va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 Debe agregar todos los documentos de plantillas para una aplicación antes de llamar a [RegisterShellFileTypes](#registershellfiletypes).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#35;](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]  
  
##  <a name="a-nameaddtorecentfilelista--cwinappaddtorecentfilelist"></a><a name="addtorecentfilelist"></a>CWinApp::AddToRecentFileList  
 Llame a esta función miembro para agregar `lpszPathName` a la lista de archivos utilizados más Recientemente.  
  
```  
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszPathName`  
 Ruta de acceso del archivo.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a la [LoadStdProfileSettings](#loadstdprofilesettings) función miembro para cargar la lista de archivos utilizados más Recientemente actual antes de utilizar esta función miembro.  
  
 El marco de trabajo llama a esta función miembro cuando abre un archivo o si ejecuta el comando Guardar como para guardar un archivo con un nuevo nombre.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#36;](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]  
  
##  <a name="a-nameapplicationrecoverycallbacka--cwinappapplicationrecoverycallback"></a><a name="applicationrecoverycallback"></a>CWinApp::ApplicationRecoveryCallback  
 Llamado por el marco de trabajo cuando la aplicación se cierra inesperadamente.  
  
```  
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpvParam`  
 Reservado para un uso futuro.  
  
### <a name="return-value"></a>Valor devuelto  
 0 si este método se realiza correctamente; distinto de cero si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación admite el Administrador de reinicio, el marco de trabajo llama a esta función cuando la aplicación se cierra inesperadamente.  
  
 La implementación predeterminada de `ApplicationRecoveryCallback` utiliza el `CDataRecoveryHandler` para guardar la lista de documentos abiertos actualmente en el registro. Este método no Autoguardado no todos los archivos.  
  
 Para personalizar el comportamiento, reemplaza esta función en un derivado [clase CWinApp](../../mfc/reference/cwinapp-class.md) o pasar su propio método de recuperación de la aplicación como un parámetro a [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).  
  
##  <a name="a-nameclosealldocumentsa--cwinappclosealldocuments"></a><a name="closealldocuments"></a>CWinApp::CloseAllDocuments  
 Llame a esta función miembro para cerrar todos los documentos abiertos antes de salir.  
  
```  
void CloseAllDocuments(BOOL bEndSession);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEndSession`  
 Especifica si se finaliza la sesión de Windows. Es **TRUE** si la sesión está siendo finalizado; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [HideApplication](#hideapplication) antes de llamar a `CloseAllDocuments`.  
  
##  <a name="a-namecreateprinterdca--cwinappcreateprinterdc"></a><a name="createprinterdc"></a>CWinApp::CreatePrinterDC  
 Llame a esta función miembro para crear un contexto de dispositivo de impresora (DC) de la impresora seleccionada.  
  
```  
BOOL CreatePrinterDC(CDC& dc);
```  
  
### <a name="parameters"></a>Parámetros  
 `dc`  
 Una referencia a un contexto de dispositivo de impresora.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el contexto de dispositivo de impresora se ha creado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 `CreatePrinterDC`Inicializa el contexto de dispositivo que se pase por referencia, por lo que puede usar para imprimir.  
  
 Si la función se realiza correctamente, cuando haya terminado de imprimir, deberá destruir el contexto de dispositivo. Puede dejar que el destructor de la [CDC](../../mfc/reference/cdc-class.md) objeto hacerlo, o puede hacer explícitamente mediante una llamada a [CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc).  
  
##  <a name="a-namecwinappa--cwinappcwinapp"></a><a name="cwinapp"></a>CWinApp::CWinApp  
 Construye un `CWinApp` objeto y pasa `lpszAppName` se almacenen como el nombre de la aplicación.  
  
```  
CWinApp(LPCTSTR lpszAppName = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszAppName`  
 Cadena terminada en null que contiene el nombre de la aplicación que utiliza Windows. Si este argumento no se proporciona o es **NULL**, `CWinApp` utiliza la cadena de recurso **AFX_IDS_APP_TITLE** o el nombre de archivo del archivo ejecutable.  
  
### <a name="remarks"></a>Comentarios  
 Debe construir un objeto global de su `CWinApp`-clase derivada. Puede tener solo un `CWinApp` objeto de la aplicación. El constructor almacena un puntero a la `CWinApp` objeto para que `WinMain` puede llamar a del objeto funciones miembro para inicializar y ejecutar la aplicación.  
  
##  <a name="a-namedelregtreea--cwinappdelregtree"></a><a name="delregtree"></a>CWinApp::DelRegTree  
 Elimina una clave específica del registro y todas sus subclaves.  
  
```  
LONG DelRegTree(
    HKEY hParentKey,  
    const CString& strKeyName);

 
LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName,
    CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *hParentKey*  
 Identificador de una clave del registro.  
  
 *strKeyName*  
 El nombre de la clave del registro que se va a eliminar.  
  
 *pTM*  
 Puntero al objeto CAtlTransactionManager.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para eliminar la clave especificada y sus subclaves.  
  
##  <a name="a-namedomessageboxa--cwinappdomessagebox"></a><a name="domessagebox"></a>CWinApp::DoMessageBox  
 El marco de trabajo llama a esta función miembro para implementar un cuadro de mensaje para la función global [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox).  
  
```  
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,  
    UINT nType,  
    UINT nIDPrompt);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszPrompt*  
 Dirección del texto en el cuadro de mensaje.  
  
 `nType`  
 El cuadro de mensaje [estilo](../../mfc/reference/message-box-styles.md).  
  
 `nIDPrompt`  
 Un índice en una cadena de contexto de ayuda.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve los mismos valores que `AfxMessageBox`.  
  
### <a name="remarks"></a>Comentarios  
 No llame a esta función miembro para abrir un cuadro de mensaje; Utilice `AfxMessageBox` en su lugar.  
  
 Reemplace esta función miembro para personalizar el procesamiento de toda la aplicación de `AfxMessageBox` llamadas.  
  
##  <a name="a-namedowaitcursora--cwinappdowaitcursor"></a><a name="dowaitcursor"></a>CWinApp::DoWaitCursor  
 Esta función miembro se llama el marco de trabajo para implementar [CWaitCursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor), y [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).  
  
```  
virtual void DoWaitCursor(int nCode);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCode`  
 Si este parámetro es 1, aparece un cursor de espera. Si es 0, se restaura el cursor de espera sin incrementar el recuento de referencias. Si-1, se finaliza el cursor de espera.  
  
### <a name="remarks"></a>Comentarios  
 El valor predeterminado implementa un cursor de reloj de arena. `DoWaitCursor`mantiene un recuento de referencias. Si es positivo, se muestra el cursor de reloj de arena.  
  
 Mientras no se llama normalmente `DoWaitCursor` directamente, puede reemplazar esta función miembro para cambiar el cursor de espera o para realizar un procesamiento adicional mientras se muestra el cursor de espera.  
  
 Para que una forma más fácil y más sencilla de implementar un cursor de espera, utilice `CWaitCursor`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#37;](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]  
  
##  <a name="a-nameenabled2dsupporta--cwinappenabled2dsupport"></a><a name="enabled2dsupport"></a>CWinApp::EnableD2DSupport  
 [!INCLUDE[dev10_sp1required](../../mfc/reference/includes/dev10_sp1required_md.md)]  
  
 Habilita la compatibilidad de aplicaciones D2D. Llame a este método antes de que se inicialice la ventana principal.  
  
```  
BOOL EnableD2DSupport(
D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>Parámetros  
 `d2dFactoryType`  
 El modelo de subprocesos de la fábrica D2D y los recursos que se crea.  
  
 `writeFactoryType`  
 Un valor que especifica si el objeto de generador de escritura se comparten o aislado  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si D2D compatibilidad se ha habilitado:  
  
##  <a name="a-nameenablehtmlhelpa--cwinappenablehtmlhelp"></a><a name="enablehtmlhelp"></a>CWinApp::EnableHtmlHelp  
 Llame a esta función miembro desde dentro del constructor de su `CWinApp`-clase derivada para usar HTMLHelp para obtener ayuda de la aplicación.  
  
```  
void EnableHtmlHelp();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameenableshellopena--cwinappenableshellopen"></a><a name="enableshellopen"></a>CWinApp::EnableShellOpen  
 Llamar a esta función normalmente desde su `InitInstance` reemplazo, para permitir que los usuarios de la aplicación abrir archivos de datos cuando haga doble clic en los archivos desde el Administrador de archivos de Windows.  
  
```  
void EnableShellOpen();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a la `RegisterShellFileTypes` funciona junto con esta función miembro, o proporcionar una. Archivo REG con su aplicación para realizar el registro manual de los tipos de documento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#38;](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]  
  
##  <a name="a-nameenabletaskbarinteractiona--cwinappenabletaskbarinteraction"></a><a name="enabletaskbarinteraction"></a>CWinApp::EnableTaskbarInteraction  
 Permite la interacción de la barra de tareas.  
  
```  
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnable`  
 Especifica si se debe habilitar la interacción con la barra de tareas de Windows 7 ( `TRUE`), o deshabilitado ( `FALSE`).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si la interacción de la barra de tareas puede habilitarse o deshabilitarse.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a este método antes de la creación de la ventana principal, de lo contrario, se valida y se devuelve `FALSE`.  
  
##  <a name="a-nameexitinstancea--cwinappexitinstance"></a><a name="exitinstance"></a>CWinApp:: ExitInstance  
 Llamado por el marco desde el **ejecutar** función miembro para salir de esta instancia de la aplicación.  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Código de salida de la aplicación; 0 indica que no hay errores y los valores mayores que 0 indican un error. Este valor se utiliza como el valor devuelto de `WinMain`.  
  
### <a name="remarks"></a>Comentarios  
 No llame a esta función miembro desde cualquier lugar pero dentro del **ejecutar** función miembro.  
  
 La implementación predeterminada de esta función escribe opciones framework a la aplicación. Archivo INI. Reemplazar esta función para limpiar cuando la aplicación termina.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#39;](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]  
  
##  <a name="a-namegetapplicationrecoveryparametera--cwinappgetapplicationrecoveryparameter"></a><a name="getapplicationrecoveryparameter"></a>CWinApp::GetApplicationRecoveryParameter  
 Recupera el parámetro de entrada para el método de recuperación de la aplicación.  
  
```  
virtual LPVOID GetApplicationRecoveryParameter();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El parámetro de entrada predeterminado para el método de recuperación de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 El comportamiento predeterminado de esta función devuelve `NULL`.  
  
 Para obtener más información, consulte [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).  
  
##  <a name="a-namegetapplicationrecoverypingintervala--cwinappgetapplicationrecoverypinginterval"></a><a name="getapplicationrecoverypinginterval"></a>CWinApp::GetApplicationRecoveryPingInterval  
 Devuelve la longitud de tiempo que espera el Administrador de reinicio para que la función de devolución de llamada de recuperación devolver.  
  
```  
virtual DWORD GetApplicationRecoveryPingInterval();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud de tiempo en milisegundos.  
  
### <a name="remarks"></a>Comentarios  
 Cuando una aplicación que se registra con la Administrador de reinicio se cierra inesperadamente, la aplicación intenta guardar los documentos abiertos y llama a la función de devolución de llamada de recuperación. La función de devolución de llamada de recuperación predeterminada es [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).  
  
 La longitud de tiempo que espera la función de devolución de llamada de recuperación para devolver el marco de trabajo es el intervalo de ping. Puede personalizar el intervalo de ping invalidando `CWinApp::GetApplicationRecoveryPingInterval` o proporcionando un valor personalizado para `RegisterWithRestartManager`.  
  
##  <a name="a-namegetapplicationrestartflagsa--cwinappgetapplicationrestartflags"></a><a name="getapplicationrestartflags"></a>CWinApp::GetApplicationRestartFlags  
 Devuelve las marcas para el Administrador de reinicio.  
  
```  
virtual DWORD GetApplicationRestartFlags();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Las marcas para el Administrador de reinicio. La implementación predeterminada devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Las marcas para el Administrador de reinicio no tienen ningún efecto con la implementación predeterminada. Se proporcionan para su uso futuro.  
  
 Se establecen las marcas cuando registre la aplicación con el Administrador de reinicio mediante [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).  
  
 Los valores posibles para las marcas del Administrador de reinicio son:  
  
- `RESTART_NO_CRASH`  
  
- `RESTART_NO_HANG`  
  
- `RESTART_NO_PATCH`  
  
- `RESTART_NO_REBOOT`  
  
##  <a name="a-namegetappregistrykeya--cwinappgetappregistrykey"></a><a name="getappregistrykey"></a>CWinApp::GetAppRegistryKey  
 Devuelve la clave de HKEY_CURRENT_USER\\\RegistryKey\ProfileName "Software".  
  
```  
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pTM`  
 Puntero a un `CAtlTransactionManager` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Clave de aplicación si la función se realiza correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetdatarecoveryhandlera--cwinappgetdatarecoveryhandler"></a><a name="getdatarecoveryhandler"></a>CWinApp::GetDataRecoveryHandler  
 Obtiene el controlador de recuperación de datos para esta instancia de la aplicación.  
  
```  
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El controlador de recuperación de datos para esta instancia de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Cada aplicación que utiliza el Administrador de reinicio debe tener una instancia de la [CDataRecoveryHandler clase](../../mfc/reference/cdatarecoveryhandler-class.md). Esta clase es responsable de supervisar los archivos de autoguardado y documentos abiertos. El comportamiento de la `CDataRecoveryHandler` depende de la configuración del Administrador de reinicio. Para obtener más información, consulte [CDataRecoveryHandler clase](../../mfc/reference/cdatarecoveryhandler-class.md).  
  
 Este método devuelve `NULL` en sistemas operativos anteriores a [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)]. El Administrador de reinicio no se admite en sistemas operativos anteriores a [!INCLUDE[wiprlhext](../../c-runtime-library/reference/includes/wiprlhext_md.md)].  
  
 Si la aplicación no tiene actualmente un controlador de recuperación de datos, este método crea y devuelve un puntero a ella.  
  
##  <a name="a-namegetfirstdoctemplatepositiona--cwinappgetfirstdoctemplateposition"></a><a name="getfirstdoctemplateposition"></a>CWinApp::GetFirstDocTemplatePosition  
 Obtiene la posición de la primera plantilla de documento en la aplicación.  
  
```  
POSITION GetFirstDocTemplatePosition() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un **posición** valor que puede utilizarse para la iteración o recuperación de puntero de objeto; **NULL** si la lista está vacía.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la **posición** valor devuelto en una llamada a [GetNextDocTemplate](#getnextdoctemplate) para obtener el primer [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto.  
  
##  <a name="a-namegethelpmodea--cwinappgethelpmode"></a><a name="gethelpmode"></a>CWinApp::GetHelpMode  
 Recupera el tipo de ayuda utilizado por la aplicación.  
  
```  
AFX_HELP_TYPE GetHelpMode();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tipo de ayuda utilizado por la aplicación. Consulte [CWinApp::m_eHelpType](#m_ehelptype) para obtener más información.  
  
##  <a name="a-namegetnextdoctemplatea--cwinappgetnextdoctemplate"></a><a name="getnextdoctemplate"></a>CWinApp::GetNextDocTemplate  
 Obtiene la plantilla de documento identificada por `pos`, a continuación, se establece `pos` a la **posición** valor.  
  
```  
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 Una referencia a un **posición** valor devuelto por una llamada anterior a `GetNextDocTemplate` o [funciones miembro GetFirstDocTemplatePosition](#getfirstdoctemplateposition). El valor se actualiza a la siguiente posición de esta llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Puede usar `GetNextDocTemplate` en un bucle de iteración de avance, si establece la posición inicial con una llamada a `GetFirstDocTemplatePosition`.  
  
 Debe asegurarse de que su **posición** valor es válido. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.  
  
 Si la plantilla de documento recuperado es el último disponible, a continuación, el nuevo valor de `pos` está establecido en **NULL**.  
  
##  <a name="a-namegetprinterdevicedefaultsa--cwinappgetprinterdevicedefaults"></a><a name="getprinterdevicedefaults"></a>CWinApp::GetPrinterDeviceDefaults  
 Llame a esta función miembro para preparar a una impresora en el contexto de dispositivo para la impresión.  
  
```  
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```  
  
### <a name="parameters"></a>Parámetros  
 *pPrintDlg*  
 Un puntero a un [PRINTDLG](http://msdn.microsoft.com/library/windows/desktop/ms646843) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Recupera los valores predeterminados actuales de impresora de Windows. Archivo INI según sea necesario, o utiliza la última configuración de impresora establecida por el usuario en la configuración de impresión.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing Nº&40;](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]  
  
##  <a name="a-namegetprofilebinarya--cwinappgetprofilebinary"></a><a name="getprofilebinary"></a>CWinApp::GetProfileBinary  
 Llame a esta función miembro para recuperar datos binarios de una entrada dentro de una sección especificada del registro de la aplicación o. Archivo INI.  
  
```  
BOOL GetProfileBinary(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPBYTE* ppData,  
    UINT* pBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszSection*  
 Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada.  
  
 *lpszEntry*  
 Apunta a una cadena terminada en NULL que contiene la entrada cuyo valor se va a recuperar.  
  
 *ppData*  
 Señala un puntero que recibirá la dirección de los datos.  
  
 *pBytes*  
 Apunta a un tipo UINT que recibirá el tamaño de los datos (en bytes).  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro no distingue mayúsculas de minúsculas, por lo que las cadenas de la *lpszSection* y *lpszEntry* parámetros pueden diferir en mayúsculas.  
  
> [!NOTE]
> **GetProfileBinary** asigna un búfer y devuelve su dirección en \* *ppData*. El llamador es responsable de liberar el búfer utilizando **delete []**.  
  
> [!IMPORTANT]
>  Los datos devueltos por esta función no están terminados en NULL necesariamente y el llamador debe realizar la validación. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing nº&41;](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]  
  
 Para obtener otro ejemplo, vea [CWinApp::WriteProfileBinary](#writeprofilebinary).  
  
##  <a name="a-namegetprofileinta--cwinappgetprofileint"></a><a name="getprofileint"></a>CWinApp::GetProfileInt  
 Llame a esta función miembro para recuperar el valor de un entero de una entrada dentro de una sección especificada del registro o el archivo .INI de la aplicación.  
  
```  
UINT GetProfileInt(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    int nDefault);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSection`  
 Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada.  
  
 `lpszEntry`  
 Apunta a una cadena terminada en NULL que contiene la entrada cuyo valor se va a recuperar.  
  
 `nDefault`  
 Especifica el valor predeterminado que se devolverá si el marco no puede encontrar la entrada.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor entero de la cadena que hay a continuación de la entrada especificada si la función se realiza correctamente. El valor devuelto es el valor del parámetro `nDefault` si la función no encuentra la entrada. El valor devuelto es 0 si el valor correspondiente a la entrada especificada no es un entero.  
  
 Esta función miembro admite la notación hexadecimal para el valor del archivo .INI. Cuando se recupera un entero con signo, se debe convertir el valor a `int`.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro no distingue mayúsculas de minúsculas, por lo que las cadenas de los parámetros `lpszSection` y `lpszEntry` pueden tener un modelo distinto de mayúsculas y minúsculas.  
  
> [!IMPORTANT]
>  Los datos devueltos por esta función no están terminados en NULL necesariamente y el llamador debe realizar la validación. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#42;](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]  
  
 Para obtener otro ejemplo, vea [CWinApp:: Writeprofileint](#writeprofileint).  
  
##  <a name="a-namegetprofilestringa--cwinappgetprofilestring"></a><a name="getprofilestring"></a>CWinApp::GetProfileString  
 Llame a esta función miembro para recuperar la cadena asociada a una entrada de la sección especificada en el registro de la aplicación o. Archivo INI.  
  
```  
CString GetProfileString(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszDefault = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSection`  
 Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada.  
  
 `lpszEntry`  
 Apunta a una cadena terminada en null que contiene la entrada cuya cadena que se va a recuperar. Este valor no debe ser **NULL**.  
  
 `lpszDefault`  
 Señala el valor de cadena predeterminado para la entrada dada, si no se encuentra la entrada en el archivo de inicialización.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto es la cadena de la aplicación. Archivo INI o `lpszDefault` si no se encuentra la cadena. La longitud máxima de cadena admitida por el marco de trabajo es `_MAX_PATH`. Si `lpszDefault` es **NULL**, el valor devuelto es una cadena vacía.  
  
### <a name="remarks"></a>Comentarios  
  
> [!IMPORTANT]
>  Los datos devueltos por esta función no están terminados en NULL necesariamente y el llamador debe realizar la validación. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#43;](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileInt](#getprofileint).  
  
##  <a name="a-namegetsectionkeya--cwinappgetsectionkey"></a><a name="getsectionkey"></a>CWinApp::GetSectionKey  
 Devuelve la clave de HKEY_CURRENT_USER\\\RegistryKey\AppName\lpszSection "Software".  
  
```  
HKEY GetSectionKey(
LPCTSTR lpszSection,  
CAtlTransactionManager* pTM = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSection`  
 El nombre de la clave que se va a obtener.  
  
 `pTM`  
 Puntero a un `CAtlTransactionManager` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Clave de sección si la función se realiza correctamente; de lo contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namehideapplicationa--cwinapphideapplication"></a><a name="hideapplication"></a>CWinApp::HideApplication  
 Llame a esta función miembro para ocultar una aplicación antes de cerrar los documentos abiertos.  
  
```  
void HideApplication();
```  
  
##  <a name="a-namehtmlhelpa--cwinapphtmlhelp"></a><a name="htmlhelp"></a>CWinApp::HtmlHelp  
 Llame a esta función miembro para invocar la aplicación HTMLHelp.  
  
```  
virtual void HtmlHelp(
    DWORD_PTR dwData,  
    UINT nCmd = 0x000F);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwData`  
 Especifica datos adicionales. El valor utilizado depende del valor de la `nCmd` parámetro.  
  
 `nCmd`  
 Especifica el tipo de ayuda solicitado. Para obtener una lista de valores posibles y cómo afectan a la `dwData` parámetro, consulte la `uCommand` parámetro se describe en acerca de la API de función HTMLHelp en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 El marco también llama a esta función para invocar la aplicación HTMLHelp.  
  
 El marco de trabajo cerrará automáticamente la aplicación HTMLHelp cuando finaliza la aplicación.  
  
##  <a name="a-nameinitinstancea--cwinappinitinstance"></a><a name="initinstance"></a>InitInstance  
 Windows permite varias copias del mismo programa para ejecutarse al mismo tiempo.  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización es correcta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Inicialización de la aplicación conceptualmente se divide en dos secciones: se ejecuta el programa de tiempo de inicialización de la aplicación de un solo uso que se realiza la primera y la inicialización de la instancia que se ejecuta cada vez una copia de las ejecuciones de programa, incluida la primera vez. Implementación del marco de trabajo de `WinMain` llama a esta función.  
  
 Reemplazar `InitInstance` para inicializar cada nueva instancia de la aplicación se ejecuta en Windows. Normalmente, invalidar `InitInstance` para crear un objeto de la ventana principal y establecer el `CWinThread::m_pMainWnd` miembro de datos para que apunte a esa ventana. Para obtener más información sobre cómo reemplazar esta función miembro, vea [CWinApp: la clase de aplicación](../../mfc/cwinapp-the-application-class.md).  
  
> [!NOTE]
>  Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si se llama a [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) en su `InitInstance` invalidar, especifique `COINIT_APARTMENTTHREADED` (en lugar de `COINIT_MULTITHREADED`). Para obtener más información, vea el artículo PRB: aplicación MFC deja de responder cuando se inicializa la aplicación como un multiproceso apartamento (828643) en [http://support.microsoft.com/default.aspxscid=kb;en-us;828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCListView&#9;](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]  
  
##  <a name="a-nameistaskbarinteractionenableda--cwinappistaskbarinteractionenabled"></a><a name="istaskbarinteractionenabled"></a>CWinApp::IsTaskbarInteractionEnabled  
 Indica si está habilitada la interacción de la barra de tareas de Windows 7.  
  
```  
virtual BOOL IsTaskbarInteractionEnabled();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `TRUE` si `EnableTaskbarInteraction` se ha llamado y el sistema operativo es Windows 7 o posterior.  
  
### <a name="remarks"></a>Comentarios  
 Interacción de la barra de tareas significa que aplicación MDI muestra el contenido de los elementos secundarios MDI de miniaturas en pestañas independientes que aparecen cuando el puntero del mouse está sobre el botón de barra de tareas de la aplicación.  
  
##  <a name="a-nameloadcursora--cwinapploadcursor"></a><a name="loadcursor"></a>CWinApp::LoadCursor  
 Carga el recurso del cursor con el nombre `lpszResourceName` o especificado por `nIDResource` desde el archivo ejecutable actual.  
  
```  
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;  ```  
  
### Parameters  
 `lpszResourceName`  
 Points to a null-terminated string that contains the name of the cursor resource. You can use a `CString` for this argument.  
  
 `nIDResource`  
 ID of the cursor resource. For a list of resources, see [LoadCursor](http://msdn.microsoft.com/library/windows/desktop/ms648391) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Return Value  
 A handle to a cursor if successful; otherwise **NULL**.  
  
### Remarks  
 `LoadCursor` loads the cursor into memory only if it has not been previously loaded; otherwise, it retrieves a handle of the existing resource.  
  
 Use the [LoadStandardCursor](#loadstandardcursor) or [LoadOEMCursor](#loadoemcursor) member function to access the predefined Windows cursors.  
  
### Example  
 [!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]  
  
##  <a name="loadicon"></a>  CWinApp::LoadIcon  
 Loads the icon resource named by `lpszResourceName` or specified by `nIDResource` from the executable file.  
  
```  
LoadIcon(LPCTSTR lpszResourceName) HICON const;  LoadIcon(UINT nIDResource) HICON const;  ```  
  
### <a name="parameters"></a>Parámetros  
 `lpszResourceName`  
 Apunta a una cadena terminada en null que contiene el nombre del recurso de icono. También puede utilizar un `CString` para este argumento.  
  
 `nIDResource`  
 Número de Id. de recurso de icono.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un icono si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 `LoadIcon`carga el icono solo si no previamente cargado; de lo contrario, recupera un identificador de recurso existente.  
  
 Puede usar el [LoadStandardIcon](#loadstandardicon) o [LoadOEMIcon](#loadoemicon) función miembro para tener acceso a los iconos de Windows predefinidos.  
  
> [!NOTE]
>  Esta función miembro llama a la función API de Win32 [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072), que sólo puede cargar un icono cuyo tamaño se ajusta a la **SM_CXICON** y **SM_CYICON** valores de métrica del sistema.  
  
##  <a name="a-nameloadoemcursora--cwinapploadoemcursor"></a><a name="loadoemcursor"></a>CWinApp::LoadOEMCursor  
 Carga Windows predefinidos de recurso de cursor especificado por `nIDCursor`.  
  
```  
HCURSOR LoadOEMCursor(UINT nIDCursor) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDCursor`  
 Un **OCR_** manifiesto identificador de constante que especifica un cursor predefinido de Windows. Debe tener **#define OEMRESOURCE** antes de **#include \<afxwin.h >** para obtener acceso a la **OCR_** constantes en WINDOWS. H.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un cursor, si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `LoadOEMCursor` o [LoadStandardCursor](#loadstandardcursor) función miembro para tener acceso a los cursores predefinidos de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing nº&45;](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]  
  
 [!code-cpp[NVC_MFCWindowing nº&46;](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]  
  
##  <a name="a-nameloadoemicona--cwinapploadoemicon"></a><a name="loadoemicon"></a>CWinApp::LoadOEMIcon  
 Las ventanas de carga predefinidos especificado por el recurso de icono `nIDIcon`.  
  
```  
HICON LoadOEMIcon(UINT nIDIcon) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDIcon`  
 Un **OIC_** manifiesto identificador de constante que especifica un icono de Windows predefinido. Debe tener **#define OEMRESOURCE** antes de **#include \<afxwin.h >** para tener acceso a la **OIC_** constantes en WINDOWS. H.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un icono si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `LoadOEMIcon` o [LoadStandardIcon](#loadstandardicon) función miembro para tener acceso a los iconos de Windows predefinidos.  
  
##  <a name="a-nameloadstandardcursora--cwinapploadstandardcursor"></a><a name="loadstandardcursor"></a>CWinApp::LoadStandardCursor  
 Recursos de cursor predefinidos de cargas de Windows que `lpszCursorName` especifica.  
  
```  
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszCursorName`  
 Un **IDC_** manifiesto identificador de constante que especifica un cursor predefinido de Windows. Estos identificadores se definen en WINDOWS. H. La siguiente lista muestra los posibles valores predefinidos y significados de `lpszCursorName`:  
  
- **IDC_ARROW** el cursor de flecha estándar  
  
- **IDC_IBEAM** el cursor de inserción de texto estándar  
  
- **IDC_WAIT** cursor de reloj de arena usado cuando Windows realiza una tarea lenta  
  
- **IDC_CROSS** cursor en forma de cruz para la selección  
  
- **IDC_UPARROW** flecha que señala hacia arriba  
  
- **IDC_SIZE** obsoleto y no admite; utilice **IDC_SIZEALL**  
  
- **IDC_SIZEALL** una flecha de cuatro puntas. Cursor que se va a utilizar para cambiar el tamaño de una ventana.  
  
- **IDC_ICON** obsoleto y no admitidos. Utilice **IDC_ARROW**.  
  
- **IDC_SIZENWSE** doble flecha con extremos en la parte superior izquierda e inferior derecha  
  
- **IDC_SIZENESW** doble flecha con extremos en la esquina superior izquierda de derecha e inferior  
  
- **IDC_SIZEWE** flecha Horizontal de dos puntas  
  
- **IDC_SIZENS** flecha Vertical de dos puntas  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un cursor, si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `LoadStandardCursor` o [LoadOEMCursor](#loadoemcursor) función miembro para tener acceso a los cursores predefinidos de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#47;](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]  
  
##  <a name="a-nameloadstandardicona--cwinapploadstandardicon"></a><a name="loadstandardicon"></a>CWinApp::LoadStandardIcon  
 Las ventanas de carga predefinidos de recurso de icono que `lpszIconName` especifica.  
  
```  
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszIconName`  
 Un identificador de constante manifiesto que especifica un icono de Windows predefinido. Estos identificadores se definen en WINDOWS. H. Para obtener una lista de los posibles valores predefinidos y sus descripciones, consulte el *lpIconName* parámetro en [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un icono si es correcto; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la `LoadStandardIcon` o [LoadOEMIcon](#loadoemicon) función miembro para tener acceso a los iconos de Windows predefinidos.  
  
##  <a name="a-nameloadstdprofilesettingsa--cwinapploadstdprofilesettings"></a><a name="loadstdprofilesettings"></a>CWinApp::LoadStdProfileSettings  
 Llamar a esta función miembro desde la [InitInstance](#initinstance) función miembro para habilitar y cargar la lista de los archivos usados más recientemente (MRU) y el último estado de vista previa.  
  
```  
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMaxMRU`  
 El número de archivos usados recientemente para realizar el seguimiento.  
  
### <a name="remarks"></a>Comentarios  
 Si `nMaxMRU` es 0, no se mantendrá ninguna lista de elementos utilizados Recientemente.  
  
##  <a name="a-namembhelpmodea--cwinappmbhelpmode"></a><a name="m_bhelpmode"></a>CWinApp::m_bHelpMode  
 **TRUE** si la aplicación está en modo de contexto de ayuda (convencionalmente se invoca con MAYÚS + F1); en caso contrario **FALSE**.  
  
```  
BOOL m_bHelpMode;  
```  
  
### <a name="remarks"></a>Comentarios  
 En el modo de contexto de ayuda, el cursor se convierte en un signo de interrogación y el usuario puede mover acerca de la pantalla. Examine esta marca si desea implementar un tratamiento especial en el modo de ayuda. `m_bHelpMode`es una variable pública de tipo **BOOL**.  
  
##  <a name="a-namemdwrestartmanagersupportflagsa--cwinappmdwrestartmanagersupportflags"></a><a name="m_dwrestartmanagersupportflags"></a>CWinApp::m_dwRestartManagerSupportFlags  
 Marcadores que determinan cómo se comporta el Administrador de reinicio.  
  
```  
DWORD m_dwRestartManagerSupportFlags;  
```  
  
### <a name="remarks"></a>Comentarios  
 Para habilitar el Administrador de reinicio, establezca `m_dwRestartManagerSupportFlags` en el comportamiento que desee. La siguiente tabla muestra las marcas que están disponibles.  
  
|||  
|-|-|  
|Marcar|Descripción|  
|`AFX_RESTART_MANAGER_SUPPORT_RESTART`|La aplicación se registra mediante [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager). El Administrador de reinicio es responsable de reiniciar la aplicación si cierra inesperadamente.|  
|- `AFX_RESTART_MANAGER_SUPPORT_RECOVERY`|La aplicación se registra con el Administrador de reinicio y el Administrador de reinicio llama a la función de devolución de llamada de recuperación cuando se reinicia la aplicación. La función de devolución de llamada de recuperación predeterminada es [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|  
|- `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`|Autoguardado esté habilitado y el Administrador de reinicio guarde automáticamente cualquier abrir documentos cuando se reinicia la aplicación.|  
|- `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL`|Autoguardado esté habilitado y el Administrador de reinicio guarde automáticamente cualquier abrir documentos a intervalos regulares. El intervalo se define por [CWinApp::m_nAutosaveInterval](#m_nautosaveinterval).|  
|- `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`|El Administrador de reinicio abre documentos abiertos previamente después de reiniciar la aplicación desde una salida inesperada. El [CDataRecoveryHandler clase](../../mfc/reference/cdatarecoveryhandler-class.md) controla almacenar la lista de documentos abiertos y restaurarlos.|  
|- `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`|El Administrador de reinicio, pide al usuario para restaurar los archivos guardados automáticamente después de reiniciar la aplicación. La `CDataRecoveryHandler` clase solicita al usuario.|  
|- `AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE`|La unión de `AFX_RESTART_MANAGER_SUPPORT_RESTART`, `AFX_RESTART_MANAGER_SUPPORT_RECOVER`, y `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`.|  
|- `AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS`|The union of `AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE`, `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`, `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL`, and `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`.|  
|- `AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS`|The union of `AFX_RESTART_MANAGER_SUPPORT_RESTART`, `AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART`, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`, and `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`.|  
|- `AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS`|The union of `AFX_RESTART_MANAGER_SUPPORT_RECOVERY`, `AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL`, `AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES`, and `AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES`.|  
  
##  <a name="a-namemehelptypea--cwinappmehelptype"></a><a name="m_ehelptype"></a>CWinApp::m_eHelpType  
 El tipo de este miembro de datos es el tipo enumerado **AFX_HELP_TYPE**, que se define dentro de la `CWinApp` clase.  
  
```  
AFX_HELP_TYPE m_eHelpType;  
```  
  
### <a name="remarks"></a>Comentarios  
 El **AFX_HELP_TYPE** enumeración se define como sigue:  
  
 `enum AFX_HELP_TYPE`  
  
 `{`  
  
 `afxWinHelp = 0,`  
  
 `afxHTMLHelp = 1`  
  
 `};`  
  
-   Para establecer la Ayuda de la aplicación Ayuda HTML, llamar a [SetHelpMode](#sethelpmode) y especifique **afxHTMLHelp**.  
  
-   Para establecer ayuda la aplicación a WinHelp, llame a `SetHelpMode` y especifique **afxWinHelp**.  
  
##  <a name="a-namemhinstancea--cwinappmhinstance"></a><a name="m_hinstance"></a>CWinApp::m_hInstance  
 Corresponde a la `hInstance` parámetro pasado por Windows para `WinMain`.  
  
```  
HINSTANCE m_hInstance;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_hInstance` miembro de datos es un identificador de la instancia actual de la aplicación se ejecuta en Windows. Se devuelve mediante la función global [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle). `m_hInstance`es una variable pública de tipo `HINSTANCE`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#55;](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]  
  
##  <a name="a-namemlpcmdlinea--cwinappmlpcmdline"></a><a name="m_lpcmdline"></a>CWinApp:: M_lpcmdline  
 Corresponde a la `lpCmdLine` parámetro pasado por Windows para `WinMain`.  
  
```  
LPTSTR m_lpCmdLine;  
```  
  
### <a name="remarks"></a>Comentarios  
 Apunta a una cadena terminada en null que especifica la línea de comandos para la aplicación. Use `m_lpCmdLine` para tener acceso a los argumentos de línea de comandos el usuario especificado cuando se inició la aplicación. `m_lpCmdLine`es una variable pública de tipo `LPTSTR`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[52 NVC_MFCWindowing](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]  
  
##  <a name="a-namemnautosaveintervala--cwinappmnautosaveinterval"></a><a name="m_nautosaveinterval"></a>CWinApp::m_nAutosaveInterval  
 La longitud de tiempo en milisegundos entre guarda.  
  
```  
int m_nAutosaveInterval;  
```  
  
### <a name="remarks"></a>Comentarios  
 Puede configurar el Administrador de reinicio para Autoguardar de documentos abiertos a intervalos establecidos. Si la aplicación no Autoguardar de archivos, este parámetro tiene ningún efecto.  
  
##  <a name="a-namemncmdshowa--cwinappmncmdshow"></a><a name="m_ncmdshow"></a>CWinApp::m_nCmdShow  
 Corresponde a la `nCmdShow` parámetro pasado por Windows para `WinMain`.  
  
```  
int m_nCmdShow;  
```  
  
### <a name="remarks"></a>Comentarios  
 Debería pasar `m_nCmdShow` como un argumento al llamar a [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) para la ventana principal de la aplicación. `m_nCmdShow`es una variable pública de tipo `int`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing nº&56;](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]  
  
##  <a name="a-namempactivewnda--cwinappmpactivewnd"></a><a name="m_pactivewnd"></a>CWinApp::m_pActiveWnd  
 Este miembro de datos se utiliza para almacenar un puntero a la ventana principal de la aplicación de contenedor OLE que tiene su OLE server aplicación activa en el contexto.  
  
### <a name="remarks"></a>Comentarios  
 Si este miembro de datos es **NULL**, la aplicación no está activo en contexto.  
  
 El marco de trabajo establece esta variable miembro cuando la ventana de marco está activado una aplicación de contenedor OLE en contexto.  
  
##  <a name="a-namempdatarecoveryhandlera--cwinappmpdatarecoveryhandler"></a><a name="m_pdatarecoveryhandler"></a>CWinApp::m_pDataRecoveryHandler  
 Puntero al controlador de recuperación de datos para la aplicación.  
  
```  
CDataRecoveryHandler* m_pDataRecoveryHandler;  
```  
  
### <a name="remarks"></a>Comentarios  
 El controlador de recuperación de datos de una aplicación supervisa los documentos abiertos y guarda ellos. El marco de trabajo usa el controlador de recuperación de datos para restaurar los archivos guardados automáticamente cuando una aplicación se reinicia después de se cierra inesperadamente. Para obtener más información, consulte [CDataRecoveryHandler clase](../../mfc/reference/cdatarecoveryhandler-class.md).  
  
##  <a name="a-namempszappnamea--cwinappmpszappname"></a><a name="m_pszappname"></a>CWinApp::m_pszAppName  
 Especifica el nombre de la aplicación.  
  
```  
LPCTSTR m_pszAppName;  
```  
  
### <a name="remarks"></a>Comentarios  
 El nombre de la aplicación puede proceder del parámetro pasado a la [CWinApp](#cwinapp) constructor, o bien, si no se especifica, en la cadena de recurso con el identificador de **AFX_IDS_APP_TITLE**. Si el nombre de la aplicación no se encuentra en el recurso, proviene del programa. Nombre de archivo EXE.  
  
 Devuelto por la función global [AfxGetAppName](application-information-and-management.md#afxgetappname). `m_pszAppName`es una variable pública de tipo **const char\***.  
  
> [!NOTE]
>  Si asigna un valor a `m_pszAppName`, se debe asignar dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Muchos va a utilizar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:  
  
 [!code-cpp[NVC_MFCWindowing&#57;](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#65;](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]  
  
##  <a name="a-namempszexenamea--cwinappmpszexename"></a><a name="m_pszexename"></a>CWinApp::m_pszExeName  
 Contiene el nombre del archivo ejecutable de la aplicación sin extensión.  
  
```  
LPCTSTR m_pszExeName;  
```  
  
### <a name="remarks"></a>Comentarios  
 A diferencia de [m_pszAppName](#m_pszappname), este nombre no puede contener espacios en blanco. `m_pszExeName`es una variable pública de tipo **const char\***.  
  
> [!NOTE]
>  Si asigna un valor a `m_pszExeName`, se debe asignar dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Muchos va a utilizar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:  
  
 [!code-cpp[NVC_MFCWindowing&#58;](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]  
  
##  <a name="a-namempszhelpfilepatha--cwinappmpszhelpfilepath"></a><a name="m_pszhelpfilepath"></a>CWinApp::m_pszHelpFilePath  
 Contiene la ruta de acceso al archivo de Ayuda de la aplicación.  
  
```  
LPCTSTR m_pszHelpFilePath;  
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el marco de trabajo inicializa `m_pszHelpFilePath` en el nombre de la aplicación con ". HLP"anexado. Para cambiar el nombre del archivo de ayuda, establezca `m_pszHelpFilePath` para que apunte a una cadena que contiene el nombre completo del archivo de Ayuda deseado. Es un lugar conveniente para hacer esto en la aplicación [InitInstance](#initinstance) (función). `m_pszHelpFilePath`es una variable pública de tipo **const char\***.  
  
> [!NOTE]
>  Si asigna un valor a `m_pszHelpFilePath`, se debe asignar dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Muchos va a utilizar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:  
  
 [!code-cpp[NVC_MFCWindowing&#59;](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]  
  
##  <a name="a-namempszprofilenamea--cwinappmpszprofilename"></a><a name="m_pszprofilename"></a>CWinApp::m_pszProfileName  
 Contiene el nombre de la aplicación. Archivo INI.  
  
```  
LPCTSTR m_pszProfileName;  
```  
  
### <a name="remarks"></a>Comentarios  
 `m_pszProfileName`es una variable pública de tipo **const char\***.  
  
> [!NOTE]
>  Si asigna un valor a `m_pszProfileName`, se debe asignar dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Muchos va a utilizar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:  
  
 [!code-cpp[60 NVC_MFCWindowing](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]  
  
##  <a name="a-namempszregistrykeya--cwinappmpszregistrykey"></a><a name="m_pszregistrykey"></a>CWinApp::m_pszRegistryKey  
 Se utiliza para determinar, en el registro o el archivo INI, configuración de perfil de aplicación que se almacena.  
  
```  
LPCTSTR m_pszRegistryKey;  
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, este miembro de datos se trata como de solo lectura.  
  
-   El valor se almacena una clave del registro. El nombre de la configuración de perfil de aplicación se anexa a la siguiente clave del registro: HKEY_CURRENT_USER/Software/LocalAppWizard-generados /.  
  
 Si asigna un valor a `m_pszRegistryKey`, se debe asignar dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Muchos va a utilizar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:  
  
 [!code-cpp[NVC_MFCWindowing&#61;](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]  
  
##  <a name="a-namempszappida--cwinappmpszappid"></a><a name="m_pszappid"></a>CWinApp::m_pszAppID  
 Id. de modelo de usuario de aplicación.  
  
```  
LPCTSTR m_pszAppID;  
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameoncontexthelpa--cwinapponcontexthelp"></a><a name="oncontexthelp"></a>CWinApp::OnContextHelp  
 Controla la ayuda MAYÚS+F1 dentro de la aplicación.  
  
```  
afx_msg void OnContextHelp();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe agregar una `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` instrucción a su `CWinApp` clase mapa de mensajes y también agregar una entrada de la tabla de aceleradores, normalmente MAYÚS+F1, para habilitar esta función miembro.  
  
 `OnContextHelp`pone la aplicación en modo de ayuda. El cursor cambia a una flecha y un signo de interrogación y el usuario puede mover el puntero del mouse y presione el botón primario del mouse para seleccionar un cuadro de diálogo, una ventana, un menú o un botón de comando. Esta función miembro recupera el contexto del objeto con el cursor y llama a la función de Windows WinHelp a dicho contexto de ayuda.  
  
##  <a name="a-nameonddecommanda--cwinapponddecommand"></a><a name="onddecommand"></a>CWinApp::OnDDECommand  
 Llamado por el marco de trabajo cuando la ventana de marco principal recibe DDE ejecutar mensaje.  
  
```  
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszCommand*  
 Apunta a una cadena de comando DDE recibido por la aplicación.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se controló el comando; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada comprueba si el comando es una solicitud para abrir un documento y, en caso afirmativo, abre el documento especificado. Normalmente, el Administrador de archivos de Windows envía esas cadenas de comandos DDE cuando el usuario hace doble clic en un archivo de datos. Reemplazar esta función para controlar otro DDE ejecutar comandos, como el comando para imprimir.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing Nº&48;](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]  
  
##  <a name="a-nameonfilenewa--cwinapponfilenew"></a><a name="onfilenew"></a>CWinApp::OnFileNew  
 Implementa el `ID_FILE_NEW` comando.  
  
```  
afx_msg void OnFileNew();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe agregar una `ON_COMMAND( ID_FILE_NEW, OnFileNew )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, esta función controla la ejecución del comando nuevo archivo.  
  
 Consulte [Nota técnica 22](../../mfc/tn022-standard-commands-implementation.md) para obtener información sobre el comportamiento predeterminado e instrucciones sobre cómo reemplazar esta función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#49;](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing&#50;](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="a-nameonfileopena--cwinapponfileopen"></a><a name="onfileopen"></a>CWinApp::OnFileOpen  
 Implementa el `ID_FILE_OPEN` comando.  
  
```  
afx_msg void OnFileOpen();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe agregar una `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, esta función controla la ejecución del comando Abrir archivo.  
  
 Para obtener información sobre el comportamiento predeterminado e instrucciones sobre cómo reemplazar esta función miembro, vea [Nota técnica 22](../../mfc/tn022-standard-commands-implementation.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#49;](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing&#50;](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="a-nameonfileprintsetupa--cwinapponfileprintsetup"></a><a name="onfileprintsetup"></a>CWinApp::OnFilePrintSetup  
 Implementa el **ID_FILE_PRINT_SETUP** comando.  
  
```  
afx_msg void OnFilePrintSetup();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe agregar una `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, esta función controla la ejecución del comando de impresión de archivos.  
  
 Para obtener información sobre el comportamiento predeterminado e instrucciones sobre cómo reemplazar esta función miembro, vea [Nota técnica 22](../../mfc/tn022-standard-commands-implementation.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#49;](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing&#50;](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]  
  
##  <a name="a-nameonhelpa--cwinapponhelp"></a><a name="onhelp"></a>CWinApp::OnHelp  
 Controla la Ayuda de F1 de la aplicación (usando el contexto actual).  
  
```  
afx_msg void OnHelp();
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente también agregará una entrada de la tecla de aceleración para la tecla F1. Habilitar la tecla F1 es sólo una convención, no es un requisito.  
  
 Debe agregar una `ON_COMMAND( ID_HELP, OnHelp )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, se llama el marco de trabajo cuando el usuario presiona la tecla F1.  
  
 La implementación predeterminada de esta función de controlador de mensajes determina el contexto de ayuda que corresponde a la ventana actual, el cuadro de diálogo o el elemento de menú y, a continuación, llama a WINHELP. EXE. Si no hay ningún contexto disponible actualmente, la función utiliza el contexto predeterminado.  
  
 Reemplace esta función miembro para establecer el contexto de ayuda a algo distinto de la ventana, el cuadro de diálogo, el elemento de menú o el botón de barra de herramientas que actualmente tiene el foco. Llame a `WinHelp` con la Ayuda de identificador de contexto.  
  
##  <a name="a-nameonhelpfindera--cwinapponhelpfinder"></a><a name="onhelpfinder"></a>CWinApp::OnHelpFinder  
 Controla la **ID_HELP_FINDER** y **ID_DEFAULT_HELP** comandos.  
  
```  
afx_msg void OnHelpFinder();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe agregar una `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, el marco de trabajo llama a esta función de controlador de mensajes cuando el usuario de la aplicación selecciona el comando de Ayuda de buscador para invocar `WinHelp` con el estándar **HELP_FINDER** tema.  
  
##  <a name="a-nameonhelpindexa--cwinapponhelpindex"></a><a name="onhelpindex"></a>CWinApp::OnHelpIndex  
 Controla la **ID_HELP_INDEX** de comandos y proporciona un tema de Ayuda predeterminado.  
  
```  
afx_msg void OnHelpIndex();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe agregar una `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, el marco de trabajo llama a esta función de controlador de mensajes cuando el usuario de la aplicación selecciona el comando de índice de la ayuda para invocar `WinHelp` con el estándar **HELP_INDEX** tema.  
  
##  <a name="a-nameonhelpusinga--cwinapponhelpusing"></a><a name="onhelpusing"></a>CWinApp::OnHelpUsing  
 Controla la **ID_HELP_USING** comando.  
  
```  
afx_msg void OnHelpUsing();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe agregar una `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. El marco de trabajo llama a esta función de controlador de mensajes cuando el usuario de la aplicación selecciona el comando Ayuda usando para invocar la `WinHelp` aplicación con el estándar **HELP_HELPONHELP** tema.  
  
##  <a name="a-nameonidlea--cwinapponidle"></a><a name="onidle"></a>CWinApp:: OnIdle  
 Reemplace esta función miembro para realizar el procesamiento de tiempo de inactividad.  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lCount`  
 Incrementa un contador cada vez que `OnIdle` se llama cuando la cola de mensajes de la aplicación está vacía. Este contador se restablece a 0 cada vez que se procesa un mensaje nuevo. Puede usar el `lCount` parámetro para determinar la cantidad relativa de tiempo la aplicación ha estado inactiva sin procesar un mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero para recibir más en tiempo de procesamiento inactivo; 0 si no hay más tiempo de inactividad es necesaria.  
  
### <a name="remarks"></a>Comentarios  
 `OnIdle`se llama en el bucle de mensajes de forma predeterminada cuando la cola de mensajes de la aplicación está vacía. Use la invalidación para llamar a su propio fondo de las tareas de controlador de inactividad.  
  
 `OnIdle`debería devolver 0 para indicar que no es necesario ningún procesamiento de tiempo de inactividad. El `lCount` parámetro se incrementa cada vez que `OnIdle` se llama cuando la cola de mensajes está vacía y se restablece a 0 cada vez que se procesa un mensaje nuevo. Puede llamar a las rutinas de inactividad diferentes basándose en este recuento.  
  
 A continuación resume el procesamiento de bucles inactivos:  
  
1.  Si el bucle de mensajes en la biblioteca Microsoft Foundation Class comprueba la cola de mensajes y no busca mensajes pendientes, llama a `OnIdle` para el objeto application y suministros 0 como el `lCount` argumento.  
  
2. `OnIdle`realiza algún procesamiento y devuelve un valor distinto de cero para indicar que se debería llamar de nuevo para realizar un procesamiento adicional.  
  
3.  El bucle de mensajes comprueba la cola de mensajes de nuevo. Si no hay mensajes pendientes, llama a `OnIdle` nuevo, incrementar el `lCount` argumento.  
  
4.  Finalmente, `OnIdle` termina de procesar todas sus tareas inactivas y devuelve 0. Esto indica que el bucle de mensajes para detener la llamada a `OnIdle` hasta que se reciba el siguiente mensaje de la cola de mensajes, momento en que el ciclo de inactividad se reinicia con el argumento establecido en 0.  
  
 No se realizan las tareas largas durante `OnIdle` porque la aplicación no puede procesar la entrada del usuario hasta que `OnIdle` devuelve.  
  
> [!NOTE]
>  La implementación predeterminada de `OnIdle` objetos de interfaz de usuario como elementos de menú y los botones de barra de herramientas de comando de actualizaciones y realiza la limpieza de la estructura de datos internos. Por lo tanto, si invalida `OnIdle`, debe llamar a `CWinApp::OnIdle` con el `lCount` en la versión invalidada. Llame primero a la clase base todo el procesamiento en inactividad (es decir, hasta que la clase base `OnIdle` devuelve 0). Si necesita realizar trabajo antes de que finalice el procesamiento de la clase base, revise la implementación de la clase base para seleccionar el propio `lCount` durante el que se va a realizar su trabajo.  
  
 Si no desea `OnIdle` para llamar siempre que un mensaje se recupera de la cola de mensajes, puede invalidar la [CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage). Si una aplicación ha definido un temporizador muy corto, o si el sistema está enviando el **WM_SYSTIMER** mensaje, a continuación, `OnIdle` llamará repetidamente y degradar el rendimiento.  
  
### <a name="example"></a>Ejemplo  
 Los dos ejemplos siguientes muestran cómo usar `OnIdle`. El primer ejemplo procesa dos tareas inactivas mediante el `lCount` argumento dar prioridad a las tareas. La primera tarea es de alta prioridad, y debe hacerlo siempre que sea posible. La segunda tarea es menos importante y debe realizarse solo cuando hay una larga pausa en la entrada del usuario. Observe la llamada a la versión de clase base `OnIdle`. El segundo ejemplo administra un grupo de tareas inactivas con diferentes prioridades.  
  
 [!code-cpp[NVC_MFCWindowing&#51;](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]  
  
##  <a name="a-nameopendocumentfilea--cwinappopendocumentfile"></a><a name="opendocumentfile"></a>CWinApp:: OpenDocumentFile  
 El marco de trabajo llama a este método para abrir la instancia con nombre [CDocument](../../mfc/reference/cdocument-class.md) archivo de la aplicación.  
  
```  
virtual CDocument* OpenDocumentFile(
LPCTSTR lpszFileName  
BOOL bAddToMRU = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `lpszFileName`  
 El nombre del archivo que desea abrir.  
  
 [in] `bAddToMRU`  
 `TRUE`indica que el documento es uno de los archivos más recientes; `FALSE` indica que el documento no es uno de los archivos más recientes.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CDocument` si es correcto; en caso contrario, `NULL`.  
  
### <a name="remarks"></a>Comentarios  
 Si un documento con ese nombre ya está abierto, la primera ventana de marco que contiene ese documento obtendrá el foco. Si una aplicación admite varias plantillas de documento, el marco de trabajo utiliza la extensión de nombre de archivo para buscar la plantilla de documento apropiado para intentar cargar el documento. Si se realiza correctamente, la plantilla de documento, a continuación, crea una ventana de marco y la vista del documento.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[52 NVC_MFCWindowing](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]  
  
##  <a name="a-nameparsecommandlinea--cwinappparsecommandline"></a><a name="parsecommandline"></a>CWinApp::ParseCommandLine  
 Llame a esta función miembro para analizar la línea de comandos y enviar los parámetros de uno en uno, a [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam).  
  
```  
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `rCmdInfo`  
 Una referencia a un [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se inicia un nuevo proyecto MFC mediante el Asistente para aplicaciones, el Asistente para aplicaciones creará una instancia local de `CCommandLineInfo`y, a continuación, llame a `ProcessShellCommand` y `ParseCommandLine` en el [InitInstance](#initinstance) función miembro. Una línea de comandos sigue la ruta que se describe a continuación:  
  
1.  Después de que se creen en `InitInstance`, `CCommandLineInfo` objeto se pasa a `ParseCommandLine`.  
  
2. `ParseCommandLine`a continuación, llama a `CCommandLineInfo::ParseParam` varias veces, una vez para cada parámetro.  
  
3. `ParseParam`rellena el `CCommandLineInfo` objeto, que se pasa a [ProcessShellCommand](#processshellcommand).  
  
4. `ProcessShellCommand`controla los argumentos de línea de comandos y las marcas.  
  
 Tenga en cuenta que se puede llamar a `ParseCommandLine` directamente según sea necesario.  
  
 Para obtener una descripción de los marcadores de línea de comandos, consulte [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).  
  
##  <a name="a-namepretranslatemessagea--cwinapppretranslatemessage"></a><a name="pretranslatemessage"></a>CWinApp:: PreTranslateMessage  
 Reemplazar esta función para filtrar los mensajes de ventana antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) la implementación predeterminada realiza la traducción de la tecla de aceleración, por lo que debe llamar el `CWinApp::PreTranslateMessage` función miembro en la versión invalidada.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMsg`  
 Un puntero a un [MSG](../../mfc/reference/msg-structure1.md) estructura que contiene el mensaje para procesar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el mensaje se ha procesado totalmente en `PreTranslateMessage` y no se debe procesar más. Cero si se debe procesar el mensaje de la manera normal.  
  
##  <a name="a-nameprocessmessagefiltera--cwinappprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinApp::ProcessMessageFilter  
 Función de enlace del marco de trabajo llama a esta función miembro para filtrar y responder a algunos mensajes de Windows.  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `code`  
 Especifica un código de enlace. Esta función miembro utiliza el código para determinar cómo procesar`lpMsg.`  
  
 `lpMsg`  
 Un puntero a un Windows [MSG](../../mfc/reference/msg-structure1.md) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se procesa el mensaje; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Una función de enlace procesa los eventos antes de enviarlos al mensaje normal de la aplicación de procesamiento.  
  
 Si reemplaza esta función avanzada, asegúrese de llamar a la versión de la clase base para mantener el marco de trabajo de procesamiento de enlace.  
  
##  <a name="a-nameprocessshellcommanda--cwinappprocessshellcommand"></a><a name="processshellcommand"></a>CWinApp::ProcessShellCommand  
 Llama a esta función miembro [InitInstance](#initinstance) para aceptar los parámetros pasados desde el `CCommandLineInfo` objeto identificado por `rCmdInfo`y llevar a cabo la acción indicada.  
  
```  
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `rCmdInfo`  
 Una referencia a un [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el comando de shell se procesa correctamente. Si es 0, devuelve **FALSE** de [InitInstance](#initinstance).  
  
### <a name="remarks"></a>Comentarios  
 Cuando se inicia un nuevo proyecto MFC mediante el Asistente para aplicaciones, el Asistente para aplicaciones creará una instancia local de `CCommandLineInfo`y, a continuación, llame a `ProcessShellCommand` y [ParseCommandLine](#parsecommandline) en el `InitInstance` función miembro. Una línea de comandos sigue la ruta que se describe a continuación:  
  
1.  Después de que se creen en `InitInstance`, `CCommandLineInfo` objeto se pasa a `ParseCommandLine`.  
  
2. `ParseCommandLine`a continuación, llama [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) varias veces, una vez para cada parámetro.  
  
3. `ParseParam`rellena el `CCommandLineInfo` objeto, que se pasa a `ProcessShellCommand`.  
  
4. `ProcessShellCommand`controla los argumentos de línea de comandos y las marcas.  
  
 Los miembros de datos de la `CCommandLineInfo` objeto, identificado por [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand), son del siguiente tipo enumerado, que se define dentro de la `CCommandLineInfo` clase.  
  
 `enum {`  
  
 `FileNew,`  
  
 `FileOpen,`  
  
 `FilePrint,`  
  
 `FilePrintTo,`  
  
 `FileDDE,`  
  
 `};`  
  
 Para obtener una breve descripción de cada uno de estos valores, consulte `CCommandLineInfo::m_nShellCommand`.  
  
##  <a name="a-nameprocesswndprocexceptiona--cwinappprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinApp::ProcessWndProcException  
 El marco de trabajo llama a esta función miembro cada vez que el controlador no detecta una excepción en uno de los mensajes de la aplicación o controladores de comandos.  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 *e*  
 Puntero a una excepción no detectada.  
  
 `pMsg`  
 Un [MSG](../../mfc/reference/msg-structure1.md) estructura que contiene información sobre el mensaje de windows que provocó el marco de trabajo producir una excepción.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor que debe devolverse a Windows. Normalmente esto es 0L para mensajes de windows, 1L ( **TRUE**) para los mensajes de comando.  
  
### <a name="remarks"></a>Comentarios  
 No llame a esta función miembro directamente.  
  
 La implementación predeterminada de esta función miembro, crea un cuadro de mensaje. Si la excepción no detectada se origina en un menú, barra de herramientas o error de comando del acelerador, el cuadro de mensaje muestra un mensaje "Error del comando"; de lo contrario, muestra un mensaje "error interno de la aplicación".  
  
 Reemplace esta función miembro para proporcionar un control de excepciones global. Si desea que el cuadro de mensaje que se mostrará sólo llamar a la funcionalidad básica.  
  
##  <a name="a-nameregistera--cwinappregister"></a><a name="register"></a>CWinApp::Register  
 Realiza las tareas de registro no controladas por `RegisterShellFileTypes`.  
  
```  
virtual BOOL Register();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso de éxito; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada simplemente devuelve TRUE. Reemplazar esta función para proporcionar los pasos de registro personalizado.  
  
##  <a name="a-nameregistershellfiletypesa--cwinappregistershellfiletypes"></a><a name="registershellfiletypes"></a>CWinApp:: RegisterShellFileTypes  
 Llame a esta función miembro para registrar todos los tipos de documento de la aplicación con el Administrador de archivos de Windows.  
  
```  
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bCompat`  
 `TRUE`Agrega entradas de registro para shell comandos impresión e imprimir, permiten al usuario imprimir archivos directamente desde el shell o arrastrando el archivo a un objeto de impresora. También agrega una clave DefaultIcon. De forma predeterminada, este parámetro es `FALSE` para compatibilidad con versiones anteriores.  
  
### <a name="remarks"></a>Comentarios  
 Esto permite al usuario abrir un archivo de datos creado por la aplicación haciendo doble clic en él desde dentro del Administrador de archivos. Llame a `RegisterShellFileTypes` después de llamar a [AddDocTemplate](#adddoctemplate) para cada una de las plantillas de documento en la aplicación. Llamar a la [EnableShellOpen](#enableshellopen) función de miembro al llamar a `RegisterShellFileTypes`.  
  
 `RegisterShellFileTypes`recorre en iteración la lista de [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objetos que la aplicación mantiene y, para cada plantilla de documento, agrega entradas a la base de datos de registro que mantiene Windows para las asociaciones de archivo. El Administrador de archivos utiliza estas entradas para abrir un archivo de datos cuando el usuario hace doble clic. Esto elimina la necesidad de enviar una. Archivo de registro con la aplicación.  
  
> [!NOTE]
> `RegisterShellFileTypes`sólo funciona si el usuario ejecuta el programa con derechos de administrador. Si el programa no tiene derechos de administrador, no puede modificar las claves del registro.  
  
 Si la base de datos de registro ya asocia una extensión de archivo a otro tipo de archivo, no se crea ninguna nueva asociación. Consulte la `CDocTemplate` clase para el formato de cadenas es necesarias registrar esta información.  
  
##  <a name="a-nameregisterwithrestartmanagera--cwinappregisterwithrestartmanager"></a><a name="registerwithrestartmanager"></a>CWinApp::RegisterWithRestartManager  
 Registra la aplicación con el Administrador de reinicio.  
  
```  
virtual HRESULT RegisterWithRestartManager(
BOOL bRegisterRecoveryCallback,  
const CString& strRestartIdentifier);

 
virtual HRESULT RegisterWithRestartManager(
LPCWSTR pwzCommandLineArgs,  
DWORD dwRestartFlags,  
APPLICATION_RECOVERY_CALLBACK pRecoveryCallback,  
LPVOID lpvParam,  
DWORD dwPingInterval,  
DWORD dwCallbackFlags);
```  
  
### <a name="parameters"></a>Parámetros  
  
|||  
|-|-|  
|Parámetro|Descripción|  
|[in] `bRegisterRecoveryCallback`|`TRUE`indica que esta instancia de la aplicación usa una función de devolución de llamada de recuperación; `FALSE` indica que no. El marco de trabajo llama a la función de devolución de llamada de recuperación cuando la aplicación se cierra inesperadamente. Para obtener más información, consulte [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|  
|[in] `strRestartIdentifier`|Cadena única que identifica esta instancia del Administrador de reinicio. El identificador del Administrador de reinicio es único para cada instancia de una aplicación.|  
|[in] `pwzCommandLineArgs`|Cadena que contiene argumentos adicionales desde la línea de comandos.|  
|[in] `dwRestartFlags`|Marcas opcionales para el Administrador de reinicio. Para obtener más información, vea la sección Comentarios.|  
|[in] `pRecoveryCallback`|La función de devolución de llamada de recuperación. Esta función debe tomar un `LPVOID` parámetro como entrada y devuelve un `DWORD`. La función de devolución de llamada de recuperación predeterminada es `CWinApp::ApplicationRecoveryCallback`.|  
|[in] `lpvParam`|El parámetro de entrada para la función de devolución de llamada de recuperación. Para obtener más información, consulte [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|  
|[in] `dwPingInterval`|La longitud de tiempo que espera el Administrador de reinicio para que la función de devolución de llamada de recuperación devolver. Este parámetro está en milisegundos.|  
|[in] `dwCallbackFlags`|Indicadores que se pasan a la función de devolución de llamada de recuperación. Reservado para un uso futuro.|  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`Si el método es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación utiliza la implementación de MFC de forma predeterminada para los archivos de autoguardado, debe usar la versión simple de `RegisterWithRestartManager`. Utilice la versión compleja de `RegisterWithRestartManager` si desea personalizar el comportamiento de autoguardado de la aplicación.  
  
 Si se llama a este método con una cadena vacía para `strRestartIdentifier`, `RegisterWithRestartManager` crea una cadena de identificador único para esta instancia de reiniciar el administrador.  
  
 Cuando una aplicación se cierra inesperadamente, el Administrador de reinicio reinicia la aplicación desde la línea de comandos y proporciona que el único identificador como un argumento opcional de reinicio. En este escenario, el marco llama a `RegisterWithRestartManager` dos veces. La primera llamada procede de [InitInstance](#initinstance) con una cadena vacía para el identificador de cadena. A continuación, el método [CWinApp::ProcessShellCommand](#processshellcommand) llamadas `RegisterWithRestartManager` con el identificador único de reinicio.  
  
 Después de registrar una aplicación con el Administrador de reinicio, el Administrador de reinicio supervisa la aplicación. Si la aplicación se cierra inesperadamente, el Administrador de reinicio llama a la función de devolución de llamada de recuperación durante el proceso de apagado. Espera el Administrador de reinicio el `dwPingInterval` una respuesta de la función de devolución de llamada de recuperación. Si la función de devolución de llamada de recuperación no responde en este momento, la aplicación se cierra sin ejecutar la función de devolución de llamada de recuperación.  
  
 De forma predeterminada, la dwRestartFlags no son compatibles, pero se proporcionan para su uso futuro. Los valores posibles de `dwRestartFlags` son los siguientes:  
  
- `RESTART_NO_CRASH`  
  
- `RESTART_NO_HANG`  
  
- `RESTART_NO_PATCH`  
  
- `RESTART_NO_REBOOT`  
  
##  <a name="a-namereopenpreviousfilesatrestarta--cwinappreopenpreviousfilesatrestart"></a><a name="reopenpreviousfilesatrestart"></a>CWinApp::ReopenPreviousFilesAtRestart  
 Determina si el Administrador de reinicio se vuelve a abrir los archivos que estaban abiertos cuando la aplicación terminó inesperadamente.  
  
```  
virtual BOOL ReopenPreviousFilesAtRestart() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica la vuelve a abrir de administrador de reinicio los archivos previamente abiertos; `FALSE` indica que el Administrador de reinicio no lo hace.  
  
##  <a name="a-namerestartinstancea--cwinapprestartinstance"></a><a name="restartinstance"></a>CWinApp::RestartInstance  
 Controla el reinicio de una aplicación iniciado por el Administrador de reinicio.  
  
```  
virtual BOOL CWinApp::RestartInstance();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si abre el controlador de recuperación de datos previamente documentos abiertos; `FALSE` si el controlador de recuperación de datos tiene un error o si no hay ningún documento abierto anteriormente.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el Administrador de reinicio reinicia una aplicación, el marco de trabajo llama a este método. Este método recupera el controlador de recuperación de datos y restaura los archivos guardados automáticamente. Este método llama a [CDataRecoveryHandler::RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) para determinar si el usuario desea restaurar los archivos guardados automáticamente.  
  
 Este método devuelve `FALSE` si la [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) determina que no hay ningún documento abierto. Si no hay ningún documento abierto, la aplicación comienza ordinariamente.  
  
##  <a name="a-namerestoreautosavedfilesatrestarta--cwinapprestoreautosavedfilesatrestart"></a><a name="restoreautosavedfilesatrestart"></a>CWinApp::RestoreAutosavedFilesAtRestart  
 Determina si el Administrador de reinicio restaura los archivos guardados automáticamente cuando se reinicia la aplicación.  
  
```  
virtual BOOL RestoreAutosavedFilesAtRestart() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica los archivos de autoguardado restauraciones del Administrador de reinicio; `FALSE` indica que el Administrador de reinicio no lo hace.  
  
##  <a name="a-nameruna--cwinapprun"></a><a name="run"></a>CWinApp:: Run  
 Proporciona un bucle de mensajes predeterminado.  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `int` valor devuelto por `WinMain`.  
  
### <a name="remarks"></a>Comentarios  
 **Ejecutar** adquiere y envía los mensajes de Windows hasta que la aplicación recibe un **WM_QUIT** mensaje. Si la cola de mensajes de la aplicación contiene actualmente no hay mensajes, **ejecutar** llamadas [OnIdle](#onidle) para realizar el procesamiento de tiempo de inactividad. Los mensajes entrantes que se van a la [PreTranslateMessage](#pretranslatemessage) función de miembro para un procesamiento especial y, a continuación, la función de Windows **TranslateMessage** para la traducción de teclado estándar; por último, el **DispatchMessage** se llama la función de Windows.  
  
 **Ejecutar** casi nunca se reemplaza, pero se pueden invalidar para proporcionar un comportamiento especial.  
  
##  <a name="a-namerunautomateda--cwinapprunautomated"></a><a name="runautomated"></a>CWinApp::RunAutomated  
 Llame a esta función para determinar si el " **/automatización**"o" **-automatización**" opción está presente, lo que indica si la aplicación de servidor se inició por una aplicación cliente.  
  
```  
BOOL RunAutomated();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se encontró la opción; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si está presente, se quita la opción de la línea de comandos. Para obtener más información sobre la automatización OLE, vea el artículo [servidores de automatización](../../mfc/automation-servers.md).  
  
##  <a name="a-namerunembeddeda--cwinapprunembedded"></a><a name="runembedded"></a>CWinApp:: RunEmbedded  
 Llame a esta función para determinar si el " **/incrustación**"o" **-Embedding**" opción está presente, lo que indica si la aplicación de servidor se inició por una aplicación cliente.  
  
```  
BOOL RunEmbedded();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se encontró la opción; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si está presente, se quita la opción de la línea de comandos. Para obtener más información sobre la incrustación, vea el artículo [servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).  
  
##  <a name="a-namesaveallmodifieda--cwinappsaveallmodified"></a><a name="saveallmodified"></a>CWinApp::SaveAllModified  
 Llamado por el marco para guardar todos los documentos si la ventana de marco principal de la aplicación consiste en Cerrar o a través de un `WM_QUERYENDSESSION` mensaje.  
  
```  
virtual BOOL SaveAllModified();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si es seguro terminar la aplicación; 0 si no es seguro terminar la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función miembro llama el [CDocument:: SaveModified](../../mfc/reference/cdocument-class.md#savemodified) función miembro en uno para todos los documentos modificados dentro de la aplicación.  
  
##  <a name="a-nameselectprintera--cwinappselectprinter"></a><a name="selectprinter"></a>CWinApp::SelectPrinter  
 Llame a esta función miembro para seleccionar una impresora específica y la versión de la impresora que se ha seleccionado anteriormente en el cuadro de diálogo de impresión.  
  
```  
void SelectPrinter(
    HANDLE hDevNames,  
    HANDLE hDevMode,  
    BOOL bFreeOld = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `hDevNames`  
 Un identificador de un [DEVNAMES](../../mfc/reference/devnames-structure.md) estructura que identifica el controlador, el dispositivo y los nombres de puerto de salida de una impresora específica.  
  
 `hDevMode`  
 Un identificador de un [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) estructura que especifica información sobre la inicialización del dispositivo y el entorno de una impresora.  
  
 *bFreeOld*  
 Libera a la impresora seleccionada anteriormente.  
  
### <a name="remarks"></a>Comentarios  
 Si ambos `hDevMode` y `hDevNames` son **NULL**, `SelectPrinter` usa la impresora predeterminada actual.  
  
##  <a name="a-namesethelpmodea--cwinappsethelpmode"></a><a name="sethelpmode"></a>CWinApp::SetHelpMode  
 Establece el tipo de Ayuda de la aplicación.  
  
```  
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```  
  
### <a name="parameters"></a>Parámetros  
 `eHelpType`  
 Especifica el tipo de ayuda para usar. Consulte [CWinApp::m_eHelpType](#m_ehelptype) para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 Establece el tipo de Ayuda de la aplicación.  
  
 Para establecer el tipo de Ayuda de la aplicación en HTMLHelp, se puede llamar a [EnableHTMLHelp](#enablehtmlhelp). Una vez que se llama a `EnableHTMLHelp`, la aplicación debe utilizar HTMLHelp como su aplicación de ayuda. Si desea cambiar para usar WinHelp, puede llamar a `SetHelpMode` y establecer `eHelpType` a **afxWinHelp**.  
  
##  <a name="a-namesetregistrykeya--cwinappsetregistrykey"></a><a name="setregistrykey"></a>CWinApp::SetRegistryKey  
 Hace que las configuraciones de aplicación se almacena en el registro en lugar de archivos INI.  
  
```  
void SetRegistryKey(LPCTSTR lpszRegistryKey);  
void SetRegistryKey(UINT nIDRegistryKey);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszRegistryKey*  
 Puntero a una cadena que contiene el nombre de la clave.  
  
 *nIDRegistryKey*  
 Identificador de un recurso de cadena que contiene el nombre de la clave del registro.  
  
### <a name="remarks"></a>Comentarios  
 Esta función establece *m_pszRegistryKey*, que, a continuación, usa el `GetProfileInt`, `GetProfileString`, `WriteProfileInt`, y `WriteProfileString` funciones miembro de `CWinApp`. Si se llama a esta función, la lista de usados más recientemente (MRU) archivos también se almacena en el registro. La clave del registro suele ser el nombre de una compañía. Se almacena en una clave de la forma siguiente: HKEY_CURRENT_USER\Software\\<company></company>\>\\<application></application>\>\\<section></section>\>\\<value></value>\>.  
  
##  <a name="a-namesupportsapplicationrecoverya--cwinappsupportsapplicationrecovery"></a><a name="supportsapplicationrecovery"></a>CWinApp::SupportsApplicationRecovery  
 Determina si el Administrador de reinicio recupera una aplicación que se cerraron de forma inesperada.  
  
```  
virtual BOOL SupportsApplicationRecovery() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica la recupera de administrador de reinicio de la aplicación; `FALSE` indica que el Administrador de reinicio no lo hace.  
  
##  <a name="a-namesupportsautosaveatintervala--cwinappsupportsautosaveatinterval"></a><a name="supportsautosaveatinterval"></a>CWinApp::SupportsAutosaveAtInterval  
 Determina si el Administrador de reinicio guarde automáticamente documentos abiertos a intervalos regulares.  
  
```  
virtual BOOL SupportsAutosaveAtInterval() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica que el Administrador de reinicio guarde automáticamente abre documentos; `FALSE` indica que el Administrador de reinicio no lo hace.  
  
##  <a name="a-namesupportsautosaveatrestarta--cwinappsupportsautosaveatrestart"></a><a name="supportsautosaveatrestart"></a>CWinApp::SupportsAutosaveAtRestart  
 Determina si el Administrador de reinicio guarde automáticamente cualquier abrir documentos cuando se reinicia la aplicación.  
  
```  
virtual BOOL SupportsAutosaveAtRestart() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica que el Administrador de reinicio guarde automáticamente los documentos abiertos cuando se reinicia la aplicación; `FALSE` indica que el Administrador de reinicio no lo hace.  
  
##  <a name="a-namesupportsrestartmanagera--cwinappsupportsrestartmanager"></a><a name="supportsrestartmanager"></a>CWinApp::SupportsRestartManager  
 Determina si la aplicación admite el Administrador de reinicio.  
  
```  
virtual BOOL SupportsRestartManager() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`indica que la aplicación es compatible con el Administrador de reinicio `FALSE` indica que la aplicación no lo hace.  
  
##  <a name="a-nameunregistera--cwinappunregister"></a><a name="unregister"></a>CWinApp::Unregister  
 Anula el registro de todos los archivos registrados por el objeto application.  
  
```  
virtual BOOL Unregister();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso de éxito; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 El `Unregister` función deshace la inscripción realizada por el objeto application y la [registrar](#register) (función). Normalmente, las dos funciones se llaman implícitamente por MFC y, por tanto, no aparecerá en el código.  
  
 Reemplazar esta función para realizar pasos de anulación de registro personalizada.  
  
##  <a name="a-nameunregistershellfiletypesa--cwinappunregistershellfiletypes"></a><a name="unregistershellfiletypes"></a>CWinApp::UnregisterShellFileTypes  
 Llame a esta función miembro para anular el registro de todos los tipos de documento de la aplicación con el Administrador de archivos de Windows.  
  
```  
void UnregisterShellFileTypes();
```  
  
##  <a name="a-namewinhelpa--cwinappwinhelp"></a><a name="winhelp"></a>CWinApp:: WinHelp  
 Llame a esta función miembro para invocar la aplicación WinHelp.  
  
```  
virtual void WinHelp(
    DWORD_PTR dwData,  
    UINT nCmd = HELP_CONTEXT);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwData`  
 Especifica datos adicionales. El valor utilizado depende del valor de la `nCmd` parámetro.  
  
 `nCmd`  
 Especifica el tipo de ayuda solicitado. Para obtener una lista de valores posibles y cómo afectan a la `dwData` parámetro, consulte la [WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267) función de Windows.  
  
### <a name="remarks"></a>Comentarios  
 El marco también llama a esta función para invocar la aplicación WinHelp.  
  
 El marco de trabajo cerrará automáticamente la aplicación WinHelp cuando finaliza la aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing nº&53;](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]  
  
##  <a name="a-namewriteprofilebinarya--cwinappwriteprofilebinary"></a><a name="writeprofilebinary"></a>CWinApp::WriteProfileBinary  
 Llame a esta función miembro para escribir datos binarios en la sección especificada del registro de la aplicación o. Archivo INI.  
  
```  
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPBYTE pData,  
    UINT nBytes);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSection`  
 Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada. Si la sección no existe, se crea. El nombre de la sección es el caso independiente; la cadena puede ser cualquier combinación de letras mayúsculas y minúsculas.  
  
 `lpszEntry`  
 Apunta a una cadena terminada en null que contiene la entrada en la que el valor se escribirá. Si la entrada no existe en la sección especificada, se crea.  
  
 `pData`  
 Apunta a los datos que se va a escribir.  
  
 `nBytes`  
 Contiene el número de bytes que se escribirán.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo utiliza `CWinApp* pApp = AfxGetApp();` para obtener la clase CWinApp que ilustra una forma que `WriteProfileBinary` y `GetProfileBinary` se pueden usar desde cualquier función en una aplicación MFC.  
  
 [!code-cpp[NVC_MFCWindowing&#54;](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]  
  
 Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileBinary](#getprofilebinary).  
  
##  <a name="a-namewriteprofileinta--cwinappwriteprofileint"></a><a name="writeprofileint"></a>CWinApp:: Writeprofileint  
 Llame a esta función miembro para escribir el valor especificado en la sección especificada del registro de la aplicación o. Archivo INI.  
  
```  
BOOL WriteProfileInt(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    int nValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSection`  
 Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada. Si la sección no existe, se crea. El nombre de la sección es el caso independiente; la cadena puede ser cualquier combinación de letras mayúsculas y minúsculas.  
  
 `lpszEntry`  
 Apunta a una cadena terminada en null que contiene la entrada en la que el valor se escribirá. Si la entrada no existe en la sección especificada, se crea.  
  
 `nValue`  
 Contiene el valor que se va a escribir.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 Este ejemplo utiliza `CWinApp* pApp = AfxGetApp();` para obtener la clase CWinApp que ilustra una forma que `WriteProfileString`, `WriteProfileInt`, `GetProfileString`, y `GetProfileInt` se pueden usar desde cualquier función en una aplicación MFC.  
  
 [!code-cpp[NVC_MFCWindowing&#43;](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileInt](#getprofileint).  
  
##  <a name="a-namewriteprofilestringa--cwinappwriteprofilestring"></a><a name="writeprofilestring"></a>CWinApp::WriteProfileString  
 Llame a esta función miembro para escribir la cadena especificada en la sección especificada del registro de la aplicación o. Archivo INI.  
  
```  
BOOL WriteProfileString(
    LPCTSTR lpszSection,  
    LPCTSTR lpszEntry,  
    LPCTSTR lpszValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszSection`  
 Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada. Si la sección no existe, se crea. El nombre de la sección es el caso independiente; la cadena puede ser cualquier combinación de letras mayúsculas y minúsculas.  
  
 `lpszEntry`  
 Apunta a una cadena terminada en null que contiene la entrada en la que el valor se escribirá. Si la entrada no existe en la sección especificada, se crea. Si este parámetro es `NULL`, la sección especificada por `lpszSection` se elimina.  
  
 `lpszValue`  
 Apunta a la cadena que se va a escribir. Si este parámetro es `NULL`, la entrada especificada por el `lpszEntry` parámetro se elimina.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#43;](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]  
  
 Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileInt](#getprofileint).  
  
##  <a name="a-namesetappida--cwinappsetappid"></a><a name="setappid"></a>CWinApp::SetAppID  
 Establece explícitamente el identificador de modelo de usuario de aplicación para la aplicación. Este método debe llamarse antes de cualquier interfaz de usuario se presenta al usuario (el mejor lugar es el constructor de la aplicación).  
  
```  
void SetAppID(LPCTSTR lpcszAppID);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpcszAppID`  
 Especifica el identificador de modelo de usuario de aplicación.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [CWinThread (clase)](../../mfc/reference/cwinthread-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Cómo: agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md)




