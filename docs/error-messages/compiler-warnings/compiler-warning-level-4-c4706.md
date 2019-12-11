---
title: Advertencia del compilador (nivel 4) C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: 2ff8794dcf29539b492f53bfdf6f0810988c0f72
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989907"
---
# <a name="compiler-warning-level-4-c4706"></a>Advertencia del compilador (nivel 4) C4706

asignación dentro de la expresión condicional

El valor de prueba en una expresión condicional era el resultado de una asignación.

Una asignación tiene un valor (el valor en el lado izquierdo de la asignación) que se puede usar legalmente en otra expresión, incluida una expresión de prueba.

En el ejemplo siguiente se genera C4706:

```cpp
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

La advertencia se producirá incluso si se duplican los paréntesis en torno a la condición de prueba:

```cpp
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

Si su intención es probar una relación y no hacer una asignación, use el operador `==`. Por ejemplo, la línea siguiente comprueba si a y b son iguales:

```cpp
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

Si tiene previsto convertir el valor de prueba en el resultado de una asignación, realice una prueba para asegurarse de que la asignación es distinta de cero o no es NULL. Por ejemplo, el código siguiente no generará esta ADVERTENCIA:

```cpp
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
