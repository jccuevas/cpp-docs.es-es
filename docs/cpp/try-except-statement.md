---
title: "try-except (Instrucci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_abnormal_termination_cpp"
  - "_exception_code_cpp"
  - "EXCEPTION_CONTINUE_SEARCH"
  - "_exception_info"
  - "__except"
  - "EXCEPTION_CONTINUE_EXECUTION"
  - "_exception_code"
  - "__except_cpp"
  - "_exception_info_cpp"
  - "EXCEPTION_EXECUTE_HANDLER"
  - "_abnormal_termination"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__try (palabra clave) [C++]"
  - "_abnormal_termination (palabra clave) [C++]"
  - "_exception_code (palabra clave) [C++]"
  - "_exception_info (palabra clave) [C++]"
  - "EXCEPTION_CONTINUE_EXECUTION (macro)"
  - "EXCEPTION_CONTINUE_SEARCH (macro)"
  - "EXCEPTION_EXECUTE_HANDLER (macro)"
  - "GetExceptionCode (función)"
  - "try-catch (palabra clave) [C++], try-except (palabra clave) [C++]"
  - "try-except (palabra clave) [C++]"
ms.assetid: 30d60071-ea49-4bfb-a8e6-7a420de66381
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# try-except (Instrucci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 La sintaxis siguiente describe una instrucción try\-except:  
  
## Sintaxis  
  
```  
  
      __try   
{  
   // guarded code  
}  
__except ( expression )  
{  
   // exception handler code  
}  
```  
  
## Comentarios  
 La instrucción **try\-except** es una extensión de Microsoft para los lenguajes C y C\+\+ que permite a las aplicaciones de destino obtener el control cuando se producen los eventos que normalmente finalizan la ejecución de un programa.  Estos eventos se denominan excepciones y el mecanismo que se encarga de las excepciones se denomina control de excepciones estructurado.  
  
 Para obtener información al respecto, vea la [instrucción try\-finally](../cpp/try-finally-statement.md).  
  
 Las excepciones pueden estar basadas en hardware o software.  Aunque las aplicaciones no pueden recuperarse completamente de las excepciones de hardware o software, el control de excepciones estructurado permite mostrar información de error y capturar el estado interno de la aplicación para ayudar a diagnosticar el problema.  Esto es especialmente útil en el caso de problemas intermitentes que no se pueden reproducir fácilmente.  
  
> [!NOTE]
>  El control de excepciones estructurado funciona con Win32 para archivos de código fuente de C y C\+\+.  Sin embargo, no está diseñado específicamente para C\+\+.  Para asegurarse de que el código será más portable, use el control de excepciones de C\+\+.  Además, el control de excepciones de C\+\+ es más flexible, ya que puede controlar excepciones de cualquier tipo.  Para los programas de C\+\+, se recomienda usar el mecanismo de control de excepciones de C\+\+ \(instrucciones [try, catch y throw](../cpp/try-throw-and-catch-statements-cpp.md)\).  
  
 La instrucción compuesta detrás de la cláusula `__try` es el cuerpo o la sección protegida.  La instrucción compuesta detrás de la cláusula `__except` es el controlador de excepción.  El controlador especifica un conjunto de acciones que se realizarán si se inicia una excepción durante la ejecución del cuerpo de la sección protegida.  La ejecución continúa de la siguiente manera:  
  
1.  Se ejecuta la sección protegida.  
  
2.  Si no se produce ninguna excepción durante la ejecución de la sección protegida, continúa la ejecución de la instrucción después de la cláusula `__except`.  
  
3.  Si se produce una excepción durante la ejecución de la sección protegida o en cualquier rutina a la que llame la sección protegida, se evalúa `__except` *expression* \(denominada expresión *filter*\) y el valor determina cómo se controla la excepción.  Existen tres valores:  
  
     **EXCEPTION\_CONTINUE\_EXECUTION \(–1\)** La excepción se descarta.  La ejecución continúa en el punto donde se ha producido la excepción.  
  
     **EXCEPTION\_CONTINUE\_SEARCH \(0\)** La excepción no se reconoce.  La búsqueda de un controlador continúa hacia la parte superior de la pila, primero con las instrucciones **try\-except** contenedoras y, después, con los controladores siguientes que tengan mayor prioridad.  
  
     **EXCEPTION\_EXECUTE\_HANDLER \(1\)** La excepción se reconoce.  Se transfiere el control al controlador de excepciones mediante la ejecución de la instrucción compuesta `__except`; después, la ejecución continúa tras el bloque `__except`.  
  
 Dado que la expresión \_\_**except** se evalúa como expresión de C, se limita a un valor único: el operador de expresión condicional u operador de coma.  Si se requiere un mayor procesamiento, la expresión puede llamar a una rutina que devuelva uno de los tres valores enumerados anteriormente.  
  
 Cada aplicación puede tener su propio controlador de excepciones.  
  
 No es válido saltar dentro de una instrucción `__try`, pero sí fuera.  No se llama al controlador de excepciones si un proceso finaliza en medio de la ejecución de una instrucción **try\-except**.  
  
 Para obtener más información, vea el artículo Q315937 de Knowledge Base: Cómo se detecta el desbordamiento de la pila en una aplicación de Visual C\+\+.  
  
## La palabra clave \_\_leave  
 La palabra clave `__leave` solo es válida dentro de la sección protegida de una instrucción `try-except` y su efecto es saltar al final de la sección protegida.  La ejecución de la primera instrucción continúa después del controlador de excepciones.  
  
 Una instrucción `goto` también puede saltar fuera de la sección protegida, y no se degrada el rendimiento como en una instrucción `try-finally`, porque no se produce desenredo de pila.  Sin embargo, se recomienda usar la palabra clave `__leave` en lugar de una instrucción `goto`, porque es menos probable que se incurra en un error de programación si la sección protegida es grande o compleja.  
  
### Funciones intrínsecas de control de excepciones estructurado  
 El control de excepciones estructurado proporciona dos funciones intrínsecas que se pueden utilizar con la instrucción **try\-except**: **GetExceptionCode** y **GetExceptionInformation**.  
  
 **GetExceptionCode** devuelve el código \(un entero de 32 bits\) de la excepción.  
  
 La función intrínseca **GetExceptionInformation** devuelve un puntero a una estructura que contiene información adicional sobre la excepción.  A través de este puntero, se puede tener acceso al estado que tenía el equipo en el momento de producirse una excepción de hardware.  La estructura es como se detalla a continuación:  
  
```  
struct _EXCEPTION_POINTERS {  
      EXCEPTION_RECORD *ExceptionRecord,  
      CONTEXT *ContextRecord }  
```  
  
 Los tipos de puntero \_**EXCEPTION\_RECORD** y \_**CONTEXT** se definen en el archivo de inclusión EXCPT.H.  
  
 Puede utilizar **GetExceptionCode** dentro del controlador de excepciones.  Sin embargo, puede utilizar **GetExceptionInformation** únicamente en la expresión de filtro de excepciones.  La información a la que señala está normalmente en la pila y ya no está disponible cuando el control se transfiere al controlador de excepciones.  
  
 La función intrínseca **AbnormalTermination** está disponible dentro de un controlador de terminación.  Devuelve 0 si el cuerpo de la instrucción `try-finally` finaliza secuencialmente.  En todos los demás casos, devuelve 1.  
  
 EXCPT.H define algunos nombres alternativos para estos intrínsecos:  
  
 **GetExceptionCode** equivale a \_exception\_code  
  
 **GetExceptionInformation** equivale a \_exception\_info  
  
 **AbnormalTermination** equivale a \_abnormal\_termination  
  
## Ejemplo  
 `// exceptions_try_except_Statement.cpp`  
  
 `// Example of try-except and try-finally statements`  
  
 `#include <stdio.h>`  
  
 `#include <windows.h> // for EXCEPTION_ACCESS_VIOLATION`  
  
 `#include <excpt.h>`  
  
 `int filter(unsigned int code, struct _EXCEPTION_POINTERS *ep) {`  
  
 `puts("in filter.");`  
  
 `if (code == EXCEPTION_ACCESS_VIOLATION) {`  
  
 `puts("caught AV as expected.");`  
  
 `return EXCEPTION_EXECUTE_HANDLER;`  
  
 `}`  
  
 `else {`  
  
 `puts("didn't catch AV, unexpected.");`  
  
 `return EXCEPTION_CONTINUE_SEARCH;`  
  
 `};`  
  
 `}`  
  
 `int main()`  
  
 `{`  
  
 `int* p = 0x00000000;   // pointer to NULL`  
  
 `puts("hello");`  
  
 `__try{`  
  
 `puts("in try");`  
  
 `__try{`  
  
 `puts("in try");`  
  
 `*p = 13;    // causes an access violation exception;`  
  
 `}__finally{`  
  
 `puts("in finally. termination: ");`  
  
 `puts(AbnormalTermination() ? "\tabnormal" : "\tnormal");`  
  
 `}`  
  
 `}__except(filter(GetExceptionCode(), GetExceptionInformation())){`  
  
 `puts("in except");`  
  
 `}`  
  
 `puts("world");`  
  
 `}`  
  
## Salida  
  
```  
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
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Escribir un controlador de excepciones](../cpp/writing-an-exception-handler.md)   
 [Control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)