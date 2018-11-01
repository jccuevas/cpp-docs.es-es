---
title: Advertencia del compilador (nivel 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: c51a4409c2a3028823462539343654b5eac365d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598177"
---
# <a name="compiler-warning-level-1-c4788"></a>Advertencia del compilador (nivel 1) C4788

'identificador': el identificador se ha truncado a 'número' caracteres

El compilador limita la longitud máxima permitida para un nombre de función. Cuando el compilador genera funclets para código EH/SEH, forma el nombre del funclet anteponiendo el nombre de función con algún texto, por ejemplo, "__catch," "\__unwind", u otra cadena.

El nombre del funclet resultante puede ser demasiado largo y el compilador lo truncará y generará la advertencia C4788.

Para resolver esta advertencia, acorte el nombre de función original. Si la función es un método o una función de plantilla de C++, utilice una definición de tipos para parte del nombre. Por ejemplo:

```
C1<x, y, z<T>>::C2<a,b,c>::f
```

se puede reemplazar por:

```
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Esta advertencia sólo aparece en el x64 compilador.