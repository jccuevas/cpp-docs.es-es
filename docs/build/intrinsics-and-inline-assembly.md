---
title: "Ensamblado intr&#237;nseco y en l&#237;nea | Microsoft Docs"
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
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Ensamblado intr&#237;nseco y en l&#237;nea
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una de las restricciones para el compilador de [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)] es no tener compatibilidad con el ensamblador alineado.  Esto significa que las funciones que no se pueden escribir en C o C\+\+ tendrán que escribirse como subrutinas o como funciones intrínsecas compatibles con el compilador.  Hay ciertas funciones a las que les afecta el rendimiento y otras a las que no.  Las funciones a las que les afecta el rendimiento se deben implementar como funciones intrínsecas.  
  
 Las funciones intrínsecos compatibles con el compilador se describen en [Funciones intrínsecas del compilador](../intrinsics/compiler-intrinsics.md).  
  
## Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)