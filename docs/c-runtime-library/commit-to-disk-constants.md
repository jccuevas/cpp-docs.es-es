---
title: "Constantes de confirmaci&#243;n en disco | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.constants"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "constantes de confirmación en disco"
ms.assetid: 0b903b23-b4fa-431e-a937-51d95f695ecf
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Constantes de confirmaci&#243;n en disco
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
## Sintaxis  
  
```  
  
#include <stdio.h>  
```  
  
## Comentarios  
 Estas constantes Microsoft\- específicas especifican si el búfer asociado al archivo abierta se vaciado a los búferes del sistema operativo o el disco.  Incluyen el modo en la cadena que especifica el tipo de acceso de lectura y escritura \(**"r"**, **"w"**, **"a"**, **"r\+"**, **"w\+"**, **"a\+"**\).  
  
 Los modos de confirmación\-a\- disco son los siguientes:  
  
 **c**  
 Escribe el contenido nos tipo de búfer especificado en el disco.  Esta funcionalidad de confirmación\-a\- disco sólo aparece en las llamadas explícitas a [fflush](../c-runtime-library/reference/fflush.md) o a la función de [\_flushall](../c-runtime-library/reference/flushall.md) .  Este modo es útil al trabajar con datos confidenciales.  Por ejemplo, si el programa termina después de una llamada a `fflush` o a `_flushall`, puede asegurarse de que los datos alcanzaron los búferes del sistema operativo.  Sin embargo, a menos que el archivo se abre con la opción de **c** , los datos podrían nunca crearla en el disco si el sistema operativo también finaliza.  
  
 **n**  
 Escribe el contenido nos tipo de búfer especificado a los búferes del sistema operativo.  El sistema operativo puede almacenar en caché datos y después determinar un poco óptimo de escribir en el disco.  En muchas condiciones, este comportamiento crea para el comportamiento del programa eficaz.  Sin embargo, si la retención de datos es crítica \(por ejemplo transacciones bank o información del billete de plano\) puede utilizar la opción de **c** .  El modo de **n** es el valor predeterminado.  
  
> [!NOTE]
>  Las opciones de **c** y de **n** no forman parte del estándar ANSI para `fopen`, pero son extensiones de Microsoft y no se deben utilizar donde desee la portabilidad de ANSI.  
  
## Utilizando la característica de Confirmación\-a\- disco con el código existente  
 De forma predeterminada, las llamadas a [fflush](../c-runtime-library/reference/fflush.md) o las funciones de la biblioteca de [\_flushall](../c-runtime-library/reference/flushall.md) escriben datos a los búferes mantenidos por el sistema operativo.  El sistema operativo determina la hora óptima de escribir realmente los datos en disco.  La característica de confirmación\-a\- disco de la biblioteca en tiempo de ejecución permite asegurarse que los datos crítico se escribe directamente en el disco y no a los búferes del sistema operativo.  Puede proporcionar esta funcionalidad a un programa existente sin reescribirlo vinculando los archivos objetos con COMMODE.OBJ.  
  
 En el archivo ejecutable resultante, las llamadas a `fflush` escriben el contenido del búfer directamente al disco, y las llamadas a `_flushall` escriben el contenido de todos los búferes en el disco.  Estas dos funciones son las únicas afectadas por COMMODE.OBJ.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [E\/S de secuencia](../c-runtime-library/stream-i-o.md)   
 [\_fdopen, \_wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen, \_wfopen](../c-runtime-library/reference/fopen-wfopen.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)