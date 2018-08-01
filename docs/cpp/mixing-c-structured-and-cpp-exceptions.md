---
title: Mezclar excepciones de C++ y C (estructuradas) | Microsoft Docs
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
ms.openlocfilehash: 6e632faddb3b4f59733710a915ed121a12f4e0c6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404868"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mezclar excepciones de C (estructuradas) y de C++
Si desea escribir código más portable, no se recomienda utilizar el control de excepciones estructuradas en un programa de C++. Sin embargo, que es posible que a veces desee compilar con **/EHa** y mezclar excepciones estructuradas y código fuente de C++ y necesitará alguna capacidad para controlar ambos tipos de excepciones. Dado que un controlador de excepciones estructurado no tiene ningún concepto de objetos de excepciones con tipo, que no puede controlar las excepciones producidas por código de C++; Sin embargo, C++ **catch** controladores pueden controlar excepciones estructuradas. Como tales, sintaxis de control de excepciones de C++ (**intente**, **throw**, **catch**) no está aceptados por el compilador de C, pero la sintaxis de control de excepciones estructurado (**__try** , **__except**, **__finally**) es compatible con el compilador de C++.  
  
 Consulte [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) para obtener información sobre cómo controlar las excepciones estructuradas como excepciones de C++.  
  
 Si mezcla excepciones estructuradas y de C++, tenga en cuenta lo siguiente:  
  
1.  Las excepciones de C++ y las excepciones estructuradas no se pueden mezclar dentro de la misma función.  
  
2.  Los controladores de terminación (**__finally** bloques) se ejecutan siempre, incluso durante el desenredo después de que se produce una excepción.  
  
3.  Control de excepciones de C++ puede detectar y conservar semántica de desenredo en todos los módulos compilados con la [/EH](../build/reference/eh-exception-handling-model.md) opción del compilador (esta opción habilita la semántica de desenredo).  
  
4.  Puede que haya situaciones en las que no se llame a las funciones de destructor para todos los objetos. Por ejemplo, si una excepción estructurada se produce al intentar realizar una llamada de función a través de un puntero de función inicializado, y esa función toma como parámetros objetos que se construyeron antes de la llamada, no se llamará a los destructores de esos objetos durante el desenredo de la pila.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
  
-   [Uso de setjmp o longjmp en programas de C++](../cpp/using-setjmp-longjmp.md)  
  
-   [Diferencias entre SEH y C++ EH](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones de C++](../cpp/cpp-exception-handling.md)