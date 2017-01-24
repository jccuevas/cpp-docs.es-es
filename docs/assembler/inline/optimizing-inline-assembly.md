---
title: "Optimizar un ensamblado alineado | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm (palabra clave) [C++], optimizar"
  - "ensamblado en línea, optimizar"
  - "optimización, ensamblado en línea"
  - "optimizar el rendimiento, ensamblado en línea"
  - "almacenamiento, optimizar en ensamblado alineado"
ms.assetid: 52a7ec83-9782-4d96-94c1-53bb2ac9e8c8
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Optimizar un ensamblado alineado
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 La presencia de un bloque `__asm` en una función afecta a la optimización de varias maneras.  En primer lugar, el compilador no intenta optimizar el propio bloque `__asm`.  Lo que se escribe en el lenguaje de ensamblado es exactamente lo que se obtiene.  En segundo lugar, la presencia de un bloque `__asm` afecta al almacenamiento de variables del registro.  El compilador evita registrar variables a través de un bloque `__asm` si existe la posibilidad de que el bloque `__asm` cambie el contenido del registro.  Por último, algunas otras optimizaciones de función resultarán afectadas por la inclusión del lenguaje de ensamblado en una función.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Ensamblador alineado](../../assembler/inline/inline-assembler.md)