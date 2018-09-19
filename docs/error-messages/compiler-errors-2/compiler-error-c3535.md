---
title: Error del compilador C3535 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3535
dev_langs:
- C++
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 215fa52f892cb569b32335ca439811eb07b28dc7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094083"
---
# <a name="compiler-error-c3535"></a>Error del compilador C3535

no se puede deducir el tipo de 'tipo1' de 'tipo2'

El tipo de la variable declarada por el `auto` palabra clave no se puede deducir el tipo de la expresión de inicialización. Por ejemplo, este error se produce si se evalúa la expresión de inicialización en `void`, que no es un tipo.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Asegúrese de que el tipo de la expresión de inicialización no es `void`.

1. Asegúrese de que la declaración no es un puntero a un tipo fundamental. Para obtener más información, consulte [tipos fundamentales](../../cpp/fundamental-types-cpp.md).

1. Asegúrese de que, si la declaración es un puntero a un tipo, la expresión de inicialización es un tipo de puntero.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3535 porque la expresión de inicialización se evalúa como `void`.

```
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3535 porque la instrucción declara la variable `x` como un puntero a un tipo deducido, pero el tipo del inicializador de la expresión es doble. Por lo tanto, el compilador no puede deducir el tipo de la variable.

```
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C3535 porque variable `p` declara un puntero a un tipo deducido, pero la expresión de inicialización no es un tipo de puntero.

```
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>Vea también

[Auto (palabra clave)](../../cpp/auto-keyword.md)<br/>
[Tipos fundamentales](../../cpp/fundamental-types-cpp.md)