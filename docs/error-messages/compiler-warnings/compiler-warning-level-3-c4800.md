---
title: Advertencia (nivel 4) del compilador C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 46418063625e16385497740a4f7e3d837e923156
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401558"
---
# <a name="compiler-warning-level-4-c4800"></a>Advertencia (nivel 4) del compilador C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 y versiones posteriores:
> Conversión implícita de '*tipo*' a bool. Pérdida de información posible.
::: moniker-end

C4800 es una advertencia de nivel 3 en Visual Studio 2015 y versiones anteriores:
> '*tipo*': forzar que el valor booleano 'true' o 'false' (advertencia de rendimiento)

Esta advertencia se genera cuando un valor se convierte implícitamente en el tipo `bool`. Normalmente, este mensaje se origina la asignación `int` variables a `bool` variables donde el `int` variable contiene solo valores **true** y **false**y podría ser puede volver a declarar como tipo `bool`. Si no se puede volver a escribir la expresión para usar el tipo `bool`, a continuación, puede agregar "`!=0`" a la expresión, que proporciona el tipo de expresión `bool`. Convertir la expresión al tipo `bool` no deshabilita la advertencia, que es así por diseño.

::: moniker range=">= vs-2017"
No se emite esta advertencia en Visual Studio 2017.
::: moniker-end

::: moniker range=">= vs-2019"
Esta advertencia está desactivada de forma predeterminada a partir de Visual Studio de 2019. Use __/w__*n*__4800__ para habilitar C4800 como un nivel *n* advertencia, o [/Wall](../../build/reference/compiler-option-warning-level.md) para habilitar todas las advertencias que están desactivados de forma predeterminada. Para obtener más información, consulte [compilador advertencias que está desactivado de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
::: moniker-end

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4800 y muestra cómo corregirlo:

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