---
title: "&lt;memory&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::<memory>"
  - "std.<memory>"
  - "<memory>"
  - "std::<memory>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memory (encabezado)"
ms.assetid: ef8e38da-7c9d-4037-9ad1-20c99febf5dc
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;memory&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define una clase, un operador y varias plantillas que sirven de ayuda para asignar y liberar objetos.  
  
## Sintaxis  
  
```  
  
#include <memory>  
  
```  
  
## Miembros  
  
### Funciones  
  
|||  
|-|-|  
|[addressof](../Topic/addressof.md)|Obtiene la dirección real de un objeto.|  
|[align](../Topic/align.md)|Devuelve un puntero a un intervalo de tamaño determinado, en función de la alineación y la dirección inicial proporcionadas,|  
|[allocate\_shared](../Topic/allocate_shared.md)|Crea un `shared_ptr` a objetos asignados y construidos para un tipo determinado con un asignador especificado.|  
|[checked\_uninitialized\_copy](../misc/checked-uninitialized-copy.md)|Igual que `uninitialized_copy` pero impone el uso de un iterador comprobado como iterador de salida.|  
|[checked\_uninitialized\_fill\_n](../misc/checked-uninitialized-fill-n.md)|Igual que `uninitialized_fill_n` pero impone el uso de un iterador comprobado como iterador de salida.|  
|[const\_pointer\_cast](../Topic/const_pointer_cast.md)|Const convertida en `shared_ptr`.|  
|[declare\_no\_pointers](../Topic/declare_no_pointers.md)|Informa a un recolector de elementos no utilizados de que los caracteres que empiezan en una dirección especificada y entran en el tamaño de bloque indicado no contienen punteros rastreables.|  
|[declare\_reachable](../Topic/declare_reachable.md)|Informa a la recolección de elementos no utilizados de que la dirección indicada es para el almacenamiento asignado y es accesible.|  
|[default\_delete](../Topic/default_delete.md)|Elimina objetos asignados a `operator new`.  Apto para el uso con `unique_ptr`.|  
|[dynamic\_pointer\_cast](../Topic/dynamic_pointer_cast.md)|Conversión dinámica en `shared_ptr`.|  
|[get\_deleter](../Topic/get_deleter%20Function.md)|Obtiene el delimitador de `shared_ptr`.|  
|[get\_pointer\_safety](../Topic/get_pointer_safety.md)|Devuelve el tipo de seguridad del puntero asumido por cualquier recolector de elementos no utilizados.|  
|[get\_temporary\_buffer](../Topic/get_temporary_buffer.md)|Asigna almacenamiento temporal para una secuencia de elementos que no supere un número especificado de elementos.|  
|[make\_shared](../Topic/make_shared%20\(%3Cmemory%3E\).md)|Crea y devuelve un `shared_ptr` que señala al objeto asignado construido sin argumentos o con algún argumento mediante el asignador predeterminado.|  
|[make\_unique](../Topic/make_unique.md)|Crea y devuelve un [unique\_ptr](../standard-library/unique-ptr-class.md) que señala al objeto asignado construido sin argumentos o con algún argumento.|  
|[owner\_less](../Topic/owner_less.md)|Permite realizar comparaciones mixtas basadas en la propiedad de punteros compartidos y parciales.|  
|[pointer\_safety](../Topic/pointer_safety%20Enumeration.md)|Una enumeración de todos los valores devueltos posibles para `get_pointer_safety`.|  
|[return\_temporary\_buffer](../Topic/return_temporary_buffer.md)|Desasigna la memoria temporal que se asignó mediante la función de plantilla `get_temporary_buffer`.|  
|[static\_pointer\_cast](../Topic/static_pointer_cast.md)|Conversión estática en `shared_ptr`.|  
|[swap](../Topic/swap%20\(C++%20Standard%20Library\).md)|Intercambia dos objetos `shared_ptr` o `weak_ptr`.|  
|[unchecked\_uninitialized\_copy](../misc/unchecked-uninitialized-copy.md)|Igual que `uninitialized_copy` pero permite el uso de un iterador no comprobado como iterador de salida cuando se define \_SECURE\_SCL\=1.|  
|[unchecked\_uninitialized\_fill\_n](../misc/unchecked-uninitialized-fill-n.md)|Igual que `uninitialized_fill_n` pero permite el uso de un iterador no comprobado como iterador de salida cuando se define \_SECURE\_SCL\=1.|  
|[undeclare\_no\_pointers](../Topic/undeclare_no_pointers.md)|Informa a un recolector de elementos no utilizados de que los caracteres del bloque de memoria definido por un puntero de dirección base y el tamaño del bloque pueden contener ahora punteros rastreables.|  
|[undeclare\_reachable](../Topic/undeclare_reachable.md)|Informa a `garbage_collector` de que una ubicación de memoria especificada es inaccesible.|  
|[uninitialized\_copy](../Topic/uninitialized_copy.md)|Copia objetos de un intervalo de entrada especificado en un intervalo de destino sin inicializar.|  
|[uninitialized\_copy\_n](../Topic/uninitialized_copy_n.md)|Crea una copia de un número especificado de elementos de un iterador de entrada.  Las copias se colocan en un iterador hacia delante.|  
|[uninitialized\_fill](../Topic/uninitialized_fill.md)|Copia objetos de un valor especificado en un intervalo de destino sin inicializar.|  
|[uninitialized\_fill\_n](../Topic/uninitialized_fill_n.md)|Copia objetos de un valor especificado en un número especificado de elementos de un intervalo de destino sin inicializar.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Cmemory%3E\).md)|Comprueba la desigualdad entre los objetos de asignador de una clase especificada.|  
|[operator\=\=](../Topic/operator==%20\(%3Cmemory%3E\).md)|Comprueba la igualdad entre los objetos de asignador de una clase especificada.|  
|[operator\>\=](../Topic/operator%3E=%20\(%3Cmemory%3E\).md)|Comprueba si un objeto de asignador es mayor o igual que un segundo objeto de asignador de una clase especificada.|  
|[operador \<](../Topic/operator%3C%20\(%3Cmemory%3E\).md)|Comprueba si un objeto es menor que un segundo objeto de una clase especificada.|  
|[operator\<\=](../Topic/operator%3C=%20\(%3Cmemory%3E\).md)|Comprueba si un objeto es menor o igual que un segundo objeto de una clase especificada.|  
|[operador \>](../Topic/operator%3E%20\(%3Cmemory%3E\).md)|Comprueba si un objeto es mayor que un segundo objeto de una clase especificada.|  
|[operador \<\<](../Topic/operator%3C%3C%20\(%3Cmemory%3E\).md)|`shared_ptr` inserter.|  
  
### Clases  
  
|||  
|-|-|  
|[asignador](../standard-library/allocator-class.md)|La clase de plantilla describe un objeto que administra la asignación de almacenamiento y la liberación de las matrices de objetos del tipo **Type**.|  
|[allocator\_traits](../standard-library/allocator-traits-class.md)|Describe un objeto que determina toda la información que necesita un contenedor habilitado como asignador.|  
|[auto\_ptr](../standard-library/auto-ptr-class.md)|La clase de plantilla describe un objeto que almacena un puntero en un objeto asignado del tipo **Type \*** que garantiza que el objeto al que señala se elimina cuando su auto\_ptr incluyente se destruye.|  
|[bad\_weak\_ptr](../standard-library/bad-weak-ptr-class.md)|Informa de una excepción weak\_ptr errónea.|  
|[enabled\_shared\_from\_this](../standard-library/enable-shared-from-this-class.md)|Ayuda a generar un `shared_ptr`.|  
|[pointer\_traits](../standard-library/pointer-traits-struct.md)|Proporciona información que necesita un objeto de clase de plantilla `allocator_traits` para describir un asignador con el tipo de puntero `Ptr`.|  
|[raw\_storage\_iterator](../standard-library/raw-storage-iterator-class.md)|Una clase de adaptador que se proporciona para permitir que los algoritmos almacenen sus resultados en memoria sin inicializar.|  
|[shared\_ptr](../standard-library/shared-ptr-class.md)|Encapsula un puntero inteligente en el que se cuentan las referencias alrededor de un objeto asignado dinámicamente.|  
|[unique\_ptr](../standard-library/unique-ptr-class.md)|Almacena un puntero a un objeto en propiedad.  El puntero únicamente es propiedad de `unique_ptr`.  Se destruye `unique_ptr` cuando se destruye el propietario.|  
|[weak\_ptr](../standard-library/weak-ptr-class.md)|Contiene un puntero débilmente vinculado.|  
  
### Especializaciones  
  
|||  
|-|-|  
|[allocator\<void\>](../standard-library/allocator-void-class.md)|Una especialización del asignador de la clase de plantilla para el tipo void, que define los únicos tipos miembro que tienen sentido en este contexto especializado.|  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)   
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)