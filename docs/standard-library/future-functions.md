---
title: '&lt;future&gt; (Funciones) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: bbb724747052c6dd636199fd1cabdf97d2bd4045
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2018
ms.locfileid: "39027402"
---
# <a name="ltfuturegt-functions"></a>&lt;future&gt; (Funciones)

||||
|-|-|-|
|[async](#async)|[future_category](#future_category)|[make_error_code](#make_error_code)|
|[make_error_condition](#make_error_condition)|[swap](#swap)|

## <a name="async"></a>  async

Representa un *proveedor asincrónico*.

```cpp
template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(Fn&& fn, ArgTypes&&... args);

template <class Fn, class... ArgTypes>
future<typename result_of<Fn(ArgTypes...)>::type>
    async(launch policy, Fn&& fn, ArgTypes&&... args);
```

### <a name="parameters"></a>Parámetros

*directiva* A [iniciar](../standard-library/future-enums.md#launch) valor.

### <a name="remarks"></a>Comentarios

Definiciones de las abreviaturas:

|||
|-|-|
|*dfn*|Resultado de llamar a `decay_copy(forward<Fn>(fn))`.|
|*dargs*|Resultado de las llamadas `decay_copy(forward<ArgsTypes>(args...))`.|
|*Ty*|El tipo `result_of<Fn(ArgTypes...)>::type`.|

La primera función de plantilla devuelve `async(launch::any, fn, args...)`.

La segunda función devuelve un objeto `future<Ty>` cuyo *estado asincrónico asociado* contiene un resultado junto con los valores de *dfn* y *dargs* y un objeto de subproceso para administrar un subproceso de ejecución independiente.

A menos que `decay<Fn>::type` sea un tipo distinto de launch, la segunda función no participa en la resolución de sobrecarga.

El estándar de C++ indica que si launch::async directiva, la función crea un nuevo subproceso. Sin embargo la implementación de Microsoft es actualmente no conforme. Obtiene los subprocesos de ThreadPool de Windows, que, en algunos casos, puede proporcionar un subproceso reciclando en lugar de una nueva. Esto significa que el `launch::async` directiva se implementa realmente como `launch::async|launch::deferred`.  Otra implicación de la implementación basada en el grupo de subprocesos es que no hay ninguna garantía de que las variables locales del subproceso se destruirán cuando finaliza el subproceso. Si el subproceso se recicle y proporciona a una nueva llamada a `async`, las variables anteriores seguirán existiendo. Por lo tanto, se recomienda que no use variables de subproceso local con `async`.

Si *directiva* es `launch::deferred`, la función marca su estado asincrónico asociado como que contiene un *función aplazada* y devuelve. La primera llamada a cualquier función no cronometrada que espera hasta que el estado asincrónico asociado esté listo llama a la función aplazada evaluando `INVOKE(dfn, dargs..., Ty)`.

En todos los casos, el estado asincrónico asociado del objeto `future` no se establece en *listo* hasta que la evaluación de `INVOKE(dfn, dargs..., Ty)` no se completa, ya sea iniciando una excepción o volviendo normalmente. El resultado del estado asincrónico asociado es una excepción si se produjo alguna, o cualquier valor devuelto por la evaluación.

> [!NOTE]
> Para un `future` (o el último [shared_future](../standard-library/shared-future-class.md)) adjunto a una tarea iniciada con `std::async`, el destructor se bloquea si la tarea no se ha completado; es decir, se bloquea si este subproceso aún no ha llamado a `.get()` o `.wait()` y la tarea todavía se está ejecutando. Si un `future` obtenido de `std::async` se desplaza fuera del ámbito local, otro código que lo utilice debe saber que su destructor se puede bloquear para que el estado compartido se convierta en listo.

La pseudofunción `INVOKE` se define en [\<functional>](../standard-library/functional.md).

## <a name="future_category"></a>  future_category

Devuelve una referencia al objeto [error_category](../standard-library/error-category-class.md) que caracteriza los errores asociados a objetos `future`.

```cpp
const error_category& future_category() noexcept;
```

## <a name="make_error_code"></a>  make_error_code

Crea un [error_code](../standard-library/error-code-class.md) junto con el objeto [error_category](../standard-library/error-category-class.md) que caracteriza los errores de [future](../standard-library/future-class.md).

```cpp
inline error_code make_error_code(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parámetros

*Errno* A [future_errc](../standard-library/future-enums.md#future_errc) valor que identifica el error notificado.

### <a name="return-value"></a>Valor devuelto

`error_code(static_cast<int>(Errno), future_category());`

## <a name="make_error_condition"></a>  make_error_condition

Crea una [error_condition](../standard-library/error-condition-class.md) junto con el objeto [error_category](../standard-library/error-category-class.md) que caracteriza los errores de [future](../standard-library/future-class.md).

```cpp
inline error_condition make_error_condition(future_errc Errno) noexcept;
```

### <a name="parameters"></a>Parámetros

*Errno* A [future_errc](../standard-library/future-enums.md#future_errc) valor que identifica el error notificado.

### <a name="return-value"></a>Valor devuelto

`error_condition(static_cast<int>(Errno), future_category());`

## <a name="swap"></a>  swap

Intercambia el *estado asincrónico asociado* de un objeto `promise` con el de otro.

```cpp
template <class Ty>
void swap(promise<Ty>& Left, promise<Ty>& Right) noexcept;

template <class Ty, class... ArgTypes>
void swap(packaged_task<Ty(ArgTypes...)>& Left, packaged_task<Ty(ArgTypes...)>& Right) noexcept;
```

### <a name="parameters"></a>Parámetros

*Izquierda* la izquierda `promise` objeto.

*Derecha* derecho `promise` objeto.

## <a name="see-also"></a>Vea también

[\<future>](../standard-library/future.md)<br/>
