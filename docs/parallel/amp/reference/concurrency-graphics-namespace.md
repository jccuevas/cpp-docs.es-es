---
title: 'Concurrency:: Graphics Namespace | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- AMP_GRAPHICS/Concurrency
dev_langs:
- C++
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31abd263f2536d0f2e73a3dfb35cad0eaa29e818
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387203"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics (Espacio de nombres)

El espacio de nombres de gráficos proporciona tipos y funciones que están diseñadas para la programación de gráficos.

## <a name="syntax"></a>Sintaxis

```
namespace graphics;
```

## <a name="members"></a>Miembros

### <a name="namespaces"></a>Espacios de nombres

|Name|Descripción|
|----------|-----------------|
|[Concurrency::graphics::direct3d (espacio de nombres)](concurrency-graphics-direct3d-namespace.md)|Proporciona funciones para la interoperabilidad de Direct3D.|

### <a name="typedefs"></a>Typedefs

|Name|Descripción|
|----------|-----------------|
|`uint`|El tipo de elemento para [uint_2 (clase)](uint-2-class.md), [uint_3 (clase)](uint-3-class.md), y [uint_4 (clase)](uint-4-class.md). Definido como `typedef unsigned int uint;`.|

### <a name="enumerations"></a>Enumeraciones

|nombre|Descripción|
|----------|-----------------|
|[address_mode (enumeración)](concurrency-graphics-namespace-enums.md#address_mode).|Especifica los modos de dirección compatibles para el muestreo de textura.|
|[filter_mode (enumeración)](concurrency-graphics-namespace-enums.md#filter_mode)|Especifica los modos de filtro compatibles para el muestreo de textura.|

### <a name="classes"></a>Clases

|Name|Descripción|
|----------|-----------------|
|[texture (clase)](texture-class.md)|Una textura es un agregado en un accelerator_view en el dominio de la extensión de datos. Es una colección de variables, uno para cada elemento en un dominio de la extensión. Cada variable contiene un valor que corresponde al tipo primitivo de C++ (unsigned int, int, float, double), o la norma de tipo escalar, o unorm (definido en Concurrency:: Graphics) o tipos elegible de vectores cortos definen en Concurrency:: Graphics.|
|[writeonly_texture_view (clase)](writeonly-texture-view-class.md)|Un writeonly_texture_view proporciona acceso de solo escritura a una textura.|
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
|[short_vector_traits (estructura)](short-vector-traits-structure.md)|Permite la recuperación de la longitud y el tipo de un vector corto.|
|[texture_view (clase)](texture-view-class.md)|Proporciona acceso de lectura y escritura a una textura.|

### <a name="functions"></a>Funciones

|Name|Descripción|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|Sobrecargado. Copia el contenido de la textura de origen en el búfer de host de destino.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Sobrecargado. Copia el contenido de la textura de origen en el búfer de host de destino de forma asincrónica.|

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_graphics.h

**Espacio de nombres:** Concurrency

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
