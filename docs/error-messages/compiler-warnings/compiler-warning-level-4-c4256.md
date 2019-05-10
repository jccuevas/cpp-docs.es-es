---
title: Advertencia del compilador (nivel 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 3e8a3ab1b11c719730016e6a0cd248770cd89af8
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447772"
---
# <a name="compiler-warning-level-4-c4256"></a>Advertencia del compilador (nivel 4) C4256

'function': constructor de clase con bases virtuales tiene '...'; las llamadas pueden no ser compatibles con versiones anteriores de Visual C++

Posible incompatibilidad.

Observe el siguiente ejemplo de código. Si la definición del constructor S2:: s2 (int i,...) se ha compilado con una versión de Microsoft C++ compilador antes de la versión 7, pero el ejemplo siguiente se compila con la versión actual, la llamada al constructor para S3 no funcionaría correctamente debido a un cambio de convención de llamada distinguieran mayúsculas y minúsculas. Si ambos se han compilado mediante Visual C++ 6.0, la llamada no funcionaría todo bien, a menos que se pasa ningún parámetro para los puntos suspensivos.

Para corregir esta advertencia,

1. No use el botón de puntos suspensivos en un constructor.

1. Asegúrese de que todos los componentes de su proyecto se compilan con la versión actual (incluidas las bibliotecas que pueden definir o hacer referencia a esta clase), a continuación, deshabilita la advertencia usando la [advertencia](../../preprocessor/warning.md) pragma.

El ejemplo siguiente genera C4256:

```
// C4256.cpp
// compile with: /W4
// #pragma warning(disable : 4256)
struct S1
{
};

struct S2: virtual public S1
{
   S2( int i, ... )    // C4256
   {
      i = 0;
   }
   /*
   // try the following line instead
   S2( int i)
   {
      i = 0;
   }
   */
};

void func1()
{
   S2 S3( 2, 1, 2 );   // C4256
   // try the following line instead
   // S2 S3( 2 );
}

int main()
{
}
```