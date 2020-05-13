---
title: Información y administración de aplicaciones
description: Referencia a las funciones de administración e información de la aplicación de la biblioteca Microsoft Foundation Class (MFC).
ms.date: 01/27/2020
helpviewer_keywords:
- applications [MFC], managing
ms.assetid: b72f4154-24db-4e75-bca3-6873e2459c15
ms.openlocfilehash: fc0b4b09f6c48da68bebe4a2825f49bcf6ab7e23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372499"
---
# <a name="application-information-and-management"></a>Información y administración de aplicaciones

Al escribir una aplicación, se crea un único objeto derivado de [CWinApp.](../../mfc/reference/cwinapp-class.md) A veces, es posible que desee `CWinApp`obtener información sobre este objeto desde fuera del objeto derivado. O puede que necesite acceso a otros objetos "manager" globales.

La biblioteca Microsoft Foundation Class proporciona las siguientes funciones globales para ayudarle a realizar estas tareas:

## <a name="application-information-and-management-functions"></a>Funciones de información y gestión de aplicaciones

|||
|-|-|
|[AfxBeginThread](#afxbeginthread)|Crea un nuevo subproceso.|
|[AfxContextMenuManager](#afxcontextmenumanager)|Puntero al administrador de [menús contextuales](ccontextmenumanager-class.md)global .|
|[AfxEndThread](#afxendthread)|Termina el subproceso actual.|
|[AfxFindResourceHandle](#afxfindresourcehandle)|Recorre la cadena de recursos y localiza un recurso específico por identificador de recurso y tipo de recurso. |
|[AfxFreeLibrary](#afxfreelibrary)|Disminuye el recuento de referencias del módulo de biblioteca de vínculos dinámicos (DLL) cargado. Cuando el recuento de referencias llega a cero, el módulo no se asigna.|
|[AfxGetApp](#afxgetapp)|Devuelve un puntero al único `CWinApp` objeto de la aplicación.|
|[AfxGetAppName](#afxgetappname)|Devuelve una cadena que contiene el nombre de la aplicación.|
|[AfxGetInstanceHandle](#afxgetinstancehandle)|Devuelve un HINSTANCE que representa esta instancia de la aplicación.|
|[AfxGetMainWnd](#afxgetmainwnd)|Devuelve un puntero a la ventana "principal" actual de una aplicación que no es OLE o a la ventana de marco en su lugar de una aplicación de servidor.|
|[AfxGetPerUserRegistration](#afxgetperuserregistration)|Utilice esta función para determinar si la aplicación redirige el acceso del Registro al nodo **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxGetResourceHandle](#afxgetresourcehandle)|Devuelve un Valor HINSTANCE al origen de los recursos predeterminados de la aplicación. Se utiliza para acceder directamente a los recursos de la aplicación.|
|[AfxGetThread](#afxgetthread)|Recupera un puntero al objeto [CWinThread](../../mfc/reference/cwinthread-class.md) actual.|
|[AfxInitRichEdit](#afxinitrichedit)|Inicializa el control rich edit de la versión 1.0 para la aplicación.|
|[AfxInitRichEdit2](#afxinitrichedit2)|Inicializa el control rich edit de la versión 2.0 y versiones posteriores para la aplicación.|
|[AfxIsExtendedFrameClass](#afxisextendedframeclass)|Determina si la ventana dada es un objeto de marco extendido.|
|[AfxIsMFCToolBar](#afxismfctoolbar)|Determina si la ventana dada es un objeto de barra de herramientas.|
|[AfxKeyboardManager](#afxkeyboardmanager)|Puntero al [administrador](ckeyboardmanager-class.md)de teclado global .|
|[AfxLoadLibrary](#afxloadlibrary)|Asigna un módulo DLL y devuelve un identificador que se puede usar para obtener la dirección de una función DLL.|
|[AfxLoadLibraryEx](#afxloadlibraryex)|Asigna un módulo DLL mediante las opciones especificadas y devuelve un identificador que se puede usar para obtener la dirección de una función DLL.|
|[AfxMenuTearOffManager](#afxmenutearoffmanager)|Puntero al gestor de [menús de desmontaje](cmenutearoffmanager-class.md)global.|
|[AfxMouseManager](#afxmousemanager)|Puntero al [administrador](cmousemanager-class.md)global del mouse .|
|[AfxRegisterClass](#afxregisterclass)|Registra una clase de ventana en un archivo DLL que usa MFC.|
|[AfxRegisterWndClass](#afxregisterwndclass)|Registra una clase de ventana de Windows para complementar las registradas automáticamente por MFC.|
|[AfxSetPerUserRegistration](#afxsetperuserregistration)|Establece si la aplicación redirige el acceso del Registro al nodo **HKEY_CURRENT_USER** (**HKCU**).|
|[AfxSetResourceHandle](#afxsetresourcehandle)|Establece el identificador HINSTANCE donde se cargan los recursos predeterminados de la aplicación.|
|[AfxShellManager](#afxshellmanager)|Puntero al [administrador](cshellmanager-class.md)de shell global . |
|[AfxSocketInit](#afxsocketinit)|Se llama `CWinApp::InitInstance` en una invalidación para inicializar Windows Sockets.|
|[AfxUserToolsManager](#afxusertoolsmanager)|Puntero al [administrador](cusertoolsmanager-class.md)global de herramientas de usuario .|
|[AfxWinInit](#afxwininit)|Llamado por la `WinMain` función proporcionada por MFC, como parte de la inicialización de [CWinApp](../../mfc/reference/cwinapp-class.md) de una aplicación basada en GUI, para inicializar MFC. Debe llamarse directamente para las aplicaciones de consola que usan MFC.|

## <a name="afxbeginthread"></a><a name="afxbeginthread"></a>AfxBeginThread

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

*pfnThreadProc*\
Señala a la función de control para el subproceso de trabajo. El puntero no puede ser NULL. Esta función debe declararse de la siguiente manera:

`UINT __cdecl MyControllingFunction( LPVOID pParam );`

*pThreadClass*\
El RUNTIME_CLASS de un objeto derivado de [CWinThread](../../mfc/reference/cwinthread-class.md).

*pParam*\
Parámetro para pasar a la función de control.

*nPrioridad*\
La prioridad que se debe establecer para el subproceso. Para obtener una lista completa y una descripción de las prioridades disponibles, vea [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el Windows SDK.

*nStackSize*\
Especifica el tamaño en bytes de la pila para el nuevo subproceso. Si es 0, el tamaño de pila tiene como valor predeterminado la misma pila de tamaño que el subproceso de creación.

*dwCreateFlags*\
Especifica una marca adicional que controla la creación del subproceso. Este indicador puede contener uno de dos valores:

- CREATE_SUSPENDED Iniciar el subproceso con un recuento de suspensión de uno. Utilice CREATE_SUSPENDED si desea inicializar los `CWinThread` datos de miembro del objeto, como [m_bAutoDelete](../../mfc/reference/cwinthread-class.md#m_bautodelete) o cualquier miembro de la clase derivada, antes de que el subproceso comience a ejecutarse. Una vez completada la inicialización, use [CWinThread::ResumeThread](../../mfc/reference/cwinthread-class.md#resumethread) para iniciar la ejecución del subproceso. El subproceso no se `CWinThread::ResumeThread` ejecutará hasta que se llame.

- **0** Inicie el subproceso inmediatamente después de la creación.

*lpSecurityAttrs*\
Apunta a una estructura [de SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica los atributos de seguridad para el subproceso. Si NULL, se usan los mismos atributos de seguridad que el subproceso de creación. Para obtener más información sobre esta estructura, consulte el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Puntero al objeto de subproceso recién creado, o NULL si se produce un error.

### <a name="remarks"></a>Observaciones

La primera `AfxBeginThread` forma de crea un subproceso de trabajo. El segundo formulario crea un subproceso que puede servir como un subproceso de interfaz de usuario o como un subproceso de trabajo.

`AfxBeginThread`crea un `CWinThread` nuevo objeto, llama a su [función CreateThread](../../mfc/reference/cwinthread-class.md#createthread) para empezar a ejecutar el subproceso y devuelve un puntero al subproceso. Se realizan comprobaciones en todo el procedimiento para asegurar que todos los objetos queden desasignados correctamente en caso de error en algún momento del proceso de creación. Para finalizar el subproceso, llame a [AfxEndThread](#afxendthread) desde dentro del subproceso o vuelva desde la función de control del subproceso de trabajo.

La aplicación debe habilitar el multithreading; de lo contrario, esta función fallará. Para obtener más información sobre cómo habilitar el multithreading, vea [/MD, /MT, /LD (Usar biblioteca](../../build/reference/md-mt-ld-use-run-time-library.md)en tiempo de ejecución) .

Para obtener `AfxBeginThread`más información sobre , vea los artículos [Multithreading: Creating Worker Threads](../../parallel/multithreading-creating-worker-threads.md) and [Multithreading: Creating User-Interface Threads](../../parallel/multithreading-creating-user-interface-threads.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CSocket::Attach](../../mfc/reference/csocket-class.md#attach).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxcontextmenumanager"></a><a name="afxcontextmenumanager"></a>AfxContextMenuManager

Puntero al administrador de [menús contextuales](ccontextmenumanager-class.md)global .

### <a name="syntax"></a>Sintaxis

```cpp
CContextMenuManager* afxContextMenuManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxcontextmenumanager.h

## <a name="afxendthread"></a><a name="afxendthread"></a>AfxEndThread

Llame a esta función para terminar el subproceso que se está ejecutando actualmente.

```cpp
void AFXAPI AfxEndThread(
    UINT nExitCode,
    BOOL bDelete  = TRUE);
```

### <a name="parameters"></a>Parámetros

*nExitCode*\
Especifica el código de salida del subproceso.

*bEliminar*\
Elimina el objeto de subproceso de la memoria.

### <a name="remarks"></a>Observaciones

Debe llamarse desde dentro del subproceso que se va a terminar.

Para obtener `AfxEndThread`más información sobre , vea el artículo [Multithreading: Terminating Threads](../../parallel/multithreading-terminating-threads.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxfindresourcehandle"></a><a name="afxfindresourcehandle"></a>AfxFindResourceHandle

Se `AfxFindResourceHandle` usa para recorrer la cadena de recursos y localizar un recurso específico por identificador de recurso y tipo de recurso.

### <a name="syntax"></a>Sintaxis

```cpp
HINSTANCE AFXAPI AfxFindResourceHandle( LPCTSTR lpszName,  LPCTSTR lpszType );
```

### <a name="parameters"></a>Parámetros

*lpszName*\
Puntero a una cadena que contiene el identificador de recurso.
*lpszType*\
Un puntero al tipo de recurso. Para obtener una lista de tipos de recursos, vea [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Identificador del módulo que contiene el recurso.

### <a name="remarks"></a>Observaciones

`AfxFindResourceHandle`busca el recurso específico y devuelve un identificador al módulo que contiene el recurso. El recurso puede estar en cualquier archivo DLL de extensión MFC que se carga. `AfxFindResourceHandle`le dice cuál tiene el recurso.

Los módulos se buscan en este orden:

1. El módulo principal, si se trata de un archivo DLL de extensión MFC.

1. Módulos que no son del sistema.

1. Módulos específicos del idioma.

1. El módulo principal, si se trata de un archivo DLL del sistema.

1. Módulos del sistema.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="afxfreelibrary"></a><a name="afxfreelibrary"></a>AfxFreeLibrary

Tanto `AfxFreeLibrary` `AfxLoadLibrary` como mantener un recuento de referencias para cada módulo de biblioteca cargado.

```cpp
BOOL AFXAPI AfxFreeLibrary(HINSTANCE hInstLib);
```

### <a name="parameters"></a>Parámetros

*hInstLib*\
Identificador del módulo de biblioteca cargado. [AfxLoadLibrary](#afxloadlibrary) devuelve este identificador.

### <a name="return-value"></a>Valor devuelto

TRUESi la función se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

`AfxFreeLibrary`disminuye el recuento de referencias del módulo de biblioteca de vínculos dinámicos (DLL) cargado. Cuando el recuento de referencias llega a cero, el módulo se desasigna desde el espacio de direcciones del proceso de llamada y el identificador ya no es válido. Este recuento de referencias `AfxLoadLibrary` se incrementa cada vez que se llama.

Antes de desasignar un módulo de biblioteca, el sistema permite que el archivo DLL se desasocie de los procesos que lo utilizan. Al hacerlo, el archivo DLL tiene la oportunidad de limpiar los recursos asignados para el proceso actual. Una vez deretorno la función de punto de entrada, el módulo de biblioteca se quita del espacio de direcciones del proceso actual.

Se `AfxLoadLibrary` utiliza para asignar un módulo DLL.

Asegúrese de `AfxFreeLibrary` `AfxLoadLibrary` usar y (en lugar `FreeLibrary` `LoadLibrary`de las funciones Win32 y ) si la aplicación utiliza varios subprocesos. Usar `AfxLoadLibrary` `AfxFreeLibrary` y garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión MFC no daña el estado global de MFC.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [AfxLoadLibrary](#afxloadlibrary).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdll_.h

## <a name="afxgetapp"></a><a name="afxgetapp"></a>AfxGetApp

El puntero devuelto por esta función se puede utilizar para tener acceso a la información de la aplicación, como el código de envío de mensajes principal o la ventana superior.

```cpp
CWinApp* AFXAPI AfxGetApp();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al `CWinApp` único objeto de la aplicación.

### <a name="remarks"></a>Observaciones

Si este método devuelve NULL, podría indicar que la ventana principal de la aplicación aún no se ha inicializado completamente. También podría indicar un problema.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#126](../../mfc/reference/codesnippet/cpp/application-information-and-management_1.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxgetappname"></a><a name="afxgetappname"></a>AfxGetAppName

La cadena devuelta se puede utilizar para mensajes de diagnóstico o como raíz para nombres de cadena temporales.

```cpp
LPCTSTR AFXAPI AfxGetAppName();
```

### <a name="return-value"></a>Valor devuelto

Cadena terminada en null que contiene el nombre de la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#127](../../mfc/reference/codesnippet/cpp/application-information-and-management_2.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxgetinstancehandle"></a><a name="afxgetinstancehandle"></a>AfxGetInstanceHandle

Esta función le permite recuperar el identificador de instancia de la aplicación actual.

```cpp
HINSTANCE  AFXAPI AfxGetInstanceHandle();
```

### <a name="return-value"></a>Valor devuelto

Un HINSTANCE a la instancia actual de la aplicación. Si se llama desde dentro de un archivo DLL vinculado con la versión USRDLL de MFC, se devuelve un Valor HINSTANCE al archivo DLL.

### <a name="remarks"></a>Observaciones

`AfxGetInstanceHandle`siempre devuelve la HINSTANCE de su archivo ejecutable (. EXE) a menos que se llame desde un archivo DLL vinculado con la versión USRDLL de MFC. En este caso, devuelve un HINSTANCE al archivo DLL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#128](../../mfc/reference/codesnippet/cpp/application-information-and-management_3.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxgetmainwnd"></a><a name="afxgetmainwnd"></a>AfxGetMainWnd

Si la aplicación es un servidor OLE, llame a esta función para recuperar un puntero a la ventana principal activa de la aplicación. Utilice este resultado en lugar de hacer referencia directamente al [m_pMainWnd](../../mfc/reference/cwinthread-class.md#m_pmainwnd) miembro del objeto de aplicación.

```cpp
CWnd* AFXAPI AfxGetMainWnd();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un puntero al objeto de ventana de marco que contiene el documento activo en el lugar, si el servidor tiene un objeto que está activo en el lugar dentro de un contenedor activo.

Si no hay ningún objeto que esté activo en su lugar dentro de un contenedor o la aplicación no sea un servidor OLE, esta función devuelve el *m_pMainWnd* del objeto de aplicación.

Si se llama a `AfxGetMainWnd` desde el subproceso principal de la aplicación, devuelve la ventana principal de la aplicación según las reglas anteriores. Si se llama a la función desde un subproceso secundario de la aplicación, la función devuelve la ventana principal asociada al subproceso que realizó la llamada.

### <a name="remarks"></a>Observaciones

Si la aplicación no es un servidor OLE, llamar a esta función equivale a hacer referencia directamente al *m_pMainWnd* miembro del objeto de aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#129](../../mfc/reference/codesnippet/cpp/application-information-and-management_4.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxgetperuserregistration"></a><a name="afxgetperuserregistration"></a>AfxGetPerUserRegistration

Utilice esta función para determinar si la aplicación redirige el acceso del Registro al nodo **HKEY_CURRENT_USER** (**HKCU**).

```cpp
BOOL AFXAPI AfxGetPerUserRegistration();
```

### <a name="return-value"></a>Valor devuelto

TRUE indica que la información del Registro se dirige al nodo HKCU. FALSE indica que la aplicación escribe información del Registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Observaciones

Si habilita la redirección del registro, el marco de trabajo redirige el acceso desde **HKCR** a **HKEY_CURRENT_USER- Software - Clases**. Solo los marcos MFC y ATL se ven afectados por la redirección.

Para cambiar si la aplicación redirige el acceso al Registro, utilice [AfxSetPerUserRegistration](#afxsetperuserregistration).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxstat_.h

## <a name="afxgetresourcehandle"></a><a name="afxgetresourcehandle"></a>AfxGetResourceHandle

Utilice el identificador HINSTANCE devuelto por esta función para tener acceso a los `FindResource`recursos de la aplicación directamente, por ejemplo, en llamadas a la función de Windows .

```cpp
extern HINSTANCE  AfxGetResourceHandle();
```

### <a name="return-value"></a>Valor devuelto

Identificador HINSTANCE donde se cargan los recursos predeterminados de la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#130](../../mfc/reference/codesnippet/cpp/application-information-and-management_5.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxgetthread"></a><a name="afxgetthread"></a>AfxGetThread

Llame a esta función para obtener un puntero a la [CWinThread](../../mfc/reference/cwinthread-class.md) objeto que representa el subproceso que se está ejecutando actualmente.

```cpp
CWinThread* AfxGetThread();
```

### <a name="return-value"></a>Valor devuelto

Puntero al subproceso que se está ejecutando actualmente; NULL.

### <a name="remarks"></a>Observaciones

Debe llamarse desde dentro del subproceso.

> [!NOTE]
> Si va a migrar un `AfxGetThread` proyecto MFC que llama desde Visual C++ versiones `AfxGetThread` 4.2, 5.0 o 6.0, llama a [AfxGetApp](#afxgetapp) si no se encuentra ningún subproceso. En versiones más recientes `AfxGetThread` del compilador, devuelve NULL si no se encontró ningún subproceso. Si desea el subproceso de `AfxGetApp`aplicación, debe llamar a .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#132](../../mfc/reference/codesnippet/cpp/application-information-and-management_6.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxinitrichedit"></a><a name="afxinitrichedit"></a>AfxInitRichEditar

Llame a esta función para inicializar el control rich edit (versión 1.0) para la aplicación.

```cpp
BOOL AFXAPI AfxInitRichEdit();
```

### <a name="remarks"></a>Observaciones

Esta función se proporciona para la compatibilidad con versiones anteriores. Las nuevas aplicaciones deben utilizar [AfxInitRichEdit2](#afxinitrichedit2).

`AfxInitRichEdit`cargas RICHED32. DLL para inicializar la versión 1.0 del control rich edit. Para utilizar las versiones 2.0 y 3.0 del control rich edit, RICHED20. DLL debe cargarse. Se carga haciendo una llamada a [AfxInitRichEdit2](#afxinitrichedit2).

Para actualizar los controles de edición enriquecidos en aplicaciones de Visual C++ existentes a la versión 2.0, abra el archivo . RC como texto, cambie el nombre de clase de cada control rich edit de "RICHEDIT" a "RichEdit20a". A continuación, `AfxInitRichEdit` reemplace `AfxInitRichEdit2`la llamada a con .

Esta función también inicializa la biblioteca de controles comunes, si la biblioteca aún no se ha inicializado para el proceso. Si usa el control rich edit directamente desde la aplicación MFC, llame a esta función para asegurarse de que MFC ha inicializado correctamente el tiempo de ejecución del control de edición enriquecida. Si se `Create` llama al método de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)o [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), normalmente no es necesario llamar a esta función, pero en algunos casos puede ser necesario.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxinitrichedit2"></a><a name="afxinitrichedit2"></a>AfxInitRichEditar2

Llame a esta función para inicializar el control rich edit (versión 2.0 y posteriores) para la aplicación.

```cpp
BOOL AFXAPI AfxInitRichEdit2();
```

### <a name="remarks"></a>Observaciones

Llame a esta función para cargar RICHED20. DLL e inicializar la versión 2.0 del control rich edit. Si se `Create` llama al método de [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md), [CRichEditView](../../mfc/reference/cricheditview-class.md)o [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), normalmente no es necesario llamar a esta función, pero en algunos casos puede ser necesario.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxisextendedframeclass"></a><a name="afxisextendedframeclass"></a>AfxIsExtendedFrameClass

Determina si la ventana dada es un objeto de marco extendido.

### <a name="syntax"></a>Sintaxis

```cpp
BOOL AFXAPI AfxIsExtendedFrameClass( CWnd* pWnd );
```

### <a name="parameters"></a>Parámetros

*pWnd*\
[en] Puntero a un objeto derivado `CWnd`de .

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana proporcionada es un objeto de marco extendido; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método devuelve TRUE si *pWnd* deriva de una de las clases siguientes:

- `CFrameWndEx`

- `CMDIFrameWndEx`

- `COleIPFrameWndEx`

- `COleDocIPFrameWndEx`

- `CMDIChildWndEx`

Este método es útil cuando tiene que validar que un parámetro de función o método es una ventana de marco extendido.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxismfctoolbar"></a><a name="afxismfctoolbar"></a>AfxIsMFCToolBar

Determina si la ventana dada es un objeto de barra de herramientas.

### <a name="syntax"></a>Sintaxis

```cpp
BOOL AFXAPI AfxIsMFCToolBar(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*\
[en] Puntero a un objeto derivado `CWnd`de .

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana proporcionada es un objeto de barra de herramientas; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Este método `TRUE` devuelve si *pWnd* deriva de `CMFCToolBar`. Este método es útil cuando tiene que validar que `CMFCToolBar` una función o parámetro de método es un objeto.

### <a name="requirements"></a>Requisitos

**Encabezado:** afxpriv.h

## <a name="afxkeyboardmanager"></a><a name="afxkeyboardmanager"></a>AfxKeyboardManager

Puntero al [administrador](ckeyboardmanager-class.md)de teclado global .

### <a name="syntax"></a>Sintaxis

```cpp
CKeyboardManager* afxKeyboardManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxkeyboardmanager.h

## <a name="afxloadlibrary"></a><a name="afxloadlibrary"></a>AfxLoadLibrary

Se `AfxLoadLibrary` utiliza para asignar un módulo DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibrary(LPCTSTR lpszModuleName);
```

### <a name="parameters"></a>Parámetros

*lpszModuleName*\
Apunta a una cadena terminada en null que contiene el nombre del módulo (ya sea un archivo . DLL o . EXE). El nombre especificado es el nombre de archivo del módulo.

Si la cadena especifica una ruta de acceso pero el archivo no existe en el directorio especificado, se produce un error en la función.

Si no se especifica una ruta de acceso y se omite la extensión de nombre de archivo, la extensión predeterminada . DLL se anexa. Sin embargo, la cadena de nombre de archivo puede incluir un carácter de punto final (.) para indicar que el nombre del módulo no tiene ninguna extensión. Cuando no se especifica ninguna ruta de acceso, la función utiliza el orden de [búsqueda para aplicaciones](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)de escritorio .

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es un identificador del módulo. En caso de error, el valor devuelto es NULL.

### <a name="remarks"></a>Observaciones

Devuelve un identificador que se puede usar en [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) para obtener la dirección de una función DLL. `AfxLoadLibrary`también se puede utilizar para mapear otros módulos ejecutables.

Cada proceso mantiene un recuento de referencias para cada módulo de biblioteca cargado. Este recuento de referencias `AfxLoadLibrary` se incrementa cada vez que `AfxFreeLibrary` se llama y se reduce cada vez que se llama. Cuando el recuento de referencias llega a cero, el módulo se desasigna desde el espacio de direcciones del proceso de llamada y el identificador ya no es válido.

Asegúrese de `AfxLoadLibrary` `AfxFreeLibrary` usar y (en lugar `LoadLibrary` `FreeLibrary`de las funciones Win32 y ) si la aplicación usa varios subprocesos y si carga dinámicamente un archivo DLL de extensión MFC. Usar `AfxLoadLibrary` `AfxFreeLibrary` y asegura que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión MFC no daña el estado global de MFC.

El `AfxLoadLibrary` uso de una aplicación requiere que se vincule dinámicamente a la versión DLL de MFC. El archivo `AfxLoadLibrary`de encabezado para , Afxdll_.h, solo se incluye si MFC está vinculado a la aplicación como un archivo DLL. Este requisito es por diseño, porque tiene que vincular a la versión DLL de MFC para usar o crear archivos DLL de extensión MFC.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_DLLUser#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_7.cpp)]
[!code-cpp[NVC_MFC_DLLUser#2](../../mfc/reference/codesnippet/cpp/application-information-and-management_8.cpp)]
[!code-cpp[NVC_MFC_DLLUser#3](../../mfc/reference/codesnippet/cpp/application-information-and-management_9.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdll_.h

## <a name="afxloadlibraryex"></a><a name="afxloadlibraryex"></a>AfxLoadLibraryEx

Se `AfxLoadLibraryEx` utiliza para asignar un módulo DLL.

```cpp
HINSTANCE AFXAPI AfxLoadLibraryEx(LPCTSTR lpFileName, HANDLE hFile, DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

*lpFileName*\
Apunta a una cadena terminada en null que contiene el nombre del módulo (ya sea un archivo . DLL o . EXE). El nombre especificado es el nombre de archivo del módulo.

Si la cadena especifica una ruta de acceso pero el archivo no existe en el directorio especificado, se produce un error en la función.

Si no se especifica una ruta de acceso y se omite la extensión de nombre de archivo, la extensión predeterminada . DLL se anexa. Sin embargo, la cadena de nombre de archivo puede incluir un carácter de punto final (.) para indicar que el nombre del módulo no tiene ninguna extensión. Cuando no se especifica ninguna ruta de acceso, la función utiliza el orden de [búsqueda para aplicaciones](/windows/win32/dlls/dynamic-link-library-search-order#search-order-for-desktop-applications)de escritorio .

*hArchivo*\
Este parámetro se reserva para uso futuro. Debe ser NULL.

*Dwflags*\
La acción que se debe realizar al cargar el módulo. Si no se especifica ningún indicador, el comportamiento `AfxLoadLibrary` de esta función es idéntico a la función. Los valores posibles de este parámetro se describen en la documentación [de LoadLibraryEx.](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw)

### <a name="return-value"></a>Valor devuelto

Si la función se realiza correctamente, el valor devuelto es un identificador del módulo. En caso de error, el valor devuelto es NULL.

### <a name="remarks"></a>Observaciones

`AfxLoadLibraryEx`devuelve un identificador que se puede usar en [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) para obtener la dirección de una función DLL. `AfxLoadLibraryEx`también se puede utilizar para mapear otros módulos ejecutables.

Cada proceso mantiene un recuento de referencias para cada módulo de biblioteca cargado. Este recuento de referencias `AfxLoadLibraryEx` se incrementa cada vez que `AfxFreeLibrary` se llama y se reduce cada vez que se llama. Cuando el recuento de referencias llega a cero, el módulo se desasigna desde el espacio de direcciones del proceso de llamada y el identificador ya no es válido.

Asegúrese de `AfxLoadLibraryEx` `AfxFreeLibrary` usar y (en lugar `LoadLibraryEx` `FreeLibrary`de las funciones Win32 y ) si la aplicación usa varios subprocesos y si carga dinámicamente un archivo DLL de extensión MFC. Usar `AfxLoadLibraryEx` `AfxFreeLibrary` y garantiza que el código de inicio y apagado que se ejecuta cuando se carga y descarga el archivo DLL de extensión MFC no daña el estado global de MFC.

El `AfxLoadLibraryEx` uso de una aplicación requiere que se vincule dinámicamente a la versión DLL de MFC. El archivo `AfxLoadLibraryEx`de encabezado para , Afxdll_.h, solo se incluye si MFC está vinculado a la aplicación como un archivo DLL. Este requisito es por diseño, porque tiene que vincular a la versión DLL de MFC para usar o crear archivos DLL de extensión MFC.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxdll_.h

## <a name="afxmenutearoffmanager"></a><a name="afxmenutearoffmanager"></a>AfxMenuTearOffManager

Puntero al gestor de [menús de desmontaje](cmenutearoffmanager-class.md)global.

### <a name="syntax"></a>Sintaxis

```cpp
CMenuTearOffManager* g_pTearOffMenuManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmenutearoffmanager.h

## <a name="afxmousemanager"></a><a name="afxmousemanager"></a>AfxMouseManager

Puntero al [administrador](cmousemanager-class.md)global del mouse .

### <a name="syntax"></a>Sintaxis

```cpp
CMouseManager* afxMouseManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxmousemanager.h

## <a name="afxregisterclass"></a><a name="afxregisterclass"></a>AfxRegisterClass

Utilice esta función para registrar clases de ventana en un archivo DLL que usa MFC.

```cpp
BOOL AFXAPI AfxRegisterClass(WNDCLASS* lpWndClass);
```

### <a name="parameters"></a>Parámetros

*lpWndClass*\
Puntero a una estructura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) que contiene información sobre la clase de ventana que se va a registrar. Para obtener más información sobre esta estructura, consulte el Windows SDK.

### <a name="return-value"></a>Valor devuelto

TRUESi la clase se registra correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Si utiliza esta función, la clase se anula automáticamente cuando se descarga el archivo DLL.

En compilaciones que no `AfxRegisterClass` son DLL, el identificador se `RegisterClass`define como una macro que se asigna a la función de Windows, ya que las clases registradas en una aplicación se anulan automáticamente. Si usa `AfxRegisterClass` en `RegisterClass`lugar de , el código se puede usar sin cambios tanto en una aplicación como en un archivo DLL.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_DLL#3](../../atl-mfc-shared/codesnippet/cpp/application-information-and-management_10.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxregisterwndclass"></a><a name="afxregisterwndclass"></a>AfxRegisterWndClass

Le permite registrar sus propias clases de ventana.

```cpp
LPCTSTR AFXAPI AfxRegisterWndClass(
    UINT nClassStyle,
    HCURSOR hCursor = 0,
    HBRUSH hbrBackground = 0,
    HICON hIcon = 0);
```

### <a name="parameters"></a>Parámetros

*nClassStyle*\
Especifica el estilo de clase de Windows o la combinación de estilos, creada mediante el operador OR (**&#124;**) bit a bit, para la clase de ventana. Para obtener una lista de estilos de clase, vea la estructura [WNDCLASS](/windows/win32/api/winuser/ns-winuser-wndclassw) en el Windows SDK. Si NULL, los valores predeterminados se establecen de la siguiente manera:

- Establece el estilo del mouse en CS_DBLCLKS, que envía mensajes de doble clic al procedimiento de ventana cuando el usuario hace doble clic en el mouse.

- Establece el estilo del cursor de flecha en el IDC_ARROW estándar de Windows.

- Establece el pincel de fondo en NULL, por lo que la ventana no borrará su fondo.

- Establece el icono en el icono estándar del logotipo de Windows con bandera ondulante.

*hCursor*\
Especifica un identificador del recurso de cursor que se instalará en cada ventana creada a partir de la clase de ventana. Si utiliza el valor predeterminado de **0**, obtendrá el cursor de IDC_ARROW estándar.

*hbrBackground*\
Especifica un identificador para el recurso de pincel que se instalará en cada ventana creada a partir de la clase de ventana. Si usa el valor predeterminado de **0**, tendrá un pincel de fondo NULL y, de forma predeterminada, la ventana no borrará su fondo mientras procesa [WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd).

*hIcon*\
Especifica un identificador del recurso de icono que se instalará en cada ventana creada a partir de la clase de ventana. Si usas el valor predeterminado de **0**, obtendrás el icono estándar del logotipo de Windows con bandera ondulante.

### <a name="return-value"></a>Valor devuelto

Cadena terminada en null que contiene el nombre de clase. Puede pasar este nombre `Create` de clase `CWnd` a la función miembro en u otras clases derivadas de **CWnd para**crear una ventana. El nombre lo genera la biblioteca Microsoft Foundation Class.

> [!NOTE]
> El valor devuelto es un puntero a un búfer estático. Para guardar esta cadena, `CString` asígnela a una variable.

### <a name="remarks"></a>Observaciones

La biblioteca Microsoft Foundation Class registra automáticamente varias clases de ventana estándar. Llame a esta función si desea registrar sus propias clases de ventana.

El nombre registrado para `AfxRegisterWndClass` una clase por depende únicamente de los parámetros. Si llama `AfxRegisterWndClass` varias veces con parámetros idénticos, solo registra una clase en la primera llamada. Las llamadas posteriores con `AfxRegisterWndClass` parámetros idénticos devuelven el nombre de clase ya registrado.

Si llama `AfxRegisterWndClass` a varias clases derivadas de CWnd con parámetros idénticos, en lugar de obtener una clase de ventana independiente para cada clase, cada clase comparte la misma clase de ventana. Este uso compartido puede causar problemas si se utiliza el estilo de clase CS_CLASSDC. En lugar de varias clases de CS_CLASSDC de ventana, termina con una sola clase de ventana CS_CLASSDC. Todas las ventanas de C++ que utilizan esa clase comparten el mismo controlador de dominio. Para evitar este problema, llame a [AfxRegisterClass](#afxregisterclass) para registrar la clase.

Refiera a la nota técnica [TN001: Registro](../../mfc/tn001-window-class-registration.md) de la `AfxRegisterWndClass` clase de ventana para más información sobre el registro de la clase de ventana y la función.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#134](../../mfc/reference/codesnippet/cpp/application-information-and-management_11.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxsetperuserregistration"></a><a name="afxsetperuserregistration"></a>AfxSetPerUserRegistration

Establece si la aplicación redirige el acceso del Registro al nodo **HKEY_CURRENT_USER** (**HKCU**).

```cpp
void AFXAPI AfxSetPerUserRegistration(BOOL bEnable);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*\
[en] TRUE indica que la información del Registro se dirige al nodo HKCU. FALSE indica que la aplicación escribe información del Registro en el nodo predeterminado. El nodo predeterminado es **HKEY_CLASSES_ROOT** (**HKCR**).

### <a name="remarks"></a>Observaciones

Antes de Windows Vista, las aplicaciones que accedieron al registro solían usar el nodo **HKEY_CLASSES_ROOT.** Sin embargo, con Windows Vista o sistemas operativos posteriores, debe ejecutar una aplicación en modo elevado para escribir en HKCR.

Este método permite a la aplicación leer y escribir en el registro sin ejecutarse en modo elevado. Funciona redireccionando el acceso del registro de HKCR a HKCU. Para obtener más información, vea Páginas de propiedades del [vinculador](../../build/reference/linker-property-pages.md).

Si habilita la redirección del registro, el marco de trabajo redirige el acceso desde HKCR a **HKEY_CURRENT_USER- Software - Clases**. Solo los marcos MFC y ATL se ven afectados por la redirección.

La implementación predeterminada tiene acceso al registro en HKCR.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxstat_.h

## <a name="afxsetresourcehandle"></a><a name="afxsetresourcehandle"></a>AfxSetResourceHandle

Utilice esta función para establecer el identificador HINSTANCE que determina dónde se cargan los recursos predeterminados de la aplicación.

```cpp
void AFXAPI AfxSetResourceHandle(HINSTANCE hInstResource);
```

### <a name="parameters"></a>Parámetros

*hInstResource*\
La instancia o el módulo se encarga de un archivo . EXE o DLL desde el que se cargan los recursos de la aplicación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCWindowing#135](../../mfc/reference/codesnippet/cpp/application-information-and-management_12.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="afxshellmanager"></a><a name="afxshellmanager"></a>AfxShellManager

Puntero al [administrador](cshellmanager-class.md)de shell global .

### <a name="syntax"></a>Sintaxis

```cpp
CShellManager* afxShellManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxshellmanager.h

## <a name="afxsocketinit"></a><a name="afxsocketinit"></a>AfxSocketInit

Llame a esta `CWinApp::InitInstance` función en la invalidación para inicializar Windows Sockets.

```cpp
BOOL AfxSocketInit(WSADATA* lpwsaData = NULL);
```

### <a name="parameters"></a>Parámetros

*lpwsaData*\
Un puntero a una estructura [WSADATA.](/windows/win32/api/winsock2/ns-winsock2-wsadata) Si *lpwsaData* no es igual a NULL, `WSADATA` la dirección de `WSAStartup`la estructura se rellena mediante la llamada a . Esta función `WSACleanup` también garantiza que se llama para usted antes de que finalice la aplicación.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Al usar sockets MFC en subprocesos secundarios en una `AfxSocketInit` aplicación MFC vinculada estáticamente, debe llamar a cada subproceso que usa sockets para inicializar las bibliotecas de sockets. De forma `AfxSocketInit` predeterminada, solo se llama en el subproceso principal.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxsock.h

## <a name="afxusertoolsmanager"></a><a name="afxusertoolsmanager"></a>AfxUserToolsManager

Puntero al [administrador](cusertoolsmanager-class.md)global de herramientas de usuario .

### <a name="syntax"></a>Sintaxis

```cpp
CUserToolsManager* afxUserToolsManager;
```

### <a name="requirements"></a>Requisitos

**Encabezado:** afxusertoolsmanager.h

## <a name="afxwininit"></a><a name="afxwininit"></a>AfxWinInit

La función proporcionada por `WinMain` MFC llama a esta función, como parte de la inicialización de [CWinApp](../../mfc/reference/cwinapp-class.md) de una aplicación basada en GUI, para inicializar MFC.

```cpp
BOOL AFXAPI AfxWinInit(
    HINSTANCE hInstance,
    HINSTANCE hPrevInstance,
    LPTSTR lpCmdLine,
    int nCmdShow);
```

### <a name="parameters"></a>Parámetros

*hInstance*\
El identificador del módulo que se está ejecutando actualmente.

*hPrevInstance*\
Identificador de una instancia anterior de la aplicación. Para una aplicación basada en Win32, este parámetro siempre es **NULL**.

*lpCmdLine*\
Apunta a una cadena terminada en null que especifica la línea de comandos de la aplicación.

*nCmdShow*\
Especifica cómo se mostraría la ventana principal de una aplicación GUI.

### <a name="remarks"></a>Observaciones

Para una aplicación de consola, que no `WinMain` usa la `AfxWinInit` función proporcionada por MFC, debe llamar directamente para inicializar MFC.

Si se `AfxWinInit` llama a sí mismo, `CWinApp` debe declarar una instancia de una clase. Para una aplicación de consola, puede optar `CWinApp` por no derivar `CWinApp` su propia clase y, en su lugar, utilizar una instancia de directamente. Esta técnica es adecuada si decide dejar toda la funcionalidad de la aplicación en la implementación de **main**.

> [!NOTE]
> Cuando se crea un contexto de activación para un ensamblado, MFC usa un recurso de manifiesto proporcionado por el módulo de usuario. El contexto de `AfxWinInit`activación se crea en . Para obtener más información, vea Compatibilidad con contextos de [activación en el estado del módulo MFC](../../mfc/support-for-activation-contexts-in-the-mfc-module-state.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFC_AfxWinInit#1](../../mfc/reference/codesnippet/cpp/application-information-and-management_13.cpp)]

### <a name="requirements"></a>Requisitos

  **Encabezado** afxwin.h

## <a name="see-also"></a>Consulte también

[Macros y Globales](mfc-macros-and-globals.md)\
[Clase CWinApp](cwinapp-class.md)\
[Clase CContextMenuManager](ccontextmenumanager-class.md)\
[Clase CWnd](cwnd-class.md)\
[Clase CFrameWndEx](cframewndex-class.md)\
[CMFCToolBar (Clase)](cmfctoolbar-class.md)\
[Clase CKeyboardManager](ckeyboardmanager-class.md)\
[Clase CMenuTearOffManager](cmenutearoffmanager-class.md)\
[Clase CMouseManager](cmousemanager-class.md)\
[Clase CShellManager](cshellmanager-class.md)\
[Clase CUserToolsManager](cusertoolsmanager-class.md)
