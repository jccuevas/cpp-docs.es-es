---
title: '&lt;allocators&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <allocators>
dev_langs: C++
helpviewer_keywords: allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b87e52294ccd61cd349ed6a85eca6760ace2c473
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;
Define varias plantillas que ayudan a asignar y liberar bloques de memoria para contenedores basados en nodos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
#include <allocators>  
```  
  
## <a name="remarks"></a>Comentarios  
 El encabezado \<allocators> proporciona seis plantillas de asignador que se pueden usar para seleccionar estrategias de administración de memoria para los contenedores basados en nodos. Para su uso con estas plantillas, también proporciona varios filtros de sincronización diferentes para adaptar la estrategia de administración de memoria a una serie de esquemas multithreading distintos (incluso ninguno). La combinación de una estrategia de administración de memoria con los patrones de uso de memoria conocidos, y los requisitos de sincronización, de una determinada aplicación, puede aumentar la velocidad o reducir los requisitos de memoria generales de una aplicación.  
  
 Las plantillas de asignador se implementan con componentes reutilizables que se pueden personalizar o reemplazar a fin de proporcionar estrategias de administración de memoria adicionales.  
  
 Los contenedores basados en nodos de la biblioteca estándar de C++ (std::list, std::set, std::multiset, std::map y std::multimap) almacenan sus elementos en nodos individuales. Todos los nodos de un tipo de contenedor determinado tienen el mismo tamaño, por lo que no es necesaria la flexibilidad de un administrador de memoria de propósito general. Dado que se conoce el tamaño de cada bloque de memoria en tiempo de compilación, el administrador de memoria puede ser mucho más rápido y sencillo.  
  
 Cuando se usan con contenedores que no están basados en nodos (por ejemplo, los contenedores std::vector std::deque y std::basic_string de la biblioteca estándar de C++), las plantillas de asignador funcionan correctamente, pero no es probable que proporcionen ninguna mejora de rendimiento con respecto al asignador predeterminado.  
  
 Un asignador es una clase de plantilla que describe un objeto que administra la asignación de almacenamiento y la liberación de objetos y matrices de objetos de un tipo designado. Los objetos de asignador son usados por varias clases de plantilla de contenedor de la biblioteca estándar de C++.  
  
 Los asignadores son todos plantillas de este tipo:  
  
 `template<class` `Type` `>`  
  
 `class allocator;`  
  
 donde el argumento de plantilla `Type` es el tipo administrado por la instancia de asignador. La biblioteca estándar de C++ proporciona un asignador predeterminado, la clase de plantilla [allocator](../standard-library/allocator-class.md), que se define en [\<memory>](../standard-library/memory.md). El encabezado \<allocators> proporciona los asignadores siguientes:  
  
- [allocator_newdel](../standard-library/allocator-newdel-class.md)  
  
- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)  
  
- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)  
  
- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)  
  
- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)  
  
- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)  
  
 Use una creación de instancias adecuada de un asignador como segundo argumento de tipo al crear un contenedor, como en el ejemplo de código siguiente.  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;`  
  
 _List0 asigna nodos con `allocator_chunklist` y el filtro de sincronización predeterminado.  
  
 Use la macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) para crear plantillas de asignador con filtros de sincronización que no sean los predeterminados:  
  
 `#include <list>`  
  
 `#include <allocators>`  
  
 `ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);`  
  
 `std::list<int, alloc<int> > _List1;`  
  
 _Lst1 asigna nodos con `allocator_chunklist` y el filtro de sincronización [sync_per_thread](../standard-library/sync-per-thread-class.md).  
  
 Un asignador de bloques es una memoria caché o un filtro. Una memoria caché es una clase de plantilla que toma un argumento de tipo std::size_t. Define un asignador de bloques que asigna y desasigna bloques de memoria de un tamaño único. Debe obtener memoria mediante el operador `new`, pero no necesita realizar una llamada independiente al operador `new` para cada bloque. Por ejemplo, puede subasignar desde un bloque mayor o almacenar en caché bloques desasignados para una reasignación posterior.  
  
 Con un compilador que no puede compilar el reenlace, el valor del argumento std:: size_t empleado al crear una instancia de la plantilla no es necesariamente el valor del argumento _Sz pasado a las funciones miembro allocate y deallocate de una memoria caché.  
  
 \<allocators> proporciona las siguientes plantillas de caché:  
  
- [cache_freelist](../standard-library/cache-freelist-class.md)  
  
- [cache_suballoc](../standard-library/cache-suballoc-class.md)  
  
- [cache_chunklist](../standard-library/cache-chunklist-class.md)  
  
 Un filtro es un asignador de bloques que implementa sus funciones miembro mediante otro asignador de bloques que se le pasa como un argumento de plantilla. La forma más común de filtro es un filtro de sincronización, que aplica una directiva de sincronización para controlar el acceso a las funciones miembro de una instancia de otro asignador de bloques. \<allocators> proporciona los siguientes filtros de sincronización:  
  
- [sync_none](../standard-library/sync-none-class.md)  
  
- [sync_per_container](../standard-library/sync-per-container-class.md)  
  
- [sync_per_thread](../standard-library/sync-per-thread-class.md)  
  
- [sync_shared](../standard-library/sync-shared-class.md)  
  
 \<allocators> también proporciona el filtro [rts_alloc](../standard-library/rts-alloc-class.md), que contiene varias instancias del asignador de bloques y determina la instancia que se va a usar para la asignación o desasignación en tiempo de ejecución, y no en tiempo de compilación. Se usa con los compiladores que no se pueden reenlazar mediante compilación.  
  
 Una directiva de sincronización determina cómo controla una instancia de asignador las solicitudes de asignación y desasignación simultáneas desde varios subprocesos. La directiva más sencilla es pasar todas las solicitudes directamente al objeto de caché subyacente, dejando la administración de la sincronización al usuario. Una directiva más compleja podría consistir en usar una exclusión mutua para serializar el acceso al objeto de caché subyacente.  
  
 Si un compilador admite la compilación de aplicaciones de un único subproceso y de varios, el filtro de sincronización predeterminado para las aplicaciones de un único subproceso es `sync_none`; en todos los demás casos, es `sync_shared`.  
  
 La plantilla caché `cache_freelist` toma un argumento de clase máxima que determina el número máximo de elementos que se van a almacenar en la lista libre.  
  
 \<allocators> proporciona las siguientes clases máximas:  
  
- [max_none](../standard-library/max-none-class.md)  
  
- [max_unbounded](../standard-library/max-unbounded-class.md)  
  
- [max_fixed_size](../standard-library/max-fixed-size-class.md)  
  
- [max_variable_size](../standard-library/max-variable-size-class.md)  
  
### <a name="macros"></a>Macros  
  
|||  
|-|-|  
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Da como resultado una clase de plantilla de asignador.|  
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Produce `stdext::allocators::cache_chunklist<sizeof(Type)>`.|  
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|Produce `stdext::allocators::cache_freelist<sizeof(Type), max>`.|  
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|Produce `stdext::allocators::cache_suballoc<sizeof(Type)>`.|  
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Da como resultado un filtro de sincronización.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator!= (\<allocators>)](../standard-library/allocators-operators.md#op_neq)|Comprueba la desigualdad entre los objetos de asignador de una clase especificada.|  
|[operator== (\<allocators>)](../standard-library/allocators-operators.md#op_eq_eq)|Comprueba la igualdad entre los objetos de asignador de una clase especificada.|  
  
### <a name="classes"></a>Clases  
  
|||  
|-|-|  
|[allocator_base](../standard-library/allocator-base-class.md)|Define la clase base y las funciones comunes necesarias para crear un asignador definido por el usuario a partir de un filtro de sincronización.|  
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos mediante una memoria caché de tipo [cache_chunklist](../standard-library/cache-chunklist-class.md).|  
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo `Type` mediante una memoria caché de tipo [cache_freelist](../standard-library/cache-freelist-class.md) con una longitud administrada por [max_fixed_size](../standard-library/max-fixed-size-class.md).|  
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementa un asignador que usa `operator delete` para desasignar un bloque de memoria y `operator new` para asignar un bloque de memoria.|  
|[allocator_suballoc](../standard-library/allocator-suballoc-class.md)|Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo `Type` mediante una memoria caché de tipo [cache_suballoc](../standard-library/cache-suballoc-class.md).|  
|[allocator_unbounded](../standard-library/allocator-unbounded-class.md)|Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo `Type` mediante una memoria caché de tipo [cache_freelist](../standard-library/cache-freelist-class.md) con una longitud administrada por [max_unbounded](../standard-library/max-unbounded-class.md).|  
|[allocator_variable_size](../standard-library/allocator-variable-size-class.md)|Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo `Type` mediante una memoria caché de tipo [cache_freelist](../standard-library/cache-freelist-class.md) con una longitud administrada por [max_variable_size](../standard-library/max-variable-size-class.md).|  
|[cache_chunklist](../standard-library/cache-chunklist-class.md)|Define un asignador de bloques que asigna y desasigna bloques de memoria de un tamaño único.|  
|[cache_freelist](../standard-library/cache-freelist-class.md)|Define un asignador de bloques que asigna y desasigna bloques de memoria de un tamaño único.|  
|[cache_suballoc](../standard-library/cache-suballoc-class.md)|Define un asignador de bloques que asigna y desasigna bloques de memoria de un tamaño único.|  
|[freelist](../standard-library/freelist-class.md)|Administra una lista de bloques de memoria.|  
|[max_fixed_size](../standard-library/max-fixed-size-class.md)|Describe un objeto de clase máxima que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima fija.|  
|[max_none](../standard-library/max-none-class.md)|Describe un objeto de clase máxima que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima de cero.|  
|[max_unbounded](../standard-library/max-unbounded-class.md)|Describe un objeto de clase máxima que no limita la longitud máxima de un objeto [freelist](../standard-library/freelist-class.md).|  
|[max_variable_size](../standard-library/max-variable-size-class.md)|Describe un objeto de clase máxima que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima que es aproximadamente proporcional al número de bloques de memoria asignados.|  
|[rts_alloc](../standard-library/rts-alloc-class.md)|La clase de plantilla rts_alloc describe un [filtro](../standard-library/allocators-header.md) que contiene una matriz de instancias de caché y determina la instancia que se va a usar para la asignación y la desasignación en tiempo de ejecución, y no en tiempo de compilación.|  
|[sync_none](../standard-library/sync-none-class.md)|Describe un filtro de sincronización que no proporciona ninguna sincronización.|  
|[sync_per_container](../standard-library/sync-per-container-class.md)|Describe un filtro de sincronización que proporciona un objeto de caché independiente para cada objeto de asignador.|  
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Describe un filtro de sincronización que proporciona un objeto de caché independiente para cada subproceso.|  
|[sync_shared](../standard-library/sync-shared-class.md)|Describe un filtro de sincronización que usa una exclusión mutua para controlar el acceso a un objeto de caché compartido por todos los asignadores.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
## <a name="see-also"></a>Vea también  
 [Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)



