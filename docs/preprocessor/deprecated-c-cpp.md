---
title: (C/C++) en desuso
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: edbad2f666ac0c6546f03da0ffbdb87f19b7e4e3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642824"
---
# <a name="deprecated-cc"></a>(C/C++) en desuso

El **en desuso** permite pragma indicar que una función, tipo o cualquier otro identificador ya no es posible que admite en una futura versión o ya no se debe usar.

> [!NOTE]
> Para obtener información acerca de C ++ 14 `[[deprecated]]` atributo y una guía sobre cuándo usar ese atributo vs el modificador declspec de Microsoft o la directiva pragma, consulte [atributos estándar de C++](../cpp/attributes.md) atributo.

## <a name="syntax"></a>Sintaxis

```
#pragma deprecated( identifier1 [,identifier2, ...] )
```

## <a name="remarks"></a>Comentarios

Cuando el compilador encuentra un identificador especificado por un **en desuso** pragma, que emite la advertencia del compilador [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).

Puede desusar nombres de macro. Coloque el nombre de la macro entre comillas; de lo contrario se producirá la expansión de la macro.

Dado que el **en desuso** pragma funciona en todos los identificadores que coinciden y no tiene en cuenta las firmas, no es la mejor opción para dejar de usar las versiones específicas de funciones sobrecargadas. Cualquier nombre de función que se incluyen en el ámbito desencadena la advertencia.

Se recomienda usar C ++ 14 `[[deprecated]]` atributo, cuando sea posible, en lugar de la **en desuso** pragma. Específico de Microsoft [__declspec (deprecated)](../cpp/deprecated-cpp.md) modificador declaración también es una opción mejor en muchos casos que el **en desuso** pragma. El `[[deprecated]]` atributo y `__declspec(deprecated)` modificador le permiten especificar el estado en desuso para formas concretas de funciones sobrecargadas. Las referencias a la función sobrecargada específica solo aparece la advertencia diagnóstico el atributo o modificador se aplica a.

## <a name="example"></a>Ejemplo

```cpp
// pragma_directive_deprecated.cpp
// compile with: /W3
#include <stdio.h>
void func1(void) {
}

void func2(void) {
}

int main() {
   func1();
   func2();
   #pragma deprecated(func1, func2)
   func1();   // C4995
   func2();   // C4995
}
```

En el ejemplo siguiente se muestra cómo desusar una clase:

```cpp
// pragma_directive_deprecated2.cpp
// compile with: /W3
#pragma deprecated(X)
class X {  // C4995
public:
   void f(){}
};

int main() {
   X x;   // C4995
}
```

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)