---
title: CWinThread (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinThread
dev_langs:
- C++
helpviewer_keywords:
- worker threads
- threading [MFC], safety
- CWinThread class
- threading [MFC], creating threads
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 866e847f9c1d73d6f9882e50b1274fbad9e21a39
ms.lasthandoff: 02/24/2017

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
|[CWinThread:: CreateThread](#createthread)|Inicia la ejecución de un `CWinThread` objeto.|  
|[CWinThread::ExitInstance](#exitinstance)|Invalidación para limpiar cuando finaliza el subproceso.|  
|[CWinThread::GetMainWnd](#getmainwnd)|Recupera un puntero a la ventana principal del subproceso.|  
|[CWinThread::GetThreadPriority](#getthreadpriority)|Obtiene la prioridad del subproceso actual.|  
|[CWinThread::InitInstance](#initinstance)|Invalidación para realizar la inicialización de la instancia de subproceso.|  
|[CWinThread::IsIdleMessage](#isidlemessage)|Comprueba si hay mensajes especiales.|  
|[CWinThread::OnIdle](#onidle)|Invalidación para realizar el procesamiento de tiempo de inactividad específicos del subproceso.|  
|[CWinThread::PostThreadMessage](#postthreadmessage)|Envía un mensaje a otro `CWinThread` objeto.|  
|[CWinThread::PreTranslateMessage](#pretranslatemessage)|Filtra los mensajes antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CWinThread::ProcessMessageFilter](#processmessagefilter)|Intercepta determinados mensajes antes de que lleguen a la aplicación.|  
|[CWinThread::ProcessWndProcException](#processwndprocexception)|Intercepta todas las excepciones no controladas producidas por el mensaje del subproceso y controladores de comandos.|  
|[CWinThread::PumpMessage](#pumpmessage)|Contiene el bucle de mensajes del subproceso.|  
|[CWinThread:: ResumeThread](#resumethread)|Recuento de suspensiones disminuye una del subproceso.|  
|[CWinThread:: Run](#run)|Función controladora para subprocesos con un bombeo de mensajes. Invalidar para personalizar el bucle de mensajes predeterminado.|  
|[CWinThread::SetThreadPriority](#setthreadpriority)|Establece la prioridad del subproceso actual.|  
|[CWinThread:: SuspendThread](#suspendthread)|Incrementos de un del subproceso recuento de suspensión.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[IDENTIFICADOR de CWinThread::operator](#operator_handle)|Recupera el identificador de la `CWinThread` objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWinThread::m_bAutoDelete](#m_bautodelete)|Especifica si se destruye el objeto en la finalización del subproceso.|  
|[CWinThread::m_hThread](#m_hthread)|Identificador del subproceso actual.|  
|[CWinThread::m_nThreadID](#m_nthreadid)|Id. del subproceso actual.|  
|[CWinThread::m_pActiveWnd](#m_pactivewnd)|Puntero a la ventana principal de la aplicación cuando un servidor OLE está activo en contexto.|  
|[CWinThread::m_pMainWnd](#m_pmainwnd)|Contiene un puntero a la ventana principal de la aplicación.|  
  
## <a name="remarks"></a>Comentarios  
 El subproceso de ejecución principal suele proporcionar un objeto derivado de `CWinApp`; `CWinApp` se deriva de `CWinThread`. Adicionales `CWinThread` objetos permiten que varios subprocesos de una aplicación dada.  
  
 Hay dos tipos generales de subprocesos que `CWinThread` admite: subprocesos de trabajo y subprocesos de interfaz de usuario. Subprocesos de trabajo no tienen suministro de mensajes: por ejemplo, un subproceso que realiza cálculos de segundo plano en una aplicación de hoja de cálculo. Subprocesos de interfaz de usuario tienen un bombeo de mensajes y procesan los mensajes recibidos desde el sistema. [CWinApp](../../mfc/reference/cwinapp-class.md) y sus clases derivadas son ejemplos de subprocesos de interfaz de usuario. Otros subprocesos de interfaz de usuario también se pueden derivar directamente de `CWinThread`.  
  
 Objetos de clase `CWinThread` normalmente existen para la duración del subproceso. Si desea modificar este comportamiento, establezca [m_bAutoDelete](#m_bautodelete) a **FALSE**.  
  
 La `CWinThread` clase es necesaria para que su código y MFC completamente segura para subprocesos. Datos locales de subprocesos utilizados por el marco de trabajo para mantener la información específica del subproceso administrados por `CWinThread` objetos. Debido a esta dependencia de `CWinThread` para controlar los datos locales del subproceso, debe crearse cualquier subproceso que utiliza MFC por MFC. Por ejemplo, un subproceso creado por la función de tiempo de ejecución [_beginthread, _beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) no se utiliza ninguna API de MFC.  
  
 Para crear un subproceso, llame a [AfxBeginThread](application-information-and-management.md#afxbeginthread). Hay dos formas, dependiendo de si desea que un subproceso de trabajo o la interfaz de usuario. Si desea que un subproceso de interfaz de usuario, pasar a `AfxBeginThread` un puntero a la `CRuntimeClass` de su `CWinThread`-clase derivada. Si desea crear un subproceso de trabajo, pasar a `AfxBeginThread` un puntero a la función controladora y el parámetro para la función controladora. Para los subprocesos de trabajo y subprocesos de interfaz de usuario, puede especificar parámetros opcionales que modifican la prioridad, el tamaño de pila, marcas de creación y atributos de seguridad. `AfxBeginThread`Devuelve un puntero a la nueva `CWinThread` objeto.  
  
 En lugar de llamar `AfxBeginThread`, puede construir un `CWinThread`-derivados de objeto y después llamar a `CreateThread`. Este método de construcción en dos fases es útil si desea reutilizar el `CWinThread` objeto entre sucesiva creación y terminaciones de ejecuciones de subprocesos.  
  
 Para obtener más información sobre `CWinThread`, consulte los artículos [Multithreading con C++ y MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: crear subprocesos de interfaz de usuario](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md), y [subprocesamiento múltiple: cómo usar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namecreatethreada--cwinthreadcreatethread"></a><a name="createthread"></a>CWinThread:: CreateThread  
 Crea un subproceso que se ejecutan en el espacio de direcciones del proceso de llamada.  
  
```  
BOOL CreateThread(
    DWORD dwCreateFlags = 0,  
    UINT nStackSize = 0,  
    LPSECURITY_ATTRIBUTES lpSecurityAttrs = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwCreateFlags`  
 Especifica un indicador adicional que controla la creación del subproceso. Este indicador puede contener uno de dos valores:  
  
- **CREATE_SUSPENDED** iniciar el subproceso con un recuento de suspensión de uno. Utilice **CREATE_SUSPENDED** si desea inicializar los datos de miembro de la `CWinThread` objeto, como [m_bAutoDelete](#m_bautodelete) o todos los miembros de la clase derivada, antes de que el subproceso empieza a ejecutarse. Una vez completada la inicialización, utilice la [CWinThread:: ResumeThread](#resumethread) para iniciar el subproceso de ejecución. El subproceso no se ejecutará hasta que `CWinThread::ResumeThread` se llama.  
  
- **0** iniciar el subproceso inmediatamente después de crear.  
  
 `nStackSize`  
 Especifica el tamaño en bytes de la pila para el nuevo subproceso. Si **0**, el tamaño de pila predeterminado es el mismo tamaño que el subproceso del proceso principal.  
  
 `lpSecurityAttrs`  
 Apunta a un [SECURITY_ATTRIBUTES](http://msdn.microsoft.com/library/windows/desktop/aa379560) estructura que especifica los atributos de seguridad para el subproceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el subproceso se ha creado correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Use `AfxBeginThread` para crear un objeto de subproceso y lo ejecuta en un solo paso. Use `CreateThread` si desea reutilizar el objeto de subproceso entre sucesiva creación y destrucción de las ejecuciones de subprocesos.  
  
##  <a name="a-namecwinthreada--cwinthreadcwinthread"></a><a name="cwinthread"></a>CWinThread::CWinThread  
 Construye un objeto `CWinThread`.  
  
```  
CWinThread();
```  
  
### <a name="remarks"></a>Comentarios  
 Para comenzar la ejecución del subproceso, llame a la [CreateThread](#createthread) función miembro. Se suele crear subprocesos llamando a [AfxBeginThread](http://msdn.microsoft.com/library/e9e8684d-24f7-4599-8fdf-1f4f560a753b), que llama a este constructor y `CreateThread`.  
  
##  <a name="a-nameexitinstancea--cwinthreadexitinstance"></a><a name="exitinstance"></a>CWinThread::ExitInstance  
 Llamado por el marco desde dentro de una rara vez reemplazado [ejecutar](#run) función miembro para salir de esta instancia del subproceso, o si una llamada a [InitInstance](#initinstance) se produce un error.  
  
```  
virtual int ExitInstance();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Código de salida del subproceso; 0 indica que no hay errores y los valores mayores que 0 indican un error. Este valor se puede recuperar mediante una llamada a [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Comentarios  
 No llame a esta función miembro desde cualquier lugar pero dentro del **ejecutar** función miembro. Esta función miembro sólo se utiliza en los subprocesos de interfaz de usuario.  
  
 La implementación predeterminada de esta función elimina el `CWinThread` objeto si [m_bAutoDelete](#m_bautodelete) es **TRUE**. Reemplace esta función si desea realizar la limpieza adicional cuando el subproceso termina. La implementación de `ExitInstance` debe llamar a la versión de la clase base después de ejecuta el código.  
  
##  <a name="a-namegetmainwnda--cwinthreadgetmainwnd"></a><a name="getmainwnd"></a>CWinThread::GetMainWnd  
 Si su aplicación es un servidor OLE, llame a esta función para recuperar un puntero a la ventana principal activa de la aplicación en lugar de hacer referencia directamente a la `m_pMainWnd` miembro del objeto de aplicación.  
  
```  
virtual CWnd* GetMainWnd();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Esta función devuelve un puntero a uno de los dos tipos de ventanas. Si el subproceso de forma parte de un servidor OLE y tiene un objeto que está activo en contexto dentro de un contenedor de active, esta función devuelve el [CWinApp::m_pActiveWnd](../../mfc/reference/cwinapp-class.md#m_pactivewnd) miembro de datos de la `CWinThread` objeto.  
  
 Si no hay ningún objeto activo en contexto dentro de un contenedor o la aplicación no es un servidor OLE, esta función devuelve el [m_pMainWnd](#m_pmainwnd) miembro de datos de su objeto de subproceso.  
  
### <a name="remarks"></a>Comentarios  
 Para los subprocesos de interfaz de usuario, esto es equivalente a hacer referencia directamente a la `m_pActiveWnd` miembro del objeto de aplicación.  
  
 Si la aplicación no es un servidor OLE, llamar a esta función equivale a hacer referencia directamente al miembro `m_pMainWnd` del objeto de aplicación.  
  
 Reemplazar esta función para modificar el comportamiento predeterminado.  
  
##  <a name="a-namegetthreadprioritya--cwinthreadgetthreadpriority"></a><a name="getthreadpriority"></a>CWinThread::GetThreadPriority  
 Obtiene el nivel de prioridad del subproceso actual de este subproceso.  
  
```  
int GetThreadPriority();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El nivel de prioridad de subproceso actual dentro de su clase de prioridad. El valor devuelto será uno de los siguientes aparecen de prioridad mayor a menor:  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Para obtener más información sobre estas prioridades, consulte [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-nameinitinstancea--cwinthreadinitinstance"></a><a name="initinstance"></a>CWinThread::InitInstance  
 `InitInstance`se debe invalidar para inicializar cada nueva instancia de un subproceso de interfaz de usuario.  
  
```  
virtual BOOL InitInstance();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización es correcta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, reemplazar `InitInstance` para realizar tareas que deben realizarse cuando se crea un subproceso.  
  
 Esta función miembro sólo se utiliza en los subprocesos de interfaz de usuario. Realizar la inicialización de subprocesos de trabajo en la función controladora pasada a [AfxBeginThread](application-information-and-management.md#afxbeginthread).  
  
##  <a name="a-nameisidlemessagea--cwinthreadisidlemessage"></a><a name="isidlemessage"></a>CWinThread::IsIdleMessage  
 Reemplazar esta función para mantener **OnIdle** desde que se llama después de generan mensajes específicos.  
  
```  
virtual BOOL IsIdleMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMsg`  
 Señala al mensaje actual que se está procesando.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si `OnIdle` debe llamarse después del procesamiento de mensajes; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no llama a **OnIdle** después de mensajes del mouse redundantes y mensajes generados por parpadea símbolos de intercalación.  
  
 Si una aplicación ha creado un temporizador corto, **OnIdle** se llama con frecuencia, causando problemas de rendimiento. Para mejorar el rendimiento de este tipo de una aplicación, invalide `IsIdleMessage` en la aplicación `CWinApp`-derivado de la clase para buscar `WM_TIMER` mensajes como sigue:  
  
 [!code-cpp[NVC_MFCDocView&#189;](../../mfc/codesnippet/cpp/cwinthread-class_1.cpp)]  
  
 Control `WM_TIMER` de esta forma mejora el rendimiento de las aplicaciones que utilizan temporizadores corto.  
  
##  <a name="a-namembautodeletea--cwinthreadmbautodelete"></a><a name="m_bautodelete"></a>CWinThread::m_bAutoDelete  
 Especifica si el objeto `CWinThread` se debe eliminar automáticamente cuando finalice el subproceso.  
  
```  
BOOL m_bAutoDelete;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_bAutoDelete` miembro de datos es una variable pública de tipo **BOOL**.  
  
 El valor de `m_bAutoDelete` no afecta a cómo se cerró el identificador de subproceso subyacente. El identificador de subproceso siempre se cierra cuando se destruye el objeto `CWinThread`.  
  
##  <a name="a-namemhthreada--cwinthreadmhthread"></a><a name="m_hthread"></a>CWinThread::m_hThread  
 Identificador para el subproceso que se adjuntará a este `CWinThread`.  
  
```  
HANDLE m_hThread;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `m_hThread` miembro de datos es una variable pública de tipo `HANDLE`. Sólo es válido si subyacente subproceso actualmente no existe.  
  
##  <a name="a-namemnthreadida--cwinthreadmnthreadid"></a><a name="m_nthreadid"></a>CWinThread::m_nThreadID  
 Identificador del subproceso que se adjuntará a este `CWinThread`.  
  
```  
DWORD m_nThreadID;  
```  
  
### <a name="remarks"></a>Comentarios  
 El **m_nThreadID** miembro de datos es una variable pública de tipo `DWORD`. Sólo es válido si subyacente subproceso actualmente no existe.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [AfxGetThread](application-information-and-management.md#afxgetthread).  
  
##  <a name="a-namempactivewnda--cwinthreadmpactivewnd"></a><a name="m_pactivewnd"></a>CWinThread::m_pActiveWnd  
 Este miembro de datos se utiliza para almacenar un puntero al objeto de la ventana activa de su subproceso.  
  
```  
CWnd* m_pActiveWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 La biblioteca Microsoft Foundation Class finalizará automáticamente su subproceso cuando la ventana que hace referencia `m_pActiveWnd` está cerrado. Si este subproceso es el subproceso principal de una aplicación, la aplicación también se cerrará. Si este miembro de datos es **NULL**, la ventana activa de la aplicación `CWinApp` se heredará el objeto. `m_pActiveWnd`es una variable pública de tipo **CWnd\***.  
  
 Normalmente, se establece esta variable miembro al reemplazar `InitInstance`. En un subproceso de trabajo, el valor de este miembro de datos se hereda del subproceso primario.  
  
##  <a name="a-namempmainwnda--cwinthreadmpmainwnd"></a><a name="m_pmainwnd"></a>CWinThread::m_pMainWnd  
 Este miembro de datos se utiliza para almacenar un puntero al objeto de ventana principal de su subproceso.  
  
```  
CWnd* m_pMainWnd;  
```  
  
### <a name="remarks"></a>Comentarios  
 La biblioteca Microsoft Foundation Class finalizará automáticamente su subproceso cuando la ventana que hace referencia `m_pMainWnd` está cerrado. Si este subproceso es el subproceso principal de una aplicación, la aplicación también se cerrará. Si este miembro de datos es **NULL**, la ventana principal de la aplicación `CWinApp` objeto se utilizará para determinar cuándo debe terminar el subproceso. `m_pMainWnd`es una variable pública de tipo **CWnd\***.  
  
 Normalmente, se establece esta variable miembro al reemplazar `InitInstance`. En un subproceso de trabajo, el valor de este miembro de datos se hereda del subproceso primario.  
  
##  <a name="a-nameonidlea--cwinthreadonidle"></a><a name="onidle"></a>CWinThread::OnIdle  
 Reemplace esta función miembro para realizar el procesamiento de tiempo de inactividad.  
  
```  
virtual BOOL OnIdle(LONG lCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lCount`  
 Incrementa un contador cada vez que `OnIdle` se llama cuando la cola de mensajes del subproceso está vacía. Este contador se restablece a 0 cada vez que se procesa un mensaje nuevo. Puede usar el `lCount` parámetro para determinar la longitud de tiempo que el subproceso ha estado inactivo sin procesar un mensaje relativa.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero para recibir más en tiempo de procesamiento inactivo; 0 si no hay más tiempo de procesamiento inactivo es necesaria.  
  
### <a name="remarks"></a>Comentarios  
 `OnIdle`se llama en el bucle de mensajes de forma predeterminada cuando la cola de mensajes del subproceso está vacía. Use la invalidación para llamar a su propio fondo de las tareas de controlador de inactividad.  
  
 `OnIdle`debería devolver 0 para indicar que no se requiere ningún tiempo de procesamiento adicional inactivo. El `lCount` parámetro se incrementa cada vez que `OnIdle` se llama cuando la cola de mensajes está vacía y se restablece a 0 cada vez que se procesa un mensaje nuevo. Puede llamar a las rutinas de inactividad diferentes basándose en este recuento.  
  
 La implementación predeterminada de esta función miembro libera objetos temporales y bibliotecas de vínculos dinámicos no utilizados de la memoria.  
  
 Esta función miembro sólo se utiliza en los subprocesos de interfaz de usuario.  
  
 Dado que la aplicación no puede procesar mensajes hasta que `OnIdle` devuelve, realizar las tareas largas en esta función.  
  
##  <a name="a-nameoperatorhandlea--cwinthreadoperator-handle"></a><a name="operator_handle"></a>IDENTIFICADOR de CWinThread::operator  
 Recupera el identificador de la `CWinThread` objeto.  
  
```  
operator HANDLE() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, el identificador del objeto de subproceso; de lo contrario, **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 Utilice el controlador para llamar directamente a las API de Windows.  
  
##  <a name="a-namepostthreadmessagea--cwinthreadpostthreadmessage"></a><a name="postthreadmessage"></a>CWinThread::PostThreadMessage  
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
 El mensaje expuesto se asigna al controlador de mensajes apropiado mediante la macro de mapa de mensajes `ON_THREAD_MESSAGE`.  
  
> [!NOTE]
>  Cuando se llama a Windows [PostThreadMessage](http://msdn.microsoft.com/library/windows/desktop/ms644946) función dentro de una aplicación MFC, el mensaje MFC no se llama a los controladores. Para obtener más información, consulte el artículo de Knowledge Base "PRB: MFC mensaje controlador no llama a PostThreadMessage()" (Q142415).  
  
##  <a name="a-namepretranslatemessagea--cwinthreadpretranslatemessage"></a><a name="pretranslatemessage"></a>CWinThread::PreTranslateMessage  
 Reemplazar esta función para filtrar los mensajes de ventana antes de enviarlos a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMsg`  
 Apunta a un [estructura MSG](../../mfc/reference/msg-structure1.md) que contiene el mensaje para procesar.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el mensaje se ha procesado totalmente en `PreTranslateMessage` y no se debe procesar más. Cero si se debe procesar el mensaje de la manera normal.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro sólo se utiliza en los subprocesos de interfaz de usuario.  
  
##  <a name="a-nameprocessmessagefiltera--cwinthreadprocessmessagefilter"></a><a name="processmessagefilter"></a>CWinThread::ProcessMessageFilter  
 Función de enlace del marco de trabajo llama a esta función miembro para filtrar y responder a algunos mensajes de Windows.  
  
```  
virtual BOOL ProcessMessageFilter(
    int code,  
    LPMSG lpMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 `code`  
 Especifica un código de enlace. Esta función miembro utiliza el código para determinar cómo procesar`lpMsg.`  
  
 `lpMsg`  
 Un puntero a un Windows [estructura MSG](../../mfc/reference/msg-structure1.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se procesa el mensaje; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Una función de enlace procesa los eventos antes de enviarlos al mensaje normal de la aplicación de procesamiento.  
  
 Si reemplaza esta función avanzada, asegúrese de llamar a la versión de la clase base para mantener el marco de trabajo de procesamiento de enlace.  
  
##  <a name="a-nameprocesswndprocexceptiona--cwinthreadprocesswndprocexception"></a><a name="processwndprocexception"></a>CWinThread::ProcessWndProcException  
 El marco de trabajo llama a esta función miembro cada vez que el controlador no detecta una excepción en uno de los mensajes de su subproceso o controladores de comandos.  
  
```  
virtual LRESULT ProcessWndProcException(
    CException* e,  
    const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parámetros  
 *e*  
 Apunta a una excepción no controlada.  
  
 `pMsg`  
 Apunta a un [estructura MSG](../../mfc/reference/msg-structure1.md) que contiene información sobre el mensaje de windows que provocó el marco de trabajo producir una excepción.  
  
### <a name="return-value"></a>Valor devuelto  
 – 1 si una `WM_CREATE` se genera una excepción; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 No llame a esta función miembro directamente.  
  
 La implementación predeterminada de esta función miembro controla sólo las excepciones que genera a partir de los siguientes mensajes:  
  
|Comando|Acción|  
|-------------|------------|  
|`WM_CREATE`|Producirá un error.|  
|`WM_PAINT`|Validar la ventana afectada, lo que evita otra `WM_PAINT` mensaje se generan.|  
  
 Reemplace esta función miembro para proporcionar un control de excepciones global. Llamar a la funcionalidad básica si desea mostrar el comportamiento predeterminado.  
  
 Esta función miembro se utiliza únicamente en los subprocesos que tienen un bombeo de mensajes.  
  
##  <a name="a-namepumpmessagea--cwinthreadpumpmessage"></a><a name="pumpmessage"></a>CWinThread::PumpMessage  
 Contiene el bucle de mensajes del subproceso.  
  
```  
virtual BOOL PumpMessage();
```  
  
### <a name="remarks"></a>Comentarios  
 `PumpMessage`contiene el bucle de mensajes del subproceso. **PumpMessage** llama a `CWinThread` al bombeo de mensajes del subproceso. Puede llamar a `PumpMessage` directamente para forzar mensajes para procesarse, o puede reemplazar `PumpMessage` para cambiar su comportamiento predeterminado.  
  
 Llamar a `PumpMessage` directamente y reemplazar el comportamiento predeterminado se recomienda sólo para usuarios avanzados.  
  
##  <a name="a-nameresumethreada--cwinthreadresumethread"></a><a name="resumethread"></a>CWinThread:: ResumeThread  
 Se llama para reanudar la ejecución de un subproceso que se suspendió la [SuspendThread](#suspendthread) función miembro o un subproceso creado con el **CREATE_SUSPENDED** marca.  
  
```  
DWORD ResumeThread();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El subproceso de la anterior Suspender recuento si es correcto; `0xFFFFFFFF` en caso contrario. Si el valor devuelto es cero, no se suspende el subproceso actual. Si el valor devuelto es uno, el subproceso se ha suspendido, pero ahora se reinicia. Cualquier valor devuelto mayor que uno significa que el subproceso permanece suspendida.  
  
### <a name="remarks"></a>Comentarios  
 El recuento de suspensión del subproceso actual se reduce en uno. Si el recuento de suspensión se reduce a cero, el subproceso reanuda la ejecución; de lo contrario, el subproceso permanece suspendido.  
  
##  <a name="a-nameruna--cwinthreadrun"></a><a name="run"></a>CWinThread:: Run  
 Proporciona un bucle de mensajes de forma predeterminada para los subprocesos de interfaz de usuario.  
  
```  
virtual int Run();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un `int` valor devuelto por el subproceso. Este valor se puede recuperar mediante una llamada a [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190).  
  
### <a name="remarks"></a>Comentarios  
 **Ejecutar** adquiere y envía los mensajes de Windows hasta que la aplicación recibe un [WM_QUIT](http://msdn.microsoft.com/library/windows/desktop/ms632641) mensaje. Si la cola de mensajes del subproceso contiene actualmente no hay mensajes, **ejecutar** llamadas `OnIdle` para realizar el procesamiento de tiempo de inactividad. Los mensajes entrantes que se van a la [PreTranslateMessage](#pretranslatemessage) función de miembro para un procesamiento especial y, a continuación, la función de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) para la traducción de teclado estándar. Por último, el [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) se llama la función de Windows.  
  
 **Ejecutar** casi nunca se reemplaza, pero se puede reemplazar para implementar un comportamiento especial.  
  
 Esta función miembro sólo se utiliza en los subprocesos de interfaz de usuario.  
  
##  <a name="a-namesetthreadprioritya--cwinthreadsetthreadpriority"></a><a name="setthreadpriority"></a>CWinThread::SetThreadPriority  
 Esta función establece el nivel de prioridad del subproceso actual en su clase de prioridad.  
  
```  
BOOL SetThreadPriority(int nPriority);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPriority`  
 Especifica el nuevo nivel de prioridad de subproceso dentro de su clase de prioridad. Este parámetro debe ser uno de los siguientes valores, enumerados de prioridad mayor a menor:  
  
- **THREAD_PRIORITY_TIME_CRITICAL**  
  
- **THREAD_PRIORITY_HIGHEST**  
  
- **THREAD_PRIORITY_ABOVE_NORMAL**  
  
- **THREAD_PRIORITY_NORMAL**  
  
- **THREAD_PRIORITY_BELOW_NORMAL**  
  
- **THREAD_PRIORITY_LOWEST**  
  
- **THREAD_PRIORITY_IDLE**  
  
 Para obtener más información sobre estas prioridades, consulte [SetThreadPriority](http://msdn.microsoft.com/library/windows/desktop/ms686277) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la función fue correcta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Sólo se puede llamar después de [CreateThread](#createthread) devuelve correctamente.  
  
##  <a name="a-namesuspendthreada--cwinthreadsuspendthread"></a><a name="suspendthread"></a>CWinThread:: SuspendThread  
 Incrementa el actual subproceso suspende el recuento.  
  
```  
DWORD SuspendThread();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El subproceso de la anterior Suspender recuento si es correcto; `0xFFFFFFFF` en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
 Si cualquier subproceso tiene un recuento de suspensión por encima de cero, ese subproceso no se ejecuta. El subproceso se puede reanudar llamando a la [ResumeThread](#resumethread) función miembro.  
  
## <a name="see-also"></a>Vea también  
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWinApp (clase)](../../mfc/reference/cwinapp-class.md)   
 [CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)

