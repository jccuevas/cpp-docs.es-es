---
title: Error matemático M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 44f406881d64d13e23ca2c0911ee278c864a2c11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50510791"
---
# <a name="math-error-m6111"></a>Error matemático M6111

subdesbordamiento de la pila

Una operación de punto flotante dieron lugar a un subdesbordamiento de la pila en el coprocesador 8087/287/387 o en el emulador.

Este error se debe a menudo mediante una llamada a un `long double` función que no devuelve un valor. Por ejemplo, lo siguiente genera este error cuando compile y ejecute:

```
long double ld() {};
main ()
{
  ld();
}
```

El programa termina con el código de salida 139.