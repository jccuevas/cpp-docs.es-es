---
title: "try-finally (instrucción) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
dev_langs: C++
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c8fd9128593d1a4ae266376ca5c8cd18ca2d119f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="try-finally-statement"></a>try-finally (Instrucción)
**Específicos de Microsoft**  
  
 La sintaxis siguiente describe la instrucción `try-finally`:  
  
```  
__try {  
   // guarded code  
}  
__finally {  
   // termination code  
}  
```  
  
## <a name="grammar"></a>Gramática  
 *try-finally-statement*:  
 `__try`*compound-statement*  
  
 `__finally`*compound-statement*  
  
 La instrucción `try-finally` es una extensión de Microsoft a los lenguajes C y C++ que permite que las aplicaciones de destino garanticen la ejecución del código de limpieza cuando se interrumpe la ejecución de un bloque de código. La limpieza consta de tareas como desasignar memoria, cerrar archivos y liberar identificadores de archivo. La instrucción `try-finally` es especialmente útil para las rutinas que tienen varios lugares donde comprobar un error, lo que puede causar que la rutina termine antes de tiempo.  
  
 Para obtener información relacionada y un ejemplo de código, vea [intente-excepto instrucción](../cpp/try-except-statement.md). Para obtener más información sobre estructurado de excepciones en general, vea [Structured Exception Handling](../cpp/structured-exception-handling-c-cpp.md). Para obtener más información sobre cómo controlar las excepciones en aplicaciones administradas, vea [control de excepciones bajo /clr](../windows/exception-handling-cpp-component-extensions.md).  
  
> [!NOTE]
>  El control de excepciones estructurado funciona con Win32 para archivos de código fuente de C y C++. Sin embargo, no está diseñado específicamente para C++. Para asegurarse de que el código será más portable, use el control de excepciones de C++. Además, el control de excepciones de C++ es más flexible, ya que puede controlar excepciones de cualquier tipo. Para los programas de C++, se recomienda que utilice el mecanismo de control de excepciones de C++ ([try, catch y throw](../cpp/try-throw-and-catch-statements-cpp.md) instrucciones).  
  
 La instrucción compuesta detrás de la cláusula `__try` es la sección protegida. La instrucción compuesta detrás de la cláusula `__finally` es el controlador de terminación. El controlador especifica un conjunto de acciones que se sale de la sección protegida, con independencia de que se salga de la sección protegida a causa de una excepción (finalización anómala) o un paso explícito (finalización normal).  
  
 El control llega a una instrucción `__try` mediante la ejecución secuencial simple (paso explícito). Cuando el control entra en `__try`, su controlador asociado se activa. Si el flujo de control alcanza el final del bloque try, la ejecución continúa del modo siguiente:  
  
1.  Se invoca al controlador de terminación.  
  
2.  Cuando el controlador de terminación finaliza, la ejecución continúa después de la instrucción `__finally`. Independientemente de cómo finalice la sección protegida (por ejemplo, mediante una instrucción `goto` fuera del cuerpo protegido o una instrucción `return`), el controlador de finalización se ejecuta antes (`before`) de que el flujo de control salga de la sección protegida.  
  
     A **__finally** instrucción no bloquea la búsqueda de un controlador de excepciones adecuado.  
  
 Si se produce una excepción en el bloque `__try`, el sistema operativo debe buscar un controlador para la excepción; de lo contrario, el programa producirá un error. Si se encuentra el controlador, se ejecutan todos y cada uno de los bloques `__finally` y la ejecución se reanuda en el controlador.  
  
 Por ejemplo, suponga que una serie de llamadas de función vincula la función A a la función D, como se muestra en la ilustración siguiente. Cada función tiene un controlador de finalización. Si se produce una excepción en la función D y se controla en A, se llama a los controladores de finalización en este orden mientras el sistema desenreda la pila: D, C, B.  
  
 ![Orden de terminación &#45; la ejecución del controlador](../cpp/media/vc38cx1.gif "vc38CX1")  
Orden de terminación-ejecución de controladores  
  
> [!NOTE]
>  El comportamiento de try-finally es diferente de otros lenguajes que admiten el uso de **finalmente**, como C#.  Una instrucción `__try` puede tener `__finally` o `__except`, pero no ambos.  Si se van a usar ambos conjuntamente, una instrucción try-except externa debe incluir la instrucción try-finally interna.  Las reglas que especifican cuándo se ejecuta cada bloque también son diferentes.  
  
## <a name="the-leave-keyword"></a>La palabra clave __leave  
 La palabra clave `__leave` solo es válida dentro de la sección protegida de una instrucción `try-finally` y su efecto es saltar al final de la sección protegida. La ejecución continúa en la primera instrucción del controlador de finalización.  
  
 Una instrucción `goto` también puede saltar fuera de la sección protegida, pero el rendimiento se degrada porque invoca el desenredado de la pila. La instrucción `__leave` es más eficaz porque no produce el desenredado de la pila.  
  
## <a name="abnormal-termination"></a>Finalización anómala  
 Salir de un `try-finally` instrucción que usa el [longjmp](../c-runtime-library/reference/longjmp.md) función en tiempo de ejecución se considera una terminación anómala. No es válido saltar dentro de una instrucción `__try`, pero sí fuera. Todas las instrucciones `__finally` que están activas entre el punto de salida (finalización normal del bloque `__try`) y el punto de destino (el bloque `__except` que controla la excepción) deben ejecutarse. Esto recibe el nombre de desenredado local.  
  
 Si un **intente** bloque esté terminado de forma prematura por cualquier motivo, incluido un salto fuera del bloque, el sistema ejecuta asociado **finalmente** bloque como parte del proceso de desenredo de la pila. En tales casos, la [AbnormalTermination](http://msdn.microsoft.com/library/windows/desktop/ms679265) función devuelve TRUE si se invoca desde la **finalmente** bloque; de lo contrario, devuelve FALSE.  
  
 No se llama al controlador de finalización si un proceso se elimina en medio de la ejecución de una instrucción `try-finally`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Escribir un controlador de terminación](../cpp/writing-a-termination-handler.md)   
 [(C/C ++) de control de excepciones estructurado](../cpp/structured-exception-handling-c-cpp.md)   
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Sintaxis de controlador de terminación](http://msdn.microsoft.com/library/windows/desktop/ms681393)