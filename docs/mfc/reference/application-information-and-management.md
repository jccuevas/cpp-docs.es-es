---
title: Información y administración de aplicaciones
description: Referencia a la información de la aplicación y a las funciones de administración de la biblioteca MFC (Microsoft Foundation Class).
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: c372f43bc5184349e70f29b6c0ae6a490f2102ed
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854597"
---
# <a name="application-information-and-management"></a>Información y administración de aplicaciones

Cuando se escribe una aplicación, se crea un único objeto derivado de [CWinApp](../../mfc/reference/cwinapp-class.md). En ocasiones, puede que desee obtener información sobre este objeto desde fuera del objeto derivado de `CWinApp`. O bien, puede que necesite tener acceso a otros objetos globales de "administrador".

El biblioteca MFC proporciona las siguientes funciones globales para ayudarle a llevar a cabo estas tareas:

## <a name="application-information-and-management-functions"></a>Funciones de administración e información de la aplicación

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Crea un nuevo subproceso.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Puntero al administrador global del [menú contextual](ccontextmenumanager-class.md).|
|[AfxEndThread](#afxendthread)|Finaliza el subproceso actual.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Recorre la cadena de recursos y localiza un recurso específico por identificador de recurso y tipo de recurso. |
|[AfxFreeLibrary](#afxfreelibrary)|Disminuye el recuento de referencias del módulo cargado de la biblioteca de vínculos dinámicos (DLL). Cuando el recuento de referencias llega a cero, el módulo se desasigna.|
|[AfxGetApp](#afxgetapp)|Devuelve un puntero al objeto de `CWinApp` único de la aplicación.|
|[AfxGetAppName](#afxgetappname)|Devuelve una cadena que contiene el nombre de la aplicación.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Devuelve un HINSTANCE que representa esta instancia de la aplicación.|
|[AfxGetMainWnd](#afxgetmainwnd)|Devuelve un puntero a la ventana "principal" actual de una aplicación que no es OLE, o la ventana de marco en contexto de una aplicación de servidor.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Utilice esta función para determinar si la aplicación redirige el acceso del registro al nodo **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Devuelve un HINSTANCE al origen de los recursos predeterminados de la aplicación. Utilice para tener acceso directamente a los recursos de la aplicación.|
|[AfxGetThread](#afxgetthread)|Recupera un puntero al objeto [CWinThread](../../mfc/reference/cwinthread-class.md) actual.|
|[AfxInitRichEdit](#afxinitrichedit)|Inicializa el control Rich Edit de la versión 1,0 para la aplicación.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicializa el control de edición enriquecida de la versión 2,0 y posterior de la aplicación.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Determina si la ventana dada es un objeto de marco extendido.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Determina si la ventana dada es un objeto de barra de herramientas.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Puntero al administrador de [teclado](ckeyboardmanager-class.md)global.|
|[AfxLoadLibrary](#afxloadlibrary)|Asigna un módulo DLL y devuelve un identificador que se puede usar para obtener la dirección de una función DLL.|
|[AfxLoadLibraryEx](#afxloadlibraryex)|Asigna un módulo DLL con las opciones especificadas y devuelve un identificador que se puede usar para obtener la dirección de una función DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Puntero al [Administrador de menús de recorte](cmenutearoffmanager-class.md)global.|
|[AfxMouseManager](#afxmousemanager)|Puntero al administrador global [del mouse](cmousemanager-class.md).|
|[AfxRegisterClass](#afxregisterclass)|Registra una clase de ventana en un archivo DLL que utiliza MFC.|
|[AfxRegisterWndClass (](#afxregisterwndclass)|Registra una clase de ventana de Windows para complementar las registradas automáticamente por MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Establece si la aplicación redirige el acceso del registro al nodo **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Establece el identificador de HINSTANCE donde se cargan los recursos predeterminados de la aplicación.|
|[AfxShellManager](#afxshellmanager)|Puntero al administrador de [Shell](cshellmanager-class.md)global. |
|[AfxSocketInit](#afxsocketinit)|Se llama en una invalidación `CWinApp::InitInstance` para inicializar Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Puntero al administrador de [herramientas de usuario](cusertoolsmanager-class.md)global.|
|[AfxWinInit](#afxwininit)|Lo llama la función de `WinMain` proporcionada por MFC, como parte de la inicialización de [CWinApp](../../mfc/reference/cwinapp-class.md) de una aplicación basada en GUI, para inicializar MFC. Se debe llamar directamente a para las aplicaciones de consola que utilizan MFC.|

## <a name="afxbeginthread"></a>AfxBeginThread

Llame a esta función para crear un nuevo subproceso.

```cpp
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

\ *pfnThreadProc*
Apunta a la función de control del subproceso de trabajo. El puntero no puede ser NULL. Esta función debe declararse de la siguiente manera:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

\ *pThreadClass*
RUNTIME_CLASS de un objeto derivado de [CWinThread](../../mfc/reference/cwinthread-class.md).

\ *pParam*
Parámetro que se va a pasar a la función controladora.

\ *nPriority*
Prioridad que se va a establecer para el subproceso. Para obtener una lista completa y una descripción de las prioridades disponibles, consulte [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el Windows SDK.

\ *nStackSize*
Especifica el tamaño en bytes de la pila para el nuevo subproceso. Si es 0, el valor predeterminado del tamaño de la pila es el mismo que el del subproceso de creación.

\ *dwCreateFlags*
Especifica una marca adicional que controla la creación del subproceso. Esta marca puede contener uno de dos valores:

- CREATE_SUSPENDED iniciar el subproceso con un recuento de suspensión de uno. Use CREATE_SUSPENDED si desea inicializar los datos de miembro del `CWinThread` objeto, como [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) o cualquier miembro de la clase derivada, antes de que el subproceso empiece a ejecutarse. Una vez completada la inicialización, use [CWinThread:: ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) para iniciar el subproceso que se está ejecutando. El subproceso no se ejecutará hasta que se llame a `CWinThread::ResumeThread`.

- **0** inicie el subproceso inmediatamente después de la creación.

\ *lpSecurityAttrs*
Apunta a una estructura de [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica los atributos de seguridad para el subproceso. Si es NULL, se usan los mismos atributos de seguridad que el subproceso de creación. Para obtener más información sobre esta estructura, vea el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de subproceso recién creado o NULL si se produce un error.

### <a name="remarks"></a>Observaciones

La primera forma de `AfxBeginThread` crea un subproceso de trabajo. En el segundo formulario se crea un subproceso que puede actuar como un subproceso de la interfaz de usuario o como un subproceso de trabajo.

`AfxBeginThread` crea un nuevo objeto `CWinThread`, llama a la función [CreateThread](../../mfc/reference/cwinthread-class.md#createthread) para empezar a ejecutar el subproceso y devuelve un puntero al subproceso. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación. Para finalizar el subproceso, llame a [AfxEndThread](#afxendthread) desde dentro del subproceso o vuelva de la función de control del subproceso de trabajo.

La aplicación debe habilitar el multithreading; de lo contrario, se producirá un error en esta función. Para obtener más información sobre cómo habilitar el multithreading, vea [/MD,/MT,/LD (usar la biblioteca en tiempo de ejecución)](../../build/reference/md-mt-ld-use-run-time-library.md).

Para obtener más información sobre `AfxBeginThread`, vea los artículos [multithreading: crear](../../parallel/multithreading-creating-worker-threads.md) subprocesos de trabajo y [multithreading: crear subprocesos de interfaz de usuario](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CSocket:: Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxcontextmenumanager"></a>AfxContextMenuManager

Puntero al administrador global del [menú contextual](ccontextmenumanager-class.md).

### <a name="syntax"></a>Sintaxis

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxcontextmenumanager. h

## <a name="afxendthread"></a>AfxEndThread

Llame a esta función para finalizar el subproceso que se está ejecutando actualmente.

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parámetros

\ *nExitCode*
Especifica el código de salida del subproceso.

*beliminar*\
Elimina el objeto de subproceso de la memoria.

### <a name="remarks"></a>Observaciones

Se debe llamar a desde dentro del subproceso para que se termine.

Para obtener más información sobre `AfxEndThread`, vea el artículo [multithreading: finalizar](../../parallel/multithreading-terminating-threads.md)subprocesos.

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxfindresourcehandle"></a>AfxFindResourceHandle

Use `AfxFindResourceHandle` para recorrer la cadena de recursos y buscar un recurso específico por identificador de recurso y tipo de recurso.

### <a name="syntax"></a>Sintaxis

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parámetros

\ *lpszName*
Puntero a una cadena que contiene el identificador de recurso.
\ *lpszType*
Puntero al tipo de recurso. Para obtener una lista de tipos de recursos, vea [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Identificador del módulo que contiene el recurso.

### <a name="remarks"></a>Observaciones

`AfxFindResourceHandle` encuentra el recurso específico y devuelve un identificador para el módulo que contiene el recurso. El recurso puede estar en cualquier archivo DLL de extensión de MFC que esté cargado. `AfxFindResourceHandle` le indica cuál tiene el recurso.

Los módulos se buscan en este orden:

1. El módulo principal, si es un archivo DLL de extensión de MFC.

1. Módulos que no son del sistema.

1. Módulos específicos del idioma.

1. El módulo principal, si es un archivo DLL del sistema.

1. Módulos del sistema.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="afxfreelibrary"></a>AfxFreeLibrary

Tanto `AfxFreeLibrary` como `AfxLoadLibrary` mantienen un recuento de referencias para cada módulo de biblioteca cargado.

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parámetros

\ *hInstLib*
Identificador del módulo de biblioteca cargado. [AfxLoadLibrary](#afxloadlibrary) devuelve este identificador.

### <a name="return-value"></a>Valor devuelto

TRUE si la función se ejecuta correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

`AfxFreeLibrary` disminuye el recuento de referencias del módulo cargado de la biblioteca de vínculos dinámicos (DLL). Cuando el recuento de referencias llega a cero, el módulo se desasigna del espacio de direcciones del proceso de llamada y el identificador ya no es válido. Este recuento de referencias se incrementa cada vez que se llama a `AfxLoadLibrary`.

Antes de quitar la asignación de un módulo de biblioteca, el sistema permite que el archivo DLL se desasocie de los procesos que lo usan. Al hacerlo, se proporciona al archivo DLL una oportunidad para limpiar los recursos asignados para el proceso actual. Una vez que la función de punto de entrada devuelve, el módulo de biblioteca se quita del espacio de direcciones del proceso actual.

Use `AfxLoadLibrary` para asignar un módulo DLL.

Asegúrese de usar `AfxFreeLibrary` y `AfxLoadLibrary` (en lugar de las funciones de Win32 `FreeLibrary` y `LoadLibrary`) si la aplicación usa varios subprocesos. El uso de `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión de MFC no daña el estado global de MFC.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdll_. h

## <a name="afxgetapp"></a>AfxGetApp

El puntero devuelto por esta función se puede usar para tener acceso a información de la aplicación, como el código principal de envío de mensajes o la ventana de nivel superior.

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de `CWinApp` único para la aplicación.

### <a name="remarks"></a>Observaciones

Si este método devuelve NULL, puede indicar que la ventana principal de la aplicación aún no se ha inicializado completamente. También podría indicar un problema.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxgetappname"></a>AfxGetAppName

La cadena devuelta se puede utilizar para los mensajes de diagnóstico o como raíz de los nombres de cadena temporales.

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Valor devuelto

Una cadena terminada en null que contiene el nombre de la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxgetinstancehandle"></a>AfxGetInstanceHandle

Esta función permite recuperar el identificador de instancia de la aplicación actual.

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Valor devuelto

HINSTANCE para la instancia actual de la aplicación. Si se llama desde dentro de un archivo DLL vinculado con la versión de USRDLL de MFC, se devuelve un HINSTANCE al archivo DLL.

### <a name="remarks"></a>Observaciones

`AfxGetInstanceHandle` siempre devuelve el HINSTANCE del archivo ejecutable (. EXE) a menos que se llame desde dentro de un archivo DLL vinculado con la versión de USRDLL de MFC. En este caso, devuelve un HINSTANCE al archivo DLL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxgetmainwnd"></a>AfxGetMainWnd

Si la aplicación es un servidor OLE, llame a esta función para recuperar un puntero a la ventana principal activa de la aplicación. Utilice este resultado en lugar de hacer referencia directamente al miembro [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) del objeto de aplicación.

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al objeto de ventana de marco que contiene el documento activo en contexto, si el servidor tiene un objeto activo en contexto dentro de un contenedor activo.

Si no hay ningún objeto activo en contexto dentro de un contenedor o la aplicación no es un servidor OLE, esta función devuelve el *m_pMainWnd* del objeto de aplicación.

Si se llama a `AfxGetMainWnd` desde el subproceso principal de la aplicación, devuelve la ventana principal de la aplicación según las reglas anteriores. Si se llama a la función desde un subproceso secundario de la aplicación, la función devuelve la ventana principal asociada al subproceso que realizó la llamada.

### <a name="remarks"></a>Observaciones

Si la aplicación no es un servidor OLE, llamar a esta función es equivalente a hacer referencia directamente al miembro *m_pMainWnd* del objeto de aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxgetperuserregistration"></a>AfxGetPerUserRegistration

Utilice esta función para determinar si la aplicación redirige el acceso del registro al nodo **HKEY_CURRENT_USER** (**HKCU**).

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que la información del registro se dirige al nodo HKCU. FALSE indica que la aplicación escribe información del registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Observaciones

Si habilita la redirección del registro, el marco de trabajo redirige el acceso desde **HKCR** a **HKEY_CURRENT_USER \software\classes**. La redirección solo afecta a los marcos de trabajo MFC y ATL.

Para cambiar si la aplicación redirige el acceso al registro, use [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxstat_. h

## <a name="afxgetresourcehandle"></a>AfxGetResourceHandle

Use el identificador de HINSTANCE devuelto por esta función para tener acceso directamente a los recursos de la aplicación, por ejemplo, en las llamadas a la función de Windows `FindResource`.

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Valor devuelto

Identificador de HINSTANCE donde se cargan los recursos predeterminados de la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxgetthread"></a>AfxGetThread

Llame a esta función para obtener un puntero al objeto [CWinThread](../../mfc/reference/cwinthread-class.md) que representa el subproceso que se está ejecutando actualmente.

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Valor devuelto

Puntero al subproceso que se está ejecutando actualmente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Se debe llamar a desde dentro del subproceso.

> [!NOTE]
> Si va a migrar un proyecto MFC que llama a `AfxGetThread` C++ desde las versiones de Visual 4,2, 5,0 o 6,0, `AfxGetThread` llama a [AfxGetApp](#afxgetapp) si no se encuentra ningún subproceso. En las versiones más recientes del compilador, `AfxGetThread` devuelve NULL si no se encuentra ningún subproceso. Si desea el subproceso de la aplicación, debe llamar a `AfxGetApp`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxinitrichedit"></a>AfxInitRichEdit

Llame a esta función para inicializar el control Rich Edit (versión 1,0) para la aplicación.

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Observaciones

Esta función se proporciona por compatibilidad con versiones anteriores. Las nuevas aplicaciones deben usar [AfxInitRichEdit2](#afxinitrichedit2).

`AfxInitRichEdit` carga RICHED32. DLL para inicializar la versión 1,0 del control Rich Edit. Para usar la versión 2,0 y 3,0 del control Rich Edit, RICHED20. DLL debe cargarse. Se carga realizando una llamada a [AfxInitRichEdit2](#afxinitrichedit2).

Para actualizar los controles Rich Edit de las C++ aplicaciones visuales existentes a la versión 2,0, abra el. Archivo RC como texto, cambie el nombre de clase de cada control Rich Edit de "RICHEDIT" a "RichEdit20a". A continuación, reemplace la llamada a `AfxInitRichEdit` por `AfxInitRichEdit2`.

Esta función también inicializa la biblioteca de controles comunes, si la biblioteca aún no se ha inicializado para el proceso. Si utiliza el control Rich Edit directamente desde la aplicación MFC, llame a esta función para asegurarse de que MFC ha inicializado correctamente el tiempo de ejecución del control Rich Edit. Si llama al método `Create` de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)o [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), normalmente no es necesario llamar a esta función, pero en algunos casos podría ser necesario.

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxinitrichedit2"></a>AfxInitRichEdit2

Llame a esta función para inicializar el control Rich Edit (versión 2,0 y posteriores) de la aplicación.

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Observaciones

Llame a esta función para cargar RICHED20. DLL e inicialice la versión 2,0 del control Rich Edit. Si llama al método `Create` de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)o [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), normalmente no es necesario llamar a esta función, pero en algunos casos podría ser necesario.

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass

Determina si la ventana dada es un objeto de marco extendido.

### <a name="syntax"></a>Sintaxis

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parámetros

\ *PWND*
de Un puntero a un objeto que se deriva de `CWnd`.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana proporcionada es un objeto de marco extendido; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método devuelve TRUE si *PWND* deriva de una de las clases siguientes:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Este método es útil cuando tiene que validar que un parámetro de función o método es una ventana de marco extendido.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxismfctoolbar"></a>AfxIsMFCToolBar

Determina si la ventana dada es un objeto de barra de herramientas.

### <a name="syntax"></a>Sintaxis

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

\ *PWND*
de Un puntero a un objeto que se deriva de `CWnd`.

### <a name="return-value"></a>Valor devuelto

TRUE si la ventana proporcionada es un objeto de barra de herramientas; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método devuelve `TRUE` si *PWND* deriva de `CMFCToolBar`. Este método es útil cuando tiene que validar que un parámetro de función o de método es un objeto de `CMFCToolBar`.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxkeyboardmanager"></a>AfxKeyboardManager

Puntero al administrador de [teclado](ckeyboardmanager-class.md)global.

### <a name="syntax"></a>Sintaxis

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxkeyboardmanager. h

## <a name="afxloadlibrary"></a>AfxLoadLibrary

Use `AfxLoadLibrary` para asignar un módulo DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parámetros

\ *lpszModuleName*
Apunta a una cadena terminada en null que contiene el nombre del módulo (ya sea un. DLL o. Archivo EXE). El nombre especificado es el nombre de archivo del módulo.

Si la cadena especifica una ruta de acceso pero el archivo no existe en el directorio especificado, se produce un error en la función.

Si no se especifica una ruta de acceso y se omite la extensión de nombre de archivo, la extensión predeterminada. Se anexa el archivo DLL. Sin embargo, la cadena de nombre de archivo puede incluir un carácter de punto final (.) para indicar que el nombre del módulo no tiene ninguna extensión. Cuando no se especifica ninguna ruta de acceso, la función usa el [orden de búsqueda de las aplicaciones de escritorio](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es un identificador del módulo. En caso de error, el valor devuelto es NULL.

### <a name="remarks"></a>Observaciones

Devuelve un identificador que se puede usar en [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) para obtener la dirección de una función dll. también se puede usar `AfxLoadLibrary` para asignar otros módulos ejecutables.

Cada proceso mantiene un recuento de referencias para cada módulo de biblioteca cargado. Este recuento de referencias se incrementa cada vez que se llama a `AfxLoadLibrary` y se reduce cada vez que se llama a `AfxFreeLibrary`. Cuando el recuento de referencias llega a cero, el módulo se desasigna del espacio de direcciones del proceso de llamada y el identificador ya no es válido.

Asegúrese de usar `AfxLoadLibrary` y `AfxFreeLibrary` (en lugar de las funciones de Win32 `LoadLibrary` y `FreeLibrary`) si la aplicación usa varios subprocesos, y si carga dinámicamente un archivo DLL de extensión de MFC. El uso de `AfxLoadLibrary` y `AfxFreeLibrary` garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión de MFC no daña el estado global de MFC.

El uso de `AfxLoadLibrary` en una aplicación requiere que se vincule dinámicamente a la versión de DLL de MFC. El archivo de encabezado de `AfxLoadLibrary`, Afxdll_. h, solo se incluye si MFC está vinculado a la aplicación como un archivo DLL. Este requisito es así por diseño, ya que tiene que vincular a la versión de DLL de MFC para usar o crear archivos dll de extensión de MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdll_. h

## <a name="afxloadlibraryex"></a>AfxLoadLibraryEx

Use `AfxLoadLibraryEx` para asignar un módulo DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

\ *lpFileName*
Apunta a una cadena terminada en null que contiene el nombre del módulo (ya sea un. DLL o. Archivo EXE). El nombre especificado es el nombre de archivo del módulo.

Si la cadena especifica una ruta de acceso pero el archivo no existe en el directorio especificado, se produce un error en la función.

Si no se especifica una ruta de acceso y se omite la extensión de nombre de archivo, la extensión predeterminada. Se anexa el archivo DLL. Sin embargo, la cadena de nombre de archivo puede incluir un carácter de punto final (.) para indicar que el nombre del módulo no tiene ninguna extensión. Cuando no se especifica ninguna ruta de acceso, la función usa el [orden de búsqueda de las aplicaciones de escritorio](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications).

\ *hFile*
Este parámetro se reserva para uso futuro. Debe ser NULL.

*dwFlags*\
Acción que se realizará al cargar el módulo. Si no se especifican marcas, el comportamiento de esta función es idéntico al de la función `AfxLoadLibrary`. Los valores posibles de este parámetro se describen en la documentación de [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) .

### <a name="return-value"></a>Valor devuelto

Si la función se ejecuta correctamente, el valor devuelto es un identificador del módulo. En caso de error, el valor devuelto es NULL.

### <a name="remarks"></a>Observaciones

`AfxLoadLibraryEx` devuelve un identificador que se puede usar en [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) para obtener la dirección de una función dll. también se puede usar `AfxLoadLibraryEx` para asignar otros módulos ejecutables.

Cada proceso mantiene un recuento de referencias para cada módulo de biblioteca cargado. Este recuento de referencias se incrementa cada vez que se llama a `AfxLoadLibraryEx` y se reduce cada vez que se llama a `AfxFreeLibrary`. Cuando el recuento de referencias llega a cero, el módulo se desasigna del espacio de direcciones del proceso de llamada y el identificador ya no es válido.

Asegúrese de usar `AfxLoadLibraryEx` y `AfxFreeLibrary` (en lugar de las funciones de Win32 `LoadLibraryEx` y `FreeLibrary`) si la aplicación usa varios subprocesos y si carga dinámicamente un archivo DLL de extensión de MFC. El uso de `AfxLoadLibraryEx` y `AfxFreeLibrary` garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión de MFC no daña el estado global de MFC.

El uso de `AfxLoadLibraryEx` en una aplicación requiere que se vincule dinámicamente a la versión de DLL de MFC. El archivo de encabezado de `AfxLoadLibraryEx`, Afxdll_. h, solo se incluye si MFC está vinculado a la aplicación como un archivo DLL. Este requisito es así por diseño, ya que tiene que vincular a la versión de DLL de MFC para usar o crear archivos dll de extensión de MFC.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdll_. h

## <a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager

Puntero al [Administrador de menús de recorte](cmenutearoffmanager-class.md)global.

### <a name="syntax"></a>Sintaxis

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmenutearoffmanager. h

## <a name="afxmousemanager"></a>AfxMouseManager

Puntero al administrador global [del mouse](cmousemanager-class.md).

### <a name="syntax"></a>Sintaxis

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmousemanager. h

## <a name="afxregisterclass"></a>AfxRegisterClass

Utilice esta función para registrar clases de ventana en un archivo DLL que utiliza MFC.

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parámetros

\ *lpWndClass*
Puntero a una estructura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) que contiene información sobre la clase de ventana que se va a registrar. Para obtener más información sobre esta estructura, vea el Windows SDK.

### <a name="return-value"></a>Valor devuelto

TRUE si la clase se registra correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

Si utiliza esta función, se anulará automáticamente el registro de la clase cuando se descargue el archivo DLL.

En las compilaciones que no son de DLL, el identificador de `AfxRegisterClass` se define como una macro que se asigna a la función de Windows `RegisterClass`, ya que las clases registradas en una aplicación se anulan automáticamente del registro. Si usa `AfxRegisterClass` en lugar de `RegisterClass`, el código se puede usar sin cambiar en una aplicación y en un archivo DLL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxregisterwndclass"></a>AfxRegisterWndClass (

Permite registrar sus propias clases de ventana.

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parámetros

\ *nClassStyle*
Especifica el estilo de clase de Windows o la combinación de estilos, creados mediante el operador bit **&#124;** a bit or (), para la clase de ventana. Para obtener una lista de estilos de clase, consulte la estructura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) en el Windows SDK. Si es NULL, los valores predeterminados se establecen de la siguiente manera:

- Establece el estilo del mouse en CS_DBLCLKS, que envía los mensajes de doble clic al procedimiento de ventana cuando el usuario hace doble clic con el mouse.

- Establece el estilo de cursor de flecha en el IDC_ARROW estándar de Windows.

- Establece el pincel de fondo en NULL, por lo que la ventana no borrará su fondo.

- Establece el icono en el icono del logotipo de Windows estándar, con la marca ondeante.

\ *hCursor*
Especifica un identificador para el recurso de cursor que se va a instalar en cada ventana creada a partir de la clase de ventana. Si usa el valor predeterminado de **0**, obtendrá el cursor de IDC_ARROW estándar.

\ *hbrBackground*
Especifica un identificador para el recurso de pincel que se va a instalar en cada ventana creada a partir de la clase de ventana. Si usa el valor predeterminado **0**, tendrá un pincel de fondo nulo y, de forma predeterminada, la ventana no borrará su fondo mientras procesa [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd).

\ *hIcon*
Especifica un identificador para el recurso de icono que se va a instalar en cada ventana creada a partir de la clase de ventana. Si usa el valor predeterminado de **0**, obtendrá el icono del logotipo de Windows estándar, con el marcador de la salud.

### <a name="return-value"></a>Valor devuelto

Una cadena terminada en null que contiene el nombre de clase. Puede pasar este nombre de clase a la función miembro `Create` en `CWnd` u otras clases derivadas **de CWnd**para crear una ventana. El biblioteca MFC genera el nombre.

> [!NOTE]
> El valor devuelto es un puntero a un búfer estático. Para guardar esta cadena, asígnela a una variable de `CString`.

### <a name="remarks"></a>Observaciones

El biblioteca MFC registra automáticamente varias clases de ventana estándar. Llame a esta función si desea registrar sus propias clases de ventana.

El nombre registrado para una clase por `AfxRegisterWndClass` depende únicamente de los parámetros. Si llama a `AfxRegisterWndClass` varias veces con parámetros idénticos, solo registra una clase en la primera llamada. Las llamadas posteriores a `AfxRegisterWndClass` con parámetros idénticos devuelven el valor de className ya registrado.

Si llama a `AfxRegisterWndClass` para varias clases derivadas de CWnd con parámetros idénticos, en lugar de obtener una clase de ventana independiente para cada clase, cada clase comparte la misma clase de ventana. Este uso compartido puede producir problemas si se usa el estilo de clase CS_CLASSDC. En lugar de varias clases de ventana de CS_CLASSDC, acaba con solo una CS_CLASSDC clase de ventana. Todas C++ las ventanas que usan esa clase comparten el mismo controlador de dominio. Para evitar este problema, llame a [AfxRegisterClass](#afxregisterclass) para registrar la clase.

Consulte la nota técnica [TN001: registro](../../mfc/tn001-window-class-registration.md) de la clase de ventana para obtener más información sobre el registro de la clase de ventana y la función `AfxRegisterWndClass`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxsetperuserregistration"></a>AfxSetPerUserRegistration

Establece si la aplicación redirige el acceso del registro al nodo **HKEY_CURRENT_USER** (**HKCU**).

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

\ *bEnable*
de TRUE indica que la información del registro se dirige al nodo HKCU. FALSE indica que la aplicación escribe información del registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Observaciones

Antes de Windows Vista, las aplicaciones que tienen acceso al registro solían usar el nodo **HKEY_CLASSES_ROOT** . Sin embargo, con Windows Vista o sistemas operativos posteriores, debe ejecutar una aplicación en modo elevado para escribir en HKCR.

Este método permite que la aplicación Lea y escriba en el registro sin ejecutarse en modo elevado. Funciona redirigiendo el acceso al registro de HKCR a HKCU. Para obtener más información, consulta [Linker Property Pages](../../build/reference/linker-property-pages.md).

Si habilita la redirección del registro, el marco de trabajo redirige el acceso desde HKCR a **HKEY_CURRENT_USER \software\classes**. La redirección solo afecta a los marcos de trabajo MFC y ATL.

La implementación predeterminada tiene acceso al registro en HKCR.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxstat_. h

## <a name="afxsetresourcehandle"></a>AfxSetResourceHandle

Use esta función para establecer el identificador de HINSTANCE que determina dónde se cargan los recursos predeterminados de la aplicación.

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parámetros

\ *hInstResource*
Identificador de instancia o módulo de un. Archivo EXE o DLL del que se cargan los recursos de la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="afxshellmanager"></a>AfxShellManager

Puntero al administrador de [Shell](cshellmanager-class.md)global.

### <a name="syntax"></a>Sintaxis

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxshellmanager. h

## <a name="afxsocketinit"></a>AfxSocketInit

Llame a esta función en la invalidación de `CWinApp::InitInstance` para inicializar Windows Sockets.

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parámetros

\ *lpwsaData*
Puntero a una estructura [wsadata (](/windows/win32/api/winsock2/ns-winsock2-wsadata) . Si *lpwsaData* no es igual a NULL, la dirección de la estructura de `WSADATA` se rellena con la llamada a `WSAStartup`. Esta función también garantiza que se llama a `WSACleanup` antes de que finalice la aplicación.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Al utilizar sockets de MFC en subprocesos secundarios en una aplicación MFC vinculada estáticamente, debe llamar a `AfxSocketInit` en cada subproceso que use Sockets para inicializar las bibliotecas de Sockets. De forma predeterminada, solo se llama a `AfxSocketInit` en el subproceso principal.

### <a name="requirements"></a>Requisitos

  **Encabezado** AfxSock. h

## <a name="afxusertoolsmanager"></a>AfxUserToolsManager

Puntero al administrador de [herramientas de usuario](cusertoolsmanager-class.md)global.

### <a name="syntax"></a>Sintaxis

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxusertoolsmanager. h

## <a name="afxwininit"></a>AfxWinInit

La función `WinMain` proporcionada por MFC, como parte de la inicialización de [CWinApp](../../mfc/reference/cwinapp-class.md) de una aplicación basada en GUI, llama a esta función para inicializar MFC.

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parámetros

*hInstance*\
Identificador del módulo que se está ejecutando actualmente.

\ *hPrevInstance*
Identificador de una instancia anterior de la aplicación. En el caso de una aplicación basada en Win32, este parámetro siempre es **null**.

\ *lpCmdLine*
Apunta a una cadena terminada en null que especifica la línea de comandos para la aplicación.

\ *nCmdShow*
Especifica cómo se mostraría la ventana principal de una aplicación GUI.

### <a name="remarks"></a>Observaciones

En el caso de una aplicación de consola, que no utiliza la función de `WinMain` proporcionada por MFC, debe llamar directamente a `AfxWinInit` para inicializar MFC.

Si llama a `AfxWinInit` usted mismo, debe declarar una instancia de una clase `CWinApp`. En el caso de una aplicación de consola, puede decidir no derivar su propia clase de `CWinApp` y, en su lugar, usar directamente una instancia de `CWinApp`. Esta técnica es adecuada si decide dejar toda la funcionalidad de la aplicación en su implementación de **Main**.

> [!NOTE]
> Cuando crea un contexto de activación para un ensamblado, MFC usa un recurso de manifiesto proporcionado por el módulo de usuario. El contexto de activación se crea en `AfxWinInit`. Para obtener más información, vea [compatibilidad con los contextos de activación en el estado del módulo MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** AFXWIN. h

## <a name="see-also"></a>Consulte también

[Macros y\ globales](mfc-macros-and-globals.md)
[CWinApp (clase](cwinapp-class.md) )\
\ de la [clase CContextMenuManager](ccontextmenumanager-class.md)
[CWnd (clase](cwnd-class.md) )\
\ de la [clase CFrameWndEx](cframewndex-class.md)
\ de la [clase CMFCToolBar](cmfctoolbar-class.md)
\ de la [clase CKeyboardManager](ckeyboardmanager-class.md)
\ de la [clase CMenuTearOffManager](cmenutearoffmanager-class.md)
\ de la [clase CMouseManager](cmousemanager-class.md)
\ de la [clase CShellManager](cshellmanager-class.md)
[CUserToolsManager (clase)](cusertoolsmanager-class.md)
