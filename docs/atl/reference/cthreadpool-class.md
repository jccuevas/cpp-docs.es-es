---
title: "CThreadPool Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CThreadPool"
  - "ATL::CThreadPool"
  - "CThreadPool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CThreadPool class"
ms.assetid: 06683718-01b9-413c-9481-2dc1734ec70f
caps.latest.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CThreadPool Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona un grupo de subprocesos de trabajo que procesen una cola de elementos de trabajo.  
  
## Sintaxis  
  
```  
  
      template <  
   class Worker,  
   class ThreadTraits = DefaultThreadTraits  
>  
class CThreadPool :  
   public IThreadPoolConfig  
```  
  
#### Parámetros  
 *Trabajo*  
 La clase bajo [arquetipo worker](../../atl/reference/worker-archetype.md) que proporciona el código utilizado en los elementos de trabajo de proceso en cola en el grupo de subprocesos.  
  
 `ThreadTraits`  
 La clase que proporciona la función utilizada para crear los subprocesos del grupo.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CThreadPool::CThreadPool](../Topic/CThreadPool::CThreadPool.md)|El constructor del grupo de subprocesos.|  
|[CThreadPool::~CThreadPool](../Topic/CThreadPool::~CThreadPool.md)|El destructor para el grupo de subprocesos.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CThreadPool::AddRef](../Topic/CThreadPool::AddRef.md)|Implementación de `IUnknown::AddRef`.|  
|[CThreadPool::GetNumThreads](../Topic/CThreadPool::GetNumThreads.md)|Llame a este método para obtener el número de subprocesos del grupo.|  
|[CThreadPool::GetQueueHandle](../Topic/CThreadPool::GetQueueHandle.md)|Llame a este método para obtener el identificador del puerto de finalización de E\/S utilizado para poner en cola los elementos de trabajo.|  
|[CThreadPool::GetSize](../Topic/CThreadPool::GetSize.md)|Llame a este método para obtener el número de subprocesos del grupo.|  
|[CThreadPool::GetTimeout](../Topic/CThreadPool::GetTimeout.md)|Llame a este método para obtener el tiempo máximo de milisegundos que el grupo de subprocesos esperará un subproceso para cerrar.|  
|[CThreadPool::Initialize](../Topic/CThreadPool::Initialize.md)|Llame a este método para inicializar el grupo de subprocesos.|  
|[CThreadPool::QueryInterface](../Topic/CThreadPool::QueryInterface.md)|implementación de **IUnknown:: QueryInterface**.|  
|[CThreadPool::QueueRequest](../Topic/CThreadPool::QueueRequest.md)|Llame a este método a la cola un elemento de trabajo que se va a controlar por un subproceso del grupo.|  
|[CThreadPool::Release](../Topic/CThreadPool::Release.md)|Implementación de `IUnknown::Release`.|  
|[CThreadPool::SetSize](../Topic/CThreadPool::SetSize.md)|Llame a este método para establecer el número de subprocesos del grupo.|  
|[CThreadPool::SetTimeout](../Topic/CThreadPool::SetTimeout.md)|Llame a este método para establecer la hora máxima de milisegundos que el grupo de subprocesos esperará un subproceso para cerrar.|  
|[CThreadPool::Shutdown](../Topic/CThreadPool::Shutdown.md)|Llame a este método para cerrar el grupo de subprocesos.|  
  
## Comentarios  
 Los subprocesos del grupo se crean y se destruyen cuando se inicializa, cambia de tamaño, o se cierra el conjunto.  Una instancia del *trabajo* de la clase se creará en la pila de cada subproceso de trabajo del conjunto.  Cada instancia vivirá mientras dure el subproceso.  
  
 Inmediatamente después de la creación de un subproceso, Worker::`Initialize` se invitado el objeto asociado a ese subproceso.  Inmediatamente antes de destrucción de un subproceso, Worker::`Terminate` se denominará.  Ambos métodos deben aceptar un argumento de **void\*** .  El valor de este argumento se pasa al grupo de subprocesos con el parámetro de `pvWorkerParam` de [CThreadPool::Initialize](../Topic/CThreadPool::Initialize.md).  
  
 Cuando hay elementos de trabajo de la cola y los subprocesos de trabajo disponibles para el trabajo, un subproceso de trabajo quitará un elemento de la cola y llama al método de **Execute** de objeto worker para ese subproceso.  Tres elementos se pasan al método: el elemento de la cola, del mismo `pvWorkerParam` pasado a Worker::`Initialize` y a Worker::`Terminate`, y un puntero a la estructura de [SOLAPADO](http://msdn.microsoft.com/library/windows/desktop/ms684342) utilizada para la cola del puerto de finalización de E\/S.  
  
 La clase worker declara el tipo de los elementos que se ponen en cola en el grupo de subprocesos proporcionando un tipo typedef, Worker::`RequestType`.  Este tipo debe ser capaz de lanzamiento a y desde **ULONG\_PTR**.  
  
 Un ejemplo de una clase worker es [CNonStatelessWorker Class](../../atl/reference/cnonstatelessworker-class.md).  
  
## Jerarquía de herencia  
 `IUnknown`  
  
 [IThreadPoolConfig](../../atl/reference/ithreadpoolconfig-interface.md)  
  
 `CThreadPool`  
  
## Requisitos  
 **encabezado:** atlutil.h  
  
## Vea también  
 [IThreadPoolConfig Interface](../../atl/reference/ithreadpoolconfig-interface.md)   
 [DefaultThreadTraits](../Topic/DefaultThreadTraits.md)   
 [Clases](../../atl/reference/atl-classes.md)