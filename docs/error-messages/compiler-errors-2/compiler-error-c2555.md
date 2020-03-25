---
title: Error del compilador C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: ebf3e4a3aff48311edd5fb95b01a7b2d23990231
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202429"
---
# <a name="compiler-error-c2555"></a>Error del compilador C2555

' Class1:: function1 ': el tipo de valor devuelto de la función virtual de invalidación es distinto y no es covariante de ' clase2:: función2 '

Una función virtual y una función de reemplazo derivada tienen listas de parámetros idénticas pero diferentes tipos de valor devueltos. Una función de invalidación en una clase derivada no puede diferir de una función virtual en una clase base solo por su tipo de valor devuelto.

Para resolver este error, convierta el valor devuelto después de llamar a la función virtual.

También puede ver este error Si compila con/CLR.   Por ejemplo, el equivalente C++ visual de la siguiente C# declaración:

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

En el ejemplo siguiente se genera C2555:

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```
