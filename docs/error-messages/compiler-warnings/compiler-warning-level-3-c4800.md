---
title: Advertencia (nivel 3) del compilador C4800 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5a19c27731192a5fe2930aec3e78fb66d790484
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090913"
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