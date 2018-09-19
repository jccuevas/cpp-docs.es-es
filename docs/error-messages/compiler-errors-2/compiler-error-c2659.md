---
title: Error del compilador C2659 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2659
dev_langs:
- C++
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a658bc000ab0f7194e4806133b949ee0f7cf9ff9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062948"
---
# <a name="compiler-error-c2659"></a>Error del compilador C2659

'operador' : función sobrecargada como operando izquierdo

Había una función en el operando izquierdo del operador especificado. La causa más común de este error es que el compilador ha analizado el identificador situado a la izquierda del operador como una función, cuando el desarrollador pretendía que fuera una variable. Para obtener más información, consulte Wikipedia artículo [análisis más molestos](http://en.wikipedia.org/wiki/Most_vexing_parse). En este ejemplo se muestra una declaración de función y una definición de variable que pueden confundirse fácilmente:

```
// C2659a.cpp
// Compile using: cl /W4 /EHsc C2659a.cpp
#include <string>
using namespace std;

int main()
{
   string string1(); // string1 is a function returning string
   string string2{}; // string2 is a string initialized to empty

   string1 = "String 1"; // C2659
   string2 = "String 2";
}
```

Para resolver este problema, cambie la declaración del identificador para que no pueda analizarse como una declaración de función.

El error C2659 también puede producirse cuando la función tiene un tipo que no se puede usar en el operando izquierdo del operador especificado en la expresión. En este ejemplo se genera el error C2659 cuando el código asigna un puntero de función a una función:

```
// C2659b.cpp
// Compile using: cl /W4 /EHsc C2659b.cpp
int func0(void) { return 42; }
int (*func1)(void);

int main()
{
   func1 = func0;
   func0 = func1; // C2659
}
```