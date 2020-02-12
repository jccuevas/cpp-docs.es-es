---
title: Concurrency::graphics (Espacio de nombres)
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: c7e3b245c8d9e6ba0c563a63910fadd678523087
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139452"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics (Espacio de nombres)

El espacio de nombres Graphics proporciona tipos y funciones que están diseñados para la programación de gráficos.

## <a name="syntax"></a>Sintaxis

```cpp
namespace graphics;
```

## <a name="members"></a>Members

### <a name="namespaces"></a>Espacios de nombres

|Nombre|Descripción|
|----------|-----------------|
|[Concurrency::graphics::direct3d (espacio de nombres)](concurrency-graphics-direct3d-namespace.md)|Proporciona funciones para la interoperabilidad de Direct3D.|

### <a name="typedefs"></a>Typedefs

|Nombre|Descripción|
|----------|-----------------|
|`uint`|El tipo de elemento de [Uint_2 clase](uint-2-class.md), [uint_3 clase](uint-3-class.md)y [uint_4 clase](uint-4-class.md). Definido como `typedef unsigned int uint;`.|

### <a name="enumerations"></a>Enumeraciones

|Nombre|Descripción|
|----------|-----------------|
|[enumeración address_mode](concurrency-graphics-namespace-enums.md#address_mode).|Especifica modos de dirección compatibles para el muestreo de textura.|
|[Enumeración filter_mode](concurrency-graphics-namespace-enums.md#filter_mode)|Especifica los modos de filtro admitidos para el muestreo de textura.|

### <a name="classes"></a>Clases

|Nombre|Descripción|
|----------|-----------------|
|[texture (clase)](texture-class.md)|Una textura es un agregado de datos en un accelerator_view en el dominio de extensión. Es una colección de variables, una para cada elemento de un dominio de extensión. Cada variable contiene un valor que corresponde C++ al tipo primitivo (int sin signo, int, Float, Double) o a un tipo escalar norma, o unorm (definido en Concurrency:: Graphics) o tipos de vectores cortos válidos definidos en Concurrency:: Graphics.|
|[writeonly_texture_view (clase)](writeonly-texture-view-class.md)|Un writeonly_texture_view proporciona el acceso WriteOnly a una textura.|
|[double_2 (clase)](double-2-class.md)|Representa un vector corto de 2 `double` valores.|
|[double_3 (clase)](double-3-class.md)|Representa un vector corto de 3 `double` valores.|
|[double_4 (clase)](double-4-class.md)|Representa un vector corto de 4 `double` valores.|
|[float_2 (clase)](float-2-class.md)|Representa un vector corto de 2 `float` valores.|
|[float_3 (clase)](float-3-class.md)|Representa un vector corto de 3 `float` valores.|
|[float_4 (clase)](float-4-class.md)|Representa un vector corto de 4 `float` valores.|
|[int_2 (clase)](int-2-class.md)|Representa un vector corto de 2 `int` valores.|
|[int_3 (clase)](int-3-class.md)|Representa un vector corto de 3 `int` valores.|
|[int_4 (clase)](int-4-class.md)|Representa un vector corto de 4 `int` valores.|
|[norm_2 (clase)](norm-2-class.md)|Representa un vector corto de 2 `norm` valores.|
|[norm_3 (clase)](norm-3-class.md)|Representa un vector corto de 3 `norm` valores.|
|[norm_4 (clase)](norm-4-class.md)|Representa un vector corto de 4 `norm` valores.|
|[uint_2 (clase)](uint-2-class.md)|Representa un vector corto de 2 `uint` valores.|
|[uint_3 (clase)](uint-3-class.md)|Representa un vector corto de 3 `uint` valores.|
|[uint_4 (clase)](uint-4-class.md)|Representa un vector corto de 4 `uint` valores.|
|[unorm_2 (clase)](unorm-2-class.md)|Representa un vector corto de 2 `unorm` valores.|
|[unorm_3 (clase)](unorm-3-class.md)|Representa un vector corto de 3 `unorm` valores.|
|[unorm_4 (clase)](unorm-4-class.md)|Representa un vector corto de 4 `unorm` valores.|
|[sampler (clase)](sampler-class.md)|Representa la configuración de muestra utilizada para el muestreo de textura.|
|[short_vector (estructura)](short-vector-structure.md)|Proporciona una implementación básica de un vector corto de valores.|
|[short_vector_traits (estructura)](short-vector-traits-structure.md)|Permite recuperar la longitud y el tipo de un vector corto.|
|[texture_view (clase)](texture-view-class.md)|Proporciona acceso de lectura y acceso de escritura a una textura.|

### <a name="functions"></a>Functions

|Nombre|Descripción|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|Sobrecargado. Copia el contenido de la textura de origen en el búfer del host de destino.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Sobrecargado. Copia de forma asincrónica el contenido de la textura de origen en el búfer del host de destino.|

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics. h

**Espacio de nombres:** Concurrency

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
