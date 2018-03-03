---
title: Caracteres especiales en un archivo MAKE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6c574040d6004516682379a5e64b87c1b92388ec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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