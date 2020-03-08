---
title: Funciones y variables &lt;mutex&gt;
ms.date: 11/04/2016
f1_keywords:
- mutex/std::adopt_lock
- mutex/std::call_once
- mutex/std::defer_lock
- mutex/std::lock
- mutex/std::try_to_lock
ms.assetid: 78ab3c8b-c7db-4226-ac93-e2e78ff8b964
helpviewer_keywords:
- std::adopt_lock [C++]
- std::call_once [C++]
- std::defer_lock [C++]
- std::lock [C++]
- std::try_to_lock [C++]
ms.openlocfilehash: f6bd6a86e91c2d59fec2083dcf0ec6314d7c41ab
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856305"
---
# <a name="ltmutexgt-functions-and-variables"></a>Funciones y variables &lt;mutex&gt;

## <a name="adopt_lock"></a>adopt_lock

Representa un objeto que se puede pasar a los constructores de [lock_guard](../standard-library/lock-guard-class.md) y [unique_lock](../standard-library/unique-lock-class.md) para indicar que el objeto de exclusión mutua que también se pasa al constructor está bloqueado.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a>call_once

Proporciona un mecanismo para llamar exactamente una vez durante la ejecución a un objeto especificado que se puede llamar.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Parámetros

*Marca*\
Un objeto [once_flag](../standard-library/once-flag-structure.md) que garantiza que solo se llama una vez al objeto que se puede llamar.

\ *F*
Un objeto al que se puede llamar.

*Un*\
Lista de argumentos.

### <a name="remarks"></a>Observaciones

Si el *marcador* no es válido, la función produce una [system_error](../standard-library/system-error-class.md) que tiene un código de error de `invalid_argument`. De lo contrario, la función de plantilla utiliza su argumento *Flag* para asegurarse de que llama a `F(A...)` correctamente una vez, independientemente del número de veces que se llame a la función de plantilla. Si `F(A...)` se cierra emitiendo una excepción, la llamada no se ha realizado correctamente.

## <a name="defer_lock"></a>defer_lock

Representa un objeto que puede pasarse al constructor para [unique_lock](../standard-library/unique-lock-class.md). Esto indica que el constructor no debe bloquear el objeto mutex que también se le está pasando.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a>bloquea

Intenta bloquear todos los argumentos sin interbloqueo.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Observaciones

Los argumentos de la función de plantilla debe ser *tipos mutex*, excepto que las llamadas a `try_lock` pueden producir excepciones.

La función bloquea todos sus argumentos sin interbloqueo mediante llamadas a `lock`, `try_lock` y `unlock`. Si una llamada a `lock` o `try_lock` produce una excepción, la función llama a `unlock` en cualquiera de los objetos mutex que se han bloqueado correctamente antes de volver a producir la excepción.

## <a name="swap"></a>pasar

```cpp
template <class Mutex>
void swap(unique_lock<Mutex>& x, unique_lock<Mutex>& y) noexcept;
```

## <a name="try_lock"></a>try_lock

```cpp
template <class L1, class L2, class... L3> int try_lock(L1&, L2&, L3&...);
```

## <a name="try_to_lock"></a>try_to_lock

Representa un objeto que se puede pasar al constructor de [unique_lock](../standard-library/unique-lock-class.md) para indicar que el constructor debería intentar desbloquear la `mutex` que también se pasa a este sin bloquearla.

```cpp
const try_to_lock_t try_to_lock;
```
