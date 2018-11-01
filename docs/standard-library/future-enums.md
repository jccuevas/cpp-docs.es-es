---
title: '&lt;future&gt; (Enumeraciones)'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 1e487128d4af5c6f9b3f29f5c71e52f616e1807a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655339"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; (Enumeraciones)

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[iniciar](#launch)|

## <a name="future_errc"></a>  future_errc (Enumeración)

Proporciona nombres simbólicos para todos los errores notificados por la clase [future_error](../standard-library/future-error-class.md).

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status"></a>  future_status (Enumeración)

Proporciona nombres simbólicos para los motivos que una función que ha agotado el tiempo de espera puede devolver.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch"></a>  launch (Enumeración)

Representa un tipo de máscara de bits que describe los posibles modos para la función de plantilla [async](../standard-library/future-functions.md#async).

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Vea también

[\<future>](../standard-library/future.md)<br/>
