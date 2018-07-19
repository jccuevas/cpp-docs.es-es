---
title: Dónde definir Macros | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- defining macros
- macros, NMAKE
- NMAKE program, defining macros
ms.assetid: 0fc59ec5-5f58-4644-b7da-7b021f7001af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9cf3e87a50362c770d45f00c4dc17ac3d264f611
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380919"
---
# <a name="where-to-define-macros"></a>Dónde definir macros
Definir macros en una línea de comandos, archivo de comandos, archivos MAKE o el archivo Tools.ini.  
  
 En un archivo MAKE o el archivo Tools.ini, cada definición de macro debe aparecer en una línea independiente y no puede comenzar con un espacio o tabulación. Se omiten los espacios o tabulaciones a ambos lados del signo igual. Todos los [cadena caracteres](../build/defining-an-nmake-macro.md) son literales, incluidas las comillas tipográficas y los espacios incrustados.  
  
 En una línea de comandos o el archivo de comandos, espacios y tabulaciones delimitan los argumentos y no se pueden delimitar el signo igual. Si `string` tiene insertados espacios o tabulaciones, encierre la propia cadena o la macro completa entre comillas dobles ("").  
  
## <a name="see-also"></a>Vea también  
 [Definición de una macro NMAKE](../build/defining-an-nmake-macro.md)