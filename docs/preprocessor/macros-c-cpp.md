---
title: Macros) (C/C ++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- preprocessor
- preprocessor, macros
- Visual C++, preprocessor macros
ms.assetid: a7bfc5d4-2537-4fe0-bef0-70cec0b43388
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6794cb56566e552a47f19d53f4092c1a9749969c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="macros-cc"></a>Macros (C/C++)
Preprocesamiento expande las macros en todas las líneas que no son directivas de preprocesador (líneas que no tienen un **#** como el primer carácter no sea un espacio en blanco) y en partes de algunas directivas que no se omiten como parte de una compilación condicional. Las directivas de "compilación condicional" permiten suprimir la compilación de partes de un archivo de código fuente mediante la prueba de un identificador o una expresión de constante para determinar qué bloques de texto se pasan al compilador y qué bloques de texto se quitan del archivo de código fuente durante el preprocesamiento.  
  
 La directiva `#define` se utiliza normalmente para asociar identificadores significativos con constantes, palabras clave e instrucciones o expresiones usadas con frecuencia. Los identificadores que representan constantes se denominan a veces "constantes simbólicas" o "constantes del manifiesto". Los identificadores que representan instrucciones o expresiones se denominan "macros". En esta documentación de preprocesador, solo se utiliza el término "macro".  
  
 Cuando el nombre de la macro se reconoce en el texto original del programa o en los argumentos de otros comandos de preprocesador determinados, se trata como una llamada a esa macro. El nombre de la macro se reemplaza por una copia del cuerpo de la macro. Si la macro acepta argumentos, los argumentos reales que siguen al nombre de la macro se sustituyen por los parámetros formales en el cuerpo de la macro. El proceso de reemplazar la llamada a una macro por la copia procesada del cuerpo se denomina "expansión" de la llamada a la macro.  
  
 En la práctica, hay dos tipos de macros. Las macros "similares a objeto" no toman argumentos, mientras que las macros "similares a función" pueden definirse para aceptar argumentos de modo que parezcan y actúen como llamadas de función. Dado que las macros no representan llamadas de función reales, a veces se puede acelerar la ejecución de los programas reemplazando las llamadas de función por macros. (En C++, las funciones insertadas suelen ser un método preferido). Sin embargo, las macros pueden crear problemas si no se definen y utilizan con cuidado. Puede que tenga que utilizar paréntesis en definiciones de macro con argumentos para conservar la prioridad correcta en una expresión. Además, puede que las macros no controlen correctamente las expresiones con efectos secundarios. Consulte la `getrandom` ejemplo de [el #define (directiva)](../preprocessor/hash-define-directive-c-cpp.md) para obtener más información.  
  
 Una vez que haya definido una macro, no podrá volver a definirla en un valor diferente sin antes quitar la definición original. Sin embargo, puede volver a definir la macro con exactamente la misma definición. De este modo, la misma definición puede aparecer más de una vez en un programa.  
  
 El signo #**undef** directiva quita la definición de una macro. Una vez que haya quitado la definición, podrá volver a definir la macro en un valor diferente. [El #define (directiva)](../preprocessor/hash-define-directive-c-cpp.md) y [la directiva #undef](../preprocessor/hash-undef-directive-c-cpp.md) tratan la `#define` y `#undef` directivas, respectivamente.  
  
 Para obtener más información, vea  
  
-   [Macros y C++](../preprocessor/macros-and-cpp.md)  
  
-   [Macros variádicas](../preprocessor/variadic-macros.md)  
  
-   [Macros predefinidas](../preprocessor/predefined-macros.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia del preprocesador de C/C++](../preprocessor/c-cpp-preprocessor-reference.md)