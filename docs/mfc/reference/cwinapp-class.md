---
title: Clase CWinApp
ms.date: 07/15/2019
f1_keywords:
- CWinApp
- AFXWIN/CWinApp
- AFXWIN/CWinApp::CWinApp
- AFXWIN/CWinApp::AddDocTemplate
- AFXWIN/CWinApp::AddToRecentFileList
- AFXWIN/CWinApp::ApplicationRecoveryCallback
- AFXWIN/CWinApp::CloseAllDocuments
- AFXWIN/CWinApp::CreatePrinterDC
- AFXWIN/CWinApp::DelRegTree
- AFXWIN/CWinApp::DoMessageBox
- AFXWIN/CWinApp::DoWaitCursor
- AFXWIN/CWinApp::EnableD2DSupport
- AFXWIN/CWinApp::EnableHtmlHelp
- AFXWIN/CWinApp::EnableTaskbarInteraction
- AFXWIN/CWinApp::ExitInstance
- AFXWIN/CWinApp::GetApplicationRecoveryParameter
- AFXWIN/CWinApp::GetApplicationRecoveryPingInterval
- AFXWIN/CWinApp::GetApplicationRestartFlags
- AFXWIN/CWinApp::GetAppRegistryKey
- AFXWIN/CWinApp::GetDataRecoveryHandler
- AFXWIN/CWinApp::GetFirstDocTemplatePosition
- AFXWIN/CWinApp::GetHelpMode
- AFXWIN/CWinApp::GetNextDocTemplate
- AFXWIN/CWinApp::GetPrinterDeviceDefaults
- AFXWIN/CWinApp::GetProfileBinary
- AFXWIN/CWinApp::GetProfileInt
- AFXWIN/CWinApp::GetProfileString
- AFXWIN/CWinApp::GetSectionKey
- AFXWIN/CWinApp::HideApplication
- AFXWIN/CWinApp::HtmlHelp
- AFXWIN/CWinApp::InitInstance
- AFXWIN/CWinApp::IsTaskbarInteractionEnabled
- AFXWIN/CWinApp::LoadCursor
- AFXWIN/CWinApp::LoadIcon
- AFXWIN/CWinApp::LoadOEMCursor
- AFXWIN/CWinApp::LoadOEMIcon
- AFXWIN/CWinApp::LoadStandardCursor
- AFXWIN/CWinApp::LoadStandardIcon
- AFXWIN/CWinApp::OnDDECommand
- AFXWIN/CWinApp::OnIdle
- AFXWIN/CWinApp::OpenDocumentFile
- AFXWIN/CWinApp::ParseCommandLine
- AFXWIN/CWinApp::PreTranslateMessage
- AFXWIN/CWinApp::ProcessMessageFilter
- AFXWIN/CWinApp::ProcessShellCommand
- AFXWIN/CWinApp::ProcessWndProcException
- AFXWIN/CWinApp::Register
- AFXWIN/CWinApp::RegisterWithRestartManager
- AFXWIN/CWinApp::ReopenPreviousFilesAtRestart
- AFXWIN/CWinApp::RestartInstance
- AFXWIN/CWinApp::RestoreAutosavedFilesAtRestart
- AFXWIN/CWinApp::Run
- AFXWIN/CWinApp::RunAutomated
- AFXWIN/CWinApp::RunEmbedded
- AFXWIN/CWinApp::SaveAllModified
- AFXWIN/CWinApp::SelectPrinter
- AFXWIN/CWinApp::SetHelpMode
- AFXWIN/CWinApp::SupportsApplicationRecovery
- AFXWIN/CWinApp::SupportsAutosaveAtInterval
- AFXWIN/CWinApp::SupportsAutosaveAtRestart
- AFXWIN/CWinApp::SupportsRestartManager
- AFXWIN/CWinApp::Unregister
- AFXWIN/CWinApp::WinHelp
- AFXWIN/CWinApp::WriteProfileBinary
- AFXWIN/CWinApp::WriteProfileInt
- AFXWIN/CWinApp::WriteProfileString
- AFXWIN/CWinApp::EnableShellOpen
- AFXWIN/CWinApp::LoadStdProfileSettings
- AFXWIN/CWinApp::OnContextHelp
- AFXWIN/CWinApp::OnFileNew
- AFXWIN/CWinApp::OnFileOpen
- AFXWIN/CWinApp::OnFilePrintSetup
- AFXWIN/CWinApp::OnHelp
- AFXWIN/CWinApp::OnHelpFinder
- AFXWIN/CWinApp::OnHelpIndex
- AFXWIN/CWinApp::OnHelpUsing
- AFXWIN/CWinApp::RegisterShellFileTypes
- AFXWIN/CWinApp::SetAppID
- AFXWIN/CWinApp::SetRegistryKey
- AFXWIN/CWinApp::UnregisterShellFileTypes
- AFXWIN/CWinApp::m_bHelpMode
- AFXWIN/CWinApp::m_eHelpType
- AFXWIN/CWinApp::m_hInstance
- AFXWIN/CWinApp::m_lpCmdLine
- AFXWIN/CWinApp::m_nCmdShow
- AFXWIN/CWinApp::m_pActiveWnd
- AFXWIN/CWinApp::m_pszAppID
- AFXWIN/CWinApp::m_pszAppName
- AFXWIN/CWinApp::m_pszExeName
- AFXWIN/CWinApp::m_pszHelpFilePath
- AFXWIN/CWinApp::m_pszProfileName
- AFXWIN/CWinApp::m_pszRegistryKey
- AFXWIN/CWinApp::m_dwRestartManagerSupportFlags
- AFXWIN/CWinApp::m_nAutosaveInterval
- AFXWIN/CWinApp::m_pDataRecoveryHandler
helpviewer_keywords:
- CWinApp [MFC], CWinApp
- CWinApp [MFC], AddDocTemplate
- CWinApp [MFC], AddToRecentFileList
- CWinApp [MFC], ApplicationRecoveryCallback
- CWinApp [MFC], CloseAllDocuments
- CWinApp [MFC], CreatePrinterDC
- CWinApp [MFC], DelRegTree
- CWinApp [MFC], DoMessageBox
- CWinApp [MFC], DoWaitCursor
- CWinApp [MFC], EnableD2DSupport
- CWinApp [MFC], EnableHtmlHelp
- CWinApp [MFC], EnableTaskbarInteraction
- CWinApp [MFC], ExitInstance
- CWinApp [MFC], GetApplicationRecoveryParameter
- CWinApp [MFC], GetApplicationRecoveryPingInterval
- CWinApp [MFC], GetApplicationRestartFlags
- CWinApp [MFC], GetAppRegistryKey
- CWinApp [MFC], GetDataRecoveryHandler
- CWinApp [MFC], GetFirstDocTemplatePosition
- CWinApp [MFC], GetHelpMode
- CWinApp [MFC], GetNextDocTemplate
- CWinApp [MFC], GetPrinterDeviceDefaults
- CWinApp [MFC], GetProfileBinary
- CWinApp [MFC], GetProfileInt
- CWinApp [MFC], GetProfileString
- CWinApp [MFC], GetSectionKey
- CWinApp [MFC], HideApplication
- CWinApp [MFC], HtmlHelp
- CWinApp [MFC], InitInstance
- CWinApp [MFC], IsTaskbarInteractionEnabled
- CWinApp [MFC], LoadCursor
- CWinApp [MFC], LoadIcon
- CWinApp [MFC], LoadOEMCursor
- CWinApp [MFC], LoadOEMIcon
- CWinApp [MFC], LoadStandardCursor
- CWinApp [MFC], LoadStandardIcon
- CWinApp [MFC], OnDDECommand
- CWinApp [MFC], OnIdle
- CWinApp [MFC], OpenDocumentFile
- CWinApp [MFC], ParseCommandLine
- CWinApp [MFC], PreTranslateMessage
- CWinApp [MFC], ProcessMessageFilter
- CWinApp [MFC], ProcessShellCommand
- CWinApp [MFC], ProcessWndProcException
- CWinApp [MFC], Register
- CWinApp [MFC], RegisterWithRestartManager
- CWinApp [MFC], ReopenPreviousFilesAtRestart
- CWinApp [MFC], RestartInstance
- CWinApp [MFC], RestoreAutosavedFilesAtRestart
- CWinApp [MFC], Run
- CWinApp [MFC], RunAutomated
- CWinApp [MFC], RunEmbedded
- CWinApp [MFC], SaveAllModified
- CWinApp [MFC], SelectPrinter
- CWinApp [MFC], SetHelpMode
- CWinApp [MFC], SupportsApplicationRecovery
- CWinApp [MFC], SupportsAutosaveAtInterval
- CWinApp [MFC], SupportsAutosaveAtRestart
- CWinApp [MFC], SupportsRestartManager
- CWinApp [MFC], Unregister
- CWinApp [MFC], WinHelp
- CWinApp [MFC], WriteProfileBinary
- CWinApp [MFC], WriteProfileInt
- CWinApp [MFC], WriteProfileString
- CWinApp [MFC], EnableShellOpen
- CWinApp [MFC], LoadStdProfileSettings
- CWinApp [MFC], OnContextHelp
- CWinApp [MFC], OnFileNew
- CWinApp [MFC], OnFileOpen
- CWinApp [MFC], OnFilePrintSetup
- CWinApp [MFC], OnHelp
- CWinApp [MFC], OnHelpFinder
- CWinApp [MFC], OnHelpIndex
- CWinApp [MFC], OnHelpUsing
- CWinApp [MFC], RegisterShellFileTypes
- CWinApp [MFC], SetAppID
- CWinApp [MFC], SetRegistryKey
- CWinApp [MFC], UnregisterShellFileTypes
- CWinApp [MFC], m_bHelpMode
- CWinApp [MFC], m_eHelpType
- CWinApp [MFC], m_hInstance
- CWinApp [MFC], m_lpCmdLine
- CWinApp [MFC], m_nCmdShow
- CWinApp [MFC], m_pActiveWnd
- CWinApp [MFC], m_pszAppID
- CWinApp [MFC], m_pszAppName
- CWinApp [MFC], m_pszExeName
- CWinApp [MFC], m_pszHelpFilePath
- CWinApp [MFC], m_pszProfileName
- CWinApp [MFC], m_pszRegistryKey
- CWinApp [MFC], m_dwRestartManagerSupportFlags
- CWinApp [MFC], m_nAutosaveInterval
- CWinApp [MFC], m_pDataRecoveryHandler
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
ms.openlocfilehash: 4bb1ade4182424cbdcbf0d7ba69af88bbb88abe6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750675"
---
# <a name="cwinapp-class"></a>Clase CWinApp

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
|[CWinApp::AddDocTemplate](#adddoctemplate)|Agrega una plantilla de documento a la lista de plantillas de documento disponibles de la aplicación.|
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|Agrega un nombre de archivo a la lista de archivos (MRU) más reciente.|
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|Llamado por el marco de trabajo cuando la aplicación se cierra inesperadamente.|
|[CWinApp::CloseAllDocuments](#closealldocuments)|Cierra todos los documentos abiertos.|
|[CWinApp::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora.|
|[CWinApp::DelRegTree](#delregtree)|Elimina una clave especificada y todas sus subclaves.|
|[CWinApp::DoMessageBox](#domessagebox)|Implementa [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) para la aplicación.|
|[CWinApp::DoWaitCursor](#dowaitcursor)|Activa y desactiva el cursor de espera.|
|[CWinApp::Enabled2DSupport](#enabled2dsupport)|Habilita la compatibilidad con D2D de la aplicación. Llame a este método antes de que se inicialice la ventana principal.|
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|Implementa HTMLHelp para la aplicación, en lugar de WinHelp.|
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|Habilita la interacción de la barra de tareas.|
|[CWinApp::ExitInstance](#exitinstance)|Invalide para limpiar cuando finalice la aplicación.|
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|Recupera el parámetro de entrada para el método de recuperación de la aplicación.|
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|Devuelve el tiempo que el Administrador de reinicio espera a que se devuelva la función de devolución de llamada de recuperación.|
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|Devuelve las marcas para el administrador de reinicio.|
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|Devuelve la\\clave para HKEY_CURRENT_USER "Software", RegistryKey, ProfileName.|
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|Obtiene el controlador de recuperación de datos para esta instancia de la aplicación.|
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Recupera la posición de la primera plantilla de documento.|
|[CWinApp::GetHelpMode](#gethelpmode)|Recupera el tipo de ayuda utilizada por la aplicación.|
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|Recupera la posición de una plantilla de documento. Se puede utilizar de forma recursiva.|
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|Recupera los valores predeterminados del dispositivo de impresora.|
|[CWinApp::GetProfileBinary](#getprofilebinary)|Recupera datos binarios de una entrada en el archivo . Archivo INI.|
|[CWinApp::GetProfileInt](#getprofileint)|Recupera un entero de una entrada en el archivo . Archivo INI.|
|[CWinApp::GetProfileString](#getprofilestring)|Recupera una cadena de una entrada de la aplicación . Archivo INI.|
|[CWinApp::GetSectionKey](#getsectionkey)|Devuelve la\\clave para HKEY_CURRENT_USER "Software", RegistryKey, AppName, lpszSection.|
|[CWinApp::HideApplication](#hideapplication)|Oculta la aplicación antes de cerrar todos los documentos.|
|[CWinApp::HtmlHelp](#htmlhelp)|Llama `HTMLHelp` a la función Windows.|
|[CWinApp::InitInstance](#initinstance)|Invalidación para realizar la inicialización de instancias de Windows, como crear objetos de ventana.|
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|Indica si la interacción de la barra de tareas de Windows 7 está habilitada.|
|[CWinApp::LoadCursor](#loadcursor)|Carga un recurso de cursor.|
|[CWinApp::LoadIcon](#loadicon)|Carga un recurso de icono.|
|[CWinApp::LoadOEMCursor](#loadoemcursor)|Carga un cursor predefinido OEM de Windows que las constantes **OCR_** especifican en WINDOWS. H.|
|[CWinApp::LoadOEMIcon](#loadoemicon)|Carga un icono predefinido OEM de Windows que las constantes **OIC_** especifican en WINDOWS. H.|
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|Carga un cursor predefinido de Windows que las constantes **IDC_** especifican en WINDOWS. H.|
|[CWinApp::LoadStandardIcon](#loadstandardicon)|Carga un icono predefinido de Windows que las constantes **IDI_** especifican en WINDOWS. H.|
|[CWinApp::OnDDECommand](#onddecommand)|Llamado por el marco de trabajo en respuesta a un comando de ejecución de intercambio de datos dinámico (DDE).|
|[Cwinapp::OnIdle](#onidle)|Invalide para realizar el procesamiento en tiempo de inactividad específico de la aplicación.|
|[CWinApp::OpenDocumentFile](#opendocumentfile)|Llamado por el marco de trabajo para abrir un documento desde un archivo.|
|[CWinApp::ParseCommandLine](#parsecommandline)|Analiza parámetros y indicadores individuales en la línea de comandos.|
|[CWinApp::PreTranslateMessage](#pretranslatemessage)|Filtra los mensajes antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|Intercepta ciertos mensajes antes de que lleguen a la aplicación.|
|[CWinApp::ProcessShellCommand](#processshellcommand)|Controla los argumentos y las marcas de la línea de comandos.|
|[CWinApp::ProcessWndProcException](#processwndprocexception)|Intercepta todas las excepciones no controladas producidas por los controladores de mensajes y comandos de la aplicación.|
|[CWinApp::Registrarse](#register)|Realiza el registro personalizado.|
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|Registra la aplicación con el administrador de reinicio.|
|[CWinApp::ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|Determina si el administrador de reinicio vuelve a abrir los archivos que estaban abiertos cuando la aplicación se salió inesperadamente.|
|[CWinApp::RestartInstance](#restartinstance)|Controla un reinicio de la aplicación iniciado por el Administrador de reinicio.|
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|Determina si el Administrador de reinicio restaura los archivos guardados automáticamente cuando reinicia la aplicación.|
|[CWinApp::Ejecutar](#run)|Ejecuta el bucle de mensajes predeterminado. Reemplazar para personalizar el bucle de mensajes.|
|[CWinApp::RunAutomated](#runautomated)|Comprueba la línea de comandos de la aplicación para la opción **/Automation.** Obsoleto. En su lugar, utilice el valor de [CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) después de llamar a [ParseCommandLine](#parsecommandline).|
|[CWinApp::RunEmbedded](#runembedded)|Comprueba la línea de comandos de la aplicación para la opción **/Embedding.** Obsoleto. En su lugar, utilice el valor de [CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) después de llamar a [ParseCommandLine](#parsecommandline).|
|[CWinApp::SaveAllModified](#saveallmodified)|Solicita al usuario que guarde todos los documentos modificados.|
|[CWinApp::SelectPrinter](#selectprinter)|Selecciona una impresora previamente indicada por un usuario a través de un cuadro de diálogo de impresión.|
|[CWinApp::SetHelpMode](#sethelpmode)|Establece e inicializa el tipo de ayuda utilizada por la aplicación.|
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|Determina si el Administrador de reinicio recupera una aplicación que se ha salido inesperadamente.|
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|Determina si el gestor de reinicio guarda automáticamente los documentos abiertos a intervalos regulares.|
|[CWinApp::SupportsAutosaveAtRestart](#supportsautosaveatrestart)|Determina si el administrador de reinicio guarda automáticamente los documentos abiertos cuando se reinicia la aplicación.|
|[CWinApp::SupportsRestartManager](#supportsrestartmanager)|Determina si la aplicación admite el Administrador de reinicio.|
|[CWinApp::Unregister](#unregister)|Anula el registro de todo `CWinApp` lo que se sabe que está registrado por el objeto.|
|[CWinApp::WinHelp](#winhelp)|Llama `WinHelp` a la función Windows.|
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|Escribe datos binarios en una entrada de la aplicación . Archivo INI.|
|[CWinApp::WriteProfileInt](#writeprofileint)|Escribe un entero en una entrada de la aplicación . Archivo INI.|
|[CWinApp::WriteProfileString](#writeprofilestring)|Escribe una cadena en una entrada de la aplicación . Archivo INI.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CWinApp::EnableShellOpen](#enableshellopen)|Permite al usuario abrir archivos de datos desde el Administrador de archivos de Windows.|
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|Carga estándar . InI y habilita la función de lista de archivos MRU.|
|[CwinApp::OnContextHelp](#oncontexthelp)|Controla la Ayuda de SHIFT+F1 dentro de la aplicación.|
|[Cwinapp::OnFileNew](#onfilenew)|Implementa el comando ID_FILE_NEW.|
|[CwinApp::OnFileOpen](#onfileopen)|Implementa el comando ID_FILE_OPEN.|
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|Implementa el comando ID_FILE_PRINT_SETUP.|
|[Cwinapp::OnHelp](#onhelp)|Controla la Ayuda de F1 de la aplicación (usando el contexto actual).|
|[Cwinapp::OnHelpFinder](#onhelpfinder)|Controla los comandos ID_HELP_FINDER y ID_DEFAULT_HELP.|
|[CwinApp::OnHelpIndex](#onhelpindex)|Controla el comando ID_HELP_INDEX y proporciona un tema de Ayuda predeterminado.|
|[Cwinapp::OnHelpUsing](#onhelpusing)|Controla el comando ID_HELP_USING.|
|[CWinApp::RegisterShellFileTypes](#registershellfiletypes)|Registra todos los tipos de documentos de la aplicación con el Administrador de archivos de Windows.|
|[CWinApp::SetAppID](#setappid)|Establece explícitamente el identificador de modelo de usuario de aplicación para la aplicación. Se debe llamar a este método antes de que se presente al usuario cualquier interfaz de usuario (el mejor lugar es el constructor de la aplicación).|
|[CWinApp::SetRegistryKey](#setregistrykey)|Hace que la configuración de la aplicación se almacene en el registro en lugar de . Archivos INI.|
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|Anula el registro de todos los tipos de documentos de la aplicación con el Administrador de archivos de Windows.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinApp::m_bHelpMode](#m_bhelpmode)|Indica si el usuario está en modo de contexto de Ayuda (normalmente invocado con MAY+F1).|
|[CWinApp::m_eHelpType](#m_ehelptype)|Especifica el tipo de ayuda utilizada por la aplicación.|
|[CWinApp::m_hInstance](#m_hinstance)|Identifica la instancia actual de la aplicación.|
|[CWinApp::m_lpCmdLine](#m_lpcmdline)|Apunta a una cadena terminada en null que especifica la línea de comandos de la aplicación.|
|[CWinApp::m_nCmdShow](#m_ncmdshow)|Especifica cómo se mostrará la ventana inicialmente.|
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|Puntero a la ventana principal de la aplicación contenedora cuando un servidor OLE está activo en el lugar.|
|[CWinApp::m_pszAppID](#m_pszappid)|ID de modelo de usuario de aplicación.|
|[CWinApp::m_pszAppName](#m_pszappname)|Especifica el nombre de la aplicación.|
|[CWinApp::m_pszExeName](#m_pszexename)|El nombre del módulo de la aplicación.|
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|La ruta de acceso al archivo de Ayuda de la aplicación.|
|[CWinApp::m_pszProfileName](#m_pszprofilename)|La aplicación es . Nombre de archivo INI.|
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|Se utiliza para determinar la clave completa del Registro para almacenar la configuración del perfil de aplicación.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Indicadores que determinan cómo se comporta el administrador de reinicio.|
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|La longitud de tiempo en milisegundos entre los guardados automáticos.|
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Puntero al controlador de recuperación de datos para la aplicación.|

## <a name="remarks"></a>Observaciones

Un objeto de aplicación proporciona funciones miembro para inicializar la aplicación (y cada instancia de la misma) y para ejecutar la aplicación.

Cada aplicación que usa las clases de Microsoft `CWinApp`Foundation solo puede contener un objeto derivado de . Este objeto se construye cuando se construyen otros objetos globales de `WinMain` C++ y ya está disponible cuando Windows llama a la función, que proporciona la biblioteca Microsoft Foundation Class. Declare el `CWinApp` objeto derivado a nivel global.

Al derivar una clase `CWinApp`de aplicación de , reemplace la función miembro [InitInstance](#initinstance) para crear el objeto de ventana principal de la aplicación.

Además `CWinApp` de las funciones miembro, la biblioteca Microsoft `CWinApp` Foundation Class proporciona las siguientes funciones globales para tener acceso al objeto y otra información global:

- [AfxGetApp](application-information-and-management.md#afxgetapp) Obtiene un puntero `CWinApp` al objeto.

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle) Obtiene un identificador de la instancia de aplicación actual.

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle) Obtiene un identificador de los recursos de la aplicación.

- [AfxGetAppName](application-information-and-management.md#afxgetappname) Obtiene un puntero a una cadena que contiene el nombre de la aplicación. Como alternativa, si tiene un `CWinApp` puntero `m_pszExeName` al objeto, utilice para obtener el nombre de la aplicación.

Consulte [CWinApp: la clase](../../mfc/cwinapp-the-application-class.md) de `CWinApp` aplicación para obtener más información sobre la clase, incluida una descripción general de lo siguiente:

- `CWinApp`-código derivado escrito por el Asistente para aplicaciones.

- `CWinApp`'s rol en la secuencia de ejecución de la aplicación.

- `CWinApp`Implementaciones de función miembro predeterminadas de 's.

- `CWinApp`Las llaves son reemplazables.

El `m_hPrevInstance` miembro de datos ya no existe. Para determinar si se está ejecutando otra instancia de la aplicación, utilice una exclusión mutua con nombre. Si se produce un error al abrir la exclusión mutua, no hay otras instancias de la aplicación en ejecución.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cwinappadddoctemplate"></a><a name="adddoctemplate"></a>CWinApp::AddDocTemplate

Llame a esta función miembro para agregar una plantilla de documento a la lista de plantillas de documento disponibles que mantiene la aplicación.

```cpp
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>Parámetros

*pTemplate*<br/>
Un puntero `CDocTemplate` a la que se va a agregar.

### <a name="remarks"></a>Observaciones

Debe agregar todas las plantillas de documento a una aplicación antes de llamar a [RegisterShellFileTypes](#registershellfiletypes).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

## <a name="cwinappaddtorecentfilelist"></a><a name="addtorecentfilelist"></a>CWinApp::AddToRecentFileList

Llame a esta función miembro para agregar *lpszPathName* a la lista de archivos MRU.

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*<br/>
Ruta de acceso del archivo.

### <a name="remarks"></a>Observaciones

Debe llamar a la [LoadStdProfileSettings](#loadstdprofilesettings) función miembro para cargar la lista de archivos MRU actual antes de usar esta función miembro.

El marco de trabajo llama a esta función miembro cuando abre un archivo o ejecuta el comando Guardar como para guardar un archivo con un nuevo nombre.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

## <a name="cwinappapplicationrecoverycallback"></a><a name="applicationrecoverycallback"></a>CWinApp::ApplicationRecoveryCallback

Llamado por el marco de trabajo cuando la aplicación se cierra inesperadamente.

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>Parámetros

*lpvParam*<br/>
[in] Reservado para uso futuro.

### <a name="return-value"></a>Valor devuelto

0 si este método es correcto; distinto de cero si se produce un error.

### <a name="remarks"></a>Observaciones

Si la aplicación admite el Administrador de reinicio, el marco de trabajo llama a esta función cuando la aplicación se cierra inesperadamente.

La implementación `ApplicationRecoveryCallback` predeterminada `CDataRecoveryHandler` de utiliza el para guardar la lista de documentos abiertos actualmente en el registro. Este método no guarda automáticamente ningún archivo.

Para personalizar el comportamiento, reemplace esta función en una [clase CWinApp](../../mfc/reference/cwinapp-class.md) derivada o pase su propio método de recuperación de aplicaciones como parámetro a [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).

## <a name="cwinappclosealldocuments"></a><a name="closealldocuments"></a>CWinApp::CloseAllDocuments

Llame a esta función miembro para cerrar todos los documentos abiertos antes de salir.

```cpp
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parámetros

*bEndSession*<br/>
Especifica si se está finalizando o no la sesión de Windows. Es TRUE si se está finalizando la sesión; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Llame a [HideApplication](#hideapplication) antes de llamar a `CloseAllDocuments`.

## <a name="cwinappcreateprinterdc"></a><a name="createprinterdc"></a>CWinApp::CreatePrinterDC

Llame a esta función miembro para crear un contexto de dispositivo de impresora (DC) a partir de la impresora seleccionada.

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>Parámetros

*Dc*<br/>
Una referencia al contexto de un dispositivo de impresora.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el contexto del dispositivo de impresora se crea correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

`CreatePrinterDC`inicializa el contexto del dispositivo que se pasa por referencia, por lo que puede usarlo para imprimir.

Si la función se realiza correctamente, cuando haya terminado de imprimir, debe destruir el contexto del dispositivo. Puede dejar que el destructor del objeto [CDC](../../mfc/reference/cdc-class.md) lo haga o puede hacerlo explícitamente llamando a [CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc).

## <a name="cwinappcwinapp"></a><a name="cwinapp"></a>CWinApp::CWinApp

Construye un `CWinApp` objeto y pasa *lpszAppName* para almacenarlo como el nombre de la aplicación.

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszAppName*<br/>
Cadena terminada en null que contiene el nombre de aplicación que usa Windows. Si este argumento no se `CWinApp` proporciona o es NULL, utiliza la cadena de recursos AFX_IDS_APP_TITLE o el nombre de archivo del archivo ejecutable.

### <a name="remarks"></a>Observaciones

Debe construir un objeto `CWinApp`global de la clase derivada. Solo puede tener `CWinApp` un objeto en la aplicación. El constructor almacena un `CWinApp` puntero `WinMain` al objeto para que pueda llamar a las funciones miembro del objeto para inicializar y ejecutar la aplicación.

## <a name="cwinappdelregtree"></a><a name="delregtree"></a>CWinApp::DelRegTree

Elimina una clave de registro específica y todas sus subclaves.

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

*hParentKey*<br/>
Controle una clave del Registro.

*strKeyName*<br/>
El nombre de la clave del Registro que se va a eliminar.

*Ptm*<br/>
Puntero a CAtlTransactionManager objeto.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto se ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.

### <a name="remarks"></a>Observaciones

Llame a esta función para eliminar la clave especificada y sus subclaves.

## <a name="cwinappdomessagebox"></a><a name="domessagebox"></a>CWinApp::DoMessageBox

El marco de trabajo llama a esta función miembro para implementar un cuadro de mensaje para la función global [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox).

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>Parámetros

*lpszPrompt*<br/>
Dirección del texto en el cuadro de mensaje.

*nType*<br/>
El [estilo](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)de cuadro de mensaje .

*nIDPrompt*<br/>
Un índice de una cadena de contexto de Ayuda.

### <a name="return-value"></a>Valor devuelto

Devuelve los mismos valores que `AfxMessageBox`.

### <a name="remarks"></a>Observaciones

No llame a esta función miembro para abrir un cuadro de mensaje; usar `AfxMessageBox` en su lugar.

Invalide esta función miembro para `AfxMessageBox` personalizar el procesamiento de llamadas en toda la aplicación.

## <a name="cwinappdowaitcursor"></a><a name="dowaitcursor"></a>CWinApp::DoWaitCursor

El marco de trabajo llama a esta función miembro para implementar [CWaitCursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)y [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>Parámetros

*nCódigo*<br/>
Si este parámetro es 1, aparece un cursor de espera. Si es 0, el cursor de espera se restaura sin incrementar el recuento de referencias. Si -1, el cursor de espera finaliza.

### <a name="remarks"></a>Observaciones

El valor predeterminado implementa un cursor de reloj de arena. `DoWaitCursor`mantiene un recuento de referencias. Cuando es positivo, se muestra el cursor del reloj de arena.

Aunque normalmente no `DoWaitCursor` llamaría directamente, podría invalidar esta función miembro para cambiar el cursor de espera o para realizar un procesamiento adicional mientras se muestra el cursor de espera.

Para una forma más fácil y simplificada `CWaitCursor`de implementar un cursor de espera, utilice .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

## <a name="cwinappenabled2dsupport"></a><a name="enabled2dsupport"></a>CWinApp::Enabled2DSupport

Se requiere Visual Studio 2010 SP1.

Habilita la compatibilidad con D2D de la aplicación. Llame a este método antes de que se inicialice la ventana principal.

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parámetros

*d2dFactoryType*<br/>
El modelo de subprocesamiento de la fábrica D2D y los recursos que crea.

*writeFactoryType*<br/>
Valor que especifica si el objeto de fábrica de escritura se compartirá o aislará

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se ha habilitado la compatibilidad con D2D, FALSE - de lo contrario

## <a name="cwinappenablehtmlhelp"></a><a name="enablehtmlhelp"></a>CWinApp::EnableHtmlHelp

Llame a esta función miembro `CWinApp`desde el constructor de la clase derivada para usar HTMLHelp para la ayuda de la aplicación.

```cpp
void EnableHtmlHelp();
```

### <a name="remarks"></a>Observaciones

## <a name="cwinappenableshellopen"></a><a name="enableshellopen"></a>CWinApp::EnableShellOpen

Llame a esta función, normalmente desde la invalidación, `InitInstance` para permitir que los usuarios de la aplicación abran archivos de datos cuando hagan doble clic en los archivos desde el Administrador de archivos de Windows.

```cpp
void EnableShellOpen();
```

### <a name="remarks"></a>Observaciones

Llame `RegisterShellFileTypes` a la función miembro junto con esta función o proporcione un archivo . REG con su solicitud para el registro manual de tipos de documentos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

## <a name="cwinappenabletaskbarinteraction"></a><a name="enabletaskbarinteraction"></a>CWinApp::EnableTaskbarInteraction

Habilita la interacción de la barra de tareas.

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
Especifica si la interacción con la barra de tareas de Windows 7 debe estar habilitada (TRUE) o deshabilitada (FALSE).

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la interacción de la barra de tareas se puede habilitar o deshabilitar.

### <a name="remarks"></a>Observaciones

Este método debe llamarse antes de la creación de la ventana principal, de lo contrario afirma y devuelve FALSE.

## <a name="cwinappexitinstance"></a><a name="exitinstance"></a>CWinApp::ExitInstance

Llamado por el marco `Run` de trabajo desde dentro de la función miembro para salir de esta instancia de la aplicación.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Valor devuelto

Código de salida de la aplicación; 0 indica que no hay errores y los valores mayores que 0 indican un error. Este valor se utiliza como `WinMain`el valor devuelto de .

### <a name="remarks"></a>Observaciones

No llame a esta función `Run` miembro desde cualquier lugar, pero dentro de la función miembro.

La implementación predeterminada de esta función escribe opciones de marco de trabajo en el archivo . Archivo INI. Invalide esta función para limpiar cuando finalice la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

## <a name="cwinappgetapplicationrecoveryparameter"></a><a name="getapplicationrecoveryparameter"></a>CWinApp::GetApplicationRecoveryParameter

Recupera el parámetro de entrada para el método de recuperación de la aplicación.

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>Valor devuelto

El parámetro de entrada predeterminado para el método de recuperación de la aplicación.

### <a name="remarks"></a>Observaciones

El comportamiento predeterminado de esta función devuelve NULL.

Para obtener más información, vea [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

## <a name="cwinappgetapplicationrecoverypinginterval"></a><a name="getapplicationrecoverypinginterval"></a>CWinApp::GetApplicationRecoveryPingInterval

Devuelve el tiempo que el Administrador de reinicio espera a que se devuelva la función de devolución de llamada de recuperación.

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>Valor devuelto

La longitud de tiempo en milisegundos.

### <a name="remarks"></a>Observaciones

Cuando una aplicación que está registrada con el administrador de reinicio se cierra inesperadamente, la aplicación intenta guardar documentos abiertos y llama a la función de devolución de llamada de recuperación. La función de devolución de llamada de recuperación predeterminada es [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

El tiempo que el marco de trabajo espera a que la función de devolución de llamada de recuperación devuelva es el intervalo de ping. Puede personalizar el intervalo de `CWinApp::GetApplicationRecoveryPingInterval` ping reemplazando o `RegisterWithRestartManager`proporcionando un valor personalizado a .

## <a name="cwinappgetapplicationrestartflags"></a><a name="getapplicationrestartflags"></a>CWinApp::GetApplicationRestartFlags

Devuelve las marcas para el administrador de reinicio.

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>Valor devuelto

Las marcas para el administrador de reinicio. La implementación predeterminada devuelve 0.

### <a name="remarks"></a>Observaciones

Los indicadores para el administrador de reinicio no tienen ningún efecto con la implementación predeterminada. Se proporcionan para su uso futuro.

Los indicadores se establecen al registrar la aplicación en el Administrador de reinicio mediante [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).

Los valores posibles para los indicadores del gestor de reinicio son los siguientes:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappgetappregistrykey"></a><a name="getappregistrykey"></a>CWinApp::GetAppRegistryKey

Devuelve la clave\\para HKEY_CURRENT_USER "Software", RegistryKey, ProfileName.

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*Ptm*<br/>
Puntero a `CAtlTransactionManager` un objeto.

### <a name="return-value"></a>Valor devuelto

Tecla de aplicación si la función se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

## <a name="cwinappgetdatarecoveryhandler"></a><a name="getdatarecoveryhandler"></a>CWinApp::GetDataRecoveryHandler

Obtiene el controlador de recuperación de datos para esta instancia de la aplicación.

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>Valor devuelto

El controlador de recuperación de datos para esta instancia de la aplicación.

### <a name="remarks"></a>Observaciones

Cada aplicación que utiliza el Administrador de reinicio debe tener una instancia de la [clase CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md). Esta clase es responsable de supervisar los documentos abiertos y guardar automáticamente los archivos. El comportamiento `CDataRecoveryHandler` del depende de la configuración del administrador de reinicio. Para obtener más información, vea [CDataRecoveryHandler (Clase)](../../mfc/reference/cdatarecoveryhandler-class.md).

Este método devuelve NULL en sistemas operativos anteriores a Windows Vista. El Administrador de reinicio no es compatible con sistemas operativos anteriores a Windows Vista.

Si la aplicación no tiene actualmente un controlador de recuperación de datos, este método crea uno y devuelve un puntero a él.

## <a name="cwinappgetfirstdoctemplateposition"></a><a name="getfirstdoctemplateposition"></a>CWinApp::GetFirstDocTemplatePosition

Obtiene la posición de la primera plantilla de documento en la aplicación.

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor POSITION que se puede utilizar para la iteración o la recuperación de punteros de objeto; NULL si la lista está vacía.

### <a name="remarks"></a>Observaciones

Utilice el valor POSITION devuelto en una llamada a [GetNextDocTemplate](#getnextdoctemplate) para obtener el primer [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto.

## <a name="cwinappgethelpmode"></a><a name="gethelpmode"></a>CWinApp::GetHelpMode

Recupera el tipo de ayuda utilizada por la aplicación.

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>Valor devuelto

El tipo de ayuda utilizado por la aplicación. Consulte [CWinApp::m_eHelpType](#m_ehelptype) para obtener más información.

## <a name="cwinappgetnextdoctemplate"></a><a name="getnextdoctemplate"></a>CWinApp::GetNextDocTemplate

Obtiene la plantilla de documento identificada por *pos*y, a continuación, establece *pos* en el valor POSITION.

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>Parámetros

*Pos*<br/>
Una referencia a un valor POSITION `GetNextDocTemplate` devuelto por una llamada anterior a o [GetFirstDocTemplatePosition](#getfirstdoctemplateposition). El valor se actualiza a la siguiente posición mediante esta llamada.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto.

### <a name="remarks"></a>Observaciones

Puede utilizar `GetNextDocTemplate` en un bucle de iteración directa `GetFirstDocTemplatePosition`si establece la posición inicial con una llamada a .

Debe asegurarse de que el valor POSITION es válido. Si no es válido, la versión de depuración de la biblioteca microsoft Foundation Class afirma.

Si la plantilla de documento recuperada es la última disponible, el nuevo valor de *pos* se establece en NULL.

## <a name="cwinappgetprinterdevicedefaults"></a><a name="getprinterdevicedefaults"></a>CWinApp::GetPrinterDeviceDefaults

Llame a esta función miembro para preparar un contexto de dispositivo de impresora para la impresión.

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>Parámetros

*pPrintDlg*<br/>
Puntero a una estructura [PRINTDLG.](/windows/win32/api/commdlg/ns-commdlg-printdlga)

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Recupera los valores predeterminados de impresora actuales de Windows . INI según sea necesario, o utiliza la última configuración de impresora establecida por el usuario en Configuración de impresión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

## <a name="cwinappgetprofilebinary"></a><a name="getprofilebinary"></a>CWinApp::GetProfileBinary

Llame a esta función miembro para recuperar datos binarios de una entrada dentro de una sección especificada del registro de la aplicación o . Archivo INI.

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>Parámetros

*lpszSection*<br/>
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada.

*lpszEntry*<br/>
Apunta a una cadena terminada en NULL que contiene la entrada cuyo valor se va a recuperar.

*ppData*<br/>
Apunta a un puntero que recibirá la dirección de los datos.

*pBytes*<br/>
Señala a un UINT que recibirá el tamaño de los datos (en bytes).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Esta función miembro no distingue mayúsculas de minúsculas, por lo que las cadenas de los *parámetros lpszSection* y *lpszEntry* pueden diferir en caso.

> [!NOTE]
> `GetProfileBinary`asigna un búfer y devuelve \* su dirección en *ppData*. El autor de la llamada es responsable de liberar el búfer mediante **delete []**.

> [!IMPORTANT]
> Los datos devueltos por esta función no están terminados en NULL necesariamente y el llamador debe realizar la validación. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

Para obtener un ejemplo adicional, vea [CWinApp::WriteProfileBinary](#writeprofilebinary).

## <a name="cwinappgetprofileint"></a><a name="getprofileint"></a>CWinApp::GetProfileInt

Llame a esta función miembro para recuperar el valor de un entero de una entrada dentro de una sección especificada del registro o el archivo .INI de la aplicación.

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>Parámetros

*lpszSection*<br/>
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada.

*lpszEntry*<br/>
Apunta a una cadena terminada en NULL que contiene la entrada cuyo valor se va a recuperar.

*nPredeterminado*<br/>
Especifica el valor predeterminado que se devolverá si el marco no puede encontrar la entrada.

### <a name="return-value"></a>Valor devuelto

Valor entero de la cadena que hay a continuación de la entrada especificada si la función se realiza correctamente. El valor devuelto es el valor del parámetro *nDefault* si la función no encuentra la entrada. El valor devuelto es 0 si el valor correspondiente a la entrada especificada no es un entero.

Esta función miembro admite la notación hexadecimal para el valor del archivo .INI. Al recuperar un entero con signo, debe convertir el valor en un **int**.

### <a name="remarks"></a>Observaciones

Esta función miembro no distingue mayúsculas de minúsculas, por lo que las cadenas de los *parámetros lpszSection* y *lpszEntry* pueden diferir en caso.

> [!IMPORTANT]
> Los datos devueltos por esta función no están terminados en NULL necesariamente y el llamador debe realizar la validación. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

Para obtener un ejemplo adicional, vea [CWinApp::WriteProfileInt](#writeprofileint).

## <a name="cwinappgetprofilestring"></a><a name="getprofilestring"></a>CWinApp::GetProfileString

Llame a esta función miembro para recuperar la cadena asociada a una entrada dentro de la sección especificada en el registro de la aplicación o . Archivo INI.

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszSection*<br/>
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada.

*lpszEntry*<br/>
Apunta a una cadena terminada en null que contiene la entrada cuya cadena se va a recuperar. Este valor no debe ser NULL.

*lpszDefault*<br/>
Señala el valor de cadena predeterminado para la entrada especificada si la entrada no se encuentra en el archivo de inicialización.

### <a name="return-value"></a>Valor devuelto

El valor devuelto es la cadena de la aplicación . INI o *lpszDefault* si no se encuentra la cadena. La longitud máxima de cadena admitida por el marco de trabajo es _MAX_PATH. Si *lpszDefault* es NULL, el valor devuelto es una cadena vacía.

### <a name="remarks"></a>Observaciones

> [!IMPORTANT]
> Los datos devueltos por esta función no están terminados en NULL necesariamente y el llamador debe realizar la validación. Para obtener más información, vea [Avoiding Buffer Overruns](/windows/win32/SecBP/avoiding-buffer-overruns)(Evitar saturaciones del búfer).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileInt](#getprofileint).

## <a name="cwinappgetsectionkey"></a><a name="getsectionkey"></a>CWinApp::GetSectionKey

Devuelve la clave\\de HKEY_CURRENT_USER "Software", RegistryKey, AppName, lpszSection.

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszSection*<br/>
El nombre de la clave que se va a obtener.

*Ptm*<br/>
Puntero a `CAtlTransactionManager` un objeto.

### <a name="return-value"></a>Valor devuelto

Tecla de sección si la función se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

## <a name="cwinapphideapplication"></a><a name="hideapplication"></a>CWinApp::HideApplication

Llame a esta función miembro para ocultar una aplicación antes de cerrar los documentos abiertos.

```cpp
void HideApplication();
```

## <a name="cwinapphtmlhelp"></a><a name="htmlhelp"></a>CWinApp::HtmlHelp

Llame a esta función miembro para invocar la aplicación HTMLHelp.

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>Parámetros

*dwData*<br/>
Especifica datos adicionales. El valor utilizado depende del valor del parámetro *nCmd.* Valor predeterminado `0x000F` significa [HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command).

*nCmd*<br/>
Especifica el tipo de ayuda solicitado. Para obtener una lista de los valores posibles y cómo afectan al parámetro *dwData,* vea el parámetro *uCommand* descrito en las funciones de la API [HtmlHelpW](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw) o [HtmlHelpA](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) en el Windows SDK.

### <a name="remarks"></a>Observaciones

El marco de trabajo también llama a esta función para invocar la aplicación HTMLHelp.

El marco de trabajo cerrará automáticamente la aplicación HTMLHelp cuando finalice la aplicación.

## <a name="cwinappinitinstance"></a><a name="initinstance"></a>CWinApp::InitInstance

Windows permite que varias copias del mismo programa se ejecuten al mismo tiempo.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realiza correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La inicialización de la aplicación se divide conceptualmente en dos secciones: la inicialización de la aplicación de una sola vez que se realiza la primera vez que se ejecuta el programa y la inicialización de instancias que se ejecuta cada vez que se ejecuta una copia del programa, incluida la primera vez. La implementación del `WinMain` marco de trabajo llama a esta función.

Invalide `InitInstance` para inicializar cada nueva instancia de la aplicación que se ejecuta en Windows. Normalmente, se `InitInstance` reemplaza para construir el `CWinThread::m_pMainWnd` objeto de ventana principal y se establece el miembro de datos para que apunte a esa ventana. Para obtener más información sobre cómo reemplazar esta función miembro, vea [CWinApp: la clase de aplicación](../../mfc/cwinapp-the-application-class.md).

> [!NOTE]
> Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si llama a [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) en la invalidación, `InitInstance` especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

## <a name="cwinappistaskbarinteractionenabled"></a><a name="istaskbarinteractionenabled"></a>CWinApp::IsTaskbarInteractionEnabled

Indica si la interacción de la barra de tareas de Windows 7 está habilitada.

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE `EnableTaskbarInteraction` si se ha llamado y el sistema operativo es Windows 7 o superior.

### <a name="remarks"></a>Observaciones

Interacción de la barra de tareas significa que la aplicación MDI muestra el contenido de los elementos secundarios MDI en miniaturas con pestañas independientes que aparecen cuando el puntero del mouse está sobre el botón de la barra de tareas de la aplicación.

## <a name="cwinapploadcursor"></a><a name="loadcursor"></a>CWinApp::LoadCursor

Carga el recurso de cursor denominado por *lpszResourceName* o especificado por *nIDResource* desde el archivo ejecutable actual.

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Apunta a una cadena terminada en null que contiene el nombre del recurso de cursor. Puede usar `CString` a para este argumento.

*nIDResource*<br/>
ID del recurso del cursor. Para obtener una lista de recursos, consulte [LoadCursor](/windows/win32/api/winuser/nf-winuser-loadcursorw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Un identificador de un cursor si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

`LoadCursor`carga el cursor en la memoria solo si no se ha cargado previamente; de lo contrario, recupera un identificador del recurso existente.

Utilice la [LoadStandardCursor](#loadstandardcursor) o [LoadOEMCursor](#loadoemcursor) función miembro para tener acceso a los cursores de Windows predefinidos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

## <a name="cwinapploadicon"></a><a name="loadicon"></a>CWinApp::LoadIcon

Carga el recurso de icono denominado por *lpszResourceName* o especificado por *nIDResource* desde el archivo ejecutable.

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*<br/>
Apunta a una cadena terminada en null que contiene el nombre del recurso de icono. También puede usar `CString` a para este argumento.

*nIDResource*<br/>
Número de ID del recurso de icono.

### <a name="return-value"></a>Valor devuelto

Un identificador de un icono si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

`LoadIcon`carga el icono solo si no se ha cargado previamente; de lo contrario, recupera un identificador del recurso existente.

Puede utilizar la función miembro [LoadStandardIcon](#loadstandardicon) o [LoadOEMIcon](#loadoemicon) para tener acceso a los iconos predefinidos de Windows.

> [!NOTE]
> Esta función miembro llama a la función de API de Win32 [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw), que solo puede cargar un icono cuyo tamaño se ajusta a los valores de métrica del sistema SM_CXICON y SM_CYICON.

## <a name="cwinapploadoemcursor"></a><a name="loadoemcursor"></a>CWinApp::LoadOEMCursor

Carga el recurso de cursor predefinido de Windows especificado por *nIDCursor*.

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>Parámetros

*nIDCursor*<br/>
Identificador de constante de manifiesto **de OCR_** que especifica un cursor de Windows predefinido. Debe tener `#define OEMRESOURCE` `#include \<afxwin.h>` antes para obtener acceso a las constantes **OCR_** en WINDOWS. H.

### <a name="return-value"></a>Valor devuelto

Un identificador de un cursor si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Utilice `LoadOEMCursor` la función miembro [LoadStandardCursor o LoadStandardCursor](#loadstandardcursor) para tener acceso a los cursores predefinidos de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

## <a name="cwinapploadoemicon"></a><a name="loadoemicon"></a>CWinApp::LoadOEMIcon

Carga el recurso de icono predefinido de Windows especificado por *nIDIcon*.

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>Parámetros

*nIDIcon*<br/>
Un identificador de constante de manifiesto **OIC_** que especifica un icono predefinido de Windows. Debe tener `#define OEMRESOURCE` `#include \<afxwin.h>` antes de tener acceso a las **constantes OIC_** en WINDOWS. H.

### <a name="return-value"></a>Valor devuelto

Un identificador de un icono si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Utilice `LoadOEMIcon` la función miembro [LoadStandardIcon](#loadstandardicon) para tener acceso a los iconos predefinidos de Windows.

## <a name="cwinapploadstandardcursor"></a><a name="loadstandardcursor"></a>CWinApp::LoadStandardCursor

Carga el recurso de cursor predefinido de Windows que *lpszCursorName* especifica.

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>Parámetros

*lpszCursorName*<br/>
Un identificador de constante de manifiesto **IDC_** que especifica un cursor de Windows predefinido. Estos identificadores se definen en WINDOWS. H. La siguiente lista muestra los posibles valores predefinidos y significados para *lpszCursorName*:

- IDC_ARROW cursor de flecha estándar

- IDC_IBEAM Cursor de inserción de texto estándar

- IDC_WAIT cursor de Hourglass que se utiliza cuando Windows realiza una tarea que consume mucho tiempo

- IDC_CROSS cursor de cruz para la selección

- IDC_UPARROW Flecha que apunta hacia arriba

- IDC_SIZE Obsoleto y no compatible; usar IDC_SIZEALL

- IDC_SIZEALL Una flecha de cuatro puntas. El cursor que se va a utilizar para cambiar el tamaño de una ventana.

- IDC_ICON Obsoleto y no compatible. Usa IDC_ARROW.

- IDC_SIZENWSE Flecha de dos cabezas con extremos en la parte superior izquierda e inferior derecha

- IDC_SIZENESW flecha de dos cabezas con extremos en la parte superior derecha e inferior izquierda

- IDC_SIZEWE Flecha horizontal de dos puntas

- IDC_SIZENS Flecha vertical de dos puntas

### <a name="return-value"></a>Valor devuelto

Un identificador de un cursor si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Utilice `LoadStandardCursor` la función miembro [LoadOEMCursor o LoadOEMCursor](#loadoemcursor) para tener acceso a los cursores predefinidos de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

## <a name="cwinapploadstandardicon"></a><a name="loadstandardicon"></a>CWinApp::LoadStandardIcon

Carga el recurso de icono predefinido de Windows que *especifica lpszIconName.*

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>Parámetros

*lpszIconName*<br/>
Identificador de constante de manifiesto que especifica un icono predefinido de Windows. Estos identificadores se definen en WINDOWS. H. Para obtener una lista de los posibles valores predefinidos y sus descripciones, vea el parámetro *lpIconName* en [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Un identificador de un icono si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Utilice `LoadStandardIcon` la función miembro o [LoadOEMIcon](#loadoemicon) para tener acceso a los iconos predefinidos de Windows.

## <a name="cwinapploadstdprofilesettings"></a><a name="loadstdprofilesettings"></a>CWinApp::LoadStdProfileSettings

Llame a esta función miembro desde dentro de la [InitInstance](#initinstance) función miembro para habilitar y cargar la lista de archivos utilizados más recientemente (MRU) y el último estado de vista previa.

```cpp
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>Parámetros

*nMaxMRU*<br/>
El número de archivos usados recientemente para realizar un seguimiento.

### <a name="remarks"></a>Observaciones

Si *nMaxMRU* es 0, no se mantendrá ninguna lista MRU.

## <a name="cwinappm_bhelpmode"></a><a name="m_bhelpmode"></a>CWinApp::m_bHelpMode

TRUESi la aplicación está en modo de contexto de Ayuda (invocado convencionalmente con SHIFT + F1); de lo contrario FALSO.

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>Observaciones

En el modo de contexto De ayuda, el cursor se convierte en un signo de interrogación y el usuario puede moverlo por la pantalla. Examine esta marca si desea implementar un control especial en el modo Ayuda. `m_bHelpMode`es una variable pública de tipo BOOL.

## <a name="cwinappm_dwrestartmanagersupportflags"></a><a name="m_dwrestartmanagersupportflags"></a>CWinApp::m_dwRestartManagerSupportFlags

Indicadores que determinan cómo se comporta el administrador de reinicio.

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>Observaciones

Para habilitar el administrador `m_dwRestartManagerSupportFlags` de reinicio, establezca el comportamiento que desee. En la tabla siguiente se muestran los indicadores que están disponibles.

|||
|-|-|
|Marca|Descripción|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|La aplicación se registra mediante [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager). El administrador de reinicio es responsable de reiniciar la aplicación si se cierra inesperadamente.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY|La aplicación se registra con el Administrador de reinicio y el Administrador de reinicio llama a la función de devolución de llamada de recuperación cuando reinicia la aplicación. La función de devolución de llamada de recuperación predeterminada es [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|El guardado automático está habilitado y el administrador de reinicio guarda automáticamente los documentos abiertos cuando se reinicia la aplicación.|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|El guardado automático está habilitado y el administrador de reinicio guarda automáticamente los documentos abiertos a intervalos regulares. El intervalo se define mediante [CWinApp::m_nAutosaveInterval](#m_nautosaveinterval).|
|- AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|El Administrador de reinicio abre documentos abiertos anteriormente después de reiniciar la aplicación desde una salida inesperada. La [clase CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) controla el almacenamiento de la lista de documentos abiertos y su restauración.|
|- AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|El Administrador de reinicio solicita al usuario que restaure los archivos guardados automáticamente después de reiniciar la aplicación. La `CDataRecoveryHandler` clase consulta al usuario.|
|- AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|La unión de AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_SUPPORT_RECOVER y AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|La unión de AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL y AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|La unión de AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES y AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|El sindicato ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES y AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|

## <a name="cwinappm_ehelptype"></a><a name="m_ehelptype"></a>CWinApp::m_eHelpType

El tipo de este miembro de datos es el `CWinApp` tipo enumerado AFX_HELP_TYPE, que se define dentro de la clase.

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>Observaciones

La enumeración AFX_HELP_TYPE se define de la siguiente manera:

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- Para establecer la ayuda de la aplicación en la `afxHTMLHelp`Ayuda HTML, llame a [SetHelpMode](#sethelpmode) y especifique .

- Para establecer la ayuda de la `SetHelpMode` aplicación `afxWinHelp`en WinHelp, llame y especifique .

## <a name="cwinappm_hinstance"></a><a name="m_hinstance"></a>CWinApp::m_hInstance

Corresponde al parámetro *hInstance* pasado `WinMain`por Windows a .

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>Observaciones

El `m_hInstance` miembro de datos es un identificador de la instancia actual de la aplicación que se ejecuta en Windows. Esto lo devuelve la función global [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle). `m_hInstance`es una variable pública de tipo HINSTANCE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

## <a name="cwinappm_lpcmdline"></a><a name="m_lpcmdline"></a>CWinApp::m_lpCmdLine

Corresponde al parámetro *lpCmdLine* pasado `WinMain`por Windows a .

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>Observaciones

Apunta a una cadena terminada en null que especifica la línea de comandos de la aplicación. Se `m_lpCmdLine` utiliza para tener acceso a los argumentos de línea de comandos que el usuario introdujo cuando se inició la aplicación. `m_lpCmdLine`es una variable pública de tipo LPTSTR.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappm_nautosaveinterval"></a><a name="m_nautosaveinterval"></a>CWinApp::m_nAutosaveInterval

La longitud de tiempo en milisegundos entre los guardados automáticos.

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>Observaciones

Puede configurar el gestor de reinicio para guardar automáticamente los documentos abiertos a intervalos establecidos. Si la aplicación no guarda archivos automáticamente, este parámetro no tiene ningún efecto.

## <a name="cwinappm_ncmdshow"></a><a name="m_ncmdshow"></a>CWinApp::m_nCmdShow

Corresponde al parámetro *nCmdShow* pasado `WinMain`por Windows a .

```
int m_nCmdShow;
```

### <a name="remarks"></a>Observaciones

Debe pasar `m_nCmdShow` como argumento cuando se llama a [CWnd::ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) para la ventana principal de la aplicación. `m_nCmdShow`es una variable pública de tipo **int**.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

## <a name="cwinappm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinApp::m_pActiveWnd

Utilice este miembro de datos para almacenar un puntero a la ventana principal de la aplicación contenedora OLE que tiene activada la aplicación de servidor OLE en contexto.

### <a name="remarks"></a>Observaciones

Si este miembro de datos es NULL, la aplicación no está activa en su lugar.

El marco de trabajo establece esta variable miembro cuando la ventana de marco está activada en contexto por una aplicación contenedora OLE.

## <a name="cwinappm_pdatarecoveryhandler"></a><a name="m_pdatarecoveryhandler"></a>CWinApp::m_pDataRecoveryHandler

Puntero al controlador de recuperación de datos para la aplicación.

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>Observaciones

El controlador de recuperación de datos de una aplicación supervisa los documentos abiertos y los guarda automáticamente. El marco de trabajo usa el controlador de recuperación de datos para restaurar archivos guardados automáticamente cuando una aplicación se reinicia después de que se cierra inesperadamente. Para obtener más información, vea [CDataRecoveryHandler (Clase)](../../mfc/reference/cdatarecoveryhandler-class.md).

## <a name="cwinappm_pszappname"></a><a name="m_pszappname"></a>CWinApp::m_pszAppName

Especifica el nombre de la aplicación.

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>Observaciones

El nombre de la aplicación puede provenir del parámetro pasado al constructor [CWinApp](#cwinapp) o, si no se especifica, a la cadena de recursos con el identificador de AFX_IDS_APP_TITLE. Si el nombre de la aplicación no se encuentra en el recurso, procede del programa . EXE nombre de archivo.

Devuelta por la función global [AfxGetAppName](application-information-and-management.md#afxgetappname). `m_pszAppName`es una variable pública de tipo **const char**<strong>\*</strong>.

> [!NOTE]
> Si asigna un `m_pszAppName`valor a , debe asignarse dinámicamente en el montón. El `CWinApp` destructor llama **a free**( ) con este puntero. Muchos desean utilizar `_tcsdup`la función de biblioteca en tiempo de ejecución ( ) para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

## <a name="cwinappm_pszexename"></a><a name="m_pszexename"></a>CWinApp::m_pszExeName

Contiene el nombre del archivo ejecutable de la aplicación sin extensión.

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>Observaciones

A diferencia [de m_pszAppName](#m_pszappname), este nombre no puede contener espacios en blanco. `m_pszExeName`es una variable pública de tipo **const char**<strong>\*</strong>.

> [!NOTE]
> Si asigna un `m_pszExeName`valor a , debe asignarse dinámicamente en el montón. El `CWinApp` destructor llama **a free**( ) con este puntero. Muchos desean utilizar `_tcsdup`la función de biblioteca en tiempo de ejecución ( ) para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

## <a name="cwinappm_pszhelpfilepath"></a><a name="m_pszhelpfilepath"></a>CWinApp::m_pszHelpFilePath

Contiene la ruta de acceso al archivo de Ayuda de la aplicación.

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, `m_pszHelpFilePath` el marco de trabajo se inicializa en el nombre de la aplicación con ". HLP" anexado. Para cambiar el nombre del `m_pszHelpFilePath` archivo de ayuda, establezca para que apunte a una cadena que contenga el nombre completo del archivo de ayuda deseado. Un lugar conveniente para hacer esto es en la función [InitInstance](#initinstance) de la aplicación. `m_pszHelpFilePath`es una variable pública de tipo **const char**<strong>\*</strong>.

> [!NOTE]
> Si asigna un `m_pszHelpFilePath`valor a , debe asignarse dinámicamente en el montón. El `CWinApp` destructor llama **a free**( ) con este puntero. Muchos desean utilizar `_tcsdup`la función de biblioteca en tiempo de ejecución ( ) para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

## <a name="cwinappm_pszprofilename"></a><a name="m_pszprofilename"></a>CWinApp::m_pszProfileName

Contiene el nombre de la aplicación . Archivo INI.

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>Observaciones

`m_pszProfileName`es una variable pública de tipo **const char**<strong>\*</strong>.

> [!NOTE]
> Si asigna un `m_pszProfileName`valor a , debe asignarse dinámicamente en el montón. El `CWinApp` destructor llama **a free**( ) con este puntero. Muchos desean utilizar `_tcsdup`la función de biblioteca en tiempo de ejecución ( ) para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

## <a name="cwinappm_pszregistrykey"></a><a name="m_pszregistrykey"></a>CWinApp::m_pszRegistryKey

Se utiliza para determinar dónde se almacenan, en el registro o en el archivo INI, la configuración del perfil de aplicación.

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>Observaciones

Normalmente, este miembro de datos se trata como de solo lectura.

- El valor se almacena en una clave del Registro. El nombre de la configuración del perfil de aplicación se anexa a la siguiente clave del Registro: HKEY_CURRENT_USER/Software/LocalAppWizard-Generated/.

Si asigna un `m_pszRegistryKey`valor a , debe asignarse dinámicamente en el montón. El `CWinApp` destructor llama **a free**( ) con este puntero. Muchos desean utilizar `_tcsdup`la función de biblioteca en tiempo de ejecución ( ) para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

## <a name="cwinappm_pszappid"></a><a name="m_pszappid"></a>CWinApp::m_pszAppID

ID de modelo de usuario de aplicación.

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>Observaciones

## <a name="cwinapponcontexthelp"></a><a name="oncontexthelp"></a>CwinApp::OnContextHelp

Controla la Ayuda de SHIFT+F1 dentro de la aplicación.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Observaciones

Debe agregar `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` una instrucción al mapa de mensajes de `CWinApp` clase y también agregar una entrada de tabla de aceleradores, normalmente SHIFT+F1, para habilitar esta función miembro.

`OnContextHelp`pone la aplicación en modo de ayuda. El cursor cambia a una flecha y un signo de interrogación, y el usuario puede mover el puntero del ratón y presionar el botón izquierdo del ratón para seleccionar un cuadro de diálogo, ventana, menú o botón de comando. Esta función miembro recupera el contexto de Ayuda del objeto bajo el cursor y llama a la función de Windows WinHelp con ese contexto de Ayuda.

## <a name="cwinapponddecommand"></a><a name="onddecommand"></a>CWinApp::OnDDECommand

Llamado por el marco de trabajo cuando la ventana de marco principal recibe un mensaje de ejecución DDE.

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>Parámetros

*lpszCommand*<br/>
Apunta a una cadena de comandos DDE recibida por la aplicación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se controla el comando; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada comprueba si el comando es una solicitud para abrir un documento y, si es así, abre el documento especificado. El Administrador de archivos de Windows normalmente envía estas cadenas de comandos DDE cuando el usuario hace doble clic en un archivo de datos. Reemplace esta función para controlar otros comandos de ejecución de DDE, como el comando que se va a imprimir.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

## <a name="cwinapponfilenew"></a><a name="onfilenew"></a>Cwinapp::OnFileNew

Implementa el comando ID_FILE_NEW.

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>Observaciones

Debe agregar `ON_COMMAND( ID_FILE_NEW, OnFileNew )` una instrucción al mapa de mensajes de `CWinApp` clase para habilitar esta función miembro. Si está habilitada, esta función controla la ejecución del comando Archivo nuevo.

Consulte [la Nota técnica 22](../../mfc/tn022-standard-commands-implementation.md) para obtener información sobre el comportamiento predeterminado y instrucciones sobre cómo invalidar esta función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileopen"></a><a name="onfileopen"></a>CwinApp::OnFileOpen

Implementa el comando ID_FILE_OPEN.

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>Observaciones

Debe agregar `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` una instrucción al mapa de mensajes de `CWinApp` clase para habilitar esta función miembro. Si está habilitada, esta función controla la ejecución del comando Abrir archivo.

Para obtener información sobre el comportamiento predeterminado y las instrucciones sobre cómo invalidar esta función miembro, vea [Nota técnica 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponfileprintsetup"></a><a name="onfileprintsetup"></a>CWinApp::OnFilePrintSetup

Implementa el comando ID_FILE_PRINT_SETUP.

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>Observaciones

Debe agregar `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` una instrucción al mapa de mensajes de `CWinApp` clase para habilitar esta función miembro. Si está habilitada, esta función controla la ejecución del comando Impresión de archivos.

Para obtener información sobre el comportamiento predeterminado y las instrucciones sobre cómo invalidar esta función miembro, vea [Nota técnica 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

## <a name="cwinapponhelp"></a><a name="onhelp"></a>Cwinapp::OnHelp

Controla la Ayuda de F1 de la aplicación (usando el contexto actual).

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>Observaciones

Por lo general, también agregará una entrada de tecla de aceleración para la tecla F1. Habilitar la clave F1 es solo una convención, no un requisito.

Debe agregar `ON_COMMAND( ID_HELP, OnHelp )` una instrucción al mapa de mensajes de `CWinApp` clase para habilitar esta función miembro. Si está habilitado, llamado por el marco de trabajo cuando el usuario presiona la tecla F1.

La implementación predeterminada de esta función de controlador de mensajes determina el contexto de Ayuda que corresponde a la ventana actual, cuadro de diálogo o elemento de menú y, a continuación, llama a WINHELP. Exe. Si no hay ningún contexto disponible actualmente, la función utiliza el contexto predeterminado.

Invalide esta función miembro para establecer el contexto de Ayuda en algo distinto de la ventana, el cuadro de diálogo, el elemento de menú o el botón de barra de herramientas que actualmente tiene el foco. Llame `WinHelp` con el identificador de contexto de ayuda deseado.

## <a name="cwinapponhelpfinder"></a><a name="onhelpfinder"></a>Cwinapp::OnHelpFinder

Controla los comandos ID_HELP_FINDER y ID_DEFAULT_HELP.

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>Observaciones

Debe agregar `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` una instrucción al mapa de mensajes de `CWinApp` clase para habilitar esta función miembro. Si está habilitado, el marco de trabajo llama a esta función de `WinHelp` controlador de mensajes cuando el usuario de la aplicación selecciona el comando Buscador de ayuda para invocar con el tema **de HELP_FINDER** estándar.

## <a name="cwinapponhelpindex"></a><a name="onhelpindex"></a>CwinApp::OnHelpIndex

Controla el comando ID_HELP_INDEX y proporciona un tema de Ayuda predeterminado.

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>Observaciones

Debe agregar `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` una instrucción al mapa de mensajes de `CWinApp` clase para habilitar esta función miembro. Si está habilitado, el marco de trabajo llama a esta función de `WinHelp` controlador de mensajes cuando el usuario de la aplicación selecciona el comando de índice de ayuda para invocar con el tema **de HELP_INDEX** estándar.

## <a name="cwinapponhelpusing"></a><a name="onhelpusing"></a>Cwinapp::OnHelpUsing

Controla el comando ID_HELP_USING.

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>Observaciones

Debe agregar `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` una instrucción al mapa de mensajes de `CWinApp` clase para habilitar esta función miembro. El marco de trabajo llama a esta función de controlador de `WinHelp` mensajes cuando el usuario de la aplicación selecciona el comando Ayuda a usar para invocar la aplicación con el tema **de HELP_HELPONHELP** estándar.

## <a name="cwinapponidle"></a><a name="onidle"></a>Cwinapp::OnIdle

Invalide esta función miembro para realizar el procesamiento en tiempo de inactividad.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
Se llama a `OnIdle` un contador incrementado cada vez cuando la cola de mensajes de la aplicación está vacía. Este recuento se restablece a 0 cada vez que se procesa un nuevo mensaje. Puede utilizar el parámetro *lCount* para determinar el tiempo relativo durante el que la aplicación ha estado inactiva sin procesar un mensaje.

### <a name="return-value"></a>Valor devuelto

Distinto de cero para recibir más tiempo de procesamiento inactivo; 0 si no se necesita más tiempo de inactividad.

### <a name="remarks"></a>Observaciones

`OnIdle`se llama en el bucle de mensajes predeterminado cuando la cola de mensajes de la aplicación está vacía. Use la invalidación para llamar a sus propias tareas de controlador inactivo en segundo plano.

`OnIdle`debe devolver 0 para indicar que no se requiere ningún tiempo de procesamiento inactivo. El parámetro *lCount* se `OnIdle` incrementa cada vez que se llama cuando la cola de mensajes está vacía y se restablece a 0 cada vez que se procesa un nuevo mensaje. Puede llamar a sus diferentes rutinas de inactividad en función de este recuento.

A continuación se resume el procesamiento de bucle inactivo:

1. Si el bucle de mensajes de la biblioteca Microsoft Foundation Class comprueba `OnIdle` la cola de mensajes y no encuentra ningún mensaje pendiente, llama al objeto de aplicación y proporciona 0 como argumento *lCount.*

2. `OnIdle`realiza algún procesamiento y devuelve un valor distinto de cero para indicar que se debe llamar de nuevo para realizar un procesamiento posterior.

3. El bucle de mensajes comprueba la cola de mensajes de nuevo. Si no hay mensajes `OnIdle` pendientes, vuelve a llamar, incrementando el argumento *lCount.*

4. Finalmente, `OnIdle` termina de procesar todas sus tareas inactivas y devuelve 0. Esto indica al bucle de `OnIdle` mensajes que deje de llamar hasta que se reciba el siguiente mensaje de la cola de mensajes, momento en el que el ciclo inactivo se reinicia con el argumento establecido en 0.

No realice tareas largas durante `OnIdle` porque la `OnIdle` aplicación no puede procesar la entrada del usuario hasta que se devuelve.

> [!NOTE]
> La implementación `OnIdle` predeterminada de los objetos de interfaz de usuario del comando updates, como los elementos de menú y los botones de la barra de herramientas, y realiza la limpieza de la estructura de datos interna. Por lo tanto, si invalida `OnIdle`, debe llamar `CWinApp::OnIdle` con la `lCount` versión invalidada en. En primer lugar, llame a todo el procesamiento `OnIdle` inactivo de clase base (es decir, hasta que la clase base devuelva 0). Si necesita realizar el trabajo antes de que se complete el procesamiento de clase base, revise la implementación de clase base para seleccionar el *lCount* adecuado durante el cual realizar su trabajo.

Si no desea `OnIdle` que se le llame siempre que se recupere un mensaje de la cola de mensajes, puede invalidar [el CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage). Si una aplicación ha establecido un temporizador muy corto, o `OnIdle` si el sistema está enviando el mensaje WM_SYSTIMER, se llamará repetidamente y degradará el rendimiento.

### <a name="example"></a>Ejemplo

Los dos ejemplos siguientes `OnIdle`muestran cómo utilizar . El primer ejemplo procesa dos tareas inactivas mediante el argumento *lCount* para priorizar las tareas. La primera tarea es de alta prioridad, y debe hacerlo siempre que sea posible. La segunda tarea es menos importante y debe realizarse solo cuando hay una larga pausa en la entrada del usuario. Observe la llamada a la `OnIdle`versión de clase base de . El segundo ejemplo administra un grupo de tareas inactivas con diferentes prioridades.

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

## <a name="cwinappopendocumentfile"></a><a name="opendocumentfile"></a>CWinApp::OpenDocumentFile

El marco de trabajo llama a este método para abrir el archivo [CDocument](../../mfc/reference/cdocument-class.md) con nombre para la aplicación.

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
[en] El nombre del archivo que se va a abrir.

*bAddToMRU*<br/>
[en] TRUE indica que el documento es uno de los archivos más recientes; FALSE indica que el documento no es uno de los archivos más recientes.

### <a name="return-value"></a>Valor devuelto

Un puntero `CDocument` a un si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si un documento que tiene ese nombre ya está abierto, la primera ventana de marco que contiene ese documento obtendrá el foco. Si una aplicación admite varias plantillas de documento, el marco de trabajo usa la extensión de nombre de archivo para buscar la plantilla de documento adecuada para intentar cargar el documento. Si se realiza correctamente, la plantilla de documento crea una ventana de marco y una vista para el documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

## <a name="cwinappparsecommandline"></a><a name="parsecommandline"></a>CWinApp::ParseCommandLine

Llame a esta función miembro para analizar la línea de comandos y enviar los parámetros, uno a la vez, a [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam).

```cpp
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parámetros

*rCmdInfo*<br/>
Una referencia a un [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) objeto.

### <a name="remarks"></a>Observaciones

Al iniciar un nuevo proyecto MFC mediante el Asistente para aplicaciones, el Asistente para aplicaciones creará una instancia local `CCommandLineInfo`de , y, a continuación, llamar `ProcessShellCommand` y `ParseCommandLine` en el [InitInstance](#initinstance) función miembro. Una línea de comandos sigue la ruta que se describe a continuación:

1. Después de `InitInstance`crearse en , el `CCommandLineInfo` objeto se pasa a `ParseCommandLine`.

2. `ParseCommandLine`luego `CCommandLineInfo::ParseParam` llama repetidamente, una vez para cada parámetro.

3. `ParseParam`rellena el `CCommandLineInfo` objeto, que se pasa a [ProcessShellCommand](#processshellcommand).

4. `ProcessShellCommand`controla los argumentos y las marcas de la línea de comandos.

Tenga en cuenta `ParseCommandLine` que puede llamar directamente según sea necesario.

Para obtener una descripción de los indicadores de línea de comandos, vea [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).

## <a name="cwinapppretranslatemessage"></a><a name="pretranslatemessage"></a>CWinApp::PreTranslateMessage

Invalidar esta función para filtrar los mensajes de ventana antes de que se distribuyen a las funciones `CWinApp::PreTranslateMessage` de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) La implementación predeterminada realiza la traducción de clave de acelerador, por lo que debe llamar a la función miembro en la versión invalidada.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*Pmsg*<br/>
Puntero a una estructura [MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene el mensaje que se está procesando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el `PreTranslateMessage` mensaje se ha procesado por completo y no se debe procesar más. Cero si el mensaje debe procesarse de la manera normal.

## <a name="cwinappprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinApp::ProcessMessageFilter

La función de enlace del marco de trabajo llama a esta función miembro para filtrar y responder a determinados mensajes de Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*code*<br/>
Especifica un código de enlace. Esta función miembro utiliza el código para determinar cómo procesar *lpMsg.*

*lpMsg*<br/>
Un puntero a una tructura [MSG](/windows/win32/api/winuser/ns-winuser-msg)de Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se procesa el mensaje; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Una función de enlace procesa eventos antes de que se envíen al procesamiento normal de mensajes de la aplicación.

Si invalida esta característica avanzada, asegúrese de llamar a la versión de clase base para mantener el procesamiento de enlaces del marco de trabajo.

## <a name="cwinappprocessshellcommand"></a><a name="processshellcommand"></a>CWinApp::ProcessShellCommand

[InitInstance](#initinstance) llama a esta función miembro para `CCommandLineInfo` aceptar los parámetros pasados desde el objeto identificado por *rCmdInfo*y realizar la acción indicada.

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parámetros

*rCmdInfo*<br/>
Una referencia a un [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el comando shell se procesa correctamente. Si es 0, devuelva FALSE de [InitInstance](#initinstance).

### <a name="remarks"></a>Observaciones

Al iniciar un nuevo proyecto MFC mediante el Asistente para aplicaciones, el Asistente para aplicaciones creará una instancia local de `CCommandLineInfo`, y, a continuación, llamar `ProcessShellCommand` y [ParseCommandLine](#parsecommandline) en la `InitInstance` función miembro. Una línea de comandos sigue la ruta que se describe a continuación:

1. Después de `InitInstance`crearse en , el `CCommandLineInfo` objeto se pasa a `ParseCommandLine`.

2. `ParseCommandLine`a continuación, llama a [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) repetidamente, una vez para cada parámetro.

3. `ParseParam`rellena el `CCommandLineInfo` objeto, que luego se pasa a `ProcessShellCommand`.

4. `ProcessShellCommand`controla los argumentos y las marcas de la línea de comandos.

Los miembros `CCommandLineInfo` de datos del objeto, identificados por [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand), son `CCommandLineInfo` del siguiente tipo enumerado, que se define dentro de la clase.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

Para obtener una breve descripción `CCommandLineInfo::m_nShellCommand`de cada uno de estos valores, consulte .

## <a name="cwinappprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinApp::ProcessWndProcException

El marco de trabajo llama a esta función miembro siempre que el controlador no detecta una excepción iniciada en uno de los controladores de mensajes o comandos de la aplicación.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*e*<br/>
Puntero a una excepción no detectada.

*Pmsg*<br/>
Una tructura [MSG](/windows/win32/api/winuser/ns-winuser-msg)que contiene información sobre el mensaje de Windows que provocó que el marco de trabajo producira una excepción.

### <a name="return-value"></a>Valor devuelto

El valor que se debe devolver a Windows. Normalmente esto es 0L para los mensajes de Windows, 1L ( TRUE) para los mensajes de comando.

### <a name="remarks"></a>Observaciones

No llame a esta función miembro directamente.

La implementación predeterminada de esta función miembro crea un cuadro de mensaje. Si la excepción no detectada se origina con un error de comando de menú, barra de herramientas o acelerador, el cuadro de mensaje muestra un mensaje "Error de comando"; de lo contrario, muestra un mensaje de "Error interno de la aplicación".

Invalide esta función miembro para proporcionar el control global de las excepciones. Solo llame a la funcionalidad base si desea que se muestre el cuadro de mensaje.

## <a name="cwinappregister"></a><a name="register"></a>CWinApp::Registrarse

Realiza las tareas de registro `RegisterShellFileTypes`que no se controlan mediante .

```
virtual BOOL Register();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada simplemente devuelve TRUE. Reemplace esta función para proporcionar los pasos de registro personalizados.

## <a name="cwinappregistershellfiletypes"></a><a name="registershellfiletypes"></a>CWinApp::RegisterShellFileTypes

Llame a esta función miembro para registrar todos los tipos de documentode sla aplicación con el Administrador de archivos de Windows.

```cpp
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>Parámetros

*bCompat*<br/>
[en] TRUE agrega entradas de registro para los comandos de shell Imprimir e Imprimir en, lo que permite al usuario imprimir archivos directamente desde el shell o arrastrando el archivo a un objeto de impresora. También agrega una clave DefaultIcon. De forma predeterminada, este parámetro es FALSE para la compatibilidad con versiones anteriores.

### <a name="remarks"></a>Observaciones

Esto permite al usuario abrir un archivo de datos creado por la aplicación haciendo doble clic en él desde el Administrador de archivos. Llame `RegisterShellFileTypes` después de llamar a [AddDocTemplate](#adddoctemplate) para cada una de las plantillas de documento de la aplicación. También llame a la [EnableShellOpen](#enableshellopen) función miembro cuando se llama a `RegisterShellFileTypes`.

`RegisterShellFileTypes`Recorre en iteración la lista de [objetos CDocTemplate](../../mfc/reference/cdoctemplate-class.md) que la aplicación mantiene y, para cada plantilla de documento, agrega entradas a la base de datos de registro que Windows mantiene para las asociaciones de archivos. El Administrador de archivos utiliza estas entradas para abrir un archivo de datos cuando el usuario hace doble clic en él. Esto elimina la necesidad de enviar un archivo . REG con su aplicación.

> [!NOTE]
> `RegisterShellFileTypes`sólo funciona si el usuario ejecuta el programa con derechos de administrador. Si el programa no tiene derechos de administrador, no puede modificar las claves del Registro.

Si la base de datos de registro ya asocia una extensión de nombre de archivo determinada con otro tipo de archivo, no se crea ninguna asociación nueva. Consulte `CDocTemplate` la clase para conocer el formato de cadenas necesariopara registrar esta información.

## <a name="cwinappregisterwithrestartmanager"></a><a name="registerwithrestartmanager"></a>CWinApp::RegisterWithRestartManager

Registra la aplicación con el administrador de reinicio.

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
|*bRegisterRecoveryCallback*|[en] TRUE indica que esta instancia de la aplicación utiliza una función de devolución de llamada de recuperación; FALSE indica que no lo hace. El marco de trabajo llama a la función de devolución de llamada de recuperación cuando la aplicación se cierra inesperadamente. Para obtener más información, vea [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*strRestartIdentifier*|[en] Cadena única que identifica esta instancia del administrador de reinicio. El identificador del administrador de reinicio es único para cada instancia de una aplicación.|
|*pwzCommandLineArgs*|[en] Cadena que contiene argumentos adicionales de la línea de comandos.|
|*dwRestartFlags*|[en] Marcas opcionales para el administrador de reinicio. Para obtener más información, vea la sección Comentarios.|
|*pRecoveryCallback*|[en] La función de devolución de llamada de recuperación. Esta función debe tomar un parámetro LPVOID como entrada y devolver un DWORD. La función de `CWinApp::ApplicationRecoveryCallback`devolución de llamada de recuperación predeterminada es .|
|*lpvParam*|[en] El parámetro de entrada para la función de devolución de llamada de recuperación. Para obtener más información, vea [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|*dwPingInterval*|[en] El tiempo que el Administrador de reinicio espera a que se devuelva la función de devolución de llamada de recuperación. Este parámetro está en milisegundos.|
|*dwCallbackFlags*|[en] Indicadores pasados a la función de devolución de llamada de recuperación. Reservado para uso futuro.|

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

Si la aplicación utiliza la implementación de MFC predeterminada para `RegisterWithRestartManager`guardar archivos automáticamente, debe usar la versión simple de . Utilice la versión compleja de `RegisterWithRestartManager` si desea personalizar el comportamiento de guardado automático de la aplicación.

Si llama a este método con una cadena `RegisterWithRestartManager` vacía para *strRestartIdentifier*, crea una cadena de identificador único para esta instancia del Administrador de reinicio.

Cuando una aplicación se cierra inesperadamente, el Administrador de reinicio reinicia la aplicación desde la línea de comandos y proporciona el identificador de reinicio único como argumento opcional. En este escenario, `RegisterWithRestartManager` el marco de trabajo llama dos veces. La primera llamada proviene de [CWinApp::InitInstance](#initinstance) con una cadena vacía para el identificador de cadena. A continuación, el método [CWinApp::ProcessShellCommand](#processshellcommand) llama `RegisterWithRestartManager` con el identificador de reinicio único.

Después de registrar una aplicación con el Administrador de reinicio, el Administrador de reinicio supervisa la aplicación. Si la aplicación se cierra inesperadamente, el administrador de reinicio llama a la función de devolución de llamada de recuperación durante el proceso de apagado. El Administrador de reinicio espera *dwPingInterval* para obtener una respuesta de la función de devolución de llamada de recuperación. Si la función de devolución de llamada de recuperación no responde dentro de este tiempo, la aplicación se cierra sin ejecutar la función de devolución de llamada de recuperación.

De forma predeterminada, dwRestartFlags no se admite, pero se proporcionan para su uso futuro. Los valores posibles para *dwRestartFlags* son los siguientes:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

## <a name="cwinappreopenpreviousfilesatrestart"></a><a name="reopenpreviousfilesatrestart"></a>CWinApp::ReopenPreviousFilesAtRestart

Determina si el administrador de reinicio vuelve a abrir los archivos que estaban abiertos cuando la aplicación se salió inesperadamente.

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el administrador de reinicio vuelve a abrir los archivos abiertos anteriormente; FALSE indica que el administrador de reinicio no lo hace.

## <a name="cwinapprestartinstance"></a><a name="restartinstance"></a>CWinApp::RestartInstance

Controla un reinicio de la aplicación iniciado por el Administrador de reinicio.

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>Valor devuelto

TRUESi el controlador de recuperación de datos abre documentos abiertos anteriormente; FALSE si el controlador de recuperación de datos tiene un error o si no hay documentos abiertos previamente.

### <a name="remarks"></a>Observaciones

Cuando el Administrador de reinicio reinicia una aplicación, el marco de trabajo llama a este método. Este método recupera el controlador de recuperación de datos y restaura los archivos guardados automáticamente. Este método llama a [CDataRecoveryHandler::RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) para determinar si el usuario desea restaurar los archivos guardados automáticamente.

Este método devuelve FALSE si el [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) determina que no había documentos abiertos. Si no había documentos abiertos, la aplicación se inicia normalmente.

## <a name="cwinapprestoreautosavedfilesatrestart"></a><a name="restoreautosavedfilesatrestart"></a>CWinApp::RestoreAutosavedFilesAtRestart

Determina si el Administrador de reinicio restaura los archivos guardados automáticamente cuando reinicia la aplicación.

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el administrador de reinicio restaura los archivos guardados automáticamente; FALSE indica que el administrador de reinicio no lo hace.

## <a name="cwinapprun"></a><a name="run"></a>CWinApp::Ejecutar

Proporciona un bucle de mensajes predeterminado.

```
virtual int Run();
```

### <a name="return-value"></a>Valor devuelto

Un valor **int** devuelto `WinMain`por .

### <a name="remarks"></a>Observaciones

`Run`adquiere y distribuye mensajes de Windows hasta que la aplicación recibe un mensaje de WM_QUIT. Si la cola de mensajes de `Run` la aplicación no contiene actualmente ningún mensaje, llama a [OnIdle](#onidle) para realizar el procesamiento en tiempo de inactividad. Los mensajes entrantes van a la [PreTranslateMessage](#pretranslatemessage) función `TranslateMessage` miembro para el procesamiento especial y, a continuación, a la función de Windows para la traducción de teclado estándar; finalmente, `DispatchMessage` se llama a la función de Windows.

`Run`rara vez se invalida, pero puede invalidarlo para proporcionar un comportamiento especial.

## <a name="cwinapprunautomated"></a><a name="runautomated"></a>CWinApp::RunAutomated

Llame a esta función para determinar si la opción " **/Automation**" o " **-Automation**" está presente, lo que indica si la aplicación de servidor se inició mediante una aplicación cliente.

```
BOOL RunAutomated();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró la opción; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si está presente, la opción se elimina de la línea de comandos. Para obtener más información sobre la automatización OLE, vea el artículo Servidores de [automatización](../../mfc/automation-servers.md).

## <a name="cwinapprunembedded"></a><a name="runembedded"></a>CWinApp::RunEmbedded

Llame a esta función para determinar si la opción " **/Embedding**" o " **-Embedding**" está presente, lo que indica si la aplicación de servidor se inició mediante una aplicación cliente.

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró la opción; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si está presente, la opción se elimina de la línea de comandos. Para obtener más información sobre la incrustación, vea el artículo [Servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).

## <a name="cwinappsaveallmodified"></a><a name="saveallmodified"></a>CWinApp::SaveAllModified

Llamado por el marco de trabajo para guardar todos los documentos cuando se va a cerrar la ventana de marco principal de la aplicación, o a través de un mensaje de WM_QUERYENDSESSION.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es seguro terminar la aplicación; 0 si no es seguro terminar la aplicación.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función miembro llama a la [CDocument::SaveModified](../../mfc/reference/cdocument-class.md#savemodified) función miembro a su vez para todos los documentos modificados dentro de la aplicación.

## <a name="cwinappselectprinter"></a><a name="selectprinter"></a>CWinApp::SelectPrinter

Llame a esta función miembro para seleccionar una impresora específica y suelte la impresora que se seleccionó anteriormente en el cuadro de diálogo Imprimir.

```cpp
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>Parámetros

*hDevNames*<br/>
Identificador de una referencia [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)que identifica los nombres de controlador, dispositivo y puerto de salida de una impresora específica.

*hDevMode*<br/>
Identificador de una estructura [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) que especifica información sobre la inicialización del dispositivo y el entorno de una impresora.

*bFreeOld*<br/>
Libera la impresora seleccionada anteriormente.

### <a name="remarks"></a>Observaciones

Si *hDevMode* y *hDevNames* `SelectPrinter` son NULL, utiliza la impresora predeterminada actual.

## <a name="cwinappsethelpmode"></a><a name="sethelpmode"></a>CWinApp::SetHelpMode

Establece el tipo de ayuda de la aplicación.

```cpp
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>Parámetros

*eHelpType*<br/>
Especifica el tipo de ayuda que se va a utilizar. Consulte [CWinApp::m_eHelpType](#m_ehelptype) para obtener más información.

### <a name="remarks"></a>Observaciones

Establece el tipo de Ayuda de la aplicación.

Para establecer el tipo de Ayuda de la aplicación en HTMLHelp, puede llamar a [EnableHTMLHelp](#enablehtmlhelp). Una vez `EnableHTMLHelp`que se llama a , la aplicación debe usar HTMLHelp como su aplicación de ayuda. Si desea cambiar para usar WinHelp, `SetHelpMode` puede llamar y `afxWinHelp`establecer *eHelpType* en .

## <a name="cwinappsetregistrykey"></a><a name="setregistrykey"></a>CWinApp::SetRegistryKey

Hace que la configuración de la aplicación se almacene en el registro en lugar de en los archivos INI.

```cpp
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>Parámetros

*lpszRegistryKey*<br/>
Puntero a una cadena que contiene el nombre de la clave.

*nIDRegistryKey*<br/>
ID de un recurso de cadena que contiene el nombre de la clave del Registro.

### <a name="remarks"></a>Observaciones

Esta función establece *m_pszRegistryKey*, `GetProfileInt`que, a continuación, se utilizan en las `GetProfileString`funciones , `WriteProfileInt`, , y `WriteProfileString` miembro de `CWinApp`. Si se ha llamado a esta función, la lista de archivos más utilizados (MRU) también se almacena en el registro. La clave del Registro suele ser el nombre de una empresa. Se almacena en una clave del siguiente\\ formulario:\> \\ HKEY_CURRENT_USER,Software\> \\<\> \\ nombre de\>la empresa<nombre de la aplicación<nombre de la sección<nombre de valor.

## <a name="cwinappsupportsapplicationrecovery"></a><a name="supportsapplicationrecovery"></a>CWinApp::SupportsApplicationRecovery

Determina si el Administrador de reinicio recupera una aplicación que se ha salido inesperadamente.

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el administrador de reinicio recupera la aplicación; FALSE indica que el administrador de reinicio no lo hace.

## <a name="cwinappsupportsautosaveatinterval"></a><a name="supportsautosaveatinterval"></a>CWinApp::SupportsAutosaveAtInterval

Determina si el gestor de reinicio guarda automáticamente los documentos abiertos a intervalos regulares.

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el gestor de reinicio guarda automáticamente los documentos abiertos; FALSE indica que el administrador de reinicio no lo hace.

## <a name="cwinappsupportsautosaveatrestart"></a><a name="supportsautosaveatrestart"></a>CWinApp::SupportsAutosaveAtRestart

Determina si el administrador de reinicio guarda automáticamente los documentos abiertos cuando se reinicia la aplicación.

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el administrador de reinicio guarda automáticamente los documentos abiertos cuando se reinicia la aplicación; FALSE indica que el administrador de reinicio no lo hace.

## <a name="cwinappsupportsrestartmanager"></a><a name="supportsrestartmanager"></a>CWinApp::SupportsRestartManager

Determina si la aplicación admite el Administrador de reinicio.

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que la aplicación admite el Administrador de reinicio; FALSE indica que la aplicación no lo hace.

## <a name="cwinappunregister"></a><a name="unregister"></a>CWinApp::Unregister

Anula el registro de todos los archivos registrados por el objeto de aplicación.

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Observaciones

La `Unregister` función deshace el registro realizado por el objeto de aplicación y la función [Register.](#register) Normalmente, MFC llama implícitamente a ambas funciones y, por lo tanto, no aparecerá en el código.

Invalide esta función para realizar pasos de anulación de registro personalizados.

## <a name="cwinappunregistershellfiletypes"></a><a name="unregistershellfiletypes"></a>CWinApp::UnregisterShellFileTypes

Llame a esta función miembro para anular el registro de todos los tipos de documento de la aplicación con el Administrador de archivos de Windows.

```cpp
void UnregisterShellFileTypes();
```

## <a name="cwinappwinhelp"></a><a name="winhelp"></a>CWinApp::WinHelp

Llame a esta función miembro para invocar la aplicación WinHelp.

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>Parámetros

*dwData*<br/>
Especifica datos adicionales. El valor utilizado depende del valor del parámetro *nCmd.*

*nCmd*<br/>
Especifica el tipo de ayuda solicitado. Para obtener una lista de los valores posibles y cómo afectan al parámetro *dwData,* consulte la función [WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) de Windows.

### <a name="remarks"></a>Observaciones

El marco de trabajo también llama a esta función para invocar la aplicación WinHelp.

El marco de trabajo cerrará automáticamente la aplicación WinHelp cuando finalice la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

## <a name="cwinappwriteprofilebinary"></a><a name="writeprofilebinary"></a>CWinApp::WriteProfileBinary

Llame a esta función miembro para escribir datos binarios en la sección especificada del registro de la aplicación o . Archivo INI.

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>Parámetros

*lpszSection*<br/>
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada. Si la sección no existe, se crea. El nombre de la sección es independiente del caso; la cadena puede ser cualquier combinación de letras mayúsculas y minúsculas.

*lpszEntry*<br/>
Apunta a una cadena terminada en null que contiene la entrada en la que se va a escribir el valor. Si la entrada no existe en la sección especificada, se crea.

*pData*<br/>
Señala los datos que se van a escribir.

*nBytes*<br/>
Contiene el número de bytes que se van a escribir.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

En este `CWinApp* pApp = AfxGetApp();` ejemplo se usa para obtener en la `WriteProfileBinary` `GetProfileBinary` clase CWinApp que ilustra una forma que y se puede usar desde cualquier función de una aplicación MFC.

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileBinary](#getprofilebinary).

## <a name="cwinappwriteprofileint"></a><a name="writeprofileint"></a>CWinApp::WriteProfileInt

Llame a esta función miembro para escribir el valor especificado en la sección especificada del registro de la aplicación o . Archivo INI.

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>Parámetros

*lpszSection*<br/>
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada. Si la sección no existe, se crea. El nombre de la sección es independiente del caso; la cadena puede ser cualquier combinación de letras mayúsculas y minúsculas.

*lpszEntry*<br/>
Apunta a una cadena terminada en null que contiene la entrada en la que se va a escribir el valor. Si la entrada no existe en la sección especificada, se crea.

*nValor*<br/>
Contiene el valor que se va a escribir.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

En este `CWinApp* pApp = AfxGetApp();` ejemplo se usa para obtener en la `WriteProfileString` `WriteProfileInt`clase `GetProfileString`CWinApp que ilustra una forma que , , , y `GetProfileInt` se puede usar desde cualquier función de una aplicación MFC.

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileInt](#getprofileint).

## <a name="cwinappwriteprofilestring"></a><a name="writeprofilestring"></a>CWinApp::WriteProfileString

Llame a esta función miembro para escribir la cadena especificada en la sección especificada del registro de la aplicación o . Archivo INI.

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parámetros

*lpszSection*<br/>
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada. Si la sección no existe, se crea. El nombre de la sección es independiente del caso; la cadena puede ser cualquier combinación de letras mayúsculas y minúsculas.

*lpszEntry*<br/>
Apunta a una cadena terminada en null que contiene la entrada en la que se va a escribir el valor. Si la entrada no existe en la sección especificada, se crea. Si este parámetro es NULL, se elimina la sección especificada por *lpszSection.*

*lpszValue*<br/>
Señala la cadena que se va a escribir. Si este parámetro es NULL, se elimina la entrada especificada por el parámetro *lpszEntry.*

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileInt](#getprofileint).

## <a name="cwinappsetappid"></a><a name="setappid"></a>CWinApp::SetAppID

Establece explícitamente el identificador de modelo de usuario de aplicación para la aplicación. Se debe llamar a este método antes de que se presente al usuario cualquier interfaz de usuario (el mejor lugar es el constructor de la aplicación).

```cpp
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>Parámetros

*lpcszAppID*<br/>
Especifica el identificador del modelo de usuario de aplicación.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[CWinThread (clase)](../../mfc/reference/cwinthread-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Procedimiento para agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md)
