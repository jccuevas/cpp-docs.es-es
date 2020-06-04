---
title: Mezclar C (estructuradas) C++ y excepciones
ms.date: 08/14/2018
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
ms.openlocfilehash: e49731f1c81057002eaae2bef16cda4a5cf86f8d
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246460"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mezclar C (estructuradas) C++ y excepciones

Si desea escribir código portable, no se recomienda el uso del control de excepciones estructurado (SEH) C++ en un programa. Sin embargo, a veces es posible que desee compilar mediante [/EHA](../build/reference/eh-exception-handling-model.md) y C++ mezclar las excepciones estructuradas y el código fuente, y necesite alguna utilidad para controlar ambos tipos de excepciones. Dado que un controlador de excepciones estructurado no tiene ningún concepto de objetos o excepciones con tipo, no puede controlar C++ las excepciones iniciadas por el código. Sin embargo C++ , los controladores **catch** pueden controlar las excepciones estructuradas. C++el compilador de C no acepta la sintaxis de control de excepciones (**try**, **Throw**, **catch**), pero el compiladoradmite C++ la sintaxis de control de excepciones estructurado ( **__try**, **__except**, __finally).

Consulte [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) para obtener información sobre cómo controlar las excepciones estructuradas como C++ excepciones.

Si mezcla estructurada y C++ excepciones, tenga en cuenta estos posibles problemas:

- Las excepciones de C++ y las excepciones estructuradas no se pueden mezclar dentro de la misma función.

- Los controladores de finalización (bloques de **__finally** ) siempre se ejecutan, incluso durante el desenredado después de que se produzca una excepción.

- C++el control de excepciones puede detectar y conservar la semántica de desenredo en todos los módulos compilados con las opciones del compilador [/EH](../build/reference/eh-exception-handling-model.md) , que habilitan la semántica de desenredo.

- Puede que haya situaciones en las que no se llame a las funciones de destructor para todos los objetos. Por ejemplo, si se produce una excepción estructurada al intentar realizar una llamada a una función a través de un puntero de función no inicializado y esa función toma como objetos de parámetros construidos antes de la llamada, no se llama a los destructores de esos objetos. durante el desenredo de la pila.

## <a name="next-steps"></a>Pasos siguientes

- [Usar setjmp o longjmp en C++ programas](../cpp/using-setjmp-longjmp.md)

  Vea más información sobre el uso de `setjmp` y `longjmp` en C++ programas.

- [Controlar excepciones estructuradas en C++](../cpp/exception-handling-differences.md)

  Vea ejemplos de las formas que puede usar C++ para controlar las excepciones estructuradas.

## <a name="see-also"></a>Vea también

[Prácticas C++ recomendadas modernas para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md)
