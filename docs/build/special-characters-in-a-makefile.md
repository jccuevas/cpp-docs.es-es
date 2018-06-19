---
title: Caracteres especiales en un archivo MAKE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 157f9ed499ef7a0ac9efdd6bebe118ca593acabb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380464"
---
# <a name="special-characters-in-a-makefile"></a>Caracteres especiales en un archivo MAKE
Para utilizar un carácter especial de NMAKE como un carácter literal, coloque un símbolo de intercalación (^) delante de él. NMAKE omite los símbolos de intercalación que preceden a otros caracteres. Los caracteres especiales son:  
  
 `:  ;  #  (  )  $  ^  \  {  }  !  @  —`  
  
 Un símbolo de intercalación (^) dentro de una cadena entre comillas se trata como un carácter de intercalación literal. Un símbolo de intercalación al final de una línea inserta un carácter de nueva línea literal en una cadena o una macro.  
  
 En macros, una barra diagonal inversa (\\) seguido por una nueva línea carácter se reemplaza por un espacio.  
  
 En los comandos, un símbolo de porcentaje (%) es un especificador de archivo. Para representar % literalmente en un comando, especifique un doble signo de porcentaje (%) en lugar de una sola instrucción. En otras situaciones, NMAKE interpreta un solo carácter % literalmente, pero siempre interpreta un doble %% como un solo carácter %. Por lo tanto, para representar un literal %%, especifique tres signos de porcentaje, %%%, o signos de porcentaje de cuatro %%%.  
  
 Para usar el signo de dólar ($) como un carácter literal en un comando, especifique dos signos de moneda ($). Este método también se puede utilizar en otras situaciones donde ^ $ funciona.  
  
## <a name="see-also"></a>Vea también  
 [Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)