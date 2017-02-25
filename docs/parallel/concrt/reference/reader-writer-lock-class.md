---
title: "reader_writer_lock (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::reader_writer_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "reader_writer_lock (clase)"
ms.assetid: 91a59cd2-ca05-4b74-8398-d826d9f86736
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# reader_writer_lock (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Un bloqueo de lectura o escritura basado en cola, con preferencia del sistema de escritura y con giro solo local.  El bloqueo permite el acceso primero en entrar, primero en salir \(FIFO\) a los sistemas de escritura y lectores agotados bajo una carga continua de sistemas de escritura.  
  
## Sintaxis  
  
```  
class reader_writer_lock;  
```  
  
## Miembros  
  
### Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[reader\_writer\_lock::scoped\_lock \(Clase\)](../Topic/reader_writer_lock::scoped_lock%20Class.md)|Una excepción segura del contenedor RAII que se puede usar para adquirir objetos de bloqueo `reader_writer_lock` como un sistema de escritura.|  
|[reader\_writer\_lock::scoped\_lock\_read \(Clase\)](../Topic/reader_writer_lock::scoped_lock_read%20Class.md)|Una excepción segura del contenedor RAII que se puede usar para adquirir objetos de bloqueo `reader_writer_lock` como un lector.|  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[reader\_writer\_lock::reader\_writer\_lock \(Constructor\)](../Topic/reader_writer_lock::reader_writer_lock%20Constructor.md)|Crea un nuevo objeto `reader_writer_lock`.|  
|[reader\_writer\_lock::~reader\_writer\_lock \(Destructor\)](../Topic/reader_writer_lock::~reader_writer_lock%20Destructor.md)|Destruye el objeto `reader_writer_lock`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[reader\_writer\_lock::lock \(Método\)](../Topic/reader_writer_lock::lock%20Method.md)|Adquiere el bloqueo de lectura o escritura como un sistema de escritura.|  
|[reader\_writer\_lock::lock\_read \(Método\)](../Topic/reader_writer_lock::lock_read%20Method.md)|Adquiere el bloqueo de lectura o escritura como un lector.  Si hay sistemas de escritura, los lectores activos tienen que esperar hasta que hayan terminado.  El lector simplemente registra un interés en el bloqueo y espera que los sistemas de escritura lo liberen.|  
|[reader\_writer\_lock::try\_lock \(Método\)](../Topic/reader_writer_lock::try_lock%20Method.md)|Intenta adquirir el bloqueo reader\-writer como un sistema de escritura sin bloqueo.|  
|[reader\_writer\_lock::try\_lock\_read \(Método\)](../Topic/reader_writer_lock::try_lock_read%20Method.md)|Intenta adquirir el bloqueo reader\-writer como un lector sin bloqueo.|  
|[reader\_writer\_lock::unlock \(Método\)](../Topic/reader_writer_lock::unlock%20Method.md)|Desbloquea el bloqueo del sistema de escritura del lector basado en quién lo bloqueó, en el lector o en el sistema de escritura.|  
  
## Comentarios  
 Para obtener más información, vea [Estructuras de datos de sincronización](../../../parallel/concrt/synchronization-data-structures.md).  
  
## Jerarquía de herencia  
 `reader_writer_lock`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [critical\_section \(Clase\)](../../../parallel/concrt/reference/critical-section-class.md)