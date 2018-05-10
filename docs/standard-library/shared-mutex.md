---
title: '&lt;shared_mutex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <shared_mutex>
- shared_mutex/std::swap
- shared_mutex/std::shared_lock
- shared_mutex/std::shared_lock::shared_lock
- shared_mutex/std::shared_lock::operator=
- shared_mutex/std::shared_lock::operator =
- shared_mutex/std::shared_lock::lock
- shared_mutex/std::shared_lock::try_lock
- shared_mutex/std::shared_lock::try_lock_for
- shared_mutex/std::shared_lock::try_lock_until
- shared_mutex/std::shared_lock::unlock
- shared_mutex/std::shared_lock::swap
- shared_mutex/std::shared_lock::release
- shared_mutex/std::shared_lock::owns_lock
- shared_mutex/std::shared_lock::operator bool
- shared_mutex/std::shared_lock::mutex
- shared_mutex/std::shared_mutex
- shared_mutex/std::shared_mutex::native_handle_type
- shared_mutex/std::shared_mutex::shared_mutex
- shared_mutex/std::shared_mutex::operator=
- shared_mutex/std::shared_mutex::operator =
- shared_mutex/std::shared_mutex::lock
- shared_mutex/std::shared_mutex::try_lock
- shared_mutex/std::shared_mutex::unlock
- shared_mutex/std::shared_mutex::lock_shared
- shared_mutex/std::shared_mutex::try_lock_shared
- shared_mutex/std::shared_mutex::unlock_shared
- shared_mutex/std::shared_mutex::native_handle
- shared_mutex/std::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::operator=
- shared_mutex/std::shared_timed_mutex::operator =
- shared_mutex/std::shared_timed_mutex::lock
- shared_mutex/std::shared_timed_mutex::try_lock
- shared_mutex/std::shared_timed_mutex::try_lock_for
- shared_mutex/std::shared_timed_mutex::try_lock_until
- shared_mutex/std::shared_timed_mutex::unlock
- shared_mutex/std::shared_timed_mutex::lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared_for
- shared_mutex/std::shared_timed_mutex::try_lock_shared_until
- shared_mutex/std::shared_timed_mutex::unlock_shared
dev_langs:
- C++
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b4a9cd6c4533b3b59fdb3c5cab17ffaba071fb08
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="ltsharedmutex"></a>&lt;shared_mutex >

El &lt;shared_mutex > encabezado proporciona primitivas de sincronización para la protección de datos compartidos que se pueden tener acceso varios subprocesos. Además del control de acceso exclusivo proporcionado por las clases mutex, las clases mutex compartidas también permiten la propiedad compartida por varios subprocesos para el acceso no exclusivo. Las exclusiones mutuas compartidas pueden usarse para controlar los recursos que varios subprocesos pueden leer sin causar una condición de carrera, pero se deben escribir exclusivamente por un único subproceso.

El encabezado &lt;shared_mutex > define las clases de `shared_mutex` y `shared_timed_mutex`, la clase de plantilla `shared_lock`y la función de plantilla `swap` para comparten el soporte técnico de la exclusión mutua.

|Clases|Descripción|
|-------------|-----------------|
|[shared_mutex (Clase)](../standard-library/shared-mutex.md#class_shared_mutex)|Un tipo de exclusión mutua compartida que se puede bloquear de manera exclusiva por un agente o compartir de manera no exclusiva por varios agentes.|
|[shared_timed_mutex (Clase)](../standard-library/shared-mutex.md#class_shared_timed_mutex)|Un tipo de exclusión mutua compartida temporizada que se puede bloquear de manera exclusiva por un agente o compartir de manera no exclusiva por varios agentes.|
|[shared_lock (Clase)](../standard-library/shared-mutex.md#class_shared_lock)|Una clase de plantilla que contiene una exclusión mutua compartida para admitir operaciones de bloqueo temporizado y que se puede compartir de manera no exclusiva por varios agentes.|

|Funciones|Descripción|
|---------------|-----------------|
|[swap](../standard-library/shared-mutex.md#function_swap)|Intercambia el contenido de los objetos de exclusión mutua compartida al que hacen referencia los parámetros de función.|

## <a name="syntax"></a>Sintaxis

```cpp
namespace std {
    class shared_mutex;
    class shared_timed_mutex;
    template <class Mutex>
class shared_lock;
    template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
}
```

## <a name="remarks"></a>Comentarios

Una instancia de la clase `shared_mutex` es un *tipo de exclusión mutua compartida*, un tipo que controla la propiedad compartida de una exclusión mutua dentro de un ámbito. Un tipo de exclusión mutua compartida cumple todos los requisitos de un tipo de exclusión mutua, así como los miembros para admitir la propiedad compartida no exclusiva.

Un tipo de exclusión mutua compartida admite los métodos adicionales `lock_shared`, `unlock_shared` y `try_lock_shared`:

- El método `lock_shared` bloquea el subproceso que realiza la llamada hasta que el subproceso obtenga la propiedad compartida de la exclusión mutua.

- El método `unlock_shared` libera la propiedad compartida de la exclusión mutua del subproceso que llama.

- El método `try_lock_shared` intenta obtener la propiedad compartida de la exclusión mutua sin bloquear. Su tipo de valor devuelto se puede convertir a `bool` y `true` si el método obtiene la propiedad, pero en caso contrario es `false`.

La clase `shared_timed_mutex` es un *tipo de exclusión mutua compartida temporizada*, un tipo que cumple los requisitos de exclusión mutua compartida y de exclusión mutua temporizada.

Un tipo de exclusión mutua compartida temporizada admite los métodos adicionales `try_lock_shared_for` y `try_lock_shared_until`:

- El método `try_lock_shared_for` intenta obtener la propiedad compartida de la exclusión mutua hasta que haya transcurrido el tiempo especificado por el parámetro. Si la duración no es positiva, el método es equivalente a `try_lock_shared`. El método no devuelve dentro de la duración especificada, a menos que se obtenga la propiedad compartida. Su valor devuelto es `true` si el método obtiene la propiedad, pero en caso contrario es `false`.

- El método `try_lock_shared_until` intenta obtener la propiedad compartida de la exclusión mutua hasta que haya transcurrido el tiempo absoluto especificado. Si ya ha pasado el tiempo especificado, el método es equivalente a `try_lock_shared`. El método no devuelve antes del tiempo especificado, a menos que se obtenga la propiedad compartida. Su valor devuelto es `true` si el método obtiene la propiedad, pero en caso contrario es `false`.

La clase de plantilla `shared_lock` extiende el soporte para el bloqueo temporizado y transfiere la propiedad a una exclusión mutua compartida. La propiedad de la exclusión mutua puede obtenerse en el momento de la construcción o después, y se puede transferir a otro objeto `shared_lock`. Los objetos de tipo `shared_lock` se pueden mover pero no copiar.

> [!WARNING]
> A partir de Visual Studio 2015, los tipos de sincronización de la biblioteca estándar de C++ se basan en los primitivos de sincronización de Windows y ya no utilizan ConcRT (salvo cuando la plataforma de destino es Windows XP). Los tipos definidos en &lt;shared_mutex > no debe usarse con cualquier función o tipo ConcRT.

## <a name="classes"></a>Clases

###  <a name="class_shared_mutex"></a> shared_mutex (Clase)

La clase `shared_mutex` implementa una exclusión mutua no recursiva con la semántica de propiedad compartida.

```cpp
class shared_mutex {
public:
   shared_mutex();
   ~shared_mutex();
   shared_mutex(const shared_mutex&) = delete;
   shared_mutex& operator=(const shared_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   void unlock_shared();
   // Getters
   typedef void** native_handle_type; // implementation defined
   native_handle_type native_handle();
   };
```

###  <a name="class_shared_timed_mutex"></a> shared_timed_mutex (Clase)

La clase `shared_timed_mutex` implementa una exclusión mutua no recursiva con la semántica de propiedad compartida que cumpla los requisitos de un tipo de exclusión mutua temporizada.

```cpp
class shared_timed_mutex {
public:
   shared_timed_mutex();
   ~shared_timed_mutex();
   shared_timed_mutex(const shared_timed_mutex&) = delete;
   shared_timed_mutex& operator=(const shared_timed_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   template <class Rep, class Period>
   bool try_lock_shared_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_shared_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock_shared();
   };
```

###  <a name="&lt;shared"></a> shared_lock (Clase)

La clase de plantilla `shared_lock` controla la propiedad compartida de un objeto de exclusión mutua compartida dentro de un ámbito. El parámetro de plantilla debe ser un tipo de exclusión mutua compartida.

```cpp
class shared_lock {
public:
   typedef Mutex mutex_type;
   shared_lock() noexcept;
   explicit shared_lock(mutex_type& m);
   // blocking
   shared_lock(mutex_type& m, defer_lock_t) noexcept;
   shared_lock(mutex_type& m, try_to_lock_t);
   shared_lock(mutex_type& m, adopt_lock_t);
   template <class Clock, class Duration>
   shared_lock(mutex_type& m,
   const chrono::time_point<Clock, Duration>& abs_time);
   template <class Rep, class Period>
   shared_lock(mutex_type& m,
   const chrono::duration<Rep, Period>& rel_time);
   ~shared_lock();
   shared_lock(shared_lock const&) = delete;
   shared_lock& operator=(shared_lock const&) = delete;
   shared_lock(shared_lock&& u) noexcept;
   shared_lock& operator=(shared_lock&& u) noexcept;
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Setters
   void swap(shared_lock& u) noexcept;
   mutex_type* release() noexcept;
   // Getters
   bool owns_lock() const noexcept;
   explicit operator bool () const noexcept;
   mutex_type* mutex() const noexcept;
private:
   mutex_type* pm; // exposition only
   bool owns; // exposition only
   };
```

## <a name="functions"></a>Funciones

###  <a name="function_swap"></a> Intercambiar

Intercambia los objetos `shared_lock`.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Intercambia el contenido de dos objetos `shared_lock`. De forma efectiva es igual que `x.swap(y)`.

## <a name="requirements"></a>Requisitos

**Encabezado:** &lt;shared_mutex>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Referencia de archivos de encabezado](../standard-library/cpp-standard-library-header-files.md)
[&lt;mutex >](../standard-library/mutex.md)
