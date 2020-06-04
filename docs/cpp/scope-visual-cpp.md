---
title: Ámbito (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
ms.openlocfilehash: a5b5601c89991fbe1a148ebaf781fe2ad6a9dfc4
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2020
ms.locfileid: "83204134"
---
# <a name="scope-c"></a>Ámbito (C++)

Cuando se declara un elemento de programa como una clase, una función o una variable, su nombre solo se puede "Mostrar" y usar en determinadas partes del programa. El contexto en el que un nombre es visible se denomina *ámbito*. Por ejemplo, si declara una variable `x` en una función, `x` solo es visible dentro del cuerpo de la función. Tiene *ámbito local*. Puede tener otras variables con el mismo nombre en el programa; siempre y cuando se encuentren en ámbitos distintos, no infringirán la regla de definición única y no se producirá ningún error.

En el caso de las variables automáticas no estáticas, el ámbito también determina cuándo se crean y destruyen en la memoria del programa.

Hay seis tipos de ámbito:

- **Ámbito global** Un nombre global es aquél que se declara fuera de cualquier clase, función o espacio de nombres. Sin embargo, en C++ incluso existen estos nombres con un espacio de nombres global implícito. El ámbito de los nombres globales se extiende desde el punto de declaración hasta el final del archivo en el que se declaran. En el caso de los nombres globales, la visibilidad también se rige por las reglas de [vinculación](program-and-linkage-cpp.md) que determinan si el nombre está visible en otros archivos del programa.

- **Ámbito de espacio de nombres** Un nombre que se declara dentro de un [espacio de nombres](namespaces-cpp.md), fuera de cualquier definición de clase o enumeración o bloque de función, es visible desde su punto de declaración hasta el final del espacio de nombres. Un espacio de nombres se puede definir en varios bloques a través de archivos diferentes.

- **Ámbito local** Un nombre declarado dentro de una función o una expresión lambda, incluidos los nombres de parámetro, tiene ámbito local. A menudo se conocen como "variables locales". Solo son visibles desde su punto de declaración hasta el final de la función o el cuerpo de la expresión lambda. El ámbito local es un tipo de ámbito de bloque, que se describe más adelante en este artículo.

- **Ámbito de clase** Los nombres de los miembros de clase tienen ámbito de clase, que se extiende a lo largo de la definición de clase, independientemente del punto de declaración. La accesibilidad de miembros de clase se controla más a través de las palabras clave **Public**, **Private**y **Protected** . Solo se puede tener acceso a los miembros públicos o protegidos mediante los operadores de selección de miembro (**.** o **->** ) o operadores de puntero a miembro (**.** <strong>\*</strong> o **->** <strong>\*</strong> ).

- **Ámbito de instrucción** Los nombres declarados en una instrucción **for**, **If**, **While**o **Switch** están visibles hasta el final del bloque de instrucciones.

- **Ámbito de función** Una [etiqueta](labeled-statements.md) tiene ámbito de función, lo que significa que es visible en todo el cuerpo de la función, incluso antes de su punto de declaración. El ámbito de función permite escribir instrucciones como `goto cleanup` antes de que `cleanup` se declare la etiqueta.

## <a name="hiding-names"></a>Ocultar nombres

Puede ocultar un nombre declarándolo en un bloque delimitado. En la ilustración siguiente, `i` se declara dentro del bloque interno, ocultando de esta manera la variable asociada a `i` en el ámbito del bloque externo.

![Ocultar nombre de ámbito de&#45;de bloque](../cpp/media/vc38sf1.png "Ocultar nombre de ámbito de&#45;de bloque") <br/>
Ocultar el ámbito de bloque y el nombre

El resultado del programa que se muestra en la figura es:

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> El argumento `szWhat` se considera en el ámbito de la función. Por consiguiente, se trata como si se hubiera declarado en el bloque exterior de la función.

## <a name="hiding-class-names"></a>Ocultar nombres de clase

Puede ocultar nombres de clase declarando una función, un objeto o una variable, o un enumerador en el mismo ámbito. Sin embargo, todavía se puede tener acceso al nombre de clase cuando el prefijo es la **clase**keyword.

```cpp
// hiding_class_names.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Declare class Account at global scope.
class Account
{
public:
    Account( double InitialBalance )
        { balance = InitialBalance; }
    double GetBalance()
        { return balance; }
private:
    double balance;
};

double Account = 15.37;            // Hides class name Account

int main()
{
    class Account Checking( Account ); // Qualifies Account as
                                       //  class name

    cout << "Opening account with a balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with a balance of: 15.37
```

> [!NOTE]
> Cualquier lugar en el que se llame al nombre de clase ( `Account` ), la clase de palabra clave debe usarse para diferenciarlo de la cuenta de variable de ámbito global. Esta regla no se aplica cuando el nombre de clase aparece a la izquierda del operador de resolución de ámbito (::). Los nombres del lado izquierdo del operador de resolución de ámbito siempre se consideran nombres de clase.

En el ejemplo siguiente se muestra cómo declarar un puntero a un objeto de tipo `Account` mediante la palabra clave **Class** :

```cpp
class Account *Checking = new class Account( Account );
```

`Account`En el inicializador (entre paréntesis) de la instrucción anterior tiene ámbito global; es de tipo **Double**.

> [!NOTE]
> La reutilización de los nombres de identificador, tal y como se muestra en este ejemplo, se considera mal estilo de programación.

Para obtener información sobre la declaración y la inicialización de objetos de clase, vea [clases, estructuras y uniones](../cpp/classes-and-structs-cpp.md). Para obtener información sobre el uso de los operadores **New** y **Delete** de almacenamiento libre, vea [operadores New y DELETE](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Ocultar nombres con ámbito global

Puede ocultar nombres con ámbito global declarando explícitamente el mismo nombre en el ámbito de bloque. Sin embargo, se puede tener acceso a los nombres de ámbito global mediante el operador de resolución de ámbito ( `::` ).

```cpp
#include <iostream>

int i = 7;   // i has global scope, outside all blocks
using namespace std;

int main( int argc, char *argv[] ) {
   int i = 5;   // i has block scope, hides i at global scope
   cout << "Block-scoped i has the value: " << i << "\n";
   cout << "Global-scoped i has the value: " << ::i << "\n";
}
```

```Output
Block-scoped i has the value: 5
Global-scoped i has the value: 7
```

## <a name="see-also"></a>Vea también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)
