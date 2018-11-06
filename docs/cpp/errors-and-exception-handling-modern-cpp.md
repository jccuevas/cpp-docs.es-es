---
title: Controlar errores y excepciones (C++ moderno)
ms.date: 09/17/2018
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: 8f5e0070f3e52d20293ddd624a0d0de57660e316
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668000"
---
# <a name="errors-and-exception-handling-modern-c"></a>Controlar errores y excepciones (C++ moderno)

En C++ moderno, en la mayoría de los escenarios, la mejor manera de comunicar y controlar errores lógicos y errores en tiempo de ejecución es utilizar excepciones. Esto es especialmente cierto cuando la pila puede contener varias llamadas de función entre la función que detecta el error y la función que tiene el contexto para saber cómo controlarla. Las excepciones proporcionan una manera formal y bien definida para el código que detecta errores para pasar la información de la pila de llamadas.

Errores del programa generalmente se dividen en dos categorías: errores lógicos que se deben a errores de programación, por ejemplo, un error "índice fuera del intervalo" y errores de tiempo de ejecución que quedan fuera del control del programador, por ejemplo, un "servicio de red no está disponible" error. En la programación de estilo C y en COM, informe de errores se administra devolviendo un valor que representa un código de error o un código de estado para una función determinada, o estableciendo una variable global que el llamador pueda recuperar opcionalmente después de cada llamada de función para ver Si se notificaron errores. Por ejemplo, la programación COM utiliza el valor devuelto HRESULT para comunicar errores al llamador, y la API Win32 tiene la función GetLastError para recuperar el último error detectado por la pila de llamadas. En ambos casos, es al llamador reconocer el código y responder adecuadamente. Si el llamador no controla explícitamente el código de error, el programa podría bloquearse sin advertencia, o seguir se ejecutan con datos erróneos y generar resultados incorrectos.

Las excepciones se prefieren en C++ moderno por las razones siguientes:

- Una excepción fuerza el código que realiza la llamada para reconocer una condición de error y controlarla. Las excepciones no controladas detienen la ejecución de programa.

- Una excepción omite el punto en la pila de llamadas que puede controlar el error. Las funciones intermedias pueden permitir que la excepción a propagar. No tienen que coordinar con otras capas.

- El mecanismo de desenredo de pila de excepción destruye todos los objetos en el ámbito según reglas bien definidas después de que se produce una excepción.

- Una excepción permite una separación clara entre el código que detecta el error y el código que controla el error.

El siguiente ejemplo simplificado muestra la sintaxis necesaria para iniciar y detectar excepciones en C++.

```cpp

#include <stdexcept>
#include <limits>
#include <iostream>

using namespace std;

void MyFunc(int c)
{
    if (c > numeric_limits< char> ::max())
        throw invalid_argument("MyFunc argument too large.");
    //...
}

int main()
{
    try
    {
        MyFunc(256); //cause an exception to throw
    }

    catch (invalid_argument& e)
    {
        cerr << e.what() << endl;
        return -1;
    }
    //...
    return 0;
}

```

Las excepciones de C++ son similares a las de lenguajes como C# y Java. En el **intente** bloquear, si es una excepción *produce* será *detectada* por los primeros asociados **catch** bloque cuyo tipo coincide con el de la excepción. En otras palabras, la ejecución salta de la **throw** instrucción a la **catch** instrucción. Si no se encuentra ningún bloque catch utilizable, `std::terminate` se invoca y se cierra el programa. En C++, se puede producir cualquier tipo; Sin embargo, recomendamos que lance un tipo que deriva directa o indirectamente de `std::exception`. En el ejemplo anterior, el tipo de excepción, [invalid_argument](../standard-library/invalid-argument-class.md), se define en la biblioteca estándar en el [ \<stdexcept >](../standard-library/stdexcept.md) archivo de encabezado. C++ no proporciona y no requiere un **finalmente** bloque para asegurarse de que todos los recursos se liberan si se produce una excepción. La adquisición de recursos es la expresión de inicialización (RAII), que utiliza punteros inteligentes, proporciona la funcionalidad necesaria para la limpieza de recursos. Para obtener más información, consulte [Cómo: diseño de seguridad de las excepciones](../cpp/how-to-design-for-exception-safety.md). Para obtener información sobre el mecanismo de desenredo de pila en C++, vea [excepciones y desenredo de pila](../cpp/exceptions-and-stack-unwinding-in-cpp.md).

## <a name="basic-guidelines"></a>Directrices básicas

Control de errores sólido es un desafío en cualquier lenguaje de programación. Aunque las excepciones proporcionan varias características que admiten un control de errores, no todo el trabajo por usted. Para aprovechar las ventajas del mecanismo de excepciones, mantenga las excepciones en cuenta al diseñar el código.

- Utilice aserciones para comprobar si hay errores que no deben aparecer nunca. Utilice excepciones para comprobar los errores que pueden producirse, por ejemplo, errores de validación de entrada en parámetros de funciones públicas. Para obtener más información, vea la sección titulada **excepciones vs. Aserciones**.

- Utilice excepciones cuando el código que controla el error se podría separar el código que detecta el error por uno o más llamadas de función intermedias. Considere la posibilidad de utilizar códigos de error en su lugar en bucles críticos para el rendimiento cuando el código que controla el error está estrechamente acoplado al código que lo detecta.

- Para cada función que pudiera producir o propagar una excepción, proporcione uno de las tres garantías de excepción: la garantía segura, la garantía básica o la garantía nothrow (noexcept). Para obtener más información, consulte [Cómo: diseño de seguridad de las excepciones](../cpp/how-to-design-for-exception-safety.md).

- Producir excepciones por valor, se detectan por referencia. No se atrapan no puede controlar.

- No utilice especificaciones de excepciones que están en desuso en C ++ 11. Para obtener más información, vea la sección titulada **especificaciones de excepciones y noexcept**.

- Utilice tipos de excepción de la biblioteca estándar cuando se aplican. Derivar de tipos de excepción personalizados desde el [excepción clase](../standard-library/exception-class.md) jerarquía.

- No permitir excepciones a las funciones de desasignación de memoria o de escape de los destructores.

## <a name="exceptions-and-performance"></a>Excepciones y rendimiento

El mecanismo de excepción tiene un rendimiento mínimo costo si se produce ninguna excepción. Si se produce una excepción, el costo del recorrido de pila y desenredado es aproximadamente comparable al costo de una llamada de función. Estructuras de datos adicionales necesarios para realizar un seguimiento de la pila de llamadas después de un **intente** bloque se captan y se requieren instrucciones adicionales para desenredar la pila si se produce una excepción. Sin embargo, en la mayoría de los escenarios, el costo en rendimiento y consumo de memoria no es significativo. El efecto adverso de excepciones en el rendimiento es probable que sean significativas sólo en sistemas muy restringidos de memoria o de rendimiento bucles críticos que es probable que se realizan con regularidad un error y el código para controlarlo está estrechamente al código que lo notifica. En cualquier caso, es imposible saber el costo real de excepciones sin generar perfiles y medir. Incluso en esos casos raros cuando el costo es significativo, puede sopesarlo frente a la mayor exactitud, mantenimiento más sencillo y otras ventajas proporcionadas por una directiva de excepciones bien diseñada.

## <a name="exceptions-vs-assertions"></a>Excepciones frente a aserciones

Excepciones y aserciones son dos mecanismos diferentes para detectar errores en tiempo de ejecución en un programa. Utilice aserciones para probar condiciones durante el desarrollo que nunca debe ser true si todo el código es correcto. No hay ningún punto de administrar este tipo de error con una excepción porque el error indica que algo en el código no se ha solucionado y no representa una condición de que el programa tiene que recuperarse en tiempo de ejecución. Una aserción detiene la ejecución en la instrucción para que puede inspeccionar el estado del programa en el depurador; una excepción continúa la ejecución desde el primer controlador catch adecuado. Utilice excepciones para comprobar las condiciones de error que pueden producirse en tiempo de ejecución, incluso si el código es correcto, por ejemplo, "archivo no encontrado" o "memoria insuficiente". Es posible que desea recuperar de estas condiciones, incluso si la recuperación solo genera un mensaje en un registro y cierra el programa. Compruebe siempre los argumentos para funciones públicas mediante el uso de excepciones. Incluso si la función está libre de errores, podría no tener control total sobre los argumentos que un usuario puede pasarle.

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>Excepciones de C++ frente a excepciones SEH de Windows

Programas de C y C++ pueden utilizar el mecanismo de (SEH) en el sistema operativo Windows de control de excepciones estructurado. Los conceptos en SEH se parecen a las excepciones de C++, salvo que SEH utiliza el **__try**, **__except**, y **__finally** construye en lugar de **intente** y **catch**. En Visual C++, las excepciones de C++ se implementan para SEH. Sin embargo, al escribir código de C++, use la sintaxis de la excepción de C++.

Para obtener más información sobre SEH, vea [control de excepciones estructurado (C/C ++)](../cpp/structured-exception-handling-c-cpp.md).

## <a name="exception-specifications-and-noexcept"></a>Especificaciones de excepciones y noexcept

Especificaciones de excepciones se incluyeron en C++ como una manera de especificar las excepciones que puede producir una función. Sin embargo, las especificaciones de excepción resultó problemáticas en la práctica y están en desuso en el estándar de borrador C ++ 11. Se recomienda que no usan las especificaciones de excepciones, excepto para `throw()`, lo que indica que la función no permite que las excepciones escape. Si debe utilizar las especificaciones de excepción del tipo `throw(` *tipo*`)`, tenga en cuenta que Visual C++ se sale del estándar de determinadas maneras. Para obtener más información, consulte [especificaciones de excepciones (throw)](../cpp/exception-specifications-throw-cpp.md). El `noexcept` especificador se introdujo en C ++ 11 como la alternativa preferida para `throw()`.

## <a name="see-also"></a>Vea también

[Cómo: Interfaz entre código excepcional y no excepcional](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)