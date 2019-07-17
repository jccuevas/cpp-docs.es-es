---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: b5957412d2beff0dc709dc71a77834f13eeacb41
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269347"
---
# <a name="ltmemoryresourcegt"></a>&lt;memory_resource&gt;

Define el memory_resource de clase de plantilla de contenedor y sus plantillas auxiliares.

## <a name="syntax"></a>Sintaxis

```cpp
#include <memory_resource>
```

## <a name="members"></a>Miembros

### <a name="operators"></a>Operadores

|||
|-|-|
|[operator!=](../standard-library/memory-resource-operators.md#op_neq)|Comprueba si el objeto memory_resource en el lado izquierdo del operador no es igual al objeto memory_resource en el lado derecho.|
|[operator==](../standard-library/memory-resource-operators.md#op_eq_eq)|Comprueba si el objeto memory_resource en el lado izquierdo del operador es igual al objeto memory_resource en el lado derecho.|

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
|[pool_options Struct](../standard-library/pool-options-structure.md)||
|[Clase synchronized_pool_resource](../standard-library/synchronized-pool-resource-class.md)||
|[Clase unsynchronized_pool_resource](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
