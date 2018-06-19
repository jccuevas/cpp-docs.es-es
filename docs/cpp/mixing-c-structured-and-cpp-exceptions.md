---
title: Mezclar excepciones de C++ y C (estructuradas) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e9544e10ff0af41c0ff08fa51293c67c9977f2b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420111"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mezclar excepciones de C (estructuradas) y de C++
Si desea escribir código más portable, no se recomienda utilizar el control de excepciones estructuradas en un programa de C++. Sin embargo, es que a veces desee compilar con **/EHa** y mezclar excepciones estructuradas y código fuente de C++ y necesitará alguna capacidad para controlar ambos tipos de excepciones. Dado que un controlador de excepciones estructurado no tiene ningún concepto de objetos ni de excepciones con tipo, no puede controlar las excepciones producidas por código de C++; Sin embargo, C++ **catch** controladores pueden controlar excepciones estructuradas. Como tales, sintaxis del control de excepciones de C++ (**intente**, `throw`, **catch**) no se acepta por el compilador de C, pero la sintaxis del control de excepciones estructurado (`__try`, `__except`, `__finally`) es compatible con el compilador de C++.  
  
 Vea [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) para obtener información sobre cómo controlar las excepciones estructuradas como excepciones de C++.  
  
 Si mezcla excepciones estructuradas y de C++, tenga en cuenta lo siguiente:  
  
1.  Las excepciones de C++ y las excepciones estructuradas no se pueden mezclar dentro de la misma función.  
  
2.  Los controladores de finalización (bloques `__finally`) se ejecutan siempre, incluso durante el desenredo después de producirse una excepción.  
  
3.  Control de excepciones de C++ puede detectar y conservar semántica de desenredo en todos los módulos compilados con la [/EH](../build/reference/eh-exception-handling-model.md) opción del compilador (esta opción habilita la semántica de desenredo).  
  
4.  Puede que haya situaciones en las que no se llame a las funciones de destructor para todos los objetos. Por ejemplo, si una excepción estructurada se produce al intentar realizar una llamada de función a través de un puntero de función inicializado, y esa función toma como parámetros objetos que se construyeron antes de la llamada, no se llamará a los destructores de esos objetos durante el desenredo de la pila.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Uso de setjmp o longjmp en programas de C++](../cpp/using-setjmp-longjmp.md)  
  
-   [Diferencias entre SEH y C++ EH](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones de C++](../cpp/cpp-exception-handling.md)