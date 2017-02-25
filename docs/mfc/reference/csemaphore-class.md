---
title: "CSemaphore Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CSemaphore"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSemaphore class"
  - "semáforos"
  - "synchronization objects, semáforos"
ms.assetid: 385fc7e4-8f86-4be2-85e1-d23b38c12f7f
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CSemaphore Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Un objeto de clase `CSemaphore` representa un “semáforo” — un objeto de sincronización que permite que un número limitado de subprocesos en uno o varios procesos tengan acceso a un Maintains un recuento del número de subprocesos que tienen acceso actualmente un recurso especificado.  
  
## Sintaxis  
  
```  
class CSemaphore : public CSyncObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSemaphore::CSemaphore](../Topic/CSemaphore::CSemaphore.md)|Crea un objeto `CSemaphore`.|  
  
## Comentarios  
 Los semáforos son útiles para controlar el acceso a un recurso compartido que puede admitir solo un número limitado de usuarios.  El recuento actual del objeto de `CSemaphore` es el número de usuarios adicionales permitidos.  Cuando el número llega a cero, todos los intentos de utilizar el recurso controlado por el objeto de **CSemaphore** se insertarán en una cola y una espera de sistema hasta su tiempo de espera o los encumbramientos de recuento sobre 0.  Especifique el número máximo de usuarios que pueden tener acceso al recurso controlado al mismo tiempo durante la construcción del objeto de `CSemaphore` .  
  
 Para utilizar un objeto de **CSemaphore** , cree el objeto de `CSemaphore` cuando es necesario.  Especifique el nombre de semáforo que va a esperar, y que la aplicación debe poseerla inicialmente.  Podrá obtener acceso al semáforo cuando el constructor devuelve.  Llame a [CSyncObject::Unlock](../Topic/CSyncObject::Unlock.md) cuando se haga que tiene acceso al recurso controlado.  
  
 Un método alternativo para utilizar los objetos de `CSemaphore` es agregar una variable de `CSemaphore` escrito como un miembro de datos a la clase que desee al control.  Durante la construcción del objeto controlado, llame al constructor del miembro de datos de `CSemaphore` que especifica el recuento inicial de acceso, el número máximo de acceso, el nombre del semáforo \(si utiliza los límites de un proceso\), y atributos de seguridad deseados.  
  
 Para tener acceso a los recursos controlados por los objetos de `CSemaphore` de esta manera, primero para crear una variable de [CSingleLock](../../mfc/reference/csinglelock-class.md) cualquiera de [CMultiLock](../../mfc/reference/cmultilock-class.md) escrito en la función miembro de acceso del recurso.  Llamar a continuación a la función miembro de `Lock` de objeto de bloqueo \(por ejemplo, [CSingleLock::Lock](../Topic/CSingleLock::Lock.md)\).  En este punto, el subproceso accederá el recurso, espere a que el recurso sea liberado y accederá, o esperará el recurso se producirán liberar y el tiempo de espera, si se deja para obtener acceso al recurso.  En cualquier caso, el recurso se ha tenido acceso de una manera segura para subprocesos.  Para liberar el recurso, utilizar la función miembro de `Unlock` de objeto de bloqueo \(por ejemplo, [CSingleLock::Unlock](../Topic/CSingleLock::Unlock.md)\), o permitir que el objeto de bloqueo a la reducción fuera del ámbito.  
  
 Alternativamente, puede crear un objeto de **CSemaphore** independiente, y se tiene acceso explícitamente antes de intentar obtener acceso al recurso controlado.  Este método, mientras que de alguien que lea el código fuente, es un error más propenso.  
  
 Para obtener más información sobre cómo utilizar los objetos de **CSemaphore** , vea el artículo [Multithreading: Cómo utilizar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CSemaphore`  
  
## Requisitos  
 **encabezado:** afxmt.h  
  
## Vea también  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)