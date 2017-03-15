---
title: "Archivos .Pdb como entrada del vinculador | Microsoft Docs"
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
  - ".pdb (archivos), como entrada del vinculador"
  - "PDB (archivos), como entrada del vinculador"
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Archivos .Pdb como entrada del vinculador
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los archivos objeto \(.obj\) compilados con la opción \/Zi contienen el nombre de una base de datos de programa \(PDB\).  No es preciso especificarle al vinculador el nombre del archivo PDB del objeto; de necesitarlo, LINK usará el nombre incrustado para encontrar el PDB.  Lo anterior también se aplica a los objetos depurables contenidos en una biblioteca; tanto el PDB de una biblioteca depurable como la propia biblioteca deben estar disponibles para el vinculador.  
  
 LINK también usa una PDB para contener información de depuración del archivo .exe o .dll.  La PDB del programa es, al mismo tiempo, un archivo de salida y de entrada pues LINK lo actualiza cuando recompila el programa.  
  
## Vea también  
 [Archivos de entrada de LINK](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)