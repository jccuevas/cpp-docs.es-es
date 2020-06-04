---
title: duration_values (Estructura)
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::duration_values
- chrono/std::chrono::duration_values::max
- chrono/std::chrono::duration_values::min
- chrono/std::chrono::duration_values::zero
ms.assetid: 7f66d2e3-1faf-47c3-b47e-08f2a87f20e8
ms.openlocfilehash: e2c03b4540ea5f89843562d1310b71635b3bc259
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368748"
---
# <a name="duration_values-structure"></a>duration_values (Estructura)

Proporciona valores concretos para el parámetro de plantilla [duration](../standard-library/duration-class.md)`Rep`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Rep>
struct duration_values;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[máximo](#max)|Estática. Especifica el límite superior para un valor de tipo `Rep`.|
|[Min](#min)|Estática. Especifica el límite inferior para un valor de tipo `Rep`.|
|[Cero](#zero)|Estática. Devuelve `Rep(0)`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<crono>

**Espacio de nombres:** std::chrono

## <a name="duration_valuesmax"></a><a name="max"></a>duration_values::max

Método estático que devuelve el límite superior para los valores de tipo `Ref`.

```cpp
static constexpr Rep max();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `numeric_limits<Rep>::max()`.

### <a name="remarks"></a>Observaciones

Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe ser mayor que [duration_values::zero](#zero).

## <a name="duration_valuesmin"></a><a name="min"></a>duration_values::min

Método estático que devuelve el límite inferior para valores de tipo `Ref`.

```cpp
static constexpr Rep min();
```

### <a name="return-value"></a>Valor devuelto

En efecto, devuelve `numeric_limits<Rep>::lowest()`.

### <a name="remarks"></a>Observaciones

Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe ser menor o igual que [duration_values::zero](#zero).

## <a name="duration_valueszero"></a><a name="zero"></a>duration_values::cero

Devuelve `Rep(0)`.

```cpp
static constexpr Rep zero();
```

### <a name="remarks"></a>Observaciones

Cuando `Rep` es un tipo definido por el usuario, el valor devuelto debe representar el infinito aditivo.

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<>crono](../standard-library/chrono.md)
