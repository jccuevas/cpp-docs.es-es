---
title: Advertencia del compilador (nivel 4) C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: bef825f546573b878c415c385e1a2a2286e08db4
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444905"
---
# <a name="compiler-warning-level-4-c4127"></a>Advertencia del compilador (nivel 4) C4127

> la expresión condicional es constante

## <a name="remarks"></a>Comentarios

La expresión de control de una instrucción **If** o un bucle **While** se evalúa como una constante. Debido a su uso común de idiomático, a partir de Visual Studio 2015 Update 3, las constantes triviales como 1 o **true** no desencadenan la advertencia, a menos que sean el resultado de una operación en una expresión.

Si la expresión de control de un bucle **While** es una constante porque el bucle sale en el centro, considere la posibilidad de reemplazar el bucle **While** con un bucle **for** . Puede omitir la inicialización, la prueba de terminación y el incremento de bucle de un bucle **for** , lo que hace que el bucle sea infinito, al igual que `while(1)`, y puede salir del bucle desde el cuerpo de la instrucción **for** .

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran dos formas de generar C4127 y se muestra cómo usar un bucle for para evitar la ADVERTENCIA:

```cpp
// C4127.cpp
// compile with: /W4
#include <stdio.h>
int main() {
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```

Esta advertencia también se puede generar cuando se usa una constante de tiempo de compilación en una expresión condicional:


```cpp
#include <string>

using namespace std;

template<size_t S, class T>
void MyFunc()
{
   if (sizeof(T) >= S) // C4127. "Consider using 'if constexpr' statement instead"
   {
   }
}

class Foo
{
   int i;
   string s;
};

int main()
{
   Foo f;
   MyFunc<4, Foo>();
}
```