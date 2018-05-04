---
title: Macros nulos y no definidas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, undefined macros
- Null macros in NMAKE
- macros, null and undefined
- undefined macros and NMAKE
- NMAKE program, null macros
ms.assetid: 1db4611a-1755-4328-b00f-d35365af8b6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 494a084ee5ba1da29c132aa632b647b37f305855
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="null-and-undefined-macros"></a>Macros Null y no definidas
Macros nulos y no definidas se amplían a cadenas nulas, pero una macro definida como una cadena nula se considera definida en expresiones de preprocesamiento. Para definir una macro como una cadena nula, especificar ningún carácter excepto espacios o tabulaciones después del signo igual (=) en una línea de comandos o el archivo de comandos y encierre la cadena null o definición de comillas dobles (""). Para definir una macro, utilice **! UNDEF.** Para obtener más información, consulte [directivas de preprocesamiento de archivos MAKE](../build/makefile-preprocessing-directives.md).  
  
## <a name="see-also"></a>Vea también  
 [Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)