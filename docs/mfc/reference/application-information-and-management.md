---
title: Información de la aplicación y administración | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 54265814b4b60b08bed780a39ecadcace3242202
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="application-information-and-management"></a>Información y administración de aplicaciones
Cuando se escribe una aplicación, cree un único [CWinApp](../../mfc/reference/cwinapp-class.md)-objeto derivado. En ocasiones, puede que desee obtener información acerca de este objeto desde fuera de la `CWinApp`-objeto derivado. O bien, puede que tenga acceso a otros objetos globales "Manager".
  
 La biblioteca Microsoft Foundation Class proporciona las siguientes funciones globales para ayudarle a realizar estas tareas:  
  
### <a name="application-information-and-management-functions"></a>Información de la aplicación y las funciones de administración  
  
|||  
|-|-|  
|[AfxBeginThread](#afxbeginthread)|Crea un nuevo subproceso.|  
|[AfxContextMenuManager](#afxcontextmenumanager)|Puntero a la plantilla global [Administrador de menús de contexto](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Finaliza el subproceso actual.|  
|[AfxFindResourceHandle](#afxfindresourcehandle)|Recorre la cadena de recurso y buscar un identificador de recurso por recurso específico y el tipo de recurso. |
|[AfxFreeLibrary](#afxfreelibrary)|Disminuye el recuento de referencias del módulo cargado biblioteca de vínculos dinámicos (DLL); Cuando el recuento de referencias llega a cero, el módulo no se ha asignado.|  
|[AfxGetApp](#afxgetapp)|Devuelve un puntero a la aplicación 's único `CWinApp` objeto.|  
|[AfxGetAppName](#afxgetappname)|Devuelve una cadena que contiene el nombre de la aplicación.|  
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Devuelve un `HINSTANCE` que representa esta instancia de la aplicación.|  
|[AfxGetMainWnd](#afxgetmainwnd)|Devuelve un puntero a la ventana actual "principal" de una aplicación no son compatibles con OLE o la ventana de marco en contexto de una aplicación de servidor.|  
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Utilice esta función para determinar si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.|  
|[AfxGetResourceHandle](#afxgetresourcehandle)|Devuelve un `HINSTANCE` para el origen de los recursos de la aplicación predeterminada. Utilice esto para tener acceso a recursos de la aplicación directamente.|  
|[AfxGetThread](#afxgetthread)|Recupera un puntero a la actual [CWinThread](../../mfc/reference/cwinthread-class.md) objeto.|  
|[AfxInitRichEdit](#afxinitrichedit)|Inicializa la versión de control para la aplicación de edición enriquecida 1.0.|  
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicializa la versión de control para la aplicación de edición enriquecida 2.0 y versiones posterior.| 
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Determina si la ventana dada es un objeto de marco extendido.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Determina si la ventana dada es un objeto de barra de herramientas.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Puntero a la plantilla global [manager de teclado](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Un módulo de archivo DLL se asigna y devuelve un identificador que puede utilizarse para obtener la dirección de una función DLL.|  
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Puntero a la plantilla global [manager de menú divisible](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Puntero a la plantilla global [manager mouse](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Registra una clase de ventana en un archivo DLL que utiliza MFC.|  
|[AfxRegisterWndClass](#afxregisterwndclass)|Registra una clase de ventana de Windows para complementarlos registran automáticamente por MFC.|  
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Establece si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.|  
|[AfxSetResourceHandle](#afxsetresourcehandle)|Establece el `HINSTANCE` identificador que se cargan los recursos predeterminados de la aplicación.|  
|[AfxShellManager](#afxshellmanager)|Puntero a la plantilla global [manager shell](cshellmanager-class.md). |
|[AfxSocketInit](#afxsocketinit)|Llama un `CWinApp::InitInstance` invalidación para inicializar Windows Sockets.|  
|[AfxUserToolsManager](#afxusertoolsmanager)|Puntero a la plantilla global [Administrador de herramientas de usuario](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Llama a la suministrada en MFC `WinMain` función, como parte de la [CWinApp](../../mfc/reference/cwinapp-class.md) inicialización de una aplicación basada en GUI, inicializar MFC. Se debe llamar directamente para las aplicaciones de consola que utilizan MFC.|  
  

  
##  <a name="afxbeginthread"></a>  AfxBeginThread  
 Llame a esta función para crear un nuevo subproceso.  
  
```   
CWinThread* AfxBeginThread(
    AFX_THREADPROC pfnThreadProc,  
    LPVOID pParam,  
    int nPriority = THREAD_PRIORITY_NORMAL,  
    UINT nStackSize = 0,  
    DWORD dwCreateFlags = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);

CWinThread* AfxBeginThread(
    CRuntimeClass* pThreadClass,  
    int nPriority = THREAD_PRIORITY_NORMAL,  
    UINT nStackSize = 0,  
    DWORD dwCreateFlags = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL); 
```  
  
### <a name="parameters"></a>Parámetros  
 `pfnThreadProc`  
 Apunta a la función controladora para el subproceso de trabajo. No puede ser **NULL**. Esta función debe declararse como sigue:  
  
 `UINT __cdecl MyControllingFunction( LPVOID pParam );`  
  
 *pThreadClass*  
 La clase RUNTIME_CLASS de un objeto derivado de [CWinThread](../../mfc/reference/cwinthread-class.md).  
  
 *pParam*  
 Parámetro que se pasan a la función controladora tal como se muestra en el parámetro a la declaración de función en `pfnThreadProc`.  
  
 `nPriority`  
 La prioridad deseada del subproceso. Para una lista completa y una descripción de las prioridades disponibles, vea [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) del SDK de Windows.  
  
 `nStackSize`  
 Especifica el tamaño en bytes de la pila para el nuevo subproceso. Si es 0, el tamaño de pila predeterminado es la misma pila de tamaño que del subproceso creador.  
  
 `dwCreateFlags`  
 Especifica una marca adicional que controla la creación del subproceso. Este indicador puede contener uno de dos valores:  
  
- **CREATE_SUSPENDED** iniciar el subproceso con un recuento de suspensión de uno. Use **CREATE_SUSPENDED** si desea inicializar los datos de miembro de la `CWinThread` objeto, como [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) o todos los miembros de la clase derivada, antes de que el subproceso empieza a ejecutarse. Una vez completada la inicialización, utilice [CWinThread:: ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) para iniciar el subproceso de ejecución. El subproceso no se ejecutará hasta que `CWinThread::ResumeThread` se llama.  
  
- **0** iniciar el subproceso inmediatamente después de crear.  
  
 `lpSecurityAttrs`  
 Apunta a un [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica los atributos de seguridad para el subproceso. Si **NULL**, atributos de la misma seguridad que se utilizará del subproceso creador. Para obtener más información sobre esta estructura, vea el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al objeto de subproceso recién creado, o **NULL** si se produce un error.  
  
### <a name="remarks"></a>Comentarios  
 La primera forma de `AfxBeginThread` crea un subproceso de trabajo. La segunda forma crea un subproceso que puede actuar como un subproceso de interfaz de usuario o como un subproceso de trabajo.  
  
 `AfxBeginThread` crea un nuevo `CWinThread` (objeto), llamadas su [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) función para empezar a ejecutar el subproceso y devuelve un puntero al subproceso. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación. Para finalizar el subproceso, llame a [AfxEndThread](#afxendthread) desde dentro del subproceso o valor devuelto de la función de control de subproceso de trabajo.  
  
 Subprocesamiento múltiple debe estar habilitado por la aplicación; en caso contrario, se producirá un error en esta función. Para obtener más información sobre la habilitación de subprocesamiento múltiple, consulte [/MD, / MT, /LD (utilizar la biblioteca en tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md) en *opciones del compilador de Visual C++*.  
  
 Para obtener más información sobre `AfxBeginThread`, consulte los artículos [Multithreading: crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md) y [Multithreading: crear subprocesos de la interfaz de usuario](../../parallel/multithreading-creating-user-interface-threads.md).  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  

## <a name="afxcontextmenumanager"></a> AfxContextMenuManager
Puntero a la plantilla global [Administrador de menús de contexto](ccontextmenumanager-class.md).  
   
### <a name="syntax"></a>Sintaxis    
```  
CContextMenuManager* afxContextMenuManager;  
```     
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcontextmenumanager.h     

### <a name="see-also"></a>Vea también   
 [CContextMenuManager (clase)](ccontextmenumanager-class.md)

  
##  <a name="afxendthread"></a>  AfxEndThread  
 Llame a esta función para terminar el subproceso actualmente en ejecución.  
  
```   
void AFXAPI AfxEndThread(
    UINT nExitCode,  
    BOOL bDelete  = TRUE); 
```  
  
### <a name="parameters"></a>Parámetros  
 *nExitCode*  
 Especifica el código de salida del subproceso.  
  
 *bDelete*  
 Elimina el objeto de subproceso de la memoria.  
  
### <a name="remarks"></a>Comentarios  
 Se debe invocar desde dentro del subproceso que debe finalizar.  
  
 Para obtener más información sobre `AfxEndThread`, vea el artículo [Multithreading: Finalizar subprocesos](../../parallel/multithreading-terminating-threads.md).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
Use `AfxFindResourceHandle` para recorrer la cadena de recurso y buscar un tipo específico de recursos y el identificador de recurso por recurso.  
   
### <a name="syntax"></a>Sintaxis    
```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );  
```
### <a name="parameters"></a>Parámetros  
 `lpszName`  
 Un puntero a una cadena que contiene el identificador de recurso.    
 *lpszType*  
 Un puntero al tipo de recurso. Para obtener una lista de tipos de recursos, consulte [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) del SDK de Windows.  
   
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el módulo que contiene el recurso.  
   
### <a name="remarks"></a>Comentarios  
 `AfxFindResourceHandle` busca el recurso específico y devuelve un identificador para el módulo que contiene el recurso. El recurso puede estar en cualquier ha cargado la DLL de extensión de MFC. `AfxFindResourceHandle` indica que tiene el recurso.  
  
 Los módulos se buscan en este orden:  
  
1.  El módulo principal (si es un archivo DLL de extensión MFC).  
  
2.  Módulos no son del sistema.  
  
3.  Módulos específicos del idioma.  
  
4.  El módulo principal (si es un archivo DLL del sistema).  
  
5.  Módulos del sistema.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
   
### <a name="see-also"></a>Vea también  
 [Macros y funciones globales](mfc-macros-and-globals.md)   
  
##  <a name="afxfreelibrary"></a>  AfxFreeLibrary  
 Ambos `AfxFreeLibrary` y `AfxLoadLibrary` mantener un recuento de referencias para cada módulo de biblioteca cargada.  
  
```   
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib); 
```  
  
### <a name="parameters"></a>Parámetros  
 *hInstLib*  
 Identificador del módulo de biblioteca cargada. [AfxLoadLibrary](#afxloadlibrary) devuelve este identificador.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si la función se realiza correctamente; en caso contrario, **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 `AfxFreeLibrary` disminuye el recuento de referencias del módulo cargado biblioteca de vínculos dinámicos (DLL). Cuando el recuento de referencias llega a cero, el módulo no está asignado desde el espacio de direcciones del proceso que realiza la llamada y el identificador ya no es válido. Este recuento de referencias se incrementa cada vez que `AfxLoadLibrary` se llama.  
  
 Antes de desasignación de un módulo de biblioteca, el sistema permite que la DLL se desasocie de los procesos que lo usan. Si lo hace, da la DLL oportunidad para limpiar los recursos asignados en nombre del proceso actual. Después de que se devuelva la función de punto de entrada, el módulo de biblioteca se quitará el espacio de direcciones del proceso actual.  
  
 Utilice `AfxLoadLibrary` para asignar un módulo de DLL.  
  
 Asegúrese de usar `AfxFreeLibrary` y `AfxLoadLibrary` (en lugar de las funciones de Win32 **FreeLibrary** y **LoadLibrary**) si la aplicación utiliza varios subprocesos. Usar `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y cierre que se ejecuta cuando la extensión MFC DLL se cargan y descargan no dañe el estado global de MFC.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [AfxLoadLibrary](#afxloadlibrary).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdll_.h  
  
##  <a name="afxgetapp"></a>  AfxGetApp  
 El puntero devuelto por esta función se puede utilizar para tener acceso a información de la aplicación como el código de envío de mensajes principal o la ventana de nivel superior.  
  
```   
CWinApp* AFXAPI AfxGetApp(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la única `CWinApp` objeto de la aplicación.  
  
### <a name="remarks"></a>Comentarios  
 Si este método devuelve NULL, podría indicar que la ventana principal de la aplicación no se ha totalmente inicializada todavía. También es posible que haya un problema.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxgetappname"></a>  AfxGetAppName  
 La cadena devuelta por esta función se puede utilizar para los mensajes de diagnóstico o como una raíz para los nombres de cadena temporal.  
  
```   
LPCTSTR AFXAPI AfxGetAppName(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena terminada en null que contiene el nombre de la aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxgetinstancehandle"></a>  AfxGetInstanceHandle  
 Esta función permite recuperar el identificador de instancia de la aplicación actual.  
  
```   
HINSTANCE  AFXAPI AfxGetInstanceHandle(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `HINSTANCE` a la instancia actual de la aplicación. Si se llama desde dentro de un archivo DLL vinculado con la versión de archivo USRDLL de MFC, un `HINSTANCE` se devuelve a la DLL.  
  
### <a name="remarks"></a>Comentarios  
 `AfxGetInstanceHandle` siempre devuelve el `HINSTANCE` del archivo ejecutable (. (EXE), a menos que se llama desde un archivo DLL vinculado con la versión de archivo USRDLL de MFC. En este caso, devuelve un `HINSTANCE` al archivo DLL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxgetmainwnd"></a>  AfxGetMainWnd  
 Si la aplicación es un servidor OLE, llamar a esta función para recuperar un puntero a la ventana principal activa de la aplicación en lugar de hacer referencia directamente a la [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) miembro del objeto de aplicación.  
  
```   
CWnd* AFXAPI AfxGetMainWnd(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si el servidor tiene un objeto que está activo en contexto dentro de un contenedor y ese contenedor está activo, la función devuelve un puntero al objeto de ventana marco que contiene el documento activo en contexto.  
  
 Si no hay ningún objeto activo en contexto dentro de un contenedor o la aplicación no es un servidor OLE, esta función devuelve simplemente el miembro `m_pMainWnd` del objeto de aplicación.  
  
 Si se llama a `AfxGetMainWnd` desde el subproceso principal de la aplicación, devuelve la ventana principal de la aplicación según las reglas anteriores. Si se llama a la función desde un subproceso secundario de la aplicación, la función devuelve la ventana principal asociada al subproceso que realizó la llamada.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación no es un servidor OLE, llamar a esta función equivale a hacer referencia directamente al miembro `m_pMainWnd` del objeto de aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxgetperuserregistration"></a>  AfxGetPerUserRegistration  
 Utilice esta función para determinar si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.  
  
```  
BOOL AFXAPI AfxGetPerUserRegistration();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE` indica que la información de registro se dirige a la **HKCU** nodo; `FALSE` indica que la aplicación escribe información de registro en el nodo de forma predeterminada. El nodo de valor predeterminado es **HKEY_CLASSES_ROOT** ( **HKCR**).  
  
### <a name="remarks"></a>Comentarios  
 Si habilita la redirección del registro, el marco de trabajo redirige el acceso de **HKCR** a **HKEY_CURRENT_USER\Software\Classes**. Solo los marcos de trabajo MFC y ATL se ven afectados por la redirección.  
  
 Para cambiar si la aplicación redirige el acceso al registro, use [AfxSetPerUserRegistration](#afxsetperuserregistration).  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxstat_.h    
  
##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle  
 Use la `HINSTANCE` identificador devuelto por esta función para obtener acceso a recursos de la aplicación directamente, por ejemplo, en las llamadas a la función de Windows **FindResource**.  
  
```   
extern HINSTANCE  AfxGetResourceHandle(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `HINSTANCE` identificador que se cargan los recursos predeterminados de la aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxgetthread"></a>  AfxGetThread  
 Llame a esta función para obtener un puntero a la [CWinThread](../../mfc/reference/cwinthread-class.md) objeto que representa el subproceso actualmente en ejecución.  
  
```   
CWinThread* AfxGetThread(); 
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero para el subproceso actualmente en ejecución; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Se debe invocar desde dentro el subproceso deseado.  
  
> [!NOTE]
>  Si va a trasladar una llamada de proyecto MFC `AfxGetThread` de Visual C++ versión 4.2, 5.0 o 6.0, `AfxGetThread` llamadas [AfxGetApp](#afxgetapp) si no se encuentra ningún subproceso. En las versiones más recientes del compilador, `AfxGetThread` devuelve **NULL** si no se encontró ningún subproceso. Si desea que el subproceso de la aplicación, debe llamar a `AfxGetApp`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxinitrichedit"></a>  AfxInitRichEdit  
 Llame a esta función para inicializar el control rich edit (versión 1.0) para la aplicación.  
  
```   
BOOL AFXAPI AfxInitRichEdit(); 
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función se proporciona por compatibilidad con versiones anteriores. Las aplicaciones nuevas deben utilizar [AfxInitRichEdit2](#afxinitrichedit2).  
  
 `AfxInitRichEdit` carga RICHED32. DLL para inicializar la versión 1.0 del control rich edit. Para usar la versión 2.0 y 3.0 del control rich edit, RICHED20. Archivo DLL debe cargarse. Esto se logra con una llamada a [AfxInitRichEdit2](#afxinitrichedit2).  
  
 Para actualizar los controles de edición enriquecidas en las aplicaciones existentes de Visual C++ a la versión 2.0, abra el. Archivo RC como texto, cambie el nombre de clase de cada control rich edit de "RICHEDIT" a "RichEdit20a". A continuación, reemplace la llamada a `AfxInitRichEdit` con `AfxInitRichEdit2`.  
  
 Esta función también inicializa la biblioteca de controles comunes, si la biblioteca ya no se ha inicializado para el proceso. Si utiliza el control rich edit directamente desde la aplicación MFC, debe llamar a esta función para asegurarse de que MFC ha inicializado correctamente el tiempo de ejecución del control rich Edit. Si llama al método Create de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), o [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), normalmente no es necesario llamar a esta función, pero en algunos casos es posible es necesario.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxinitrichedit2"></a>  AfxInitRichEdit2  
 Llame a esta función para inicializar el control rich edit (versión 2.0 y versiones posterior) para la aplicación.  
  
```   
BOOL AFXAPI AfxInitRichEdit2(); 
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para cargar el RICHED20. Archivo DLL e inicialice la versión 2.0 de los datos completos de control de edición. Si llama al método Create de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), o [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), normalmente no es necesario llamar a esta función, pero en algunos casos es posible es necesario.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  

  ## <a name="afxisextendedframeclass"></a>  AfxIsExtendedFrameClass
Determina si la ventana dada es un objeto de marco extendido.  
   
### <a name="syntax"></a>Sintaxis    
```  
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );  
```
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a un objeto que se deriva de `CWnd`.  
   
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si la ventana proporcionada es un objeto de marco extendido; en caso contrario, `FALSE`.  
   
### <a name="remarks"></a>Comentarios  
 Este método devuelve `TRUE` si `pWnd` se deriva de una de las clases siguientes:  
  
-   `CFrameWndEx`  
  
-   `CMDIFrameWndEx`  
  
-   `COleIPFrameWndEx`  
  
-   `COleDocIPFrameWndEx`  
  
-   `CMDIChildWndEx`  
  
 Este método es útil cuando tiene que validar que un parámetro de función o método es una ventana de marco extendido.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpriv.h  
   
### <a name="see-also"></a>Vea también  
 [CWnd (clase)](cwnd-class.md)   
 [CFrameWndEx (clase)](cframewndex-class.md)   

## <a name="afxismfctoolbar"></a> AfxIsMFCToolBar
Determina si la ventana dada es un objeto de barra de herramientas.  
   
### <a name="syntax"></a>Sintaxis    
```  
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);  
```
### <a name="parameters"></a>Parámetros  
 [in] `pWnd`  
 Un puntero a un objeto que se deriva de `CWnd`.  
   
### <a name="return-value"></a>Valor devuelto  
 `TRUE` Si la ventana proporcionada es un objeto de barra de herramientas; en caso contrario, `FALSE`.  
   
### <a name="remarks"></a>Comentarios  
 Este método devuelve `TRUE` si `pWnd` deriva de `CMFCToolBar`. Este método es útil cuando tenga que validar que un parámetro de función o un método es un `CMFCToolBar` objeto.  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxpriv.h  
   
### <a name="see-also"></a>Vea también  
 [CWnd (clase)](cwnd-class.md)   
 [CMFCToolBar (clase)](cmfctoolbar-class.md)

 
## <a name="afxkeyboardmanager"></a> AfxKeyboardManager
Puntero a la plantilla global [manager de teclado](ckeyboardmanager-class.md).  
   
### <a name="syntax"></a>Sintaxis    
```  
CKeyboardManager* afxKeyboardManager;  
```  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxkeyboardmanager.h  
   
### <a name="see-also"></a>Vea también  

 [Macros, funciones globales y Variables globales](mfc-macros-and-globals.md)   
 [CKeyboardManager (clase)](ckeyboardmanager-class.md)


##  <a name="afxloadlibrary"></a>  AfxLoadLibrary  
 Utilice `AfxLoadLibrary` para asignar un módulo de DLL.  
  
```   
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName); 
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszModuleName*  
 Señala a una cadena terminada en null que contiene el nombre del módulo (ya sea una. Archivo DLL o. Archivo ejecutable). El nombre especificado es el nombre de archivo del módulo.  
  
 Si la cadena especifica una ruta de acceso, pero el archivo no existe en el directorio especificado, se produce un error en la función.  
  
 Si no se especifica una ruta de acceso y se omite la extensión de nombre de archivo, la extensión predeterminada. Se anexa el archivo DLL. Sin embargo, la cadena de nombre de archivo puede incluir un carácter de punto final (.) para indicar que el nombre del módulo no tiene ninguna extensión. Cuando no se especifica ninguna ruta de acceso, la función busca el archivo en la siguiente secuencia:  
  
-   El directorio desde el que se carga la aplicación.  
  
-   El directorio actual.  
  
- **Windows 95 ó 98:** el directorio de sistema de Windows. **Windows NT:** el directorio del sistema de Windows de 32 bits. El nombre de este directorio es SYSTEM32.  
  
- **Sólo en Windows NT:** directorio del sistema de Windows de los 16 bits. No hay ninguna función de Win32 que obtiene la ruta de acceso de este directorio, pero se busca. El nombre de este directorio es sistema.  
  
-   El directorio de Windows.  
  
-   Los directorios que se muestran en la variable de entorno PATH.  
  
### <a name="return-value"></a>Valor devuelto  
 Si la función se realiza correctamente, el valor devuelto es un identificador para el módulo. Si se produce un error en la función, el valor devuelto es NULL.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve un identificador que se puede usar en [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) para obtener la dirección de una función DLL. `AfxLoadLibrary` También puede utilizarse para asignar otros módulos ejecutables.  
  
 Cada proceso mantiene un recuento de referencias para cada módulo de biblioteca cargada. Este recuento de referencias se incrementa cada vez que `AfxLoadLibrary` se llama y va disminuyendo cada vez que `AfxFreeLibrary` se llama. Cuando el recuento de referencias llega a cero, el módulo no está asignado desde el espacio de direcciones del proceso que realiza la llamada y el identificador ya no es válido.  
  
 Asegúrese de usar `AfxLoadLibrary` y `AfxFreeLibrary` (en lugar de las funciones de Win32 **LoadLibrary** y **FreeLibrary**) si la aplicación utiliza varios subprocesos y si carga dinámicamente a MFC archivo DLL de extensión. Usar `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y cierre que se ejecuta cuando se cargan y descargan el archivo DLL de extensión MFC no dañe el estado global de MFC.  
  
 Usando `AfxLoadLibrary` en una aplicación requiere que se vincule dinámicamente a la versión DLL de MFC; el archivo de encabezado para `AfxLoadLibrary`, Afxdll_.h, sólo está incluido si MFC está vinculado a la aplicación como un archivo DLL. Esto es así por diseño, porque se deben vincular a la versión del archivo DLL de MFC para utilizar o crear archivos DLL de extensión MFC.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]  
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxdll_.h  
   
## <a name="afxmenutearoffmanager"></a> AfxMenuTearOffManager
Puntero a la plantilla global [manager de menú divisible](cmenutearoffmanager-class.md).  
   
### <a name="syntax"></a>Sintaxis    
```  
CMenuTearOffManager* g_pTearOffMenuManager;  
```  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmenutearoffmanager.h  
   
### <a name="see-also"></a>Vea también     
 [CMenuTearOffManager (clase)](cmenutearoffmanager-class.md)
 
## <a name="afxmousemanager"></a>  AfxMouseManager
Puntero a la plantilla global [manager mouse](cmousemanager-class.md).  
   
### <a name="syntax"></a>Sintaxis  
  ```  
CMouseManager* afxMouseManager;  
```  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxmousemanager.h  
   
### <a name="see-also"></a>Vea también  
 [CMouseManager (clase)](cmousemanager-class.md)
 

  
##  <a name="afxregisterclass"></a>  AfxRegisterClass  
 Use esta función para registrar clases de ventana en un archivo DLL que utiliza MFC.  
  
```   
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass); 
```  
  
### <a name="parameters"></a>Parámetros  
 *lpWndClass*  
 Puntero a un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura que contiene información acerca de la clase de ventana que se registrará. Para obtener más información sobre esta estructura, vea el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si la clase está correctamente registrado; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Si usa esta función, la clase se elimina automáticamente cuando se descarga el archivo DLL.  
  
 En las compilaciones no DLL, el `AfxRegisterClass` identificador se define como una macro que se asigna a la función de Windows **RegisterClass**, ya que las clases que se registran en una aplicación se elimina automáticamente. Si usa `AfxRegisterClass` en lugar de **RegisterClass**, el código se puede utilizar sin cambios en una aplicación y en un archivo DLL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxregisterwndclass"></a>  AfxRegisterWndClass  
 Permite registrar sus propias clases de ventana.  
  
```  
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,  
    HCURSOR hCursor = 0,  
    HBRUSH hbrBackground = 0,  
    HICON hIcon = 0);  
```  
  
### <a name="parameters"></a>Parámetros  
 *nClassStyle*  
 Especifica el estilo de clase de Windows o una combinación de estilos, creado mediante la operación bit a bit OR ( **&#124;**) operador, para la clase de ventana. Para obtener una lista de estilos de clase, consulte el [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura en el SDK de Windows. Si **NULL**, los valores predeterminados se establecerá como se indica a continuación:  
  
-   Establece el estilo de mouse (ratón) en **CS_DBLCLKS**, que envía haga doble clic en los mensajes al procedimiento de ventana cuando el usuario hace doble clic del mouse.  
  
-   Establece el estilo de cursor de flecha en el estándar de Windows **IDC_ARROW**.  
  
-   Establece el pincel del fondo **NULL**, por lo que la ventana no borra el fondo.  
  
-   Establece el icono para el icono del logotipo de Windows estándar, marca mostrando.  
  
 `hCursor`  
 Especifica un identificador para el recurso de cursor que se va a instalarse en cada ventana creado a partir de la clase de ventana. Si utiliza el valor predeterminado de **0**, obtendrá el estándar **IDC_ARROW** cursor.  
  
 *hbrBackground*  
 Especifica un identificador para el recurso de pincel para instalarse en cada ventana creado a partir de la clase de ventana. Si utiliza el valor predeterminado de **0**, tendrá un **NULL** pincel del fondo y que la ventana, de forma predeterminada, no borran el fondo mientras se procesaba [WM_ERASEBKGND](http://msdn.microsoft.com/library/windows/desktop/ms648055).  
  
 `hIcon`  
 Especifica un identificador para el recurso de icono para instalarse en cada ventana creado a partir de la clase de ventana. Si utiliza el valor predeterminado de **0**, obtendrá el icono del logotipo de Windows estándar, marca mostrando.  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena terminada en null que contiene el nombre de clase. Puede pasar este nombre de clase para la **crear** función miembro en `CWnd` u otros **CWnd -** sus clases derivadas para crear una ventana. El nombre es generado por la biblioteca Microsoft Foundation Class.  
  
> [!NOTE]
>  El valor devuelto es un puntero a un búfer estático. Para guardar esta cadena, asígnelo a un `CString` variable.  
  
### <a name="remarks"></a>Comentarios  
 La biblioteca Microsoft Foundation Class registra automáticamente varias clases de ventana estándar para usted. Llame a esta función si desea registrar sus propias clases de ventana.  
  
 El nombre registrado para una clase `AfxRegisterWndClass` solamente depende de los parámetros. Si se llama a `AfxRegisterWndClass` varias veces con parámetros idénticos, sólo registra una clase en la primera llamada. Las llamadas subsiguientes a `AfxRegisterWndClass` con parámetros idénticos simplemente devuelve el nombre de clase ya registrado.  
  
 Si se llama a `AfxRegisterWndClass` para varias clases derivadas de CWnd con parámetros idénticos, en lugar de ver una clase de ventana independiente para cada clase, cada clase comparte la misma clase de ventana. Esto puede causar problemas si el **CS_CLASSDC** se utiliza el estilo de clase. En lugar de varios **CS_CLASSDC** clases de ventana, terminará con una **CS_CLASSDC** clase de ventana y todas las ventanas de C++ que utilizan que clase comparten el mismo controlador de dominio. Para evitar este problema, llame a [AfxRegisterClass](#afxregisterclass) para registrar la clase.  
  
 Consulte la nota técnica [TN001: registro de la clase de ventana](../../mfc/tn001-window-class-registration.md) para obtener más información sobre el registro de la clase de ventana y el `AfxRegisterWndClass` función.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
  
##  <a name="afxsetperuserregistration"></a>  AfxSetPerUserRegistration  
 Establece si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.  
  
```  
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```  
  
### <a name="parameters"></a>Parámetros  
 [in] `bEnable`  
 `TRUE` indica que la información de registro se dirige a la **HKCU** nodo; `FALSE` indica que la aplicación escribe información de registro en el nodo de forma predeterminada. El nodo de valor predeterminado es **HKEY_CLASSES_ROOT** ( **HKCR**).  
  
### <a name="remarks"></a>Comentarios  

Antes de Windows Vista, las aplicaciones que tiene acceso el registro normalmente se usa el **HKEY_CLASSES_ROOT** nodo. Sin embargo, con Windows Vista o sistemas operativos posteriores, debe ejecutar una aplicación en modo con privilegios elevados para escribir en **HKCR**.  
  
 Este método permite que la aplicación leer y escribir en el registro sin ejecutar en modo elevado redirigiendo el acceso al registro desde **HKCR** a **HKCU**. Para obtener más información, consulte [páginas de propiedades vinculador](../../ide/linker-property-pages.md).  
  
 Si habilita la redirección del registro, el marco de trabajo redirige el acceso de **HKCR** a **HKEY_CURRENT_USER\Software\Classes**. Solo los marcos de trabajo MFC y ATL se ven afectados por la redirección.  
  
 La implementación predeterminada obtiene acceso al registro en **HKCR**.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxstat_.h    
  
##  <a name="afxsetresourcehandle"></a>  AfxSetResourceHandle  
 Use esta función para establecer el `HINSTANCE` identificador que se determina que se cargan los recursos predeterminados de la aplicación.  
  
```  
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstResource`  
 El identificador de instancia o un módulo para un. Archivo EXE o DLL desde el que se cargarán los recursos de la aplicación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  

## <a name="afxshellmanager"></a>  AfxShellManager
Puntero a la plantilla global [manager shell](cshellmanager-class.md).  
   
### <a name="syntax"></a>Sintaxis    
```  
CShellManager* afxShellManager;  
```  

### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxshellmanager.h  
   
### <a name="see-also"></a>Vea también  
 [CShellManager (clase)](cshellmanager-class.md)
  
##  <a name="afxsocketinit"></a>  AfxSocketInit  
 Llame a esta función su `CWinApp::InitInstance` invalidación para inicializar Windows Sockets.  
  
```  
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpwsaData`  
 Un puntero a un [WSADATA](../../mfc/reference/wsadata-structure.md) estructura. Si `lpwsaData` no es igual a `NULL`, a continuación, la dirección de la `WSADATA` estructura se rellena por la llamada a `WSAStartup`. Esta función también garantiza que `WSACleanup` se llama automáticamente antes de que finalice la aplicación.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Al utilizar sockets de MFC en subprocesos secundarios en una aplicación MFC vinculado estáticamente, se debe llamar a `AfxSocketInit` en cada subproceso que usa sockets para inicializar las bibliotecas de socket. De forma predeterminada, `AfxSocketInit` se denomina solo en el subproceso principal.  
  
### <a name="requirements"></a>Requisitos  
  **Encabezado** afxsock.h  

## <a name="afxusertoolsmanager"></a>  AfxUserToolsManager
Puntero a la plantilla global [Administrador de herramientas de usuario](cusertoolsmanager-class.md).  
   
### <a name="syntax"></a>Sintaxis    
```  
CUserToolsManager* afxUserToolsManager;  
```  
   
### <a name="requirements"></a>Requisitos  
 **Encabezado:** afxusertoolsmanager.h  
   
### <a name="see-also"></a>Vea también  
 [CUserToolsManager (clase)](cusertoolsmanager-class.md)
 
  
##  <a name="afxwininit"></a>  AfxWinInit  
 Esta función llama a la suministrada en MFC `WinMain` función, como parte de la [CWinApp](../../mfc/reference/cwinapp-class.md) inicialización de una aplicación basada en GUI, inicializar MFC.  
  
```  
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,  
    HINSTANCE hPrevInstance,  
    LPTSTR lpCmdLine,  
    int nCmdShow);  
```  
  
### <a name="parameters"></a>Parámetros  
 `hInstance`  
 El identificador del módulo que se está ejecutando.  
  
 *hPrevInstance*  
 Un identificador para una instancia anterior de la aplicación. Para una aplicación basada en Win32, este parámetro es siempre **NULL**.  
  
 `lpCmdLine`  
 Apunta a una cadena terminada en null que especifica la línea de comandos para la aplicación.  
  
 `nCmdShow`  
 Especifica cómo se mostrará la ventana principal de una aplicación de interfaz gráfica de usuario.  
  
### <a name="remarks"></a>Comentarios  
 Para una aplicación de consola que no usa MFC proporcionado `WinMain` función, se debe llamar a `AfxWinInit` directamente para inicializar MFC.  
  
 Si se llama a `AfxWinInit` usted mismo, debe declarar una instancia de un `CWinApp` clase. Para una aplicación de consola, puede elegir no derivar su propia clase de `CWinApp` y en su lugar, use una instancia de `CWinApp` directamente. Esta técnica es apropiada si decide dejar toda la funcionalidad de la aplicación en la implementación de **principal**.  
  
> [!NOTE]
>  Cuando crea un contexto de activación de un ensamblado, MFC usa un recurso del manifiesto proporcionado por el módulo de usuario. El contexto de activación se crea en `AfxWinInit`. Para obtener más información, consulte [compatibilidad con contextos de activación en el estado del módulo MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]  

### <a name="requirements"></a>Requisitos  
  **Encabezado** afxwin.h  
    
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)
