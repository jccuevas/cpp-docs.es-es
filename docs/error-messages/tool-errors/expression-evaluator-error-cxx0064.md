---
title: Error del evaluador de expresiones CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: f763754299ed9257fb909b49a7a19c6f3ad58681
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184468"
---
# <a name="expression-evaluator-error-cxx0064"></a>Error del evaluador de expresiones CXX0064

no se puede establecer un punto de interrupción en una función miembro virtual enlazada

Se estableció un punto de interrupción en una función miembro virtual a través de un puntero a un objeto, como:

```
pClass->vfunc( int );
```

Se puede establecer un punto de interrupción en una función virtual escribiendo la clase, por ejemplo:

```
Class::vfunc( int );
```

Este error es idéntico a CAN0064.
