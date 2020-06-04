---
title: Error del compilador C2665
ms.date: 11/04/2016
f1_keywords:
- C2665
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
ms.openlocfilehash: 95ca5ea846f9cd45bdb1e9706ae377589d37a285
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756024"
---
# <a name="compiler-error-c2665"></a>Error del compilador C2665

' function ': ninguna de las sobrecargas número1 puede convertir el parámetro número2 del tipo ' type '

Un parámetro de la función sobrecargada no se puede convertir al tipo requerido.  Soluciones posibles:

- Proporcione un operador de conversión.

- Use la conversión explícita.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C2665.

```cpp
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```
