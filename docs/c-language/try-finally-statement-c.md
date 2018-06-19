---
title: try-finally (Instrucción) (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 54e33f4648861e872ab8d866930d3412a56a5ef4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391553"
---
# <a name="try-finally-statement-c"></a>try-finally (Instrucción) (C)
**Específicos de Microsoft**  
  
 La instrucción `try-finally` es una extensión de Microsoft al lenguaje C que permite que las aplicaciones garanticen la ejecución del código de limpieza cuando se interrumpe la ejecución de un bloque de código. La limpieza consta de tareas como desasignar memoria, cerrar archivos y liberar identificadores de archivo. La instrucción `try-finally` es especialmente útil para las rutinas que tienen varios lugares donde comprobar un error, lo que puede causar que la rutina termine antes de tiempo.  
  
 *try-finally-statement*:  
 **__try**  *compound-statement*  
  
 **__finally**  *compound-statement*  
  
 La instrucción compuesta detrás de la cláusula `__try` es la sección protegida. La instrucción compuesta detrás de la cláusula `__finally` es el controlador de terminación. El controlador especifica un conjunto de acciones que se ejecutan cuando se sale de la sección protegida, tanto si se sale de esta sección por una excepción (terminación anómala) o después de pasar por ella (terminación normal).  
  
 El control llega a una instrucción `__try` mediante la ejecución secuencial simple (paso explícito). Cuando el control entra en la instrucción `__try`, su controlador asociado se activa. La ejecución continúa de la siguiente manera:  
  
1.  Se ejecuta la sección protegida.  
  
2.  Se invoca al controlador de terminación.  
  
3.  Cuando el controlador de terminación finaliza, la ejecución continúa después de la instrucción `__finally`. Independientemente de cómo finalice la sección protegida (por ejemplo, mediante una instrucción `goto` fuera del cuerpo protegido o a través de una instrucción `return`), el controlador de terminación se ejecuta antes de que el flujo de control salga de la sección protegida.  
  
 La palabra clave `__leave` es válida dentro de un bloque de instrucciones `try-finally`. El efecto de `__leave` es saltar al final del bloque `try-finally`. El controlador de terminación se ejecuta inmediatamente. Aunque se puede utilizar una instrucción `goto` para lograr el mismo resultado, una instrucción `goto` produce el desenredado de la pila. La instrucción `__leave` es más eficaz porque no produce el desenredado de la pila.  
  
 Salir de una instrucción `try-finally` mediante una instrucción `return` o mediante la función de tiempo de ejecución `longjmp` se considera una terminación anómala. No es válido saltar dentro de una instrucción `__try`, pero sí fuera. Se deben ejecutar todas las instrucciones `__finally` activas entre el punto de salida y el destino. Esto recibe el nombre de "desenredado local".  
  
 No se llama al controlador de terminación si un proceso se elimina mientras se ejecuta una instrucción `try-finally`.  
  
> [!NOTE]
>  El control estructurado de excepciones funciona con archivos de código fuente de C y C++. Sin embargo, no está diseñado específicamente para C++. Para asegurarse de que el código será más portable, use el control de excepciones de C++. Además, el mecanismo de control de excepciones de C++ es mucho más flexible, ya que puede controlar excepciones de cualquier tipo.  
  
> [!NOTE]
>  Para los programas de C++, se debe usar el control de excepciones de C++ en lugar del control estructurado de excepciones. Para obtener más información, vea [Control de excepciones](../cpp/exception-handling-in-visual-cpp.md) en la *Referencia del lenguaje C++*.  
  
 Consulte el ejemplo de la [instrucción try-except](../c-language/try-except-statement-c.md) para ver cómo funciona la instrucción `try-finally`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [try-finally (Instrucción)](../cpp/try-finally-statement.md)