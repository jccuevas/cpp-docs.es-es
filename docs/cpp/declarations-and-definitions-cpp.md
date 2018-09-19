---
title: Declaraciones y definiciones (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f2155fef0f9287273b3c45e9318665acfdae527
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46070644"
---
# <a name="declarations-and-definitions-c"></a>Declaraciones y definiciones (C++)

Las declaraciones introducen nombres en un programa, por ejemplo, los nombres de variables, espacios de nombres, funciones y clases. Las declaraciones también especifican información de tipos y otras características del objeto que se declara. Antes de poder usar un nombre, hay que declararlo; en C++, el punto en el que se declara un nombre determina si es visible para el compilador. Se no se puede hacer referencia a una función o clase que se declara en algún momento posterior en la unidad de compilación; Puede usar *reenviar declaraciones* para superar esta limitación.

Las definiciones de especifican qué código o datos describe el nombre. El compilador necesita la definición a fin de asignar espacio de almacenamiento para el elemento que se declara.

## <a name="declarations"></a>Declaraciones

Una declaración introduce uno o más nombres en un programa. Las declaraciones pueden aparecer varias veces en un programa. Por tanto, las clases, estructuras, tipos enumerados y otros tipos definidos por el usuario se pueden declarar para cada unidad de compilación. La restricción de esta declaración múltiple es que todas las declaraciones deben ser idénticas. Las declaraciones también actúan como definiciones, excepto cuando la declaración:

1. Es un prototipo de función (una declaración de función sin cuerpo de función).

1. Contiene el **extern** especificador pero ningún inicializador (objetos y variables) o el cuerpo de la función (funciones). Esto significa que la definición no está necesariamente en la unidad de traducción actual y proporciona al nombre vinculación externa.

1. Es de un miembro de datos estático en una declaración de clase.

     Como los miembros de datos estáticos de clase son variables discretas compartidas por todos los objetos de la clase, se deben definir e inicializar fuera de la declaración de clase. (Para obtener más información sobre las clases y miembros de clase, vea [clases](../cpp/classes-and-structs-cpp.md).)

1. Es una declaración de nombre de clase sin la siguiente definición, como `class T;`.

1. Es un **typedef** instrucción.

Estos son algunos ejemplos de declaraciones que también son definiciones:

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
            Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

Algunas declaraciones que no son definiciones son:

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

Se considera que un nombre se declara inmediatamente después de su declarador pero antes de su inicializador (opcional). Para obtener más información, consulte [punto de declaración](../cpp/point-of-declaration-in-cpp.md).

Las declaraciones se producen en un *ámbito*. El ámbito controla la visibilidad del nombre declarado y la duración del objeto definido, si existe. Para obtener más información acerca de cómo interactúan las reglas de ámbito con declaraciones, vea [ámbito](../cpp/scope-visual-cpp.md).

Una declaración de objeto es también una definición a menos que contenga el **extern** especificador de clase de almacenamiento que se describe en [clases de almacenamiento](storage-classes-cpp.md). Una declaración de función es también una definición a menos que sea un prototipo. Un prototipo es un encabezado de función sin un cuerpo de definición de la función. La definición de un objeto provoca la asignación del almacenamiento y las inicializaciones adecuadas para ese objeto.

## <a name="definitions"></a>Definiciones

Una definición es una especificación única de un objeto o una variable, función, clase o enumerador. Como las definiciones deben ser únicas, un programa solo puede contener una definición para un determinado elemento de programa. Puede haber una correspondencia varios a uno entre las declaraciones y definiciones. Hay dos casos en los que un elemento de programa puede estar declarado y no definido:

1. Se declara una función pero nunca se hace referencia a ella con una llamada de función o una expresión que tome la dirección de la función.

1. Una clase solo se utiliza de forma que no sea necesario conocer su definición. Sin embargo, la clase debe declararse. En el código siguiente se muestra este caso:

    ```cpp
    // definitions.cpp
    class WindowCounter;   // Forward declaration; no definition

    class Window
    {
       // Definition of WindowCounter not required
       static WindowCounter windowCounter;
    };

    int main()
    {
    }
    ```

## <a name="see-also"></a>Vea también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)<br/>
[Punto de declaración](../cpp/point-of-declaration-in-cpp.md)