---
title: Error del evaluador de expresiones CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: 71e4e3e87b33849e6b487b79268ebc9574c2e5a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511870"
---
# <a name="expression-evaluator-error-cxx0064"></a>Error del evaluador de expresiones CXX0064

no se puede establecer un punto de interrupción en la función miembro virtual enlazada

Un punto de interrupción se estableció en una función miembro virtual a través de un puntero a un objeto, como:

```
pClass->vfunc( int );
```

Un punto de interrupción se puede establecer en una función virtual escribiendo la clase, como:

```
Class::vfunc( int );
```

Este error es idéntico a CAN0064.