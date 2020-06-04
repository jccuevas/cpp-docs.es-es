---
title: Declaraciones y definiciones (C++)
ms.date: 12/12/2019
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: 7aa9e07a471ed5a32ecc8f13690f1a1bf08b655f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077216"
---
# <a name="declarations-and-definitions-c"></a>Declaraciones y definiciones (C++)

Un C++ programa consta de varias entidades como variables, funciones, tipos y espacios de nombres. Cada una de estas entidades debe *declararse* antes de que se puedan utilizar. Una declaración especifica un nombre único para la entidad, junto con información sobre su tipo y otras características. En C++ el punto en el que se declara un nombre, es el punto en el que se hace visible para el compilador. No se puede hacer referencia a una función o clase declarada en algún punto posterior de la unidad de compilación. Las variables deben declararse lo más cerca posible antes del punto en el que se usan.

En el ejemplo siguiente se muestran algunas declaraciones:

```cpp
#include <string>

void f(); // forward declaration

int main()
{
    const double pi = 3.14; //OK
    int i = f(2); //OK. f is forward-declared
    std::string str; // OK std::string is declared in <string> header
    C obj; // error! C not yet declared.
    j = 0; // error! No type specified.
    auto k = 0; // OK. type inferred as int by compiler.
}

int f(int i)
{
    return i + 42;
}

namespace N {
   class C{/*...*/};
}
```

En la línea 5, se declara la función `main`. En la línea 7, se declara e *inicializa*una variable **const** denominada `pi`. En la línea 8, se declara un entero `i` y se inicializa con el valor generado por la función `f`. El nombre `f` es visible para el compilador debido a la *declaración adelantada* en la línea 3.

En la línea 9, se declara una variable denominada `obj` de tipo `C`. Sin embargo, esta declaración genera un error porque `C` no se declara hasta más tarde en el programa y no se declara hacia delante. Para corregir el error, puede trasladar la *definición* completa de `C` antes de `main`, o bien agregar una declaración de avance para ella. Este comportamiento es diferente de otros lenguajes como C#, en el que las funciones y clases se pueden usar antes de su punto de declaración en un archivo de código fuente.

En la línea 10, se declara una variable denominada `str` de tipo `std::string`. El nombre `std::string` es visible porque se presenta en el archivo de [encabezado](header-files-cpp.md) `string`, que se combina en el archivo de código fuente en la línea 1. `std` es el espacio de nombres en el que se declara la clase `string`.

En la línea 11, se genera un error porque no se ha declarado el nombre `j`. Una declaración debe proporcionar un tipo, a diferencia de otros lenguajes como javaScript. En la línea 12, se usa la palabra clave `auto`, que indica al compilador que infiera el tipo de `k` basándose en el valor con el que se inicializa. En este caso, el compilador elige `int` para el tipo.  

## <a name="declaration-scope"></a>Ámbito de la declaración

El nombre que se introduce en una declaración es válido dentro del *ámbito* en el que se produce la declaración. En el ejemplo anterior, las variables que se declaran dentro de la función `main` son *variables locales*. Podría declarar otra variable denominada `i` fuera de Main, en el *ámbito global*, y sería una entidad completamente independiente. Sin embargo, dicha duplicación de nombres puede conducir a errores y confusión del programador y debe evitarse. En la línea 21, la clase `C` se declara en el ámbito del espacio de nombres `N`. El uso de espacios de nombres ayuda a evitar *conflictos de nombres*. La C++ mayoría de los nombres de biblioteca estándar se declaran dentro del espacio de nombres `std`. Para obtener más información sobre cómo interactúan las reglas de ámbito con las declaraciones, vea [ámbito](../cpp/scope-visual-cpp.md).

## <a name="definitions"></a>Definiciones

Algunas entidades, incluidas las funciones, las clases, las enumeraciones y las variables constantes, deben definirse además de declararse. Una *definición* proporciona al compilador toda la información que necesita para generar código máquina cuando la entidad se usa más adelante en el programa. En el ejemplo anterior, la línea 3 contiene una declaración para la función `f` pero la *definición* de la función se proporciona en las líneas 15 a 18. En la línea 21, la clase `C` se declara y se define (aunque, tal y como se define, la clase no hace nada). Se debe definir una variable constante, en otras palabras asignadas a un valor, en la misma instrucción en la que se declara. Una declaración de un tipo integrado como `int` es automáticamente una definición, ya que el compilador conoce la cantidad de espacio que se va a asignar.

En el ejemplo siguiente se muestran las declaraciones que también son definiciones:

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

Estas son algunas declaraciones que no son definiciones:

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

## <a name="typedefs-and-using-statements"></a>Typedefs y instrucciones Using

En versiones anteriores de C++, la palabra clave [typedef](aliases-and-typedefs-cpp.md) se utiliza para declarar un nuevo nombre que es un *alias* de otro nombre. Por ejemplo, el tipo `std::string` es otro nombre para `std::basic_string<char>`. Debe ser obvio por qué los programadores usan el nombre de la definición de tipo y no el nombre real. En moderno C++, se prefiere la palabra clave [using](aliases-and-typedefs-cpp.md) a TypeDef, pero la idea es la misma: se ha declarado un nuevo nombre para una entidad que ya se ha declarado y definido.

## <a name="static-class-members"></a>Miembros de clase estáticos

Dado que los miembros de datos de clase estática son variables discretas compartidas por todos los objetos de la clase, deben definirse e inicializarse fuera de la definición de clase. (Para obtener más información, vea [clases](../cpp/classes-and-structs-cpp.md)).

## <a name="extern-declarations"></a>declaraciones extern

Un C++ programa podría contener más de una [unidad de compilación](header-files-cpp.md). Para declarar una entidad que se define en una unidad de compilación independiente, utilice la palabra clave [extern](extern-cpp.md) . La información de la declaración es suficiente para el compilador, pero si la definición de la entidad no se encuentra en el paso de vinculación, el enlazador producirá un error.

## <a name="in-this-section"></a>En esta sección

[Clases de almacenamiento](storage-classes-cpp.md)<br/>
[const](const-cpp.md)<br/>
[constexpr](constexpr-cpp.md)<br/>
[extern](extern-cpp.md)<br/>
[Inicializadores](initializers.md)<br/>
[Alias y definiciones de tipo](aliases-and-typedefs-cpp.md)<br/>
[Using (declaración)](using-declaration.md)<br/>
[volatile](volatile-cpp.md)<br/>
[decltype](decltype-cpp.md)<br/>
[Atributos deC++](attributes.md)<br/>

## <a name="see-also"></a>Consulte también

[Conceptos básicos](../cpp/basic-concepts-cpp.md)<br/>
