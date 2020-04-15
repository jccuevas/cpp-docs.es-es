---
title: mutex (Clase, biblioteca estándar de C++)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 84e6e3a46903a204444df9886556ae2c563304a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364844"
---
# <a name="mutex-class-c-standard-library"></a>mutex (Clase, biblioteca estándar de C++)

Representa un *tipo de exclusión mutua*. Los objetos de este tipo se pueden usar para aplicar la exclusión mutua dentro de un programa.

## <a name="syntax"></a>Sintaxis

```cpp
class mutex;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[exclusión mutua](#mutex)|Construye un objeto `mutex`.|
|[mutex::~mutex Destructor](#dtormutex_destructor)|Libera todos los recursos utilizados por el objeto `mutex`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Cerradura](#lock)|Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.|
|[native_handle](#native_handle)|Devuelve el tipo específico de la implementación que representa el identificador de exclusión mutua.|
|[try_lock](#try_lock)|Intenta obtener la propiedad de `mutex` sin bloquearlo.|
|[Desbloquear](#unlock)|Libera la propiedad de `mutex`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<> de exclusión mutua

**Espacio de nombres:** std

## <a name="mutexlock"></a><a name="lock"></a>mutex::lock

Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Observaciones

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="mutexmutex-constructor"></a><a name="mutex"></a>mutex::mutex Constructor

Crea un objeto `mutex` que no está bloqueado.

```cpp
constexpr mutex() noexcept;
```

## <a name="mutexmutex-destructor"></a><a name="dtormutex_destructor"></a>mutex::-mutex Destructor

Libera todos los recursos usados por el objeto `mutex`.

```cpp
~mutex();
```

### <a name="remarks"></a>Observaciones

Si el objeto está bloqueado cuando se ejecuta el destructor, el comportamiento es indefinido.

## <a name="mutexnative_handle"></a><a name="native_handle"></a>mutex::native_handle

Devuelve el tipo específico de la implementación que representa el identificador de exclusión mutua. El controlador de exclusión mutua puede usarse en aspectos específicos de la implementación.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valor devuelto

`native_handle_type` se define como un `Concurrency::critical_section *` que se convierte en `void *`.

## <a name="mutextry_lock"></a><a name="try_lock"></a>mutex::try_lock

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valor devuelto

**true** si el método obtiene correctamente `mutex`la propiedad de la ; de lo contrario, **false**.

### <a name="remarks"></a>Observaciones

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="mutexunlock"></a><a name="unlock"></a>mutex::unlock

Libera la propiedad de `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Observaciones

Si el subproceso que realiza la llamada no posee `mutex`, el comportamiento es indefinido.

## <a name="see-also"></a>Consulte también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)\
[\<>de exclusión mutua](../standard-library/mutex.md)
