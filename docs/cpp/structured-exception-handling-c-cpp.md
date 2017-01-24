---
title: "Control de excepciones estructurado (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de excepciones de C++, controladores de excepciones"
  - "control de excepciones de C++, controladores de terminación"
  - "control estructurado de excepciones"
  - "controladores de terminación, controlar excepciones en C++"
  - "try-catch (palabra clave) [C++], controladores de excepciones"
  - "try-catch (palabra clave) [C++], controladores de terminación"
ms.assetid: dd3b647d-c269-43a8-aab9-ad1458712976
caps.latest.revision: 14
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de excepciones estructurado (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Aunque Windows y Visual C\+\+ admiten el control de excepciones estructurado \(SEH\), se recomienda utilizar el control de excepciones de C\+\+ estándar de ISO porque hace que el código sea más portátil y flexible.  Sin embargo, en el código existente o en determinadas clases de programas, quizás tenga que seguir utilizando SEH.  
  
## Específicos de Microsoft  
  
## Gramática  
 *try\-except\-statement*:  
  
 `__try` *compound\-statement*  
  
 `__except` \(`expression` \) *compound\-statement*  
  
## Comentarios  
 Con SEH, puede asegurarse de que recursos como los bloques de memoria y los archivos son correctos si la ejecución finaliza inesperadamente.  También se pueden controlar determinados problemas, como memoria insuficiente, mediante código estructurado conciso que no utiliza instrucciones `goto` ni realiza pruebas detalladas de los códigos de retorno.  
  
 Las instrucciones try\-except y try\-finally mencionadas en este artículo son extensiones de Microsoft al lenguaje C.  Admiten SEH al permitir que las aplicaciones tomen el control de un programa después de que se produzcan eventos que de lo contrario finalizarían la ejecución.  Aunque SEH funciona con archivos de código fuente de C\+\+, no está diseñado específicamente para C\+\+.  Si se utiliza SEH en un programa de C\+\+ que se compila mediante la opción [\/EH](../build/reference/eh-exception-handling-model.md), junto con determinados modificadores, se llama a los destructores para los objetos locales, pero otro comportamiento de ejecución puede no ser el esperado.  \(Para obtener un ejemplo, vea el ejemplo más adelante en este artículo\). En la mayoría de los casos, en lugar de SEH se recomienda usar el [Control de excepciones de C\+\+](../cpp/try-throw-and-catch-statements-cpp.md) estándar de ISO, que Visual C\+\+ también admite.  Mediante el control de excepciones de C\+\+, puede asegurarse de que el código sea más portátil y puede controlar excepciones de cualquier tipo.  
  
 Si tiene módulos de C que usan SEH, puede combinarlos con módulos de C\+\+ que utilizan el control de excepciones de C\+\+.  Para obtener información, vea [Diferencias en el control de excepciones](../cpp/exception-handling-differences.md).  
  
 Existen dos mecanismos de SEH:  
  
-   [Controladores de excepciones](../cpp/writing-an-exception-handler.md), que pueden responder a la excepción o descartarla.  
  
-   [Controladores de terminación](../cpp/writing-a-termination-handler.md), a los que se llama cuando una excepción provoca la finalización de un bloque de código.  
  
 Estas dos clases de controladores son distintas, pero están estrechamente relacionadas mediante un proceso conocido como "desenredo de la pila". Cuando se produce una excepción, Windows busca el controlador de excepciones instalado más recientemente que está activo actualmente.  El controlador puede hacer una de tres cosas:  
  
-   No reconocer la excepción y pasar el control a otros controladores.  
  
-   Reconocer la excepción pero descartarla.  
  
-   Reconocer la excepción y controlarla.  
  
 El controlador de excepciones que reconoce la excepción puede no estar en la función que se estaba ejecutando cuando se produjo la excepción.  En algunos casos, puede estar en una función situada mucho más arriba en la pila.  La función que se está ejecutando actualmente y todas las demás funciones del marco de pila finalizan.  Durante este proceso, se "desenreda" la pila; es decir, las variables locales de las funciones finalizadas \(a menos que sean `static`\) se borran de la pila.  
  
 A medida que se desenreda la pila, el sistema operativo llama a cualquier controlador de terminación que haya escrito para cada función.  Mediante un controlador de terminación, se pueden limpiar recursos que de lo contrario quedarían abiertos debido a una finalización anormal.  Si se ha entrado en una sección crítica, se puede salir de ella en el controlador de terminación.  Si el programa se va a cerrar, se pueden realizar otras tareas de mantenimiento como cerrar y quitar archivos temporales.  
  
 Para obtener más información, consulte:  
  
-   [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)  
  
-   [Escribir un controlador de finalización](../cpp/writing-a-termination-handler.md)  
  
-   [Usar el control de excepciones estructurado con C\+\+](../cpp/using-structured-exception-handling-with-cpp.md)  
  
## Ejemplo  
 Como se ha explicado anteriormente, se llama a los destructores de los objetos locales si se utiliza SEH en un programa de C\+\+ y se compila con la opción **\/EH** junto con ciertos modificadores; por ejemplo, **\/EHsc** y **\/EHa**.  Sin embargo, el comportamiento durante la ejecución puede no ser el esperado si también se utilizan excepciones de C\+\+.  En el ejemplo siguiente se muestran estas diferencias de comportamiento.  
  
```cpp  
#include <stdio.h>  
#include <Windows.h>  
#include <exception>  
  
class TestClass  
{  
public:  
    ~TestClass()  
    {  
        printf("Destroying TestClass!\r\n");  
    }  
};  
  
__declspec(noinline) void TestCPPEX()  
{  
#ifdef CPPEX  
    printf("Throwing C++ exception\r\n");  
    throw std::exception("");  
#else  
    printf("Triggering SEH exception\r\n");  
    volatile int *pInt = 0x00000000;  
    *pInt = 20;  
#endif  
}  
  
__declspec(noinline) void TestExceptions()  
{  
    TestClass d;  
    TestCPPEX();  
}  
  
int main()  
{  
    __try  
    {  
        TestExceptions();  
    }  
    __except(EXCEPTION_EXECUTE_HANDLER)  
    {  
        printf("Executing SEH __except block\r\n");  
    }  
  
    return 0;  
}  
  
```  
  
 Si se utiliza **\/EHsc** para compilar este código pero el control de pruebas local `CPPEX` está sin definir, no se ejecuta el destructor `TestClass` y la salida es similar a la siguiente:  
  
  **Triggering SEH exception**  
**Executing SEH \_\_except block** Si se utiliza **\/EHsc** para compilar el código y `CPPEX` se define mediante `/DCPPEX` \(para que se produzca una excepción de C\+\+\), se ejecuta el destructor `TestClass` y la salida es similar a la siguiente:  
  
  **Throwing C\+\+ exception**  
**Destroying TestClass\!  Executing SEH \_\_except block**  Si se utiliza **\/EHa** para compilar el código, el destructor `TestClass` se ejecuta independientemente de que se produjera o no la excepción mediante `std::throw` o mediante SEH para desencadenar la excepción \(`CPPEX` definido o no\).  La salida es similar a la siguiente:  
  
  **Throwing C\+\+ exception**  
**Destroying TestClass\!  Executing SEH \_\_except block**  Para obtener más información acerca del control de excepciones, vea [\/EH \(Modelo de control de excepciones\)](../build/reference/eh-exception-handling-model.md).  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Control de excepciones](../cpp/exception-handling-in-visual-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [\<exception\>](../standard-library/exception.md)   
 [Controlar errores y excepciones](../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Control de excepciones estructurado \(Windows\)](http://msdn.microsoft.com/library/windows/desktop/ms680657.aspx)