---
title: Conversiones de tipos definidos por el usuario (C++)
ms.date: 11/04/2016
f1_keywords:
- explicit_cpp
helpviewer_keywords:
- constructors [C++], and constants
- conversion functions [C++]
- explicit keyword [C++]
- type conversion
- constructors [C++], drawbacks
- conversion constructors
- type conversion [C++], explicit conversion
- coercion [C++]
- conversions [C++], explicit
- objects [C++], converting
- conversion functions [C++], rules for declaring
- declaring functions [C++], conversion functions
- functions [C++], conversion
- converting objects
- constructors [C++], conversion
- conversions [C++], by constructors
- data type conversion [C++], explicit
ms.assetid: d40e4310-a190-4e95-a34c-22c5c20aa0b9
ms.openlocfilehash: 055b5bd5c82e4f0be449d548de25267eabef47bd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187939"
---
# <a name="user-defined-type-conversions-c"></a>Conversiones de tipos definidos por el usuario (C++)

Una *conversión* genera un nuevo valor de algún tipo a partir de un valor de un tipo diferente. Las *conversiones estándar* están integradas en C++ el lenguaje y admiten sus tipos integrados, y puede crear conversiones *definidas por el usuario* para realizar conversiones a, desde o entre tipos definidos por el usuario.

Las conversiones estándar realizan conversiones entre tipos integrados, entre punteros o referencias a tipos relacionados por herencia, a y desde punteros void, y al puntero nulo. Para obtener más información, vea [conversiones estándar](../cpp/standard-conversions.md). Las conversiones definidas por el usuario realizan conversiones entre tipos definidos por el usuario, o entre tipos definidos por el usuario y tipos integrados. Puede implementarlos como [constructores de conversión](#ConvCTOR) o como [funciones de conversión](#ConvFunc).

Las conversiones pueden ser explícitas, si el programador solicita que un tipo se convierta en otro, como en el caso de una conversión o inicialización directa, o implícitas, si el lenguaje o programa llama a un tipo que no es el determinado por el programador.

Se intenta realizar conversiones implícitas cuando:

- El argumento que se proporciona a una función no tiene el mismo tipo que el parámetro correspondiente.

- El valor que devuelve una función no tiene el mismo tipo que el tipo devuelto de la función.

- Una expresión de inicializador no tiene el mismo tipo que el objeto que está inicializando.

- Una expresión que controla una instrucción condicional, una construcción en bucle o un modificador no tiene el tipo de resultado necesario para controlarlos.

- El operando proporcionado a un operador no tiene el mismo tipo que el parámetro-operando correspondiente. En el caso de los operadores integrados, los dos operandos deben tener el mismo tipo y los dos se convierten a un tipo común que pueda representarlos a ambos. Para obtener más información, vea [conversiones estándar](standard-conversions.md). En el caso de los operadores definidos por el usuario, cada operando debe tener el mismo tipo que el parámetro-operando correspondiente.

Si una conversión estándar no puede llevar a cabo una conversión implícita, el compilador puede usar una conversión definida por el usuario, que puede ir seguida de una conversión estándar adicional, para terminarla.

Si hay disponibles dos o más conversiones definidas por el usuario que realizan la misma conversión en un lugar de conversión, se dice que la conversión es ambigua. Ese tipo de ambigüedades es un error, ya que el compilador no puede determinar cuál de las conversiones disponibles debe elegir. Con todo, no constituye un error simplemente definir varias formas de realizar la misma conversión, porque el conjunto de conversiones disponibles puede ser distinto en distintos lugares del código fuente, por ejemplo, en función de los archivos de encabezados incluidos en un archivo de código fuente. Siempre que solo haya una conversión disponible en el lugar de la conversión, no hay ambigüedad. Las conversiones ambiguas pueden deberse a varios motivos, pero los más habituales son:

- Herencia múltiple. La conversión está definida en más de una clase base.

- Llamada de función ambigua. La conversión se define como constructor de conversión del tipo de destino y como función de conversión del tipo de origen. Para obtener más información, vea [funciones de conversión](#ConvFunc).

Normalmente, las ambigüedades se pueden resolver simplemente calificando el tipo en cuestión de forma más precisa o realizando una conversión explícita que aclare su finalidad.

Los constructores y las funciones de conversión siguen reglas de control de acceso de los miembros, pero la accesibilidad de las conversiones solo se tiene en cuenta si se puede determinar una conversión no ambigua. Dicho de otro modo, una conversión puede ser ambigua incluso cuando el nivel de acceso de una conversión competidora pudiera impedir que se usara. Para obtener más información sobre la accesibilidad de los miembros, vea [Access Control miembro](../cpp/member-access-control-cpp.md).

## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Palabra clave explícita y problemas con conversiones implícitas

De forma predeterminada, cuando se crea una conversión definida por el usuario, el compilador puede usarla para realizar conversiones implícitas. Hay casos en los que se desea hacer así, pero en otros las sencillas reglas que indican al compilador cómo hacer las conversiones implícitas pueden hacerle aceptar código que no se desea usar.

Un ejemplo conocido de una conversión implícita que puede causar problemas es la conversión a **bool**. Hay muchas razones por las que podría querer crear un tipo de clase que se pueda usar en un contexto booleano (por ejemplo, para que se pueda usar para controlar una instrucción **If** o un bucle), pero cuando el compilador realice una conversión definida por el usuario a un tipo integrado, el compilador podrá aplicar una conversión estándar adicional después. La intención de esta conversión estándar adicional es permitir elementos como la promoción de **Short** a **int**, pero también abre la puerta de las conversiones menos obvias, por ejemplo, de **bool** a **int**, lo que permite usar el tipo de clase en contextos enteros que nunca se ha previsto. Este problema concreto se conoce como el *problema de bool seguro*. Este tipo de problema es donde la palabra clave **Explicit** puede resultar de ayuda.

La palabra clave **Explicit** indica al compilador que la conversión especificada no se puede usar para realizar conversiones implícitas. Si desease la comodidad sintáctica de las conversiones implícitas antes de que se introdujera la palabra clave **Explicit** , tenía que aceptar las consecuencias no deseadas que a veces creaba la conversión implícita o usar las funciones de conversión con nombre menos convenientes como solución alternativa. Ahora, mediante la palabra clave **Explicit** , puede crear conversiones convenientes que solo se pueden usar para realizar conversiones explícitas o inicialización directa, y que no conducen al tipo de problemas ejemplificados por el problema de bool seguro.

La palabra clave **Explicit** se puede aplicar a los constructores de conversión desde c++ 98 y a las funciones de conversión desde c++ 11. En las secciones siguientes se incluye más información sobre cómo usar la palabra clave **Explicit** .

## <a name="conversion-constructors"></a><a name="ConvCTOR"></a>Constructores de conversión

Los constructores de conversión definen conversiones de tipos integrados o definidos por el usuario en un tipo definido por el usuario. En el ejemplo siguiente se muestra un constructor de conversión que convierte del tipo integrado **Double** a un tipo definido por el usuario `Money`.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };

    display_balance(payable);
    display_balance(49.95);
    display_balance(9.99f);

    return 0;
}
```

Observe que la primera llamada a la función `display_balance`, que toma un argumento de tipo `Money`, no requiere conversión porque su argumento es del tipo correcto. Sin embargo, en la segunda llamada a `display_balance`, se necesita una conversión porque el tipo del argumento, un **Double** con un valor de `49.95`, no es lo que espera la función. La función no puede usar este valor directamente, pero como hay una conversión del tipo del argumento (**Double**) al tipo del parámetro coincidente (`Money`): un valor temporal de tipo `Money` se construye a partir del argumento y se usa para completar la llamada de función. En la tercera llamada a `display_balance`, observe que el argumento no es de **tipo Double**, sino que es un valor **float** con un valor de `9.99`. sin embargo, la llamada a la función todavía se puede completar porque el compilador puede realizar una conversión estándar (en este caso, de **float** a **Double**) y, a continuación, realizar la conversión definida por el usuario de **Double** a `Money` para completar la

### <a name="declaring-conversion-constructors"></a>Declarar constructores de conversión

Al declarar un constructor de conversión se aplican las reglas siguientes:

- El tipo de destino de la conversión es el tipo definido por el usuario que se está construyendo.

- Generalmente, los constructores de conversión toman exactamente un argumento, que tiene el tipo del origen. Con todo, un constructor de conversión puede especificar parámetros adicionales si cada uno de ellos tiene un valor predeterminado. El tipo del primer parámetro es el tipo de origen.

- Los constructores de conversión, como todos los constructores, no especifican un tipo de retorno. La especificación de un tipo de retorno en la declaración es un error.

- Los constructores de conversión pueden ser explícitos.

### <a name="explicit-conversion-constructors"></a>Constructores de conversión explícitos

Al declarar un constructor de conversión para que sea **explícito**, solo se puede usar para realizar la inicialización directa de un objeto o para realizar una conversión explícita. Así se impide que las funciones que aceptan un argumento del tipo de la clase acepten también implícitamente argumentos del tipo del origen del constructor de conversión. También se impide que se inicialice una copia del tipo de la clase a partir de un valor del tipo de origen. En el ejemplo siguiente se muestra cómo definir un constructor de construcción explícito y su efecto en qué código está formado correctamente.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    explicit Money(double _amount) : amount{ _amount } {};

    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance.amount << std::endl;
}

int main(int argc, char* argv[])
{
    Money payable{ 79.99 };        // Legal: direct initialization is explicit.

    display_balance(payable);      // Legal: no conversion required
    display_balance(49.95);        // Error: no suitable conversion exists to convert from double to Money.
    display_balance((Money)9.99f); // Legal: explicit cast to Money

    return 0;
}
```

Observe que, en este ejemplo, se puede seguir usando el constructor de conversión para realizar la inicialización directa de `payable`. Si, en lugar de ello, se inicializara una copia de `Money payable = 79.99;`, sería un error. La primera llamada a `display_balance` no se ve afectada porque el argumento es del tipo correcto. La segunda llamada a `display_balance` es un error, porque el constructor de conversión no se puede usar para realizar conversiones implícitas. La tercera llamada a `display_balance` es válida debido a la conversión explícita a `Money`, pero tenga en cuenta que el compilador todavía ha ayudado a completar la conversión insertando una conversión implícita de **float** a **Double**.

El hecho de admitir conversiones implícitas puede parecer práctico, pero podría introducir errores difíciles de detectar. En general, es mejor que todos los constructores de conversión sean explícitos, excepto cuando se desea que una conversión concreta tenga lugar de forma implícita.

##  <a name="conversion-functions"></a><a name="ConvFunc"></a>Funciones de conversión

Las funciones de conversión definen conversiones de un tipo definido por el usuario a otros tipos. Estas funciones se denominan a veces "operadores de conversión" ya que, junto con los constructores de conversión, se les llama cuando un valor se convierte en otro tipo. En el ejemplo siguiente se muestra una función de conversión que convierte del tipo definido por el usuario, `Money`, a un tipo integrado, **Double**:

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << balance << std::endl;
}
```

Tenga en cuenta que la variable miembro `amount` se convierte en privada y que se introduce una función de conversión pública en tipo **Double** para devolver el valor de `amount`. En la función `display_balance` se produce una conversión implícita cuando el valor de `balance` se envía a una salida estándar mediante el uso del operador de inserción de secuencia `<<`. Dado que no se define ningún operador de inserción de secuencia para el tipo definido por el usuario `Money`, pero hay uno para el tipo integrado **Double**, el compilador puede utilizar la función de conversión de `Money` a **Double** para satisfacer el operador de inserción de secuencia.

Las clases derivadas heredan las funciones de conversión. Las funciones de conversión de una clase derivada solo invalidan una función de conversión heredada cuando se convierten exactamente en el mismo tipo. Por ejemplo, una función de conversión definida por el usuario del operador de clase derivada **int** no invalida (o incluso influencia) una función de conversión definida por el usuario del **operador**de clase base Short, aunque las conversiones estándar definen una relación de conversión entre **int** y **Short**.

### <a name="declaring-conversion-functions"></a>Declarar funciones de conversión

Al declarar una función de conversión se aplican las reglas siguientes:

- El tipo de destino de la conversión de debe declarar antes que la declaración de la función de conversión. No se pueden declarar clases, estructuras, enumeraciones ni definiciones de tipos en la declaración de la función de conversión.

    ```cpp
    operator struct String { char string_storage; }() // illegal
    ```

- Las funciones de conversión no toman ningún argumento. La especificación de cualquier parámetro en la declaración es un error.

- Las funciones de conversión tienen un tipo de retorno que se especifica mediante el nombre de la función de conversión, que es también el nombre del tipo de destino de la conversión. La especificación de un tipo de retorno en la declaración es un error.

- Las funciones de conversión pueden ser virtuales.

- Las funciones de conversión pueden ser explícitas.

### <a name="explicit-conversion-functions"></a>Funciones de conversión explícita

Si se declara que una función de conversión es explícita, solo se puede usar para realizar una conversión explícita. Así se impide que las funciones que aceptan un argumento del tipo de destino de la función de conversión acepten también implícitamente argumentos del tipo de clase. También se impide que se inicialicen copias de instancias del tipo de destino a partir de un valor del tipo de clase. En el ejemplo siguiente se muestra cómo definir una función de construcción explícita y su efecto en qué código está formado correctamente.

```cpp
#include <iostream>

class Money
{
public:
    Money() : amount{ 0.0 } {};
    Money(double _amount) : amount{ _amount } {};

    explicit operator double() const { return amount; }
private:
    double amount;
};

void display_balance(const Money balance)
{
    std::cout << "The balance is: " << (double)balance << std::endl;
}
```

Aquí, el **operador Double** de la función de conversión se ha hecho explícito y se ha introducido una conversión explícita al tipo **Double** en la función `display_balance` para realizar la conversión. Si se omitiera esta conversión, el compilador no encontraría un operador de inserción de secuencia `<<` adecuado para el tipo `Money` y se produciría un error.
