---
title: try-except (Instrucción)
description: Referencia de Microsoft C++ a las instrucciones de control de excepciones estructurado __try y __except.
ms.date: 04/03/2020
f1_keywords:
- _abnormal_termination_cpp
- _exception_code_cpp
- _exception_info
- __except
- _except
- _exception_code
- __except_cpp
- _exception_info_cpp
helpviewer_keywords:
- __try keyword [C++]
- EXCEPTION_CONTINUE_EXECUTION macro
- EXCEPTION_CONTINUE_SEARCH macro
- EXCEPTION_EXECUTE_HANDLER macro
- GetExceptionCode function
- try-catch keyword [C++], try-except keyword [C++]
- _exception_code keyword [C++]
- try-except keyword [C++]
- _exception_info keyword [C++]
- _abnormal_termination keyword [C++]
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
ms.openlocfilehash: d0471bbd50e07fccbf160e9e866de4c545cdeb7e
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825775"
---
# <a name="try-except-statement"></a>try-except (Instrucción)

La instrucción **try-except** es una extensión de Microsoft que admite el control de excepciones estructurado en los lenguajes C y C++. Esta extensión es **específica de Microsoft**.

## <a name="syntax"></a>Sintaxis

> **\_\_prueba**\
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;código protegido \
> }\
> Except ( *expresión* ) \ ** \_ \_**
> {\
> &nbsp;&nbsp;&nbsp;&nbsp;Código del controlador de excepciones \
> }

## <a name="remarks"></a>Observaciones

La instrucción **try-except** es una extensión de Microsoft para los lenguajes C y C++. Permite a las aplicaciones de destino obtener el control cuando se producen eventos que normalmente finalizan la ejecución del programa. Estos eventos se denominan *excepciones estructuradas*o *excepciones* para abreviar. El mecanismo que se encarga de estas excepciones se denomina *control de excepciones estructurado* (SEH).

Para obtener información relacionada, vea la [instrucción try-finally](../cpp/try-finally-statement.md).

Las excepciones pueden estar basadas en hardware o en software. El control estructurado de excepciones es útil incluso cuando las aplicaciones no pueden recuperarse completamente de las excepciones de hardware o software. SEH permite mostrar información de error y capturar el estado interno de la aplicación para ayudar a diagnosticar el problema. Es especialmente útil para problemas intermitentes que no son fáciles de reproducir.

> [!NOTE]
> El control de excepciones estructurado funciona con Win32 para archivos de código fuente de C y C++. Sin embargo, no está diseñado específicamente para C++. Para asegurarse de que el código será más portable, use el control de excepciones de C++. Además, el control de excepciones de C++ es más flexible, ya que puede controlar excepciones de cualquier tipo. En el caso de los programas de C++, se recomienda usar las instrucciones de control de excepciones de C++ nativo: [try, Catch y Throw](../cpp/try-throw-and-catch-statements-cpp.md) .

La instrucción compuesta después de la cláusula **__try** es el *cuerpo* o la sección *protegida* . La expresión **__except** también se conoce como expresión de *filtro* . Su valor determina cómo se controla la excepción. La instrucción compuesta después de la cláusula **__except** es el controlador de excepciones. El controlador especifica las acciones que deben llevarse a cabo si se produce una excepción durante la ejecución de la sección del cuerpo. La ejecución continúa de la siguiente manera:

1. Se ejecuta la sección protegida.

1. Si no se produce ninguna excepción durante la ejecución de la sección protegida, la ejecución continúa en la instrucción después de la cláusula **__except** .

1. Si se produce una excepción durante la ejecución de la sección protegida o en cualquier rutina a la que llame la sección protegida, se evalúa la expresión **__except** . Hay tres valores posibles:

   - `EXCEPTION_CONTINUE_EXECUTION`(-1) Se descartará la excepción. La ejecución continúa en el punto donde se ha producido la excepción.

   - `EXCEPTION_CONTINUE_SEARCH`(0) no se reconoce la excepción. La búsqueda de un controlador continúa hacia la parte superior de la pila, primero con las instrucciones **try-except** contenedoras y, después, con los controladores siguientes que tengan mayor prioridad.

   - `EXCEPTION_EXECUTE_HANDLER`(1) se reconoce la excepción. Transfiera el control al controlador de excepciones ejecutando la instrucción compuesta de **__except** y, a continuación, continúe con la ejecución después del bloque de **__except** .

La expresión **__except** se evalúa como una expresión de C. Está limitado a un único valor, el operador de expresión condicional o el operador de coma. Si se requiere un mayor procesamiento, la expresión puede llamar a una rutina que devuelva uno de los tres valores enumerados anteriormente.

Cada aplicación puede tener su propio controlador de excepciones.

No es válido saltar a una instrucción **__try** , pero es válida para saltar de una. No se llama al controlador de excepciones si un proceso finaliza en medio de la ejecución de una instrucción **try-except** .

Por compatibilidad con versiones anteriores, **_try**, **_except**y **_leave** son sinónimos de **__try**, **__except**y **__leave** a menos que se especifique la opción del compilador [ \(/za deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

### <a name="the-__leave-keyword"></a>La palabra clave __leave

La palabra clave **__leave** solo es válida dentro de la sección protegida de una instrucción **try-except** y su efecto es saltar al final de la sección protegida. La ejecución de la primera instrucción continúa después del controlador de excepciones.

Una instrucción **goto** también puede saltar fuera de la sección protegida y no degrada el rendimiento como en una instrucción **try-finally** . Esto se debe a que no se produce el desenredado de la pila. Sin embargo, se recomienda usar la palabra clave **__leave** en lugar de una instrucción **goto** . La razón es que es menos probable que se produzca un error de programación si la sección protegida es grande o compleja.

### <a name="structured-exception-handling-intrinsic-functions"></a>Funciones intrínsecas de control de excepciones estructurado

El control de excepciones estructurado proporciona dos funciones intrínsecas que están disponibles para su uso con la instrucción **try-except** : [GetExceptionCode](/windows/win32/Debug/getexceptioncode) y [GetExceptionInformation](/windows/win32/Debug/getexceptioninformation).

`GetExceptionCode`Devuelve el código (un entero de 32 bits) de la excepción.

La función `GetExceptionInformation` intrínseca devuelve un puntero a una estructura de [EXCEPTION_POINTERS](/windows/win32/api/winnt/ns-winnt-exception_pointers) que contiene información adicional sobre la excepción. A través de este puntero, se puede tener acceso al estado que tenía el equipo en el momento de producirse una excepción de hardware. La estructura es como sigue:

```cpp
typedef struct _EXCEPTION_POINTERS {
    PEXCEPTION_RECORD ExceptionRecord;
    PCONTEXT ContextRecord;
} EXCEPTION_POINTERS, *PEXCEPTION_POINTERS;
```

Los tipos `PEXCEPTION_RECORD` de puntero `PCONTEXT` y se definen en el archivo \<de inclusión Winnt. h `_EXCEPTION_RECORD`> `_CONTEXT` y y se definen en el \<archivo de inclusión excpt. h>

Puede usar `GetExceptionCode` dentro del controlador de excepciones. Sin embargo, solo puede `GetExceptionInformation` usar dentro de la expresión de filtro de excepciones. La información a la que apunta está generalmente en la pila y ya no está disponible cuando el control se transfiere al controlador de excepciones.

La función intrínseca [AbnormalTermination](/windows/win32/Debug/abnormaltermination) está disponible dentro de un controlador de terminación. Devuelve 0 si el cuerpo de la instrucción **try-finally** finaliza secuencialmente. En todos los demás casos, devuelve 1.

\<excpt. h> define algunos nombres alternativos para estos intrínsecos:

`GetExceptionCode` es equivalente a `_exception_code`

`GetExceptionInformation` es equivalente a `_exception_info`

`AbnormalTermination` es equivalente a `_abnormal_termination`

## <a name="example"></a>Ejemplo

```cpp
// exceptions_try_except_Statement.cpp
// Example of try-except and try-finally statements
#include <stdio.h>
#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION
#include <excpt.h>

int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep)
{
    puts("in filter.");
    if (code == EXCEPTION_ACCESS_VIOLATION)
    {
        puts("caught AV as expected.");
        return EXCEPTION_EXECUTE_HANDLER;
    }
    else
    {
        puts("didn't catch AV, unexpected.");
        return EXCEPTION_CONTINUE_SEARCH;
    };
}

int main()
{
    int* p = 0x00000000;   // pointer to NULL
    puts("hello");
    __try
    {
        puts("in try");
        __try
        {
            puts("in try");
            *p = 13;    // causes an access violation exception;
        }
        __finally
        {
            puts("in finally. termination: ");
            puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");
        }
    }
    __except(filter(GetExceptionCode(), GetExceptionInformation()))
    {
        puts("in except");
    }
    puts("world");
}
```

### <a name="output"></a>Salida

```Output
hello
in try
in try
in filter.
caught AV as expected.
in finally. termination:
        abnormal
in except
world
```

## <a name="see-also"></a>Vea también

[Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)<br/>
[Control de excepciones estructurado (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
