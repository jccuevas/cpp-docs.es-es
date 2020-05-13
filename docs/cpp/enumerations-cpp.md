---
title: Enumeraciones [C++]
ms.date: 06/01/2018
f1_keywords:
- enum_cpp
helpviewer_keywords:
- declarations, enumerations
- enumerators, declaring
- enum keyword [C++]
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: 081829db-5dca-411e-a53c-bffef315bcb3
ms.openlocfilehash: 2a1b3d33534887568c6a55e320e77e0a018cafff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366324"
---
# <a name="enumerations-c"></a>Enumeraciones [C++]

Una enumeración es un tipo definido por el usuario que consta de un conjunto de constantes enteras con nombre conocidas como enumeradores.

> [!NOTE]
> Este artículo cubre el tipo de **enumeración** de lenguaje C++ estándar ISO y el tipo de **clase enum** con ámbito (o fuertemente tipado) que se introduce en C++11. Para obtener información sobre la **clase de enumeración pública** o los tipos de clase **enum privada** en C++/CLI y C++/CX, consulte [enum class](../extensions/enum-class-cpp-component-extensions.md).

## <a name="syntax"></a>Sintaxis

```
// unscoped enum:
enum [identifier] [: type]
{enum-list};

// scoped enum:
enum [class|struct]
[identifier] [: type]
{enum-list};
```

```cpp
// Forward declaration of enumerations  (C++11):
enum A : int; // non-scoped enum must have type specified
enum class B; // scoped enum defaults to int but ...
enum class C : short;  // ... may have any integral underlying type
```

## <a name="parameters"></a>Parámetros

*Identificador*<br/>
Nombre del tipo dado a la enumeración.

*type*<br/>
El tipo subyacente de los enumeradores; cada enumerador tiene el mismo tipo subyacente. Puede ser cualquier tipo entero.

*enum-list*<br/>
Una lista delimitada por comas de los enumeradores en la enumeración. Cada enumerador o nombre de variable en el ámbito debe ser único. Sin embargo, los valores pueden estar duplicados. En una enumeración sin ámbito, el ámbito es el ámbito circundante; en una enumeración de ámbito, el ámbito es la propia *lista de enumeración.*  En una enumeración con ámbito, la lista puede estar vacía, lo que en efecto define un nuevo tipo entero.

*clase*<br/>
Mediante el uso de esta palabra clave en la declaración, especifique el ámbito de la enumeración y se debe proporcionar un *identificador.* También puede utilizar la palabra clave **struct** en lugar de **class**, ya que son semánticamente equivalentes en este contexto.

## <a name="enumerator-scope"></a>Alcance del enumerador

Una enumeración proporciona contexto para describir un intervalo de valores que se representan como constantes con nombre, y también se denominan enumeradores. En los tipos de enumeración original de C y C++, los enumeradores incompletos están visibles en el ámbito en el que se declara enum. En enumeraciones de ámbito, el nombre del enumerador debe calificarse con el nombre de tipo enum. El ejemplo siguiente muestra esta diferencia básica entre las dos clases de enumeraciones:

```cpp
namespace CardGame_Scoped
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Suit::Clubs) // Enumerator must be qualified by enum type
        { /*...*/}
    }
}

namespace CardGame_NonScoped
{
    enum Suit { Diamonds, Hearts, Clubs, Spades };

    void PlayCard(Suit suit)
    {
        if (suit == Clubs) // Enumerator is visible without qualification
        { /*...*/
        }
    }
}
```

A cada nombre de la enumeración se le asigna un valor entero que corresponde al lugar que ocupa en el orden de los valores de la enumeración. De forma predeterminada, al primer valor se asigna 0, al siguiente se asigna 1 y así sucesivamente, pero puede establecer explícitamente el valor de un enumerador, como se muestra aquí:

```cpp
enum Suit { Diamonds = 1, Hearts, Clubs, Spades };
```

El enumerador `Diamonds` tiene asignado el valor `1`. Los enumeradores subsiguientes, si no se les asigna un valor explícito, reciben el valor del enumerador anterior más uno. En el ejemplo anterior, `Hearts` tendría el valor 2, `Clubs` tendría 3, etc.

Cada enumerador se trata como una constante y debe tener un nombre único dentro del ámbito donde se define la **enumeración** (para enumeraciones sin ámbito) o dentro de la propia **enumeración** (para enumeraciones con ámbito). Los valores especificados en los nombres no tienen que ser únicos. Por ejemplo, si la declaración de una enumeración sin ámbito `Suit` es esta:

```cpp
enum Suit { Diamonds = 5, Hearts, Clubs = 4, Spades };
```

Los valores de `Diamonds`, `Hearts`, `Clubs` y `Spades` son 5, 6, 4 y 5, respectivamente. Observe que 5 se utiliza más de una vez; esto se permite incluso aunque pueda no ser intencionado. Estas reglas son las mismas para las enumeraciones de ámbito.

## <a name="casting-rules"></a>Reglas de conversión

Las constantes de enumeración sin ámbito se pueden convertir implícitamente a **int**, pero un **int** nunca es implícitamente convertible a un valor de enumeración. El ejemplo siguiente muestra lo que ocurre si intenta asignar a `hand` un valor que no sea `Suit`:

```cpp
int account_num = 135692;
Suit hand;
hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
```

Se requiere una conversión para convertir un **int** en un enumerador con ámbito o sin ámbito. Sin embargo, puede promover un enumerador sin ámbito a un valor entero sin una conversión.

```cpp
int account_num = Hearts; //OK if Hearts is in a unscoped enum
```

Utilizar conversiones implícitas de esta manera puede provocar efectos secundarios imprevistos. Para ayudar a eliminar los errores de programación asociados a las enumeraciones sin ámbito, los valores de ámbito de enumeración están fuertemente tipados. Los enumeradores con ámbito deben calificarse por el nombre de tipo enumeración (identificador) y no pueden convertirse implícitamente, como se muestra en el ejemplo siguiente:

```cpp
namespace ScopedEnumConversions
{
    enum class Suit { Diamonds, Hearts, Clubs, Spades };

    void AttemptConversions()
    {
        Suit hand;
        hand = Clubs; // error C2065: 'Clubs' : undeclared identifier
        hand = Suit::Clubs; //Correct.
        int account_num = 135692;
        hand = account_num; // error C2440: '=' : cannot convert from 'int' to 'Suit'
        hand = static_cast<Suit>(account_num); // OK, but probably a bug!!!

        account_num = Suit::Hearts; // error C2440: '=' : cannot convert from 'Suit' to 'int'
        account_num = static_cast<int>(Suit::Hearts); // OK
    }
}
```

Observe que la línea `hand = account_num;` aún produce el error que se produce con enumeraciones sin ámbito, como se muestra anteriormente. Esto se permite con una conversión explícita. Sin embargo, con las enumeraciones con ámbito, la conversión que se ha intentado en la siguiente instrucción, `account_num = Suit::Hearts;`, ya no se permite sin una conversión explícita.

## <a name="enums-with-no-enumerators"></a><a name="no_enumerators"></a>Enums sin enumeradores

**Visual Studio 2017 versión 15.3 y versiones posteriores** (disponible con [/std:c++17):](../build/reference/std-specify-language-standard-version.md)al definir una enumeración (regular o con ámbito) con un tipo subyacente explícito y sin enumeradores, en efecto puede introducir un nuevo tipo entero que no tenga ninguna conversión implícita a ningún otro tipo. Mediante el uso de este tipo en lugar de su tipo subyacente integrado, puede eliminar la posibilidad de errores sutiles causados por conversiones implícitas inadvertidas.

```cpp
enum class byte : unsigned char { };
```

El nuevo tipo es una copia exacta del tipo subyacente y, por lo tanto, tiene la misma convención de llamada, lo que significa que se puede usar en abs sin ninguna penalización de rendimiento. No se requiere ninguna conversión cuando las variables del tipo se inicializan mediante la inicialización de lista directa. En el ejemplo siguiente se muestra cómo inicializar enumeraciones sin enumeradores en varios contextos:

```cpp
enum class byte : unsigned char { };

enum class E : int { };
E e1{ 0 };
E e2 = E{ 0 };

struct X
{
    E e{ 0 };
    X() : e{ 0 } { }
};

E* p = new E{ 0 };

void f(E e) {};

int main()
{
    f(E{ 0 });
    byte i{ 42 };
    byte j = byte{ 42 };

    // unsigned char c = j; // C2440: 'initializing': cannot convert from 'byte' to 'unsigned char'
    return 0;
}
```

## <a name="see-also"></a>Consulte también

[C Declaraciones de enumeración](../c-language/c-enumeration-declarations.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
