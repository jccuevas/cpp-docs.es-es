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
ms.openlocfilehash: 9aae1205866a0bf982ab7c41b792aac0f63ea149
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50524892"
---
# <a name="timedmutex-class"></a>timed_mutex (Clase)

Representa un *tipo de exclusión mutua cronometrado*. Los objetos de este tipo se usan para aplicar una exclusión mutua mediante un bloqueo limitado por tiempo dentro de un programa.

## <a name="syntax"></a>Sintaxis

```cpp
class timed_mutex;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[timed_mutex](#timed_mutex)|Crea un objeto `timed_mutex` que no está bloqueado.|
|[timed_mutex::~timed_mutex (Destructor)](#dtortimed_mutex_destructor)|Libera todos los recursos usados por el objeto `timed_mutex`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[lock](#lock)|Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.|
|[try_lock](#try_lock)|Intenta obtener la propiedad de `mutex` sin bloquearlo.|
|[try_lock_for](#try_lock_for)|Intenta obtener la propiedad de `mutex` para un intervalo de tiempo especificado.|
|[try_lock_until](#try_lock_until)|Intenta obtener la propiedad de `mutex` hasta una hora especificada.|
|[unlock](#unlock)|Libera la propiedad de `mutex`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<mutex >

**Espacio de nombres:** std

## <a name="lock"></a>  timed_mutex::lock

Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="timed_mutex"></a>  timed_mutex::timed_mutex (Constructor)

Crea un objeto `timed_mutex` que no está bloqueado.

```cpp
timed_mutex();
```

## <a name="dtortimed_mutex_destructor"></a>  timed_mutex::~timed_mutex (Destructor)

Libera todos los recursos usados por el objeto `mutex`.

```cpp
~timed_mutex();
```

### <a name="remarks"></a>Comentarios

Si el objeto está bloqueado cuando se ejecuta el destructor, el comportamiento es indefinido.

## <a name="try_lock"></a>  timed_mutex::try_lock

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valor devuelto

**True** si el método obtiene correctamente la propiedad de la `mutex`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="try_lock_for"></a>  timed_mutex::try_lock_for

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
template <class Rep, class Period>
bool try_lock_for(const chrono::duration<Rep, Period>& Rel_time);
```

### <a name="parameters"></a>Parámetros

*Rel_time*<br/>
Un objeto [chrono::duration](../standard-library/duration-class.md) que especifica el tiempo máximo que el método intenta obtener la propiedad de `mutex`.

### <a name="return-value"></a>Valor devuelto

**True** si el método obtiene correctamente la propiedad de la `mutex`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="try_lock_until"></a>  timed_mutex::try_lock_until

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
template <class Clock, class Duration>
bool try_lock_for(const chrono::time_point<Clock, Duration>& Abs_time);

bool try_lock_until(const xtime* Abs_time);
```

### <a name="parameters"></a>Parámetros

*Abs_time*<br/>
Punto en el tiempo que especifica el umbral después del cual el método ya no intenta obtener la propiedad de `mutex`.

### <a name="return-value"></a>Valor devuelto

**True** si el método obtiene correctamente la propiedad de la `mutex`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="unlock"></a>  timed_mutex::Unlock

Libera la propiedad de `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada no posee `mutex`, el comportamiento es indefinido.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
