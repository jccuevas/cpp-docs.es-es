---
title: '&lt;memory&gt;'
ms.date: 04/04/2019
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: 7c30a44de70675af69648fdba79325a173ab62fc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451889"
---
# <a name="ltmemorygt"></a>&lt;memory&gt;

Define una clase, un operador y varias plantillas que sirven de ayuda para asignar y liberar objetos.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<memory>

**Espacio de nombres:** std

## <a name="members"></a>Miembros

### <a name="functions"></a>Funciones

|||
|-|-|
|[addressof](../standard-library/memory-functions.md#addressof)|Obtiene la dirección real de un objeto.|
|[align](../standard-library/memory-functions.md#align)|Devuelve un puntero a un intervalo de tamaño determinado, en función de la alineación y la dirección inicial proporcionadas,|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|Crea un elemento `shared_ptr` en objetos asignados y construidos para un tipo determinado con un asignador especificado.|
|[atomic_compare_exchange_strong](../standard-library/memory-functions.md#atomic_compare_exchange_strong)||
|[atomic_compare_exchange_weak](../standard-library/memory-functions.md#atomic_compare_exchange_weak)||
|[atomic_compare_exchange_strong_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_strong_explicit)||
|[atomic_compare_exchange_weak_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_weak_explicit)||
|[atomic_exchange](../standard-library/memory-functions.md#atomic_exchange)||
|[atomic_exchange_explicit](../standard-library/memory-functions.md#atomic_exchange_explicit)||
|[atomic_is_lock_free](../standard-library/memory-functions.md#atomic_is_lock_free)||
|[atomic_load](../standard-library/memory-functions.md#atomic_load)||
|[atomic_load_explicit](../standard-library/memory-functions.md#atomic_load_explicit)||
|[atomic_store](../standard-library/memory-functions.md#atomic_store)||
|[atomic_store_explicit](../standard-library/memory-functions.md#atomic_store_explicit)||
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|Const convertida en `shared_ptr`.|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|Informa a un recolector de elementos no utilizados de que los caracteres que empiezan en una dirección especificada y entran en el tamaño de bloque indicado no contienen punteros rastreables.|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|Informa a la recolección de elementos no utilizados de que la dirección indicada es para el almacenamiento asignado y es accesible.|
|[default_delete](../standard-library/memory-functions.md#default_delete)|Elimina objetos asignados a `operator new`. Apto para el uso con `unique_ptr`.|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|Método `destroy` abreviado.|
|[destroy](../standard-library/memory-functions.md#destroy)|Método `destroy` abreviado.|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|Método `destroy` abreviado.|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|Conversión dinámica en `shared_ptr`.|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|Obtiene el delimitador de `shared_ptr`.|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|Devuelve el tipo de seguridad del puntero asumido por cualquier recolector de elementos no utilizados.|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|Asigna almacenamiento temporal para una secuencia de elementos que no supere un número especificado de elementos.|
|[make_shared](../standard-library/memory-functions.md#make_shared)|Crea y devuelve un `shared_ptr` que señala al objeto asignado construido sin argumentos o con algún argumento mediante el asignador predeterminado.|
|[make_unique](../standard-library/memory-functions.md#make_unique)|Crea y devuelve un elemento [unique_ptr](../standard-library/unique-ptr-class.md) que señala al objeto asignado construido desde cero o con algún argumento.|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|Una enumeración de todos los valores devueltos posibles para `get_pointer_safety`.|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|Desasigna la memoria temporal que se asignó mediante la función de plantilla `get_temporary_buffer`.|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|Conversión estática en `shared_ptr`.|
|[swap](../standard-library/memory-functions.md#swap)|Intercambia dos objetos `shared_ptr` o `weak_ptr`.|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|Informa a un recolector de elementos no utilizados de que los caracteres del bloque de memoria definido por un puntero de dirección base y el tamaño del bloque pueden contener ahora punteros rastreables.|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|Informa a `garbage_collector` de que una ubicación de memoria especificada es inaccesible.|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|Copia objetos de un intervalo de entrada especificado en un intervalo de destino sin inicializar.|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|Crea una copia de un número especificado de elementos de un iterador de entrada. Las copias se colocan en un iterador hacia delante.|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|Método `uninitialized_default_construct` abreviado.|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|Método `uninitialized_construct` abreviado.|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|Copia objetos de un valor especificado en un intervalo de destino sin inicializar.|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|Copia objetos de un valor especificado en un número especificado de elementos de un intervalo de destino sin inicializar.|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|Método `uninitialized_move` abreviado.|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|Método `uninitialized_move` abreviado.|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|Método `uninitialized_value_construct` abreviado.|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|Método `uninitialized_value_construct` abreviado.|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|Comprueba la desigualdad entre los objetos de asignador de una clase especificada.|
|[operator==](../standard-library/memory-operators.md#op_eq_eq)|Comprueba la igualdad entre los objetos de asignador de una clase especificada.|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|Comprueba si un objeto de asignador es mayor o igual que un segundo objeto de asignador de una clase especificada.|
|[operator<](../standard-library/memory-operators.md#op_lt)|Comprueba si un objeto es menor que un segundo objeto de una clase especificada.|
|[operator\<=](../standard-library/memory-operators.md#op_gt_eq)|Comprueba si un objeto es menor o igual que un segundo objeto de una clase especificada.|
|[operator>](../standard-library/memory-operators.md#op_gt)|Comprueba si un objeto es mayor que un segundo objeto de una clase especificada.|
|[operator<<](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` inserter.|

### <a name="classes"></a>Clases

|||
|-|-|
|[allocator](../standard-library/allocator-class.md)|La clase de plantilla describe un objeto que administra la asignación de almacenamiento y la liberación de las matrices de objetos de tipo **Type**.|
|[allocator_traits](../standard-library/allocator-traits-class.md)|Describe un objeto que determina toda la información que necesita un contenedor habilitado como asignador.|
|[auto_ptr](../standard-library/auto-ptr-class.md)|La clase de plantilla describe un objeto que almacena un puntero a un objeto asignado de tipo **Type** <strong>\*</strong> que garantiza que el objeto al que señala se elimina cuando se destruye su auto_ptr contenedor.|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|Informa de una excepción weak_ptr errónea.|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|Ayuda a generar un `shared_ptr`.|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|Proporciona información que necesita un objeto de clase de plantilla `allocator_traits` para describir un asignador con el tipo de puntero `Ptr`.|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|Una clase de adaptador que se proporciona para permitir que los algoritmos almacenen sus resultados en memoria sin inicializar.|
|[shared_ptr](../standard-library/shared-ptr-class.md)|Encapsula un puntero inteligente en el que se cuentan las referencias alrededor de un objeto asignado dinámicamente.|
|[unique_ptr](../standard-library/unique-ptr-class.md)|Almacena un puntero a un objeto en propiedad. El puntero únicamente es propiedad de `unique_ptr`. Se destruye `unique_ptr` cuando se destruye el propietario.|
|[weak_ptr](../standard-library/weak-ptr-class.md)|Contiene un puntero débilmente vinculado.|

### <a name="structures"></a>Estructuras

|||
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|[hash]()||
|[owner_less](../standard-library/memory-functions.md#owner_less)|Permite realizar comparaciones mixtas basadas en la propiedad de punteros compartidos y parciales.|
|[uses_allocator](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>Especializaciones

|||
|-|-|
|[allocator\<void>](../standard-library/allocator-void-class.md)|Una especialización del asignador de la clase de plantilla para el tipo void, que define los únicos tipos miembro que tienen sentido en este contexto especializado.|

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
