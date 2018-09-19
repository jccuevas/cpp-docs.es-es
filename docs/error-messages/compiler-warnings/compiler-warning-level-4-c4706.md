---
title: Compilador advertencia (nivel 4) C4706 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 843edeaf490f27475003e9303f7929b818e2b104
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036961"
---
# <a name="compiler-warning-level-4-c4706"></a>Advertencia del compilador (nivel 4) C4706

asignación de la expresión condicional

El valor de prueba en una expresión condicional fue el resultado de una asignación.

Una asignación tiene un valor (el valor en el lado izquierdo de la asignación) que puede utilizarse correctamente en otra expresión, incluida una expresión de prueba.

El ejemplo siguiente genera C4706:

```
// C4706a.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a  = b ) // C4706
   {
   }
}
```

La advertencia se produce si se doblan los paréntesis alrededor de la condición de prueba:

```
// C4706b.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a  =  b ) ) // C4706
   {
   }
}
```

Si su intención es probar una relación y no desea realizar una asignación, utilice el `==` operador. Por ejemplo, la línea siguiente prueba si un y b son iguales:

```
// C4706c.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a == b )
   {
   }
}
```

Si piensa realizar la prueba del resultado de una asignación de valor, una prueba para asegurarse de que la asignación es distinto de cero o no es null. Por ejemplo, el código siguiente no generará esta advertencia:

```
// C4706d.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a = b ) != 0 )
   {
   }
}
```