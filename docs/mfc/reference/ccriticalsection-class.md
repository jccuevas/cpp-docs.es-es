---
title: "CCriticalSection Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CCriticalSection"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCriticalSection class"
  - "critical sections"
  - "clases de sincronización, CCriticalSection class"
  - "synchronization objects, critical section"
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CCriticalSection Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una “sección crítica” — un objeto de sincronización que permite que un subproceso cada vez tenga acceso a un recurso o a una sección de código.  
  
## Sintaxis  
  
```  
class CCriticalSection : public CSyncObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCriticalSection::CCriticalSection](../Topic/CCriticalSection::CCriticalSection.md)|Crea un objeto `CCriticalSection`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCriticalSection::Lock](../Topic/CCriticalSection::Lock.md)|Utilice para obtener acceso al objeto de `CCriticalSection` .|  
|[CCriticalSection::Unlock](../Topic/CCriticalSection::Unlock.md)|Libera el objeto de `CCriticalSection` .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCriticalSection::operator CRITICAL\_SECTION\*](../Topic/CCriticalSection::operator%20CRITICAL_SECTION*.md)|Recupera un puntero al objeto interno de **CRITICAL\_SECTION** .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CCriticalSection::m\_sect](../Topic/CCriticalSection::m_sect.md)|un objeto de **CRITICAL\_SECTION** .|  
  
## Comentarios  
 Las secciones críticas son útiles cuando sólo un subproceso cada vez se puede permitir modificar datos o a otro recurso controlado.  Por ejemplo, agregar nodos a una lista vinculada es un proceso que se debe permitir únicamente por un subproceso cada vez.  Utilizando un objeto de `CCriticalSection` para controlar la lista vinculada, solo un subproceso a la vez puede obtener acceso a la lista.  
  
> [!NOTE]
>  La funcionalidad de la clase de `CCriticalSection` proporcionan un objeto real de Win32 **CRITICAL\_SECTION** .  
  
 Las secciones críticas se utilizan en lugar de exclusiones mutuas \(vea [CMutex](../../mfc/reference/cmutex-class.md)\) cuando la velocidad es crítica y no se utilizará el recurso a través de límites de procesos.  
  
 Hay dos métodos para utilizar un objeto de `CCriticalSection` : independiente y incrustado en una clase.  
  
-   El método independiente para utilizar un objeto independiente de `CCriticalSection` , construye el objeto de `CCriticalSection` cuando es necesario.  Después de que un retorno correcto de constructor, explícitamente bloquea el objeto con una llamada a [bloqueo](../Topic/CCriticalSection::Lock.md).  Llame a [Unlock](../Topic/CCriticalSection::Unlock.md) cuando termine teniendo acceso a la sección crítica.  Este método, mientras que de alguien que lee el código fuente, es un error más propenso como debe recordar bloquear y desbloquear la sección crítica antes y después de acceso.  
  
     un método más preferible es utilizar la clase de [CSingleLock](../../mfc/reference/csinglelock-class.md) .  También tiene un método de `Lock` y de `Unlock` , pero no tiene que preocuparse de desbloquear el recurso si se produce una excepción.  
  
-   El método incrustado también puede compartir una clase con varios subprocesos agregando `CCriticalSection`\- escriba el miembro de datos a la clase y a bloquear el miembro de datos cuando sea necesario.  
  
 Para obtener más información sobre cómo utilizar los objetos de `CCriticalSection` , vea el artículo [Multithreading: Cómo utilizar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CCriticalSection`  
  
## Requisitos  
 **encabezado:** afxmt.h  
  
## Vea también  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMutex Class](../../mfc/reference/cmutex-class.md)