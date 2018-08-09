---
title: Internacionalización | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5afb7bd027fca215e1c10c111132ee881ad49548
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018070"
---
# <a name="international-enabling"></a>Internacionalización
Código de C y C++ más tradicional hace suposiciones sobre la manipulación de cadenas y caracteres que no funcionan bien para aplicaciones internacionales. Aunque MFC y la biblioteca en tiempo de ejecución son compatibles con Unicode o MBCS, todavía hay trabajo para que pueda hacer. Para guiarle, esta sección explica el significado de "internacionalización" en Visual C++:  
  
-   Unicode y MBCS se habilitan por medio de los tipos de datos portables en MFC listas de parámetros de función y tipos de valor devuelto. Estos tipos se definen condicionalmente de forma apropiada, dependiendo de si la compilación define el símbolo `_UNICODE` o el símbolo `_MBCS` (lo que significa DBCS). Variantes diferentes de las bibliotecas MFC se vinculan automáticamente con la aplicación, dependiendo de cuál de estos dos símbolos define la compilación.  
  
-   Código de la biblioteca de clases utiliza funciones portables en tiempo de ejecución y otros medios para garantizar el comportamiento correcto de MBCS o Unicode.  
  
-   Todavía debe controlar ciertos tipos de tareas de internacionalización en el código:  
  
    -   Use las mismas funciones de tiempo de ejecución portables que hagan que MFC portables en cada entorno.  
  
    -   Hacer que cadenas literales y caracteres portables en cada entorno, mediante la `_T` macro. Para obtener más información, consulte [asignaciones de texto genérico en Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
    -   Tomar precauciones al analizar cadenas en MBCS. Estas precauciones no son necesarios en Unicode. Para obtener más información, consulte [sugerencias de programación para MBCS](../text/mbcs-programming-tips.md).  
  
    -   Tenga cuidado si mezcla ANSI (8 bits) y caracteres de Unicode (16 bits) en la aplicación. Es posible usar caracteres ANSI en algunas partes del programa y caracteres Unicode en otras, pero no se pueden mezclar en la misma cadena.  
  
    -   Hacer que las cadenas no codifique de forma rígida en la aplicación. En su lugar, hacerlos recursos STRINGTABLE agregándolas al archivo .rc de la aplicación. A continuación, se puede localizar su aplicación sin necesidad de cambios de código fuente o recompilación. Para obtener más información acerca de los recursos STRINGTABLE, vea [Editor de cadenas](../windows/string-editor.md).  
  
> [!NOTE]
>  Juegos de caracteres de Europa y MBCS tienen algunos caracteres, como las letras acentuadas, con códigos de carácter mayores que 0 x 80. Dado que la mayoría del código utiliza caracteres con signo, estos caracteres mayores que 0 x 80 son signos al convertir a **int**. Se trata de un problema para la indización de matriz porque los caracteres extendidos de inicio de sesión que sean negativos índices fuera de la matriz. Idiomas que utilizan MBCS, como el japonés, también son únicos. Dado que un carácter puede consistir en 1 o 2 bytes, siempre debe manipular ambos bytes al mismo tiempo.  
  
## <a name="see-also"></a>Vea también  
 [Unicode y MBCS](../text/unicode-and-mbcs.md)   
 [Estrategias de internacionalización](../text/internationalization-strategies.md)