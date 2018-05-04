---
title: Aserción y mensajes proporcionados por el usuario (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e93798dadee3e4270d82eac84a794c6133c05c07
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="assertion-and-user-supplied-messages-c"></a>Aserción y mensajes proporcionados por el usuario (C++)
El C++ lenguaje admite tres error mecanismos de control que le ayudan a depuración la aplicación: la [#error (directiva)](../preprocessor/hash-error-directive-c-cpp.md), el [static_assert](../cpp/static-assert.md) palabra clave y el [assert (macro), _assert, _ wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) macro. Los tres mecanismos emiten mensajes de error y dos de ellos también prueban las aserciones de software. Una aserción de software especifica una condición que se espera que sea cierta (valor true) en un determinado punto del programa. Si se produce un error de aserción en tiempo de compilación, el compilador emite un mensaje de diagnóstico y un error de compilación. Si se produce un error de aserción en tiempo de ejecución, el sistema operativo emite un mensaje de diagnóstico y cierra la aplicación.  
  
## <a name="remarks"></a>Comentarios  
 La duración de la aplicación se compone de una fase de preprocesamiento, una de compilación y una de tiempo de ejecución. Cada mecanismo de control de errores tiene acceso a la información de depuración disponible durante una de estas fases. Para depurar eficazmente, seleccione el mecanismo que proporciona la información adecuada sobre esa fase:  
  
-   El [#error (directiva)](../preprocessor/hash-error-directive-c-cpp.md) está en vigor en tiempo de preprocesamiento. Emite incondicionalmente un mensaje definido por el usuario y hace que se produzca un error de compilación. El mensaje puede contener texto que se manipula mediante directivas de preprocesador, pero no se evalúa ninguna expresión resultante.  
  
-   El [static_assert](../cpp/static-assert.md) declaración está en vigor en tiempo de compilación. Prueba una aserción de software que está representada por una expresión de tipo entero definida por el usuario que se puede convertir en un valor booleano. Si la expresión se evalúa como cero (false), el compilador emite el mensaje definido por el usuario y se produce un error de compilación.  
  
     La declaración `static_assert` resulta especialmente útil para depurar plantillas, porque los argumentos de plantilla se pueden incluir en la expresión especificada por el usuario.  
  
-   El [assert (macro), _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) macro está vigente en tiempo de ejecución. Evalúa una expresión definida por el usuario y, si el resultado es cero, el sistema emite un mensaje de diagnóstico y cierra la aplicación. Muchas otras macros, como[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) y `_ASSERTE`, son similares a esta macro pero emitir mensajes de diagnóstico diferentes definido por el sistema o definido por el usuario.  
  
## <a name="see-also"></a>Vea también  
 [#error (directiva) (C/C ++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_ASSERT, _ASSERTE, _ASSERT_EXPR (Macros)](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [static_assert](../cpp/static-assert.md)   
 [_STATIC_ASSERT (macro)](../c-runtime-library/reference/static-assert-macro.md)   
 [Templates](../cpp/templates-cpp.md) (Plantillas [C++])