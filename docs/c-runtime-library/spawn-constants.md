---
title: "spawn (Constantes) | Microsoft Docs"
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
  - "_P_NOWAIT"
  - "_P_OVERLAY"
  - "_P_WAIT"
  - "_P_DETACH"
  - "_P_NOWAITO"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_P_DETACH (constante)"
  - "_P_NOWAIT (constante)"
  - "_P_NOWAITO (constante)"
  - "_P_OVERLAY (constante)"
  - "_P_WAIT (constante)"
  - "P_DETACH (constante)"
  - "P_NOWAIT (constante)"
  - "P_NOWAITO (constante)"
  - "P_OVERLAY (constante)"
  - "P_WAIT (constante)"
  - "spawn (constantes)"
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# spawn (Constantes)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
#include <process.h>  
```  
  
## Comentarios  
 El argumento de `mode` determina la acción realizada por el proceso de llamada antes y durante una operación del generar.  Los siguientes valores para `mode` son posibles:  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_P_OVERLAY`|Superpone proceso de llamada con el nuevo proceso, destruyendo el proceso de llamada \(el mismo efecto que las llamadas de `_exec` \).|  
|`_P_WAIT`|Suspende el subproceso de llamada hasta que la ejecución del nuevo proceso se complete \( `_spawn`sincrónico\).|  
|`_P_NOWAIT`, `_P_NOWAITO`|Sigue ejecutando procesos que llama simultáneamente al nuevo proceso \( `_spawn`asincrónico\).|  
|`_P_DETACH`|Sigue ejecutando proceso de llamada; el nuevo proceso se ejecuta en segundo plano sin el acceso a la consola o el teclado.  Las llamadas a `_cwait` con nuevo proceso producirá un error.  Esto es `_spawn`asincrónico.|  
  
## Vea también  
 [\_spawn, \_wspawn \(Funciones\)](../c-runtime-library/spawn-wspawn-functions.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)