---
title: break (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 3dda0b19fffaaf725ab363a0c4fe70d2ca54e3f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267720"
---
# <a name="break-statement-c"></a>break (Instrucción) (C++)

El **salto** instrucción finaliza la ejecución de la envolvente más próximo bucle o instrucción condicional en la que aparece. El control pasa a la instrucción que hay a continuación del final de la instrucción, si hay alguna.

## <a name="syntax"></a>Sintaxis

```
break;
```

## <a name="remarks"></a>Comentarios

El **salto** instrucción se utiliza con el atributo conditional [cambiar](../cpp/switch-statement-cpp.md) instrucción y con el [hacer](../cpp/do-while-statement-cpp.md), [para](../cpp/for-statement-cpp.md), y [al](../cpp/while-statement-cpp.md) las instrucciones de bucle.

En un **cambiar** instrucción, el **salto** instrucción hace que el programa ejecute la siguiente instrucción fuera el **cambiar** instrucción. Sin un **salto** instrucción, todas las instrucciones de la coincidente **caso** etiqueta al final de la **cambiar** instrucción, incluida la **predeterminada**cláusula, se ejecuta.

En los bucles, el **salto** instrucción finaliza la ejecución de envolvente **hacer**, **para**, o **mientras** instrucción. El control pasa a la instrucción que hay a continuación de la instrucción finalizada, si hay alguna.

Dentro de instrucciones anidadas, la **salto** instrucción finaliza solo la **hacer**, **para**, **cambiar**, o **mientras**instrucción que incluye de forma inmediata. Puede usar un **devolver** o **goto** instrucción para transferir el control desde el más profundamente anidada estructuras.

## <a name="example"></a>Ejemplo

El código siguiente muestra cómo usar el **salto** instrucción en un **para** bucle.

```cpp
#include <iostream>
using namespace std;

int main()
{
    // An example of a standard for loop
    for (int i = 1; i < 10; i++)
    {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }

    // An example of a range-based for loop
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};

    for (int i : nums) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
    }
}
```

```Output
In each case:
1
2
3
```

El código siguiente muestra cómo usar **salto** en un **mientras** bucle y un **hacer** bucle.

```cpp
#include <iostream>
using namespace std;

int main() {
    int i = 0;

    while (i < 10) {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    }

    i = 0;
    do {
        if (i == 4) {
            break;
        }
        cout << i << '\n';
        i++;
    } while (i < 10);
}
```

```Output
In each case:
0123
```

El código siguiente muestra cómo usar **salto** en una instrucción switch. Debe usar **salto** en todos los casos si desea tratar cada caso por separado; si no usas **salto**, la ejecución de código pasa a la siguiente expresión case.

```cpp
#include <iostream>
using namespace std;

enum Suit{ Diamonds, Hearts, Clubs, Spades };

int main() {

    Suit hand;
    . . .
    // Assume that some enum value is set for hand
    // In this example, each case is handled separately
    switch (hand)
    {
    case Diamonds:
        cout << "got Diamonds \n";
        break;
    case Hearts:
        cout << "got Hearts \n";
        break;
    case Clubs:
        cout << "got Clubs \n";
        break;
    case Spades:
        cout << "got Spades \n";
        break;
    default:
          cout << "didn't get card \n";
    }
    // In this example, Diamonds and Hearts are handled one way, and
    // Clubs, Spades, and the default value are handled another way
    switch (hand)
    {
    case Diamonds:
    case Hearts:
        cout << "got a red card \n";
        break;
    case Clubs:
    case Spades:
    default:
        cout << "didn't get a red card \n";
    }
}
```

## <a name="see-also"></a>Vea también

[Instrucciones de salto](../cpp/jump-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[continue (Instrucción)](../cpp/continue-statement-cpp.md)