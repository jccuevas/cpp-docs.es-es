---
title: ADVERTENCIA del compilador (nivel 4) C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 828b38aeb184741af284f2d7722017b24f6255a3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198593"
---
# <a name="compiler-warning-level-4-c4800"></a>ADVERTENCIA del compilador (nivel 4) C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 y versiones posteriores:
> Conversión implícita de '*tipo*' a bool. Posible pérdida de información
::: moniker-end

C4800 es una advertencia de nivel 3 en Visual Studio 2015 y versiones anteriores:
> '*Type*': forzando valor a bool ' true ' o ' false ' (ADVERTENCIA de rendimiento)

Esta advertencia se genera cuando un valor se convierte implícitamente en el tipo `bool`. Normalmente, este mensaje se debe a que se asignan `int` variables a `bool` variables en las que la variable `int` solo contiene valores **true** y **false**, y se puede volver a declarar como tipo `bool`. Si no puede volver a escribir la expresión para usar el tipo `bool`, puede Agregar "`!=0`" a la expresión, que proporciona el tipo de expresión `bool`. La conversión de la expresión al tipo `bool` no deshabilita la advertencia, que es por diseño.

::: moniker range=">= vs-2017"
Esta advertencia no se emite en Visual Studio 2017.
::: moniker-end

::: moniker range=">= vs-2019"
Esta advertencia está desactivada de forma predeterminada a partir de Visual Studio 2019. Use __/w__*n*__4800__ para habilitar C4800 como advertencia de nivel *n* o [/Wall](../../build/reference/compiler-option-warning-level.md) para habilitar todas las advertencias que están desactivadas de forma predeterminada. Para obtener más información, vea [advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
::: moniker-end

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4800 y se muestra cómo corregirlo:

```cpp
// C4800.cpp
// compile with: /W4 /w44800
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```
