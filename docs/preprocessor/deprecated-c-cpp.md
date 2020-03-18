---
title: pragma en desuso
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 5694c5175ff23952c601884243b428a842278b7d
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446469"
---
# <a name="deprecated-pragma"></a>pragma en desuso

La pragma **desusada** permite indicar que una función, tipo o cualquier otro identificador ya no se admite en una versión futura o que ya no debe usarse.

> [!NOTE]
> Para obtener información sobre el atributo de `[[deprecated]]` de C++ 14, así como instrucciones sobre Cuándo usar ese atributo en lugar del modificador de `__declspec(deprecated)` de Microsoft o el pragma en **desuso** , vea [atributos en C++ ](../cpp/attributes.md).

## <a name="syntax"></a>Sintaxis

> **#pragma en desuso (** *identificador1* [ **,** *identificador2* ...] **)**

## <a name="remarks"></a>Observaciones

Cuando el compilador encuentra un identificador especificado por una pragma **desusada** , emite la advertencia del compilador [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).

Puede desusar nombres de macro. Coloque el nombre de la macro entre comillas; de lo contrario se producirá la expansión de la macro.

Dado que la Directiva pragma en **desuso** funciona en todos los identificadores coincidentes y no tiene en cuenta las signaturas, no es la mejor opción para dejar en desuso versiones específicas de funciones sobrecargadas. Cualquier nombre de función coincidente que se incluye en el ámbito desencadena la advertencia.

Se recomienda usar el atributo de `[[deprecated]]` de C++ 14, siempre que sea posible, en lugar de la Directiva pragma **desusada** . El modificador de declaración __declspec específico de Microsoft [(en desuso)](../cpp/deprecated-cpp.md) también es una opción mejor en muchos casos que la pragma **desusada** . El atributo `[[deprecated]]` y el modificador `__declspec(deprecated)` permiten especificar el estado en desuso para determinados formatos de funciones sobrecargadas. La advertencia de diagnóstico solo aparece en referencias a la función sobrecargada específica a la que se aplica el atributo o modificador.

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

## <a name="see-also"></a>Consulte también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)