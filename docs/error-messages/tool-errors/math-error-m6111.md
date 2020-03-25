---
title: Error matemático M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: e8abedf6a326a826d0c8ac513b15037c8bf89bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173696"
---
# <a name="math-error-m6111"></a>Error matemático M6111

subdesbordamiento de la pila

Una operación de punto flotante produjo un subdesbordamiento de la pila en el coprocesador 8087/287/387 o en el emulador.

Este error suele deberse a una llamada a una función `long double` que no devuelve un valor. Por ejemplo, lo siguiente genera este error cuando se compila y se ejecuta:

```
long double ld() {};
main ()
{
  ld();
}
```

El programa finaliza con el código de salida 139.
