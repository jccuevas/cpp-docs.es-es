---
title: CWinThread (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 406fc12869d6fe02188de6e469af17b3809df9b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cwinthread-class"></a>CWinThread (clase)
Representa un subproceso de ejecución dentro de una aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CWinThread : public CCmdTarget  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinThread::CWinThread](#cwinthread)|Construye un objeto `CWinThread`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinThread:: CreateThread](#createthread)|Inicia la ejecución de un `CWinThread` objeto.|  
|[CWinThread::ExitInstance](#exitinstance)|Reemplace este valor para limpiar cuando finaliza el subproceso.|  
|[CWinThread::GetMainWnd](#getmainwnd)|Recupera un puntero a la ventana principal para el subproceso.|  
|[CWinThread::GetThreadPriority](#getthreadpriority)|Obtiene la prioridad del subproceso actual.|  
|[CWinThread::InitInstance](#initinstance)|Reemplace este valor para realizar la inicialización de la instancia de subproceso.|  
|[CWinThread::IsIdleMessage](#isidlemessage)|Comprueba si hay mensajes especiales.|  
|[CWinThread::OnIdle](#onidle)|Reemplace este valor para realizar el procesamiento de tiempo de inactividad específicos del subproceso.|  
|[CWinThread::PostThreadMessage](#postthreadmessage)|Envía un mensaje a otro `CWinThread` objeto.|  
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtra los mensajes antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Intercepta determinados mensajes antes de alcanzar la aplicación.|  
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Intercepta todas las excepciones no controladas producidas por el mensaje del subproceso y controladores de comandos.|  
|[CWinThread::PumpMessage](#pumpmessage)|Contiene el bucle de mensajes del subproceso.|  
|[CWinThread:: ResumeThread](#resumethread)|Recuento de suspensiones disminuye una del subproceso.|  
|[CWinThread:: Run](#run)|Función controladora para subprocesos con una bomba de mensaje. Invalidar para personalizar el bucle de mensajes de forma predeterminada.|  
|[CWinThread::SetThreadPriority](#setthreadpriority)|Establece la prioridad del subproceso actual.|  
|[CWinThread:: SuspendThread](#suspendthread)|Recuento de suspensiones de incrementos un del subproceso.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinThread::operator identificador](#operator_handle)|Recupera el identificador de la `CWinThread` objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Especifica si se destruye el objeto cuando finalice el subproceso.|  
|[CWinThread::m_hThread](#m_hthread)|Identificador del subproceso actual.|  
|[CWinThread::m_nThreadID](#m_nthreadid)|Identificador del subproceso actual.|  
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Puntero a la ventana principal de la aplicación contenedora cuando un servidor OLE está activo en contexto.|  
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Contiene un puntero a la ventana principal de la aplicación.|  
  
## <a name="remarks"></a>Comentarios  
 El subproceso principal de ejecución suele proporcionar un objeto derivado de `CWinApp`; `CWinApp` se deriva de `CWinThread`. Adicionales `CWinThread` objetos permiten que varios subprocesos dentro de una aplicación determinada.  
  
 Hay dos tipos generales de subprocesos que `CWinThread` es compatible con: subprocesos de trabajo y los subprocesos de interfaz de usuario. Subprocesos de trabajo no tienen ningún suministro de mensajes: por ejemplo, un subproceso que realiza cálculos de fondo en una aplicación de hoja de cálculo. Subprocesos de interfaz de usuario tienen un bombeo de mensajes y procesan los mensajes recibidos desde el sistema. [CWinApp](../../mfc/reference/cwinapp-class.md) y sus clases derivadas son ejemplos de subprocesos de interfaz de usuario. Pueden que otros subprocesos de interfaz de usuario también se pueden derivar directamente desde `CWinThread`.  
  
 Objetos de clase `CWinThread` normalmente existen para la duración del subproceso. Si desea modificar este comportamiento, establezca [m_bAutoDelete](#m_bautodelete) a **FALSE**.  
  
 La `CWinThread` clase es necesaria para que su código y MFC completamente segura para subprocesos. Datos locales del subproceso utilizados por el marco de trabajo para mantener información específica del subproceso administrados por `CWinThread` objetos. Debido a esta dependencia de `CWinThread` para controlar los datos locales del subproceso, cualquier subproceso que utiliza MFC debe crearse por MFC. Por ejemplo, un subproceso creado por la función de tiempo de ejecución [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) no se utiliza ninguna API de MFC.  
  
 Para crear un subproceso, llame a [AfxBeginThread](application-information-and-management.md#afxbeginthread). Hay dos formas, dependiendo de si desea que un subproceso de trabajo o la interfaz de usuario. Si desea que un subproceso de interfaz de usuario, pasar a `AfxBeginThread` un puntero a la `CRuntimeClass` de su `CWinThread`-clase derivada. Si desea crear un subproceso de trabajo, pase a `AfxBeginThread` un puntero a la función de control y el parámetro a la función de control. Para los subprocesos de trabajo y subprocesos de interfaz de usuario, puede especificar los parámetros opcionales que modifican la prioridad, tamaño de la pila, marcas de creación y atributos de seguridad. `AfxBeginThread`Devuelve un puntero a la nueva `CWinThread` objeto.  
  
 En lugar de llamar `AfxBeginThread`, puede construir un `CWinThread`-derivados de objeto y, después, llame `CreateThread`. Este método de construcción en dos fases es útil si desea reutilizar el `CWinThread` objeto entre sucesiva creación y las terminaciones de ejecuciones de subprocesos.  
  
 Para obtener más información sobre `CWinThread`, consulte los artículos [Multithreading con C++ y MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: crear subprocesos de la interfaz de usuario](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: crear trabajo Subprocesos](../../parallel/multithreading-creating-worker-threads.md), y [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="createthread"></a>CWinThread:: CreateThread  
 Crea un subproceso que se ejecutan dentro del espacio de direcciones del proceso que realiza la llamada.  
  
```  
BOOL CreateThread(
    DWORD dwCreateFlags = 0,  
    UINT nStackSize = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwCreateFlags`  
 Especifica una marca adicional que controla la creación del subproceso. Este indicador puede contener uno de dos valores:  
  
- **CREATE_SUSPENDED** iniciar el subproceso con un recuento de suspensión de uno. Use **CREATE_SUSPENDED** si desea inicializar los datos de miembro de la `CWinThread` objeto, como [m_bAutoDelete](#m_bautodelete) o todos los miembros de la clase derivada, antes de que el subproceso empieza a ejecutarse. Una vez completada la inicialización, utilice la [CWinThread:: ResumeThread](#resumethread) para iniciar el subproceso de ejecución. El subproceso no se ejecutará hasta que `CWinThread::ResumeThread` se llama.  
  
- **0** iniciar el subproceso inmediatamente después de crear.  
  
 `nStackSize`  
 Especifica el tamaño en bytes de la pila para el nuevo subproceso. Si **0**, el tamaño de pila predeterminado es el mismo tamaño que la del subproceso principal del proceso.  
  
 `lpSecurityAttrs`  
 Apunta a un [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica los atributos de seguridad para el subproceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el subproceso se ha creado correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Use `AfxBeginThread` para crear un objeto de subproceso y lo ejecuta en un solo paso. Use `CreateThread` si desea volver a usar el objeto de subproceso entre sucesiva creación y destrucción de las ejecuciones de subprocesos.  
  
##  <a name="cwinthread"></a>CWinThread::CWinThread  
 Construye un objeto `CWinThread`.  
  
```  
CWinThread();
```  
  
### <a name="remarks"></a>Comentarios  
 Para comenzar la ejecución del subproceso, llame a la [CreateThread](#createthread) función miembro. Se suele crear subprocesos mediante una llamada a [AfxBeginThread](application-information-and-management.md#afxbeginthread), que llama a este constructor y `CreateThread`.  
  
##  <a name="exitinstance"></a>CWinThread::ExitInstance  
 Lo llama el marco de dentro de una rara vez reemplazado [ejecutar](#run) función de miembro para salir de esta instancia del subproceso, o si una llamada a [InitInstance](#initinstance) se produce un error.  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Código de salida del subproceso; 0 indica que no hay errores y los valores mayores que 0 indican un error. Este valor se puede recuperar mediante una llamada a [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Comentarios  
 No llame a esta función miembro desde cualquier lugar pero dentro del **ejecutar** función miembro. Esta función miembro solo se usa en los subprocesos de interfaz de usuario.  
  
 La implementación predeterminada de esta función elimina el `CWinThread` objeto si [m_bAutoDelete](#m_bautodelete) es **TRUE**. Reemplace esta función si desea realizar la limpieza adicional cuando finaliza el subproceso. La implementación de `ExitInstance` debe llamar a la versión de la clase base después de ejecuta el código.  
  
##  <a name="getmainwnd"></a>CWinThread::GetMainWnd  
 Si la aplicación es un servidor OLE, llamar a esta función para recuperar un puntero a la ventana principal activa de la aplicación en lugar de hacer referencia directamente a la `m_pMainWnd` miembro del objeto de aplicación.  
  
```  
virtual CWnd* GetMainWnd();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Esta función devuelve un puntero a uno de los dos tipos de windows. Si el subproceso pertenece a un servidor OLE y tiene un objeto que está activo en contexto dentro de un contenedor de active, esta función devuelve el [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) miembro de datos de la `CWinThread` objeto.  
  
 Si no hay ningún objeto que está activo en contexto dentro de un contenedor o la aplicación no es un servidor OLE, esta función devuelve el [m_pMainWnd](#m_pmainwnd) miembro de datos de su objeto de subproceso.  
  
### <a name="remarks"></a>Comentarios  
 Para los subprocesos de interfaz de usuario, esto equivale a hacer referencia directamente a la `m_pActiveWnd` miembro del objeto de aplicación.  
  
 Si la aplicación no es un servidor OLE, llamar a esta función equivale a hacer referencia directamente al miembro `m_pMainWnd` del objeto de aplicación.  
  
 Reemplace esta función para modificar el comportamiento predeterminado.  
  
##  <a name="getthreadpriority"></a>CWinThread::GetThreadPriority  
 Obtiene el nivel de prioridad de subproceso actual de este subproceso.  
  
```  
int GetThreadPriority();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nivel de prioridad de subproceso actual dentro de su clase de prioridad. El valor devuelto será uno de los siguientes, enumerados de prioridad mayor a menor:  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Para obtener más información sobre estas prioridades, vea [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) del SDK de Windows.  
  
##  <a name="initinstance"></a>CWinThread::InitInstance  
 `InitInstance`se debe invalidar para inicializar cada nueva instancia de un subproceso de interfaz de usuario.  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización se realiza correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Por lo general, invalidar `InitInstance` para realizar tareas que deben realizarse cuando se crea un subproceso.  
  
 Esta función miembro solo se usa en los subprocesos de interfaz de usuario. Realizar la inicialización de subprocesos de trabajo en la función controladora pasada a [AfxBeginThread](application-information-and-management.md#afxbeginthread).  
  
##  <a name="isidlemessage"></a>CWinThread::IsIdleMessage  
 Reemplazar esta función para mantener **OnIdle** desde que se llama después de que se generan mensajes específicos.  
  
```  
virtual BOOL IsIdleMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMsg`  
 Señala al mensaje actual que se va a procesar.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si `OnIdle` debe llamarse después del procesamiento de mensaje; de lo contrario devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no llama a **OnIdle** después de mensajes redundantes del mouse y mensajes generados por parpadea símbolos de intercalación.  
  
 Si una aplicación ha creado un temporizador corto, **OnIdle** con frecuencia, se llamará causan problemas de rendimiento. Para mejorar el rendimiento de este tipo de una aplicación, invalidar `IsIdleMessage` en la aplicación `CWinApp`-clase para que busque derivada `WM_TIMER` mensajes como se indica a continuación:  
  
 [!code-cpp[NVC_MFCDocView#189](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]  
  
 Control `WM_TIMER` de este modo mejora el rendimiento de las aplicaciones que utilizan temporizadores cortos.  
  
##  <a name="m_bautodelete"></a>CWinThread::m_bAutoDelete  
 Especifica si el objeto `CWinThread` se debe eliminar automáticamente cuando finalice el subproceso.  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_bAutoDelete` miembro de datos es una variable pública de tipo **BOOL**.  
  
 El valor de `m_bAutoDelete` no afecta a cómo se cerró el identificador de subproceso subyacente. El identificador de subproceso siempre se cierra cuando se destruye el objeto `CWinThread`.  
  
##  <a name="m_hthread"></a>CWinThread::m_hThread  
 Identificador para el subproceso asociado a este `CWinThread`.  
  
```  
HANDLE m_hThread;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_hThread` miembro de datos es una variable pública de tipo `HANDLE`. Solo es válido si subyacente subproceso actualmente no existe.  
  
##  <a name="m_nthreadid"></a>CWinThread::m_nThreadID  
 Identificador del subproceso asociado a este `CWinThread`.  
  
```  
DWORD m_nThreadID;  
```  
  
### <a name="remarks"></a>Comentarios  
 El **m_nThreadID** miembro de datos es una variable pública de tipo `DWORD`. Solo es válido si subyacente subproceso actualmente no existe.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [AfxGetThread](application-information-and-management.md#afxgetthread).  
  
##  <a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd  
 Use este miembro de datos para almacenar un puntero al objeto de la ventana activa de su subproceso.  
  
```  
CWnd* m_pActiveWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 La biblioteca Microsoft Foundation Class automáticamente se cerrará el subproceso cuando la ventana de la que hace referencia a `m_pActiveWnd` se cierra. Si este subproceso es el subproceso principal de una aplicación, también puede finalizar la aplicación. Si este miembro de datos es **NULL**, la ventana activa de la aplicación `CWinApp` se heredarán el objeto. `m_pActiveWnd`es una variable pública de tipo **CWnd\***.  
  
 Normalmente, se establece esta variable miembro al invalidar `InitInstance`. En un subproceso de trabajo, el valor de este miembro de datos se hereda de su subproceso primario.  
  
##  <a name="m_pmainwnd"></a>CWinThread::m_pMainWnd  
 Use este miembro de datos para almacenar un puntero al objeto de ventana principal de su subproceso.  
  
```  
CWnd* m_pMainWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 La biblioteca Microsoft Foundation Class automáticamente se cerrará el subproceso cuando la ventana de la que hace referencia a `m_pMainWnd` se cierra. Si este subproceso es el subproceso principal de una aplicación, también puede finalizar la aplicación. Si este miembro de datos es **NULL**, la ventana principal de la aplicación `CWinApp` objeto se utilizará para determinar cuándo se debe terminar el subproceso. `m_pMainWnd`es una variable pública de tipo **CWnd\***.  
  
 Normalmente, se establece esta variable miembro al invalidar `InitInstance`. En un subproceso de trabajo, el valor de este miembro de datos se hereda de su subproceso primario.  
  
##  <a name="onidle"></a>CWinThread::OnIdle  
 Reemplace esta función miembro para realizar el procesamiento de tiempo de inactividad.  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lCount`  
 Un contador incrementa cada vez que `OnIdle` se llama cuando la cola de mensajes del subproceso está vacía. Este recuento se restablece a 0 cada vez que se procesa un mensaje nuevo. Puede usar el `lCount` parámetro para determinar la cantidad relativa de tiempo que el subproceso ha estado inactivo sin tener que procesar un mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero para recibir más en tiempo de procesamiento de inactividad; 0 si no se necesita nada más tiempo de procesamiento inactivo.  
  
### <a name="remarks"></a>Comentarios  
 `OnIdle`se llama en el bucle de mensajes de forma predeterminada cuando la cola de mensajes del subproceso está vacía. Usar la invalidación para llamar a su propio fondo tareas de controlador de inactividad.  
  
 `OnIdle`debería devolver 0 para indicar que no se requiere ningún tiempo de procesamiento de inactividad adicional. El `lCount` parámetro se incrementa cada vez que `OnIdle` se llama cuando la cola de mensajes está vacía y se restablece a 0 cada vez que se procesa un mensaje nuevo. Puede llamar a sus rutinas de inactividad diferentes en función de este número.  
  
 La implementación predeterminada de esta función miembro libera objetos temporales y las bibliotecas de vínculos dinámicos no utilizado de la memoria.  
  
 Esta función miembro solo se usa en los subprocesos de interfaz de usuario.  
  
 Dado que la aplicación no puede procesar mensajes hasta que `OnIdle` devuelve, no realice las tareas largas en esta función.  
  
##  <a name="operator_handle"></a>CWinThread::operator identificador  
 Recupera el identificador de la `CWinThread` objeto.  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador del objeto de subproceso; en caso contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Use el identificador para llamar directamente a las API de Windows.  
  
##  <a name="postthreadmessage"></a>CWinThread::PostThreadMessage  
 Llamado para publicar un mensaje definido por el usuario a otro `CWinThread` objeto.  
  
```  
BOOL PostThreadMessage(
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parámetros  
 `message`  
 Id. del mensaje definido por el usuario.  
  
 `wParam`  
 Primer parámetro del mensaje.  
  
 `lParam`  
 Segundo parámetro del mensaje.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Mensaje publicado se asigna al controlador de mensajes adecuado mediante la macro de mapa de mensajes `ON_THREAD_MESSAGE`.  
  
> [!NOTE]
>  Al llamar a las ventanas [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946) función dentro de una aplicación MFC, el mensaje MFC no se llama a los controladores. Para obtener más información, vea el artículo de Knowledge Base "PRB: MFC mensaje controlador no llama a PostThreadMessage()" (Q142415).  
  
##  <a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage  
 Anular esta función para filtrar los mensajes de ventana antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMsg`  
 Apunta a un [estructura MSG](../../mfc/reference/msg-structure1.md) que contiene el mensaje para procesar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el mensaje se ha procesado totalmente en `PreTranslateMessage` y no puede procesar aún más. Devuelve cero si se debe procesar el mensaje de la forma habitual.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro solo se usa en los subprocesos de interfaz de usuario.  
  
##  <a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter  
 La función de enlace del marco de trabajo llama a esta función miembro para filtrar y responder a determinados mensajes de Windows.  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `code`  
 Especifica un código de enlace. Esta función miembro utiliza el código para determinar cómo procesar`lpMsg.`  
  
 `lpMsg`  
 Un puntero a una ventana de [estructura MSG](../../mfc/reference/msg-structure1.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se procesa el mensaje; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Una función de enlace procesa los eventos antes de enviarlos al mensaje normal de la aplicación de procesamiento.  
  
 Si invalida esta característica avanzada, asegúrese de llamar a la versión de la clase base para mantener el marco de trabajo de procesamiento de enlace.  
  
##  <a name="processwndprocexception"></a>CWinThread::ProcessWndProcException  
 El marco de trabajo llama a esta función miembro siempre que el controlador no detecta una excepción que se produce en uno de los mensajes de su subproceso o controladores de comandos.  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 *e*  
 Apunta a una excepción no controlada.  
  
 `pMsg`  
 Apunta a un [estructura MSG](../../mfc/reference/msg-structure1.md) que contiene información sobre el mensaje de windows que ha causado el marco de trabajo producir una excepción.  
  
### <a name="return-value"></a>Valor devuelto  
 -1 si una `WM_CREATE` se genera una excepción; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 No llame a esta función miembro directamente.  
  
 La implementación predeterminada de esta función miembro controla sólo las excepciones que genera a partir de los mensajes siguientes:  
  
|Comando|Acción|  
|-------------|------------|  
|`WM_CREATE`|Producirá un error.|  
|`WM_PAINT`|Validar la ventana afectada, lo que evita otra `WM_PAINT` mensaje desde que se está generando.|  
  
 Reemplace esta función miembro para proporcionar un control de excepciones global. Llamar a la funcionalidad básica si desea mostrar el comportamiento predeterminado.  
  
 Esta función miembro solo se usa en subprocesos que tienen una bomba de mensaje.  
  
##  <a name="pumpmessage"></a>CWinThread::PumpMessage  
 Contiene el bucle de mensajes del subproceso.  
  
```  
virtual BOOL PumpMessage();
```  
  
### <a name="remarks"></a>Comentarios  
 `PumpMessage`contiene el bucle de mensajes del subproceso. **PumpMessage** llama a `CWinThread` al bombeo de mensajes del subproceso. Puede llamar a `PumpMessage` directamente forzar que los mensajes para procesarse o puede invalidar `PumpMessage` para cambiar su comportamiento predeterminado.  
  
 Al llamar a `PumpMessage` directamente y reemplazar su comportamiento predeterminado se recomienda sólo para usuarios avanzados.  
  
##  <a name="resumethread"></a>CWinThread:: ResumeThread  
 Se llama para reanudar la ejecución de un subproceso que se suspendió la [SuspendThread](#suspendthread) función miembro o un subproceso creado con el **CREATE_SUSPENDED** marca.  
  
```  
DWORD ResumeThread();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El subproceso de la anterior suspende el recuento si se realiza correctamente; `0xFFFFFFFF` en caso contrario. Si el valor devuelto es cero, no se suspende el subproceso actual. Si el valor devuelto es uno, el subproceso se ha suspendido, pero ahora se reinicia. Cualquier valor devuelto mayor que el subproceso de un medio sigue suspendida.  
  
### <a name="remarks"></a>Comentarios  
 El recuento de suspensión del subproceso actual se reduce en uno. Si se reduce el recuento de suspensión en cero, el subproceso reanuda la ejecución; en caso contrario, el subproceso permanece suspendido.  
  
##  <a name="run"></a>CWinThread:: Run  
 Proporciona un bucle de mensajes de forma predeterminada para los subprocesos de interfaz de usuario.  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `int` valor devuelto por el subproceso. Este valor se puede recuperar mediante una llamada a [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Comentarios  
 **Ejecutar** adquiere y envía los mensajes de Windows hasta que la aplicación recibe un [WM_QUIT](http://msdn.microsoft.com/library/windows/desktop/ms632641) mensaje. Si la cola de mensajes del subproceso no contiene actualmente ningún mensaje, **ejecutar** llamadas `OnIdle` para realizar el procesamiento de tiempo de inactividad. Los mensajes entrantes hacia el [PreTranslateMessage](#pretranslatemessage) función de miembro para un procesamiento especial y, a continuación, la función de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) para la traducción de teclado estándar. Por último, el [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) se llama a la función de Windows.  
  
 **Ejecutar** casi nunca se reemplaza, pero se puede invalidar para implementar un comportamiento especial.  
  
 Esta función miembro solo se usa en los subprocesos de interfaz de usuario.  
  
##  <a name="setthreadpriority"></a>CWinThread::SetThreadPriority  
 Esta función establece el nivel de prioridad del subproceso actual dentro de su clase de prioridad.  
  
```  
BOOL SetThreadPriority(int nPriority);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPriority`  
 Especifica el nuevo nivel de prioridad de subproceso dentro de su clase de prioridad. Este parámetro debe ser uno de los siguientes valores enumerados de prioridad mayor a menor:  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Para obtener más información sobre estas prioridades, vea [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) del SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función fue correcta; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Solo se puede llamar después de [CreateThread](#createthread) devuelve correctamente.  
  
##  <a name="suspendthread"></a>CWinThread:: SuspendThread  
 Incrementa actual subproceso suspende el recuento.  
  
```  
DWORD SuspendThread();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El subproceso de la anterior suspende el recuento si se realiza correctamente; `0xFFFFFFFF` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Si cualquier subproceso tiene un recuento de suspensión por encima de cero, ese subproceso no se ejecuta. El subproceso se puede reanudar llamando a la [ResumeThread](#resumethread) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)
