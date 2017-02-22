---
title: "CWinApp Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinApp"
  - "hInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "application objects [C++]"
  - "CWinApp class"
  - "HINSTANCE"
  - "main object"
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
caps.latest.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 29
---
# CWinApp Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase base que se deriva un objeto de aplicación para Windows.  
  
## Sintaxis  
  
```  
class CWinApp : public CWinThread  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinApp::CWinApp](../Topic/CWinApp::CWinApp.md)|Crea un objeto `CWinApp`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinApp::AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md)|Agrega una plantilla de documento a la lista de plantillas de documento disponibles.|  
|[CWinApp::AddToRecentFileList](../Topic/CWinApp::AddToRecentFileList.md)|Agrega un nombre de archivo a la lista de archivos usados recientemente utilizada \(MRU\).|  
|[CWinApp::ApplicationRecoveryCallback](../Topic/CWinApp::ApplicationRecoveryCallback.md)|Llamado por el marco cuando cierra la aplicación inesperado.|  
|[CWinApp::CloseAllDocuments](../Topic/CWinApp::CloseAllDocuments.md)|Cierra todos los documentos abiertos.|  
|[CWinApp::CreatePrinterDC](../Topic/CWinApp::CreatePrinterDC.md)|Crea un contexto de dispositivo de impresora.|  
|[CWinApp::DelRegTree](../Topic/CWinApp::DelRegTree.md)|Elimina una clave especificada y todas sus subclaves.|  
|[CWinApp::DoMessageBox](../Topic/CWinApp::DoMessageBox.md)|implementa [AfxMessageBox](../Topic/AfxMessageBox.md) para la aplicación.|  
|[CWinApp::DoWaitCursor](../Topic/CWinApp::DoWaitCursor.md)|Gira el cursor de espera por intervalos.|  
|[CWinApp::EnableD2DSupport](../Topic/CWinApp::EnableD2DSupport.md)|Compatibilidad de `D2D` de la aplicación de permisos.  Llame a este método antes de que se inicialice la ventana principal.|  
|[CWinApp::EnableHtmlHelp](../Topic/CWinApp::EnableHtmlHelp.md)|Implementa HTMLHelp para la aplicación, en lugar de WinHelp.|  
|[CWinApp::EnableTaskbarInteraction](../Topic/CWinApp::EnableTaskbarInteraction.md)|Interacción de la barra de tareas de permisos.|  
|[CWinApp::ExitInstance](../Topic/CWinApp::ExitInstance.md)|reemplace para limpiar cuando la aplicación finaliza.|  
|[CWinApp::GetApplicationRecoveryParameter](../Topic/CWinApp::GetApplicationRecoveryParameter.md)|Recupera el parámetro de entrada para el método de recuperación de la aplicación.|  
|[CWinApp::GetApplicationRecoveryPingInterval](../Topic/CWinApp::GetApplicationRecoveryPingInterval.md)|Devuelve el intervalo de tiempo que el administrador de reinicio espera la función de devolución de llamada de recuperación para devolver.|  
|[CWinApp::GetApplicationRestartFlags](../Topic/CWinApp::GetApplicationRestartFlags.md)|Devuelve marcas para el administrador de reinicio.|  
|[CWinApp::GetAppRegistryKey](../Topic/CWinApp::GetAppRegistryKey.md)|Devuelve la clave de HKEY\_CURRENT\_USER \\"Software"\\RegistryKey\\ProfileName.|  
|[CWinApp::GetDataRecoveryHandler](../Topic/CWinApp::GetDataRecoveryHandler.md)|Obtiene el controlador de la recuperación de datos para esta instancia de la aplicación.|  
|[CWinApp::GetFirstDocTemplatePosition](../Topic/CWinApp::GetFirstDocTemplatePosition.md)|recupera la posición de la primera plantilla de documento.|  
|[CWinApp::GetHelpMode](../Topic/CWinApp::GetHelpMode.md)|recupera el tipo de ayuda utilizado por la aplicación.|  
|[CWinApp::GetNextDocTemplate](../Topic/CWinApp::GetNextDocTemplate.md)|recupera la posición de una plantilla de documento.  Se puede utilizar de forma recursiva.|  
|[CWinApp::GetPrinterDeviceDefaults](../Topic/CWinApp::GetPrinterDeviceDefaults.md)|Recupera los valores predeterminados del dispositivo de impresora.|  
|[CWinApp::GetProfileBinary](../Topic/CWinApp::GetProfileBinary.md)|Recupera datos binarios de una entrada en el archivo de .INI de la aplicación.|  
|[CWinApp::GetProfileInt](../Topic/CWinApp::GetProfileInt.md)|Recupera un entero de una entrada en el archivo de .INI de la aplicación.|  
|[CWinApp::GetProfileString](../Topic/CWinApp::GetProfileString.md)|Recupera una cadena de una entrada en el archivo de .INI de la aplicación.|  
|[CWinApp::GetSectionKey](../Topic/CWinApp::GetSectionKey.md)|Devuelve la clave de HKEY\_CURRENT\_USER \\"Software"\\RegistryKey\\AppName\\lpszSection.|  
|[CWinApp::HideApplication](../Topic/CWinApp::HideApplication.md)|oculta la aplicación antes de cerrar todos los documentos.|  
|[CWinApp::HtmlHelp](../Topic/CWinApp::HtmlHelp.md)|Llama a la función de `HTMLHelp` Windows.|  
|[CWinApp::InitInstance](../Topic/CWinApp::InitInstance.md)|Reemplace para realizar la inicialización de la instancia de Windows, como crear los objetos de la ventana.|  
|[CWinApp::IsTaskbarInteractionEnabled](../Topic/CWinApp::IsTaskbarInteractionEnabled.md)|Indica si la interacción de la barra de tareas de Windows 7 está habilitada.|  
|[CWinApp::LoadCursor](../Topic/CWinApp::LoadCursor.md)|Carga un recurso del cursor.|  
|[CWinApp::LoadIcon](../Topic/CWinApp::LoadIcon.md)|Carga un recurso de icono.|  
|[CWinApp::LoadOEMCursor](../Topic/CWinApp::LoadOEMCursor.md)|Carga Windows cursor predefinido OEM que las constantes de **OCR\_** especificados en WINDOWS.H.|  
|[CWinApp::LoadOEMIcon](../Topic/CWinApp::LoadOEMIcon.md)|Carga un icono predefinido OEM de Windows que las constantes de **OIC\_** especificados en WINDOWS.H.|  
|[CWinApp::LoadStandardCursor](../Topic/CWinApp::LoadStandardCursor.md)|Carga el cursor predefinido Windows que las constantes de **IDC\_** especificados en WINDOWS.H.|  
|[CWinApp::LoadStandardIcon](../Topic/CWinApp::LoadStandardIcon.md)|Carga un icono predefinido Windows que las constantes de **IDI\_** especificados en WINDOWS.H.|  
|[CWinApp::OnDDECommand](../Topic/CWinApp::OnDDECommand.md)|Llamado por el marco en respuesta a un intercambio de datos dinámicos \(DDE\) ejecute el comando.|  
|[CWinApp::OnIdle](../Topic/CWinApp::OnIdle.md)|Reemplace para realizar el procesamiento específico de la aplicación en tiempo de inactividad.|  
|[CWinApp::OpenDocumentFile](../Topic/CWinApp::OpenDocumentFile.md)|Llamado por el marco para abrir un documento de un archivo.|  
|[CWinApp::ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md)|Analiza los parámetros individuales y marca en la línea de comandos.|  
|[CWinApp::PreTranslateMessage](../Topic/CWinApp::PreTranslateMessage.md)|Mensajes de filtros antes de que se envíen a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CWinApp::ProcessMessageFilter](../Topic/CWinApp::ProcessMessageFilter.md)|Algunos mensajes de las intersecciones antes de que llegan a la aplicación.|  
|[CWinApp::ProcessShellCommand](../Topic/CWinApp::ProcessShellCommand.md)|Controla argumentos de la línea de comandos e indicadores.|  
|[CWinApp::ProcessWndProcException](../Topic/CWinApp::ProcessWndProcException.md)|Intercepta todas las excepciones no controladas producidas por los controladores de mensajes y el comando de la aplicación.|  
|[CWinApp::Register](../Topic/CWinApp::Register.md)|performs personalizó el registro.|  
|[CWinApp::RegisterWithRestartManager](../Topic/CWinApp::RegisterWithRestartManager.md)|Registra la aplicación con el administrador de reinicio.|  
|[CWinApp::ReopenPreviousFilesAtRestart](../Topic/CWinApp::ReopenPreviousFilesAtRestart.md)|Determina si el administrador de reinicio vuelve a abrir los archivos que se abren cuando fue la aplicación inesperado.|  
|[CWinApp::RestartInstance](../Topic/CWinApp::RestartInstance.md)|Administra el reinicio de la aplicación inicia el administrador de reinicio.|  
|[CWinApp::RestoreAutosavedFilesAtRestart](../Topic/CWinApp::RestoreAutosavedFilesAtRestart.md)|Determina si el administrador de reinicio restaura los archivos autoguardados cuando se reinicia la aplicación.|  
|[CWinApp::Run](../Topic/CWinApp::Run.md)|ejecuta el bucle de mensajes predeterminado.  reemplace para personalizar el bucle de mensajes.|  
|[CWinApp::RunAutomated](../Topic/CWinApp::RunAutomated.md)|prueba la línea de comandos de la aplicación para la opción de **\/Automation** .  Obsoleto.  En su lugar, utilice el valor en [CCommandLineInfo:: m\_bRunAutomated](../Topic/CCommandLineInfo::m_bRunAutomated.md) después de llamar a [ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md).|  
|[CWinApp::RunEmbedded](../Topic/CWinApp::RunEmbedded.md)|prueba la línea de comandos de la aplicación para la opción de **\/Embedding** .  Obsoleto.  En su lugar, utilice el valor en [CCommandLineInfo:: m\_bRunEmbedded](../Topic/CCommandLineInfo::m_bRunEmbedded.md) después de llamar a [ParseCommandLine](../Topic/CWinApp::ParseCommandLine.md).|  
|[CWinApp::SaveAllModified](../Topic/CWinApp::SaveAllModified.md)|Solicita al usuario guardar todos los documentos modificados.|  
|[CWinApp::SelectPrinter](../Topic/CWinApp::SelectPrinter.md)|Selecciona una impresora indicada anteriormente por un usuario a través de un cuadro de diálogo de impresión.|  
|[CWinApp::SetHelpMode](../Topic/CWinApp::SetHelpMode.md)|Los conjuntos y inicialice el tipo de ayuda utilizado por la aplicación.|  
|[CWinApp::SupportsApplicationRecovery](../Topic/CWinApp::SupportsApplicationRecovery.md)|Determina si recupera el administrador de reinicio una aplicación que fue inesperado.|  
|[CWinApp::SupportsAutosaveAtInterval](../Topic/CWinApp::SupportsAutosaveAtInterval.md)|Determina si el administrador de reinicio autoguarda documentos abiertos de manera periódica.|  
|[CWinApp::SupportsAutosaveAtRestart](../Topic/CWinApp::SupportsAutosaveAtRestart.md)|Determina si el administrador de reinicio autoguarda los documentos abiertos cuando se reinicia la aplicación.|  
|[CWinApp::SupportsRestartManager](../Topic/CWinApp::SupportsRestartManager.md)|Determina si la aplicación es compatible con el administrador de reinicio.|  
|[CWinApp::Unregister](../Topic/CWinApp::Unregister.md)|Anula todo conocida para registrarse por el objeto de `CWinApp` .|  
|[CWinApp::WinHelp](../Topic/CWinApp::WinHelp.md)|Llama a la función de `WinHelp` Windows.|  
|[CWinApp::WriteProfileBinary](../Topic/CWinApp::WriteProfileBinary.md)|Escribe datos binarios a una entrada en el archivo de .INI de la aplicación.|  
|[CWinApp::WriteProfileInt](../Topic/CWinApp::WriteProfileInt.md)|Escriba un entero a una entrada en el archivo de .INI de la aplicación.|  
|[CWinApp::WriteProfileString](../Topic/CWinApp::WriteProfileString.md)|Escribe una cadena en una entrada en el archivo de .INI de la aplicación.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinApp::EnableShellOpen](../Topic/CWinApp::EnableShellOpen.md)|Permite que el usuario abre los archivos de datos del administrador de archivos de Windows.|  
|[CWinApp::LoadStdProfileSettings](../Topic/CWinApp::LoadStdProfileSettings.md)|Carga la configuración estándar del archivo de .INI y habilita la característica lista de archivos MRU.|  
|[CWinApp::OnContextHelp](../Topic/CWinApp::OnContextHelp.md)|Ayuda de identificadores MAYÚS\+F1 dentro de la aplicación.|  
|[CWinApp::OnFileNew](../Topic/CWinApp::OnFileNew.md)|Implementar el comando de `ID_FILE_NEW` .|  
|[CWinApp::OnFileOpen](../Topic/CWinApp::OnFileOpen.md)|Implementar el comando de `ID_FILE_OPEN` .|  
|[CWinApp::OnFilePrintSetup](../Topic/CWinApp::OnFilePrintSetup.md)|Implementar el comando de `ID_FILE_PRINT_SETUP` .|  
|[CWinApp::OnHelp](../Topic/CWinApp::OnHelp.md)|Ayuda de F1 de identificadores dentro de la aplicación \(con el contexto actual\).|  
|[CWinApp::OnHelpFinder](../Topic/CWinApp::OnHelpFinder.md)|Controla los comandos de `ID_HELP_FINDER` y de `ID_DEFAULT_HELP` .|  
|[CWinApp::OnHelpIndex](../Topic/CWinApp::OnHelpIndex.md)|Administra el comando de `ID_HELP_INDEX` y proporciona un tema de Ayuda predeterminado.|  
|[CWinApp::OnHelpUsing](../Topic/CWinApp::OnHelpUsing.md)|Controla el comando `ID_HELP_USING`.|  
|[CWinApp::RegisterShellFileTypes](../Topic/CWinApp::RegisterShellFileTypes.md)|registra los tipos de documento de toda la aplicación con el administrador de archivos de Windows.|  
|[CWinApp::SetAppID](../Topic/CWinApp::SetAppID.md)|Establece explícitamente el identificador del Modelo de usuario de la aplicación de la aplicación.  Se debe llamar a este método antes de cualquier interfaz de usuario se muestra al usuario \(el mejor lugar es el constructor de la aplicación\).|  
|[CWinApp::SetRegistryKey](../Topic/CWinApp::SetRegistryKey.md)|Hace que la configuración de la aplicación que se almacenarán en el registro en lugar de archivos de .INI.|  
|[CWinApp::UnregisterShellFileTypes](../Topic/CWinApp::UnregisterShellFileTypes.md)|Anula los tipos de documento de toda la aplicación con el administrador de archivos de Windows.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinApp::m\_bHelpMode](../Topic/CWinApp::m_bHelpMode.md)|Indica si el usuario está en el modo de contexto de Ayuda \(invocado normalmente con MAYÚS\+F1\).|  
|[CWinApp::m\_eHelpType](../Topic/CWinApp::m_eHelpType.md)|especifica el tipo de ayuda utilizado por la aplicación.|  
|[CWinApp::m\_hInstance](../Topic/CWinApp::m_hInstance.md)|identifica la instancia actual de la aplicación.|  
|[CWinApp::m\_lpCmdLine](../Topic/CWinApp::m_lpCmdLine.md)|Señala una cadena terminada en null que especifica la línea de comandos para la aplicación.|  
|[CWinApp::m\_nCmdShow](../Topic/CWinApp::m_nCmdShow.md)|especifica cómo la ventana debe ser mostrada inicialmente.|  
|[CWinApp::m\_pActiveWnd](../Topic/CWinApp::m_pActiveWnd.md)|Puntero a la ventana principal de la aplicación contenedora cuando un servidor OLE está activo en contexto.|  
|[CWinApp::m\_pszAppID](../Topic/CWinApp::m_pszAppID.md)|Identificador del Modelo de usuario de la aplicación|  
|[CWinApp::m\_pszAppName](../Topic/CWinApp::m_pszAppName.md)|Especifica el nombre de la aplicación.|  
|[CWinApp::m\_pszExeName](../Topic/CWinApp::m_pszExeName.md)|El nombre del módulo de la aplicación.|  
|[CWinApp::m\_pszHelpFilePath](../Topic/CWinApp::m_pszHelpFilePath.md)|La ruta de acceso al archivo de Ayuda de la aplicación.|  
|[CWinApp::m\_pszProfileName](../Topic/CWinApp::m_pszProfileName.md)|El nombre de archivo de .INI de la aplicación.|  
|[CWinApp::m\_pszRegistryKey](../Topic/CWinApp::m_pszRegistryKey.md)|Utilizado para determinar la clave del Registro completa para almacenar la configuración de perfil de la aplicación.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinApp::m\_dwRestartManagerSupportFlags](../Topic/CWinApp::m_dwRestartManagerSupportFlags.md)|Marca que determina cómo el administrador de reinicio se comporta.|  
|[CWinApp::m\_nAutosaveInterval](../Topic/CWinApp::m_nAutosaveInterval.md)|El intervalo de tiempo en milisegundos entre los autoguardados.|  
|[CWinApp::m\_pDataRecoveryHandler](../Topic/CWinApp::m_pDataRecoveryHandler.md)|Puntero al controlador de la recuperación de datos para la aplicación.|  
  
## Comentarios  
 Un objeto de aplicación proporciona funciones miembro para inicializar la aplicación \(y cada instancia de ella\) y ejecutar la aplicación.  
  
 Cada aplicación que utiliza las clases de windows presentation foundation Microsoft sólo puede contener un objeto derivado de `CWinApp`.  Este objeto se crea cuando se construyen otros objetos globales de C\+\+ ya está disponible cuando Windows llama a la función de `WinMain` , proporcionada por la biblioteca Microsoft Foundation Class.  declare el objeto derivado de `CWinApp` en el nivel global.  
  
 Al derivar una clase de aplicación de `CWinApp`, reemplace la función miembro de [InitInstance](../Topic/CWinApp::InitInstance.md) para crear el objeto de la ventana principal de la aplicación.  
  
 Además de las funciones miembro de `CWinApp` , la biblioteca Microsoft Foundation Class proporciona funciones globales siguientes para tener acceso a `CWinApp` y a otra información global:  
  
-   [AfxGetApp](../Topic/AfxGetApp.md) Obtains un puntero al objeto de `CWinApp` .  
  
-   [AfxGetInstanceHandle](../Topic/AfxGetInstanceHandle.md) Obtains un identificador de la instancia de aplicación actual.  
  
-   [AfxGetResourceHandle](../Topic/AfxGetResourceHandle.md) Obtains un identificador a los recursos de la aplicación.  
  
-   [AfxGetAppName](../Topic/AfxGetAppName.md) Obtains un puntero a una cadena que contiene el nombre de la aplicación.  Como alternativa, si tiene un puntero al objeto de `CWinApp` , utilice `m_pszExeName` de obtener el nombre de aplicación.  
  
 Vea [CWinApp: La clase de aplicación](../../mfc/cwinapp-the-application-class.md) para más en la clase de `CWinApp` , incluida una información general del siguiente:  
  
-   `CWinApp`\- código derivado escrito por el Asistente para aplicaciones.  
  
-   el rol de los entity\_CWinApp en la secuencia de la ejecución de la aplicación.  
  
-   implementaciones predeterminadas de funciones miembro de los entity\_CWinApp.  
  
-   los overridables clave de los entity\_CWinApp.  
  
 El miembro de datos de **m\_hPrevInstance** ya no existe.  Para obtener información sobre cómo detectar una instancia anterior de `CWinApp`, vea el artículo “Cómo de Knowledge Base a Identify una instancia Anteriores de una aplicación” \(KB106385\) en [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;es\-es;106385](http://support.microsoft.com/default.aspx?scid=kb;es-es;106385).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWinThread](../../mfc/reference/cwinthread-class.md)  
  
 `CWinApp`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CWinThread Class](../../mfc/reference/cwinthread-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Cómo: Agregar compatibilidad con el Administrador de reinicio](../../mfc/how-to-add-restart-manager-support.md)