---
title: timed_mutex (Clase)
ms.date: 11/04/2016
f1_keywords:
- mutex/std::timed_mutex
- mutex/std::timed_mutex::timed_mutex
- mutex/std::timed_mutex::lock
- mutex/std::timed_mutex::try_lock
- mutex/std::timed_mutex::try_lock_for
- mutex/std::timed_mutex::try_lock_until
- mutex/std::timed_mutex::unlock
ms.assetid: cd198081-6f38-447a-9dba-e06dfbfafe59
helpviewer_keywords:
- std::timed_mutex [C++]
- std::timed_mutex [C++], timed_mutex
- std::timed_mutex [C++], lock
- std::timed_mutex [C++], try_lock
- std::timed_mutex [C++], try_lock_for
- std::timed_mutex [C++], try_lock_until
- std::timed_mutex [C++], unlock
ms.openlocfilehash: 6c9840d9b8c00d4b03e6ea329c7707a0edff9512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368015"
---
# <a name="timed_mutex-class"></a>timed_mutex (Clase)

Representa un *tipo de exclusión mutua temporizada.* Los objetos de este tipo se usan para aplicar una exclusión mutua mediante un bloqueo limitado por tiempo dentro de un programa.

## <a name="syntax"></a>Sintaxis

```cpp
class timed_mutex;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|Crea un objeto `timed_mutex` que no está bloqueado.|
|[timed_mutex::~timed_mutex (Destructor)](#dtortimed_mutex_destructor)|Libera todos los recursos usados por el objeto `timed_mutex`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cerradura](#lock)|Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.|
|[try_lock](#try_lock)|Intenta obtener la propiedad de `mutex` sin bloquearlo.|
|[try_lock_for](#try_lock_for)|Intenta obtener la propiedad de `mutex` para un intervalo de tiempo especificado.|
|[try_lock_until](#try_lock_until)|Intenta obtener la propiedad de `mutex` hasta una hora especificada.|
|[Desbloquear](#unlock)|Libera la propiedad de `mutex`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> de exclusión mutua

**Espacio de nombres:** std

## <a name="timed_mutexlock"></a><a name="lock"></a>timed_mutex::bloqueo

Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Observaciones

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="timed_mutextimed_mutex-constructor"></a><a name="timed_mutex"></a>Constructor timed_mutex::timed_mutex

Crea un objeto `timed_mutex` que no está bloqueado.

```cpp
timed_mutex();
```

## <a name="timed_mutextimed_mutex-destructor"></a><a name="dtortimed_mutex_destructor"></a>timed_mutex::-timed_mutex Destructor

Libera todos los recursos usados por el objeto `mutex`.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Observaciones

Si el objeto está bloqueado cuando se ejecuta el destructor, el comportamiento es indefinido.

## <a name="timed_mutextry_lock"></a><a name="try_lock"></a>timed_mutex::try_lock

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valor devuelto

**true** si el método obtiene correctamente `mutex`la propiedad de la ; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="timed_mutextry_lock_for"></a><a name="try_lock_for"></a>timed_mutex::try_lock_for

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parámetros

*Rel_time*\
Un objeto [chrono::duration](../standard-library/duration-class.md) que especifica el tiempo máximo que el método intenta obtener la propiedad de `mutex`.

### <a name="return-value"></a>Valor devuelto

**true** si el método obtiene correctamente `mutex`la propiedad de la ; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="timed_mutextry_lock_until"></a><a name="try_lock_until"></a>timed_mutex::try_lock_until

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

**true** si el método obtiene correctamente `mutex`la propiedad de la ; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="timed_mutexunlock"></a><a name="unlock"></a>timed_mutex::desbloqueo

Libera la propiedad de `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Observaciones

Si el subproceso que realiza la llamada no posee `mutex`, el comportamiento es indefinido.

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<>de exclusión mutua](../standard-library/mutex.md)
