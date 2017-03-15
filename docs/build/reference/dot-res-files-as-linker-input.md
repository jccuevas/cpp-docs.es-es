---
title: "Archivos .Res como entrada del vinculador | Microsoft Docs"
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
  - "archivos .res como entrada del vinculador"
  - "vincular [C++], archivos de recursos"
  - "archivos RES como entrada del vinculador"
  - "archivos de recursos, vincular"
ms.assetid: 9c37ab00-97df-4d9a-91cd-6bf132970683
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos .Res como entrada del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Es posible especificar un archivo .res durante la vinculación de un programa.  El archivo lo crea el compilador de recursos \(RC\).  LINK convierte los archivos .res automáticamente a COFF.  La herramienta CVTRES.exe debe estar en el mismo directorio que LINK.exe o en un directorio especificado en la variable de entorno PATH.  
  
## Vea también  
 [Archivos de entrada de LINK](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)