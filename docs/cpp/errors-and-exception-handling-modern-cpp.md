---
title: Prácticas C++ recomendadas modernas para excepciones y control de errores
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: a6c111d0-24f9-4bbb-997d-3db4569761b7
ms.openlocfilehash: 85a8bf0f64681387cbee63f273fda5ce93ab7ad5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245861"
---
# <a name="modern-c-best-practices-for-exceptions-and-error-handling"></a>Prácticas C++ recomendadas modernas para excepciones y control de errores

En la C++mayoría de los casos, en la mayoría de los escenarios, la mejor manera de notificar y controlar los errores lógicos y los errores en tiempo de ejecución es usar excepciones. Esto es especialmente cierto cuando la pila puede contener varias llamadas de función entre la función que detecta el error y la función que tiene el contexto para saber cómo controlarla. Las excepciones proporcionan una forma formal y bien definida para el código que detecta errores para pasar la información hacia arriba en la pila de llamadas.

Los errores de programa suelen dividirse en dos categorías: errores lógicos causados por errores de programación, por ejemplo, un error de "Índice fuera del intervalo" y errores en tiempo de ejecución que están más allá del control del programador, por ejemplo, un "servicio de red no disponible" error. En la programación de estilo C y en COM, el informe de errores se administra devolviendo un valor que representa un código de error o un código de estado para una función determinada, o estableciendo una variable global que el llamador puede recuperar opcionalmente después de cada llamada de función para ver indica si se han generado errores. Por ejemplo, la programación COM usa el valor devuelto HRESULT para comunicar errores al autor de la llamada, y la API Win32 tiene la función GetLastError para recuperar el último error notificado por la pila de llamadas. En ambos casos, el autor de la llamada debe reconocer el código y responder a él adecuadamente. Si el autor de la llamada no controla explícitamente el código de error, el programa podría bloquearse sin ninguna advertencia o seguir ejecutándose con datos incorrectos y producir resultados incorrectos.

Las excepciones se prefieren en C++ moderno por los siguientes motivos:

- Una excepción obliga al código de llamada a reconocer una condición de error y controlarla. Las excepciones no controladas detienen la ejecución del programa.

- Una excepción salta al punto de la pila de llamadas que puede controlar el error. Las funciones intermedias pueden permitir que se propague la excepción. No tienen que coordinarse con otras capas.

- El mecanismo de desenredo de pila de excepciones destruye todos los objetos del ámbito según las reglas bien definidas después de que se produzca una excepción.

- Una excepción permite una separación limpia entre el código que detecta el error y el código que controla el error.

En el siguiente ejemplo simplificado se muestra la sintaxis necesaria para iniciar y detectar C++excepciones en.

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

Las excepciones C++ se parecen C# a las de lenguajes como y Java. En el bloque **try** , si se *produce* una excepción, se *detectará* por el primer bloque **catch** asociado cuyo tipo coincida con el de la excepción. En otras palabras, la ejecución salta de la instrucción **Throw** a la instrucción **catch** . Si no se encuentra ningún bloque catch utilizable, se invoca `std::terminate` y el programa se cierra. En C++, se puede iniciar cualquier tipo; sin embargo, se recomienda que inicie un tipo que se deriva directa o indirectamente de `std::exception`. En el ejemplo anterior, el tipo de excepción, [invalid_argument](../standard-library/invalid-argument-class.md), se define en la biblioteca estándar en el archivo de encabezado [\<stdexcept >](../standard-library/stdexcept.md) . C++no proporciona, y no requiere, un bloque **Finally** para asegurarse de que todos los recursos se liberan si se produce una excepción. La expresión de adquisición de recursos es de inicialización (RAII), que usa punteros inteligentes, proporciona la funcionalidad necesaria para la limpieza de recursos. Para obtener más información, consulte [Cómo: diseñar para la seguridad de excepciones](how-to-design-for-exception-safety.md). Para obtener información sobre C++ el mecanismo de desenredado de pila, vea [excepciones y desenredo de pila](exceptions-and-stack-unwinding-in-cpp.md).

## <a name="basic-guidelines"></a>Instrucciones básicas

Un control de errores sólido es desafiante en cualquier lenguaje de programación. Aunque las excepciones proporcionan varias características que admiten un buen control de errores, no pueden hacer todo el trabajo por usted. Para obtener las ventajas del mecanismo de excepción, tenga en cuenta las excepciones al diseñar el código.

- Utilice aserciones para comprobar si hay errores que nunca deben producirse. Utilice excepciones para comprobar si hay errores que puedan producirse, por ejemplo, errores en la validación de entrada en parámetros de funciones públicas. Para obtener más información, vea la sección titulada **excepciones frente a aserciones**.

- Utilice excepciones cuando el código que controla el error puede estar separado del código que detecta el error en una o varias llamadas de función intermedias. Considere la posibilidad de usar códigos de error en lugar de bucles críticos para el rendimiento cuando el código que controla el error está estrechamente acoplado al código que lo detecta.

- Para cada función que puede producir o propagar una excepción, proporcione una de las tres garantías de excepción: la garantía segura, la garantía básica o la garantía nothrow (noexception). Para obtener más información, consulte [Cómo: diseñar para la seguridad de excepciones](how-to-design-for-exception-safety.md).

- Producir excepciones por valor, se detectan por referencia. No se detecte lo que no se puede controlar.

- No use especificaciones de excepciones, que están desusadas en C++ 11. Para obtener más información, vea la sección titulada **Especificaciones de excepciones y noexception**.

- Use los tipos de excepción de la biblioteca estándar cuando se apliquen. Derivar tipos de excepción personalizados de la jerarquía de [clases de excepción](../standard-library/exception-class.md) .

- No permita que las excepciones salgan de los destructores o de las funciones de desasignación de memoria.

## <a name="exceptions-and-performance"></a>Excepciones y rendimiento

El mecanismo de excepción tiene un costo de rendimiento muy mínimo si no se produce ninguna excepción. Si se produce una excepción, el costo del cruce seguro y el desenredado de la pila es aproximadamente comparable al costo de una llamada de función. Se requieren estructuras de datos adicionales para realizar el seguimiento de la pila de llamadas después de especificar un bloque **try** , y se requieren instrucciones adicionales para desenredar la pila si se produce una excepción. Sin embargo, en la mayoría de los escenarios, el costo de rendimiento y la superficie de memoria no es significativo. El efecto adverso de las excepciones en el rendimiento es probable que sea significativo solo en sistemas muy restringidos de memoria, o en bucles críticos para el rendimiento en los que es probable que se produzca un error con regularidad y que el código para controlarlo esté estrechamente acoplado al código que lo notifica. En cualquier caso, es imposible conocer el costo real de las excepciones sin generar perfiles ni medir. Incluso en esos raros casos en los que el costo es significativo, puede sopesarlo con la mayor exactitud, mantenimiento más sencillo y otras ventajas que proporciona una directiva de excepciones bien diseñada.

## <a name="exceptions-vs-assertions"></a>Excepciones frente a aserciones

Las excepciones y aserciones son dos mecanismos distintos para detectar errores en tiempo de ejecución en un programa. Use aserciones para comprobar las condiciones durante el desarrollo que nunca deben ser true si todo el código es correcto. No hay ningún punto de controlar este tipo de error mediante el uso de una excepción porque el error indica que se tiene que corregir algo en el código y no representa una condición que el programa tiene que recuperar en tiempo de ejecución. Una aserción detiene la ejecución en la instrucción para que pueda inspeccionar el estado del programa en el depurador. una excepción continúa la ejecución del primer controlador Catch adecuado. Utilice excepciones para comprobar las condiciones de error que pueden producirse en tiempo de ejecución, incluso si el código es correcto, por ejemplo, "archivo no encontrado" o "memoria insuficiente". Es posible que desee realizar la recuperación de estas condiciones, incluso si la recuperación solo genera un mensaje en un registro y finaliza el programa. Compruebe siempre los argumentos de las funciones públicas mediante el uso de excepciones. Incluso si la función no tiene errores, es posible que no tenga control total sobre los argumentos que puede pasar un usuario a él.

## <a name="c-exceptions-versus-windows-seh-exceptions"></a>C++excepciones frente a excepciones SEH de Windows

Tanto C como C++ los programas pueden usar el mecanismo de control de excepciones estructurado (SEH) en el sistema operativo Windows. Los conceptos de SEH son similares a los C++ de las excepciones, salvo que SEH usa las construcciones **__try**, **__except**y **__finally** en lugar de **try** y **catch**. En el compilador de Microsoft C++ ( C++ MSVC), las excepciones se implementan para SEH. Sin embargo, al escribir C++ código, use la C++ sintaxis de la excepción.

Para obtener más información acerca de SEH, vea [control de excepciones estructuradoC++(C/)](structured-exception-handling-c-cpp.md).

## <a name="exception-specifications-and-noexcept"></a>Especificaciones de excepciones y noexception

Las especificaciones de excepción se C++ introdujeron en como una manera de especificar las excepciones que una función puede iniciar. Sin embargo, las especificaciones de excepción demostraron un problema en la práctica y están en desuso en el borrador estándar de C++ 11. Se recomienda no usar especificaciones de excepción excepto `throw()`, lo que indica que la función no permite excepciones de escape. Si debe usar especificaciones de excepción del tipo `throw(`*tipo*`)`, tenga en cuenta que MSVC se integra del estándar de ciertas maneras. Para obtener más información, vea [Especificaciones de excepciones (Throw)](exception-specifications-throw-cpp.md). El especificador de `noexcept` se introduce en C++ 11 como la alternativa preferida a `throw()`.

## <a name="see-also"></a>Vea también

[Cómo: Interfaz entre código excepcional y no excepcional](../cpp/how-to-interface-between-exceptional-and-non-exceptional-code.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
