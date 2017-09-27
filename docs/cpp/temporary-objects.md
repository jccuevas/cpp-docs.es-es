---
title: Objetos temporales | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 2f1e30ce63374a3b8fddb52f7d2afa3f219287d4
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="temporary-objects"></a>Objetos temporales
En algunos casos, es necesario que el compilador cree objetos temporales. Estos objetos temporales se pueden crear por las razones siguientes:  
  
-   Para inicializar una referencia de `const` con un inicializador de un tipo diferente del tipo subyacente de la referencia que se va a inicializar.  
  
-   Para almacenar el valor devuelto de una función que devuelve un tipo definido por el usuario. Estos objetos temporales solo se crean si el programa no copia el valor devuelto en un objeto. Por ejemplo:  
  
    ```  
    UDT Func1();    //  Declare a function that returns a user-defined  
                    //   type.  
  
    ...  
  
    Func1();        //  Call Func1, but discard return value.  
                    //  A temporary object is created to store the return  
                    //   value.  
    ```  
  
     Como el valor devuelto no se copia en otro objeto, se crea un objeto temporal. Un caso más común de creación de objetos temporales es durante la evaluación de una expresión en la que deben llamarse a funciones de operador sobrecargadas. Estas funciones de operador sobrecargadas devuelven un tipo definido por el usuario que normalmente no se copia a otro objeto.  
  
     Considere la expresión `ComplexResult = Complex1 + Complex2 + Complex3`. La expresión `Complex1 + Complex2` se evalúa y el resultado se almacena en un objeto temporal. Siguiente, la expresión *temporal* `+ Complex3` se evalúa, y se copia el resultado en `ComplexResult` (no está sobrecargado la suponiendo que el operador de asignación).  
  
-   Para almacenar el resultado de una conversión en un tipo definido por el usuario. Cuando un objeto de un tipo determinado se convierte explícitamente en un tipo definido por el usuario, este nuevo objeto se crea como un objeto temporal.  
  
 Los objetos temporales tienen una duración que viene definida por su punto de creación y por el punto en el que se destruyen. Cualquier expresión que cree más de un objeto temporal los acabará destruyendo en el orden inverso en que se crearon. Los puntos en los que se produce la destrucción se muestran en la tabla siguiente.  
  
### <a name="destruction-points-for-temporary-objects"></a>Puntos de destrucción de objetos temporales  
  
|Motivo por el que se creó el objeto temporal|Punto de destrucción|  
|------------------------------|-----------------------|  
|Resultado de evaluación de la expresión|Todos los objetos temporales creados como resultado de la evaluación de la expresión se destruyen al final de la instrucción de expresión (es decir, en el punto y coma) o al final de las expresiones de control en el caso de las instrucciones `for`, `if`, `while`, `do` y `switch`.|  
|Inicialización de referencias `const`|Si un inicializador no es un valor L del mismo tipo que la referencia que se va a inicializar, se crea un objeto temporal del tipo de objeto subyacente y se inicializa con la expresión de inicialización. Este objeto temporal se destruye inmediatamente después de que se destruya el objeto de referencia al que está enlazado.|  
  

