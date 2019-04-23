---
title: Advertencia del compilador (nivel 4) C4062
ms.date: 04/05/2019
f1_keywords:
- C4062
helpviewer_keywords:
- C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
ms.openlocfilehash: 79658afc31565b708cdbd8a88f49b887cdd10cf3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59237190"
---
# <a name="compiler-warning-level-4-c4062"></a>Advertencia del compilador (nivel 4) C4062

> enumerador '*identificador*'en el conmutador de la enumeración'*enumeración*' no está controlado

El enumerador *identificador* no tiene ningún asociado `case` controlador en un `switch` instrucción y no hay ningún `default` etiqueta que puede detectarla. El caso de que falta puede ser un descuido y es un posible error en el código. Para una advertencia relacionada con los enumeradores no utilizadas en `switch` las instrucciones que tienen un `default` case, consulte [C4061](compiler-warning-level-4-c4061.md).

De forma predeterminada, esta advertencia está desactivada. Para obtener más información acerca de cómo habilitar las advertencias que están desactivadas de forma predeterminada, consulte [compilador advertencias que están desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4062 y muestra cómo corregirlo:

```cpp
// C4062.cpp
// compile with: /EHsc /W4
#pragma warning(default : 4062)
enum E { a, b, c };
void func ( E e ) {
   switch(e) {
      case a:
      case b:
   // case c:  // to fix, uncomment this line
      break;   // no default label
   }   // C4062, enumerator 'c' not handled
}

int main() {
}
```

## <a name="see-also"></a>Vea también

[Advertencia del compilador (nivel 4) C4061](compiler-warning-level-4-c4061.md)
