---
title: '&lt;future&gt; (Enumeraciones)'
ms.date: 11/04/2016
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 0f1064fdf434560c3130d1254512470cc5bc1ee0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370694"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; (Enumeraciones)

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[Lanzamiento](#launch)|

## <a name="future_errc-enumeration"></a><a name="future_errc"></a>future_errc (Enumeración)

Proporciona nombres simbólicos para todos los errores notificados por la clase [future_error](../standard-library/future-error-class.md).

```cpp
class future_errc {
   broken_promise,
   future_already_retrieved,
   promise_already_satisfied,
   no_state
   };
```

## <a name="future_status-enumeration"></a><a name="future_status"></a>future_status (enumeración)

Proporciona nombres simbólicos para los motivos que una función que ha agotado el tiempo de espera puede devolver.

```cpp
enum future_status{
    ready,
    timeout,
    deferred
};
```

## <a name="launch-enumeration"></a><a name="launch"></a>iniciar la enumeración

Representa un tipo de máscara de bits que describe los posibles modos para la función de plantilla [async](../standard-library/future-functions.md#async).

```cpp
class launch{
   async,
   deferred
   };
```

## <a name="see-also"></a>Consulte también

[\<>futuro](../standard-library/future.md)
