---
title: Advertencia del compilador (niveles 1 y 4) C4112
ms.date: 11/04/2016
f1_keywords:
- C4112
helpviewer_keywords:
- C4112
ms.assetid: aff64897-bb79-4a67-9b6f-902c6d44f3dc
ms.openlocfilehash: f614373e1b96de2c8167d7981c0a87a4e1c58435
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991232"
---
# <a name="compiler-warning-levels-1-and-4-c4112"></a>Advertencia del compilador (niveles 1 y 4) C4112

la línea \#requiere un entero entre 1 y número

La directiva [#line](../../preprocessor/hash-line-directive-c-cpp.md) especifica un parámetro entero que está fuera del intervalo permitido.

Si el parámetro especificado es menor que 1, el contador de línea se restablece en 1. Si el parámetro especificado es mayor que *número*, que es el límite definido por el compilador, el contador de línea no se modifica. Esta es una advertencia de nivel 1 con la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) y una advertencia de nivel 4 con las extensiones de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

El ejemplo siguiente genera la advertencia C4112:

```cpp
// C4112.cpp
// compile with: /W4
#line 0   // C4112, value must be between 1 and number

int main() {
}
```
