---
title: "signal (Constantes de acci&#243;n) | Microsoft Docs"
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
  - "SIG_IGN"
  - "SIG_DFL"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "SIG_DFL (constante)"
  - "SIG_IGN (constante)"
  - "signal (constantes de acción)"
ms.assetid: c3cb4f15-d39e-4d9d-84f9-0d33e3eb5993
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# signal (Constantes de acci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La acción realizada cuando se recibe la señal de la interrupción depende del valor de `func`.  
  
## Sintaxis  
  
```  
#include <signal.h>  
```  
  
## Comentarios  
 El argumento de `func` debe ser una dirección de función o una de las constantes de manifiesto que se enumeran a continuación y definidas en SIGNAL.H.  
  
 `SIG_DFL`  
 Utiliza respuesta de sistema\- predeterminado.  Si el programa de llamada utiliza E\/S de secuencia, los búferes creados por la biblioteca en tiempo de ejecución no se vacía.  
  
 `SIG_IGN`  
 Omite la señal de la interrupción.  Este valor nunca debe proporcionar para `SIGFPE`, ya que dejan el estado flotante de proceso definida.  
  
 `SIG_SGE`  
 Indica un error en la señal.  
  
 `SIG_ACK`  
 Indica que una confirmación se recibida.  
  
 `SIG_ERR`  
 Un tipo de valor devuelto de una señal que indique que se ha producido un error.  
  
## Vea también  
 [signal](../c-runtime-library/reference/signal.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)