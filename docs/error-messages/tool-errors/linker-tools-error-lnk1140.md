---
title: "Error de las herramientas del vinculador LNK1140 | Microsoft Docs"
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
  - "LNK1140"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1140"
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1140
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

demasiados módulos para la base de datos del programa; vincule con \/PDB:NONE  
  
 El proyecto contiene más de 4096 módulos.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Vuelva a vincular mediante [\/PDB:NONE](../../build/reference/pdb-use-program-database.md).  
  
2.  Compile algunos módulos sin usar información de depuración.  
  
3.  Reduzca el número de módulos.