---
title: Error del compilador C3872
ms.date: 11/04/2016
f1_keywords:
- C3872
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
ms.openlocfilehash: f4b116729ad3b84014d202deb31ab490435fcef3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761447"
---
# <a name="compiler-error-c3872"></a>Error del compilador C3872

'char': este carácter no se permite en un identificador.

El compilador de C++ respeta el estándar de C++11 respecto de los caracteres permitidos en un identificador. Solo se permiten determinados rangos de caracteres y nombres de carácter universal en un identificador. Se aplican restricciones adicionales respecto del carácter inicial de un identificador. Para obtener más información y una lista de caracteres permitidos y rangos de nombre de carácter universal, consulte [Identifiers](../../cpp/identifiers-cpp.md).

El rango de caracteres permitidos en un identificador es menos restrictivo cuando se compila código C++/CLI. Los identificadores del código compilado con /clr deben regirse por el  [Estándar ECMA-335: Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

En el siguiente ejemplo se genera el error C3872:

```cpp
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```
