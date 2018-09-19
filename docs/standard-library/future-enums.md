---
title: '&lt;future&gt; (Enumeraciones) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- future/std::future_errc
- future/std::future_status
- future/std::launch
ms.assetid: 8c675645-db47-4cab-bc0e-7b87f8a302df
ms.openlocfilehash: 0056d54844e9396d517fd44c3649f1bc9605829b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700562"
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
