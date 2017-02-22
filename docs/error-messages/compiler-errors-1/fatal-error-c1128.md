---
title: "Error irrecuperable C1128 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1128"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1128"
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error irrecuperable C1128
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el número de secciones superó el límite de formato de archivo de objeto: compile con \/bigobj  
  
 Un archivo .obj supera el número de secciones permitidas; ésta es una limitación del formato de archivo objeto COFF.  
  
 Esta limitación puede producirse como resultado del uso de [\/Gy](../../build/reference/gy-enable-function-level-linking.md) y una versión de depuración; **\/Gy** hace que las funciones tengan acceso a sus propias secciones COMDAT.  En una versión de depuración, hay una sección de información de depuración para cada función COMDAT.  
  
 También puede producirse el error C1128 cuando hay demasiadas funciones inline.  
  
 Para corregir este error, divida el archivo de código fuente en varios archivos de este tipo, compile sin **\/Gy** o compile con [\/bigobj \(Aumentar el número de secciones en el archivo .Obj\)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Si no compila con **\/Gy**, tendrá que especificar individualmente las optimizaciones, ya que tanto **\/O2** como **\/O1** implican **\/Gy**.  
  
 Si es posible, compile sin información de depuración.  
  
 También es posible que necesite disponer de creaciones de instancias de plantillas específicas en archivos de código fuente independientes, en lugar de esperar a que el compilador las emita.  
  
 Al trasladar código, probablemente aparecerá el error C1128 la primera vez que se use el compilador x64 y más tarde con el compilador x86. En x64 se asociarán al menos 4 secciones a cada función **\/Gy** compilada o insertada a partir de plantillas o una clase alineada: code, pdata e información de depuración, y posiblemente xdata.  x86 no tendrá pdata.