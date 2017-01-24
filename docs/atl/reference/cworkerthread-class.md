---
title: "CWorkerThread Class | Microsoft Docs"
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
  - "ATL::CWorkerThread<ThreadTraits>"
  - "ATL::CWorkerThread"
  - "ATL.CWorkerThread"
  - "ATL.CWorkerThread<ThreadTraits>"
  - "CWorkerThread"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWorkerThread class"
ms.assetid: be79a832-1345-4a36-a13e-a406cc65286f
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWorkerThread Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase crea un subproceso de trabajo o utiliza existente, espera en uno o más controladores de objeto de kernel, y ejecuta una función especificada del cliente a uno de los identificadores se señala.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class ThreadTraits= DefaultThreadTraits  
>  
class CWorkerThread  
```  
  
#### Parámetros  
 `ThreadTraits`  
 La clase que proporciona a la función de creación de subproceso, como [CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md) o [Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md).  
  
## Members  
  
### estructuras protegidas  
  
|Name|Descripción|  
|----------|-----------------|  
|`WorkerClientEntry`||  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWorkerThread::CWorkerThread](../Topic/CWorkerThread::CWorkerThread.md)|El constructor del subproceso de trabajo.|  
|[CWorkerThread::~CWorkerThread](../Topic/CWorkerThread::~CWorkerThread.md)|El destructor para el subproceso de trabajo.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CWorkerThread::AddHandle](../Topic/CWorkerThread::AddHandle.md)|Llame a este método para agregar el identificador de un objeto espera a la lista mantenida por el subproceso de trabajo.|  
|[CWorkerThread::AddTimer](../Topic/CWorkerThread::AddTimer.md)|Llame a este método para agregar un temporizador espera periódico a la lista mantenida por el subproceso de trabajo.|  
|[CWorkerThread::GetThreadHandle](../Topic/CWorkerThread::GetThreadHandle.md)|Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.|  
|[CWorkerThread::GetThreadId](../Topic/CWorkerThread::GetThreadId.md)|Llame a este método para obtener el identificador de subproceso del subproceso de trabajo.|  
|[CWorkerThread::Initialize](../Topic/CWorkerThread::Initialize.md)|Llame a este método para inicializar el subproceso de trabajo.|  
|[CWorkerThread::RemoveHandle](../Topic/CWorkerThread::RemoveHandle.md)|Llame a este método para quitar un identificador de la lista de objetos espera.|  
|[CWorkerThread::Shutdown](../Topic/CWorkerThread::Shutdown.md)|Llame a este método para cerrar el subproceso de trabajo.|  
  
## Comentarios  
  
### para utilizar CWorkerThread  
  
1.  cree una instancia de esta clase.  
  
2.  Llame a [CWorkerThread:: Inicialice](../Topic/CWorkerThread::Initialize.md).  
  
3.  llamada [CWorkerThread:: AddHandle](../Topic/CWorkerThread::AddHandle.md) con el identificador de un objeto de kernel y un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
     \-O bien\-  
  
     llamada [CWorkerThread:: AddTimer](../Topic/CWorkerThread::AddTimer.md) con un puntero a una implementación de [IWorkerThreadClient](../../atl/reference/iworkerthreadclient-interface.md).  
  
4.  Implemente [IWorkerThreadClient:: Ejecutar](../Topic/IWorkerThreadClient::Execute.md) para realizar alguna acción cuando se señala el identificador o el temporizador.  
  
5.  Para quitar un objeto de la lista de objetos espera, llame a [CWorkerThread:: RemoveHandle](../Topic/CWorkerThread::RemoveHandle.md).  
  
6.  Para finalizar el subproceso, llame a [CWorkerThread:: Apagado](../Topic/CWorkerThread::Shutdown.md).  
  
## Requisitos  
 **encabezado:** atlutil.h  
  
## Vea también  
 [DefaultThreadTraits](../Topic/DefaultThreadTraits.md)   
 [Clases](../../atl/reference/atl-classes.md)   
 [Subprocesamiento múltiple: Crear subprocesos de trabajo](../../parallel/multithreading-creating-worker-threads.md)   
 [IWorkerThreadClient Interface](../../atl/reference/iworkerthreadclient-interface.md)