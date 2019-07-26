---
title: recursive_timed_mutex (Clase)
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::recursive_timed_mutex
- mutex/std::recursive_timed_mutex::lock
- mutex/std::recursive_timed_mutex::try_lock
- mutex/std::recursive_timed_mutex::try_lock_for
- mutex/std::recursive_timed_mutex::try_lock_until
- mutex/std::recursive_timed_mutex::unlock
ms.assetid: 59cc2d5c-ed80-45f3-a0a8-05652a8ead7e
helpviewer_keywords:
- std::recursive_timed_mutex [C++]
- std::recursive_timed_mutex [C++], recursive_timed_mutex
- std::recursive_timed_mutex [C++], lock
- std::recursive_timed_mutex [C++], try_lock
- std::recursive_timed_mutex [C++], try_lock_for
- std::recursive_timed_mutex [C++], try_lock_until
- std::recursive_timed_mutex [C++], unlock
ms.openlocfilehash: 6ae61d17084cc744cac8819ac2c0ca48eb59add7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460116"
---
# <a name="recursivetimedmutex-class"></a>recursive_timed_mutex (Clase)

Representa un *tipo de exclusión mutua cronometrado*. Los objetos de este tipo se usan para aplicar una exclusión mutua mediante un bloqueo limitado por tiempo dentro de un programa. A diferencia de los objetos de tipo [timed_mutex](../standard-library/timed-mutex-class.md), el efecto de llamar a métodos de bloqueo de objetos `recursive_timed_mutex` está bien definido.

## <a name="syntax"></a>Sintaxis

```cpp
class recursive_timed_mutex;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[recursive_timed_mutex](#recursive_timed_mutex)|Crea un objeto `recursive_timed_mutex` que no está bloqueado.|
|[~recursive_timed_mutex (Destructor)](#dtorrecursive_timed_mutex_destructor)|Libera todos los recursos usados por el objeto `recursive_timed_mutex`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[lock](#lock)|Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.|
|[try_lock](#try_lock)|Intenta obtener la propiedad de `mutex` sin bloquearlo.|
|[try_lock_for](#try_lock_for)|Intenta obtener la propiedad de `mutex` para un intervalo de tiempo especificado.|
|[try_lock_until](#try_lock_until)|Intenta obtener la propiedad de `mutex` hasta una hora especificada.|
|[unlock](#unlock)|Libera la propiedad de `mutex`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<exclusión mutua >

**Espacio de nombres:** std

## <a name="lock"></a> lock

Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada ya posee `mutex`, el método se devuelve inmediatamente, y el bloqueo anterior permanece vigente.

## <a name="recursive_timed_mutex"></a> recursive_timed_mutex (Constructor)

Crea un objeto `recursive_timed_mutex` que no está bloqueado.

```cpp
recursive_timed_mutex();
```

## <a name="dtorrecursive_timed_mutex_destructor"></a> ~recursive_timed_mutex (Destructor)

Libera todos los recursos usados por el objeto `recursive_timed_mutex`.

```cpp
~recursive_timed_mutex();
```

### <a name="remarks"></a>Comentarios

Si el objeto está bloqueado cuando se ejecuta el destructor, el comportamiento es indefinido.

## <a name="try_lock"></a> try_lock

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Valor devuelto

**true** si el método obtuvo correctamente la propiedad de `mutex` o si el subproceso que realiza la `mutex`llamada ya posee el; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la `mutex`llamada ya posee, la función devuelve inmediatamente **true**y el bloqueo anterior permanece en vigor.

## <a name="try_lock_for"></a> try_lock_for

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parámetros

*Rel_time*\
Un objeto [chrono::duration](../standard-library/duration-class.md) que especifica el tiempo máximo que el método intenta obtener la propiedad de `mutex`.

### <a name="return-value"></a>Valor devuelto

**true** si el método obtiene correctamente la propiedad de `mutex` o si el subproceso que realiza la llamada ya posee el  `mutex`; en caso contrario, false.

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la `mutex`llamada ya posee, el método devuelve inmediatamente **true**y el bloqueo anterior permanece en vigor.

## <a name="try_lock_until"></a> try_lock_until

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parámetros

*Abs_time*\
Punto en el tiempo que especifica el umbral después del cual el método ya no intenta obtener la propiedad de `mutex`.

### <a name="return-value"></a>Valor devuelto

**true** si el método obtiene correctamente la propiedad de `mutex` o si el subproceso que realiza la llamada ya posee el  `mutex`; en caso contrario, false.

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la `mutex`llamada ya posee, el método devuelve inmediatamente **true**y el bloqueo anterior permanece en vigor.

## <a name="unlock"></a> unlock

Libera la propiedad de `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Comentarios

Este método libera la propiedad de `mutex` solo después de que se llame tantas veces como se ha llamado a [lock](#lock), [try_lock](#try_lock), [try_lock_for](#try_lock_for) y [try_lock_until](#try_lock_until) correctamente en el objeto `recursive_timed_mutex`.

Si el subproceso que realiza la llamada no posee `mutex`, el comportamiento es indefinido.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
