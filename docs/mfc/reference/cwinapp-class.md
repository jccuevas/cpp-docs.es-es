---
title: CWinApp (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c756de90967b4c9178d5e6a584990cc53ad7786c
ms.sourcegitcommit: f923f667065cd6c4203d10ca9520600ee40e5f84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/24/2018
ms.locfileid: "42900943"
---
# <a name="cwinapp-class"></a>CWinApp (clase)

La clase base de la que se deriva un objeto de aplicación Windows.

## <a name="syntax"></a>Sintaxis

```
class CWinApp : public CWinThread
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CWinApp::CWinApp](#cwinapp)|Construye un objeto `CWinApp`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CWinApp:: AddDocTemplate](#adddoctemplate)|Agrega una plantilla de documento a la lista de la aplicación de plantillas de documento disponibles.|
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|Agrega un nombre de archivo a la lista de archivos usa recientemente (MRU).|
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|Lo llama el marco de trabajo cuando la aplicación se cierra inesperadamente.|
|[CWinApp::CloseAllDocuments](#closealldocuments)|Cierra todos los documentos abiertos.|
|[CWinApp::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora.|
|[CWinApp::DelRegTree](#delregtree)|Elimina una clave especificada y todas sus subclaves.|
|[CWinApp::DoMessageBox](#domessagebox)|Implementa [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox) para la aplicación.|
|[CWinApp::DoWaitCursor](#dowaitcursor)|Activa el cursor de espera y desactiva.|
|[CWinApp::EnableD2DSupport](#enabled2dsupport)|Habilita la compatibilidad D2D de aplicación. Llame a este método antes de que se inicialice la ventana principal.|
|[CWinApp::EnableHtmlHelp](#enablehtmlhelp)|Implementa HTMLHelp para la aplicación, en lugar de WinHelp.|
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|Permite la interacción de la barra de tareas.|
|[CWinApp:: ExitInstance](#exitinstance)|Invalide para limpiar cuando finaliza la aplicación.|
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|Recupera el parámetro de entrada para el método de recuperación de la aplicación.|
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|Devuelve la longitud de tiempo que espera el Administrador de reinicio para que la función de devolución de llamada de recuperación devolver.|
|[CWinApp::GetApplicationRestartFlags](#getapplicationrestartflags)|Devuelve las marcas para el Administrador de reinicio.|
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|Devuelve la clave HKEY_CURRENT_USER\\\RegistryKey\ProfileName "Software".|
|[CWinApp::GetDataRecoveryHandler](#getdatarecoveryhandler)|Obtiene el controlador de recuperación de datos para esta instancia de la aplicación.|
|[CWinApp::GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|Recupera la posición de la primera plantilla de documento.|
|[CWinApp::GetHelpMode](#gethelpmode)|Recupera el tipo de ayuda utilizado por la aplicación.|
|[CWinApp::GetNextDocTemplate](#getnextdoctemplate)|Recupera la posición de una plantilla de documento. Puede utilizar de forma recursiva.|
|[CWinApp::GetPrinterDeviceDefaults](#getprinterdevicedefaults)|Recupera los valores predeterminados de dispositivo de impresora.|
|[CWinApp::GetProfileBinary](#getprofilebinary)|Recupera los datos binarios de una entrada en la aplicación. Archivo INI.|
|[CWinApp::GetProfileInt](#getprofileint)|Recupera un entero de una entrada en la aplicación. Archivo INI.|
|[CWinApp::GetProfileString](#getprofilestring)|Recupera una cadena de una entrada en la aplicación. Archivo INI.|
|[CWinApp::GetSectionKey](#getsectionkey)|Devuelve la clave HKEY_CURRENT_USER\\\RegistryKey\AppName\lpszSection "Software".|
|[CWinApp::HideApplication](#hideapplication)|Oculta la aplicación antes de cerrar todos los documentos.|
|[CWinApp::HtmlHelp](#htmlhelp)|Las llamadas del `HTMLHelp` función de Windows.|
|[CWinApp:: InitInstance](#initinstance)|Reemplace este valor para realizar la inicialización de instancia de Windows, como la creación de los objetos de ventana.|
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|Indica si está habilitada la interacción de la barra de tareas de Windows 7.|
|[CWinApp::LoadCursor](#loadcursor)|Carga un recurso de cursor.|
|[CWinApp::LoadIcon](#loadicon)|Carga un recurso de icono.|
|[CWinApp::LoadOEMCursor](#loadoemcursor)|Carga un OEM de Windows predefinida de cursor que el **OCR_** constantes se especifican en WINDOWS. H.|
|[CWinApp::LoadOEMIcon](#loadoemicon)|Carga un icono predefinido de OEM de Windows que el **OIC_** constantes se especifican en WINDOWS. H.|
|[CWinApp::LoadStandardCursor](#loadstandardcursor)|Carga un Windows predefinidos de cursor que el **IDC_** constantes se especifican en WINDOWS. H.|
|[CWinApp::LoadStandardIcon](#loadstandardicon)|Carga un icono predefinido de Windows que el **IDI_** constantes se especifican en WINDOWS. H.|
|[CWinApp::OnDDECommand](#onddecommand)|Llamado por el marco de trabajo en respuesta a los datos dinámicos DDE (intercambio) ejecute el comando.|
|[CWinApp:: OnIdle](#onidle)|Reemplace este valor para realizar el procesamiento de tiempo de inactividad específico de la aplicación.|
|[CWinApp:: OpenDocumentFile](#opendocumentfile)|Lo llama el marco de trabajo para abrir un documento desde un archivo.|
|[CWinApp::ParseCommandLine](#parsecommandline)|Analiza los parámetros individuales y marcas en la línea de comandos.|
|[CWinApp:: PreTranslateMessage](#pretranslatemessage)|Filtra los mensajes antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|Intercepta determinados mensajes antes de llegar a la aplicación.|
|[CWinApp::ProcessShellCommand](#processshellcommand)|Controla las marcas y los argumentos de línea de comandos.|
|[CWinApp::ProcessWndProcException](#processwndprocexception)|Intercepta todas las excepciones no controladas producidas por mensaje de la aplicación y los controladores de comandos.|
|[CWinApp::Register](#register)|Realiza el registro personalizado.|
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|Registra la aplicación con el Administrador de reinicio.|
|[CWinApp::ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|Determina si el Administrador de reinicio, vuelve a abrir los archivos que se abrieron cuando la aplicación se ha cerrado inesperadamente.|
|[CWinApp::RestartInstance](#restartinstance)|Controla el reinicio de una aplicación iniciado por el Administrador de reinicio.|
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|Determina si el Administrador de reinicio restaura los archivos guardados automáticamente cuando esta reinicie la aplicación.|
|[CWinApp:: Run](#run)|Se ejecuta el bucle de mensajes de forma predeterminada. Invalidar para personalizar el bucle de mensajes.|
|[CWinApp::RunAutomated](#runautomated)|Pruebas de línea de comandos de la aplicación para la **/Automation** opción. Obsoleto. En su lugar, use el valor de [CCommandLineInfo::m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated) después de llamar a [ParseCommandLine](#parsecommandline).|
|[CWinApp:: RunEmbedded](#runembedded)|Pruebas de línea de comandos de la aplicación para la **/incrustación** opción. Obsoleto. En su lugar, use el valor de [CCommandLineInfo::m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded) después de llamar a [ParseCommandLine](#parsecommandline).|
|[CWinApp::SaveAllModified](#saveallmodified)|Pide al usuario guardar documentos de todas las modificaciones.|
|[CWinApp::SelectPrinter](#selectprinter)|Selecciona una impresora anteriormente indicada por un usuario a través de un cuadro de diálogo de impresión.|
|[CWinApp::SetHelpMode](#sethelpmode)|Establece e inicializa el tipo de ayuda utilizado por la aplicación.|
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|Determina si el Administrador de reinicio recupera una aplicación que se cerró inesperadamente.|
|[CWinApp::SupportsAutosaveAtInterval](#supportsautosaveatinterval)|Determina si el Administrador de reinicio guarde automáticamente abre documentos a intervalos regulares.|
|[CWinApp::SupportsAutosaveAtRestart](#supportsautosaveatrestart)|Determina si el Administrador de reinicio guarde automáticamente cualquier abrir documentos cuando se reinicia la aplicación.|
|[CWinApp::SupportsRestartManager](#supportsrestartmanager)|Determina si la aplicación admite el Administrador de reinicio.|
|[CWinApp::Unregister](#unregister)|Anula el registro de todo lo que sabe que se ha registrado por el `CWinApp` objeto.|
|[CWinApp:: WinHelp](#winhelp)|Las llamadas del `WinHelp` función de Windows.|
|[CWinApp::WriteProfileBinary](#writeprofilebinary)|Escribe datos binarios en una entrada en la aplicación. Archivo INI.|
|[CWinApp:: Writeprofileint](#writeprofileint)|Escribe un entero a una entrada de la aplicación. Archivo INI.|
|[CWinApp::WriteProfileString](#writeprofilestring)|Escribe una cadena en una entrada en la aplicación. Archivo INI.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CWinApp::EnableShellOpen](#enableshellopen)|Permite al usuario que abra los archivos de datos desde el Administrador de archivos de Windows.|
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|Estándar de carga. Característica de lista de archivos de configuración del archivo .ini y habilita los elementos utilizados Recientemente.|
|[CWinApp::OnContextHelp](#oncontexthelp)|Controla la tecla MAYÚS + F1 Ayuda dentro de la aplicación.|
|[CWinApp::OnFileNew](#onfilenew)|Implementa ID_FILE_NEW (comando).|
|[CWinApp::OnFileOpen](#onfileopen)|Implementa el comando ID_FILE_OPEN.|
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|Implementa ID_FILE_PRINT_SETUP (comando).|
|[CWinApp::OnHelp](#onhelp)|Controla la Ayuda de F1 de la aplicación (usando el contexto actual).|
|[CWinApp::OnHelpFinder](#onhelpfinder)|Controla los comandos ID_HELP_FINDER y ID_DEFAULT_HELP.|
|[CWinApp::OnHelpIndex](#onhelpindex)|Controla el comando ID_HELP_INDEX y proporciona un tema de Ayuda de forma predeterminada.|
|[CWinApp::OnHelpUsing](#onhelpusing)|Controla el ID_HELP_USING (comando).|
|[CWinApp:: RegisterShellFileTypes](#registershellfiletypes)|Tipos de documentos de toda la aplicación se registra con el Administrador de archivos de Windows.|
|[CWinApp::SetAppID](#setappid)|Id. de modelo de aplicación de usuario se establece explícitamente para la aplicación. Este método debe llamarse antes de cualquier interfaz de usuario se presenta al usuario (lo mejor es el constructor de la aplicación).|
|[CWinApp::SetRegistryKey](#setregistrykey)|Hace que se almacenen en el registro en lugar de configuración de la aplicación. Archivos INI.|
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|Anula el registro de tipos de documentos de toda la aplicación con el Administrador de archivos de Windows.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CWinApp::m_bHelpMode](#m_bhelpmode)|Indica si el usuario está en modo de contexto de ayuda (normalmente se invoca con MAYÚS + F1).|
|[CWinApp::m_eHelpType](#m_ehelptype)|Especifica el tipo de ayuda utilizado por la aplicación.|
|[CWinApp::m_hInstance](#m_hinstance)|Identifica la instancia actual de la aplicación.|
|[CWinApp:: M_lpcmdline](#m_lpcmdline)|Apunta a una cadena terminada en null que especifica la línea de comandos para la aplicación.|
|[CWinApp::m_nCmdShow](#m_ncmdshow)|Especifica cómo se muestra inicialmente la ventana.|
|[CWinApp::m_pActiveWnd](#m_pactivewnd)|Puntero a la ventana principal de la aplicación contenedora cuando un servidor OLE en contexto activo.|
|[CWinApp::m_pszAppID](#m_pszappid)|Identificador de modelo de usuario de aplicación.|
|[CWinApp::m_pszAppName](#m_pszappname)|Especifica el nombre de la aplicación.|
|[CWinApp::m_pszExeName](#m_pszexename)|El nombre del módulo de la aplicación.|
|[CWinApp::m_pszHelpFilePath](#m_pszhelpfilepath)|La ruta de acceso al archivo de Ayuda de la aplicación.|
|[CWinApp::m_pszProfileName](#m_pszprofilename)|La aplicación. Nombre de archivo INI.|
|[CWinApp::m_pszRegistryKey](#m_pszregistrykey)|Se utiliza para determinar la clave del registro completo para almacenar la configuración de perfil de aplicación.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|nombre|Descripción|
|----------|-----------------|
|[CWinApp::m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|Marcas que determinan cómo se comporta el Administrador de reinicio.|
|[CWinApp::m_nAutosaveInterval](#m_nautosaveinterval)|El período de tiempo en milisegundos entre guarde automáticamente.|
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|Puntero en el controlador de recuperación de datos para la aplicación.|

## <a name="remarks"></a>Comentarios

Un objeto de aplicación proporciona funciones miembro para inicializar la aplicación (y cada instancia de ella) y para ejecutar la aplicación.

Cada aplicación que utiliza Microsoft Foundation classes solo puede contener un objeto derivado de `CWinApp`. Este objeto se crea cuando se crean otros objetos globales de C++ y ya está disponible cuando se llama Windows la `WinMain` función, que se ha proporcionado por la biblioteca Microsoft Foundation Class. Declarar la derivada `CWinApp` objeto en el nivel global.

Al derivar una clase de aplicación de `CWinApp`, invalidar el [InitInstance](#initinstance) función miembro para crear el objeto de ventana principal de la aplicación.

Además el `CWinApp` funciones miembro, la biblioteca Microsoft Foundation Class proporciona las siguientes funciones globales para tener acceso a su `CWinApp` objeto y otra información global:

- [AfxGetApp](application-information-and-management.md#afxgetapp) Obtiene un puntero a la `CWinApp` objeto.

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle) Obtiene un identificador de la instancia actual de la aplicación.

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle) Obtiene un identificador de recursos de la aplicación.

- [AfxGetAppName](application-information-and-management.md#afxgetappname) Obtiene un puntero a una cadena que contiene el nombre de la aplicación. Como alternativa, si tiene un puntero a la `CWinApp` de objeto, utilice `m_pszExeName` para obtener el nombre de la aplicación.

Consulte [CWinApp: la clase de aplicación](../../mfc/cwinapp-the-application-class.md) para obtener más información sobre la `CWinApp` (clase), incluida una descripción general de las siguientes acciones:

- `CWinApp`-derivada código escrito por el Asistente para la aplicación.

- `CWinApp`del rol en la secuencia de ejecución de la aplicación.

- `CWinApp`'s las implementaciones de funciones de miembro predeterminado.

- `CWinApp`de la clave reemplazables.

El `m_hPrevInstance` miembro de datos ya no existe. Para obtener información sobre la detección de una instancia anterior de `CWinApp`, consulte el artículo de Knowledge Base "Cómo identificar un anterior instancia de una aplicación" (KB106385) en [ http://support.microsoft.com/default.aspxscid=kb; en-us; 106385](http://support.microsoft.com/default.aspxscid=kb;en-us;106385).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="adddoctemplate"></a>  CWinApp:: AddDocTemplate

Llame a esta función miembro para agregar una plantilla de documento a la lista de plantillas de documento disponibles que mantiene la aplicación.

```
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>Parámetros

*pTemplate*  
Un puntero a la `CDocTemplate` va a agregar.

### <a name="remarks"></a>Comentarios

Debe agregar todas las plantillas a una aplicación de documento antes de llamar a [RegisterShellFileTypes](#registershellfiletypes).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

##  <a name="addtorecentfilelist"></a>  CWinApp::AddToRecentFileList

Llame a esta función miembro para agregar *lpszPathName* a la lista de archivos de elementos utilizados Recientemente.

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>Parámetros

*lpszPathName*  
Ruta de acceso del archivo.

### <a name="remarks"></a>Comentarios

Debe llamar a la [LoadStdProfileSettings](#loadstdprofilesettings) función miembro para cargar la lista de archivos MRU actual antes de usar esta función miembro.

El marco de trabajo llama a esta función miembro cuando se abre un archivo o se ejecuta el comando Guardar como para guardar un archivo con un nombre nuevo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

##  <a name="applicationrecoverycallback"></a>  CWinApp::ApplicationRecoveryCallback

Lo llama el marco de trabajo cuando la aplicación se cierra inesperadamente.

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>Parámetros

[in] *lpvParam*  
Reservado para un uso futuro.

### <a name="return-value"></a>Valor devuelto

0 si este método se realiza correctamente; distinto de cero si se produce un error.

### <a name="remarks"></a>Comentarios

Si la aplicación es compatible con el Administrador de reinicio, el marco de trabajo llama a esta función cuando la aplicación se cierra inesperadamente.

La implementación predeterminada de `ApplicationRecoveryCallback` usa el `CDataRecoveryHandler` para guardar la lista de documentos actualmente abiertos en el registro. Este método no Autoguardar no todos los archivos.

Para personalizar el comportamiento, reemplace esta función en una derivada [CWinApp (clase)](../../mfc/reference/cwinapp-class.md) o pasar su propio método de recuperación de la aplicación como un parámetro a [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).

##  <a name="closealldocuments"></a>  CWinApp::CloseAllDocuments

Llame a esta función miembro para cerrar todos los documentos abiertos antes de salir.

```
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>Parámetros

*bEndSession*  
Especifica si se finaliza la sesión de Windows. Es TRUE si se finaliza la sesión; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Llame a [HideApplication](#hideapplication) antes de llamar a `CloseAllDocuments`.

##  <a name="createprinterdc"></a>  CWinApp::CreatePrinterDC

Llame a esta función miembro para crear un contexto de dispositivo de impresora (DC) de la impresora seleccionada.

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>Parámetros

*dc*  
Una referencia a un contexto de dispositivo de impresora.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el contexto de dispositivo de impresora se ha creado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

`CreatePrinterDC` Inicializa el contexto de dispositivo que se pasa por referencia, por lo que puede usar para imprimir.

Si la función se realiza correctamente, cuando haya terminado de imprimir, deberá destruir el contexto de dispositivo. Puede permitir que el destructor de la [CDC](../../mfc/reference/cdc-class.md) objeto hacerlo, o puede hacer explícitamente mediante una llamada a [CDC::DeleteDC](../../mfc/reference/cdc-class.md#deletedc).

##  <a name="cwinapp"></a>  CWinApp::CWinApp

Construye un `CWinApp` objeto y pasa *lpszAppName* que se almacenará como el nombre de la aplicación.

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszAppName*  
Una cadena terminada en null que contiene el nombre de la aplicación que usa Windows. Si este argumento no se proporciona o es NULL, `CWinApp` usa la cadena de recurso AFX_IDS_APP_TITLE o el nombre de archivo del archivo ejecutable.

### <a name="remarks"></a>Comentarios

Debe construir un objeto global de su `CWinApp`-clase derivada. Puede tener sólo uno `CWinApp` objeto en la aplicación. El constructor almacena un puntero a la `CWinApp` objeto poder `WinMain` puede llamar a del objeto funciones miembro para inicializar y ejecutar la aplicación.

##  <a name="delregtree"></a>  CWinApp::DelRegTree

Elimina una clave del Registro específica y todas sus subclaves.

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
El nombre de la clave del registro va a eliminar.

*pTM*  
Puntero al objeto CAtlTransactionManager.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es ERROR_SUCCESS. Si se produce un error en la función, el valor devuelto es un código de error distinto de cero definido en Winerror.h.

### <a name="remarks"></a>Comentarios

Llame a esta función para eliminar la clave especificada y sus subclaves.

##  <a name="domessagebox"></a>  CWinApp::DoMessageBox

El marco llama a esta función miembro para implementar un cuadro de mensaje para la función global [AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox).

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>Parámetros

*lpszPrompt*  
Dirección del texto en el cuadro de mensaje.

*nLas*  
El cuadro de mensaje [estilo](../../mfc/reference/styles-used-by-mfc.md#message-box-styles).

*nIDPrompt*  
Un índice en una cadena de contexto de ayuda.

### <a name="return-value"></a>Valor devuelto

Devuelve los mismos valores que `AfxMessageBox`.

### <a name="remarks"></a>Comentarios

No llame a esta función miembro para abrir un cuadro de mensaje; Utilice `AfxMessageBox` en su lugar.

Reemplace esta función miembro para personalizar el procesamiento de toda la aplicación de `AfxMessageBox` llamadas.

##  <a name="dowaitcursor"></a>  CWinApp::DoWaitCursor

Esta función miembro se llama el marco de trabajo para implementar [CWaitCursor](../../mfc/reference/cwaitcursor-class.md), [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor), [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor), y [ CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor).

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>Parámetros

*nCode*  
Si este parámetro es 1, aparece un cursor de espera. Si es 0, se restaura el cursor de espera sin incrementar el recuento de referencias. Si-1, se finaliza el cursor de espera.

### <a name="remarks"></a>Comentarios

El valor predeterminado implementa un cursor de reloj de arena. `DoWaitCursor` mantiene un recuento de referencias. Si es positivo, se muestra el cursor de reloj de arena.

Mientras no llamará normalmente `DoWaitCursor` directamente, podría invalidar esta función miembro para cambiar el cursor de espera o para realizar un procesamiento adicional mientras se muestra el cursor de espera.

Para conocer una manera más fácil, más sencilla de implementar un cursor de espera, utilice `CWaitCursor`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

##  <a name="enabled2dsupport"></a>  CWinApp::EnableD2DSupport

Se requiere Visual Studio 2010 SP1.

Habilita la compatibilidad D2D de aplicación. Llame a este método antes de que se inicialice la ventana principal.

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parámetros

*d2dFactoryType*  
El modelo de subprocesos de la fábrica D2D y los recursos que crea.

*writeFactoryType*  
Un valor que especifica si el objeto de fábrica de escritura se comparten o aislado

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si compatibilidad D2D estaba habilitado, FALSE: de lo contrario

##  <a name="enablehtmlhelp"></a>  CWinApp::EnableHtmlHelp

Llame a esta función miembro desde dentro del constructor de su `CWinApp`-clase derivada para usar HTMLHelp para obtener ayuda de la aplicación.

```
void EnableHtmlHelp();
```

### <a name="remarks"></a>Comentarios

##  <a name="enableshellopen"></a>  CWinApp::EnableShellOpen

Llamar a esta función, normalmente desde su `InitInstance` invalidación para permitir que los usuarios de su aplicación abrir archivos de datos cuando haga doble clic en los archivos desde el Administrador de archivos dentro de Windows.

```
void EnableShellOpen();
```

### <a name="remarks"></a>Comentarios

Llame a la `RegisterShellFileTypes` funciona junto con esta función miembro, o proporcionar una. Archivo REG con la aplicación para el registro manual de tipos de documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

##  <a name="enabletaskbarinteraction"></a>  CWinApp::EnableTaskbarInteraction

Permite la interacción de la barra de tareas.

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar el*  
Especifica si la interacción con la barra de tareas de Windows 7 debe estar habilitada (TRUE) o deshabilitado (FALSE).

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si la interacción de la barra de tareas puede habilitarse o deshabilitarse.

### <a name="remarks"></a>Comentarios

Este método debe llamarse antes de la creación de la ventana principal, en caso contrario declara y devuelve FALSE.

##  <a name="exitinstance"></a>  CWinApp:: ExitInstance

Lo llama el marco de trabajo desde el `Run` para salir de esta instancia de la aplicación de función miembro.

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Valor devuelto

Código de salida de la aplicación; 0 no indica errores, y los valores mayores que 0 indican un error. Este valor se utiliza como el valor devuelto de `WinMain`.

### <a name="remarks"></a>Comentarios

No llame a esta función miembro desde cualquier lugar, pero dentro del `Run` función miembro.

La implementación predeterminada de esta función escribe las opciones de marco de trabajo en la aplicación. Archivo INI. Reemplace esta función para limpiar cuando finaliza la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

##  <a name="getapplicationrecoveryparameter"></a>  CWinApp::GetApplicationRecoveryParameter

Recupera el parámetro de entrada para el método de recuperación de la aplicación.

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>Valor devuelto

El parámetro de entrada predeterminado para el método de recuperación de la aplicación.

### <a name="remarks"></a>Comentarios

El comportamiento predeterminado de esta función devuelve NULL.

Para obtener más información, consulte [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

##  <a name="getapplicationrecoverypinginterval"></a>  CWinApp::GetApplicationRecoveryPingInterval

Devuelve la longitud de tiempo que espera el Administrador de reinicio para que la función de devolución de llamada de recuperación devolver.

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>Valor devuelto

El período de tiempo en milisegundos.

### <a name="remarks"></a>Comentarios

Cuando una aplicación que se registra con la Administrador de reinicio se cierra inesperadamente, la aplicación intenta guardar los documentos abiertos y llama a la función de devolución de llamada de recuperación. La función de devolución de llamada de recuperación predeterminada es [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).

El período de tiempo que espera la función de devolución de llamada de recuperación devolver el marco de trabajo es el intervalo de ping. Puede personalizar el intervalo de ping invalidando `CWinApp::GetApplicationRecoveryPingInterval` o proporcionando un valor personalizado para `RegisterWithRestartManager`.

##  <a name="getapplicationrestartflags"></a>  CWinApp::GetApplicationRestartFlags

Devuelve las marcas para el Administrador de reinicio.

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>Valor devuelto

Marcas para el Administrador de reinicio. La implementación predeterminada devuelve 0.

### <a name="remarks"></a>Comentarios

Las marcas para el Administrador de reinicio no tienen ningún efecto con la implementación predeterminada. Se proporcionan para uso futuro.

Establecer las marcas al registrar la aplicación con el Administrador de reinicio mediante el uso de [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager).

Los valores posibles para las marcas de administrador de reinicio son como sigue:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="getappregistrykey"></a>  CWinApp::GetAppRegistryKey

Devuelve la clave de HKEY_CURRENT_USER\\\RegistryKey\ProfileName "Software".

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*pTM*  
Puntero a un `CAtlTransactionManager` objeto.

### <a name="return-value"></a>Valor devuelto

Clave de aplicación si la función se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

##  <a name="getdatarecoveryhandler"></a>  CWinApp::GetDataRecoveryHandler

Obtiene el controlador de recuperación de datos para esta instancia de la aplicación.

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>Valor devuelto

El controlador de recuperación de datos para esta instancia de la aplicación.

### <a name="remarks"></a>Comentarios

Cada aplicación que utiliza el Administrador de reinicio debe tener una instancia de la [CDataRecoveryHandler (clase)](../../mfc/reference/cdatarecoveryhandler-class.md). Esta clase es responsable de supervisar guardando archivos y documentos abiertos. El comportamiento de la `CDataRecoveryHandler` depende de la configuración del Administrador de reinicio. Para obtener más información, consulte [CDataRecoveryHandler (clase)](../../mfc/reference/cdatarecoveryhandler-class.md).

Este método devuelve NULL en los sistemas operativos anteriores a Windows Vista. El Administrador de reinicio no se admite en sistemas operativos anteriores a Windows Vista.

Si la aplicación no tiene actualmente un controlador de recuperación de datos, este método crea una y devuelve un puntero a él.

##  <a name="getfirstdoctemplateposition"></a>  CWinApp::GetFirstDocTemplatePosition

Obtiene la posición de la primera plantilla de documento en la aplicación.

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor de posición que se puede usar para la iteración o recuperación de objetos de puntero; Es NULL si la lista está vacía.

### <a name="remarks"></a>Comentarios

Use el valor de posición devuelto en una llamada a [GetNextDocTemplate](#getnextdoctemplate) para obtener el primer [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto.

##  <a name="gethelpmode"></a>  CWinApp::GetHelpMode

Recupera el tipo de ayuda utilizado por la aplicación.

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>Valor devuelto

El tipo de ayuda utilizado por la aplicación. Consulte [CWinApp::m_eHelpType](#m_ehelptype) para obtener más información.

##  <a name="getnextdoctemplate"></a>  CWinApp::GetNextDocTemplate

Obtiene la plantilla de documento identificada por *pos*, a continuación, establece *pos* en el valor de posición.

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>Parámetros

*punto de venta*  
Una referencia a un valor de posición devuelto por una llamada anterior a `GetNextDocTemplate` o [funciones miembro GetFirstDocTemplatePosition](#getfirstdoctemplateposition). El valor se actualiza a la siguiente posición de esta llamada.

### <a name="return-value"></a>Valor devuelto

Un puntero a un [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objeto.

### <a name="remarks"></a>Comentarios

Puede usar `GetNextDocTemplate` en un bucle de iteración de avance, si establece la posición inicial con una llamada a `GetFirstDocTemplatePosition`.

Debe asegurarse de que el valor de posición es válido. Si no es válido, se valida la versión de depuración de la biblioteca Microsoft Foundation Class.

Si la plantilla de documento recuperado es el último disponible, a continuación, el nuevo valor de *pos* se establece en NULL.

##  <a name="getprinterdevicedefaults"></a>  CWinApp::GetPrinterDeviceDefaults

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

Recupera los valores predeterminados de impresora actuales de la Windows. Archivo INI según sea necesario, o usan la última configuración de impresora establecida por el usuario en el programa de instalación de impresión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

##  <a name="getprofilebinary"></a>  CWinApp::GetProfileBinary

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
Apunta a un puntero que va a recibir la dirección de los datos.

*pBytes*  
Apunta a un tipo UINT que recibirá el tamaño de los datos (en bytes).

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Esta función miembro no es distingue mayúsculas de minúsculas, por lo que las cadenas en el *lpszSection* y *lpszEntry* parámetros pueden diferir en el caso.

> [!NOTE]
> `GetProfileBinary` asigna un búfer y devuelve su dirección en \* *ppData*. El llamador es responsable de liberar el búfer mediante **delete []**.

> [!IMPORTANT]
> Los datos devueltos por esta función no están terminados en NULL necesariamente y el llamador debe realizar la validación. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

Para obtener un ejemplo adicional, consulte [CWinApp::WriteProfileBinary](#writeprofilebinary).

##  <a name="getprofileint"></a>  CWinApp::GetProfileInt

Llame a esta función miembro para recuperar el valor de un entero de una entrada dentro de una sección especificada del registro o el archivo .INI de la aplicación.

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>Parámetros

*lpszSection*  
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada.

*lpszEntry*  
Apunta a una cadena terminada en NULL que contiene la entrada cuyo valor se va a recuperar.

*nDefault*  
Especifica el valor predeterminado que se devolverá si el marco no puede encontrar la entrada.

### <a name="return-value"></a>Valor devuelto

Valor entero de la cadena que hay a continuación de la entrada especificada si la función se realiza correctamente. El valor devuelto es el valor de la *nDefault* parámetro si la función no encuentra la entrada. El valor devuelto es 0 si el valor correspondiente a la entrada especificada no es un entero.

Esta función miembro admite la notación hexadecimal para el valor del archivo .INI. Cuando se recupera un entero con signo, debe convertir el valor a un **int**.

### <a name="remarks"></a>Comentarios

Esta función miembro no es distingue mayúsculas de minúsculas, por lo que las cadenas en el *lpszSection* y *lpszEntry* parámetros pueden diferir en el caso.

> [!IMPORTANT]
> Los datos devueltos por esta función no están terminados en NULL necesariamente y el llamador debe realizar la validación. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

Para obtener un ejemplo adicional, consulte [CWinApp:: Writeprofileint](#writeprofileint).

##  <a name="getprofilestring"></a>  CWinApp::GetProfileString

Llame a esta función miembro para recuperar la cadena asociada a una entrada de la sección especificada en el registro de la aplicación o. Archivo INI.

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszSection*  
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada.

*lpszEntry*  
Apunta a una cadena terminada en null que contiene la entrada es cuya cadena va a recuperar. Este valor no debe ser NULL.

*lpszDefault*  
Señala el valor de cadena predeterminado para la entrada especificada si la entrada no se encuentra en el archivo de inicialización.

### <a name="return-value"></a>Valor devuelto

El valor devuelto es la cadena de la aplicación. Archivo INI o *lpszDefault* si no se encuentra la cadena. La longitud máxima de cadena admitida por el marco de trabajo es _MAX_PATH. Si *lpszDefault* es NULL, el valor devuelto es una cadena vacía.

### <a name="remarks"></a>Comentarios

> [!IMPORTANT]
> Los datos devueltos por esta función no están terminados en NULL necesariamente y el llamador debe realizar la validación. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileInt](#getprofileint).

##  <a name="getsectionkey"></a>  CWinApp::GetSectionKey

Devuelve la clave de HKEY_CURRENT_USER\\\RegistryKey\AppName\lpszSection "Software".

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>Parámetros

*lpszSection*  
El nombre de la clave que se va a obtener.

*pTM*  
Puntero a un `CAtlTransactionManager` objeto.

### <a name="return-value"></a>Valor devuelto

Clave de sección si la función se realiza correctamente; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

##  <a name="hideapplication"></a>  CWinApp::HideApplication

Llame a esta función miembro para ocultar una aplicación antes de cerrar los documentos abiertos.

```
void HideApplication();
```

##  <a name="htmlhelp"></a>  CWinApp::HtmlHelp

Llame a esta función miembro para invocar la aplicación HTMLHelp.

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>Parámetros

*dwData*  
Especifica datos adicionales. El valor utilizado depende del valor de la *nCmd* parámetro.

*nCmd*  
Especifica el tipo de ayuda solicitado. Para obtener una lista de valores posibles y cómo afectan la *dwData* parámetro, vea el *uCommand* parámetro se describe en acerca de la API de función HTMLHelp en el SDK de Windows.

### <a name="remarks"></a>Comentarios

El marco de trabajo también llama a esta función para invocar la aplicación HTMLHelp.

El marco de trabajo cerrará automáticamente la aplicación HTMLHelp cuando finaliza la aplicación.

##  <a name="initinstance"></a>  CWinApp:: InitInstance

Windows permite que varias copias del mismo programa para ejecutar al mismo tiempo.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización es correcta; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Inicialización de la aplicación conceptualmente se divide en dos secciones: inicialización de la aplicación de un solo uso que se realiza la primera vez el programa se ejecuta y la inicialización de la instancia que se ejecuta cada vez una copia de las ejecuciones de programa, incluida la primera vez. Implementación de .NET framework de `WinMain` llama a esta función.

Invalidar `InitInstance` para inicializar cada nueva instancia de la aplicación que se ejecutan en Windows. Normalmente, invalida `InitInstance` para construir el objeto de ventana principal y establecer el `CWinThread::m_pMainWnd` miembro de datos para que señale a esa ventana. Para obtener más información sobre cómo reemplazar esta función miembro, vea [CWinApp: la clase de aplicación](../../mfc/cwinapp-the-application-class.md).

> [!NOTE]
> Las aplicaciones MFC deben inicializarse como contenedor uniproceso (STA). Si se llama a [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) en su `InitInstance` invalidar, especifique COINIT_APARTMENTTHREADED (en lugar de COINIT_MULTITHREADED). Para obtener más información, vea el artículo PRB: aplicación MFC deja de responder al inicializar la aplicación como un multiproceso apartamento (828643) en [ http://support.microsoft.com/default.aspxscid=kb; en-us; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

##  <a name="istaskbarinteractionenabled"></a>  CWinApp::IsTaskbarInteractionEnabled

Indica si está habilitada la interacción de la barra de tareas de Windows 7.

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si `EnableTaskbarInteraction` se ha llamado y el sistema operativo es Windows 7 o posterior.

### <a name="remarks"></a>Comentarios

Interacción de la barra de tareas significa que aplicación MDI muestra el contenido de elementos secundarios MDI de miniaturas en pestañas independientes que aparecen cuando el puntero del mouse está sobre el botón de barra de tareas de la aplicación.

##  <a name="loadcursor"></a>  CWinApp::LoadCursor

Carga el recurso de cursor con el nombre *lpszResourceName* o especificado por *nIDResource* desde el archivo ejecutable actual.

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*  
Apunta a una cadena terminada en null que contiene el nombre del recurso de cursor. Puede usar un `CString` para este argumento.

*nIDResource*  
Id. de recurso del cursor. Para obtener una lista de recursos, consulte [LoadCursor](http://msdn.microsoft.com/library/windows/desktop/ms648391) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Un identificador de un cursor, si es correcto; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

`LoadCursor` carga el cursor en la memoria sólo si no se han previamente cargado; en caso contrario, recupera un identificador de recurso existente.

Use la [LoadStandardCursor](#loadstandardcursor) o [LoadOEMCursor](#loadoemcursor) función miembro para tener acceso a los cursores predefinidos de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

##  <a name="loadicon"></a>  CWinApp::LoadIcon

Carga el recurso de icono denominado por *lpszResourceName* o especificado por *nIDResource* desde el archivo ejecutable.

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>Parámetros

*lpszResourceName*  
Apunta a una cadena terminada en null que contiene el nombre del recurso de icono. También puede usar un `CString` para este argumento.

*nIDResource*  
Número de Id. del recurso de icono.

### <a name="return-value"></a>Valor devuelto

Un identificador de un icono si es correcto; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

`LoadIcon` carga el icono solo si no se han previamente cargado; en caso contrario, recupera un identificador de recurso existente.

Puede usar el [LoadStandardIcon](#loadstandardicon) o [LoadOEMIcon](#loadoemicon) función miembro para tener acceso a los iconos de Windows predefinidos.

> [!NOTE]
> Esta función miembro llama a la función de la API Win32 [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072), que solo puede cargar un icono cuyo tamaño se ajusta a los valores de métrica de sistema SM_CXICON y SM_CYICON.

##  <a name="loadoemcursor"></a>  CWinApp::LoadOEMCursor

Carga el Windows predefinidos de recurso de cursor especificado por *nIDCursor*.

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>Parámetros

*nIDCursor*  
Un **OCR_** manifiesto el identificador de constante que especifica un cursor predefinido de Windows. Debe tener `#define OEMRESOURCE` antes `#include \<afxwin.h>` para obtener acceso a la **OCR_** constantes en WINDOWS. H.

### <a name="return-value"></a>Valor devuelto

Un identificador de un cursor, si es correcto; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Use la `LoadOEMCursor` o [LoadStandardCursor](#loadstandardcursor) función miembro para tener acceso a los cursores predefinidos de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

##  <a name="loadoemicon"></a>  CWinApp::LoadOEMIcon

Carga el Windows predefinidos especificado por el recurso de icono *nIDIcon*.

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>Parámetros

*nIDIcon*  
Un **OIC_** manifiesto el identificador de constante que especifica un icono de Windows predefinido. Debe tener `#define OEMRESOURCE` antes `#include \<afxwin.h>` para tener acceso a la **OIC_** constantes en WINDOWS. H.

### <a name="return-value"></a>Valor devuelto

Un identificador de un icono si es correcto; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Use la `LoadOEMIcon` o [LoadStandardIcon](#loadstandardicon) función miembro para tener acceso a los iconos de Windows predefinidos.

##  <a name="loadstandardcursor"></a>  CWinApp::LoadStandardCursor

Carga el Windows predefinidos recursos de cursor que *lpszCursorName* especifica.

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>Parámetros

*lpszCursorName*  
Un **IDC_** manifiesto el identificador de constante que especifica un cursor predefinido de Windows. Estos identificadores se definen en WINDOWS. H. La lista siguiente muestran los posibles valores predefinidos y significados para *lpszCursorName*:

- Cursor de flecha IDC_ARROW estándar

- Cursor de inserción de texto IDC_IBEAM estándar

- Cursor de reloj de arena IDC_WAIT usado cuando Windows lleva a cabo una tarea lenta

- Cursor de cruz IDC_CROSS para la selección

- IDC_UPARROW flecha que señala hacia arriba

- IDC_SIZE obsoleto y no compatible; usar IDC_SIZEALL

- IDC_SIZEALL A cuatro flechas. Cursor que se va a utilizar para cambiar el tamaño de una ventana.

- IDC_ICON obsoleto y no admitidos. Utilice IDC_ARROW.

- Flecha de dos puntas IDC_SIZENWSE con termina en la esquina superior izquierda e inferior derecha

- Flecha de dos puntas IDC_SIZENESW con termina en la esquina superior izquierda inferior y derecha

- Flecha de dos puntas IDC_SIZEWE Horizontal

- Flecha de dos puntas IDC_SIZENS Vertical

### <a name="return-value"></a>Valor devuelto

Un identificador de un cursor, si es correcto; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Use la `LoadStandardCursor` o [LoadOEMCursor](#loadoemcursor) función miembro para tener acceso a los cursores predefinidos de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

##  <a name="loadstandardicon"></a>  CWinApp::LoadStandardIcon

Carga el Windows predefinidos de recurso de icono que *lpszIconName* especifica.

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>Parámetros

*lpszIconName*  
Un identificador de constante manifiesto que especifica un icono de Windows predefinido. Estos identificadores se definen en WINDOWS. H. Para obtener una lista de los posibles valores predefinidos y sus descripciones, consulte el *lpIconName* parámetro [LoadIcon](http://msdn.microsoft.com/library/windows/desktop/ms648072) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Un identificador de un icono si es correcto; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Use la `LoadStandardIcon` o [LoadOEMIcon](#loadoemicon) función miembro para tener acceso a los iconos de Windows predefinidos.

##  <a name="loadstdprofilesettings"></a>  CWinApp::LoadStdProfileSettings

Llame a esta función miembro desde el [InitInstance](#initinstance) función miembro para habilitar y cargar la lista de los archivos usados más recientemente (MRU) y la última vista previa de estado.

```
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>Parámetros

*nMaxMRU*  
El número de archivos usados recientemente para realizar un seguimiento.

### <a name="remarks"></a>Comentarios

Si *nMaxMRU* es 0, no se mantendrá ninguna lista MRU.

##  <a name="m_bhelpmode"></a>  CWinApp::m_bHelpMode

TRUE si la aplicación está en modo de contexto de ayuda (convencionalmente se invocó con MAYÚS + F1); en caso contrario, FALSE.

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>Comentarios

En el modo de contexto de ayuda, el cursor se convierte en un signo de interrogación y el usuario puede mover acerca de la pantalla. Examine esta marca si desea implementar un tratamiento especial en el modo de ayuda. `m_bHelpMode` es una variable pública de tipo BOOL.

##  <a name="m_dwrestartmanagersupportflags"></a>  CWinApp::m_dwRestartManagerSupportFlags

Marcas que determinan cómo se comporta el Administrador de reinicio.

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>Comentarios

Para habilitar el Administrador de reinicio, establezca `m_dwRestartManagerSupportFlags` al comportamiento que desee. La siguiente tabla muestra las marcas que están disponibles.

|||
|-|-|
|Marcar|Descripción|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|La aplicación se registra mediante [CWinApp::RegisterWithRestartManager](#registerwithrestartmanager). El Administrador de reinicio es responsable de reinicio de la aplicación si cierra inesperadamente.|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY|La aplicación está registrada con el Administrador de reinicio y el Administrador de reinicio llama a la función de devolución de llamada de recuperación cuando se reinicia la aplicación. La función de devolución de llamada de recuperación predeterminada es [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|Autoguardado esté habilitado y el Administrador de reinicio guarde automáticamente cualquier abrir documentos cuando se reinicia la aplicación.|
|-AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|Autoguardado esté habilitado y el Administrador de reinicio guarde automáticamente cualquier abrir documentos a intervalos regulares. El intervalo se define mediante [CWinApp::m_nAutosaveInterval](#m_nautosaveinterval).|
|-AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|El Administrador de reinicio abre documentos abiertos previamente después de reiniciar la aplicación de una salida inesperada. El [CDataRecoveryHandler (clase)](../../mfc/reference/cdatarecoveryhandler-class.md) controla el almacenamiento de la lista de documentos abiertos y restaurarlos.|
|-AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|El Administrador de reinicio, pide al usuario para restaurar los archivos guardados automáticamente después de reiniciar la aplicación. La `CDataRecoveryHandler` clase consulta al usuario.|
|-AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|La unión de AFX_RESTART_MANAGER_SUPPORT_RESTART AFX_RESTART_MANAGER_SUPPORT_RECOVER y AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES.|
|-AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|La unión de AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL y AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|-AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|La unión de AFX_RESTART_MANAGER_SUPPORT_RESTART, AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES y AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|
|-AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|La unión ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY, AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL, AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES y AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES.|

##  <a name="m_ehelptype"></a>  CWinApp::m_eHelpType

El tipo de este miembro de datos es el tipo enumerado AFX_HELP_TYPE, que se define dentro de la `CWinApp` clase.

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>Comentarios

La enumeración AFX_HELP_TYPE se define como sigue:

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- Para establecer la Ayuda de la aplicación Ayuda HTML, llame a [SetHelpMode](#sethelpmode) y especifique `afxHTMLHelp`.

- Para establecer la Ayuda de la aplicación WinHelp, llame a `SetHelpMode` y especifique `afxWinHelp`.

##  <a name="m_hinstance"></a>  CWinApp::m_hInstance

Corresponde a la *hInstance* parámetro pasado por Windows para `WinMain`.

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>Comentarios

El `m_hInstance` miembro de datos es un identificador de la instancia actual de la aplicación que se ejecutan en Windows. Se devuelve mediante la función global [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle). `m_hInstance` es una variable pública de tipo HINSTANCE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

##  <a name="m_lpcmdline"></a>  CWinApp:: M_lpcmdline

Corresponde a la *lpCmdLine* parámetro pasado por Windows para `WinMain`.

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>Comentarios

Apunta a una cadena terminada en null que especifica la línea de comandos para la aplicación. Use `m_lpCmdLine` para tener acceso a los argumentos de línea de comandos especificado cuando se inicia la aplicación por el usuario. `m_lpCmdLine` es una variable pública de tipo LPTSTR.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="m_nautosaveinterval"></a>  CWinApp::m_nAutosaveInterval

El período de tiempo en milisegundos entre guarde automáticamente.

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>Comentarios

Puede configurar el Administrador de reinicio para Autoguardar de documentos abiertos a intervalos establecidos. Si la aplicación no Autoguardar archivos, este parámetro tiene ningún efecto.

##  <a name="m_ncmdshow"></a>  CWinApp::m_nCmdShow

Corresponde a la *nCmdShow* parámetro pasado por Windows para `WinMain`.

```
int m_nCmdShow;
```

### <a name="remarks"></a>Comentarios

Debería pasar `m_nCmdShow` como argumento al llamar a [CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow) para la ventana principal de la aplicación. `m_nCmdShow` es una variable pública de tipo **int**.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

##  <a name="m_pactivewnd"></a>  CWinApp::m_pActiveWnd

Utilice a este miembro de datos para almacenar un puntero a la ventana principal de la aplicación de contenedor OLE que tiene su OLE server aplicación activa en el contexto.

### <a name="remarks"></a>Comentarios

Si este miembro de datos es NULL, la aplicación no está activo en contexto.

El marco de trabajo establece esta variable miembro cuando la ventana de marco es activado por una aplicación de contenedor OLE en contexto.

##  <a name="m_pdatarecoveryhandler"></a>  CWinApp::m_pDataRecoveryHandler

Puntero en el controlador de recuperación de datos para la aplicación.

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>Comentarios

El controlador de recuperación de datos de una aplicación supervisa los documentos abiertos y guarda ellos. El marco de trabajo usa el controlador de recuperación de datos para restaurar los archivos guardados automáticamente cuando una aplicación se reinicia después de se cierra inesperadamente. Para obtener más información, consulte [CDataRecoveryHandler (clase)](../../mfc/reference/cdatarecoveryhandler-class.md).

##  <a name="m_pszappname"></a>  CWinApp::m_pszAppName

Especifica el nombre de la aplicación.

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>Comentarios

El nombre de la aplicación puede proceder del parámetro pasado a la [CWinApp](#cwinapp) constructor, o bien, si no se especifica, en la cadena de recurso con el Id. de AFX_IDS_APP_TITLE. Si el nombre de la aplicación no se encuentra en el recurso, procede del programa. Nombre del archivo EXE.

Devuelto por la función global [AfxGetAppName](application-information-and-management.md#afxgetappname). `m_pszAppName` es una variable pública de tipo **const char\***.

> [!NOTE]
> Si asigna un valor a `m_pszAppName`, deben asignarse dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Tal vez desee usar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

##  <a name="m_pszexename"></a>  CWinApp::m_pszExeName

Contiene el nombre del archivo ejecutable de la aplicación sin una extensión.

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>Comentarios

A diferencia de [m_pszAppName](#m_pszappname), este nombre no puede contener espacios en blanco. `m_pszExeName` es una variable pública de tipo **const char\***.

> [!NOTE]
> Si asigna un valor a `m_pszExeName`, deben asignarse dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Tal vez desee usar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

##  <a name="m_pszhelpfilepath"></a>  CWinApp::m_pszHelpFilePath

Contiene la ruta de acceso al archivo de Ayuda de la aplicación.

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, el marco de trabajo inicializa `m_pszHelpFilePath` en el nombre de la aplicación con ". HLP"anexado. Para cambiar el nombre del archivo de ayuda, establezca `m_pszHelpFilePath` para que apunte a una cadena que contiene el nombre completo del archivo de Ayuda deseado. Es un lugar conveniente para hacer esto en la aplicación [InitInstance](#initinstance) función. `m_pszHelpFilePath` es una variable pública de tipo **const char\***.

> [!NOTE]
> Si asigna un valor a `m_pszHelpFilePath`, deben asignarse dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Tal vez desee usar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

##  <a name="m_pszprofilename"></a>  CWinApp::m_pszProfileName

Contiene el nombre de la aplicación. Archivo INI.

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>Comentarios

`m_pszProfileName` es una variable pública de tipo **const char\***.

> [!NOTE]
> Si asigna un valor a `m_pszProfileName`, deben asignarse dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Tal vez desee usar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

##  <a name="m_pszregistrykey"></a>  CWinApp::m_pszRegistryKey

Se usa para determinar, en el registro o el archivo. INI, configuración del perfil de aplicación que se almacena.

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>Comentarios

Normalmente, este miembro de datos se trata como de solo lectura.

- El valor se almacena una clave del registro. El nombre de la configuración de perfil de aplicación se anexa a la siguiente clave del registro: HKEY_CURRENT_USER/Software/LocalAppWizard-generado /.

Si asigna un valor a `m_pszRegistryKey`, deben asignarse dinámicamente en el montón. El `CWinApp` llamadas de destructor **libre**() con este puntero. Tal vez desee usar el `_tcsdup`función de biblioteca en tiempo de ejecución () para realizar la asignación. Además, libere la memoria asociada con el puntero actual antes de asignar un nuevo valor. Por ejemplo:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

##  <a name="m_pszappid"></a>  CWinApp::m_pszAppID

Identificador de modelo de usuario de aplicación.

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>Comentarios

##  <a name="oncontexthelp"></a>  CWinApp::OnContextHelp

Controla la tecla MAYÚS + F1 Ayuda dentro de la aplicación.

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Comentarios

Debe agregar una `ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )` instrucción a su `CWinApp` mapa de mensajes de la clase y también agregar una entrada de la tabla de aceleradores, normalmente MAYÚS+F1, para habilitar esta función miembro.

`OnContextHelp` coloca la aplicación en modo de ayuda. El cursor cambia a una flecha y un signo de interrogación y el usuario, a continuación, puede mover el puntero del mouse y presione el botón primario del mouse para seleccionar un cuadro de diálogo, ventana, menú o botón de comando. Esta función miembro recupera el contexto de Ayuda del objeto bajo el cursor y se llama a la función WinHelp de Windows con ese contexto de ayuda.

##  <a name="onddecommand"></a>  CWinApp::OnDDECommand

Lo llama el marco de trabajo cuando la ventana de marco principal recibe un DDE ejecutar mensaje.

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>Parámetros

*lpszCommand*  
Apunta a una cadena de comando DDE recibido por la aplicación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se controló el comando; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada comprueba si el comando es una solicitud para abrir un documento y, en caso afirmativo, abre el documento especificado. El Administrador de archivos de Windows envía normalmente estas cadenas de comandos DDE cuando el usuario hace doble clic en un archivo de datos. Invalide esta función para controlar otro DDE ejecutar comandos, como el comando para imprimir.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

##  <a name="onfilenew"></a>  CWinApp::OnFileNew

Implementa ID_FILE_NEW (comando).

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>Comentarios

Debe agregar una `ON_COMMAND( ID_FILE_NEW, OnFileNew )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, esta función controla la ejecución del comando archivo nuevo.

Consulte [Nota técnica 22](../../mfc/tn022-standard-commands-implementation.md) para obtener información sobre el comportamiento predeterminado e instrucciones sobre cómo reemplazar esta función miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileopen"></a>  CWinApp::OnFileOpen

Implementa el comando ID_FILE_OPEN.

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>Comentarios

Debe agregar una `ON_COMMAND( ID_FILE_OPEN, OnFileOpen )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, esta función controla la ejecución del comando Abrir archivo.

Para obtener información sobre el comportamiento predeterminado e instrucciones sobre cómo reemplazar esta función miembro, vea [Nota técnica 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileprintsetup"></a>  CWinApp::OnFilePrintSetup

Implementa ID_FILE_PRINT_SETUP (comando).

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>Comentarios

Debe agregar una `ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, esta función controla la ejecución del comando archivo imprimir.

Para obtener información sobre el comportamiento predeterminado e instrucciones sobre cómo reemplazar esta función miembro, vea [Nota técnica 22](../../mfc/tn022-standard-commands-implementation.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onhelp"></a>  CWinApp::OnHelp

Controla la Ayuda de F1 de la aplicación (usando el contexto actual).

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>Comentarios

Normalmente, también agregará una entrada de tecla de aceleración para la tecla F1. Habilitación de la tecla F1 es sólo una convención, no es un requisito.

Debe agregar una `ON_COMMAND( ID_HELP, OnHelp )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, lo llama el marco cuando el usuario presiona la tecla F1.

La implementación predeterminada de esta función de controlador de mensajes determina el contexto de ayuda que corresponde a la ventana actual, el cuadro de diálogo o el elemento de menú y, a continuación, llama a WINHELP. EXE. Si no hay ningún contexto está disponible actualmente, la función utiliza el contexto predeterminado.

Reemplace esta función miembro para establecer el contexto de ayuda en algo distinto de la ventana, cuadro de diálogo, elemento de menú o botón de barra de herramientas que actualmente tiene el foco. Llamar a `WinHelp` con deseado le ayudarán a identificador de contexto.

##  <a name="onhelpfinder"></a>  CWinApp::OnHelpFinder

Controla los comandos ID_HELP_FINDER y ID_DEFAULT_HELP.

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>Comentarios

Debe agregar una `ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, el marco llama a esta función de controlador de mensajes cuando el usuario de la aplicación selecciona el comando de Ayuda de buscador para invocar `WinHelp` con el estándar **HELP_FINDER** tema.

##  <a name="onhelpindex"></a>  CWinApp::OnHelpIndex

Controla el comando ID_HELP_INDEX y proporciona un tema de Ayuda de forma predeterminada.

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>Comentarios

Debe agregar una `ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. Si está habilitada, el marco llama a esta función de controlador de mensajes cuando el usuario de la aplicación selecciona el comando de índice de la Ayuda que se invoca `WinHelp` con el estándar **HELP_INDEX** tema.

##  <a name="onhelpusing"></a>  CWinApp::OnHelpUsing

Controla el ID_HELP_USING (comando).

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>Comentarios

Debe agregar una `ON_COMMAND( ID_HELP_USING, OnHelpUsing )` instrucción a su `CWinApp` mapa de mensajes de la clase para habilitar esta función miembro. El marco llama a esta función de controlador de mensajes cuando el usuario de la aplicación selecciona el comando de la Ayuda usando para invocar el `WinHelp` aplicación con el estándar **HELP_HELPONHELP** tema.

##  <a name="onidle"></a>  CWinApp:: OnIdle

Reemplace esta función miembro para llevar a cabo el procesamiento de tiempo de inactividad.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parámetros

*lCount*  
Un contador incrementa cada vez que `OnIdle` se llama cuando la cola de mensajes de la aplicación está vacía. Este recuento se restablece a 0 cada vez que se procesa un mensaje nuevo. Puede usar el *lCount* parámetro para determinar la cantidad relativa de tiempo ha estado inactiva la aplicación sin tener que procesar un mensaje.

### <a name="return-value"></a>Valor devuelto

Distinto de cero para recibir más en tiempo de procesamiento inactivo; 0 si se necesita nada más tiempo de inactividad.

### <a name="remarks"></a>Comentarios

`OnIdle` se llama en el bucle de mensajes de forma predeterminada cuando la cola de mensajes de la aplicación está vacía. Use la invalidación para llamar a su propio fondo de las tareas de controlador de inactividad.

`OnIdle` debería devolver 0 para indicar que no se requiere ningún tiempo de inactividad de procesamiento. El *lCount* parámetro se incrementa cada vez `OnIdle` se llama cuando la cola de mensajes está vacía y se restablece a 0 cada vez que se procesa un mensaje nuevo. Puede llamar a las rutinas de inactividad diferentes según este recuento.

A continuación resume el procesamiento de bucle de inactividad:

1. Si el bucle de mensajes en la biblioteca Microsoft Foundation Class comprueba la cola de mensajes y no busca los mensajes pendientes, llama a `OnIdle` para el objeto de aplicación y proporciona 0 como el *lCount* argumento.

2. `OnIdle` realiza algún procesamiento y devuelve un valor distinto de cero para indicar que se debe llamar nuevamente para realizar su posterior procesamiento.

3. El bucle de mensajes comprueba la cola de mensajes de nuevo. Si no hay mensajes pendientes, llama a `OnIdle` nuevo, incrementar el *lCount* argumento.

4. Finalmente, `OnIdle` termina de procesar todas sus tareas inactivas y devuelve 0. Esto indica que el bucle de mensajes para detener una llamada a `OnIdle` hasta que se recibe el siguiente mensaje de la cola de mensajes, momento en que el ciclo de inactividad se reinicia con el argumento establecido en 0.

No se realizan las tareas largas durante `OnIdle` porque la aplicación no puede procesar la entrada del usuario hasta que `OnIdle` devuelve.

> [!NOTE]
> La implementación predeterminada de `OnIdle` las actualizaciones de objetos de interfaz de usuario como elementos de menú y los botones de barra de herramientas de comandos y realiza la limpieza de la estructura de datos internos. Por lo tanto, si invalida `OnIdle`, debe llamar a `CWinApp::OnIdle` con el `lCount` en la versión invalidada. Llamar primero a la clase base todo el procesamiento en inactividad (es decir, hasta que la clase base `OnIdle` devuelve 0). Si necesita realizar el trabajo antes de que finalice el procesamiento de la clase base, revise la implementación de la clase base para seleccionar el correcto *lCount* durante el que se va a realizar su trabajo.

Si no desea `OnIdle` para que se llamará siempre que un mensaje se recupera de la cola de mensajes, puede invalidar el [CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage). Si una aplicación ha definido un temporizador muy corto, o si el sistema envía el mensaje WM_SYSTIMER, a continuación, `OnIdle` se llamará repetidamente y degradar el rendimiento.

### <a name="example"></a>Ejemplo

Los dos ejemplos siguientes muestran cómo usar `OnIdle`. El primer ejemplo procesa dos tareas inactivas mediante el *lCount* argumento dar prioridad a las tareas. La primera tarea es de alta prioridad, y debe hacerlo siempre que sea posible. La segunda tarea es menos importante y debe realizarse solo cuando hay una pausa larga en la entrada del usuario. Tenga en cuenta la llamada a la versión de la clase base de `OnIdle`. El segundo ejemplo administra un grupo de tareas inactivas con prioridades diferentes.

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

##  <a name="opendocumentfile"></a>  CWinApp:: OpenDocumentFile

El marco llama a este método para abrir la instancia con nombre [CDocument](../../mfc/reference/cdocument-class.md) archivo para la aplicación.

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>Parámetros

[in] *lpszFileName*  
El nombre del archivo que se puede abrir.

[in] *bAddToMRU*  
TRUE indica que el documento es uno de los archivos más recientes; FALSE indica que el documento no es uno de los archivos más recientes.

### <a name="return-value"></a>Valor devuelto

Un puntero a un `CDocument` si es correcto; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

Si un documento con ese nombre ya está abierto, la primera ventana de marco que contiene ese documento obtendrá el foco. Si una aplicación es compatible con varias plantillas de documento, el marco de trabajo usa la extensión de nombre de archivo para buscar la plantilla de documento apropiado para intentar cargar el documento. Si se realiza correctamente, la plantilla de documento, a continuación, crea una ventana de marco y la vista del documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="parsecommandline"></a>  CWinApp::ParseCommandLine

Llame a esta función miembro para analizar la línea de comandos y enviar a los parámetros, una vez [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam).

```
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parámetros

*rCmdInfo*  
Una referencia a un [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) objeto.

### <a name="remarks"></a>Comentarios

Cuando se inicia un nuevo proyecto MFC mediante el Asistente para aplicaciones, el Asistente para aplicaciones creará una instancia local de `CCommandLineInfo`y, a continuación, llame a `ProcessShellCommand` y `ParseCommandLine` en el [InitInstance](#initinstance) función miembro. Una línea de comandos sigue la ruta que se describe a continuación:

1. Después de que se crean en `InitInstance`, `CCommandLineInfo` objeto se pasa a `ParseCommandLine`.

2. `ParseCommandLine` a continuación, llama a `CCommandLineInfo::ParseParam` varias veces, una vez para cada parámetro.

3. `ParseParam` rellena el `CCommandLineInfo` objeto, que, a continuación, se pasa a [ProcessShellCommand](#processshellcommand).

4. `ProcessShellCommand` controla los argumentos de línea de comandos y las marcas.

Tenga en cuenta que puede llamar a `ParseCommandLine` directamente según sea necesario.

Para obtener una descripción de los marcadores de línea de comandos, consulte [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand).

##  <a name="pretranslatemessage"></a>  CWinApp:: PreTranslateMessage

Reemplace esta función para filtrar los mensajes de ventana antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) la implementación predeterminada realiza la tecla de aceleración traducción, por lo que debe llamar el `CWinApp::PreTranslateMessage` función miembro en la versión invalidada.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*pMsg*  
Un puntero a un [MSG](../../mfc/reference/msg-structure1.md) estructura que contiene el mensaje que se va a procesar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el mensaje se haya procesado totalmente en `PreTranslateMessage` y no se puede procesar aún más. Cero si se debe procesar el mensaje de la manera normal.

##  <a name="processmessagefilter"></a>  CWinApp::ProcessMessageFilter

La función de enlace de .NET framework llama a esta función miembro para filtrar y responder a algunos mensajes de Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*Código*  
Especifica un código de enlace. Esta función miembro usa el código para determinar cómo procesar *lpMsg.*

*lpMsg*  
Un puntero a un Windows [MSG](../../mfc/reference/msg-structure1.md) estructura.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se procesa el mensaje; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Una función de enlace procesa los eventos antes de enviarlos al mensaje normal de la aplicación de procesamiento.

Si invalida esta característica avanzada, asegúrese de llamar a la versión de la clase base para mantener el marco de trabajo de procesamiento de enlace.

##  <a name="processshellcommand"></a>  CWinApp::ProcessShellCommand

Esta función miembro llama a [InitInstance](#initinstance) para aceptar los parámetros pasados desde el `CCommandLineInfo` objeto identificado por *rCmdInfo*y llevar a cabo la acción indicada.

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>Parámetros

*rCmdInfo*  
Una referencia a un [CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el comando de shell se procesa correctamente. Si 0, se devuelve FALSE desde [InitInstance](#initinstance).

### <a name="remarks"></a>Comentarios

Cuando se inicia un nuevo proyecto MFC mediante el Asistente para aplicaciones, el Asistente para aplicaciones creará una instancia local de `CCommandLineInfo`y, a continuación, llame a `ProcessShellCommand` y [ParseCommandLine](#parsecommandline) en el `InitInstance` función miembro. Una línea de comandos sigue la ruta que se describe a continuación:

1. Después de que se crean en `InitInstance`, `CCommandLineInfo` objeto se pasa a `ParseCommandLine`.

2. `ParseCommandLine` a continuación, llama a [CCommandLineInfo::ParseParam](../../mfc/reference/ccommandlineinfo-class.md#parseparam) varias veces, una vez para cada parámetro.

3. `ParseParam` rellena el `CCommandLineInfo` objeto, que, a continuación, se pasa a `ProcessShellCommand`.

4. `ProcessShellCommand` controla los argumentos de línea de comandos y las marcas.

Los miembros de datos de la `CCommandLineInfo` objeto, identificado por [CCommandLineInfo::m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand), son del tipo enumerado siguiente, que se define dentro de la `CCommandLineInfo` clase.

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

Para obtener una descripción breve de cada uno de estos valores, consulte `CCommandLineInfo::m_nShellCommand`.

##  <a name="processwndprocexception"></a>  CWinApp::ProcessWndProcException

El marco de trabajo llama a esta función miembro siempre que el controlador no detecta una excepción en uno de los mensajes de la aplicación o los controladores de comandos.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*e*  
Un puntero a una excepción no detectada.

*pMsg*  
Un [MSG](../../mfc/reference/msg-structure1.md) estructura que contiene información sobre el mensaje de windows que ha provocado el marco de trabajo producir una excepción.

### <a name="return-value"></a>Valor devuelto

El valor que se debe devolver a Windows. Normalmente esto es 0L para mensajes de windows, 1L (TRUE) para los mensajes de comandos.

### <a name="remarks"></a>Comentarios

No llame a esta función miembro directamente.

La implementación predeterminada de esta función miembro, crea un cuadro de mensaje. Si la excepción no detectada que se origina con un menú, barra de herramientas o error de comando de acelerador, el cuadro de mensaje muestra un mensaje "Error del comando"; en caso contrario, muestra un mensaje "error interno de la aplicación".

Reemplace esta función miembro para proporcionar un control de excepciones global. Solo llame a la funcionalidad básica si desea que se mostrará el cuadro de mensaje.

##  <a name="register"></a>  CWinApp::Register

Realiza las tareas de registro no controladas por `RegisterShellFileTypes`.

```
virtual BOOL Register();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada simplemente devuelve TRUE. Reemplace esta función para proporcionar los pasos de registro personalizado.

##  <a name="registershellfiletypes"></a>  CWinApp:: RegisterShellFileTypes

Llame a esta función miembro para registrar todos los tipos de documentos de la aplicación con el Administrador de archivos de Windows.

```
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>Parámetros

[in] *bCompat*  
TRUE agrega entradas de registro para los comandos de shell de impresión y de impresión a, permiten al usuario imprimir archivos directamente desde el shell, o bien arrastrando el archivo a un objeto de la impresora. También agrega una clave DefaultIcon. De forma predeterminada, este parámetro es FALSE por compatibilidad con versiones anteriores.

### <a name="remarks"></a>Comentarios

Esto permite al usuario que abra un archivo de datos creado por la aplicación haciendo doble clic en él desde dentro del Administrador de archivos. Llame a `RegisterShellFileTypes` después de llamar a [AddDocTemplate](#adddoctemplate) para cada una de las plantillas de documento en la aplicación. Llamar también a la [EnableShellOpen](#enableshellopen) función de miembro al llamar a `RegisterShellFileTypes`.

`RegisterShellFileTypes` recorre en iteración la lista de [CDocTemplate](../../mfc/reference/cdoctemplate-class.md) objetos que mantiene la aplicación y, por cada plantilla de documento, agrega entradas a la base de datos de registro que Windows mantiene las asociaciones de archivos. Administrador de archivos utiliza estas entradas para abrir un archivo de datos cuando el usuario hace doble clic en él. Esto elimina la necesidad de enviar una. Archivo de registro con la aplicación.

> [!NOTE]
> `RegisterShellFileTypes` solo funciona si el usuario ejecuta el programa con derechos de administrador. Si el programa no tiene derechos de administrador, no puede modificar las claves del registro.

Si la base de datos de registro ya asocia una extensión de nombre de archivo especificado con otro tipo de archivo, no se crea ninguna nueva asociación. Consulte la `CDocTemplate` clase para el formato de cadenas es necesarias registrar esta información.

##  <a name="registerwithrestartmanager"></a>  CWinApp::RegisterWithRestartManager

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
|[in] *bRegisterRecoveryCallback*|TRUE indica que esta instancia de la aplicación usa una función de devolución de llamada de recuperación; FALSE indica que no. El marco de trabajo llama a la función de devolución de llamada de recuperación cuando la aplicación se cierra inesperadamente. Para obtener más información, consulte [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|[in] *strRestartIdentifier*|La cadena única que identifica esta instancia del Administrador de reinicio. El identificador del Administrador de reinicio es único para cada instancia de una aplicación.|
|[in] *pwzCommandLineArgs*|Una cadena que contiene los argumentos adicionales de la línea de comandos.|
|[in] *dwRestartFlags*|Marcas opcionales para el Administrador de reinicio. Para obtener más información, vea la sección Comentarios.|
|[in] *pRecoveryCallback*|La función de devolución de llamada de recuperación. Esta función debe tomar un parámetro LPVOID como entrada y devolver un valor DWORD. La función de devolución de llamada de recuperación predeterminada es `CWinApp::ApplicationRecoveryCallback`.|
|[in] *lpvParam*|El parámetro de entrada para la función de devolución de llamada de recuperación. Para obtener más información, consulte [CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback).|
|[in] *dwPingInterval*|El período de tiempo que espera el Administrador de reinicio para que la función de devolución de llamada de recuperación devolver. Este parámetro está en milisegundos.|
|[in] *dwCallbackFlags*|Marcas se pasan a la función de devolución de llamada de recuperación. Reservado para un uso futuro.|

### <a name="return-value"></a>Valor devuelto

S_OK si el método se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

Si la aplicación utiliza la implementación de MFC de forma predeterminada para los archivos de guardado automático, debe usar la versión simple de `RegisterWithRestartManager`. Use la versión de complejos `RegisterWithRestartManager` si desea personalizar el comportamiento de guardado automático de la aplicación.

Si se llama a este método con una cadena vacía para *strRestartIdentifier*, `RegisterWithRestartManager` crea una cadena de identificador único para esta instancia de reiniciar el administrador.

Cuando una aplicación se cierra inesperadamente, el Administrador de reinicio reinicia la aplicación desde la línea de comandos y proporciona que el único identificador como un argumento opcional de reinicio. En este escenario, el marco llama a `RegisterWithRestartManager` dos veces. La primera llamada procede de [CWinApp:: InitInstance](#initinstance) con una cadena vacía para el identificador de cadena. A continuación, el método [CWinApp::ProcessShellCommand](#processshellcommand) llamadas `RegisterWithRestartManager` con el identificador único de reinicio.

Después de registrar una aplicación con el Administrador de reinicio, el Administrador de reinicio supervisa la aplicación. Si la aplicación se cierra inesperadamente, el Administrador de reinicio llama a la función de devolución de llamada de recuperación durante el proceso de apagado. Espera el Administrador de reinicio el *dwPingInterval* una respuesta de la función de devolución de llamada de recuperación. Si la función de devolución de llamada de recuperación no responde dentro de este tiempo, la aplicación se cierra sin ejecutar la función de devolución de llamada de recuperación.

De forma predeterminada, el dwRestartFlags no se admiten, pero se proporcionan para su uso futuro. Los valores posibles de *dwRestartFlags* son los siguientes:

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="reopenpreviousfilesatrestart"></a>  CWinApp::ReopenPreviousFilesAtRestart

Determina si el Administrador de reinicio, vuelve a abrir los archivos que se abrieron cuando la aplicación se ha cerrado inesperadamente.

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el Administrador de reinicio, vuelve a abrir los archivos abiertos previamente; FALSE indica que el Administrador de reinicio no lo hace.

##  <a name="restartinstance"></a>  CWinApp::RestartInstance

Controla el reinicio de una aplicación iniciado por el Administrador de reinicio.

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>Valor devuelto

TRUE si el controlador de recuperación de datos abre documentos abiertos previamente; FALSE si el controlador de recuperación de datos tiene un error o si no hay ningún documentos abiertos previamente.

### <a name="remarks"></a>Comentarios

Cuando el Administrador de reinicio reinicia una aplicación, el marco llama a este método. Este método recupera el controlador de recuperación de datos y restaura los archivos guardados automáticamente. Este método llama a [CDataRecoveryHandler::RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments) para determinar si el usuario desea restaurar los archivos guardados automáticamente.

Este método devuelve FALSE si el [CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md) determina que no había ningún documento abierto. Si no hubiera ningún documento abierto, la aplicación se inicia normalmente.

##  <a name="restoreautosavedfilesatrestart"></a>  CWinApp::RestoreAutosavedFilesAtRestart

Determina si el Administrador de reinicio restaura los archivos guardados automáticamente cuando esta reinicie la aplicación.

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el Administrador de reinicio restaura los archivos de autoguardado; FALSE indica que el Administrador de reinicio no lo hace.

##  <a name="run"></a>  CWinApp:: Run

Proporciona un bucle de mensajes de forma predeterminada.

```
virtual int Run();
```

### <a name="return-value"></a>Valor devuelto

Un **int** valor devuelto por `WinMain`.

### <a name="remarks"></a>Comentarios

`Run` adquiere y envía mensajes de Windows hasta que la aplicación recibe un mensaje WM_QUIT. Si la cola de mensajes de la aplicación no contiene actualmente ningún mensaje, `Run` llamadas [OnIdle](#onidle) para realizar el procesamiento de tiempo de inactividad. Los mensajes entrantes que se van a la [PreTranslateMessage](#pretranslatemessage) función de miembro para un procesamiento especial y, a continuación, la función Windows `TranslateMessage` para la traducción de teclado estándar; por último, el `DispatchMessage` se llama a la función de Windows.

`Run` casi nunca se reemplaza, pero puede invalidar para proporcionar un comportamiento especial.

##  <a name="runautomated"></a>  CWinApp::RunAutomated

Llame a esta función para determinar si el " **/Automation**"o" **-Automation**" opción está presente, lo que indica si la aplicación de servidor se inició una aplicación cliente.

```
BOOL RunAutomated();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró la opción; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si está presente, se quita la opción de la línea de comandos. Para obtener más información sobre la automatización OLE, vea el artículo [servidores de automatización](../../mfc/automation-servers.md).

##  <a name="runembedded"></a>  CWinApp:: RunEmbedded

Llame a esta función para determinar si el " **/incrustación**"o" **-Embedding**" opción está presente, lo que indica si la aplicación de servidor se inició una aplicación cliente.

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró la opción; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si está presente, se quita la opción de la línea de comandos. Para obtener más información sobre la incrustación, vea el artículo [servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).

##  <a name="saveallmodified"></a>  CWinApp::SaveAllModified

Se llama el marco de trabajo para guardar todos los documentos cuando la ventana de marco principal de la aplicación está a punto de cerrarse o a través de un mensaje WM_QUERYENDSESSION.

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es seguro terminar la aplicación; 0 si no es seguro terminar la aplicación.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función miembro llama a la [CDocument:: SaveModified](../../mfc/reference/cdocument-class.md#savemodified) función miembro a su vez para todos los documentos modificados dentro de la aplicación.

##  <a name="selectprinter"></a>  CWinApp::SelectPrinter

Llame a esta función miembro para seleccionar una impresora específica y suelte la impresora que estaba seleccionada anteriormente en el cuadro de diálogo de impresión.

```
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>Parámetros

*hDevNames*  
Un identificador para un [DEVNAMES](../../mfc/reference/devnames-structure.md) estructura que identifica el controlador, dispositivo y los nombres de puerto de salida de una determinada impresora.

*hDevMode*  
Un identificador para un [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) estructura que especifica información sobre la inicialización del dispositivo y el entorno de una impresora.

*bFreeOld*  
Libera a la impresora seleccionada anteriormente.

### <a name="remarks"></a>Comentarios

Si ambos *hDevMode* y *hDevNames* son NULL, `SelectPrinter` usa la impresora predeterminada actual.

##  <a name="sethelpmode"></a>  CWinApp::SetHelpMode

Establece el tipo de Ayuda de la aplicación.

```
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>Parámetros

*eHelpType*  
Especifica el tipo de ayuda para su uso. Consulte [CWinApp::m_eHelpType](#m_ehelptype) para obtener más información.

### <a name="remarks"></a>Comentarios

Establece el tipo de Ayuda de la aplicación.

Para establecer el tipo de Ayuda de la aplicación HTMLHelp, puede llamar a [EnableHTMLHelp](#enablehtmlhelp). Una vez que llamamos `EnableHTMLHelp`, la aplicación debe utilizar HTMLHelp como su aplicación de ayuda. Si desea cambiar para usar WinHelp, puede llamar a `SetHelpMode` y establecer *eHelpType* a `afxWinHelp`.

##  <a name="setregistrykey"></a>  CWinApp::SetRegistryKey

Hace que la configuración de aplicación que se almacenará en el registro en lugar de archivos INI.

```
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>Parámetros

*lpszRegistryKey*  
Puntero a una cadena que contiene el nombre de la clave.

*nIDRegistryKey*  
Id. de un recurso de cadena que contiene el nombre de la clave del registro.

### <a name="remarks"></a>Comentarios

Esta función establece *m_pszRegistryKey*, que, a continuación, usa el `GetProfileInt`, `GetProfileString`, `WriteProfileInt`, y `WriteProfileString` funciones miembro de `CWinApp`. Si se ha llamado esta función, la lista de usados recientemente (MRU) archivos también se almacena en el registro. La clave del registro suele ser el nombre de una empresa. Se almacena en una clave de la forma siguiente: HKEY_CURRENT_USER\Software\\< nombre de la compañía\>\\< nombre de la aplicación\>\\< nombre de sección\>\\< valor nombre\>.

##  <a name="supportsapplicationrecovery"></a>  CWinApp::SupportsApplicationRecovery

Determina si el Administrador de reinicio recupera una aplicación que se cerró inesperadamente.

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el Administrador de reinicio recupera la aplicación. FALSE indica que el Administrador de reinicio no lo hace.

##  <a name="supportsautosaveatinterval"></a>  CWinApp::SupportsAutosaveAtInterval

Determina si el Administrador de reinicio guarde automáticamente abre documentos a intervalos regulares.

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el Administrador de reinicio guarde automáticamente abre documentos; FALSE indica que el Administrador de reinicio no lo hace.

##  <a name="supportsautosaveatrestart"></a>  CWinApp::SupportsAutosaveAtRestart

Determina si el Administrador de reinicio guarde automáticamente cualquier abrir documentos cuando se reinicia la aplicación.

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que el Administrador de reinicio guarde automáticamente los documentos abiertos cuando se reinicia la aplicación; FALSE indica que el Administrador de reinicio no lo hace.

##  <a name="supportsrestartmanager"></a>  CWinApp::SupportsRestartManager

Determina si la aplicación admite el Administrador de reinicio.

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que la aplicación es compatible con el Administrador de reinicio FALSE indica que la aplicación no lo hace.

##  <a name="unregister"></a>  CWinApp::Unregister

Anula el registro de todos los archivos registrados por el objeto de aplicación.

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero en caso de éxito; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

El `Unregister` función deshace la inscripción realizada por el objeto de aplicación y el [registrar](#register) función. Normalmente, ambas funciones se llaman implícitamente por MFC y, por tanto, no aparecerá en el código.

Reemplace esta función para llevar a cabo los pasos de anulación de registro personalizada.

##  <a name="unregistershellfiletypes"></a>  CWinApp::UnregisterShellFileTypes

Llame a esta función miembro para anular el registro de todos los tipos de documento de la aplicación con el Administrador de archivos de Windows.

```
void UnregisterShellFileTypes();
```

##  <a name="winhelp"></a>  CWinApp:: WinHelp

Llame a esta función miembro para invocar la aplicación WinHelp.

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>Parámetros

*dwData*  
Especifica datos adicionales. El valor utilizado depende del valor de la *nCmd* parámetro.

*nCmd*  
Especifica el tipo de ayuda solicitado. Para obtener una lista de valores posibles y cómo afectan la *dwData* parámetro, vea el [WinHelp](http://msdn.microsoft.com/library/windows/desktop/bb762267) función de Windows.

### <a name="remarks"></a>Comentarios

El marco de trabajo también llama a esta función para invocar la aplicación WinHelp.

El marco de trabajo cerrará automáticamente la aplicación WinHelp cuando finaliza la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

##  <a name="writeprofilebinary"></a>  CWinApp::WriteProfileBinary

Llame a esta función miembro para escribir datos binarios en la sección especificada del registro de la aplicación o. Archivo INI.

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>Parámetros

*lpszSection*  
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada. Si la sección no existe, se crea. El nombre de la sección es el caso independiente; la cadena puede ser cualquier combinación de mayúsculas y minúsculas.

*lpszEntry*  
Apunta a una cadena terminada en null que contiene la entrada en la que el valor es que se va a escribir. Si la entrada no existe en la sección especificada, se crea.

*pData*  
Apunta a los datos se escriban.

*nBytes*  
Contiene el número de bytes que se escribirán.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

Este ejemplo se utiliza `CWinApp* pApp = AfxGetApp();` para obtener la clase CWinApp que ilustra una forma que `WriteProfileBinary` y `GetProfileBinary` puede usarse desde cualquier función en una aplicación MFC.

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileBinary](#getprofilebinary).

##  <a name="writeprofileint"></a>  CWinApp:: Writeprofileint

Llame a esta función miembro para escribir el valor especificado en la sección especificada del registro de la aplicación o. Archivo INI.

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>Parámetros

*lpszSection*  
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada. Si la sección no existe, se crea. El nombre de la sección es el caso independiente; la cadena puede ser cualquier combinación de mayúsculas y minúsculas.

*lpszEntry*  
Apunta a una cadena terminada en null que contiene la entrada en la que el valor es que se va a escribir. Si la entrada no existe en la sección especificada, se crea.

*nvalor*  
Contiene el valor que se va a escribir.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

Este ejemplo se utiliza `CWinApp* pApp = AfxGetApp();` para obtener la clase CWinApp que ilustra una forma que `WriteProfileString`, `WriteProfileInt`, `GetProfileString`, y `GetProfileInt` puede usarse desde cualquier función en una aplicación MFC.

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileInt](#getprofileint).

##  <a name="writeprofilestring"></a>  CWinApp::WriteProfileString

Llame a esta función miembro para escribir la cadena especificada en la sección especificada del registro de la aplicación o. Archivo INI.

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>Parámetros

*lpszSection*  
Apunta a una cadena terminada en NULL que especifica la sección que contiene la entrada. Si la sección no existe, se crea. El nombre de la sección es el caso independiente; la cadena puede ser cualquier combinación de mayúsculas y minúsculas.

*lpszEntry*  
Apunta a una cadena terminada en null que contiene la entrada en la que el valor es que se va a escribir. Si la entrada no existe en la sección especificada, se crea. Si este parámetro es NULL, la sección especificada por *lpszSection* se elimina.

*lpszValue*  
Apunta a la cadena que se va a escribir. Si este parámetro es NULL, la entrada especificada por el *lpszEntry* se elimina el parámetro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

Para obtener otro ejemplo, vea el ejemplo de [CWinApp::GetProfileInt](#getprofileint).

##  <a name="setappid"></a>  CWinApp::SetAppID

Id. de modelo de aplicación de usuario se establece explícitamente para la aplicación. Este método debe llamarse antes de cualquier interfaz de usuario se presenta al usuario (lo mejor es el constructor de la aplicación).

```
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>Parámetros

*lpcszAppID*  
Especifica el identificador de modelo de usuario de aplicación.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[CWinThread (clase)](../../mfc/reference/cwinthread-class.md)  
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)  
[Procedimiento para agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md)  
