---
title: "accelerator_view (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amprt/Concurrency::accelerator_view"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator_view (clase)"
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
caps.latest.revision: 18
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# accelerator_view (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Representa una abstracción del dispositivo virtual en un acelerador C\+\+ AMP de datos en paralelo.  
  
## Sintaxis  
  
```  
class accelerator_view;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accelerator\_view::accelerator\_view \(Constructor\)](../Topic/accelerator_view::accelerator_view%20Constructor.md)|Inicializa una nueva instancia de la clase `accelerator_view`.|  
|[accelerator\_view::~accelerator\_view \(Destructor\)](../Topic/accelerator_view::~accelerator_view%20Destructor.md)|Destruye el objeto `accelerator_view`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accelerator\_view::create\_marker \(Método\)](../Topic/accelerator_view::create_marker%20Method.md)|Devuelve un futuro para realizar un seguimiento de la finalización de todos los comandos presentados hasta ahora a este objeto `accelerator_view`.|  
|[accelerator\_view::flush \(Método\)](../Topic/accelerator_view::flush%20Method.md)|Presenta todos los comandos pendientes en cola al objeto `accelerator_view` al acelerador para su ejecución.|  
|[accelerator\_view::get\_accelerator \(Método\)](../Topic/accelerator_view::get_accelerator%20Method.md)|Devuelve el objeto `accelerator` para el objeto `accelerator_view`.|  
|[accelerator\_view::get\_is\_auto\_selection \(Método\)](../Topic/accelerator_view::get_is_auto_selection%20Method.md)|Devuelve un valor booleano que indica si el runtime seleccionará automáticamente un acelerador adecuado cuando el objeto `accelerator_view` se pase a [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md).|  
|[accelerator\_view::get\_is\_debug \(Método\)](../Topic/accelerator_view::get_is_debug%20Method.md)|Devuelve un valor booleano que indica si el objeto `accelerator_view` tiene el nivel DEBUG habilitado para informar sobre errores importantes.|  
|[accelerator\_view::get\_queuing\_mode \(Método\)](../Topic/accelerator_view::get_queuing_mode%20Method.md)|Devuelve el modo de puesta en cola para el objeto `accelerator_view`.|  
|[accelerator\_view::get\_version \(Método\)](../Topic/accelerator_view::get_version%20Method.md)|Devuelve la versión del `accelerator_view`.|  
|[accelerator\_view::wait \(Método\)](../Topic/accelerator_view::wait%20Method.md)|Espera a que todos los comandos enviados al objeto `accelerator_view` terminen.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accelerator\_view::operator\!\= \(Operador\)](../Topic/accelerator_view::operator!=%20Operator.md)|Compara este objeto `accelerator_view` con otro y devuelve `false` si son iguales; de lo contrario, devuelve `true`.|  
|[accelerator\_view::operator\= \(Operador\)](../Topic/accelerator_view::operator=%20Operator.md)|Copia el contenido del objeto especificado `accelerator_view` en este.|  
|[accelerator\_view::operator\=\= \(Operador\)](../Topic/accelerator_view::operator==%20Operator.md)|Compara este objeto `accelerator_view` con otro y devuelve `true` si son iguales; de lo contrario, devuelve `false`.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accelerator\_view::accelerator \(Miembro de datos\)](../Topic/accelerator_view::accelerator%20Data%20Member.md)|Obtiene el objeto `accelerator` para el objeto `accelerator_view`.|  
|[accelerator\_view::is\_auto\_selection \(Miembro de datos\)](../Topic/accelerator_view::is_auto_selection%20Data%20Member.md)|Obtiene un valor booleano que indica si el runtime seleccionará automáticamente un acelerador adecuado cuando el objeto `accelerator_view` se pase a [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md).|  
|[accelerator\_view::is\_debug \(Miembro de datos\)](../Topic/accelerator_view::is_debug%20Data%20Member.md)|Obtiene un valor booleano que indica si el objeto `accelerator_view` tiene el nivel DEBUG habilitado para informar sobre errores importantes.|  
|[accelerator\_view::queuing\_mode \(Miembro de datos\)](../Topic/accelerator_view::queuing_mode%20Data%20Member.md)|Obtiene el modo de puesta en cola para el objeto `accelerator_view`.|  
|[accelerator\_view::version \(Miembro de datos\)](../Topic/accelerator_view::version%20Data%20Member.md)|Obtiene la versión del acelerador.|  
  
## Jerarquía de herencia  
 `accelerator_view`  
  
## Comentarios  
 Un objeto `accelerator_view` representa una vista aislada y lógica desde un acelerador.  Un único dispositivo físico de cálculo puede tener muchos objetos lógicos, aislados de los objetos `accelerator_view`.  Cada acelerador tiene un objeto predeterminado `accelerator_view`.  Se pueden crear objetos adicionales `accelerator_view`.  
  
 Muchos subprocesos de cliente pueden compartir los dispositivos físicos.  Los subprocesos de cliente pueden utilizar cooperativamente el mismo objeto `accelerator_view` de un acelerador, o cada cliente puede comunicarse con un dispositivo de cálculo mediante un objeto independiente `accelerator_view` para aislarlo de otros subprocesos de cliente.  
  
 Un objeto `accelerator_view` puede tener uno de dos estados [queuing\_mode \(Enumeración\)](../../../parallel/amp/reference/queuing-mode-enumeration.md).  Si el modo de la puesta en cola es `immediate`, los comandos como `copy` y `parallel_for_each` se envían al correspondiente dispositivo de aceleradores en cuanto vuelven al llamador.  Si el modo de puesta en cola es `deferred`, estos comandos se ponen en cola en una cola de comando que corresponde al objeto `accelerator_view`.  Los comandos no se envían realmente al dispositivo hasta que se llame a `flush()`.  
  
## Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Simultaneidad  
  
## Vea también  
 [Espacio de nombres de simultaneidad \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)