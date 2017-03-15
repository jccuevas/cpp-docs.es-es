---
title: "Error del compilador de recursos RC2151 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2151"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2151"
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador de recursos RC2151
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se pueden volver a usar constantes de cadena  
  
 Se está utilizando el mismo valor dos veces en una instrucción **STRINGTABLE.** Asegúrese de que no se mezclan valores decimales y hexadecimales superpuestos.  
  
 Cada uno de los identificadores en una **STRINGTABLE** debe ser único.  Para obtener la máxima eficacia utilice constantes contiguas que comiencen con un múltiplo de 16.