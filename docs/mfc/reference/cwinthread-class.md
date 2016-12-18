---
title: "CWinThread Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CWinThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinThread (clase)"
  - "subprocesamiento [MFC], crear subprocesos"
  - "subprocesamiento [MFC], seguridad"
  - "subprocesos de trabajo"
ms.assetid: 10cdc294-4057-4e76-ac7c-a8967a89af0b
caps.latest.revision: 24
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa un subproceso de ejecución dentro de una aplicación.  
  
## Sintaxis  
  
```  
class CWinThread : public CCmdTarget  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinThread::CWinThread](../Topic/CWinThread::CWinThread.md)|Crea un objeto `CWinThread`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinThread::CreateThread](../Topic/CWinThread::CreateThread.md)|Inicia la ejecución de un objeto de `CWinThread` .|  
|[CWinThread::ExitInstance](../Topic/CWinThread::ExitInstance.md)|Reemplace para limpiar cuando el subproceso termina.|  
|[CWinThread::GetMainWnd](../Topic/CWinThread::GetMainWnd.md)|Recupera un puntero a la ventana principal del subproceso.|  
|[CWinThread::GetThreadPriority](../Topic/CWinThread::GetThreadPriority.md)|Obtiene la prioridad del subproceso actual.|  
|[CWinThread::InitInstance](../Topic/CWinThread::InitInstance.md)|Reemplace para realizar la inicialización de la instancia del subproceso.|  
|[CWinThread::IsIdleMessage](../Topic/CWinThread::IsIdleMessage.md)|Comprueba mensajes especiales.|  
|[CWinThread::OnIdle](../Topic/CWinThread::OnIdle.md)|Reemplace para realizar el procesamiento subproceso\- específico de tiempo de inactividad.|  
|[CWinThread::PostThreadMessage](../Topic/CWinThread::PostThreadMessage.md)|Envía un mensaje a otro objeto de `CWinThread` .|  
|[CWinThread::PreTranslateMessage](../Topic/CWinThread::PreTranslateMessage.md)|Mensajes de filtros antes de que se envíen a las funciones de Windows [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) y [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934).|  
|[CWinThread::ProcessMessageFilter](../Topic/CWinThread::ProcessMessageFilter.md)|Algunos mensajes de las intersecciones antes de que llegan a la aplicación.|  
|[CWinThread::ProcessWndProcException](../Topic/CWinThread::ProcessWndProcException.md)|Intercepta todas las excepciones no controladas producidas por los controladores de mensajes y del subproceso.|  
|[CWinThread::PumpMessage](../Topic/CWinThread::PumpMessage.md)|Contiene el bucle de mensajes del subproceso.|  
|[CWinThread::ResumeThread](../Topic/CWinThread::ResumeThread.md)|Disminuye el recuento de suspensión de un subproceso.|  
|[CWinThread::Run](../Topic/CWinThread::Run.md)|Supervisar la función para subprocesos con un mensaje bombee.  Reemplace para personalizar el bucle de mensajes predeterminado.|  
|[CWinThread::SetThreadPriority](../Topic/CWinThread::SetThreadPriority.md)|Establece la prioridad del subproceso actual.|  
|[CWinThread::SuspendThread](../Topic/CWinThread::SuspendThread.md)|Incrementa el recuento de suspensión de un subproceso.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinThread::operator HANDLE](../Topic/CWinThread::operator%20HANDLE.md)|Recupera el identificador de objeto de `CWinThread` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWinThread::m\_bAutoDelete](../Topic/CWinThread::m_bAutoDelete.md)|Especifica si destruir el objeto en la finalización del subproceso.|  
|[CWinThread::m\_hThread](../Topic/CWinThread::m_hThread.md)|Identificador del subproceso actual.|  
|[CWinThread::m\_nThreadID](../Topic/CWinThread::m_nThreadID.md)|Id. del subproceso actual.|  
|[CWinThread::m\_pActiveWnd](../Topic/CWinThread::m_pActiveWnd.md)|Puntero a la ventana principal de la aplicación contenedora cuando un servidor OLE está activo en contexto.|  
|[CWinThread::m\_pMainWnd](../Topic/CWinThread::m_pMainWnd.md)|Contiene un puntero a la ventana principal de la aplicación.|  
  
## Comentarios  
 El subproceso de ejecución principal es proporcionado normalmente mediante un objeto derivado de `CWinApp`; `CWinApp` se deriva de `CWinThread`.  Objetos adicionales de `CWinThread` permiten varios subprocesos dentro de una aplicación determinada.  
  
 Hay dos tipos generales de subprocesos que `CWinThread` admite: subprocesos de trabajo y de interfaz de usuario.  Los subprocesos de trabajo no tienen ninguna suministro de mensajes: por ejemplo, un subproceso que realiza cálculos en segundo plano en una aplicación de hoja de cálculo.  Los subprocesos de interfaz de usuario tienen mensajes de mensaje de suministro y procesar del sistema.  [CWinApp](../../mfc/reference/cwinapp-class.md) y clases derivados de son ejemplos de subprocesos de interfaz de usuario.  Otros subprocesos de interfaz de usuario también se pueden derivar directamente de `CWinThread`.  
  
 Los objetos de la clase `CWinThread` existen normalmente para la duración del subproceso.  Si desea modificar este comportamiento, establezca [m\_bAutoDelete](../Topic/CWinThread::m_bAutoDelete.md) a **FALSE**.  
  
 La clase de `CWinThread` es necesaria para que la codificación y MFC segura para subprocesos.  Los datos de Subproceso\- local utiliza el marco para mantener la información subproceso\- concreta es administrado por los objetos de `CWinThread` .  Debido a esta dependencia en `CWinThread` para administrar datos de subproceso\- local, cualquier subproceso que utiliza MFC se debe crear por MFC.  Por ejemplo, un subproceso creado por la función [\_beginthread, \_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md) en tiempo de ejecución no puede usar ningún MFC API.  
  
 Para crear un subproceso, llame a [AfxBeginThread](../Topic/AfxBeginThread.md).  Hay dos formas, dependiendo de si desea un trabajo o un subproceso de interfaz de usuario.  Si desea que un subproceso de interfaz de usuario, pase a `AfxBeginThread` un puntero a `CRuntimeClass` del `CWinThread`\- clase derivada.  Si desea crear un subproceso de trabajo, pase a `AfxBeginThread` un puntero a la función controladora y el parámetro a la función controladora.  Para ambos subprocesos de trabajo y de interfaz de usuario, puede especificar parámetros opcionales que modifican prioridad, tamaño de la pila, los marcadores de la creación, y los atributos de seguridad.  `AfxBeginThread` devolverá un puntero al nuevo objeto de `CWinThread` .  
  
 En lugar de llamar a `AfxBeginThread`, puede construir `CWinThread`\- objeto derivado y llamar después a `CreateThread`.  Este método de dos fases de la construcción es útil si desea reutilizar el objeto de `CWinThread` entre la creación y las finalizaciones sucesivas de las ejecuciones de subproceso.  
  
 Para obtener más información sobre `CWinThread`, vea los artículos [Multithreading con C\+\+ y MFC](../../parallel/multithreading-with-cpp-and-mfc.md), [Multithreading: Crear subprocesos de interfaz de usuario](../../parallel/multithreading-creating-user-interface-threads.md), [Multithreading: Crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md), y [Multithreading: Cómo utilizar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `CWinThread`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWinApp Class](../../mfc/reference/cwinapp-class.md)   
 [CCmdTarget Class](../../mfc/reference/ccmdtarget-class.md)