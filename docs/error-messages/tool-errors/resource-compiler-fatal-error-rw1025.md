---
title: "Error irrecuperable del compilador de recursos RW1025 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RW1025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RW1025"
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable del compilador de recursos RW1025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Memoria de montón far insuficiente  
  
 Compruebe si hay software residente en memoria que podría estar ocupando demasiado espacio.  Utilice el programa CHKDSK para averiguar la memoria de que dispone.  
  
 Si está creando un archivo de recursos grande, divida el script de recursos en dos archivos.  Después de crear dos archivos .RES, utilice la línea de comandos de MS\-DOS para unirlos:  
  
```  
copy first.res /b + second.res /b full.res  
```