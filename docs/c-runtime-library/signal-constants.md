---
title: "signal (Constantes) | Microsoft Docs"
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
  - "SIGTERM"
  - "SIGFPE"
  - "SIGABRT"
  - "SIGILL"
  - "SIGINT"
  - "SIGSEGV"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "SIGABRT (constante)"
  - "SIGFPE (constante)"
  - "SIGILL (constante)"
  - "SIGINT (constante)"
  - "signal (constantes)"
  - "SIGSEGV (constante)"
  - "SIGTERM (constante)"
ms.assetid: a3b39281-dae7-4e44-8d68-e6a610c669dd
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# signal (Constantes)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
#include <signal.h>  
```  
  
## Comentarios  
 El argumento de `sig` debe ser una de las constantes de manifiesto que se enumeran a continuación \(definido en SIGNAL.H\).  
  
 `SIGABRT`  
 Terminación anormal.  La acción predeterminada finaliza el programa de llamada con el código de salida 3.  
  
 `SIGABRT_COMPAT`  
 Igual que SIGABRT.  Para la compatibilidad con otras plataformas.  
  
 `SIGFPE`  
 Error flotante, como desbordamiento, división por cero, o operación no válida.  La acción predeterminada finaliza el programa de llamada.  
  
 `SIGILL`  
 Instrucción no válida.  La acción predeterminada finaliza el programa de llamada.  
  
 `SIGINT`  
 Interrupción de CTRL\+C.  La acción predeterminada finaliza el programa de llamada con el código de salida 3.  
  
 `SIGSEGV`  
 Acceso no válido de almacenamiento.  La acción predeterminada finaliza el programa de llamada.  
  
 `SIGTERM`  
 Solicitud de finalización enviada al programa.  La acción predeterminada finaliza el programa de llamada con el código de salida 3.  
  
 `SIG_ERR`  
 Un tipo de valor devuelto de una señal que indique que se ha producido un error.  
  
## Vea también  
 [signal](../c-runtime-library/reference/signal.md)   
 [raise](../c-runtime-library/reference/raise.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)