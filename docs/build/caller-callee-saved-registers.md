---
title: "Registros guardados del llamador y del destinatario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Registros guardados del llamador y del destinatario
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los registros RAX, RCX, RDX, R8, R9, R10 y R11 se consideran volátiles y deben considerarse destruidos en las llamadas a funciones \(salvo que su seguridad quede demostrada mediante un análisis, como la optimización de todo el programa\).  
  
 Los registros RBX, RBP, RDI, RSI, RSP, R12, R13, R14 y R15 se consideran no volátiles, y debe guardarlos y restaurarlos una función que los utilice.  
  
## Vea también  
 [Convención de llamada](../build/calling-convention.md)