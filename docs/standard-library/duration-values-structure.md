---
title: duration_values (Estructura)
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: bc382bbc408b11cbc18210f3ab944dda39adc8f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653393"
---
# <a name="durationvalues-structure"></a>duration_values (Estructura)

Proporciona valores concretos para el parámetro de plantilla [duration](../standard-library/duration-class.md) `Rep`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[max](#max)|Estático. Especifica el límite superior para un valor de tipo `Rep`.|
|[min](#min)|Estático. Especifica el límite inferior para un valor de tipo `Rep`.|
|[cero](#zero)|Estático. Devuelve `Rep(0)`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<chrono >

**Espacio de nombres:** std::chrono

## <a name="max"></a>  duration_values::max

Método estático que devuelve el límite superior para los valores de tipo `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Comentarios

Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe ser mayor que [duration_values::zero](#zero).

## <a name="min"></a>  duration_values::min

Método estático que devuelve el límite inferior para valores de tipo `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Comentarios

Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe ser menor o igual que [duration_values::zero](#zero).

## <a name="zero"></a>  duration_values::zero

Devuelve `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Comentarios

Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe representar el infinito aditivo.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
