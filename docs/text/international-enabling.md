---
title: "Habilitar la internacionalización | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce0210546dafd354d0d62225c97df8b36a8d84e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="international-enabling"></a>Internacionalización
Código de C y C++ más tradicional hace suposiciones sobre la manipulación de cadenas y caracteres que no funcionan bien en aplicaciones internacionales. Aunque MFC y la biblioteca en tiempo de ejecución admiten Unicode o MBCS, todavía queda trabajo para el programador. Para guiarle, en esta sección se explica el significado de "internacionalización" en Visual C++:  
  
-   Unicode y MBCS se habilitan por medio de tipos de datos portables en MFC listas de parámetros de función y tipos de valor devuelto. Estos tipos se definen condicionalmente de forma apropiada, dependiendo de si la compilación define el símbolo **_UNICODE** o el símbolo **_MBCS** (lo que significa DBCS). Diferentes variaciones de las bibliotecas MFC se vinculan automáticamente a la aplicación, dependiendo de cuál de estos dos símbolos define la compilación.  
  
-   Código de la biblioteca de clases utiliza funciones portables en tiempo de ejecución y otros medios para asegurar un comportamiento correcto de Unicode o MBCS.  
  
-   Todavía debe controlar ciertos tipos de tareas de internacionalización en el código:  
  
    -   Use las mismas funciones portables de tiempo de ejecución que hagan que MFC sea portable en cualquier entorno.  
  
    -   Hacer que las cadenas literales y caracteres portables en cada entorno, mediante la **_T** macro. Para obtener más información, consulte [asignaciones de texto genérico en Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
    -   Tome precauciones al analizar cadenas bajo MBCS. Estas precauciones no son necesarias en Unicode. Para obtener más información, consulte [sugerencias de programación para MBCS](../text/mbcs-programming-tips.md).  
  
    -   Tenga cuidado si mezcla ANSI (8 bits) y los caracteres Unicode (16 bits) en la aplicación. Es posible utilizar caracteres ANSI en algunas partes del programa y caracteres Unicode en otras, pero no se pueden mezclar en la misma cadena.  
  
    -   No las cadenas de no codifique de forma rígida en la aplicación. En su lugar, hágalos recursos STRINGTABLE agregándolas al archivo .rc de la aplicación. A continuación, se puede localizar la aplicación sin necesidad de modificar el código fuente ni volver a compilar. Para obtener más información acerca de los recursos STRINGTABLE, vea [Editor de cadena](../windows/string-editor.md).  
  
> [!NOTE]
>  Juegos de caracteres europeos y MBCS tienen algunos caracteres, como las letras acentuadas, con códigos de caracteres superiores a 0 x 80. Dado que la mayoría del código utiliza caracteres con signo, estos caracteres superiores a 0 x 80 son signos hasta llegar al convertir a `int`. Se trata de un problema para la indización de matriz porque los caracteres extendidos con signo que sean negativos, índices fuera de la matriz. Idiomas que utilizan MBCS, como el japonés, también son únicos. Dado que un carácter puede consistir en 1 o 2 bytes, siempre debería manipular ambos bytes a la vez.  
  
## <a name="see-also"></a>Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Estrategias de internacionalización](../text/internationalization-strategies.md)