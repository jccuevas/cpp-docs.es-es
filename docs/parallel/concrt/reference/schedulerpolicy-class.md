---
title: SchedulerPolicy (clase)
ms.date: 11/04/2016
f1_keywords:
- SchedulerPolicy
- concrt/concurrency::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::SchedulerPolicy
- concrt/concurrency::SchedulerPolicy::GetPolicyValue
- concrt/concurrency::SchedulerPolicy::SetConcurrencyLimits
- concrt/concurrency::SchedulerPolicy::SetPolicyValue
helpviewer_keywords:
- SchedulerPolicy class
ms.assetid: bcebf51a-65f8-45a3-809b-d1ff93527dc4
ms.openlocfilehash: fed33c198502b75e824bcaf698227d283f4b85f9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142747"
---
# <a name="schedulerpolicy-class"></a>SchedulerPolicy (clase)

La clase `SchedulerPolicy` contiene un conjunto de pares clave-valor, uno para cada elemento de directiva, que controla el comportamiento de una instancia del programador.

## <a name="syntax"></a>Sintaxis

```cpp
class SchedulerPolicy;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[SchedulerPolicy](#ctor)|Sobrecargado. Construye una nueva Directiva del programador y la rellena con valores para [las claves de directiva](concurrency-namespace-enums.md) admitidas por los programadores de Runtime de simultaneidad y el administrador de recursos.|
|[~ SchedulerPolicy (destructor)](#dtor)|Destruye una directiva de programador.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[GetPolicyValue (](#getpolicyvalue)|Recupera el valor de la clave de directiva proporcionado como el parámetro `key`.|
|[Setconcurrencylimits (](#setconcurrencylimits)|Simultáneamente establece las directivas `MinConcurrency` y `MaxConcurrency` en el objeto `SchedulerPolicy`.|
|[Setpolicyvalue (](#setpolicyvalue)|Establece el valor de la clave de directiva proporcionado como el parámetro `key` y devuelve el valor anterior.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operator=](#operator_eq)|Asigna la directiva de programador a partir de otra directiva de programador.|

## <a name="remarks"></a>Observaciones

Para obtener más información sobre las directivas que se pueden controlar mediante la clase `SchedulerPolicy`, vea [policyelementkey (](concurrency-namespace-enums.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`SchedulerPolicy`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrt. h, concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="getpolicyvalue"></a>GetPolicyValue (

Recupera el valor de la clave de directiva proporcionado como el parámetro `key`.

```cpp
unsigned int GetPolicyValue(PolicyElementKey key) const;
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave de directiva para la que se va a recuperar un valor.

### <a name="return-value"></a>Valor devuelto

Si se admite la clave especificada por el parámetro `key`, el valor de la Directiva para la clave se convierte en un `unsigned int`.

### <a name="remarks"></a>Observaciones

El método producirá [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) para una clave de Directiva no válida.

## <a name="operator_eq"></a>operador =

Asigna la directiva de programador a partir de otra directiva de programador.

```cpp
SchedulerPolicy& operator= (const SchedulerPolicy& _RhsPolicy);
```

### <a name="parameters"></a>Parámetros

*_RhsPolicy*<br/>
Directiva que se va a asignar a esta Directiva.

### <a name="return-value"></a>Valor devuelto

Referencia a la Directiva del programador.

### <a name="remarks"></a>Observaciones

A menudo, la manera más conveniente de definir una nueva directiva del programador es copiar una directiva existente y modificarla mediante los métodos `SetPolicyValue` o `SetConcurrencyLimits`.

## <a name="ctor"></a>SchedulerPolicy

Construye una nueva Directiva del programador y la rellena con valores para [las claves de directiva](concurrency-namespace-enums.md) admitidas por los programadores de Runtime de simultaneidad y el administrador de recursos.

```cpp
SchedulerPolicy();

SchedulerPolicy(
    size_t _PolicyKeyCount,
...);

SchedulerPolicy(
    const SchedulerPolicy& _SrcPolicy);
```

### <a name="parameters"></a>Parámetros

*_PolicyKeyCount*<br/>
El número de pares clave-valor que sigue al parámetro `_PolicyKeyCount`.

*_SrcPolicy*<br/>
La directiva de origen que se va a copiar.

### <a name="remarks"></a>Observaciones

El primer constructor crea una nueva directiva de programador donde todas las directivas se inicializarán en sus valores predeterminado.

El segundo constructor crea una nueva directiva del programador que usa un estilo de inicialización de parámetro con nombre. Los valores que aparecen después del parámetro `_PolicyKeyCount` se proporcionan como pares clave-valor. Cualquier clave de directiva que no se especifique en este constructor tendrá su valor predeterminado. Este constructor podría producir las excepciones [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md), [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) o [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md).

El tercer constructor es un constructor de copias. A menudo, la manera más conveniente de definir una nueva directiva del programador es copiar una directiva existente y modificarla mediante los métodos `SetPolicyValue` o `SetConcurrencyLimits`.

## <a name="dtor"></a>~ SchedulerPolicy

Destruye una directiva de programador.

```cpp
~SchedulerPolicy();
```

## <a name="setconcurrencylimits"></a>Setconcurrencylimits (

Simultáneamente establece las directivas `MinConcurrency` y `MaxConcurrency` en el objeto `SchedulerPolicy`.

```cpp
void SetConcurrencyLimits(
    unsigned int _MinConcurrency,
    unsigned int _MaxConcurrency = MaxExecutionResources);
```

### <a name="parameters"></a>Parámetros

*_MinConcurrency*<br/>
Valor de la clave de directiva de `MinConcurrency`.

*_MaxConcurrency*<br/>
Valor de la clave de directiva de `MaxConcurrency`.

### <a name="remarks"></a>Observaciones

El método producirá [invalid_scheduler_policy_thread_specification](invalid-scheduler-policy-thread-specification-class.md) si el valor especificado para la directiva de `MinConcurrency` es mayor que el especificado para la directiva de `MaxConcurrency`.

El método también puede iniciar [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) para otros valores no válidos.

## <a name="setpolicyvalue"></a>Setpolicyvalue (

Establece el valor de la clave de directiva proporcionado como el parámetro `key` y devuelve el valor anterior.

```cpp
unsigned int SetPolicyValue(
    PolicyElementKey key,
    unsigned int value);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Clave de directiva para la que se va a establecer un valor.

*value*<br/>
Valor en el que se va a establecer la clave de directiva.

### <a name="return-value"></a>Valor devuelto

Si se admite la clave especificada por el parámetro `key`, el valor anterior de la Directiva para la clave se convierte en un `unsigned int`.

### <a name="remarks"></a>Observaciones

El método producirá [invalid_scheduler_policy_key](invalid-scheduler-policy-key-class.md) para una clave de Directiva no válida o una clave de directiva cuyo valor no se puede establecer mediante el método `SetPolicyValue`.

El método producirá [invalid_scheduler_policy_value](invalid-scheduler-policy-value-class.md) para un valor que no se admite para la clave especificada por el parámetro `key`.

Tenga en cuenta que este método no tiene permiso para establecer las directivas de `MinConcurrency` o `MaxConcurrency`. Para establecer estos valores, use el método [setconcurrencylimits (](#setconcurrencylimits) .

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)<br/>
[Policyelementkey (](concurrency-namespace-enums.md)<br/>
[CurrentScheduler (clase)](currentscheduler-class.md)<br/>
[Scheduler (clase)](scheduler-class.md)<br/>
[Programador de tareas](../../../parallel/concrt/task-scheduler-concurrency-runtime.md)
