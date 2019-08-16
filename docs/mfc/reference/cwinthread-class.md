---
title: CWinThread (clase)
ms.date: 11/04/2016
f1_keywords:
- CWinThread
- AFXWIN/CWinThread
- AFXWIN/CWinThread::CWinThread
- AFXWIN/CWinThread::CreateThread
- AFXWIN/CWinThread::ExitInstance
- AFXWIN/CWinThread::GetMainWnd
- AFXWIN/CWinThread::GetThreadPriority
- AFXWIN/CWinThread::InitInstance
- AFXWIN/CWinThread::IsIdleMessage
- AFXWIN/CWinThread::OnIdle
- AFXWIN/CWinThread::PostThreadMessage
- AFXWIN/CWinThread::PreTranslateMessage
- AFXWIN/CWinThread::ProcessMessageFilter
- AFXWIN/CWinThread::ProcessWndProcException
- AFXWIN/CWinThread::PumpMessage
- AFXWIN/CWinThread::ResumeThread
- AFXWIN/CWinThread::Run
- AFXWIN/CWinThread::SetThreadPriority
- AFXWIN/CWinThread::SuspendThread
- AFXWIN/CWinThread::m_bAutoDelete
- AFXWIN/CWinThread::m_hThread
- AFXWIN/CWinThread::m_nThreadID
- AFXWIN/CWinThread::m_pActiveWnd
- AFXWIN/CWinThread::m_pMainWnd
helpviewer_keywords:
- CWinThread [MFC], CWinThread
- CWinThread [MFC], CreateThread
- CWinThread [MFC], ExitInstance
- CWinThread [MFC], GetMainWnd
- CWinThread [MFC], GetThreadPriority
- CWinThread [MFC], InitInstance
- CWinThread [MFC], IsIdleMessage
- CWinThread [MFC], OnIdle
- CWinThread [MFC], PostThreadMessage
- CWinThread [MFC], PreTranslateMessage
- CWinThread [MFC], ProcessMessageFilter
- CWinThread [MFC], ProcessWndProcException
- CWinThread [MFC], PumpMessage
- CWinThread [MFC], ResumeThread
- CWinThread [MFC], Run
- CWinThread [MFC], SetThreadPriority
- CWinThread [MFC], SuspendThread
- CWinThread [MFC], m_bAutoDelete
- CWinThread [MFC], m_hThread
- CWinThread [MFC], m_nThreadID
- CWinThread [MFC], m_pActiveWnd
- CWinThread [MFC], m_pMainWnd
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
ms.openlocfilehash: 43154e1ec4c6b856ad203a4b9ac49e4f4bcf9576
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502395"
---
# <a name="cwinthread-class"></a>CWinThread (clase)

Representa un subproceso de ejecución dentro de una aplicación.

## <a name="syntax"></a>Sintaxis

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWinThread::CWinThread](#cwinthread)|Construye un objeto `CWinThread`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWinThread::CreateThread](#createthread)|Inicia la ejecución de `CWinThread` un objeto.|
|[CWinThread::ExitInstance](#exitinstance)|Invalide para limpiar cuando finalice el subproceso.|
|[CWinThread::GetMainWnd](#getmainwnd)|Recupera un puntero a la ventana principal del subproceso.|
|[CWinThread::GetThreadPriority](#getthreadpriority)|Obtiene la prioridad del subproceso actual.|
|[CWinThread::InitInstance](#initinstance)|Invalide para realizar la inicialización de instancia de subproceso.|
|[CWinThread::IsIdleMessage](#isidlemessage)|Comprueba los mensajes especiales.|
|[CWinThread::OnIdle](#onidle)|Invalide para realizar el procesamiento de tiempo de inactividad específico del subproceso.|
|[CWinThread::PostThreadMessage](#postthreadmessage)|Envía un mensaje a otro `CWinThread` objeto.|
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtra los mensajes antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Intercepta ciertos mensajes antes de que lleguen a la aplicación.|
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Intercepta todas las excepciones no controladas producidas por los controladores de comandos y mensajes del subproceso.|
|[CWinThread::PumpMessage](#pumpmessage)|Contiene el bucle de mensajes del subproceso.|
|[CWinThread::ResumeThread](#resumethread)|Disminuye el recuento de suspensiones de un subproceso.|
|[CWinThread::Run](#run)|Control de la función para los subprocesos con un bombeo de mensajes. Invalide para personalizar el bucle de mensajes predeterminado.|
|[CWinThread::SetThreadPriority](#setthreadpriority)|Establece la prioridad del subproceso actual.|
|[CWinThread::SuspendThread](#suspendthread)|Incrementa el recuento de suspensiones de un subproceso.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWinThread::operator HANDLE](#operator_handle)|Recupera el identificador del `CWinThread` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Especifica si se va a destruir el objeto en la terminación del subproceso.|
|[CWinThread::m_hThread](#m_hthread)|Identificador del subproceso actual.|
|[CWinThread::m_nThreadID](#m_nthreadid)|IDENTIFICADOR del subproceso actual.|
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Puntero a la ventana principal de la aplicación contenedora cuando un servidor OLE está activo en contexto.|
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Contiene un puntero a la ventana principal de la aplicación.|

## <a name="remarks"></a>Comentarios

Normalmente, el subproceso principal de ejecución es proporcionado por un objeto `CWinApp`derivado de; se deriva de `CWinThread`. `CWinApp` Los `CWinThread` objetos adicionales permiten varios subprocesos dentro de una aplicación determinada.

Hay dos tipos generales de subprocesos `CWinThread` que admiten: subprocesos de trabajo y subprocesos de la interfaz de usuario. Los subprocesos de trabajo no tienen bombeo de mensajes: por ejemplo, un subproceso que realiza cálculos en segundo plano en una aplicación de hoja de cálculo. Los subprocesos de la interfaz de usuario tienen un bombeo de mensajes y procesan los mensajes recibidos del sistema. [CWinApp](../../mfc/reference/cwinapp-class.md) y las clases derivadas de él son ejemplos de subprocesos de la interfaz de usuario. Otros subprocesos de la interfaz de usuario también se `CWinThread`pueden derivar directamente de.

Normalmente, los `CWinThread` objetos de la clase existen mientras dure el subproceso. Si desea modificar este comportamiento, establezca [m_bAutoDelete](#m_bautodelete) en false.

La `CWinThread` clase es necesaria para que el código y MFC sea totalmente seguro para subprocesos. Los datos locales de subprocesos utilizados por el marco de trabajo para mantener la información `CWinThread` específica del subproceso se administran mediante objetos. Debido a esta dependencia de `CWinThread` para controlar los datos locales de subprocesos, MFC debe crear cualquier subproceso que use MFC. Por ejemplo, un subproceso creado por la función en tiempo de ejecución _ [beginthread, _ beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) no puede usar ninguna API de MFC.

Para crear un subproceso, llame a [AfxBeginThread](application-information-and-management.md#afxbeginthread). Hay dos formas, dependiendo de si desea un subproceso de trabajo o de interfaz de usuario. Si desea un subproceso de interfaz de usuario, pase `AfxBeginThread` a un puntero `CRuntimeClass` al de la `CWinThread`clase derivada de. Si desea crear un subproceso de trabajo, pase a `AfxBeginThread` un puntero a la función controladora y al parámetro a la función controladora. Para los subprocesos de trabajo y los subprocesos de la interfaz de usuario, puede especificar parámetros opcionales que modifiquen la prioridad, el tamaño de la pila, las marcas de creación y los atributos de seguridad. `AfxBeginThread`devolverá un puntero al nuevo `CWinThread` objeto.

En lugar de llamar `AfxBeginThread`a, puede construir un `CWinThread`objeto derivado de y, a `CreateThread`continuación, llamar a. Este método de construcción en dos fases es útil si desea volver a usar `CWinThread` el objeto entre la creación y finalización sucesivas de las ejecuciones de subprocesos.

Para obtener más información `CWinThread`sobre, vea los artículos multithreading [ C++ con y MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [multithreading: Crear subprocesos de](../../parallel/multithreading-creating-user-interface-threads.md)interfaz [de usuario, multithreading: Crear subprocesos](../../parallel/multithreading-creating-worker-threads.md)de [trabajo y multithreading: Cómo usar las clases](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)de sincronización.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="createthread"></a>  CWinThread::CreateThread

Crea un subproceso para que se ejecute dentro del espacio de direcciones del proceso de llamada.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parámetros

*dwCreateFlags*<br/>
Especifica una marca adicional que controla la creación del subproceso. Esta marca puede contener uno de dos valores:

- CREATE_SUSPENDED inicia el subproceso con un recuento de suspensión de uno. Use CREATE_SUSPENDED si desea inicializar los datos de miembros del `CWinThread` objeto, como [m_bAutoDelete](#m_bautodelete) o cualquier miembro de la clase derivada, antes de que el subproceso empiece a ejecutarse. Una vez completada la inicialización, use [CWinThread:: ResumeThread](#resumethread) para iniciar el subproceso que se está ejecutando. El subproceso no se ejecutará hasta que `CWinThread::ResumeThread` se llame a.

- **0** inicie el subproceso inmediatamente después de la creación.

*nStackSize*<br/>
Especifica el tamaño en bytes de la pila para el nuevo subproceso. Si es **0**, el tamaño de la pila tiene como valor predeterminado el mismo tamaño que el del subproceso principal del proceso.

*lpSecurityAttrs*<br/>
Apunta a una estructura [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica los atributos de seguridad para el subproceso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el subproceso se crea correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Use `AfxBeginThread` para crear un objeto de subproceso y ejecutarlo en un solo paso. Use `CreateThread` si desea reutilizar el objeto de subproceso entre la creación y finalización sucesivas de ejecuciones de subprocesos.

##  <a name="cwinthread"></a>  CWinThread::CWinThread

Construye un objeto `CWinThread`.

```
CWinThread();
```

### <a name="remarks"></a>Comentarios

Para comenzar la ejecución del subproceso, llame a la función miembro [CreateThread](#createthread) . Normalmente, se crean subprocesos llamando a [AfxBeginThread](application-information-and-management.md#afxbeginthread), que llamará a `CreateThread`este constructor y.

##  <a name="exitinstance"></a>  CWinThread::ExitInstance

Lo llama el marco de trabajo desde una función de miembro de [ejecución](#run) que rara vez se invalida para salir de esta instancia del subproceso o si se produce un error en una llamada a [InitInstance](#initinstance) .

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Valor devuelto

Código de salida del subproceso; 0 indica que no hay errores y los valores mayores que 0 indican un error. Este valor se puede recuperar llamando a [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Comentarios

No llame a esta función miembro desde cualquier lugar pero dentro `Run` de la función miembro. Esta función miembro solo se utiliza en subprocesos de la interfaz de usuario.

La implementación predeterminada de esta función elimina el `CWinThread` objeto si [m_bAutoDelete](#m_bautodelete) es true. Invalide esta función si desea realizar una limpieza adicional cuando finalice el subproceso. Su implementación de `ExitInstance` debe llamar a la versión de la clase base después de ejecutar el código.

##  <a name="getmainwnd"></a>  CWinThread::GetMainWnd

Si la aplicación es un servidor OLE, llame a esta función para recuperar un puntero a la ventana principal activa de la aplicación en lugar de hacer referencia directamente `m_pMainWnd` al miembro del objeto de aplicación.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Valor devuelto

Esta función devuelve un puntero a uno de dos tipos de ventanas. Si el subproceso forma parte de un servidor OLE y tiene un objeto activo en contexto dentro de un contenedor activo, esta función devuelve el miembro de datos [CWinApp:: m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) del `CWinThread` objeto.

Si no hay ningún objeto activo en contexto dentro de un contenedor o la aplicación no es un servidor OLE, esta función devuelve el miembro de datos [m_pMainWnd](#m_pmainwnd) del objeto de subproceso.

### <a name="remarks"></a>Comentarios

En el caso de subprocesos de la interfaz de usuario, es `m_pActiveWnd` equivalente a hacer referencia directamente al miembro del objeto de aplicación.

Si la aplicación no es un servidor OLE, llamar a esta función equivale a hacer referencia directamente al miembro `m_pMainWnd` del objeto de aplicación.

Invalide esta función para modificar el comportamiento predeterminado.

##  <a name="getthreadpriority"></a>  CWinThread::GetThreadPriority

Obtiene el nivel de prioridad del subproceso actual de este subproceso.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Valor devuelto

Nivel de prioridad del subproceso actual dentro de su clase de prioridad. El valor devuelto será uno de los siguientes, enumerados de la prioridad más alta a la más baja:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Para obtener más información sobre estas prioridades, vea [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el Windows SDK.

##  <a name="initinstance"></a>  CWinThread::InitInstance

`InitInstance`se debe invalidar para inicializar cada nueva instancia de un subproceso de la interfaz de usuario.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización es correcta; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Normalmente, se invalida `InitInstance` para realizar tareas que deben completarse cuando se crea un subproceso por primera vez.

Esta función miembro solo se utiliza en subprocesos de la interfaz de usuario. Realice la inicialización de los subprocesos de trabajo en la función de control que se pasa a [AfxBeginThread](application-information-and-management.md#afxbeginthread).

##  <a name="isidlemessage"></a>  CWinThread::IsIdleMessage

Invalide esta función `OnIdle` para evitar que se realice una llamada después de que se generen mensajes específicos.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*pMsg*<br/>
Apunta al mensaje actual que se está procesando.

### <a name="return-value"></a>Valor devuelto

Es distinto de `OnIdle` cero si debe llamarse después del mensaje de procesamiento; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La implementación predeterminada no llama a `OnIdle` después de mensajes de mouse redundantes y mensajes generados por las intercalaciones de parpadeo.

Si una aplicación ha creado un temporizador breve, `OnIdle` se llamará con frecuencia, lo que provocará problemas de rendimiento. Para mejorar el rendimiento de esta aplicación, invalide `IsIdleMessage` en la clase derivada de la `CWinApp`aplicación para comprobar los mensajes WM_TIMER de la manera siguiente:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

El control de WM_TIMER de este modo mejorará el rendimiento de las aplicaciones que usan temporizadores cortos.

##  <a name="m_bautodelete"></a>  CWinThread::m_bAutoDelete

Especifica si el objeto `CWinThread` se debe eliminar automáticamente cuando finalice el subproceso.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Comentarios

El `m_bAutoDelete` miembro de datos es una variable pública de tipo bool.

El valor de `m_bAutoDelete` no afecta al modo en que se cierra el identificador del subproceso subyacente, pero afecta a la temporización de cierre del identificador. El identificador de subproceso siempre se cierra cuando se destruye el objeto `CWinThread`.

##  <a name="m_hthread"></a>  CWinThread::m_hThread

Identificador del subproceso asociado a este `CWinThread`.

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Comentarios

El `m_hThread` miembro de datos es una variable pública de identificador de tipo. Solo es válido si el objeto de subproceso de kernel subyacente existe actualmente y el identificador todavía no se ha cerrado.

El destructor CWinThread llama a CloseHandle `m_hThread`en. Si [m_bAutoDelete](#m_bautodelete) es true cuando finaliza el subproceso, se destruye el objeto CWinThread, lo que invalida los punteros al objeto CWinThread y sus variables miembro. Es posible que necesite `m_hThread` el miembro para comprobar el valor de salida del subproceso o para esperar una señal. Para mantener el objeto CWinThread y su `m_hThread` miembro durante la ejecución del subproceso y después de que `m_bAutoDelete` finalice, establezca en false antes de permitir que continúe la ejecución de subprocesos. De lo contrario, el subproceso puede terminar, destruir el objeto CWinThread y cerrar el identificador antes de intentar usarlo. Si utiliza esta técnica, es responsable de la eliminación del objeto CWinThread.

##  <a name="m_nthreadid"></a>  CWinThread::m_nThreadID

IDENTIFICADOR del subproceso asociado a este `CWinThread`.

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Comentarios

El `m_nThreadID` miembro de datos es una variable pública de tipo DWORD. Solo es válido si el objeto de subproceso de kernel subyacente existe actualmente.
Vea también comentarios sobre la duración de [m_hThread](#m_hthread) .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [AfxGetThread](application-information-and-management.md#afxgetthread).

##  <a name="m_pactivewnd"></a>  CWinThread::m_pActiveWnd

Utilice este miembro de datos para almacenar un puntero al objeto de ventana activo del subproceso.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Comentarios

El biblioteca MFC finalizará automáticamente el subproceso cuando `m_pActiveWnd` se cierre la ventana a la que hace referencia. Si este subproceso es el subproceso principal de una aplicación, la aplicación también se terminará. Si este miembro de datos es null, se heredará la ventana activa `CWinApp` del objeto de la aplicación. `m_pActiveWnd`es una variable pública de tipo `CWnd*`.

Normalmente, se establece esta variable miembro al reemplazar `InitInstance`. En un subproceso de trabajo, el valor de este miembro de datos se hereda de su subproceso primario.

##  <a name="m_pmainwnd"></a>  CWinThread::m_pMainWnd

Use este miembro de datos para almacenar un puntero al objeto de ventana principal del subproceso.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Comentarios

El biblioteca MFC finalizará automáticamente el subproceso cuando `m_pMainWnd` se cierre la ventana a la que hace referencia. Si este subproceso es el subproceso principal de una aplicación, la aplicación también se terminará. Si este miembro de datos es null, se utilizará la ventana principal `CWinApp` del objeto de la aplicación para determinar cuándo debe terminarse el subproceso. `m_pMainWnd`es una variable pública de tipo `CWnd*`.

Normalmente, se establece esta variable miembro al reemplazar `InitInstance`. En un subproceso de trabajo, el valor de este miembro de datos se hereda de su subproceso primario.

##  <a name="onidle"></a>  CWinThread::OnIdle

Invalide esta función miembro para realizar el procesamiento en tiempo de inactividad.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
Un contador incrementado cada vez `OnIdle` que se llama cuando la cola de mensajes del subproceso está vacía. Este recuento se restablece en 0 cada vez que se procesa un mensaje nuevo. Puede usar el parámetro *lCount* para determinar la cantidad relativa de tiempo que el subproceso ha estado inactivo sin procesar un mensaje.

### <a name="return-value"></a>Valor devuelto

Distinto de cero para recibir más tiempo de procesamiento inactivo; 0 si no se necesita más tiempo de procesamiento inactivo.

### <a name="remarks"></a>Comentarios

`OnIdle`se llama a en el bucle de mensajes predeterminado cuando la cola de mensajes del subproceso está vacía. Use la invalidación para llamar a sus propias tareas de controlador de inactividad en segundo plano.

`OnIdle`debe devolver 0 para indicar que no se requiere tiempo de procesamiento de inactividad adicional. El parámetro *lCount* se incrementa cada vez `OnIdle` que se llama a cuando la cola de mensajes está vacía y se restablece en 0 cada vez que se procesa un mensaje nuevo. Puede llamar a sus distintas rutinas inactivas en función de este recuento.

La implementación predeterminada de esta función miembro libera objetos temporales y bibliotecas de vínculos dinámicos no utilizadas de la memoria.

Esta función miembro solo se utiliza en subprocesos de la interfaz de usuario.

Dado que la aplicación no puede procesar `OnIdle` mensajes hasta que devuelve, no realice tareas largas en esta función.

##  <a name="operator_handle"></a>CWinThread:: Operator (identificador)

Recupera el identificador del `CWinThread` objeto.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Valor devuelto

Si es correcto, el identificador del objeto de subproceso; de lo contrario, es NULL.

### <a name="remarks"></a>Comentarios

Use el identificador para llamar directamente a las API de Windows.

##  <a name="postthreadmessage"></a>  CWinThread::PostThreadMessage

Se llama para publicar un mensaje definido por el usuario `CWinThread` en otro objeto.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*message*<br/>
IDENTIFICADOR del mensaje definido por el usuario.

*wParam*<br/>
Primer parámetro de mensaje.

*lParam*<br/>
Segundo parámetro del mensaje.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El mensaje expuesto se asigna al controlador de mensajes adecuado mediante la macro de mapa de mensajes ON_THREAD_MESSAGE.

> [!NOTE]
> Cuando se llama a [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew), el mensaje se coloca en la cola de mensajes del subproceso. Sin embargo, dado que los mensajes publicados de esta manera no están asociados a una ventana, MFC no los enviará a los controladores de mensajes o comandos. Para controlar estos mensajes, invalide la `PreTranslateMessage()` función de la clase derivada de CWinApp y controle los mensajes manualmente.

##  <a name="pretranslatemessage"></a>  CWinThread::PreTranslateMessage

Invalide esta función para filtrar los mensajes de ventana antes de enviarlos a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*pMsg*<br/>
Apunta a una [estructura MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene el mensaje que se va a procesar.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si el mensaje se ha `PreTranslateMessage` procesado completamente en y no se debe procesar aún más. Cero si el mensaje se debe procesar de la manera normal.

### <a name="remarks"></a>Comentarios

Esta función miembro solo se utiliza en subprocesos de la interfaz de usuario.

##  <a name="processmessagefilter"></a>CWinThread::P rocessMessageFilter

La función de enlace del marco de trabajo llama a esta función miembro para filtrar y responder a ciertos mensajes de Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*code*<br/>
Especifica un código de enlace. Esta función miembro usa el código para determinar cómo procesar *lpMsg.*

*lpMsg*<br/>
Puntero a una estructura de [mensajes](/windows/win32/api/winuser/ns-winuser-msg)de Windows.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se procesa el mensaje; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Una función de enlace procesa los eventos antes de que se envíen al procesamiento de mensajes normal de la aplicación.

Si invalida esta característica avanzada, asegúrese de llamar a la versión de la clase base para mantener el procesamiento de enlace del marco.

##  <a name="processwndprocexception"></a>  CWinThread::ProcessWndProcException

El marco de trabajo llama a esta función miembro siempre que el controlador no detecta una excepción que se produce en uno de los controladores de mensajes o comandos del subproceso.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*e*<br/>
Apunta a una excepción no controlada.

*pMsg*<br/>
Apunta a una [estructura MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene información sobre el mensaje de Windows que hizo que el marco de trabajo produjera una excepción.

### <a name="return-value"></a>Valor devuelto

-1 si se genera una excepción WM_CREATE; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

No llame a esta función miembro directamente.

La implementación predeterminada de esta función miembro solo controla las excepciones generadas a partir de los siguientes mensajes:

|Get-Help|.|
|-------------|------------|
|WM_CREATE|Puedan.|
|WM_PAINT|Valida la ventana afectada, lo que impide que se genere otro mensaje WM_PAINT.|

Invalide esta función miembro para proporcionar el control global de las excepciones. Llame a la funcionalidad base solo si desea mostrar el comportamiento predeterminado.

Esta función miembro solo se utiliza en subprocesos que tienen un bombeo de mensajes.

##  <a name="pumpmessage"></a>CWinThread::P umpMessage

Contiene el bucle de mensajes del subproceso.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Comentarios

`PumpMessage`contiene el bucle de mensajes del subproceso. `PumpMessage`llama `CWinThread` a para bombear los mensajes del subproceso. Puede llamar `PumpMessage` directamente para forzar el procesamiento de los mensajes o puede invalidar `PumpMessage` para cambiar su comportamiento predeterminado.

Solo `PumpMessage` se recomienda llamar a directamente y reemplazar su comportamiento predeterminado para usuarios avanzados.

##  <a name="resumethread"></a>  CWinThread::ResumeThread

Se llama para reanudar la ejecución de un subproceso suspendido por la función miembro [SuspendThread](#suspendthread) , o un subproceso creado con la marca CREATE_SUSPENDED.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Valor devuelto

Recuento de suspensión anterior del subproceso si se realiza correctamente; `0xFFFFFFFF` en caso contrario,. Si el valor devuelto es cero, el subproceso actual no se suspendió. Si el valor devuelto es uno, se suspendió el subproceso, pero ahora se reiniciará. Cualquier valor devuelto mayor que uno significa que el subproceso permanece suspendido.

### <a name="remarks"></a>Comentarios

El recuento de suspensión del subproceso actual se reduce en uno. Si el recuento de suspensiones se reduce a cero, el subproceso reanuda la ejecución; de lo contrario, el subproceso permanece suspendido.

##  <a name="run"></a>  CWinThread::Run

Proporciona un bucle de mensajes predeterminado para los subprocesos de la interfaz de usuario.

```
virtual int Run();
```

### <a name="return-value"></a>Valor devuelto

Valor **int** devuelto por el subproceso. Este valor se puede recuperar llamando a [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Comentarios

`Run`adquiere y envía mensajes de Windows hasta que la aplicación recibe un mensaje [WM_QUIT](/windows/win32/winmsg/wm-quit) . Si la cola de mensajes del subproceso no contiene ningún `Run` mensaje `OnIdle` , llama a para realizar el procesamiento en tiempo de inactividad. Los mensajes entrantes van a la función miembro [PreTranslateMessage](#pretranslatemessage) para su procesamiento especial y, a continuación, a la función de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) para la traducción de teclado estándar. Por último, se llama a la función de Windows [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) .

`Run`rara vez se invalida, pero puede invalidarlo para implementar un comportamiento especial.

Esta función miembro solo se utiliza en subprocesos de la interfaz de usuario.

##  <a name="setthreadpriority"></a>  CWinThread::SetThreadPriority

Esta función establece el nivel de prioridad del subproceso actual dentro de su clase de prioridad.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parámetros

*nPriority*<br/>
Especifica el nuevo nivel de prioridad del subproceso dentro de su clase de prioridad. Este parámetro debe ser uno de los siguientes valores, que se enumeran de la prioridad más alta a la más baja:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Para obtener más información sobre estas prioridades, vea [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Solo se puede llamar después de que [CreateThread](#createthread) devuelva correctamente.

##  <a name="suspendthread"></a>  CWinThread::SuspendThread

Incrementa el recuento de suspensiones del subproceso actual.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Valor devuelto

Recuento de suspensión anterior del subproceso si se realiza correctamente; `0xFFFFFFFF` en caso contrario,.

### <a name="remarks"></a>Comentarios

Si un subproceso tiene un recuento de suspensión por encima de cero, ese subproceso no se ejecuta. El subproceso se puede reanudar mediante una llamada a la función miembro [ResumeThread](#resumethread) .

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWinApp (clase)](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
