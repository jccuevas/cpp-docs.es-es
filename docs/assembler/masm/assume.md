---
title: "ASSUME | Microsoft Docs"
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
  - "ASSUME"
  - "_assume_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ASSUME directive"
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ASSUME
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita la comprobación de errores para los valores del registro.  
  
## Sintaxis  
  
```  
  
      ASSUME segregister:name [[, segregister:name]]...  
ASSUME dataregister:type [[, dataregister:type]]...  
ASSUME register:ERROR [[, register:ERROR]]...  
ASSUME [[register:]] NOTHING [[, register:NOTHING]]...  
```  
  
## Comentarios  
 Después de ejecutar `ASSUME` , relojes de código ensamblador para los cambios a los valores de los registros especificados.  **ERROR** genera un error si se utiliza el registro.  **NOTHING** quita comprobación del registro de errores.  Puede combinar varias clases de supuestos en una instrucción.  
  
## Vea también  
 [Directives Reference](../../assembler/masm/directives-reference.md)