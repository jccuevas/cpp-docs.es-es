---
title: "/FD (Recompilaci&#243;n m&#237;nima de IDE) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/FD"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FD (opción del compilador) [C++]"
  - "FD (opción del compilador) [C++]"
  - "-FD (opción del compilador) [C++]"
ms.assetid: 7ef21b8c-a448-4bb4-9585-a2a870028e17
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FD (Recompilaci&#243;n m&#237;nima de IDE)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\/FD** no se expone a los usuarios, salvo en la página de propiedades [Línea de comandos](../../ide/command-line-property-pages.md) del cuadro de diálogo **Páginas de propiedades** de un proyecto de C\+\+, exclusivamente si no se ha seleccionado tampoco [\/Gm \(Habilitar recompilación mínima\)](../../build/reference/gm-enable-minimal-rebuild.md).  **\/FD** solo tiene efecto en el entorno de desarrollo.  **\/FD** no se expone en el resultado de **cl \/?**.  
  
 Si no habilita **\/Gm** en el entorno de desarrollo, se usará **\/FD**.  **\/FD** asegura que el archivo .idb tiene suficiente información de dependencia.  Solo el entorno de desarrollo usa **\/FD**, y no debe utilizarse en la línea de comandos ni en un script de compilación.  
  
## Vea también  
 [\/F \(Opciones del archivo de resultados\)](../../build/reference/output-file-f-options.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)