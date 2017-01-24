---
title: "&lt;allocators&gt; | Microsoft Docs"
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
  - "stdext::<allocators>"
  - "allocators/stdext::allocators"
  - "<allocators>"
  - "stdext.<allocators>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "allocators (encabezado)"
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;allocators&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Define varias plantillas que ayudan a asignar y los bloques de memoria libre para los contenedores nodo\- basados en.  
  
## Sintaxis  
  
```  
#include <allocators>  
```  
  
## Comentarios  
 \<El encabezado\> de los asignadores proporciona seis plantillas de asignador que se pueden utilizar las estrategias de administración de memoria seleccionar para los contenedores nodo\- basados en.  Para el uso con estas plantillas, también proporciona varios filtros de sincronización para adaptar la estrategia de administración de memoria a distintos esquemas de multithreading \(sin incluida.  La coincidencia una estrategia de administración de memoria los modelos conocidos de utilización de memoria, y los requisitos de sincronización, una aplicación determinada puede aumentar la velocidad o reducir a menudo los requisitos de memoria total de una aplicación.  
  
 Las plantillas de asignador se implementan con componentes reutilizables que pueden ser personalizados o reemplazar para proporcionar estrategias de administración de memoria adicionales.  
  
 Los contenedores nodo\- basándose en la biblioteca estándar de C\+\+ \(std::list, std::set, std::multiset, std::map y std::multimap\) almacenan sus elementos en nodos.  Todos los nodos de un tipo de contenedor set son el mismo tamaño, por lo que la flexibilidad de un administrador de memoria de uso general no es necesaria.  Dado que el tamaño de cada bloque de memoria se conoce en tiempo de compilación, el administrador de memoria puede ser mucho más sencilla y más rápido.  
  
 Cuando se utilizan con contenedores que nodo\- no se basan \(como el std::deque estándar de std::vector de los contenedores de la biblioteca de C\+\+ y, std::basic\_string\), las plantillas de alllocator funcionarán correctamente, pero no probablemente proporcionar ninguna mejora de rendimiento sobre el asignador predeterminado.  
  
 Un asignador es una clase de plantilla que describe un objeto que administra la asignación de almacenamiento y liberar para los objetos y matrices de objetos de tipo designado.  Los objetos del asignador utilizan varias clases de plantilla de contenedor en la biblioteca estándar de C\+\+.  
  
 Los asignadores son todas las plantillas de este tipo:  
  
 `template<class`  `Type` `>`  
  
 `class allocator;`  
  
 donde es el tipo el argumento `Type` de plantilla administrado por la instancia del asignador.  La biblioteca estándar de C\+\+ proporciona un asignador predeterminado, la clase de plantilla [asignador](../standard-library/allocator-class.md), que se define en [\<memory\>](../standard-library/memory.md).  \<El encabezado\> de los asignadores proporciona los asignadores siguientes:  
  
-   [allocator\_newdel](../standard-library/allocator-newdel-class.md)  
  
-   [allocator\_unbounded](../standard-library/allocator-unbounded-class.md)  
  
-   [allocator\_fixed\_size](../standard-library/allocator-fixed-size-class.md)  
  
-   [allocator\_variable\_size](../standard-library/allocator-variable-size-class.md)  
  
-   [allocator\_suballoc](../standard-library/allocator-suballoc-class.md)  
  
-   [allocator\_chunklist](../standard-library/allocator-chunklist-class.md)  
  
 Utilice una creación correcta de un asignador como segundo argumento de tipo al crear un contenedor, como en el ejemplo de código siguiente.  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`  
  
 \_List0 asigna nodos con `allocator_chunklist` y el filtro predeterminado de sincronización.  
  
 Utilice la macro [ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md) para crear plantillas de asignador con los filtros de sincronización distinto del predeterminado:  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`  
  
 `std::list<int, alloc<int> > _List1;`  
  
 \_Lst1 asigna nodos con `allocator_chunklist` y el filtro de sincronización de [synchronization\_per\_thread](../standard-library/sync-per-thread-class.md) .  
  
 Un asignador de bloque es caché o un filtro.  Caché es una clase de plantilla que toma un argumento de std::size\_t escrito.  Define un asignador de bloque que asignar y desasignar cualquier espacio bloques de memoria de un solo tamaño.  Debe obtener memoria utilizando el operador `new`, pero no necesita realizar una llamada independiente al operador `new` para cada bloque.  Puede, por ejemplo, suballocate de un bloque mayor o bloques desasignados caché para la reasignación subsiguiente.  
  
 Con un compilador que no pueda compilar reencuaderne el valor del argumento de std::size\_t se usa cuando la plantilla se han creado instancias no es necesariamente el valor de \_Sz del argumento pasado al miembro de caché que las funciones asignan y que desasignan.  
  
 \<los asignadores\> proporcionan las siguientes plantillas de caché:  
  
-   [cache\_freelist](../standard-library/cache-freelist-class.md)  
  
-   [cache\_suballoc](../standard-library/cache-suballoc-class.md)  
  
-   [cache\_chunklist](../standard-library/cache-chunklist-class.md)  
  
 Un filtro es un asignador de bloque que implementa sus funciones miembro utilizando otro asignador del bloque que se pasa a como argumento de plantilla.  La forma más común de filtro es un filtro de sincronización, que aplica una directiva de sincronización para controlar el acceso a las funciones miembro de una instancia de otro asignador de bloque. \<los asignadores\> proporciona filtros siguientes de sincronización:  
  
-   [synchronization\_none](../standard-library/sync-none-class.md)  
  
-   [synchronization\_per\_container](../standard-library/sync-per-container-class.md)  
  
-   [synchronization\_per\_thread](../standard-library/sync-per-thread-class.md)  
  
-   [synchronization\_shared](../standard-library/sync-shared-class.md)  
  
 \<los asignadores\> también proporcionan el filtro [rts\_alloc](../standard-library/rts-alloc-class.md), que contiene las instancias del asignador de bloques de varias y determina que instancia a utilizar para la asignación o la desasignación en tiempo de ejecución en lugar de en tiempo de compilación.  Se utiliza con compiladores que no pueden compilar reencuadernan.  
  
 Una directiva de sincronización determina cómo los identificadores de instancia las solicitudes simultáneas de asignación de un asignador y la desasignación de varios subprocesos.  La directiva más simple es pasar todas las solicitudes directamente a través del objeto de caché subyacente, ya que la administración de sincronización al usuario.  Una directiva más compleja podría ser utilizar una exclusión mutua para serializar el acceso al objeto de caché subyacente.  
  
 Si un compilador admite la compilación de aplicaciones de un único subproceso y multiproceso, el filtro predeterminado de sincronización para las aplicaciones de un único subproceso es `sync_none`; para todos los demás casos es `sync_shared`.  
  
 La plantilla `cache_freelist` de caché toma un argumento máximo de la clase que determina el número máximo de elementos que se almacenan en la lista disponible.  
  
 \<los asignadores\> proporcionan las clases de siguientes:  
  
-   [max\_none](../standard-library/max-none-class.md)  
  
-   [max\_unbounded](../standard-library/max-unbounded-class.md)  
  
-   [max\_fixed\_size](../standard-library/max-fixed-size-class.md)  
  
-   [max\_variable\_size](../standard-library/max-variable-size-class.md)  
  
### Macros  
  
|||  
|-|-|  
|[ALLOCATOR\_DECL](../Topic/ALLOCATOR_DECL%20\(%3Callocators%3E\).md)|Genera una clase de plantilla de asignador.|  
|[CACHE\_CHUNKLIST](../Topic/CACHE_CHUNKLIST%20\(%3Callocators%3E\).md)|Produce `stdext::allocators::cache_chunklist<sizeof(Type)>`.|  
|[CACHE\_FREELIST](../Topic/CACHE_FREELIST%20\(%3Callocators%3E\).md)|Produce `stdext::allocators::cache_freelist<sizeof(Type), max>`.|  
|[CACHE\_SUBALLOC](../Topic/CACHE_SUBALLOC%20\(%3Callocators%3E\).md)|Produce `stdext::allocators::cache_suballoc<sizeof(Type)>`.|  
|[SYNC\_DEFAULT](../Topic/SYNC_DEFAULT%20\(%3Callocators%3E\).md)|Produce un filtro de sincronización.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\!\=](../Topic/operator!=%20\(%3Callocators%3E\).md)|Comprueba la desigualdad entre los objetos de asignador de una clase especificada.|  
|[operator\=\=](../Topic/operator==%20\(%3Callocators%3E\).md)|Comprueba la igualdad entre los objetos de asignador de una clase especificada.|  
  
### Clases  
  
|||  
|-|-|  
|[allocator\_base](../standard-library/allocator-base-class.md)|Define la clase base y funciones comunes necesarias para crear un asignador definido por el usuario de un filtro de sincronización.|  
|[allocator\_chunklist](../standard-library/allocator-chunklist-class.md)|Describe un objeto que administra la asignación de almacenamiento y liberar para los objetos en la memoria caché de [cache\_chunklist](../standard-library/cache-chunklist-class.md)escrito.|  
|[allocator\_fixed\_size](../standard-library/allocator-fixed-size-class.md)|Describe un objeto que administra la asignación de almacenamiento y liberar para los objetos de `Type` escribe utilizando la memoria caché de [cache\_freelist](../standard-library/cache-freelist-class.md) escrito con una longitud administrada por [max\_fixed\_size](../standard-library/max-fixed-size-class.md).|  
|[allocator\_newdel](../standard-library/allocator-newdel-class.md)|Implementa un asignador que utilice `operator delete` para desasignar un bloque y `operator new` de memoria para asignar un bloque de memoria.|  
|[allocator\_suballoc](../standard-library/allocator-suballoc-class.md)|Describe un objeto que administra la asignación de almacenamiento y liberar para los objetos de `Type` escribe utilizando la memoria caché de [cache\_suballoc](../standard-library/cache-suballoc-class.md)escrito.|  
|[allocator\_unbounded](../standard-library/allocator-unbounded-class.md)|Describe un objeto que administra la asignación de almacenamiento y liberar para los objetos de `Type` escribe utilizando la memoria caché de [cache\_freelist](../standard-library/cache-freelist-class.md) escrito con una longitud administrada por [max\_unbounded](../standard-library/max-unbounded-class.md).|  
|[allocator\_variable\_size](../standard-library/allocator-variable-size-class.md)|Describe un objeto que administra la asignación de almacenamiento y liberar para los objetos de `Type` escribe utilizando la memoria caché de [cache\_freelist](../standard-library/cache-freelist-class.md) escrito con una longitud administrada por [max\_variable\_size](../standard-library/max-variable-size-class.md).|  
|[cache\_chunklist](../standard-library/cache-chunklist-class.md)|Define un asignador de bloque que asignar y desasignar cualquier espacio bloques de memoria de un solo tamaño.|  
|[cache\_freelist](../standard-library/cache-freelist-class.md)|Define un asignador de bloque que asignar y desasignar cualquier espacio bloques de memoria de un solo tamaño.|  
|[cache\_suballoc](../standard-library/cache-suballoc-class.md)|Define un asignador de bloque que asignar y desasignar cualquier espacio bloques de memoria de un solo tamaño.|  
|[freelist](../standard-library/freelist-class.md)|Administra una lista de bloques de memoria.|  
|[max\_fixed\_size](../standard-library/max-fixed-size-class.md)|Describe un objeto máximo de la clase limitar un objeto de [freelist](../standard-library/freelist-class.md) a una longitud máxima fija.|  
|[max\_none](../standard-library/max-none-class.md)|Describe un objeto máximo de la clase limitar un objeto de [freelist](../standard-library/freelist-class.md) a una longitud máxima de cero.|  
|[max\_unbounded](../standard-library/max-unbounded-class.md)|Describe un objeto máximo de clase que no limita la longitud máxima de un objeto de [freelist](../standard-library/freelist-class.md) .|  
|[max\_variable\_size](../standard-library/max-variable-size-class.md)|Describe un objeto máximo de la clase limitar un objeto de [freelist](../standard-library/freelist-class.md) a una longitud máxima que sea aproximadamente proporcional al número de bloques de memoria asignados.|  
|[rts\_alloc](../standard-library/rts-alloc-class.md)|La clase de plantilla de rts\_alloc describe [filtro](../standard-library/allocators-header.md) que contiene una matriz de instancias de caché y determina que instancia a utilizar para la asignación y la desasignación en tiempo de ejecución en lugar de en tiempo de compilación.|  
|[synchronization\_none](../standard-library/sync-none-class.md)|Describe un filtro de sincronización que no proporciona ninguna sincronización.|  
|[synchronization\_per\_container](../standard-library/sync-per-container-class.md)|Describe un filtro de sincronización que proporciona un objeto de caché independiente para cada objeto de asignador.|  
|[synchronization\_per\_thread](../standard-library/sync-per-thread-class.md)|Describe un filtro de sincronización que proporciona un objeto de caché independiente para cada subproceso.|  
|[synchronization\_shared](../standard-library/sync-shared-class.md)|Describe un filtro de sincronización que utilice una exclusión mutua para controlar el acceso a un objeto de caché compartido por todos los asignadores.|  
  
## Requisitos  
 asignadores \<de**Encabezado:** \>  
  
 **Espacio de nombres:** stdext  
  
## Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)