---
title: duration_values (Estructura)
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: ba4b202a5c8c6da742ac884bf58a5b8c55373d14
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454289"
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

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[max](#max)|Estático. Especifica el límite superior para un valor de tipo `Rep`.|
|[min](#min)|Estático. Especifica el límite inferior para un valor de tipo `Rep`.|
|[zero](#zero)|Estático. Devuelve `Rep(0)`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> crónico

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

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
