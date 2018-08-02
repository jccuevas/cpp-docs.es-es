---
title: (C/C ++) de control de excepciones estructurado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 1edcf2cb24273f475b1ba98e5e973f5704c0cec8
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461707"
---
# <a name="structured-exception-handling-cc"></a>Structured Exception Handling (C/C++)
Aunque Windows y Visual C++ admiten el control de excepciones estructurado (SEH), se recomienda utilizar el control de excepciones de C++ estándar de ISO porque hace que el código sea más portátil y flexible. Sin embargo, en el código existente o en determinadas clases de programas, quizás tenga que seguir utilizando SEH.  
  
## <a name="microsoft-specific"></a>Específicos de Microsoft  
  
## <a name="grammar"></a>Gramática  
 *try-except-statement* :  
  
 `__try` *Compound-statement*  
  
 `__except` ( `expression` ) *compound-statement*  
  
## <a name="remarks"></a>Comentarios  
 Con SEH, puede asegurarse de que recursos como los bloques de memoria y los archivos son correctos si la ejecución finaliza inesperadamente. También puede controlar determinados problemas, por ejemplo, memoria insuficiente, mediante el uso de código estructurado conciso que no se basa en **goto** instrucciones ni realiza pruebas detalladas de los códigos de retorno.  
  
 Las instrucciones try-except y try-finally mencionadas en este artículo son extensiones de Microsoft al lenguaje C. Admiten SEH al permitir que las aplicaciones tomen el control de un programa después de que se produzcan eventos que de lo contrario finalizarían la ejecución. Aunque SEH funciona con archivos de código fuente de C++, no está diseñado específicamente para C++. Si se utiliza SEH en un programa de C++ que se compila con la [/EH](../build/reference/eh-exception-handling-model.md) opción, junto con determinados modificadores, se llama a destructores para objetos locales, pero otro comportamiento de ejecución podría no ser los esperados. (Para obtener un ejemplo, vea el ejemplo más adelante en este artículo). En la mayoría de los casos, en lugar de SEH se recomienda usar la norma ISO [control de excepciones de C++](../cpp/try-throw-and-catch-statements-cpp.md), que también admite Visual C++. Mediante el control de excepciones de C++, puede asegurarse de que el código sea más portátil y puede controlar excepciones de cualquier tipo.  
  
 Si tiene módulos de C que usan SEH, puede combinarlos con módulos de C++ que utilizan el control de excepciones de C++. Para obtener información, consulte [diferencias en el control de excepciones](../cpp/exception-handling-differences.md).  
  
 Existen dos mecanismos de SEH:  
  
-   [Los controladores de excepciones](../cpp/writing-an-exception-handler.md), que puede responder a la excepción o descartarla.  
  
-   [Los controladores de terminación](../cpp/writing-a-termination-handler.md), que se llama cuando una excepción provoca la finalización de un bloque de código.  
  
 Estas dos clases de controladores son distintas, pero están estrechamente relacionadas mediante un proceso conocido como "desenredo de la pila". Cuando se produce una excepción, Windows busca el controlador de excepciones instalado más recientemente que está activo actualmente. El controlador puede hacer una de tres cosas:  
  
-   No reconocer la excepción y pasar el control a otros controladores.  
  
-   Reconocer la excepción pero descartarla.  
  
-   Reconocer la excepción y controlarla.  
  
 El controlador de excepciones que reconoce la excepción puede no estar en la función que se estaba ejecutando cuando se produjo la excepción. En algunos casos, puede estar en una función situada mucho más arriba en la pila. La función que se está ejecutando actualmente y todas las demás funciones del marco de pila finalizan. Durante este proceso, la pila se "desenreda"; es decir, las variables locales de las funciones finalizadas, a menos que sean **estático**, se borran de la pila.  
  
 A medida que se desenreda la pila, el sistema operativo llama a cualquier controlador de terminación que haya escrito para cada función. Mediante un controlador de terminación, se pueden limpiar recursos que de lo contrario quedarían abiertos debido a una finalización anormal. Si se ha entrado en una sección crítica, se puede salir de ella en el controlador de terminación. Si el programa se va a cerrar, se pueden realizar otras tareas de mantenimiento como cerrar y quitar archivos temporales.  
  
 Para obtener más información, consulte:  
  
-   [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)  
  
-   [Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)  
  
-   [Usar el control de excepciones estructurado con C++](../cpp/using-structured-exception-handling-with-cpp.md)  
  
## <a name="example"></a>Ejemplo  
 Como se ha explicado anteriormente, se llama a los destructores de los objetos locales si se utiliza SEH en un programa de C++ y se compila con la opción `/EH` junto con ciertos modificadores; por ejemplo, `/EHsc` y `/EHa`. Sin embargo, el comportamiento durante la ejecución puede no ser el esperado si también se utilizan excepciones de C++. En el ejemplo siguiente se muestran estas diferencias de comportamiento.  
  
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
  
 Si usas **/EHsc** para compilar este código, pero el control de pruebas local `CPPEX` es undefined, no hay ninguna ejecución de la `TestClass` destructor y la salida tiene el aspecto como este:  
  
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
  
 Si usas **/EHa** para compilar el código, el `TestClass` destructor se ejecuta independientemente de si se produjo la excepción mediante el uso de `std::throw` o mediante SEH para desencadenar la excepción (`CPPEX` definido o no). La salida es similar a la siguiente:  
  
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