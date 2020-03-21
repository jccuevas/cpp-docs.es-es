---
title: Definiciones de tipo &lt;new&gt;
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 30bd84a1d69d3d8f24cd36450a18b23b92c3c2c6
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076424"
---
# <a name="ltnewgt-typedefs"></a>Definiciones de tipo &lt;new&gt;

## <a name="hardware_constructive_interference_size"></a><a name="hardware_constructive_interference_size"></a>hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Observaciones

Este número es el tamaño recomendado máximo de la memoria contigua ocupada por dos objetos a los que se tiene acceso con una ubicación temporal mediante subprocesos simultáneos. Debe ser al menos `alignof(max_align_t)`.

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

## <a name="hardware_destructive_interference_size"></a><a name="hardware_destructive_interference_size"></a>hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Observaciones

Este número es el desplazamiento mínimo recomendado entre dos objetos de acceso simultáneo para evitar una degradación del rendimiento adicional debido a la contención introducida por la implementación. Debe ser al menos `alignof(max_align_t)`.

### <a name="example"></a>Ejemplo

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a><a name="new_handler"></a>new_handler

El tipo que apunta a una función que se puede usar como un controlador nuevo.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Observaciones

El **operador New** o `operator new[]` llama a este tipo de función de controlador cuando no pueden satisfacer una solicitud de almacenamiento adicional.

### <a name="example"></a>Ejemplo

Vea [set_new_handler](../standard-library/new-functions.md#set_new_handler) para obtener un ejemplo que usa `new_handler` como un valor devuelto.
