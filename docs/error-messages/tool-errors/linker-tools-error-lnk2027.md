---
title: "Error de las herramientas del vinculador LNK2027 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2027"
ms.assetid: e2f857a8-8e8a-4697-bbff-12ccb84a35c1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error de las herramientas del vinculador LNK2027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

referencia de módulo sin resolver 'módulo'  
  
 Un archivo pasado al vinculador tiene una dependencia en un módulo que no se especificó con **\/ASSEMBLYMODULE** ni se pasó directamente al vinculador.  
  
 Para solucionarlo, realice una de las acciones siguientes:  
  
-   No pase al vinculador el archivo que tiene la dependencia de módulo.  
  
-   Especifique el módulo con **\/ASSEMBLYMODULE**.  
  
-   Si el módulo es un .netmodule seguro, pase el módulo directamente al vinculador.  
  
 Para obtener más información, vea [\/ASSEMBLYMODULE \(Agregar un módulo MSIL al ensamblado\)](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) y [.Archivos netmodule como entrada del vinculador](../../build/reference/netmodule-files-as-linker-input.md).