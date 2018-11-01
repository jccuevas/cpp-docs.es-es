---
title: Advertencia del compilador (nivel 3) C4800
ms.date: 11/04/2016
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 591b706249201691c7a9743d2cad082eb61e68b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636142"
---
# <a name="compiler-warning-level-3-c4800"></a>Advertencia del compilador (nivel 3) C4800

> '*tipo*': forzar que el valor booleano 'true' o 'false' (advertencia de rendimiento)

Esta advertencia se genera cuando un valor que no es `bool` se asignan o se convierten en tipo `bool`. Normalmente, este mensaje se origina la asignación `int` variables a `bool` variables donde el `int` variable contiene solo valores **true** y **false**y podría ser puede volver a declarar como tipo `bool`. Si no se puede volver a escribir la expresión para usar el tipo `bool`, a continuación, puede agregar "`!=0`" a la expresión, que proporciona el tipo de expresión `bool`. Convertir la expresión al tipo `bool` deshabilitar la advertencia, que es así por diseño.

En Visual Studio 2017 ya no genera esta advertencia.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4800 y muestra cómo corregirlo:

```cpp
// C4800.cpp
// compile with: /W3
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```