---
title: "CMultiLock Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMultiLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiLock class"
  - "synchronization objects, control de acceso"
ms.assetid: c5b7c78b-1f81-4387-b7dd-2c813c5b6b61
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CMultiLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa el mecanismo de control de acceso utilizado para controlar el acceso a los recursos en un programa de multithreading.  
  
## Sintaxis  
  
```  
class CMultiLock  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMultiLock::CMultiLock](../Topic/CMultiLock::CMultiLock.md)|Crea un objeto `CMultiLock`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMultiLock::IsLocked](../Topic/CMultiLock::IsLocked.md)|Determina si un objeto de sincronización concreto en la matriz está bloqueado.|  
|[CMultiLock::Lock](../Topic/CMultiLock::Lock.md)|Espera en la matriz de objetos de sincronización.|  
|[CMultiLock::Unlock](../Topic/CMultiLock::Unlock.md)|Libera los objetos de sincronización de.|  
  
## Comentarios  
 `CMultiLock` no tiene una clase base.  
  
 Para utilizar las clases [CSemaphore](../../mfc/reference/csemaphore-class.md)de sincronización, [CMutex](../../mfc/reference/cmutex-class.md), y [CEvent](../../mfc/reference/cevent-class.md), puede crear un objeto de **CMultiLock** o de [CSingleLock](../../mfc/reference/csinglelock-class.md) a la espera en y liberar el objeto de sincronización.  Utilice **CMultiLock** cuando hay varios objetos que puede usar en un momento determinado.  Utilice `CSingleLock` si solo necesita esperar en un objeto cada vez.  
  
 Para utilizar un objeto de **CMultiLock** , primero cree una matriz de los objetos de sincronización en los que desee a la espera.  A continuación, llama al constructor del objeto de **CMultiLock** dentro de una función miembro en la clase de recurso controlado.  Llamar a continuación a la función miembro de [bloqueo](../Topic/CMultiLock::Lock.md) para determinar si un recurso está disponible \(designado\).  Si es uno, continúe con el resto de la función miembro.  Si no hay recursos disponibles, espere una cierta cantidad de tiempo que un recurso sea liberado, o devuelve el error.  El uso posterior de un recurso se completa, cualquier llamada la función de [Unlock](../Topic/CMultiLock::Unlock.md) si el objeto de **CMultiLock** a utilizar de nuevo, o permite que el objeto de **CMultiLock** se destruirá.  
  
 Los objetos de**CMultiLock** son más útiles cuando un subproceso tiene un gran número de objetos de `CEvent` que puede responder.  Cree una matriz que contiene todos los punteros de `CEvent` , y llame a `Lock`.  Esto hará que el subproceso para esperar hasta que uno de los eventos se señala.  
  
 Para obtener más información sobre cómo utilizar los objetos de **CMultiLock** , vea el artículo [Multithreading: Cómo utilizar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## Jerarquía de herencia  
 `CMultiLock`  
  
## Requisitos  
 **encabezado:** afxmt.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)