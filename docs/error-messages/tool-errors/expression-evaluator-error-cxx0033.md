---
title: "Error del evaluador de expresiones CXX0033 | Microsoft Docs"
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
  - "CXX0033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0033"
  - "CXX0033"
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del evaluador de expresiones CXX0033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error en información de tipo OMF  
  
 El archivo ejecutable no tiene un formato de módulo de objeto \(OMF\) válido para depuración.  
  
 Este error es idéntico a CAN00033.  
  
### Posibles causas del error:  
  
1.  El archivo ejecutable no se creó con el vinculador incluido con esta versión de Visual C\+\+.  Vuelva a vincular el código de objeto con la versión actual de LINK.exe.  
  
2.  El archivo .exe puede estar dañado.  Vuelva a compilar y vuelva a vincular el programa.