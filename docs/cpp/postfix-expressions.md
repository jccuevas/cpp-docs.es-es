---
title: Expresiones postfijas
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: 25dfc6fd8f28f6c78fd5a4e9f76759ac076cae1b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177695"
---
# <a name="postfix-expressions"></a>Expresiones postfijas

Las expresiones de postfijo constan de expresiones primarias o expresiones en las que los operadores de postfijo siguen una expresión primaria. Los operadores de postfijo se enumeran en la tabla siguiente.

### <a name="postfix-operators"></a>Operadores de postfijo

|Nombre del operador|Notación de operador|
|-------------------|-----------------------|
|[Operador de subíndice](../cpp/subscript-operator.md)|**[ ]**|
|[Operador de llamada de función](../cpp/function-call-operator-parens.md)|**( )**|
|[Operador de conversión de tipo explícito](../cpp/explicit-type-conversion-operator-parens.md)|*type-name* **()**|
|[Operador de acceso a miembros](../cpp/member-access-operators-dot-and.md)|**.** o **->** ,|
|[Operador de incremento de postfijo](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[Operador de decremento postfijo](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

La sintaxis siguiente describe expresiones de postfijo posibles:

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

La *expresión de postfijo* anterior puede ser una expresión primaria u otra expresión de postfijo.  Vea **expresiones primarias**.  Las expresiones de postfijo se agrupan de izquierda a derecha, por lo que las expresiones se pueden encadenar unas a otras del modo siguiente:

```cpp
func(1)->GetValue()++
```

En la expresión anterior, `func` es una expresión primaria, `func(1)` es una expresión de postfijo de función, `func(1)->GetValue` es una expresión de postfijo que especifica un miembro de la clase, `func(1)->GetValue()` es otra expresión de postfijo de función y toda la expresión es una expresión de postfijo que incrementa el valor devuelto de GetValue.  El significado de la expresión completa es que la función que llama pasa 1 como argumento y obtiene un puntero a una clase como valor devuelto.  A continuación, llame a `GetValue()` en esa clase y, a continuación, incremente el valor devuelto.

Las expresiones enumeradas anteriormente son expresiones de asignación, lo que significa que el resultado de estas expresiones debe ser un valor R.

La forma de expresión de postfijo

```cpp
simple-type-name ( expression-list )
```

indica la invocación del constructor.  Si el nombre de tipo simple es un tipo fundamental, la lista de expresiones debe ser una expresión única y esta expresión indica una conversión del valor de la expresión al tipo fundamental.  Este tipo de expresión de conversión imita un constructor.  Dado que esta forma permite la construcción de tipos y clases fundamentales utilizando la misma sintaxis, es especialmente útil cuando se definen clases de plantilla.

*Cast-keyword* es uno de **dynamic_cast**, **static_cast** o **reinterpret_cast**.  Puede encontrar más información en **dynamic_cast**, **static_cast** y **reinterpet_cast**.

El operador **typeid** se considera una expresión de postfijo.  Vea **operador typeid**.

## <a name="formal-and-actual-arguments"></a>Argumentos formales y reales

Los programas que llaman pasan información a las funciones llamadas en "argumentos reales". Las funciones llamadas tienen acceso a la información mediante el uso de los correspondientes "argumentos formales".

Cuando se llama a una función, se realizan las tareas siguientes:

- Se evalúan todos los argumentos reales (los proporcionados por el llamador). No hay ningún orden implícito en el que se evalúan estos argumentos, pero se evalúan todos los argumentos y se completan todos los efectos secundarios antes de la entrada a la función.

- Cada argumento formal se inicializa con su argumento real correspondiente de la lista de expresiones. (Un argumento formal es un argumento que se declara en el encabezado de función y se usa en el cuerpo de una función). Las conversiones se realizan como si se inicializara; tanto las conversiones estándar como las definidas por el usuario se realizan en la conversión de un argumento real al tipo correcto. Inicialización realizada se muestra de forma conceptual en el código siguiente:

    ```cpp
    void Func( int i ); // Function prototype
    ...
    Func( 7 );          // Execute function call
    ```

   Las inicializaciones conceptuales anteriores a la llamada son:

    ```cpp
    int Temp_i = 7;
    Func( Temp_i );
    ```

   Observe que la inicialización se realiza como si se utilizara la sintaxis de signo igual en lugar de la sintaxis de paréntesis. Se realiza una copia de `i` antes de pasar el valor a la función. (Para obtener más información, vea [inicializadores](../cpp/initializers.md) y [conversiones](../cpp/user-defined-type-conversions-cpp.md)).

   Por consiguiente, si el prototipo de función (declaración) llama a para un argumento de tipo **Long**, y si el programa que realiza la llamada proporciona un argumento real de tipo **int**, el argumento real se promueve utilizando una conversión de tipo estándar al tipo **Long** (vea [conversiones estándar](../cpp/standard-conversions.md)).

   Es un error proporcionar un argumento real para el que no hay ninguna conversión estándar o definida por el usuario al tipo del argumento formal.

   Para los argumentos reales de tipo de clase, el argumento formal se inicializa llamando al constructor de la clase. (Vea [constructores](../cpp/constructors-cpp.md) para obtener más información sobre estas funciones miembro de clase especiales).

- Se ejecuta la llamada de función.

El fragmento de programa siguiente muestra una llamada de función:

```cpp
// expre_Formal_and_Actual_Arguments.cpp
void func( long param1, double param2 );

int main()
{
    long i = 1;
    double j = 2;

    // Call func with actual arguments i and j.
    func( i, j );
}

// Define func with formal parameters param1 and param2.
void func( long param1, double param2 )
{
}
```

Cuando se llama a `func` desde Main, el parámetro formal `param1` se inicializa con el valor de `i` (`i` se convierte al tipo **Long** para que se corresponda con el tipo correcto mediante una conversión estándar) y el parámetro formal `param2` se inicializa con el valor de `j` (`j` se convierte al tipo **Double** mediante una conversión estándar).

## <a name="treatment-of-argument-types"></a>Tratamiento de tipos de argumento

Los argumentos formales declarados como tipos const no se pueden cambiar dentro del cuerpo de una función. Las funciones pueden cambiar cualquier argumento que no sea de tipo **const**. Sin embargo, el cambio es local para la función y no afecta al valor del argumento real a menos que el argumento real fuera una referencia a un objeto que no es de tipo **const**.

Las funciones siguientes muestran algunos de estos conceptos:

```cpp
// expre_Treatment_of_Argument_Types.cpp
int func1( const int i, int j, char *c ) {
   i = 7;   // C3892 i is const.
   j = i;   // value of j is lost at return
   *c = 'a' + j;   // changes value of c in calling function
   return i;
}

double& func2( double& d, const char *c ) {
   d = 14.387;   // changes value of d in calling function.
   *c = 'a';   // C3892 c is a pointer to a const object.
    return d;
}
```

## <a name="ellipses-and-default-arguments"></a>Elipse y argumentos predeterminados

Las funciones se pueden declarar para aceptar menos argumentos que los especificados en la definición de función, mediante uno de estos dos métodos: puntos suspensivos (`...`) o argumentos predeterminados.

Los puntos suspensivos denotan que los argumentos pueden ser necesarios pero no se especifican el número y los tipos en la declaración. Normalmente se considera una mala práctica de programación en C++, porque se frustra una de las ventajas de C++: la seguridad de tipos. A las funciones declaradas con puntos suspensivos se les aplican conversiones diferentes de las que se aplican a las funciones para las que se conocen los tipos de argumento formal y real:

- Si el argumento real es de tipo **float**, se promueve al tipo **Double** antes de la llamada de función.

- Los campos con signo o sin **signo**, **Short**, de tipo enumerado o de bits se convierten en un valor signed o unsigned **int** mediante promoción de entero.

- Cualquier argumento de tipo de clase se pasa por valor como estructura de datos; la copia se crea mediante copia binaria en lugar de invocar el constructor de copia de clase (si existe).

Los puntos suspensivos, si se utilizan, se deben declarar en último lugar en la lista de argumentos. Para obtener más información sobre cómo pasar un número variable de argumentos, vea la explicación de [va_arg, va_start y va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) en la referencia de la *biblioteca en tiempo de ejecución*.

Para obtener información sobre los argumentos predeterminados en la programación con CLR, vea [listas de argumentosC++variables (...) (/CLI)](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

Los argumentos predeterminados permiten especificar el valor que un argumento debe asumir si no se proporciona ninguno en la llamada a función. El fragmento de código siguiente muestra cómo funcionan los argumentos predeterminados. Para obtener más información sobre las restricciones en la especificación de argumentos predeterminados, vea [argumentos predeterminados](../cpp/default-arguments.md).

```cpp
// expre_Ellipses_and_Default_Arguments.cpp
// compile with: /EHsc
#include <iostream>

// Declare the function print that prints a string,
// then a terminator.
void print( const char *string,
            const char *terminator = "\n" );

int main()
{
    print( "hello," );
    print( "world!" );

    print( "good morning", ", " );
    print( "sunshine." );
}

using namespace std;
// Define print.
void print( const char *string, const char *terminator )
{
    if( string != NULL )
        cout << string;

    if( terminator != NULL )
        cout << terminator;
}
```

El programa anterior declara una función, `print`, que toma dos argumentos. Sin embargo, el segundo argumento, *Terminator*, tiene un valor predeterminado, `"\n"`. En `main`, las dos primeras llamadas a `print` permiten que el segundo argumento predeterminado proporcione una nueva línea para finalizar la cadena impresa. La tercera llamada especifica un valor explícito para el segundo argumento. El resultado del programa es

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>Consulte también

[Tipos de expresiones](../cpp/types-of-expressions.md)
