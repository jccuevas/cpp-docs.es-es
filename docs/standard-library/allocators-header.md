---
title: '&lt;allocators&gt;'
ms.date: 11/04/2016
f1_keywords:
- <allocators>
helpviewer_keywords:
- allocators header
ms.assetid: 4393a607-4df8-4278-bbb2-c8ec52e60b83
ms.openlocfilehash: f6be154be68cd5e43fd6f934d88c04fb25be9dc5
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754450"
---
# <a name="ltallocatorsgt"></a>&lt;allocators&gt;

Define varias plantillas que ayudan a asignar y liberar bloques de memoria para contenedores basados en nodos.

## <a name="syntax"></a>Sintaxis

```cpp
#include <allocators>
```

> [!NOTE]
> \<> de asignadores está en desuso, a partir de Visual Studio 2019 versión 16.3.

## <a name="remarks"></a>Observaciones

El encabezado \<allocators> proporciona seis plantillas de asignador que se pueden usar para seleccionar estrategias de administración de memoria para los contenedores basados en nodos. Para su uso con estas plantillas, también proporciona varios filtros de sincronización diferentes para adaptar la estrategia de administración de memoria a una serie de esquemas multithreading distintos (incluso ninguno). Puede acelerar la aplicación o reducir sus requisitos de memoria haciendo coincidir una estrategia de administración de memoria con sus patrones de uso de memoria y requisitos de sincronización.

Las plantillas de asignador se implementan con componentes reutilizables que se pueden personalizar o reemplazar a fin de proporcionar estrategias de administración de memoria adicionales.

Los contenedores basados en nodos de la biblioteca estándar C++ (std::list, std::set, std::multiset, std::map y std::multimap) almacenan sus elementos en nodos individuales. Todos los nodos de un tipo de contenedor determinado tienen el mismo tamaño, por lo que no es necesaria la flexibilidad de un administrador de memoria de propósito general. Dado que se conoce el tamaño de cada bloque de memoria en tiempo de compilación, el administrador de memoria puede ser mucho más rápido y sencillo.

Cuando se utiliza con contenedores que no están basados en nodo (como los contenedores de la biblioteca estándar C++ std::vector std::deque y std::basic_string), las plantillas de asignador funcionarán correctamente, pero no es probable que proporcionen ninguna mejora de rendimiento con respecto al asignador predeterminado.

Un asignador es una plantilla de clase que describe un objeto que administra la asignación de almacenamiento y la liberación de objetos y matrices de objetos de un tipo designado. Varias plantillas de clase contenedora utilizan objetos de asignador en la biblioteca estándar de C++.

Los asignadores son todos plantillas de este tipo:

```cpp
template<class Type>
class allocator;
```

donde el argumento de plantilla `Type` es el tipo administrado por la instancia de asignador. La biblioteca estándar C++ proporciona un asignador predeterminado, [asignador](../standard-library/allocator-class.md)de plantilla de clase, que se define en [ \<la memoria>](../standard-library/memory.md). El encabezado \<allocators> proporciona los asignadores siguientes:

- [allocator_newdel](../standard-library/allocator-newdel-class.md)

- [allocator_unbounded](../standard-library/allocator-unbounded-class.md)

- [allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)

- [allocator_variable_size](../standard-library/allocator-variable-size-class.md)

- [allocator_suballoc](../standard-library/allocator-suballoc-class.md)

- [allocator_chunklist](../standard-library/allocator-chunklist-class.md)

Use una creación de instancias adecuada de un asignador como segundo argumento de tipo al crear un contenedor, como en el ejemplo de código siguiente.

```cpp
#include <list>
#include <allocators>
std::list<int, stdext::allocators::allocator_chunklist<int> > _List0;
```

_List0 asigna nodos con `allocator_chunklist` y el filtro de sincronización predeterminado.

Use la macro [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl) para crear plantillas de asignador con filtros de sincronización que no sean los predeterminados:

```cpp
#include <list>
#include <allocators>
ALLOCATOR_DECL(CACHE_CHUNKLIST, stdext::allocators::sync_per_thread, Alloc);
std::list<int, alloc<int> > _List1;
```

_Lst1 asigna nodos con `allocator_chunklist` y el filtro de sincronización [sync_per_thread](../standard-library/sync-per-thread-class.md).

Un asignador de bloques es una memoria caché o un filtro. Una memoria caché es una plantilla de clase que toma un argumento de tipo std::size_t. Define un asignador de bloques que asigna y desasigna bloques de memoria de un tamaño único. Debe obtener memoria mediante el operador **new**, pero no es necesario realizar una llamada independiente al operador **new** para cada bloque. Por ejemplo, puede subasignar desde un bloque mayor o almacenar en caché bloques desasignados para una reasignación posterior.

Con un compilador que no puede volver a enlazar el valor del argumento std::size_t utilizado cuando se crea una instancia de la plantilla no es necesariamente el valor del argumento _Sz pasa a las funciones miembro de una memoria caché asignar y desasignar.

\<allocators> proporciona las siguientes plantillas de caché:

- [cache_freelist](../standard-library/cache-freelist-class.md)

- [cache_suballoc](../standard-library/cache-suballoc-class.md)

- [cache_chunklist](../standard-library/cache-chunklist-class.md)

Un filtro es un asignador de bloques que implementa sus funciones miembro mediante otro asignador de bloques, que se le pasa como argumento de plantilla. La forma más común de filtro es un filtro de sincronización, que aplica una directiva de sincronización para controlar el acceso a las funciones miembro de una instancia de otro asignador de bloques. \<allocators> proporciona los siguientes filtros de sincronización:

- [sync_none](../standard-library/sync-none-class.md)

- [sync_per_container](../standard-library/sync-per-container-class.md)

- [sync_per_thread](../standard-library/sync-per-thread-class.md)

- [sync_shared](../standard-library/sync-shared-class.md)

\<allocators> también proporciona el filtro [rts_alloc](../standard-library/rts-alloc-class.md), que contiene varias instancias del asignador de bloques y determina la instancia que se va a usar para la asignación o desasignación en tiempo de ejecución, y no en tiempo de compilación. Se usa con los compiladores que no se pueden reenlazar mediante compilación.

Una directiva de sincronización determina cómo controla una instancia de asignador las solicitudes de asignación y desasignación simultáneas desde varios subprocesos. La directiva más sencilla es pasar todas las solicitudes directamente al objeto de caché subyacente, dejando la administración de la sincronización al usuario. Una directiva más compleja podría consistir en usar una exclusión mutua para serializar el acceso al objeto de caché subyacente.

Si un compilador admite la compilación de aplicaciones de un único subproceso y de varios, el filtro de sincronización predeterminado para las aplicaciones de un único subproceso es `sync_none`; en todos los demás casos, es `sync_shared`.

La plantilla `cache_freelist` de caché toma un argumento de clase max, que determina el número máximo de elementos que se almacenarán en la lista gratuita.

\<allocators> proporciona las siguientes clases máximas:

- [max_none](../standard-library/max-none-class.md)

- [max_unbounded](../standard-library/max-unbounded-class.md)

- [max_fixed_size](../standard-library/max-fixed-size-class.md)

- [max_variable_size](../standard-library/max-variable-size-class.md)

### <a name="macros"></a>Macros

|Macro|Descripción|
|-|-|
|[ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)|Produce una plantilla de clase de asignador.|
|[CACHE_CHUNKLIST](../standard-library/allocators-functions.md#cache_chunklist)|Produce `stdext::allocators::cache_chunklist<sizeof(Type)>`.|
|[CACHE_FREELIST](../standard-library/allocators-functions.md#cache_freelist)|Produce `stdext::allocators::cache_freelist<sizeof(Type), max>`.|
|[CACHE_SUBALLOC](../standard-library/allocators-functions.md#cache_suballoc)|Produce `stdext::allocators::cache_suballoc<sizeof(Type)>`.|
|[SYNC_DEFAULT](../standard-library/allocators-functions.md#sync_default)|Da como resultado un filtro de sincronización.|

### <a name="operators"></a>Operadores

|Operator|Descripción|
|-|-|
|[operador! (\<asignadores>)](../standard-library/allocators-operators.md#op_neq)|Comprueba la desigualdad entre los objetos de asignador de una clase especificada.|
|[operator== (\<allocators>)](../standard-library/allocators-operators.md#op_eq_eq)|Comprueba la igualdad entre los objetos de asignador de una clase especificada.|

### <a name="classes"></a>Clases

|Clase|Descripción|
|-|-|
|[allocator_base](../standard-library/allocator-base-class.md)|Define la clase base y las funciones comunes necesarias para crear un asignador definido por el usuario a partir de un filtro de sincronización.|
|[allocator_chunklist](../standard-library/allocator-chunklist-class.md)|Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos mediante una memoria caché de tipo [cache_chunklist](../standard-library/cache-chunklist-class.md).|
|[allocator_fixed_size](../standard-library/allocator-fixed-size-class.md)|Describe un objeto que administra la asignación de almacenamiento y la liberación de objetos de tipo `Type` mediante una memoria caché de tipo [cache_freelist](../standard-library/cache-freelist-class.md) con una longitud administrada por [max_fixed_size](../standard-library/max-fixed-size-class.md).|
|[allocator_newdel](../standard-library/allocator-newdel-class.md)|Implementa un asignador que utiliza **operator delete** para desasignar un bloque de memoria y un **operador new** para asignar un bloque de memoria.|
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
|[max_variable_size](../standard-library/max-variable-size-class.md)|Describe un objeto de clase máxima que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima que es aproximadamente proporcional al número de bloques de memoria asignada.|
|[rts_alloc](../standard-library/rts-alloc-class.md)|La plantilla de clase rts_alloc describe un [filtro](../standard-library/allocators-header.md) que contiene una matriz de instancias de caché y determina qué instancia se va a utilizar para la asignación y desasignación en tiempo de ejecución en lugar de en tiempo de compilación.|
|[sync_none](../standard-library/sync-none-class.md)|Describe un filtro de sincronización que no proporciona ninguna sincronización.|
|[sync_per_container](../standard-library/sync-per-container-class.md)|Describe un filtro de sincronización que proporciona un objeto de caché independiente para cada objeto de asignador.|
|[sync_per_thread](../standard-library/sync-per-thread-class.md)|Describe un filtro de sincronización que proporciona un objeto de caché independiente para cada subproceso.|
|[sync_shared](../standard-library/sync-shared-class.md)|Describe un filtro de sincronización que usa una exclusión mutua para controlar el acceso a un objeto de caché compartido por todos los asignadores.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<allocators>

**Espacio de nombres:** stdext

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
