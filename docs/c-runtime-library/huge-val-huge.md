---
title: "HUGE_VAL, _HUGE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_HUGE"
apilocation: 
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_HUGE"
  - "HUGE_VAL"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_HUGE (constante)"
  - "HUGE_VAL (constante)"
  - "double (valor)"
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# HUGE_VAL, _HUGE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
#include <math.h>  
  
```  
  
## Comentarios  
 `HUGE_VAL` es el valor double puede representar mayor.  Este valor es devuelto por muchas funciones matemáticas en tiempo de ejecución cuando se produce un error.  Para algunas funciones, – se devuelve`HUGE_VAL` .  `HUGE_VAL` se define como `_HUGE`, pero funciones matemáticas `HUGE_VAL`return en tiempo de ejecución.  También debe utilizar `HUGE_VAL` en el código para la coherencia.  
  
## Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)