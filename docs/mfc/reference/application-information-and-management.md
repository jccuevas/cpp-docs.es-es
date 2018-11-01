---
title: Información y administración de aplicaciones
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: 71b5eb9c97b8c6370a08281fdf4be7074a579f8f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596669"
---
# <a name="application-information-and-management"></a>Información y administración de aplicaciones

Al escribir una aplicación, cree una sola [CWinApp](../../mfc/reference/cwinapp-class.md)-objeto derivado. En ocasiones, es posible que desea obtener información acerca de este objeto desde fuera de la `CWinApp`-objeto derivado. O bien, puede que necesite acceso a otros objetos globales "Manager".

La biblioteca Microsoft Foundation Class proporciona las siguientes funciones globales para ayudarle a realizar estas tareas:

### <a name="application-information-and-management-functions"></a>Información de la aplicación y las funciones de administración

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Crea un nuevo subproceso.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Puntero a la plantilla global [Administrador de menús de contexto](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Finaliza el subproceso actual.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Recorre la cadena de recursos y busque un identificador de recurso por recurso específico y el tipo de recurso. |
|[AfxFreeLibrary](#afxfreelibrary)|Disminuye el recuento de referencias del módulo cargado biblioteca de vínculos dinámicos (DLL); Cuando el recuento de referencias llega a cero, el módulo no está asignado.|
|[AfxGetApp](#afxgetapp)|Devuelve el único de un puntero a la aplicación del `CWinApp` objeto.|
|[AfxGetAppName](#afxgetappname)|Devuelve una cadena que contiene el nombre de la aplicación.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Devuelve un objeto HINSTANCE que representa esta instancia de la aplicación.|
|[AfxGetMainWnd](#afxgetmainwnd)|Devuelve un puntero a la ventana actual "principal" de una aplicación que no son compatibles con OLE, o la ventana de marco en contexto de una aplicación de servidor.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Utilice esta función para determinar si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Devuelve un objeto HINSTANCE al origen de los recursos predeterminados de la aplicación. Utilice esto para tener acceso a recursos de la aplicación directamente.|
|[AfxGetThread](#afxgetthread)|Recupera un puntero a la actual [CWinThread](../../mfc/reference/cwinthread-class.md) objeto.|
|[AfxInitRichEdit](#afxinitrichedit)|Inicializa la versión 1.0 enriquecido editar control para la aplicación.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicializa la versión 2.0 y versiones posterior enriquecido editar control para la aplicación.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Determina si la ventana dada es un objeto de marco extendido.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Determina si la ventana dada es un objeto de barra de herramientas.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Puntero a la plantilla global [manager teclado](ckeyboardmanager-class.md).|
|[AfxLoadLibrary](#afxloadlibrary)|Un módulo DLL se asigna y devuelve un identificador que puede usarse para obtener la dirección de una función DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Puntero a la plantilla global [manager de menú divisible](cmenutearoffmanager-class.md).|
|[AfxMouseManager](#afxmousemanager)|Puntero a la plantilla global [manager mouse](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Registra una clase de ventana en un archivo DLL que utiliza MFC.|
|[AfxRegisterWndClass](#afxregisterwndclass)|Registra una clase de ventana de Windows para complementarlos registrados automáticamente por MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Establece si la aplicación redirige el acceso de registro a la **HKEY_CURRENT_USER** ( **HKCU**) nodo.|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Establece el identificador HINSTANCE donde se cargan los recursos predeterminados de la aplicación.|
|[AfxShellManager](#afxshellmanager)|Puntero a la plantilla global [manager shell](cshellmanager-class.md). |
|[AfxSocketInit](#afxsocketinit)|Llamado en un `CWinApp::InitInstance` invalidar para inicializar Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Puntero a la plantilla global [Administrador de las herramientas de usuario](cusertoolsmanager-class.md).|
|[AfxWinInit](#afxwininit)|Lo llama el proporcionado por MFC `WinMain` función, como parte de la [CWinApp](../../mfc/reference/cwinapp-class.md) inicialización de una aplicación basada en GUI, inicializar MFC. Debe llamarse directamente para las aplicaciones de consola que utilizan la biblioteca MFC.|

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

*pfnThreadProc*<br/>
Apunta a la función controladora para el subproceso de trabajo. No puede ser nulo. Esta función debe declararse como sigue:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*<br/>
La clase RUNTIME_CLASS de un objeto derivado de [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*<br/>
Parámetro que se pasará a la función controladora como se muestra en el parámetro de la declaración de función en *pfnThreadProc*.

*nPriority*<br/>
La prioridad deseada del subproceso. Para una lista completa y una descripción de las prioridades disponibles, consulte [SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el SDK de Windows.

*nStackSize*<br/>
Especifica el tamaño en bytes de la pila para el nuevo subproceso. Si es 0, el tamaño de pila predeterminado es el mismo tamaño de pila como del subproceso creador.

*dwCreateFlags*<br/>
Especifica un mensaje adicional que controla la creación del subproceso. Este indicador puede contener uno de dos valores:

- CREATE_SUSPENDED iniciar el subproceso con un recuento de suspensión de uno. Utilice CREATE_SUSPENDED si desea inicializar los datos de miembro de la `CWinThread` objetos, como [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) o los miembros de la clase derivada, antes de que el subproceso empieza a ejecutarse. Una vez completada la inicialización, utilice [CWinThread:: ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) para iniciar el subproceso que se ejecuta. El subproceso no se ejecutará hasta `CWinThread::ResumeThread` se llama.

- **0** iniciar el subproceso inmediatamente después de crear.

*lpSecurityAttrs*<br/>
Apunta a un [SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica los atributos de seguridad para el subproceso. Si es NULL, se utilizará los mismos atributos de seguridad que del subproceso creador. Para obtener más información sobre esta estructura, consulte el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de subproceso recién creado, o NULL si se produce un error.

### <a name="remarks"></a>Comentarios

El primer formulario del `AfxBeginThread` crea un subproceso de trabajo. El segundo formulario crea un subproceso que puede actuar como un subproceso de interfaz de usuario o como un subproceso de trabajo.

`AfxBeginThread` crea un nuevo `CWinThread` (objeto), llama a su [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) funcionan para empezar a ejecutar el subproceso y devuelve un puntero al subproceso. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación. Para finalizar el subproceso, llame a [AfxEndThread](#afxendthread) desde dentro del subproceso o el valor devuelto de la función controladora del subproceso de trabajo.

Multithreading se debe habilitar la aplicación; en caso contrario, se producirá un error en esta función. Para obtener más información sobre la habilitación de multithreading, consulte [/MD, / MT, /LD (utilizar la biblioteca de tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md) en *opciones del compilador de Visual C++*.

Para obtener más información sobre `AfxBeginThread`, consulte los artículos [Multithreading: crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md) y [Multithreading: crear subprocesos de la interfaz de usuario](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CSocket:: Attach](../../mfc/reference/csocket-class.md#attach).

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

*nExitCode*<br/>
Especifica el código de salida del subproceso.

*bDelete*<br/>
Elimina el objeto de subproceso de la memoria.

### <a name="remarks"></a>Comentarios

Debe llamarse desde dentro del subproceso que se finalice.

Para obtener más información sobre `AfxEndThread`, consulte el artículo [Multithreading: Finalizar subprocesos](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

  ## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle
Use `AfxFindResourceHandle` para recorrer la cadena de recursos y busque un tipo específico de recursos y el Id. de recurso por recurso.

### <a name="syntax"></a>Sintaxis

```
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parámetros

*lpszName*<br/>
Un puntero a una cadena que contiene el identificador de recurso.
*lpszType*<br/>
Un puntero al tipo de recurso. Para obtener una lista de tipos de recursos, consulte [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) en el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Un identificador para el módulo que contiene el recurso.

### <a name="remarks"></a>Comentarios

`AfxFindResourceHandle` busca el recurso específico y devuelve un identificador para el módulo que contiene el recurso. El recurso podría estar en cualquier extensión que ha cargado la DLL de MFC. `AfxFindResourceHandle` indica cuál de ellos tiene el recurso.

Los módulos se buscan en este orden:

1. El módulo principal (si es un archivo DLL de extensión MFC).

1. Módulos que no son del sistema.

1. Módulos específicos del idioma.

1. El módulo principal (si es un archivo DLL del sistema).

1. Módulos del sistema.

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

*hInstLib*<br/>
Identificador del módulo de biblioteca cargada. [AfxLoadLibrary](#afxloadlibrary) devuelve este identificador.

### <a name="return-value"></a>Valor devuelto

TRUE si la función se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

`AfxFreeLibrary` disminuye el recuento de referencias del módulo cargado biblioteca de vínculos dinámicos (DLL). Cuando el recuento de referencias llega a cero, el módulo no está asignado desde el espacio de direcciones del proceso que realiza la llamada y el identificador ya no es válido. Este recuento de referencias se incrementa cada vez `AfxLoadLibrary` se llama.

Antes de la desasignación de un módulo de biblioteca, el sistema permite que el archivo DLL se desasocie de los procesos que lo usan. Esto le proporciona la DLL de una oportunidad para limpiar los recursos asignados en nombre del proceso actual. Después de que se devuelva la función de punto de entrada, el módulo de biblioteca se quita el espacio de direcciones del proceso actual.

Use `AfxLoadLibrary` para asignar un módulo de DLL.

Procure usar `AfxFreeLibrary` y `AfxLoadLibrary` (en lugar de las funciones de Win32 `FreeLibrary` y `LoadLibrary`) si la aplicación utiliza varios subprocesos. Uso de `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y apagado que se ejecuta cuando la extensión se carga y descarga el archivo DLL de MFC no dañe el estado global de MFC.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdll_.h

##  <a name="afxgetapp"></a>  AfxGetApp

El puntero devuelto por esta función puede utilizarse para tener acceso a información de la aplicación como el código de envío de mensajes principal o la ventana de nivel superior.

```
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la única `CWinApp` objeto de la aplicación.

### <a name="remarks"></a>Comentarios

Si este método devuelve NULL, podría indicar que la ventana principal de la aplicación no ha totalmente inicializada aún. También podría indicar un problema.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

##  <a name="afxgetappname"></a>  AfxGetAppName

La cadena devuelta por esta función puede utilizarse para mensajes de diagnóstico o como una raíz para los nombres de cadena temporal.

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

HINSTANCE para la instancia actual de la aplicación. Si se llama desde dentro de un archivo DLL vinculado con la versión de archivo USRDLL de MFC, se devuelve HINSTANCE al archivo DLL.

### <a name="remarks"></a>Comentarios

`AfxGetInstanceHandle` siempre devuelve el HINSTANCE del archivo ejecutable (. (EXE) a menos que se llama desde un archivo DLL vinculado con la versión de archivo USRDLL de MFC. En este caso, devuelve un objeto HINSTANCE al archivo DLL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

##  <a name="afxgetmainwnd"></a>  AfxGetMainWnd

Si la aplicación es un servidor OLE, llame a esta función para recuperar un puntero a la ventana principal activa de la aplicación en lugar de hacer referencia directamente a la [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) miembro del objeto de aplicación.

```
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Valor devuelto

Si el servidor tiene un objeto que está activo en contexto dentro de un contenedor y ese contenedor está activo, la función devuelve un puntero al objeto de ventana marco que contiene el documento activo en contexto.

Si no hay ningún objeto que está activo en contexto dentro de un contenedor o la aplicación no es un servidor OLE, esta función devuelve simplemente el *m_pMainWnd* del objeto de aplicación.

Si se llama a `AfxGetMainWnd` desde el subproceso principal de la aplicación, devuelve la ventana principal de la aplicación según las reglas anteriores. Si se llama a la función desde un subproceso secundario de la aplicación, la función devuelve la ventana principal asociada al subproceso que realizó la llamada.

### <a name="remarks"></a>Comentarios

Si la aplicación no es un servidor OLE, llamar a esta función es equivalente a hacer referencia directamente a la *m_pMainWnd* miembro del objeto de aplicación.

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

TRUE indica que la información del registro se dirige al nodo HKCU; FALSE indica que la aplicación escribe información del registro en el nodo de forma predeterminada. El nodo de valor predeterminado es **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Comentarios

Si habilita la redirección del registro, el marco de trabajo redirige el acceso desde **HKCR** a **HKEY_CURRENT_USER\Software\Classes**. Solo los marcos de trabajo MFC y ATL se ven afectados por la redirección.

Para cambiar si la aplicación redirige el acceso al registro, use [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxstat_.h

##  <a name="afxgetresourcehandle"></a>  AfxGetResourceHandle

Use controlar HINSTANCE devuelto por esta función para obtener acceso a recursos de la aplicación directamente, por ejemplo, en las llamadas a la Windows función `FindResource`.

```
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Valor devuelto

Un identificador HINSTANCE donde se cargan los recursos predeterminados de la aplicación.

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

Puntero en el subproceso actualmente en ejecución; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Debe llamarse desde dentro del subproceso deseado.

> [!NOTE]
>  Si va a trasladar una llamada de proyecto MFC `AfxGetThread` de versiones de Visual C++ 4.2, 5.0 ó 6.0, `AfxGetThread` llamadas [AfxGetApp](#afxgetapp) si no se encuentra ningún subproceso. En las versiones más recientes del compilador, `AfxGetThread` devuelve NULL si no se encontró ningún subproceso. Si desea que el subproceso de la aplicación, debe llamar a `AfxGetApp`.

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

`AfxInitRichEdit` carga RICHED32. Archivo DLL para inicializar la versión 1.0 del control rich edit. Para usar la versión 2.0 y 3.0 del control rich edit, RICHED20. Archivo DLL debe cargarse. Esto se logra con una llamada a [AfxInitRichEdit2](#afxinitrichedit2).

Para actualizar los controles de edición enriquecida en aplicaciones de Visual C++ existentes a la versión 2.0, abra el. Archivo RC como texto, cambie el nombre de clase de cada control rich edit de "RICHEDIT" a "RichEdit20a". A continuación, reemplace la llamada a `AfxInitRichEdit` con `AfxInitRichEdit2`.

Esta función también inicializa la biblioteca de controles comunes, si aún no se ha inicializado la biblioteca para el proceso. Si utiliza el control rich edit directamente desde la aplicación MFC, debe llamar a esta función para asegurarse de que MFC ha inicializado correctamente el tiempo de ejecución del control de edición enriquecida. Si llama al método Create de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), o [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), normalmente no es necesario llamar a esta función, pero en algunos casos podría ser es necesario.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

##  <a name="afxinitrichedit2"></a>  AfxInitRichEdit2

Llame a esta función para inicializar el control rich edit (versión 2.0 y versiones posterior) para la aplicación.

```
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Comentarios

Llame a esta función para cargar el RICHED20. Archivo DLL e inicialice la versión 2.0 de la amplia el control de edición. Si llama al método Create de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md), o [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), normalmente no es necesario llamar a esta función, pero en algunos casos podría ser es necesario.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

  ## <a name="afxisextendedframeclass"></a>  AfxIsExtendedFrameClass
Determina si la ventana dada es un objeto de marco extendido.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
[in] Un puntero a un objeto que se deriva de `CWnd`.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana proporcionada es un objeto de marco extendido; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método devuelve TRUE si *conquistado* deriva de una de las clases siguientes:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Este método es útil cuando tiene que validar que un parámetro de función o método es una ventana de marco extendido.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

### <a name="see-also"></a>Vea también

[CWnd (clase)](cwnd-class.md)<br/>
[CFrameWndEx (clase)](cframewndex-class.md)

## <a name="afxismfctoolbar"></a> AfxIsMFCToolBar

Determina si la ventana dada es un objeto de barra de herramientas.

### <a name="syntax"></a>Sintaxis

```
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*conquistado*<br/>
[in] Un puntero a un objeto que se deriva de `CWnd`.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana proporcionada es un objeto de la barra de herramientas; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método devuelve `TRUE` si *conquistado* deriva `CMFCToolBar`. Este método es útil cuando tiene que validar que un parámetro de función o método es un `CMFCToolBar` objeto.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

### <a name="see-also"></a>Vea también

[CWnd (clase)](cwnd-class.md)<br/>
[CMFCToolBar (clase)](cmfctoolbar-class.md)

## <a name="afxkeyboardmanager"></a> AfxKeyboardManager

Puntero a la plantilla global [manager teclado](ckeyboardmanager-class.md).

### <a name="syntax"></a>Sintaxis

```
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxkeyboardmanager.h

### <a name="see-also"></a>Vea también

[Macros, funciones globales y Variables globales](mfc-macros-and-globals.md)<br/>
[CKeyboardManager (clase)](ckeyboardmanager-class.md)

##  <a name="afxloadlibrary"></a>  AfxLoadLibrary

Use `AfxLoadLibrary` para asignar un módulo de DLL.

```
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parámetros

*lpszModuleName*<br/>
Señala a una cadena terminada en null que contiene el nombre del módulo (ya sea una. Archivo DLL o. Archivo ejecutable). El nombre especificado es el nombre de archivo del módulo.

Si la cadena especifica una ruta de acceso, pero el archivo no existe en el directorio especificado, se produce un error en la función.

Si no se especifica una ruta de acceso y se omite la extensión de nombre de archivo, la extensión predeterminada. Se anexa el archivo DLL. Sin embargo, la cadena de nombre de archivo puede incluir un carácter de punto final (.) para indicar que el nombre del módulo no tiene ninguna extensión. Cuando no se especifica ninguna ruta de acceso, la función busca el archivo en la siguiente secuencia:

- El directorio desde el que se carga la aplicación.

- El directorio actual.

- **Windows 95/98:** el directorio del sistema de Windows. **Windows NT:** el directorio del sistema de Windows de 32 bits. El nombre de este directorio es SYSTEM32.

- **Sólo en Windows NT:** directorio del sistema de Windows de los 16 bits. No hay ninguna función de Win32 que obtiene la ruta de acceso de este directorio, pero se va a buscar. El nombre de este directorio es el sistema.

- El directorio de Windows.

- Los directorios que se muestran en la variable de entorno PATH.

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es un identificador para el módulo. Si se produce un error en la función, el valor devuelto es NULL.

### <a name="remarks"></a>Comentarios

Devuelve un identificador que se puede usar en [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) para obtener la dirección de una función DLL. `AfxLoadLibrary` También puede usarse para asignar otros módulos ejecutables.

Cada proceso mantiene un recuento de referencias para cada módulo de biblioteca cargada. Este recuento de referencias se incrementa cada vez `AfxLoadLibrary` se llama y disminuye cada vez que `AfxFreeLibrary` se llama. Cuando el recuento de referencias llega a cero, el módulo no está asignado desde el espacio de direcciones del proceso que realiza la llamada y el identificador ya no es válido.

Procure usar `AfxLoadLibrary` y `AfxFreeLibrary` (en lugar de las funciones de Win32 `LoadLibrary` y `FreeLibrary`) si la aplicación usa varios subprocesos y si carga dinámicamente un archivo DLL de extensión MFC. Uso de `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión MFC no dañe el estado global de MFC.

Mediante `AfxLoadLibrary` en una aplicación requiere que se vincule dinámicamente a la versión de DLL de MFC; el archivo de encabezado para `AfxLoadLibrary`, Afxdll_.h, sólo está incluido si MFC está vinculado a la aplicación como un archivo DLL. Esto es así por diseño porque tiene un vínculo a la versión DLL de MFC para usar o crear archivos DLL de extensión MFC.

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

*lpWndClass*<br/>
Puntero a un [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) estructura que contiene información acerca de la clase de ventana que se registrarán. Para obtener más información sobre esta estructura, consulte el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

TRUE si la clase se ha registrado correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si usa esta función, la clase se elimina automáticamente cuando se descarga el archivo DLL.

En las compilaciones que no son DLL, el `AfxRegisterClass` identificador se define como una macro que se asigna a la función de Windows `RegisterClass`, ya que las clases que se registran en una aplicación se elimina automáticamente. Si usas `AfxRegisterClass` en lugar de `RegisterClass`, se puede usar el código sin cambios en una aplicación y en un archivo DLL.

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

*nClassStyle*<br/>
Especifica el estilo de clase de Windows o una combinación de estilos, creados mediante el uso de la operación bit a bit OR ( **&#124;**) operador para la clase de ventana. Para obtener una lista de estilos de clase, vea el [WNDCLASS](https://msdn.microsoft.com/library/windows/desktop/ms633576) estructura en el SDK de Windows. Si es NULL, los valores predeterminados se establecerá como sigue:

- Establece el estilo del mouse en CS_DBLCLKS, que envía haga doble clic en los mensajes al procedimiento de ventana cuando el usuario hace doble clic del mouse.

- Establece el estilo de cursor de flecha a la IDC_ARROW estándar de Windows.

- Establece el pincel del fondo en NULL, por lo que la ventana no borrará el fondo.

- Establece el icono en el icono del logotipo de Windows estándar, marca saludando.

*hCursor*<br/>
Especifica un identificador para el recurso de cursor para instalarse en cada ventana creado a partir de la clase de ventana. Si usa el valor predeterminado de **0**, obtendrá el cursor IDC_ARROW estándar.

*hbrBackground*<br/>
Especifica un identificador para el recurso de pincel para instalarse en cada ventana creado a partir de la clase de ventana. Si usa el valor predeterminado de **0**, tendrá un pincel de fondo es NULL, y la ventana, de forma predeterminada, no borrará el fondo mientras se procesaba [WM_ERASEBKGND](/windows/desktop/winmsg/wm-erasebkgnd).

*hIcon*<br/>
Especifica un identificador para el recurso de icono para instalarse en cada ventana creado a partir de la clase de ventana. Si usa el valor predeterminado de **0**, obtendrá el icono del logotipo de Windows estándar, marca saludando.

### <a name="return-value"></a>Valor devuelto

Una cadena terminada en null que contiene el nombre de clase. Puede pasar este nombre de clase a la `Create` función miembro en `CWnd` u otros **CWnd -** sus clases derivadas para crear una ventana. El nombre es generado por la biblioteca Microsoft Foundation Class.

> [!NOTE]
>  El valor devuelto es un puntero a un búfer estático. Para guardar esta cadena, asígnelo a un `CString` variable.

### <a name="remarks"></a>Comentarios

La biblioteca Microsoft Foundation Class registra automáticamente varias clases de ventana estándar para usted. Llame a esta función si desea registrar sus propias clases de ventana.

El nombre registrado para una clase `AfxRegisterWndClass` depende exclusivamente de los parámetros. Si se llama a `AfxRegisterWndClass` varias veces con parámetros idénticos, sólo registra una clase en la primera llamada. Las llamadas subsiguientes a `AfxRegisterWndClass` con parámetros idénticos simplemente devolver el nombre de clase ya registrado.

Si se llama a `AfxRegisterWndClass` para varias clases derivadas de CWnd con parámetros idénticos, en lugar de obtener una clase de ventana independiente para cada clase, cada clase comparte la misma clase de ventana. Esto puede causar problemas si se usa el estilo de clase CS_CLASSDC. En lugar de varias clases de ventana CS_CLASSDC, terminará con una clase de ventana CS_CLASSDC y todas las ventanas de C++ que usen ese recurso compartido de clase el mismo controlador de dominio. Para evitar este problema, llame a [AfxRegisterClass](#afxregisterclass) para registrar la clase.

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

*bHabilitar el*<br/>
[in] TRUE indica que la información del registro se dirige al nodo HKCU; FALSE indica que la aplicación escribe información del registro en el nodo de forma predeterminada. El nodo de valor predeterminado es **HKEY_CLASSES_ROOT** ( **HKCR**).

### <a name="remarks"></a>Comentarios

Antes de Windows Vista, las aplicaciones que tiene acceso el registro suele usarse el **HKEY_CLASSES_ROOT** nodo. Sin embargo, con Windows Vista o sistemas operativos posteriores, debe ejecutar una aplicación en modo con privilegios elevados para escribir en HKCR.

Este método permite que la aplicación leer y escribir en el registro sin que se ejecuta en modo con privilegios elevados mediante el redireccionamiento de acceso al registro de HKCR en HKCU. Para obtener más información, consulta [Linker Property Pages](../../ide/linker-property-pages.md).

Si habilita la redirección del registro, el marco de trabajo redirige el acceso desde HKCR **HKEY_CURRENT_USER\Software\Classes**. Solo los marcos de trabajo MFC y ATL se ven afectados por la redirección.

La implementación predeterminada obtiene acceso al registro en HKCR.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxstat_.h

##  <a name="afxsetresourcehandle"></a>  AfxSetResourceHandle

Utilice esta función para establecer el identificador HINSTANCE que determina dónde se cargan los recursos predeterminados de la aplicación.

```
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parámetros

*hInstResource*<br/>
El identificador de instancia o módulo una. Archivo EXE o DLL desde el que se cargan los recursos de la aplicación.

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

Llame a esta función su `CWinApp::InitInstance` invalidar para inicializar Windows Sockets.

```
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parámetros

*lpwsaData*<br/>
Un puntero a un [WSADATA](../../mfc/reference/wsadata-structure.md) estructura. Si *lpwsaData* no es igual a NULL, a continuación, la dirección de la `WSADATA` estructura se rellena mediante la llamada a `WSAStartup`. Esta función también garantiza que `WSACleanup` es llamado automáticamente antes de que termine la aplicación.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Cuando se usa sockets MFC en subprocesos secundarios en una aplicación MFC vinculada estáticamente, debe llamar a `AfxSocketInit` en cada subproceso que usa sockets para inicializar las bibliotecas de socket. De forma predeterminada, `AfxSocketInit` se llama sólo en el subproceso principal.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxsock.h

## <a name="afxusertoolsmanager"></a>  AfxUserToolsManager

Puntero a la plantilla global [Administrador de las herramientas de usuario](cusertoolsmanager-class.md).

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

*hInstance*<br/>
El identificador del módulo que se está ejecutando.

*hPrevInstance*<br/>
Identificador de una instancia anterior de la aplicación. Para una aplicación basada en Win32, este parámetro siempre es **NULL**.

*lpCmdLine*<br/>
Apunta a una cadena terminada en null que se especifica la línea de comandos para la aplicación.

*nCmdShow*<br/>
Especifica cómo se muestra la ventana principal de una aplicación de interfaz gráfica de usuario.

### <a name="remarks"></a>Comentarios

Para una aplicación de consola que no usa MFC proporcionado `WinMain` función, debe llamar a `AfxWinInit` directamente para inicializar MFC.

Si se llama a `AfxWinInit` usted mismo, debe declarar una instancia de un `CWinApp` clase. Para una aplicación de consola, puede elegir no derivar su propia clase de `CWinApp` y en su lugar, use una instancia de `CWinApp` directamente. Esta técnica es apropiada si decide dejar toda la funcionalidad de la aplicación en la implementación de **principal**.

> [!NOTE]
>  Cuando crea un contexto de activación de un ensamblado, MFC usa un recurso de manifiesto proporcionado por el módulo de usuario. El contexto de activación se crea en `AfxWinInit`. Para obtener más información, consulte [compatibilidad con contextos de activación en el estado del módulo MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CWinApp (clase)](../../mfc/reference/cwinapp-class.md)
