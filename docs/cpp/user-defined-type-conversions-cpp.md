---
title: Conversiones de tipos (C++) definido por el usuario | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: explicit_cpp
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 561730527a215d5314f7239affc764d9f5925f67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-type-conversions-c"></a>Conversiones de tipos definidos por el usuario (C++)
A *conversión* produce un valor nuevo de cierto tipo a partir de un valor de un tipo diferente. *Conversiones estándar* están integradas en el lenguaje C++ y la compatibilidad con sus tipos integrados y se pueden crear *conversiones definidas por el usuario* para realizar conversiones a, desde o entre tipos definidos por el usuario.  
  
 Las conversiones estándar realizan conversiones entre tipos integrados, entre punteros o referencias a tipos relacionados por herencia, a y desde punteros void, y al puntero nulo. Para obtener más información, consulte [conversiones estándar](../cpp/standard-conversions.md). Las conversiones definidas por el usuario realizan conversiones entre tipos definidos por el usuario, o entre tipos definidos por el usuario y tipos integrados. Puede implementarlos como [constructores de conversión](#ConvCTOR) o como [funciones de conversión](#ConvFunc).  
  
 Las conversiones pueden ser explícitas, si el programador solicita que un tipo se convierta en otro, como en el caso de una conversión o inicialización directa, o implícitas, si el lenguaje o programa llama a un tipo que no es el determinado por el programador.  
  
 Se intenta realizar conversiones implícitas cuando:  
  
-   El argumento que se proporciona a una función no tiene el mismo tipo que el parámetro correspondiente.  
  
-   El valor que devuelve una función no tiene el mismo tipo que el tipo devuelto de la función.  
  
-   Una expresión de inicializador no tiene el mismo tipo que el objeto que está inicializando.  
  
-   Una expresión que controla una instrucción condicional, una construcción en bucle o un modificador no tiene el tipo de resultado necesario para controlarlos.  
  
-   El operando proporcionado a un operador no tiene el mismo tipo que el parámetro-operando correspondiente. En el caso de los operadores integrados, los dos operandos deben tener el mismo tipo y los dos se convierten a un tipo común que pueda representarlos a ambos. Para obtener más información, consulte [conversiones estándar](standard-conversions.md). En el caso de los operadores definidos por el usuario, cada operando debe tener el mismo tipo que el parámetro-operando correspondiente.  
  
 Si una conversión estándar no puede llevar a cabo una conversión implícita, el compilador puede usar una conversión definida por el usuario, que puede ir seguida de una conversión estándar adicional, para terminarla.  
  
 Si hay disponibles dos o más conversiones definidas por el usuario que realizan la misma conversión en un lugar de conversión, se dice que la conversión es ambigua. Ese tipo de ambigüedades es un error, ya que el compilador no puede determinar cuál de las conversiones disponibles debe elegir. Con todo, no constituye un error simplemente definir varias formas de realizar la misma conversión, porque el conjunto de conversiones disponibles puede ser distinto en distintos lugares del código fuente, por ejemplo, en función de los archivos de encabezados incluidos en un archivo de código fuente. Siempre que solo haya una conversión disponible en el lugar de la conversión, no hay ambigüedad. Las conversiones ambiguas pueden deberse a varios motivos, pero los más habituales son:  
  
-   Herencia múltiple. La conversión está definida en más de una clase base. 
  
-   Llamada de función ambigua. La conversión se define como constructor de conversión del tipo de destino y como función de conversión del tipo de origen. Para obtener más información, consulte [funciones de conversión](#ConvFunc).  
  
 Normalmente, las ambigüedades se pueden resolver simplemente calificando el tipo en cuestión de forma más precisa o realizando una conversión explícita que aclare su finalidad.  
  
 Los constructores y las funciones de conversión siguen reglas de control de acceso de los miembros, pero la accesibilidad de las conversiones solo se tiene en cuenta si se puede determinar una conversión no ambigua. Dicho de otro modo, una conversión puede ser ambigua incluso cuando el nivel de acceso de una conversión competidora pudiera impedir que se usara. Para obtener más información acerca de la accesibilidad de miembro, vea [Control de acceso de miembro](../cpp/member-access-control-cpp.md).  
  
## <a name="the-explicit-keyword-and-problems-with-implicit-conversion"></a>Palabra clave explícita y problemas con conversiones implícitas  
 De forma predeterminada, cuando se crea una conversión definida por el usuario, el compilador puede usarla para realizar conversiones implícitas. Hay casos en los que se desea hacer así, pero en otros las sencillas reglas que indican al compilador cómo hacer las conversiones implícitas pueden hacerle aceptar código que no se desea usar.  
  
 Un ejemplo bien conocido de conversión implícita que puede dar problemas es la conversión a `bool`. Existen muchas razones por las que podría desear un tipo de clase que se pueda usar en un contexto booleano, por ejemplo, para que se pueda usar para controlar una instrucción o bucle `if`, pero cuando el compilador realiza una conversión definida por el usuario en un tipo integrado, se permite que el compilador aplique una conversión estándar adicional a continuación. El objetivo de esa conversión estándar adicional es admitir, entre otras cosas, la promoción de `short` a `int`. Además, puede admitir otras conversiones menos obvias, por ejemplo, de `bool` a `int`, que permite usar el tipo de clase en contextos de enteros que no se habían previsto. Este problema en particular se conoce como el *problema Bool seguro*. Y este es el tipo de problema con el que la palabra clave `explicit` puede ayudar.  
  
 La palabra clave `explicit` indica al compilador que la conversión especificada no se puede usar para realizar conversiones implícitas. Antes de que se introdujera la palabra clave `explicit`, si quería usar la comodidad sintáctica de las conversiones implícitas, tenía que aceptar las consecuencias no previstas que a veces creaba la conversión implícita, o bien usar como solución las funciones de conversión con nombre, que resultan menos prácticas. Ahora, al usar la palabra clave `explicit` puede crear conversiones prácticas que solo se pueden usar para realizar conversiones explícitas o inicialización directa, lo que no da lugar al tipo de problemas que ilustra el problema de valor booleano seguro.  
  
 La palabra clave `explicit` se puede aplicar a constructores de conversión desde C++98 y a funciones de conversión desde C++11. En las secciones siguientes se proporciona más información sobre el uso de la palabra clave `explicit`.  
  
##  <a name="ConvCTOR"></a>Constructores de conversión  
 Los constructores de conversión definen conversiones de tipos integrados o definidos por el usuario en un tipo definido por el usuario. En el ejemplo siguiente se muestra un constructor de conversión que convierte el tipo integrado `double` en un tipo `Money` definido por el usuario.  
  
```  
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
  
 Observe que la primera llamada a la función `display_balance`, que toma un argumento de tipo `Money`, no requiere conversión porque su argumento es del tipo correcto. Sin embargo, en la segunda llamada a `display_balance`, se necesita una conversión porque el tipo del argumento, un `double` con un valor de `49.95`, no es lo que la función espera. La función no puede usar este valor directamente, pero como hay una conversión del tipo de argumento, `double`, al tipo de parámetro correspondiente, `Money`, a partir del argumento se crea un valor temporal de tipo `Money`, que se usa para finalizar la llamada a la función. En la tercera llamada a `display_balance`, tenga en cuenta que el argumento no es un `double`, sino que es un `float` con un valor de `9.99`, y aún la llamada de función aún se puede completar porque el compilador puede realizar una conversión estándar, en este caso , de `float` a `double`: y, a continuación, realizar la conversión definida por el usuario de `double` a `Money` para completar la conversión necesaria.  
  
### <a name="declaring-conversion-constructors"></a>Declarar constructores de conversión  
 Al declarar un constructor de conversión se aplican las reglas siguientes:  
  
-   El tipo de destino de la conversión es el tipo definido por el usuario que se está construyendo.  
  
-   Generalmente, los constructores de conversión toman exactamente un argumento, que tiene el tipo del origen. Con todo, un constructor de conversión puede especificar parámetros adicionales si cada uno de ellos tiene un valor predeterminado. El tipo del primer parámetro es el tipo de origen.  
  
-   Los constructores de conversión, como todos los constructores, no especifican un tipo de retorno. La especificación de un tipo de retorno en la declaración es un error.  
  
-   Los constructores de conversión pueden ser explícitos.  
  
### <a name="explicit-conversion-constructors"></a>Constructores de conversión explícitos  
 Si se declara que un constructor de conversión es `explicit`, solo se puede usar para realizar la inicialización directa de un objeto o para realizar una conversión explícita. Así se impide que las funciones que aceptan un argumento del tipo de la clase acepten también implícitamente argumentos del tipo del origen del constructor de conversión. También se impide que se inicialice una copia del tipo de la clase a partir de un valor del tipo de origen. En el ejemplo siguiente se muestra cómo definir un constructor de construcción explícito y su efecto en qué código está formado correctamente.  
  
```  
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
  
 Observe que, en este ejemplo, se puede seguir usando el constructor de conversión para realizar la inicialización directa de `payable`. Si, en lugar de ello, se inicializara una copia de `Money payable = 79.99;`, sería un error. La primera llamada a `display_balance` no se ve afectada porque el argumento es del tipo correcto. La segunda llamada a `display_balance` es un error, porque el constructor de conversión no se puede usar para realizar conversiones implícitas. La tercera llamada a `display_balance` es válida por la presencia de la conversión explícita a `Money`, pero con todo el compilador contribuyó a la finalización de la conversión mediante la inserción de una conversión implícita de `float` a `double`.  
  
 El hecho de admitir conversiones implícitas puede parecer práctico, pero podría introducir errores difíciles de detectar. En general, es mejor que todos los constructores de conversión sean explícitos, excepto cuando se desea que una conversión concreta tenga lugar de forma implícita.  
  
##  <a name="ConvFunc"></a>Funciones de conversión  
 Las funciones de conversión definen conversiones de un tipo definido por el usuario a otros tipos. Estas funciones se denominan a veces "operadores de conversión" ya que, junto con los constructores de conversión, se les llama cuando un valor se convierte en otro tipo. En el ejemplo siguiente se muestra una función de conversión que convierte el tipo definido por el usuario `Money` en un tipo `double` integrado:  
  
```  
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
  
 Observe que la variable miembro `amount` se hace privada y que se introduce una función de conversión pública en el tipo `double` simplemente para que devuelva el valor de `amount`. En la función `display_balance` se produce una conversión implícita cuando el valor de `balance` se envía a una salida estándar mediante el uso del operador de inserción de secuencia `<<`. Como no se define un operador de inserción de secuencia para el tipo definido por el usuario `Money`, pero sí hay uno para el tipo integrado `double`, el compilador puede usar la función de conversión de `Money` en `double` para cumplir con el operador de inserción de secuencia.  
  
 Las clases derivadas heredan las funciones de conversión. Las funciones de conversión de una clase derivada solo invalidan una función de conversión heredada cuando se convierten exactamente en el mismo tipo. Por ejemplo, una función de conversión definida por el usuario de la clase derivada `operator int` no invalida, ni afecta de ninguna forma, una función de conversión definida por el usuario de la clase base `operator short`, a pesar de que las conversiones estándar definen una relación de conversión entre `int` y `short`.  
  
### <a name="declaring-conversion-functions"></a>Declarar funciones de conversión  
 Al declarar una función de conversión se aplican las reglas siguientes:  
  
-   El tipo de destino de la conversión de debe declarar antes que la declaración de la función de conversión. No se pueden declarar clases, estructuras, enumeraciones ni definiciones de tipos en la declaración de la función de conversión.  
  
    ```  
    operator struct String { char string_storage; }() // illegal  
    ```  
  
-   Las funciones de conversión no toman ningún argumento. La especificación de cualquier parámetro en la declaración es un error.  
  
-   Las funciones de conversión tienen un tipo de retorno que se especifica mediante el nombre de la función de conversión, que es también el nombre del tipo de destino de la conversión. La especificación de un tipo de retorno en la declaración es un error.  
  
-   Las funciones de conversión pueden ser virtuales.  
  
-   Las funciones de conversión pueden ser explícitas.  
  
### <a name="explicit-conversion-functions"></a>Funciones de conversión explícitas  
 Si se declara que una función de conversión es explícita, solo se puede usar para realizar una conversión explícita. Así se impide que las funciones que aceptan un argumento del tipo de destino de la función de conversión acepten también implícitamente argumentos del tipo de clase. También se impide que se inicialicen copias de instancias del tipo de destino a partir de un valor del tipo de clase. En el ejemplo siguiente se muestra cómo definir una función de construcción explícita y su efecto en qué código está formado correctamente.  
  
```  
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
  
 Aquí, la función de conversión `operator double` se ha hecho explícita, y se ha introducido una conversión explícita al tipo `double` en la función `display_balance` para realizar la conversión. Si se omitiera esta conversión, el compilador no encontraría un operador de inserción de secuencia `<<` adecuado para el tipo `Money` y se produciría un error.  
  
