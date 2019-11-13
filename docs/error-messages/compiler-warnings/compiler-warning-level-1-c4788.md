---
title: Advertencia del compilador (nivel 1) C4788
ms.date: 11/04/2016
f1_keywords:
- C4788
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
ms.openlocfilehash: 03ce38aaa910a410025c5cccdf39646d34104779
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052388"
---
# <a name="compiler-warning-level-1-c4788"></a>Advertencia del compilador (nivel 1) C4788

'identificador': el identificador se ha truncado a 'número' caracteres

El compilador limita la longitud máxima permitida para un nombre de función. Cuando el compilador genera funclets para código EH/SEH, forma el nombre de funclet anteponiendo el nombre de la función con algún texto, por ejemplo "__catch", "\__unwind" u otra cadena.

El nombre del funclet resultante puede ser demasiado largo y el compilador lo truncará y generará la advertencia C4788.

Para resolver esta advertencia, acorte el nombre de función original. Si la función es un método o una función de plantilla de C++, utilice una definición de tipos para parte del nombre. Por ejemplo:

```cpp
C1<x, y, z<T>>::C2<a,b,c>::f
```

se puede reemplazar por:

```cpp
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;
new_class::f
```

Esta advertencia solo se produce en el compilador x64.