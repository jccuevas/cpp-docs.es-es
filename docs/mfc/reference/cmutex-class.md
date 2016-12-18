---
title: "CMutex Class | Microsoft Docs"
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
  - "Mutex"
  - "CMutex"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMutex class"
  - "mutex"
  - "clases de sincronización, CMutex class"
  - "synchronization objects, mutex"
ms.assetid: 6330c050-4f01-4195-a099-2029b92f8cf1
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMutex Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una “exclusión mutua” — un objeto de sincronización que permite que un subproceso tenga \- acceso exclusivo a un recurso.  
  
## Sintaxis  
  
```  
class CMutex : public CSyncObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMutex::CMutex](../Topic/CMutex::CMutex.md)|Crea un objeto `CMutex`.|  
  
## Comentarios  
 Exclusiones mutuas es útil cuando sólo un subproceso cada vez se puede permitir modificar datos o a otro recurso controlado.  Por ejemplo, agregar nodos a una lista vinculada es un proceso que se debe permitir únicamente por un subproceso cada vez.  Utilizando un objeto de `CMutex` para controlar la lista vinculada, solo un subproceso a la vez puede obtener acceso a la lista.  
  
 Para utilizar un objeto de `CMutex` , cree el objeto de `CMutex` cuando es necesario.  Especifique el nombre mutex que va a esperar, y que la aplicación debe poseerla inicialmente.  Podrá obtener acceso a la exclusión mutua cuando el constructor devuelve.  Llame a [CSyncObject::Unlock](../Topic/CSyncObject::Unlock.md) cuando se haga que tiene acceso al recurso controlado.  
  
 Un método alternativo para utilizar los objetos de `CMutex` es agregar una variable de `CMutex` escrito como un miembro de datos a la clase que desee al control.  Durante la construcción del objeto controlado, llame al constructor de especificar de los `CMutex` si la exclusión mutua se posee inicialmente, nombre mutex \(si utiliza los límites de un proceso\), y los atributos de seguridad deseados.  
  
 Para tener acceso a los recursos controlados por los objetos de `CMutex` de esta manera, primero para crear una variable de [CSingleLock](../../mfc/reference/csinglelock-class.md) cualquiera de [CMultiLock](../../mfc/reference/cmultilock-class.md) escrito en la función miembro de acceso del recurso.  Llamar a continuación a la función miembro de `Lock` de objeto de bloqueo \(por ejemplo, [CSingleLock::Lock](../Topic/CSingleLock::Lock.md)\).  En este punto, el subproceso accederá el recurso, espere a que el recurso sea liberado y accederá, o esperará el recurso se producirán liberar y el tiempo de espera, si se deja para obtener acceso al recurso.  En cualquier caso, el recurso se ha tenido acceso de una manera segura para subprocesos.  Para liberar el recurso, utilizar la función miembro de `Unlock` de objeto de bloqueo \(por ejemplo, [CSingleLock::Unlock](../Topic/CSingleLock::Unlock.md)\), o permitir que el objeto de bloqueo a la reducción fuera del ámbito.  
  
 Para obtener más información sobre cómo utilizar los objetos de `CMutex` , vea el artículo [Multithreading: Cómo utilizar las clases de sincronización](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CSyncObject](../../mfc/reference/csyncobject-class.md)  
  
 `CMutex`  
  
## Requisitos  
 **encabezado:** afxmt.h  
  
## Vea también  
 [CSyncObject Class](../../mfc/reference/csyncobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)