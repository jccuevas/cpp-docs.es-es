---
title: "Advertencia del compilador (nivel 4) C4513 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4513"
ms.assetid: 6877334a-f30a-4184-9483-dac3348737a4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 4) C4513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'clase' : no se pudo generar un destructor  
  
 El compilador no pudo generar un destructor predeterminado para la clase dada; no se creó ningún destructor.  El destructor pertenece a una clase base que no es accesible para la clase derivada.  Si la clase base tiene un destructor privado, debe hacerse público o protegido.