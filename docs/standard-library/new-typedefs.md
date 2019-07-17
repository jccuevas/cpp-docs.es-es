---
title: Definiciones de tipo &lt;new&gt;
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245159"
---
# <a name="ltnewgt-typedefs"></a>Definiciones de tipo &lt;new&gt;

## <a name="hardware_constructive_interference_size"></a> hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Comentarios

Este número es el máximo recomendado de tamaño de memoria contigua ocupada por dos objetos con localidad temporal accediendo a subprocesos simultáneos. Deberá ser al menos `alignof(max_align_t)`.

### <a name="example"></a>Ejemplo

```cpp
struct together { 
    atomic<int> dog;
    int puppy;
};

struct kennel {
    // Other data members...
    alignas(sizeof(together)) together pack;
    // Other data members...
};

static_assert(sizeof(together) <= hardware_constructive_interference_size);
```

## <a name="hardware_destructive_interference_size"></a> hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Comentarios

Este número es el desplazamiento mínimo recomendado entre dos objetos tenga acceso simultáneo a evitar la degradación del rendimiento adicional debido a la contención introducido por la implementación. Deberá ser al menos `alignof(max_align_t)`.

### <a name="example"></a>Ejemplo

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a> new_handler

El tipo que apunta a una función que se puede usar como un controlador nuevo.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Comentarios

Llama a este tipo de función de controlador **new (operador)** o `operator new[]` cuando no pueden satisfacer una solicitud de almacenamiento adicional.

### <a name="example"></a>Ejemplo

Vea [set_new_handler](../standard-library/new-functions.md#set_new_handler) para obtener un ejemplo que usa `new_handler` como un valor devuelto.
