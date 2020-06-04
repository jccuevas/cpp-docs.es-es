---
title: Advertencia del compilador (nivel 4) C4256
ms.date: 11/04/2016
f1_keywords:
- C4256
helpviewer_keywords:
- C4256
ms.assetid: a755a32e-895a-4837-a2b5-4ea06b736798
ms.openlocfilehash: 1ec3e64548cead53cea906cdf2abd3dd25ee06d4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991383"
---
# <a name="compiler-warning-level-4-c4256"></a>Advertencia del compilador (nivel 4) C4256

' función ': el constructor de la clase con bases virtuales tiene '... '; es posible que las llamadas no sean compatibles con versiones anteriores de VisualC++

Posible incompatibilidad.

Considere el ejemplo de código siguiente: Si la definición del constructor S2:: S2 (int i,...) se compiló con una versión del compilador de C++ Microsoft anterior a la versión 7, pero el ejemplo siguiente se compila con la versión actual, la llamada al constructor de S3 no funcionaría correctamente debido a un cambio de Convención de llamada de casos especiales. Si ambos se compilaron con C++ visual 6,0, la llamada no funcionará bien, a menos que no se haya pasado ningún parámetro para los puntos suspensivos.

Para corregir esta advertencia,

1. No utilice puntos suspensivos en un constructor.

1. Asegúrese de que todos los componentes del proyecto se compilan con la versión actual (incluidas las bibliotecas que puedan definir o que hagan referencia a esta clase) y, a continuación, deshabilite la advertencia mediante la pragma [Warning](../../preprocessor/warning.md) .

En el ejemplo siguiente se genera C4256:

```cpp
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
