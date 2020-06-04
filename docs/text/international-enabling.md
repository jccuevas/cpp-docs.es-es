---
title: Internacionalización
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
ms.openlocfilehash: b6c645bafef87ed0b2d43903f4752ef659d79f89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375801"
---
# <a name="international-enabling"></a>Internacionalización

La mayoría del código C y C+ tradicional hace suposiciones sobre la manipulación de caracteres y cadenas que no funcionan bien para aplicaciones internacionales. Aunque MFC y la biblioteca en tiempo de ejecución admiten Unicode o MBCS, todavía hay trabajo que hacer. Para guiarlo, en esta sección se explica el significado de "habilitación internacional" en Visual C++:

- Unicode y MBCS se habilitan mediante tipos de datos portátiles en listas de parámetros de función MFC y tipos de valor devuelto. Estos tipos se definen condicionalmente de las maneras adecuadas, dependiendo de si la compilación define el símbolo `_UNICODE` o el símbolo `_MBCS` (lo que significa DBCS). Diferentes variantes de las bibliotecas MFC se vinculan automáticamente con la aplicación, dependiendo de cuál de estos dos símbolos defina la compilación.

- El código de la biblioteca de clases utiliza funciones portátiles en tiempo de ejecución y otros medios para garantizar un comportamiento correcto de Unicode o MBCS.

- Todavía debe controlar ciertos tipos de tareas de internacionalización en el código:

  - Utilice las mismas funciones portátiles en tiempo de ejecución que hacen que MFC sea portátil en cualquier entorno.

  - Haga que las cadenas literales y `_T` los caracteres sean portátiles en cualquier entorno, utilizando la macro. Para obtener más información, consulte [Asignaciones de texto genérico en tchar.h](../text/generic-text-mappings-in-tchar-h.md).

  - Tome precauciones al analizar cadenas en MBCS. Estas precauciones no son necesarias en Unicode. Para obtener más información, consulte Consejos de programación de [MBCS](../text/mbcs-programming-tips.md).

  - Tenga cuidado si mezcla caracteres ANSI (8 bits) y Unicode (16 bits) en la aplicación. Es posible utilizar caracteres ANSI en algunas partes del programa y caracteres Unicode en otras, pero no se pueden mezclar en la misma cadena.

  - No codifique cadenas de disco duro en la aplicación. En su lugar, constérdelos con recursos STRINGTABLE agregándolos al archivo .rc de la aplicación. A continuación, la aplicación se puede localizar sin necesidad de cambios en el código fuente o recompilación. Para obtener más información acerca de los recursos STRINGTABLE, vea [Editor de cadenas](../windows/string-editor.md).

> [!NOTE]
> Los conjuntos de caracteres europeos y MBCS tienen algunos caracteres, como letras acentuadas, con códigos de caracteres superiores a 0x80. Dado que la mayoría del código utiliza caracteres firmados, estos caracteres mayores que 0x80 se extienden por signo cuando se convierten a **int**. Esto es un problema para la indexación de matrices porque los caracteres de signo extendido, siendo negativos, se indizan fuera de la matriz. Los idiomas que utilizan MBCS, como el japonés, también son únicos. Dado que un carácter puede constar de 1 o 2 bytes, siempre debe manipular ambos bytes al mismo tiempo.

## <a name="see-also"></a>Consulte también

[Unicode y MBCS](../text/unicode-and-mbcs.md)<br/>
[Estrategias de Internacionalización](../text/internationalization-strategies.md)
