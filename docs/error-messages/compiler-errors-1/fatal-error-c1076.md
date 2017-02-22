---
title: "Error irrecuperable C1076 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1076"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1076"
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error irrecuperable C1076
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

límite del compilador : se ha alcanzado el límite del montón interno; utilice \/Zm para especificar un límite más alto  
  
 Este error puede producirse por un exceso de símbolos o de instancias de la plantilla.  
  
 Para resolver este error:  
  
1.  Use la opción [\/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) para establecer el límite de memoria del compilador en el valor especificado en el mensaje de error [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md).  Para obtener más información y saber cómo puede configurar este valor en [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)], vea la sección Comentarios de [\/Zm \(Especificar el límite de asignación de memoria del encabezado precompilado\)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).  
  
2.  Si usa los compiladores hospedados de 32 bits en un sistema operativo de 64 bits, utilice en su lugar los compiladores hospedados de 64 bits.  Para obtener más información, vea [Cómo: Habilitar un conjunto de herramientas de Visual C\+\+ de 64 bits en la línea de comandos](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).  
  
3.  Elimine los archivos de inclusión innecesarios.  
  
4.  Elimine las variables globales que no son necesarias \(por ejemplo, asignando memoria dinámicamente, en lugar de declarar una matriz grande\).  
  
5.  Elimine las declaraciones que no utilice.  
  
6.  Divida las funciones grandes en funciones más pequeñas.  
  
7.  Divida las clases grandes en clases más pequeñas.  
  
8.  Divida el archivo actual en archivos más pequeños.  
  
 Si el error C1076 se produce inmediatamente después de comenzar la compilación, es probable que se deba a que el valor especificado por **\/Zm** es demasiado alto para el programa.  Reduzca el valor **\/Zm**.