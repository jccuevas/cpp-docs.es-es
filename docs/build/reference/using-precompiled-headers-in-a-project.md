---
title: "Utilizar encabezados precompilados en un proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "pch"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "encabezados precompilados"
ms.assetid: 95010260-a035-4327-9d61-222016ac146c
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Utilizar encabezados precompilados en un proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las secciones anteriores presentan información general sobre los encabezados precompilados: \/Yc e \/Yu, la opción \/Fp y la directiva pragma [hdrstop](../../preprocessor/hdrstop.md).  Esta sección describe un método para utilizar las opciones de encabezados precompilados en un proyecto y termina con un archivo MAKE de ejemplo y el código que administra.  
  
 Para ver otro enfoque del uso de opciones manuales de encabezados precompilados en un proyecto, estudie uno de los archivos MAKE ubicados en el directorio MFC\\SRC que se crea durante la instalación predeterminada de Visual C\+\+.  Estos archivos MAKE utilizan un método similar al presentado en esta sección, pero hacen un uso más extensivo de las macros de la Utilidad de mantenimiento de programas de Microsoft \(NMAKE\) y ofrecen un mayor control del proceso de compilación.  
  
 Esta sección contiene los siguientes temas:  
  
-   [Archivos PCH en el proceso de compilación](../../build/reference/pch-files-in-the-build-process.md)  
  
-   [Ejemplo de archivo MAKE para PCH](../../build/reference/sample-makefile-for-pch.md)  
  
-   [Código de ejemplo para PCH](../../build/reference/example-code-for-pch.md)  
  
## Vea también  
 [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)