---
title: (C/C ++) de control de excepciones estructurado | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- termination handlers [C++], handling exceptions in C++
- structured exception handling [C++]
- try-catch keyword [C++], exception handlers
- C++ exception handling, termination handlers
- try-catch keyword [C++], termination handlers
- C++ exception handling, exception handlers
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: db7dd23a1b68e4ea97eb837e009c380514230de8
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2018
ms.locfileid: "42573098"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)

Control de excepciones estructurado (SEH) es una extensión de Microsoft C para controlar determinadas situaciones excepcionales de código, como errores de hardware correctamente. Aunque Windows y Visual C++ admiten SEH, se recomienda que utilice el control de excepciones de C++ estándar de ISO porque hace que el código más portátil y flexible. No obstante, para mantener el código existente o para determinados tipos de programas, aún tendrá que usan SEH.

**Específicas de Microsoft:**

## <a name="grammar"></a>Gramática

*try-except-statement* :  
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *compound-statement* **__except** **(** *expresión* **)** *compound-statement*

*try-finally-statement* :  
&nbsp;&nbsp;&nbsp;&nbsp;**__try** *compound-statement* **__finally** *compound-statement*

## <a name="remarks"></a>Comentarios

Con SEH, puede asegurarse de que se liberen los recursos como bloques de memoria y los archivos correctamente si la ejecución finaliza inesperadamente. También puede controlar determinados problemas, por ejemplo, memoria insuficiente, mediante el uso de código estructurado conciso que no se basa en **goto** instrucciones ni realiza pruebas detalladas de los códigos de retorno.

Las instrucciones try-except y try-finally mencionadas en este artículo son extensiones de Microsoft al lenguaje C. Admiten SEH al permitir que las aplicaciones tomen el control de un programa después de que se produzcan eventos que de lo contrario finalizarían la ejecución. Aunque SEH funciona con archivos de código fuente de C++, no está diseñado específicamente para C++. Si se utiliza SEH en un programa de C++ que se compila con la [/EHa o/EHsc](../build/reference/eh-exception-handling-model.md) opción, los destructores para objetos locales se denominan pero otro comportamiento de ejecución podría no ser los esperados. Para obtener un ejemplo, vea el ejemplo más adelante en este artículo. En la mayoría de los casos, en lugar de SEH se recomienda usar la norma ISO [control de excepciones de C++](../cpp/try-throw-and-catch-statements-cpp.md), que también admite Visual C++. Mediante el control de excepciones de C++, puede asegurarse de que el código sea más portátil y puede controlar excepciones de cualquier tipo.

Si tiene código de C que se utiliza SEH, se pueden mezclar código C++ que usa el control de excepciones de C++. Para obtener información, consulte [controlar las excepciones estructuradas en C++](../cpp/exception-handling-differences.md).

Existen dos mecanismos de SEH:

- [Los controladores de excepciones](../cpp/writing-an-exception-handler.md), o **__except** bloques, que pueden responder a la excepción o descartarla.

- [Los controladores de terminación](../cpp/writing-a-termination-handler.md), o **__finally** bloques, que siempre se llaman si una excepción provoca la terminación o no.

Estas dos clases de controladores son distintas, pero están estrechamente relacionadas mediante un proceso conocido como "desenredo de la pila". Cuando se produce una excepción estructurada, Windows busca el controlador de excepciones instalado más recientemente que está activo actualmente. El controlador puede hacer una de tres cosas:

- No reconocer la excepción y pasar el control a otros controladores.

- Reconocer la excepción pero descartarla.

- Reconocer la excepción y controlarla.

El controlador de excepciones que reconoce la excepción puede no estar en la función que se estaba ejecutando cuando se produjo la excepción. En algunos casos, puede estar en una función situada mucho más arriba en la pila. La función que se está ejecutando actualmente y todas las demás funciones del marco de pila finalizan. Durante este proceso, la pila se "desenreda"; es decir, las variables locales de no estáticos de las funciones finalizadas se borran de la pila.

A medida que se desenreda la pila, el sistema operativo llama a cualquier controlador de terminación que haya escrito para cada función. Mediante un controlador de terminación, se pueden limpiar recursos que de lo contrario quedarían abiertos debido a una finalización anormal. Si ha especificado una sección crítica, puede salir del controlador de finalización. Si el programa se va a cerrar, se pueden realizar otras tareas de mantenimiento como cerrar y quitar archivos temporales.

## <a name="next-steps"></a>Pasos siguientes

- [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)

- [Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)

- [Controlar excepciones estructuradas en C++](../cpp/exception-handling-differences.md)

## <a name="example"></a>Ejemplo

Como se indicó anteriormente, los destructores para objetos locales se llaman si se utiliza SEH en un programa de C++ y se compila utilizando el **/EHa** o **/EHsc** opción. Sin embargo, el comportamiento durante la ejecución puede no ser el esperado si también se utilizan excepciones de C++. En este ejemplo se muestra estas diferencias de comportamiento.

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

Si usas **/EHsc** para compilar este código, pero la macro de control de pruebas local `CPPEX` es undefined, no hay ninguna ejecución de la `TestClass` destructor y la salida tiene el aspecto como este:

```Output
Triggering SEH exception
Executing SEH __except block
```

Si usas **/EHsc** para compilar el código y `CPPEX` se define mediante el uso de `/DCPPEX` (de modo que se produce una excepción de C++), el `TestClass` ejecuta el destructor y el resultado tendrá un aspecto similar al siguiente:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Si usas **/EHa** para compilar el código, el `TestClass` destructor se ejecuta independientemente de si se produjo la excepción mediante el uso de `std::throw` o mediante SEH para desencadenar la excepción, es decir, si `CPPEX` definido o no. La salida es similar a la siguiente:

```Output
Throwing C++ exception
Destroying TestClass!
Executing SEH __except block
```

Para obtener más información, consulte [/EH (Modelo de control de excepciones)](../build/reference/eh-exception-handling-model.md).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)  
[Palabras clave](../cpp/keywords-cpp.md)  
[\<exception>](../standard-library/exception.md)  
[Controlar errores y excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)  
[(Windows) de control de excepciones estructurado](http://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)  
