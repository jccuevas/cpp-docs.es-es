---
title: "Error irrecuperable C1060 | Microsoft Docs"
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
  - "C1060"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1060"
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1060
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

espacio de montón insuficiente en el compilador  
  
 El sistema operativo o la biblioteca en tiempo de ejecución no pueden satisfacer una solicitud de memoria.  
  
### Para corregir este error pruebe las siguientes soluciones  
  
1.  Si el compilador también emite los errores [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) y [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), use la opción [\/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) del compilador para reducir el límite de asignación de memoria.  Habrá más espacio de montón disponible para la aplicación si reduce la asignación de memoria restante.  
  
     Si la opción [\/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) ya está establecida, pruebe a quitarla.  El espacio de montón podría agotarse si el límite de asignación de memoria especificado en la opción es demasiado alto.  El compilador utilizará un límite predeterminado si quita la opción [\/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).  
  
2.  Si está compilando en una plataforma de 64 bits, utilice el conjunto de herramientas del compilador de 64 bits.  Para obtener más información, vea [Cómo: Habilitar un conjunto de herramientas de Visual C\+\+ de 64 bits en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).  
  
3.  En Windows de 32 bits, pruebe a utilizar el conmutador de boot.ini [\/3GB](http://go.microsoft.com/fwlink/?LinkId=177831).  
  
4.  Aumente el tamaño del archivo de intercambio de Windows.  
  
5.  Cierre los demás programas que se estén ejecutando.  
  
6.  Elimine los archivos de inclusión innecesarios.  
  
7.  Elimine las variables globales que no son necesarias, por ejemplo, asignando memoria dinámicamente, en lugar de declarar una matriz grande.  
  
8.  Elimine las declaraciones que no utilice.  
  
9. Divida el archivo actual en archivos más pequeños.