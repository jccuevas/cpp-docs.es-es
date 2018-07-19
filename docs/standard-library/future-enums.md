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
ms.openlocfilehash: 6e228eb538a0d281dff8066390b0c6dd2e7ea4d8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33843852"
---
# <a name="ltfuturegt-enums"></a>&lt;future&gt; (Enumeraciones)

||||
|-|-|-|
|[future_errc](#future_errc)|[future_status](#future_status)|[Iniciar](#launch)|

## <a name="future_errc"></a>  future_errc (Enumeración)

Proporciona nombres simbólicos para todos los errores notificados por la clase [future_error](../standard-library/future-error-class.md).

class future_errc { broken_promise, future_already_retrieved, promise_already_satisfied, no_state };

## <a name="future_status"></a>  future_status (Enumeración)

Proporciona nombres simbólicos para los motivos que una función que ha agotado el tiempo de espera puede devolver.

```cpp
enum future_status{    ready,
    timeout,
 deferred};
```

## <a name="launch"></a>  launch (Enumeración)

Representa un tipo de máscara de bits que describe los posibles modos para la función de plantilla [async](../standard-library/future-functions.md#async).

class launch{ async, deferred };

## <a name="see-also"></a>Vea también

[\<future>](../standard-library/future.md)<br/>
