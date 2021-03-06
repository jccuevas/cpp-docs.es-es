---
title: Advertencia del compilador (nivel 4) C4130
ms.date: 11/04/2016
f1_keywords:
- C4130
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
ms.openlocfilehash: 3bc632bf641fa3944cfd21dc405590c803498d80
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991570"
---
# <a name="compiler-warning-level-4-c4130"></a>Advertencia del compilador (nivel 4) C4130

'operador': operación lógica en dirección de una constante de cadena.

Usar el operador con la dirección de un literal de cadena produce código inesperado.

El ejemplo siguiente genera la advertencia C4130:

```cpp
// C4130.cpp
// compile with: /W4
int main()
{
   char *pc;
   pc = "Hello";
   if (pc == "Hello") // C4130
   {
   }
}
```

La instrucción **if** compara el valor almacenado en el puntero `pc` con la dirección de la cadena "Hola", que se asigna por separado cada vez que aparece la cadena en el código. La instrucción **if** no compara la cadena a la que apunta `pc` con la cadena "Hola".

Para comparar cadenas, use la función `strcmp` .
