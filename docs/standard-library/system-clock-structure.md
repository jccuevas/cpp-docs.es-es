---
title: system_clock (Estructura)
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: ca516551bb1b41d96b99aaf7b842666c9341ee7d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376511"
---
# <a name="system_clock-structure"></a>system_clock (Estructura)

Representa un *tipo de reloj* basado en el reloj en tiempo real del sistema.

## <a name="syntax"></a>Sintaxis

```cpp
struct system_clock;
```

## <a name="remarks"></a>Observaciones

Se usa un *tipo de reloj* para obtener la hora actual en formato UTC. El tipo personifica una creación de instancias de [duration](../standard-library/duration-class.md) y la plantilla de clase [time_point](../standard-library/time-point-class.md), y define una función miembro estática `now()` que devuelve la hora.

Un reloj es *monotónico* si el valor devuelto por la primera llamada a `now()` siempre es menor o igual que el valor devuelto por una llamada posterior a `now()`.

Un reloj es *constante* si es *monotónico* y si el tiempo entre los ciclos de reloj es constante.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|`system_clock::duration`|Sinónimo de `duration<rep, period>`.|
|`system_clock::period`|Sinónimo del tipo que se utiliza para representar el período de ciclo en la creación de instancias contenida de `duration`.|
|`system_clock::rep`|Sinónimo del tipo que se utiliza para representar el número de ciclos del reloj en la creación de instancias contenida de `duration`.|
|`system_clock::time_point`|Sinónimo de `time_point<Clock, duration>`, donde `Clock` es un sinónimo del tipo de reloj propiamente dicho o de otro tipo de reloj basado en la mismo tiempo base y tiene el mismo tipo `duration` anidado.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[from_time_t](#from_time_t)|Estática. Devuelve el `time_point` que más se aproxima a una hora especificada.|
|[Ahora](#now)|Estática. Devuelve la hora actual.|
|[to_time_t](#to_time_t)|Estática. Devuelve el objeto `time_t` que más se aproxima a un `time_point` especificado.|

### <a name="public-constants"></a>Constantes públicas

|Nombre|Descripción|
|----------|-----------------|
|[system_clock::is_monotonic (Constante)](#is_monotonic_constant)|Especifica si el tipo de reloj es monotónico.|
|[system_clock::is_steady (Constante)](#is_steady_constant)|Especifica si el tipo de reloj es constante.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<crono>

**Espacio de nombres:** std::chrono

## <a name="system_clockfrom_time_t"></a><a name="from_time_t"></a>system_clock::from_time_t

Método estático que devuelve un [time_point](../standard-library/time-point-class.md) que se aproxima más a la hora representada por *Tm*.

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>Parámetros

*Tm*\
Un objeto [time_t](../c-runtime-library/standard-types.md).

## <a name="system_clockis_monotonic-constant"></a><a name="is_monotonic_constant"></a>system_clock::is_monotonic Constante

Valor estático que especifica si el tipo del reloj es monotónico.

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>Valor devuelto

En esta `system_clock::is_monotonic` implementación, siempre devuelve **false**.

### <a name="remarks"></a>Observaciones

Un reloj es *monotónico* si el valor devuelto por la primera llamada a `now()` siempre es menor o igual que el valor devuelto por una llamada posterior a `now()`.

## <a name="system_clockis_steady-constant"></a><a name="is_steady_constant"></a>system_clock::is_steady Constante

Valor estático que especifica si el tipo del reloj es *constante*.

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>Valor devuelto

En esta `system_clock::is_steady` implementación, siempre devuelve **false**.

### <a name="remarks"></a>Observaciones

Un reloj es *constante* si es [monotónico](#is_monotonic_constant) y si el tiempo entre los ciclos de reloj es constante.

## <a name="system_clocknow"></a><a name="now"></a>system_clock::ahora

Método estático que devuelve la hora actual.

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>Valor devuelto

Un objeto [time_point](../standard-library/time-point-class.md) que representa la hora actual.

## <a name="system_clockto_time_t"></a><a name="to_time_t"></a>system_clock::to_time_t

Método estático que devuelve un [time_t](../c-runtime-library/standard-types.md) que se aproxima más a la hora representada por *Time*.

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>Parámetros

*hora*\
Un objeto [time_point](../standard-library/time-point-class.md).

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<>crono](../standard-library/chrono.md)\
[Struct steady_clock](../standard-library/steady-clock-struct.md)
