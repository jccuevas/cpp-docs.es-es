---
title: "Opciones de v&#237;nculo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nothrownew.obj"
  - "newmode.obj"
  - "noenv.obj"
  - "psetargv.obj"
  - "loosefpmath.obj"
  - "smallheap.obj"
  - "fp10.obj"
  - "nochkclr.obj"
  - "chkstk.obj"
  - "pcommode.obj"
  - "pnoenv.obj"
  - "opciones de vínculo [C++]"
  - "invalidcontinue.obj"
  - "pnothrownew.obj"
  - "pwsetargv.obj"
  - "pinvalidcontinue.obj"
  - "wsetargv.obj"
  - "binmode.obj"
  - "setargv.obj"
  - "noarg.obj"
  - "pnewmode.obj"
  - "commode.obj"
  - "pthreadlocale.obj"
  - "pbinmode.obj"
  - "threadlocale.obj"
  - "pnoarg.obj"
ms.assetid: 05b5a77b-9dd1-494b-ae46-314598c770bb
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Opciones de v&#237;nculo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El directorio de lib CRT incluye varios pequeños archivos objeto que habilitan las características específicas de CRT sin ningún cambio en el código.  Éstas se conocen como “opciones de vínculo” título que tiene que agregarlos a la línea de comandos del vinculador para utilizarlos.  
  
 Se han agregado las versiones puros de modo.  Utilice las versiones estándar para código nativo y el código de \/clr, utiliza las versiones puras \(prefijadas con un p\) para el modo de \/clr:pure .  
  
|Nativo y \/clr|Modo puro|Descripción|  
|--------------------|---------------|-----------------|  
|binmode.obj|pbinmode.obj|Establece el modo predeterminado del archivo \(el archivo traducción a binario.  Vea [\_fmode](../c-runtime-library/fmode.md).|  
|chkstk.obj|no disponible|Proporciona compatibilidad el pila\- comprobar y alloca memory cuando no mediante CRT.|  
|commode.obj|pcommode.obj|Establece la marca global de confirmación “para confirmar”.  Vea [fopen, \_wfopen](../c-runtime-library/reference/fopen-wfopen.md) y [fopen\_s, \_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md).|  
|fp10.obj|no disponible|Cambia el control predeterminado de precisión a 64 bits.  Vea [Compatibilidad con el punto flotante](../c-runtime-library/floating-point-support.md).|  
|invalidcontinue.obj|pinvalidcontinue.obj|Establezca un controlador no válido predeterminado del parámetro que no hace nada, lo que significa que los parámetros no válidos pasados a funciones CRT solo aparecen errno y devolverán un resultado de error.|  
|loosefpmath.obj|no disponible|Garantiza que el código de punto flotante tolere valores denormal.|  
|newmode.obj|pnewmode.obj|Haga [malloc](../c-runtime-library/reference/malloc.md) para llamar al nuevo controlador del error.  Vea [\_set\_new\_mode](../c-runtime-library/reference/set-new-mode.md), [\_set\_new\_handler](../c-runtime-library/reference/set-new-handler.md), [calloc](../c-runtime-library/reference/calloc.md) y [realloc](../c-runtime-library/reference/realloc.md).|  
|noarg.obj|pnoarg.obj|Deshabilita el procesamiento de argc y argv.|  
|nochkclr.obj|no disponible|No hace nada.  Quite del proyecto.|  
|noenv.obj|pnoenv.obj|Deshabilita la creación de un entorno almacenado en caché para CRT.|  
|nothrownew.obj|pnothrownew.obj|Habilita la versión no que produce de CRT.  Vea [Operadores new y delete](../cpp/new-and-delete-operators.md).|  
|setargv.obj|psetargv.obj|Permite la extensión del comodín de argumentos de la línea de comandos.  Vea [Expandir argumentos de caracteres comodín](../c-language/expanding-wildcard-arguments.md).|  
|smalheap.obj|no disponible|Instala un pequeño administrador muy sencillo de la pila.|  
|threadlocale.obj|pthreadlocale.obj|Habilita la configuración regional de por\- subproceso para todos los subprocesos de forma predeterminada.|  
|wsetargv.obj|pwsetargv.obj|Permite la extensión del comodín de argumentos de la línea de comandos.  Vea [Expandir argumentos de caracteres comodín](../c-language/expanding-wildcard-arguments.md).|  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)