---
title: Macros nulos y no definidas | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ee85d6959536d2845d7b6e6ccf7f07924e46143f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="null-and-undefined-macros"></a>Macros Null y no definidas
Macros nulos y no definidas se amplían a cadenas nulas, pero una macro definida como una cadena nula se considera definida en expresiones de preprocesamiento. Para definir una macro como una cadena nula, especificar ningún carácter excepto espacios o tabulaciones después del signo igual (=) en una línea de comandos o el archivo de comandos y encierre la cadena null o definición de comillas dobles (""). Para definir una macro, utilice **! UNDEF.** Para obtener más información, consulte [directivas de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-directives.md).  
  
## <a name="see-also"></a>Vea también  
 [Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)