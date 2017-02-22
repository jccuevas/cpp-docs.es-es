---
title: "Conflictos con el compilador de x86 | Microsoft Docs"
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
ms.assetid: 8e47f0d3-afe0-42d9-9efa-de239ddd3a05
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Conflictos con el compilador de x86
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los tipos de datos que son mayores que 4 bytes no están alineados automáticamente en la pila al utilizar el compilador de x86 para compilar una aplicación.  Puesto que la arquitectura para el compilador de x86 es una pila alineada de 4 bytes, algo mayor que 4 bytes, por ejemplo, un entero de 64 bits, no puede estar alineado automáticamente a una dirección de 8 bytes.  
  
 Trabajar con datos no alineados tiene dos consecuencias.  
  
-   Puede llevar mucho más tiempo tener acceso a las ubicaciones desalineadas que el tiempo que se tarda en tener acceso a las ubicaciones alineadas.  
  
-   Las ubicaciones desalineadas no se pueden utilizar en operaciones entrelazadas.  
  
 Si se necesita una alineación más estricta, use `__declspec(align(N)) on your variable declarations`.  Esto provoca que el compilador alinee la pila de forma dinámica para cumplir sus especificaciones.  Sin embargo, ajustar la pila dinámicamente en tiempo de ejecución puede provocar una ejecución más lenta de la aplicación.  
  
## Vea también  
 [Tipos y almacenamiento](../build/types-and-storage.md)   
 [align](../cpp/align-cpp.md)