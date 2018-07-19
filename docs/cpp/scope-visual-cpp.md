---
title: Ámbito (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 04/08/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e79ae7f861553ce2bcd7bee6cbb14a3c2965d4ce
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2018
ms.locfileid: "36261082"
---
# <a name="scope-c"></a>Ámbito (C++)

Cuando se declara un elemento de programa como una clase, una función o una variable, su nombre puede solo pueden "ver" y usar en determinadas partes del programa. Se llama el contexto en el que está visible un nombre de su *ámbito*. Por ejemplo, si se declara una variable `x` dentro de una función, `x` sólo es visible dentro del cuerpo de la función. Tiene *ámbito local*. Puede tener otras variables con el mismo nombre en el programa; siempre que se encuentran en distintos ámbitos, no infringen una regla de definición y se produce ningún error.

Para las variables automáticas de no estáticos, ámbito también determina cuando se crean y se destruyen en memoria de programa. 

Existen seis tipos de ámbito:

- **Ámbito global** un nombre global es aquel que se declara fuera de cualquier clase, la función o el espacio de nombres. Sin embargo, en C++ existen incluso estos nombres con un espacio de nombres global implícito. El ámbito de nombres globales se extiende desde el punto de declaración hasta el final del archivo en el que se declaran. Para los nombres globales, visibilidad también se rige por las reglas de [vinculación](program-and-linkage-cpp.md) que determinan si el nombre está visible en otros archivos en el programa.

- **Ámbito de Namespace** un nombre que se declara dentro de un [espacio de nombres](namespaces-cpp.md), fuera de cualquier definición de clase o una enumeración o un bloque de la función, es visible desde su punto de declaración hasta el final del espacio de nombres. Un espacio de nombres puede definirse en varios bloques en archivos diferentes.

- **Ámbito local** un nombre declarado dentro de una función o expresión lambda, incluidos los nombres de parámetro, tienen ámbito local. A menudo se conocen como "locales". Solo son visibles desde su punto de declaración hasta el final del cuerpo de función o expresión lambda. Ámbito local es un tipo de ámbito de bloque, que se explica más adelante en este artículo.

- **Ámbito de clase** nombres de miembros de clase tienen ámbito de clase, que se extiende a lo largo de la definición de clase sin tener en cuenta el punto de declaración. Accesibilidad de miembro de clase es obtener controlada por el **público**, **privada**, y **protegido** palabras clave. Pueden tener acceso a miembros públicos o protegidos sólo mediante los operadores de selección de miembro (**.** o **->**) u operadores de puntero a miembro (**.\***  o **-> \***).

- **Ámbito de la instrucción** nombres declarados en un **para**, **si**, **mientras**, o **cambiar** instrucción son visibles hasta el final de la bloque de instrucciones.

- **Ámbito de función** A [etiqueta](labeled-statements.md) tiene ámbito de función, lo que significa que es visible en el cuerpo de una función incluso antes de que su punto de declaración. Ámbito de función permite escribir instrucciones como `goto cleanup` antes de la `cleanup` etiqueta se declara.

## <a name="hiding-names"></a>Ocultar nombres

Puede ocultar un nombre declarándolo en un bloque delimitado. En la ilustración siguiente, `i` se declara dentro del bloque interno, ocultando de esta manera la variable asociada a `i` en el ámbito del bloque externo.

 ![Bloque&#45;ocultación de nombres de ámbito](../cpp/media/vc38sf1.png "vc38SF1") ámbito de bloque y ocultación de nombre

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

 Puede ocultar nombres de clase declarando una función, un objeto o una variable, o un enumerador en el mismo ámbito. Sin embargo, el nombre de clase todavía son accesibles cuando va precedido por la palabra clave **clase**.

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

    cout << "Opening account with balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with balance of: 15.37
```

> [!NOTE]
> Cualquier lugar donde el nombre de clase (`Account`) se llama para, debe usar la palabra clave class para diferenciarla de la cuenta de variable con ámbito global. Esta regla no se aplica cuando el nombre de clase aparece a la izquierda del operador de resolución de ámbito (::). Los nombres del lado izquierdo del operador de resolución de ámbito siempre se consideran nombres de clase.

 En el ejemplo siguiente se muestra cómo declarar un puntero a un objeto de tipo `Account` mediante la **clase** palabra clave:

```cpp
class Account *Checking = new class Account( Account );
```

 El `Account` en el inicializador (entre paréntesis) en la instrucción anterior tiene ámbito global; es de tipo **doble**.

> [!NOTE]
> La reutilización de los nombres de identificador, tal y como se muestra en este ejemplo, se considera mal estilo de programación.

 Para obtener más información acerca de los punteros, vea [tipos derivados](http://msdn.microsoft.com/en-us/aa14183c-02fe-4d81-95fe-beddb0c01c7c). Para obtener información acerca de la declaración e inicialización de objetos de clase, consulte [clases, estructuras y uniones](../cpp/classes-and-structs-cpp.md). Para obtener información sobre el uso de la **nueva** y **eliminar** operadores de almacenamiento libre, consulte [nueva y eliminar operadores](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Ocultar nombres con ámbito global

 Puede ocultar nombres con ámbito global declarando explícitamente el mismo nombre en el ámbito de bloque. Sin embargo, los nombres de ámbito global pueden tener acceso mediante el operador de resolución de ámbito (`::`).

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