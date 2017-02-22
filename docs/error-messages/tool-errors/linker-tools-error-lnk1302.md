---
title: "Error de las herramientas del vinculador LNK1302 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1302"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1302"
ms.assetid: aea3c753-c2c4-4249-bbc3-f2d4f0164b5e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error de las herramientas del vinculador LNK1302
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

sólo admite vincular .netmodules seguro; no se puede leer el archivo de vínculo .netmodule  
  
 Un .netmodule \(compilado con **\/LN**\) se pasó al vinculador en un intento del usuario de invocar la vinculación de MSIL.  Un módulo de C\+\+ es válido para la vinculación de MSIL si se compila con **\/clr:safe**.  
  
 Para corregir este error, compile con **\/clr:safe** para permitir la vinculación MSIL o pase el archivo .obj **\/clr** o **\/clr:pure** al vinculador en lugar del módulo.  
  
 Para obtener más información, vea  
  
-   [\/LN \(Crear un módulo MSIL\)](../../build/reference/ln-create-msil-module.md)  
  
-   [.Archivos netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md)