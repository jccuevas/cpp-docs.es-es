---
title: Funciones y variables &lt;mutex&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 85ed95250b5563cd8a7c1ef9cfc0ee048cb3bc60
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858217"
---
# <a name="ltmutexgt-functions-and-variables"></a>Funciones y variables &lt;mutex&gt;

||||
|-|-|-|
|[adopt_lock](#adopt_lock)|[call_once](#call_once)|[defer_lock](#defer_lock)|
|[lock](#lock)|[try_to_lock](#try_to_lock)|

## <a name="adopt_lock"></a> adopt_lock (Variable)

Representa un objeto que se puede pasar a los constructores de [lock_guard](../standard-library/lock-guard-class.md) y [unique_lock](../standard-library/unique-lock-class.md) para indicar que el objeto de exclusión mutua que también se pasa al constructor está bloqueado.

```cpp
const adopt_lock_t adopt_lock;
```

## <a name="call_once"></a> call_once

Proporciona un mecanismo para llamar exactamente una vez durante la ejecución a un objeto especificado que se puede llamar.

```cpp
template <class Callable, class... Args>
void call_once(once_flag& Flag,
    Callable F&&, Args&&... A);
```

### <a name="parameters"></a>Parámetros

`Flag` A [once_flag](../standard-library/once-flag-structure.md) objeto que se asegura de que el objeto que se puede llamar solo se llama una vez.

`F` Un objeto que se puede llamar.

`A` Una lista de argumentos.

### <a name="remarks"></a>Comentarios

Si `Flag` no es válido, la función produce un [system_error](../standard-library/system-error-class.md) que tiene un código de error de `invalid_argument`. De otro modo, la función de plantilla usa su argumento `Flag` para garantizar que llama correctamente a `F(A...)` exactamente una vez, independientemente de cuántas veces se llame a la función de plantilla. Si `F(A...)` se cierra emitiendo una excepción, la llamada no se ha realizado correctamente.

## <a name="defer_lock"></a> defer_lock (Variable)

Representa un objeto que puede pasarse al constructor para [unique_lock](../standard-library/unique-lock-class.md). Esto indica que el constructor no debe bloquear el objeto mutex que también se le está pasando.

```cpp
const defer_lock_t defer_lock;
```

## <a name="lock"></a> lock

Intenta bloquear todos los argumentos sin interbloqueo.

```cpp
template <class L1, class L2, class... L3>
void lock(L1&, L2&, L3&...);
```

### <a name="remarks"></a>Comentarios

Los argumentos de la función de plantilla debe ser *tipos mutex*, excepto que las llamadas a `try_lock` pueden producir excepciones.

La función bloquea todos sus argumentos sin interbloqueo mediante llamadas a `lock`, `try_lock` y `unlock`. Si una llamada a `lock` o `try_lock` produce una excepción, la función llama a `unlock` en cualquiera de los objetos mutex que se han bloqueado correctamente antes de volver a producir la excepción.

## <a name="try_to_lock"></a> try_to_lock (Variable)

Representa un objeto que se puede pasar al constructor de [unique_lock](../standard-library/unique-lock-class.md) para indicar que el constructor debería intentar desbloquear la `mutex` que también se pasa a este sin bloquearla.

```cpp
const try_to_lock_t try_to_lock;
```

## <a name="see-also"></a>Vea también

[\<mutex>](../standard-library/mutex.md)<br/>
