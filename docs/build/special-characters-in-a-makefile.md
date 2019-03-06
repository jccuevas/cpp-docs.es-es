---
title: Caracteres especiales en un archivo MAKE
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
ms.openlocfilehash: e2703adbbdba392b1a317e2656c6f3dba30a36b6
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420766"
---
# <a name="special-characters-in-a-makefile"></a>Caracteres especiales en un archivo MAKE

Para utilizar un carácter especial de NMAKE como un carácter literal, coloque un símbolo de intercalación (^) delante de él. NMAKE omite los símbolos de intercalación que preceden a otros caracteres. Los caracteres especiales son:

`:  ;  #  (  )  $  ^  \  {  }  !  @  —`

Un símbolo de intercalación (^) dentro de una cadena entre comillas se trata como un carácter de intercalación literal. Un símbolo de intercalación al final de una línea, inserta un carácter literal en una cadena o una macro.

En las macros, una barra diagonal inversa (\\) seguido por una nueva línea, carácter se sustituye por un espacio.

En los comandos de un símbolo de porcentaje (%) es un especificador de archivo. Para representar % literalmente en un comando, especifique un doble signo de porcentaje (%) en lugar de uno solo. En otras situaciones, NMAKE interpreta un solo carácter % literalmente, pero siempre interpreta un valor double %% como un solo carácter %. Por lo tanto, para representar un literal %%, especifique tres signos de porcentaje, %%%, o signos de porcentaje de cuatro %%%.

Para usar el signo de dólar ($) como un carácter literal en un comando, especifique dos signos de moneda ($). Este método también se puede utilizar en otras situaciones donde ^ $ funciona.

## <a name="see-also"></a>Vea también

[Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)
