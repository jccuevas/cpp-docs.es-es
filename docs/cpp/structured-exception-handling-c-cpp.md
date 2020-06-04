---
title: Structured Exception Handling (C/C++)
ms.date: 08/14/2018
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
ms.openlocfilehash: 3282f98f48f7e416857ef2f766563ab6038ca41a
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857273"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)

El control de excepciones estructurado (SEH) es una extensión de Microsoft a C que controla ciertas situaciones de código excepcionales, como errores de hardware, sin problemas. Aunque Windows y Microsoft C++ admiten SEH, se recomienda usar el control de excepciones C++ de ISO estándar, ya que hace que el código sea más portátil y flexible. Sin embargo, para mantener el código existente o para determinados tipos de programas, es posible que tenga que usar SEH.

**Específico de Microsoft:**

## <a name="grammar"></a>Gramática

*try-except-Statement* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *compound-statement* **__except** **(** *expression* **)** *compound-statement*

*try-finally-Statement* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__try** *instrucción compuesta* **__finally** *instrucción compuesta*

## <a name="remarks"></a>Notas

Con SEH, puede asegurarse de que los recursos como los bloques de memoria y los archivos se liberan correctamente si la ejecución finaliza inesperadamente. También puede controlar problemas específicos (por ejemplo, memoria insuficiente) mediante el uso de código estructurado conciso que no depende de instrucciones **goto** ni de probar los códigos de retorno.

Las instrucciones try-except y try-finally mencionadas en este artículo son extensiones de Microsoft al lenguaje C. Admiten SEH al permitir que las aplicaciones tomen el control de un programa después de que se produzcan eventos que de lo contrario finalizarían la ejecución. Aunque SEH funciona con archivos de código fuente de C++, no está diseñado específicamente para C++. Si utiliza SEH en un C++ programa que se compila mediante la opción [/EHA o/EHsc](../build/reference/eh-exception-handling-model.md) , se llama a los destructores para los objetos locales, pero es posible que otro comportamiento de ejecución no sea el esperado. Para ver una ilustración, vea el ejemplo más adelante en este artículo. En la mayoría de los casos, en lugar de SEH, se recomienda usar el [ C++ control de excepciones](../cpp/try-throw-and-catch-statements-cpp.md)de ISO estándar C++ , que el compilador de Microsoft también admite. Mediante el control de excepciones de C++, puede asegurarse de que el código sea más portátil y puede controlar excepciones de cualquier tipo.

Si tiene código de C que usa SEH, puede combinarlo con C++ el código que usa C++ el control de excepciones. Para obtener más información, vea [controlar excepciones C++estructuradas en ](../cpp/exception-handling-differences.md).

Existen dos mecanismos de SEH:

- [Controladores de excepciones](../cpp/writing-an-exception-handler.md)o bloques de **__except** , que pueden responder o descartar la excepción.

- [Controladores de terminación](../cpp/writing-a-termination-handler.md)o bloques de **__finally** , a los que se llama siempre, independientemente de que una excepción cause la terminación o no.

Estas dos clases de controladores son distintas, pero están estrechamente relacionadas mediante un proceso conocido como "desenredo de la pila". Cuando se produce una excepción estructurada, Windows busca el controlador de excepciones instalado más recientemente que está activo actualmente. El controlador puede hacer una de tres cosas:

- No reconocer la excepción y pasar el control a otros controladores.

- Reconocer la excepción pero descartarla.

- Reconocer la excepción y controlarla.

El controlador de excepciones que reconoce la excepción puede no estar en la función que se estaba ejecutando cuando se produjo la excepción. En algunos casos, puede estar en una función situada mucho más arriba en la pila. La función que se está ejecutando actualmente y todas las demás funciones del marco de pila finalizan. Durante este proceso, la pila se "Desenreda", es decir, las variables locales no estáticas de las funciones terminadas se borran de la pila.

A medida que se desenreda la pila, el sistema operativo llama a cualquier controlador de terminación que haya escrito para cada función. Mediante un controlador de terminación, se pueden limpiar recursos que de lo contrario quedarían abiertos debido a una finalización anormal. Si ha escrito una sección crítica, puede salir en el controlador de terminación. Si el programa se va a cerrar, se pueden realizar otras tareas de mantenimiento como cerrar y quitar archivos temporales.

## <a name="next-steps"></a>Pasos siguientes

- [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)

- [Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)

- [Controlar excepciones estructuradas en C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Ejemplo

Como se indicó anteriormente, se llama a los destructores para los objetos locales si se utiliza C++ SEH en un programa y se compila mediante la opción **/EHA** o **/EHsc** . Sin embargo, el comportamiento durante la ejecución puede no ser el esperado si también se utilizan excepciones de C++. En este ejemplo se muestran estas diferencias de comportamiento.

```cpp
#include <stdio.h>
#include <Windows.h>
#include <exception>

class TestClass
{
public:
    ~TestClass()
    {
        printf("Destroying TestClass!\r\n");
    }
};

__declspec(noinline) void TestCPPEX()
{
#ifdef CPPEX
    printf("Throwing C++ exception\r\n");
    throw std::exception("");
#else
    printf("Triggering SEH exception\r\n");
    volatile int *pInt = 0x00000000;
    *pInt = 20;
#endif
}

__declspec(noinline) void TestExceptions()
{
    TestClass d;
    TestCPPEX();
}

int main()
{
    __try
    {
        TestExceptions();
    }
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        printf("Executing SEH __except block\r\n");
    }

    return 0;
}
```

Si usa **/EHsc** para compilar este código pero la macro del control de pruebas local `CPPEX` no está definida, no se ejecuta el destructor `TestClass` y el resultado tiene el siguiente aspecto:

```Output
Triggering SEH exception
Executing SEH __except block
```

Si usa **/EHsc** para compilar el código y `CPPEX` se define mediante `/DCPPEX` (para que se C++ produzca una excepción), se ejecuta el destructor `TestClass` y el resultado tiene el siguiente aspecto:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Si usa **/EHA** para compilar el código, el destructor de `TestClass` se ejecuta independientemente de que se haya producido la excepción mediante `std::throw` o con SEH para desencadenar la excepción, es decir, si `CPPEX` definido o no. La salida es similar a la siguiente:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Para obtener más información, consulte [/EH (Modelo de control de excepciones)](../build/reference/eh-exception-handling-model.md).

**FIN de específico de Microsoft**

## <a name="see-also"></a>Vea también

[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
[Errores y control de excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Control de excepciones estructurado (Windows)](/windows/win32/debug/structured-exception-handling)
