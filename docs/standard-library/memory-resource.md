---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: d4b25c6ee575191f1e17b0202d33298e2e9e67f0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451902"
---
# <a name="ltmemoryresourcegt"></a>&lt;memory_resource&gt;

Define la clase de plantilla de contenedor memory_resource y sus plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <memory_resource>
```

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|Comprueba si el objeto memory_resource del lado izquierdo del operador no es igual que el objeto memory_resource del lado derecho.|
|[operator==](../standard-library/memory-resource-operators.md#op_eq_eq)|Comprueba si el objeto memory_resource del lado izquierdo del operador es igual que el objeto memory_resource del lado derecho.|

### <a name="specialized-template-functions"></a>Funciones de plantilla especializadas

|||
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>Funciones

|||
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>Clases y structs

|||
|-|-|
|[Clase memory_resource](../standard-library/memory-resource-class.md)||
|[Clase monotonic_buffer_resource](../standard-library/monotonic-buffer-resource-class.md)||
|[Struct pool_options](../standard-library/pool-options-structure.md)||
|[Clase synchronized_pool_resource](../standard-library/synchronized-pool-resource-class.md)||
|[Clase unsynchronized_pool_resource](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
