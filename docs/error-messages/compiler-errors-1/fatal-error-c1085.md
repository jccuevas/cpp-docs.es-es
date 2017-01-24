---
title: "Error irrecuperable C1085 | Microsoft Docs"
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
  - "C1085"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1085"
ms.assetid: f2766365-d09b-4299-8a98-12e5aca98568
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1085
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede escribir el archivo tipodearchivo: 'archivo': mensaje  
  
### Posibles causas del error:  
  
1.  La unidad es de sólo lectura.  
  
2.  La unidad está llena.  
  
3.  Infracción de uso compartido.  
  
4.  Si el mensaje dice "número de archivo incorrecto", puede deberse a que el archivo se ha cerrado en primer plano mientras se estaba compilando en segundo plano.