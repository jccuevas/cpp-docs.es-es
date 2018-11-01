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
ms.openlocfilehash: 7766b063eb89a14a94eaa41ebfa17f3e4a1c102e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50522569"
---
# <a name="mutex-class-c-standard-library"></a>mutex (Clase, biblioteca estándar de C++)

Representa un *tipo de exclusión mutua*. Los objetos de este tipo se pueden usar para aplicar la exclusión mutua dentro de un programa.

## <a name="syntax"></a>Sintaxis

```cpp
class mutex;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[mutex](#mutex)|Construye un objeto `mutex`.|
|[mutex::~mutex Destructor](#dtormutex_destructor)|Libera todos los recursos utilizados por el objeto `mutex`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[lock](#lock)|Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.|
|[native_handle](#native_handle)|Devuelve el tipo específico de la implementación que representa el identificador de exclusión mutua.|
|[try_lock](#try_lock)|Intenta obtener la propiedad de `mutex` sin bloquearlo.|
|[unlock](#unlock)|Libera la propiedad de `mutex`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** \<mutex >

**Espacio de nombres:** std

## <a name="lock"></a>  Mutex

Bloquea el subproceso que realiza la llamada hasta que este obtiene la propiedad `mutex`.

```cpp
void lock();
```

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="mutex"></a> mutex::mutex (Constructor)

Crea un objeto `mutex` que no está bloqueado.

```cpp
constexpr mutex() noexcept;
```

## <a name="dtormutex_destructor"></a> mutex::~mutex (Destructor)

Libera todos los recursos usados por el objeto `mutex`.

```cpp
~mutex();
```

### <a name="remarks"></a>Comentarios

Si el objeto está bloqueado cuando se ejecuta el destructor, el comportamiento es indefinido.

## <a name="native_handle"></a>  Mutex:: native_handle

Devuelve el tipo específico de la implementación que representa el identificador de exclusión mutua. El controlador de exclusión mutua puede usarse en aspectos específicos de la implementación.

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>Valor devuelto

`native_handle_type` se define como un `Concurrency::critical_section *` que se convierte en `void *`.

## <a name="try_lock"></a>  Mutex::try_lock

Intenta obtener la propiedad de `mutex` sin bloquearlo.

```cpp
bool try_lock();
```

### <a name="return-value"></a>Valor devuelto

**True** si el método obtiene correctamente la propiedad de la `mutex`; en caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada ya posee `mutex`, el comportamiento es indefinido.

## <a name="unlock"></a>  Mutex::Unlock

Libera la propiedad de `mutex`.

```cpp
void unlock();
```

### <a name="remarks"></a>Comentarios

Si el subproceso que realiza la llamada no posee `mutex`, el comportamiento es indefinido.

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<mutex>](../standard-library/mutex.md)<br/>
