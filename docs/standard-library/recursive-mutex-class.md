---
title: recursive_mutex (Clase)
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 9ab7a96a7c07582450ab41b140dcc5494a63661f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320207"
---
# <a name="recursive_mutex-class"></a>recursive_mutex (Clase)

Representa un *tipo de exclusión mutua*. Al contrario que [mutex](../standard-library/mutex-class-stl.md), el comportamiento de las llamadas a métodos de bloqueo para objetos que ya están bloqueados está bien definido.

## <a name="syntax"></a>Sintaxis

```cpp
class recursive_mutex;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|Construye un objeto `recursive_mutex`.|
|[~recursive_mutex (Destructor)](#dtorrecursive_mutex_destructor)|Libera todos los recursos usados por el objeto `recursive_mutex`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cerradura](#lock)|Bloquea el subproceso de llamada hasta que este obtiene la propiedad de la exclusión mutua.|
|[try_lock](#try_lock)|Intenta obtener la propiedad de la exclusión mutua sin bloquearla.|
|[Desbloquear](#unlock)|Libera la propiedad de la exclusión mutua.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> de exclusión mutua

**Espacio de nombres:** std

## <a name="lock"></a><a name="lock"></a>Cerradura

Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Observaciones

Si el subproceso que realiza la llamada ya posee `mutex`, el método se devuelve inmediatamente, y el bloqueo anterior permanece vigente.

## <a name="recursive_mutex"></a><a name="recursive_mutex"></a>recursive_mutex

Crea un objeto `recursive_mutex` que no está bloqueado.

```cpp
recursive_mutex();
```

## <a name="recursive_mutex"></a><a name="dtorrecursive_mutex_destructor"></a> ~recursive_mutex

Libera todos los recursos usados por el objeto.

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Observaciones

Si el objeto está bloqueado cuando se ejecuta el destructor, el comportamiento es indefinido.

## <a name="try_lock"></a><a name="try_lock"></a>try_lock

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>Valor devuelto

**true** si el método obtiene correctamente `mutex` la propiedad de la `mutex**; otherwise, **false`o si el subproceso de llamada ya posee el archivo .

### <a name="remarks"></a>Observaciones

Si el subproceso que `mutex`realiza la llamada ya posee el valor , la función devuelve inmediatamente **true**y el bloqueo anterior permanece en vigor.

## <a name="unlock"></a><a name="unlock"></a>Desbloquear

Libera la propiedad de la exclusión mutua.

```cpp
void unlock();
```

### <a name="remarks"></a>Observaciones

Este método libera la propiedad de `mutex` solo después de que se llame tantas veces como se ha llamado a [lock](#lock) y [try_lock](#try_lock) correctamente en el objeto `recursive_mutex`.

Si el subproceso que realiza la llamada no posee `mutex`, el comportamiento es indefinido.

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<>de exclusión mutua](../standard-library/mutex.md)
