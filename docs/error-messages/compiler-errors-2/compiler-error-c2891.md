---
title: Error del compilador C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: 2544cfc9e8cff283a7c3e0ace499408bb84cd046
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201647"
---
# <a name="compiler-error-c2891"></a>Error del compilador C2891

' parámetro ': no se puede adquirir la dirección de un parámetro de plantilla

No se puede tomar la dirección de un parámetro de plantilla a menos que sea un valor l. Los parámetros de tipo no se lvalues porque no tienen ninguna dirección. Los valores sin tipo de las listas de parámetros de plantilla que no son lvalues tampoco tienen una dirección. Este es un ejemplo de código que provoca el error del compilador C2891, porque el valor que se pasa como parámetro de plantilla es una copia generada por el compilador del argumento de plantilla.

```
template <int i> int* f() { return &i; }
```

Los parámetros de plantilla que son lvalues, como los tipos de referencia, pueden tomar su dirección.

```
template <int& r> int* f() { return &r; }
```

Para corregir este error, no tome la dirección de un parámetro de plantilla a menos que sea un valor l.
