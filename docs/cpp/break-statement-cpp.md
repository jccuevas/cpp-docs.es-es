---
title: break (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- break_cpp
helpviewer_keywords:
- break keyword [C++]
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
ms.openlocfilehash: 23d31e1456106d5f82c4a13079c72c231b8477bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190487"
---
# <a name="break-statement-c"></a>break (Instrucción) (C++)

La instrucción **break** finaliza la ejecución del bucle envolvente o de la instrucción condicional más cercano en la que aparece. El control pasa a la instrucción que hay a continuación del final de la instrucción, si hay alguna.

## <a name="syntax"></a>Sintaxis

```
break;
```

## <a name="remarks"></a>Observaciones

La instrucción **break** se usa con la instrucción [Switch](../cpp/switch-statement-cpp.md) condicional y con las instrucciones de bucle [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md)y [While](../cpp/while-statement-cpp.md) .

En una instrucción **Switch** , la instrucción **break** hace que el programa ejecute la siguiente instrucción fuera de la instrucción **Switch** . Sin una instrucción **break** , se ejecuta cada instrucción de la etiqueta **Case** coincidente con el final de la instrucción **Switch** , incluida la cláusula **default** .

En los bucles, la instrucción **break** finaliza la ejecución de la instrucción **envolvente**, **for**o **While** más cercana. El control pasa a la instrucción que hay a continuación de la instrucción finalizada, si hay alguna.

Dentro de las instrucciones anidadas, la instrucción **break** finaliza solo la instrucción **do**, **for**, **Switch**o **While** que la incluye inmediatamente. Puede usar una instrucción **Return** o **goto** para transferir el control desde estructuras anidadas más profundamente.

## <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo usar la instrucción **break** en un bucle **for** .

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

En el código siguiente se muestra cómo usar **break** en un bucle **While** y un bucle **do** .

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

En el código siguiente se muestra cómo usar **break** en una instrucción switch. Debe usar **break** en todos los casos si desea controlar cada caso por separado; Si no usa **break**, la ejecución del código pasa al siguiente caso.

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

## <a name="see-also"></a>Consulte también

[Instrucciones de salto](../cpp/jump-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[continue (Instrucción)](../cpp/continue-statement-cpp.md)
