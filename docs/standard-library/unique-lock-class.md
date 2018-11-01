---
title: unique_lock (Clase)
ms.date: 11/04/2016
f1_keywords:
- mutex/std::unique_lock
ms.assetid: f4ed8ba9-c8af-446f-8ef0-0b356bad14bd
ms.openlocfilehash: 784969bea25bfff49a21c23b350afbfc8bdab59a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574426"
---
# <a name="uniquelock-class"></a>unique_lock (Clase)

Representa una plantilla de la que se pueden crear instancias para crear objetos que administren el bloqueo y desbloqueo de una `mutex`.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Mutex>
class unique_lock;
```

## <a name="remarks"></a>Comentarios

El argumento de plantilla `Mutex` debe nombrar un *tipo de exclusión mutua*.

Internamente, un `unique_lock` almacena un puntero a un asociado `mutex` objeto y un **bool** que indica si el subproceso actual posee el `mutex`.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|`mutex_type`|Sinónimo del argumento de plantilla `Mutex`.|

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[unique_lock](#unique_lock)|Construye un objeto `unique_lock`.|
|[~unique_lock (Destructor)](#dtorunique_lock_destructor)|Libera todos los recursos asociados con el objeto `unique_lock`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[lock](#lock)|Bloquea el subproceso de llamada hasta que este obtiene la propiedad de la `mutex` asociada.|
|[mutex](#mutex)|Recupera el puntero almacenado a la `mutex` asociada.|
|[owns_lock](#owns_lock)|Especifica si el subproceso de llamada tiene la propiedad de la `mutex` asociada.|
|[release](#release)|Desasocia el objeto `unique_lock` del objeto `mutex` asociado.|
|[swap](#swap)|Intercambia el objeto `mutex` asociado y el estado de la propiedad con el de un objeto especificado.|
|[try_lock](#try_lock)|Intenta obtener la propiedad del `mutex` asociado sin bloquearlo.|
|[try_lock_for](#try_lock_for)|Intenta obtener la propiedad del `mutex` asociado sin bloquearlo.|
|[try_lock_until](#try_lock_until)|Intenta obtener la propiedad del `mutex` asociado sin bloquearlo.|
|[unlock](#unlock)|Libera la propiedad del objeto `mutex` asociado.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operator bool](#op_bool)|Especifica si el subproceso de llamada tiene la propiedad del objeto `mutex` asociado.|
|[operator=](#op_eq)|Copia el puntero `mutex` almacenado y el estado de la propiedad asociada de un objeto especificado.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

*unique_lock*<br/>

## <a name="requirements"></a>Requisitos

**Encabezado:** \<mutex >

**Espacio de nombres:** std

## <a name="lock"></a> lock

Bloquea el subproceso de llamada hasta que este obtiene la propiedad de la `mutex` asociada.

```cpp
void lock();
```

### <a name="remarks"></a>Comentarios

Si el almacenado `mutex` puntero es NULL, este método produce una [system_error](../standard-library/system-error-class.md) que tiene un código de error de `operation_not_permitted`.

Si el subproceso de llamada ya posee el objeto `mutex` asociado, este método produce un `system_error` que tiene un código de error de `resource_deadlock_would_occur`.

De lo contrario, llama este método `lock` en asociado `mutex` y establece la marca de la propiedad interna del subproceso en **true**.

## <a name="mutex"></a>  mutex

Recupera el puntero almacenado a la `mutex` asociada.

```cpp
mutex_type *mutex() const noexcept;
```

## <a name="op_bool"></a>  operator bool

Especifica si el subproceso de llamada tiene la propiedad de la exclusión mutua asociada.

```cpp
explicit operator bool() noexcept
```

### <a name="return-value"></a>Valor devuelto

**True** si el subproceso posee la exclusión mutua; en caso contrario **false**.

## <a name="op_eq"></a>  operator=

Copia el puntero `mutex` almacenado y el estado de la propiedad asociada de un objeto especificado.

```cpp
unique_lock& operator=(unique_lock&& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*Otros problemas*<br/>
Un objeto `unique_lock`.

### <a name="return-value"></a>Valor devuelto

`*this`

### <a name="remarks"></a>Comentarios

Si el subproceso de llamada posee el objeto `mutex` asociado anteriormente, antes de que este método llame a `unlock` en el objeto `mutex`, asigna los nuevos valores.

Después de la copia, este método establece *otros* a un estado construido de forma predeterminada.

## <a name="owns_lock"></a>  owns_lock

Especifica si el subproceso de llamada tiene la propiedad de la `mutex` asociada.

```cpp
bool owns_lock() const noexcept;
```

### <a name="return-value"></a>Valor devuelto

**True** si el subproceso posee el `mutex`; en caso contrario, **false**.

## <a name="release"></a>  release

Desasocia el objeto `unique_lock` del objeto `mutex` asociado.

```cpp
mutex_type *release() noexcept;
```

### <a name="return-value"></a>Valor devuelto

El valor anterior del puntero `mutex` almacenado.

### <a name="remarks"></a>Comentarios

Este método establece el valor de almacenado `mutex` puntero en 0 y establece el texto interno `mutex` marca la propiedad a **false**.

## <a name="swap"></a>  swap

Intercambia el objeto `mutex` asociado y el estado de la propiedad con el de un objeto especificado.

```cpp
void swap(unique_lock& Other) noexcept;
```

### <a name="parameters"></a>Parámetros

*Otros problemas*<br/>
Un objeto `unique_lock`.

## <a name="try_lock"></a>  try_lock

Intenta obtener la propiedad del `mutex` asociado sin bloquearlo.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Valor devuelto

**True** si el método obtiene correctamente la propiedad de la `mutex`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Si el almacenado `mutex` puntero es NULL, el método produce una [system_error](../standard-library/system-error-class.md) que tiene un código de error de `operation_not_permitted`.

Si el subproceso de llamada ya posee el objeto `mutex`, el método produce un `system_error` que tiene un código de error de `resource_deadlock_would_occur`.

## <a name="try_lock_for"></a>  try_lock_for

Intenta obtener la propiedad del `mutex` asociado sin bloquearlo.

```cpp
template <class Rep, class Period>
bool try_lock_for(
    const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parámetros

*Rel_time*<br/>
Un objeto [chrono::duration](../standard-library/duration-class.md) que especifica el tiempo máximo que el método intenta obtener la propiedad de `mutex`.

### <a name="return-value"></a>Valor devuelto

**True** si el método obtiene correctamente la propiedad de la `mutex`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Si el almacenado `mutex` puntero es NULL, el método produce una [system_error](../standard-library/system-error-class.md) que tiene un código de error de `operation_not_permitted`.

Si el subproceso de llamada ya posee el objeto `mutex`, el método produce un `system_error` que tiene un código de error de `resource_deadlock_would_occur`.

## <a name="try_lock_until"></a>  try_lock_until

Intenta obtener la propiedad del `mutex` asociado sin bloquearlo.

```cpp
template <class Clock, class Duration>
bool try_lock_until(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parámetros

*Abs_time*<br/>
Punto en el tiempo que especifica el umbral después del cual el método ya no intenta obtener la propiedad de `mutex`.

### <a name="return-value"></a>Valor devuelto

**True** si el método obtiene correctamente la propiedad de la `mutex`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Si el almacenado `mutex` puntero es NULL, el método produce una [system_error](../standard-library/system-error-class.md) que tiene un código de error de `operation_not_permitted`.

Si el subproceso de llamada ya posee el objeto `mutex`, el método produce un `system_error` que tiene un código de error de `resource_deadlock_would_occur`.

## <a name="unique_lock"></a>  unique_lock (Constructor)

Construye un objeto `unique_lock`.

```cpp
unique_lock() noexcept;
unique_lock(unique_lock&& Other) noexcept;
explicit unique_lock(mutex_type& Mtx);

unique_lock(mutex_type& Mtx, adopt_lock_t Adopt);

unique_lock(mutex_type& Mtx, defer_lock_t Defer) noexcept;
unique_lock(mutex_type& Mtx, try_to_lock_t Try);

template <class Rep, class Period>
unique_lock(mutex_type& Mtx,
    const chrono::duration<Rep, Period>
Rel_time);

template <class Clock, class Duration>
unique_lock(mutex_type& Mtx,
    const chrono::time_point<Clock, Duration>
Abs_time);

unique_lock(mutex_type& Mtx,
    const xtime* Abs_time) noexcept;
```

### <a name="parameters"></a>Parámetros

*Mtx*<br/>
Un objeto de tipo de exclusión mutua.

*Rel_time*<br/>
Un objeto [chrono::duration](../standard-library/duration-class.md) que especifica el tiempo máximo que el método intenta obtener la propiedad de `mutex`.

*Abs_time*<br/>
Punto en el tiempo que especifica el umbral después del cual el método ya no intenta obtener la propiedad de `mutex`.

*Otros problemas*<br/>
Un objeto `unique_lock`.

### <a name="remarks"></a>Comentarios

El primer constructor crea un objeto que tiene un valor de puntero de exclusión mutua asociado de 0.

El segundo constructor mueve el estado de la exclusión mutua asociado desde *otros*. Tras el movimiento, *otros* ya no está asociado a una exclusión mutua.

Los constructores restantes almacenan & *Mtx* como almacenado `mutex` puntero. La propiedad del objeto `mutex` está determinada por el segundo argumento, si existe.

|||
|-|-|
|`No argument`|La propiedad se obtiene mediante una llamada al método `lock` en el objeto `mutex` asociado.|
|`Adopt`|Se supone la propiedad. `Mtx` debe estar bloqueado cuando se llama al constructor.|
|`Defer`|Se supone que el subproceso de llamada no posee el objeto `mutex`. `Mtx` no debe estar bloqueado cuando se llama al constructor.|
|`Try`|La propiedad se determina mediante una llamada a `try_lock` en el objeto `mutex` asociado. El constructor no inicia nada.|
|`Rel_time`|La propiedad se determina mediante una llamada a `try_lock_for(Rel_time)`.|
|`Abs_time`|La propiedad se determina mediante una llamada a `try_lock_until(Abs_time)`.|

## <a name="dtorunique_lock_destructor"></a>  ~unique_lock (Destructor)

Libera todos los recursos asociados con el objeto `unique_lock`.

```cpp
~unique_lock() noexcept;
```

### <a name="remarks"></a>Comentarios

Si el subproceso de llamada posee el objeto `mutex` asociado, el destructor libera la propiedad mediante la llamada a unlock en el objeto `mutex`.

## <a name="unlock"></a>  unlock

Libera la propiedad del objeto `mutex` asociado.

```cpp
void unlock();
```

### <a name="remarks"></a>Comentarios

Si el subproceso de llamada no posee el objeto `mutex` asociado, este método produce un [system_error](../standard-library/system-error-class.md) que tiene un código de error de `operation_not_permitted`.

De lo contrario, llama este método `unlock` en asociado `mutex` y establece la marca de la propiedad interna del subproceso en **false**.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
