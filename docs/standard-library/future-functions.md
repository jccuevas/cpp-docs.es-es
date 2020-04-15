---
title: '&lt;future&gt; (Funciones)'
ms.date: 11/04/2016
f1_keywords:
- future/std::async
- future/std::future_category
- future/std::make_error_code
- future/std::make_error_condition
- future/std::swap
ms.assetid: 1e3acc1e-736a-42dc-ade2-b2fe69aa96bc
helpviewer_keywords:
- std::async [C++]
- std::future_category [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::swap [C++]
ms.openlocfilehash: 16c26212cac13602e981f42d8333518da90615fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370662"
---
# <a name="ltfuturegt-functions"></a>&lt;future&gt; (Funciones)

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[swap](#swap)|

## <a name="async"></a><a name="async"></a>Async

Representa un *proveedor asincrónico.*

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>Parámetros

*Política*\
Valor [launch](../standard-library/future-enums.md#launch).

### <a name="remarks"></a>Observaciones

Definiciones de las abreviaturas:

|||
|-|-|
|*Dfn*|Resultado de llamar a `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Resultado de las llamadas `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty*|El tipo `result_of<Fn(ArgTypes...)>::type`.|

La primera función de plantilla devuelve `async(launch::any, fn, args...)`.

La segunda función devuelve un objeto `future<Ty>` cuyo *estado asincrónico asociado* contiene un resultado junto con los valores de *dfn* y *dargs* y un objeto de subproceso para administrar un subproceso de ejecución independiente.

A menos que `decay<Fn>::type` sea un tipo distinto de launch, la segunda función no participa en la resolución de sobrecarga.

El estándar C++ indica que si la directiva es launch::async, la función crea un nuevo subproceso. Sin embargo, la implementación de Microsoft no es conforme actualmente. Obtiene sus subprocesos de Windows ThreadPool, que en algunos casos puede proporcionar un subproceso reciclado en lugar de uno nuevo. Esto significa `launch::async` que la directiva `launch::async|launch::deferred`se implementa realmente como .  Otra implicación de la implementación basada en ThreadPool es que no hay ninguna garantía de que las variables locales de subprocesos se destruirán cuando se complete el subproceso. Si el subproceso se recicla y `async`se proporciona a una nueva llamada a , las variables antiguas seguirán existiendo. Por lo tanto, se recomienda no utilizar `async`variables locales de subprocesos con .

Si *policy* policy `launch::deferred`es , la función marca su estado asincrónico asociado como mantener una *función diferida* y devuelve. La primera llamada a cualquier función no cronometrada que espera hasta que el estado asincrónico asociado esté listo llama a la función aplazada evaluando `INVOKE(dfn, dargs..., Ty)`.

En todos los casos, el estado asincrónico asociado del objeto `future` no se establece en *listo* hasta que la evaluación de `INVOKE(dfn, dargs..., Ty)` no se completa, ya sea iniciando una excepción o volviendo normalmente. El resultado del estado asincrónico asociado es una excepción si se produjo alguna, o cualquier valor devuelto por la evaluación.

> [!NOTE]
> Para un `future` (o el último [shared_future](../standard-library/shared-future-class.md)) adjunto a una tarea iniciada con `std::async`, el destructor se bloquea si la tarea no se ha completado; es decir, se bloquea si este subproceso aún no ha llamado a `.get()` o `.wait()` y la tarea todavía se está ejecutando. Si un `future` obtenido de `std::async` se desplaza fuera del ámbito local, otro código que lo utilice debe saber que su destructor se puede bloquear para que el estado compartido se convierta en listo.

La pseudofunción `INVOKE` se define en [ \<>funcional. ](../standard-library/functional.md)

## <a name="future_category"></a><a name="future_category"></a>future_category

Devuelve una referencia al objeto [error_category](../standard-library/error-category-class.md) que caracteriza los errores asociados a objetos `future`.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a><a name="make_error_code"></a>make_error_code

Crea un [error_code](../standard-library/error-code-class.md) junto con el objeto [error_category](../standard-library/error-category-class.md) que caracteriza los errores de [future](../standard-library/future-class.md).

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parámetros

*Errno*\
Valor [future_errc](../standard-library/future-enums.md#future_errc) que identifica el error notificado.

### <a name="return-value"></a>Valor devuelto

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a><a name="make_error_condition"></a>make_error_condition

Crea una [error_condition](../standard-library/error-condition-class.md) junto con el objeto [error_category](../standard-library/error-category-class.md) que caracteriza los errores de [future](../standard-library/future-class.md).

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parámetros

*Errno*\
Valor [future_errc](../standard-library/future-enums.md#future_errc) que identifica el error notificado.

### <a name="return-value"></a>Valor devuelto

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a><a name="swap"></a>Intercambio

Intercambia el *estado asincrónico asociado* de un `promise` objeto con el de otro.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parámetros

*Izquierda*\
Objeto `promise` izquierdo.

*Correcto*\
Objeto `promise` derecho.

## <a name="see-also"></a>Consulte también

[\<>futuro](../standard-library/future.md)
