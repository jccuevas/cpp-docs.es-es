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
ms.openlocfilehash: f2e95dd3ba8be31633590e37d95dedc8749ebdd8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367416"
---
# <a name="cwinthread-class"></a>CWinThread (clase)

Representa un subproceso de ejecución dentro de una aplicación.

## <a name="syntax"></a>Sintaxis

```
class CWinThread : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinThread::CWinThread](#cwinthread)|Construye un objeto `CWinThread`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinThread::CreateThread](#createthread)|Inicia la `CWinThread` ejecución de un objeto.|
|[CWinThread::ExitInstance](#exitinstance)|Reemplazar para limpiar cuando el subproceso termina.|
|[CWinThread::GetMainWnd](#getmainwnd)|Recupera un puntero a la ventana principal del subproceso.|
|[CWinThread::GetThreadPriority](#getthreadpriority)|Obtiene la prioridad del subproceso actual.|
|[CWinThread::InitInstance](#initinstance)|Invalidar para realizar la inicialización de la instancia de subproceso.|
|[CWinThread::IsIdleMessage](#isidlemessage)|Comprueba si hay mensajes especiales.|
|[CwinThread::OnIdle](#onidle)|Reemplazar para realizar el procesamiento en tiempo de inactividad específico del subproceso.|
|[CWinThread::PostThreadMessage](#postthreadmessage)|Envía un mensaje `CWinThread` a otro objeto.|
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtra los mensajes antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).|
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Intercepta ciertos mensajes antes de que lleguen a la aplicación.|
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Intercepta todas las excepciones no controladas producidas por los controladores de mensajes y comandos del subproceso.|
|[CWinThread::PumpMessage](#pumpmessage)|Contiene el bucle de mensajes del subproceso.|
|[CWinThread::ResumeThread](#resumethread)|Disminuye el recuento de suspensión de un subproceso.|
|[CWinThread::Ejecutar](#run)|Función de control para roscas con una bomba de mensajes. Reemplazar para personalizar el bucle de mensajes predeterminado.|
|[CWinThread::SetThreadPriority](#setthreadpriority)|Establece la prioridad del subproceso actual.|
|[CWinThread::SuspendThread](#suspendthread)|Incrementa el recuento de suspensión de un subproceso.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinThread::operador HANDLE](#operator_handle)|Recupera el identificador `CWinThread` del objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Especifica si se debe destruir el objeto al finalizar el subproceso.|
|[CWinThread::m_hThread](#m_hthread)|Controle el subproceso actual.|
|[CWinThread::m_nThreadID](#m_nthreadid)|ID del subproceso actual.|
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Puntero a la ventana principal de la aplicación contenedora cuando un servidor OLE está activo en el lugar.|
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Mantiene un puntero a la ventana principal de la aplicación.|

## <a name="remarks"></a>Observaciones

El subproceso principal de ejecución suele ser `CWinApp`proporcionado por un objeto derivado de ; `CWinApp` se deriva `CWinThread`de . Los `CWinThread` objetos adicionales permiten varios subprocesos dentro de una aplicación determinada.

Hay dos tipos generales `CWinThread` de subprocesos que admiten: subprocesos de trabajo y subprocesos de interfaz de usuario. Los subprocesos de trabajo no tienen ninguna bomba de mensajes: por ejemplo, un subproceso que realiza cálculos en segundo plano en una aplicación de hoja de cálculo. Los subprocesos de interfaz de usuario tienen una bomba de mensajes y procesan mensajes recibidos del sistema. [CWinApp](../../mfc/reference/cwinapp-class.md) y las clases derivadas de ella son ejemplos de subprocesos de interfaz de usuario. Otros subprocesos de interfaz de `CWinThread`usuario también se pueden derivar directamente de .

Los objetos de clase `CWinThread` suelen existir durante la duración del subproceso. Si desea modificar este comportamiento, establezca [m_bAutoDelete](#m_bautodelete) en FALSE.

La `CWinThread` clase es necesaria para que el código y MFC sean totalmente seguros para subprocesos. Los `CWinThread` objetos administran los datos locales de subprocesos utilizados por el marco de trabajo para mantener información específica del subproceso. Debido a esta `CWinThread` dependencia para controlar los datos locales de subprocesos, MFC debe crear cualquier subproceso que use MFC. Por ejemplo, un subproceso creado por la función en tiempo de ejecución [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) no puede usar ninguna API de MFC.

Para crear un subproceso, llame a [AfxBeginThread](application-information-and-management.md#afxbeginthread). Hay dos formularios, dependiendo de si desea un subproceso de trabajo o de interfaz de usuario. Si desea un subproceso de interfaz de usuario, pase a `AfxBeginThread` un puntero a la de la `CRuntimeClass` `CWinThread`clase derivada. Si desea crear un subproceso de `AfxBeginThread` trabajo, pase a un puntero a la función de control y el parámetro a la función de control. Tanto para subprocesos de trabajo como para subprocesos de interfaz de usuario, puede especificar parámetros opcionales que modifiquen la prioridad, el tamaño de la pila, los indicadores de creación y los atributos de seguridad. `AfxBeginThread`devolverá un puntero `CWinThread` al nuevo objeto.

En lugar `AfxBeginThread`de llamar `CWinThread`a , puede construir `CreateThread`un objeto derivado y, a continuación, llamar a . Este método de construcción de dos etapas `CWinThread` es útil si desea reutilizar el objeto entre la creación sucesiva y las terminaciones de ejecuciones de subprocesos.

Para obtener `CWinThread`más información sobre , vea los artículos [Multithreading con C++ y MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: Creating User-Interface Threads](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: Creating Worker Threads](../../parallel/multithreading-creating-worker-threads.md)y [Multithreading: How to Use the Synchronization Classes](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CWinThread`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread::CreateThread

Crea un subproceso para ejecutar dentro del espacio de direcciones del proceso de llamada.

```
BOOL CreateThread(
    DWORD dwCreateFlags = 0,
    UINT nStackSize = 0,
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```

### <a name="parameters"></a>Parámetros

*dwCreateFlags*<br/>
Especifica una marca adicional que controla la creación del subproceso. Este indicador puede contener uno de dos valores:

- CREATE_SUSPENDED Iniciar el subproceso con un recuento de suspensión de uno. Utilice CREATE_SUSPENDED si desea inicializar los `CWinThread` datos de miembro del objeto, como [m_bAutoDelete](#m_bautodelete) o cualquier miembro de la clase derivada, antes de que el subproceso comience a ejecutarse. Una vez completada la inicialización, use [CWinThread::ResumeThread](#resumethread) para iniciar la ejecución del subproceso. El subproceso no `CWinThread::ResumeThread` se ejecutará hasta que se llame.

- **0** Inicie el subproceso inmediatamente después de la creación.

*nStackSize*<br/>
Especifica el tamaño en bytes de la pila para el nuevo subproceso. Si **0**, el tamaño de pila tiene el mismo tamaño que el del subproceso principal del proceso.

*lpSecurityAttrs*<br/>
Apunta a una estructura [de SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) que especifica los atributos de seguridad para el subproceso.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el subproceso se crea correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Se `AfxBeginThread` utiliza para crear un objeto de subproceso y ejecutarlo en un paso. Utilícelo `CreateThread` si desea reutilizar el objeto de subproceso entre la creación sucesiva y la terminación de ejecuciones de subprocesos.

## <a name="cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread::CWinThread

Construye un objeto `CWinThread`.

```
CWinThread();
```

### <a name="remarks"></a>Observaciones

Para comenzar la ejecución del subproceso, llame a la [CreateThread](#createthread) función miembro. Normalmente creará subprocesos llamando a [AfxBeginThread](application-information-and-management.md#afxbeginthread), `CreateThread`que llamará a este constructor y .

## <a name="cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread::ExitInstance

Llamado por el marco de trabajo desde dentro de un Run rara vez invalidado [Ejecutar](#run) función miembro para salir de esta instancia del subproceso, o si se produce un error en una llamada a [InitInstance.](#initinstance)

```
virtual int ExitInstance();
```

### <a name="return-value"></a>Valor devuelto

Código de salida del subproceso; 0 indica que no hay errores y los valores mayores que 0 indican un error. Este valor se puede recuperar llamando a [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Observaciones

No llame a esta función `Run` miembro desde cualquier lugar, pero dentro de la función miembro. Esta función miembro solo se utiliza en subprocesos de interfaz de usuario.

La implementación predeterminada de `CWinThread` esta función elimina el objeto si [m_bAutoDelete](#m_bautodelete) es TRUE. Invalide esta función si desea realizar una limpieza adicional cuando finalice el subproceso. La implementación de `ExitInstance` debe llamar a la versión de la clase base después de ejecutar el código.

## <a name="cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread::GetMainWnd

Si la aplicación es un servidor OLE, llame a esta función para recuperar un `m_pMainWnd` puntero a la ventana principal activa de la aplicación en lugar de hacer referencia directamente al miembro del objeto de aplicación.

```
virtual CWnd* GetMainWnd();
```

### <a name="return-value"></a>Valor devuelto

Esta función devuelve un puntero a uno de los dos tipos de ventanas. Si el subproceso forma parte de un servidor OLE y tiene un objeto que está activo en su lugar `CWinThread` dentro de un contenedor activo, esta función devuelve el [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) miembro de datos del objeto.

Si no hay ningún objeto que esté activo en su lugar dentro de un contenedor o que la aplicación no sea un servidor OLE, esta función devuelve el [m_pMainWnd](#m_pmainwnd) miembro de datos del objeto de subproceso.

### <a name="remarks"></a>Observaciones

Para los subprocesos de interfaz de `m_pActiveWnd` usuario, esto equivale a hacer referencia directamente al miembro del objeto de aplicación.

Si la aplicación no es un servidor OLE, llamar a esta función equivale a hacer referencia directamente al miembro `m_pMainWnd` del objeto de aplicación.

Invalide esta función para modificar el comportamiento predeterminado.

## <a name="cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread::GetThreadPriority

Obtiene el nivel de prioridad de subproceso actual de este subproceso.

```
int GetThreadPriority();
```

### <a name="return-value"></a>Valor devuelto

El nivel de prioridad de subproceso actual dentro de su clase de prioridad. El valor devuelto será uno de los siguientes, listado de la prioridad más alta a la más baja:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Para obtener más información sobre estas prioridades, vea [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el Windows SDK.

## <a name="cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread::InitInstance

`InitInstance`debe reemplazarse para inicializar cada nueva instancia de un subproceso de interfaz de usuario.

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realiza correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Normalmente, se `InitInstance` reemplaza para realizar tareas que se deben completar cuando se crea un subproceso por primera vez.

Esta función miembro solo se utiliza en subprocesos de interfaz de usuario. Realizar la inicialización de subprocesos de trabajo en la función de control pasada a [AfxBeginThread](application-information-and-management.md#afxbeginthread).

## <a name="cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread::IsIdleMessage

Invalide esta `OnIdle` función para evitar que se llame después de que se generen mensajes específicos.

```
virtual BOOL IsIdleMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*Pmsg*<br/>
Apunta al mensaje actual que se está procesando.

### <a name="return-value"></a>Valor devuelto

Distinto de `OnIdle` cero si debe llamarse después de procesar el mensaje; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada `OnIdle` no llama después de los mensajes y mensajes de mouse redundantes generados por los datos de intercalación parpadeantes.

Si una aplicación ha creado `OnIdle` un temporizador corto, se llamará con frecuencia, lo que causa problemas de rendimiento. Para mejorar el rendimiento de `IsIdleMessage` una aplicación de `CWinApp`este tipo, invalide en la clase derivada de la aplicación para comprobar WM_TIMER mensajes de la siguiente manera:

[!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]

El manejo de WM_TIMER de esta manera mejorará el rendimiento de las aplicaciones que utilizan temporizadores cortos.

## <a name="cwinthreadm_bautodelete"></a><a name="m_bautodelete"></a>CWinThread::m_bAutoDelete

Especifica si el objeto `CWinThread` se debe eliminar automáticamente cuando finalice el subproceso.

```
BOOL m_bAutoDelete;
```

### <a name="remarks"></a>Observaciones

El `m_bAutoDelete` miembro de datos es una variable pública de tipo BOOL.

El valor `m_bAutoDelete` de no afecta a cómo se cierra el identificador de subproceso subyacente, pero afecta a la sincronización de cierre del identificador. El identificador de subproceso siempre se cierra cuando se destruye el objeto `CWinThread`.

## <a name="cwinthreadm_hthread"></a><a name="m_hthread"></a>CWinThread::m_hThread

Controlar el subproceso asociado `CWinThread`a este archivo .

```
HANDLE m_hThread;
```

### <a name="remarks"></a>Observaciones

El `m_hThread` miembro de datos es una variable pública de tipo HANDLE. Solo es válido si el objeto de subproceso del kernel subyacente existe actualmente y el identificador aún no se ha cerrado.

El destructor CWinThread llama `m_hThread`a CloseHandle en . Si [m_bAutoDelete](#m_bautodelete) es TRUE cuando finaliza el subproceso, el CWinThread objeto se destruye, que invalida los punteros a la CWinThread objeto y sus variables miembro. Es posible `m_hThread` que necesite que el miembro compruebe el valor de salida del subproceso o que espere una señal. Para mantener el CWinThread `m_hThread` objeto y su miembro durante `m_bAutoDelete` la ejecución del subproceso y después de que finaliza, establezca en FALSE antes de permitir que la ejecución de subprocesos para continuar. De lo contrario, el subproceso puede terminar, destruir el CWinThread objeto y cerrar el identificador antes de intentar usarlo. Si utiliza esta técnica, es responsable de la eliminación de la CWinThread objeto.

## <a name="cwinthreadm_nthreadid"></a><a name="m_nthreadid"></a>CWinThread::m_nThreadID

Identificador del subproceso asociado `CWinThread`a este archivo .

```
DWORD m_nThreadID;
```

### <a name="remarks"></a>Observaciones

El `m_nThreadID` miembro de datos es una variable pública de tipo DWORD. Solo es válido si actualmente existe un objeto de subproceso de kernel subyacente.
Consulte también comentarios sobre [m_hThread](#m_hthread) vida útil.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [AfxGetThread](application-information-and-management.md#afxgetthread).

## <a name="cwinthreadm_pactivewnd"></a><a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd

Utilice este miembro de datos para almacenar un puntero al objeto de ventana activo del subproceso.

```
CWnd* m_pActiveWnd;
```

### <a name="remarks"></a>Observaciones

La biblioteca Microsoft Foundation Class terminará automáticamente el `m_pActiveWnd` subproceso cuando se cierre la ventana a la que se hace referencia. Si este subproceso es el subproceso principal de una aplicación, la aplicación también se terminará. Si este miembro de datos es NULL, `CWinApp` se heredará la ventana activa del objeto de la aplicación. `m_pActiveWnd`es una variable `CWnd*`pública de tipo .

Normalmente, se establece esta variable `InitInstance`miembro al reemplazar . En un subproceso de trabajo, el valor de este miembro de datos se hereda de su subproceso primario.

## <a name="cwinthreadm_pmainwnd"></a><a name="m_pmainwnd"></a>CWinThread::m_pMainWnd

Utilice este miembro de datos para almacenar un puntero al objeto de ventana principal del subproceso.

```
CWnd* m_pMainWnd;
```

### <a name="remarks"></a>Observaciones

La biblioteca Microsoft Foundation Class terminará automáticamente el `m_pMainWnd` subproceso cuando se cierre la ventana a la que se hace referencia. Si este subproceso es el subproceso principal de una aplicación, la aplicación también se terminará. Si este miembro de datos es NULL, `CWinApp` la ventana principal del objeto de la aplicación se usará para determinar cuándo terminar el subproceso. `m_pMainWnd`es una variable `CWnd*`pública de tipo .

Normalmente, se establece esta variable `InitInstance`miembro al reemplazar . En un subproceso de trabajo, el valor de este miembro de datos se hereda de su subproceso primario.

## <a name="cwinthreadonidle"></a><a name="onidle"></a>CwinThread::OnIdle

Invalide esta función miembro para realizar el procesamiento en tiempo de inactividad.

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>Parámetros

*lCount*<br/>
Se llama a `OnIdle` un contador incrementado cada vez cuando la cola de mensajes del subproceso está vacía. Este recuento se restablece a 0 cada vez que se procesa un nuevo mensaje. Puede utilizar el parámetro *lCount* para determinar la longitud relativa del tiempo que el subproceso ha estado inactivo sin procesar un mensaje.

### <a name="return-value"></a>Valor devuelto

Distinto de cero para recibir más tiempo de procesamiento inactivo; 0 si no se necesita más tiempo de procesamiento inactivo.

### <a name="remarks"></a>Observaciones

`OnIdle`se llama en el bucle de mensajes predeterminado cuando la cola de mensajes del subproceso está vacía. Use la invalidación para llamar a sus propias tareas de controlador inactivo en segundo plano.

`OnIdle`debe devolver 0 para indicar que no se requiere ningún tiempo de procesamiento inactivo adicional. El parámetro *lCount* se `OnIdle` incrementa cada vez que se llama cuando la cola de mensajes está vacía y se restablece a 0 cada vez que se procesa un nuevo mensaje. Puede llamar a sus diferentes rutinas de inactividad en función de este recuento.

La implementación predeterminada de esta función miembro libera objetos temporales y bibliotecas de vínculos dinámicos no utilizados de la memoria.

Esta función miembro solo se utiliza en subprocesos de interfaz de usuario.

Dado que la aplicación `OnIdle` no puede procesar mensajes hasta que se devuelve, no realice tareas largas en esta función.

## <a name="cwinthreadoperator-handle"></a><a name="operator_handle"></a>CWinThread::operador HANDLE

Recupera el identificador `CWinThread` del objeto.

```
operator HANDLE() const;
```

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el identificador del objeto de subproceso; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Use el identificador para llamar directamente a las API de Windows.

## <a name="cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread::PostThreadMessage

Se llama para publicar un `CWinThread` mensaje definido por el usuario en otro objeto.

```
BOOL PostThreadMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

*Mensaje*<br/>
ID del mensaje definido por el usuario.

*wParam*<br/>
Primer parámetro de mensaje.

*lParam*<br/>
Segundo parámetro de mensaje.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El mensaje publicado se asigna al controlador de mensajes adecuado mediante la macro de mapa de mensajes ON_THREAD_MESSAGE.

> [!NOTE]
> Cuando se llama a [PostThreadMessage](/windows/win32/api/winuser/nf-winuser-postthreadmessagew), el mensaje se coloca en la cola de mensajes del subproceso. Sin embargo, dado que los mensajes publicados de esta manera no están asociados a una ventana, MFC no los distribuirá a controladores de mensajes o comandos. Para controlar estos mensajes, `PreTranslateMessage()` invalide la función de la clase derivada de CWinApp y controle los mensajes manualmente.

## <a name="cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage

Reemplace esta función para filtrar los mensajes de ventana antes de que se distribuyan a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage).

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*Pmsg*<br/>
Apunta a una [estructura MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene el mensaje que se debe procesar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el `PreTranslateMessage` mensaje se ha procesado por completo y no se debe procesar más. Cero si el mensaje debe procesarse de la manera normal.

### <a name="remarks"></a>Observaciones

Esta función miembro solo se utiliza en subprocesos de interfaz de usuario.

## <a name="cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter

La función de enlace del marco de trabajo llama a esta función miembro para filtrar y responder a determinados mensajes de Windows.

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>Parámetros

*Código*<br/>
Especifica un código de enlace. Esta función miembro utiliza el código para determinar cómo procesar *lpMsg.*

*lpMsg*<br/>
Un puntero a una [estructura MSG de](/windows/win32/api/winuser/ns-winuser-msg)Windows .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se procesa el mensaje; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Una función de enlace procesa eventos antes de que se envíen al procesamiento normal de mensajes de la aplicación.

Si invalida esta característica avanzada, asegúrese de llamar a la versión de clase base para mantener el procesamiento de enlaces del marco de trabajo.

## <a name="cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread::ProcessWndProcException

El marco de trabajo llama a esta función miembro siempre que el controlador no detecta una excepción iniciada en uno de los controladores de comandos o mensajes del subproceso.

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

*e*<br/>
Apunta a una excepción no controlada.

*Pmsg*<br/>
Apunta a una [estructura MSG](/windows/win32/api/winuser/ns-winuser-msg) que contiene información sobre el mensaje de Windows que provocó que el marco de trabajo producira una excepción.

### <a name="return-value"></a>Valor devuelto

-1 si se genera una WM_CREATE excepción; de lo contrario 0.

### <a name="remarks"></a>Observaciones

No llame a esta función miembro directamente.

La implementación predeterminada de esta función miembro controla solo las excepciones generadas a partir de los siguientes mensajes:

|Get-Help|Acción|
|-------------|------------|
|WM_CREATE|Fallar.|
|WM_PAINT|Valide la ventana afectada, evitando así que se genere otro mensaje WM_PAINT.|

Invalide esta función miembro para proporcionar el control global de las excepciones. Llame a la funcionalidad base solo si desea mostrar el comportamiento predeterminado.

Esta función miembro solo se utiliza en subprocesos que tienen una bomba de mensajes.

## <a name="cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread::PumpMessage

Contiene el bucle de mensajes del subproceso.

```
virtual BOOL PumpMessage();
```

### <a name="remarks"></a>Observaciones

`PumpMessage`contiene el bucle de mensajes del subproceso. `PumpMessage`es llamado `CWinThread` por para bombear los mensajes del hilo. Puede llamar `PumpMessage` directamente para forzar el procesamiento `PumpMessage` de los mensajes o puede invalidar para cambiar su comportamiento predeterminado.

Llamar `PumpMessage` directamente y reemplazar su comportamiento predeterminado se recomienda solo para usuarios avanzados.

## <a name="cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread::ResumeThread

Se llama para reanudar la ejecución de un subproceso suspendido por el [SuspendThread](#suspendthread) función miembro o un subproceso creado con el CREATE_SUSPENDED marca.

```
DWORD ResumeThread();
```

### <a name="return-value"></a>Valor devuelto

El recuento de suspensión anterior del subproceso si se realiza correctamente; `0xFFFFFFFF` de lo contrario. Si el valor devuelto es cero, el subproceso actual no se suspendió. Si el valor devuelto es uno, el subproceso se suspendió, pero ahora se reinicia. Cualquier valor devuelto mayor que uno significa que el subproceso permanece suspendido.

### <a name="remarks"></a>Observaciones

El recuento de suspensión del subproceso actual se reduce en uno. Si el recuento de suspensión se reduce a cero, el subproceso reanuda la ejecución; de lo contrario, el subproceso permanece suspendido.

## <a name="cwinthreadrun"></a><a name="run"></a>CWinThread::Ejecutar

Proporciona un bucle de mensajes predeterminado para los subprocesos de interfaz de usuario.

```
virtual int Run();
```

### <a name="return-value"></a>Valor devuelto

Un valor **int** devuelto por el subproceso. Este valor se puede recuperar llamando a [GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread).

### <a name="remarks"></a>Observaciones

`Run`adquiere y distribuye mensajes de Windows hasta que la aplicación recibe un mensaje [de WM_QUIT.](/windows/win32/winmsg/wm-quit) Si la cola de mensajes del `Run` subproceso `OnIdle` no contiene actualmente mensajes, llama para realizar el procesamiento en tiempo de inactividad. Los mensajes entrantes van a la [PreTranslateMessage](#pretranslatemessage) función miembro para un procesamiento especial y, a continuación, a la función de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) para la traducción de teclado estándar. Por último, se llama a la función [DeSDispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage)

`Run`rara vez se invalida, pero puede invalidarlo para implementar un comportamiento especial.

Esta función miembro solo se utiliza en subprocesos de interfaz de usuario.

## <a name="cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread::SetThreadPriority

Esta función establece el nivel de prioridad del subproceso actual dentro de su clase de prioridad.

```
BOOL SetThreadPriority(int nPriority);
```

### <a name="parameters"></a>Parámetros

*nPrioridad*<br/>
Especifica el nuevo nivel de prioridad de subproceso dentro de su clase de prioridad. Este parámetro debe ser uno de los siguientes valores, enumerados de la prioridad más alta a la más baja:

- THREAD_PRIORITY_TIME_CRITICAL

- THREAD_PRIORITY_HIGHEST

- THREAD_PRIORITY_ABOVE_NORMAL

- THREAD_PRIORITY_NORMAL

- THREAD_PRIORITY_BELOW_NORMAL

- THREAD_PRIORITY_LOWEST

- THREAD_PRIORITY_IDLE

Para obtener más información sobre estas prioridades, vea [SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Solo se puede llamar después de [que CreateThread](#createthread) devuelva correctamente.

## <a name="cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread::SuspendThread

Incrementa el recuento de suspensión del subproceso actual.

```
DWORD SuspendThread();
```

### <a name="return-value"></a>Valor devuelto

El recuento de suspensión anterior del subproceso si se realiza correctamente; `0xFFFFFFFF` de lo contrario.

### <a name="remarks"></a>Observaciones

Si algún subproceso tiene un recuento de suspensión por encima de cero, ese subproceso no se ejecuta. El subproceso se puede reanudar mediante una llamada a la [ResumeThread](#resumethread) función miembro.

## <a name="see-also"></a>Consulte también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CWinApp](../../mfc/reference/cwinapp-class.md)<br/>
[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
