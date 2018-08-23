---
title: Mezclar excepciones de C++ y C (estructurado) | Microsoft Docs
ms.custom: ''
ms.date: 08/14/2018
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
ms.openlocfilehash: 580fb4c96db70b612135ac48e30bd9c0d45c4d1c
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2018
ms.locfileid: "42573392"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mezclar excepciones de C++ y C (estructurado)

Si desea escribir código portable, no se recomienda el uso estructurado de control de excepciones (SEH) en un programa de C++. Sin embargo, que es posible que a veces desee compilar con [/EHa](../build/reference/eh-exception-handling-model.md) y mezclar excepciones estructuradas y código fuente de C++ y necesitará alguna capacidad para controlar ambos tipos de excepciones. Dado que un controlador de excepciones estructurado no tiene ningún concepto de objetos de excepciones con tipo, que no puede controlar las excepciones producidas por código de C++. Sin embargo, C++ **catch** controladores pueden controlar excepciones estructuradas. Sintaxis del control de excepciones de C++ (**intente**, **throw**, **catch**) no está aceptados por el compilador de C, pero la sintaxis de control de excepciones estructurado (**__try**, **__except**, **__finally**) es compatible con el compilador de C++.

Consulte [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) para obtener información sobre cómo controlar las excepciones estructuradas como excepciones de C++.

Si mezcla estructurado y excepciones de C++, tenga en cuenta estos posibles problemas:

- Las excepciones de C++ y las excepciones estructuradas no se pueden mezclar dentro de la misma función.

- Los controladores de terminación (**__finally** bloques) se ejecutan siempre, incluso durante el desenredo después de que se produce una excepción.

- Control de excepciones de C++ puede detectar y conservar semántica de desenredo en todos los módulos compilados con la [/EH](../build/reference/eh-exception-handling-model.md) opciones del compilador, que permiten la semántica de desenredo.

- Puede que haya situaciones en las que no se llame a las funciones de destructor para todos los objetos. Por ejemplo, si se produce una excepción estructurada al intentar llamar a una función a través de un puntero de función no inicializado, y esa función toma como parámetros objetos que se construyeron antes de la llamada, los destructores de esos objetos no se llama a durante el desenredo de pila.

## <a name="next-steps"></a>Pasos siguientes

- [Uso de setjmp o longjmp en programas de C++](../cpp/using-setjmp-longjmp.md)

  Obtenga más información sobre el uso de `setjmp` y `longjmp` en programas de C++.

- [Controlar excepciones estructuradas en C++](../cpp/exception-handling-differences.md)

  Vea ejemplos de las formas que puede usar C++ para las excepciones estructurada de identificador.

## <a name="see-also"></a>Vea también

[Control de excepciones de C++](../cpp/cpp-exception-handling.md)  
