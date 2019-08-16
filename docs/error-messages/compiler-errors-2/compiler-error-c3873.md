---
title: Error del compilador C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: ca70af12ef3223c8c5950f0fa98b1c63a2dd3a4c
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450823"
---
# <a name="compiler-error-c3873"></a>Error del compilador C3873

'char': este carácter no se permite como primer carácter de un identificador

El compilador de C++ respeta el estándar de C++11 respecto de los caracteres permitidos en un identificador. Solo se permiten determinados rangos de caracteres y nombres de carácter universal en un identificador. Se aplican restricciones adicionales respecto del carácter inicial de un identificador. Para obtener más información y una lista de caracteres permitidos y rangos de nombre de carácter universal, consulte [Identifiers](../../cpp/identifiers-cpp.md).

El rango de caracteres permitidos en un identificador es menos restrictivo cuando se compila código C++/CLI. Los identificadores en el código compilado con/CLR deben seguir [estándar ECMA-335: Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

En el siguiente ejemplo se genera el error C3873:

```
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```