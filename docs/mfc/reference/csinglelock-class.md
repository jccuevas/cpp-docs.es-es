---
title: "CSingleLock Class | Microsoft Docs"
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
  - "CSingleLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSingleLock class"
  - "synchronization objects, control de acceso"
  - "subprocesamiento [MFC], control de acceso"
  - "subprocesamiento [MFC], sincronización"
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSingleLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa el mecanismo de control de acceso utilizado para controlar el acceso a un recurso en un programa de multithreading.  
  
## Sintaxis  
  
```  
  
class CSingleLock  
  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSingleLock::CSingleLock](../Topic/CSingleLock::CSingleLock.md)|Crea un objeto `CSingleLock`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSingleLock::IsLocked](../Topic/CSingleLock::IsLocked.md)|determina si el objeto está bloqueado.|  
|[CSingleLock::Lock](../Topic/CSingleLock::Lock.md)|espera en un objeto de sincronización.|  
|[CSingleLock::Unlock](../Topic/CSingleLock::Unlock.md)|Libere un objeto de sincronización.|  
  
## Comentarios  
 `CSingleLock` no tiene una clase base.  
  
 Para utilizar las clases [CSemaphore](../../mfc/reference/csemaphore-class.md)de sincronización, [CMutex](../../mfc/reference/cmutex-class.md), [CCriticalSection](../../mfc/reference/ccriticalsection-class.md), y [CEvent](../../mfc/reference/cevent-class.md), debe crear `CSingleLock` o el objeto de [CMultiLock](../../mfc/reference/cmultilock-class.md) a la espera en y liberar el objeto de sincronización.  Utilice `CSingleLock` si solo necesita esperar en un objeto cada vez.  Utilice **CMultiLock** cuando hay varios objetos que puede usar en un momento determinado.  
  
 Para utilizar un objeto de `CSingleLock` , llama a su constructor dentro de una función miembro en la clase de recurso controlado.  Llamar a continuación a la función miembro de [IsLocked](../Topic/CSingleLock::IsLocked.md) para determinar si el recurso está disponible.  Si es así, continúe con el resto de la función miembro.  Si el recurso no está disponible, espere una cierta cantidad de tiempo para que el recurso sea liberado, o devuelve el error.  El uso posterior de recursos se completa, cualquier llamada la función de [Unlock](../Topic/CSingleLock::Unlock.md) si el objeto de `CSingleLock` a utilizar de nuevo, o permite que el objeto de `CSingleLock` se destruirá.  
  
 los objetos de`CSingleLock` requieren la presencia de un objeto derivado de [CSyncObject](../../mfc/reference/csyncobject-class.md).  Normalmente es un miembro de datos de la clase de recurso controlado.  Para obtener más información sobre cómo utilizar los objetos de `CSingleLock` , vea el artículo [Multithreading: Cómo utilizar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## Jerarquía de herencia  
 `CSingleLock`  
  
## Requisitos  
 **encabezado:** afxmt.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMultiLock Class](../../mfc/reference/cmultilock-class.md)