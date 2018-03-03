---
title: Nombres de entorno | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: efae64f64ef6b5ed92dffafb9f83a0e32ab38513
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="environment-names"></a>Nombres de entorno
**ANSI 4.10.4.4** El conjunto de nombres de entorno y el método para modificar la lista de entorno utilizada por la función [getenv](../c-runtime-library/reference/getenv-wgetenv.md)  
  
 El conjunto de nombres de entorno es ilimitado.  
  
 Para cambiar las variables de entorno desde un programa de C, se debe llamar a la función [_putenv](../c-runtime-library/reference/putenv-wputenv.md). Para cambiar variables de entorno desde la línea de comandos de Windows, utilice el comando SET (por ejemplo, SET LIB = D: LIBS).  
  
 Las variables de entorno establecidas desde un programa de C solo existen mientras la copia del host del shell de comandos del sistema operativo está ejecutando (CMD.EXE o COMMAND.COM). Por ejemplo, la línea  
  
```  
system( SET LIB = D:\LIBS );  
```  
  
 ejecutaría una copia del shell de comandos (CMD.EXE), establecería la variable de entorno LIB y volvería al programa de C, saliendo de la copia secundaria de CMD.EXE. Cuando se sale de esa copia de CMD.EXE, se quita la variable de entorno temporal LIB.  
  
 Igualmente, los cambios realizados por la función `_putenv` solo duran hasta que el programa finaliza.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)   
 [_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)