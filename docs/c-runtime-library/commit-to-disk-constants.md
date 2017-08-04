---
title: "Constantes de confirmación en disco | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.constants
dev_langs:
- C++
helpviewer_keywords:
- commit-to-disk constants
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: c8aa858543b100239d0fe2a557b22452a0a0d572
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="commit-to-disk-constants"></a>Constantes de confirmación en disco
**Específicos de Microsoft**  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas constantes específicas de Microsoft se especifican si se vacía el búfer asociado al archivo abierto en los búferes del sistema operativo o en el disco. El modo se incluye en la cadena que especifica el tipo de acceso de lectura/escritura (**"r"**, **"w"**, **"a"**, **"r+"**, **"w+"** y **"a+"**).  
  
 Los modos de confirmación en disco son los siguientes:  
  
 **c**  
 Escribe en el disco el contenido no escrito del búfer especificado. Esta funcionalidad de confirmación en disco solo se produce en llamadas explícitas a la función [fflush](../c-runtime-library/reference/fflush.md) o [_flushall](../c-runtime-library/reference/flushall.md). Este modo es útil cuando se trabaja con información confidencial. Por ejemplo, si el programa se cierra después de llamar a `fflush` o `_flushall`, puede estar seguro de que los datos han llegado a los búferes del sistema operativo. Sin embargo, a menos que se abra un archivo con la opción **c**, los datos podrían no llegar nunca al disco si el sistema operativo también finaliza.  
  
 **n**  
 Escribe en los búferes del sistema operativo el contenido no escrito del búfer especificado. El sistema operativo puede almacenar datos en caché y, después, determinar un momento óptimo para escribirlos en el disco. En muchas condiciones, este comportamiento hace que el funcionamiento del programa sea eficaz. Sin embargo, si la retención de datos es crítica (por ejemplo, transacciones bancarias o información de billetes de avión), considere la posibilidad de usar la opción **c**. El modo **n** es el valor predeterminado.  
  
> [!NOTE]
>  Las opciones **c** y **n** no forman parte de la norma ANSI para `fopen`, pero son extensiones de Microsoft y no deben usarse si se desea usar la portabilidad de ANSI.  
  
## <a name="using-the-commit-to-disk-feature-with-existing-code"></a>Uso de la característica de confirmación en disco con código existente  
 De forma predeterminada, las llamadas a las funciones [fflush](../c-runtime-library/reference/fflush.md) o [_flushall](../c-runtime-library/reference/flushall.md) de la biblioteca escriben datos en búferes mantenidos por el sistema operativo. El sistema operativo determina el momento óptimo para escribir realmente los datos en el disco. La característica de confirmación en disco de la biblioteca en tiempo de ejecución permite asegurarse de que los datos críticos se escriben directamente en el disco y no en los búferes del sistema operativo. Puede proporcionar esta funcionalidad a un programa existente sin escribirla de nuevo mediante la vinculación de sus archivos objeto a COMMODE.OBJ.  
  
 En el archivo ejecutable resultante, las llamadas a `fflush` escriben el contenido del búfer directamente en el disco y las llamadas a `_flushall` escriben el contenido de todos los búferes en el disco. Estas dos funciones son las únicas afectadas por COMMODE.OBJ.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../c-runtime-library/stream-i-o.md)   
 [_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)
