---
title: Error matemático M6111 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95a55ec6b7cdf0b6e4c15bd283dde77c610698fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074830"
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